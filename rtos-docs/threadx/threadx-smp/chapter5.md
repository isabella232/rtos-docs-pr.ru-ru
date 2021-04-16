---
title: Глава 5. Драйверы устройств для ThreadX SMP для ОСРВ Azure
description: В этой главе приводится описание драйверов устройств для ThreadX SMP для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816064"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a><span data-ttu-id="e3626-103">Глава 5. Драйверы устройств для ThreadX SMP для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="e3626-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX SMP</span></span>

<span data-ttu-id="e3626-104">В этой главе приводится описание драйверов устройств для ThreadX SMP для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="e3626-104">This chapter contains a description of device drivers for Azure RTOS ThreadX SMP.</span></span> <span data-ttu-id="e3626-105">Сведения, представленные в этой главе, призваны помочь разработчикам при написании драйверов для конкретных приложений.</span><span class="sxs-lookup"><span data-stu-id="e3626-105">The information presented in this chapter is designed to help developers write application specific drivers.</span></span> 

## <a name="device-driver-introduction"></a><span data-ttu-id="e3626-106">Введение в драйверы устройств</span><span class="sxs-lookup"><span data-stu-id="e3626-106">Device Driver Introduction</span></span>

<span data-ttu-id="e3626-107">Связь с внешней средой — это важная составляющая большинства внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="e3626-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="e3626-108">Такая связь осуществляется с помощью аппаратных устройств, доступных ПО внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="e3626-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="e3626-109">Программные компоненты, которые отвечают за управление такими устройствами, обычно называются *драйверами*.</span><span class="sxs-lookup"><span data-stu-id="e3626-109">The software components responsible for managing such devices are commonly called *Device Drivers*.</span></span>

<span data-ttu-id="e3626-110">Драйверы устройств представляют собой внедренные работающие в реальном времени системы, которые по своей природе зависимы от приложения.</span><span class="sxs-lookup"><span data-stu-id="e3626-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="e3626-111">Это так по двум основным причинам: невероятное разнообразие целевого оборудования и настолько же широкие требования к производительности, предъявляемые к работающим в реальном времени приложениям.</span><span class="sxs-lookup"><span data-stu-id="e3626-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="e3626-112">Поэтому практически невозможно предоставить общий набор драйверов, удовлетворяющих требованиям любого приложения.</span><span class="sxs-lookup"><span data-stu-id="e3626-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="e3626-113">В связи с этим сведения в этой главе призваны помочь пользователям настроить *стандартные* драйверы устройств ThreadX SMP и написать собственные драйверы.</span><span class="sxs-lookup"><span data-stu-id="e3626-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX SMP device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="e3626-114">Функции драйверов</span><span class="sxs-lookup"><span data-stu-id="e3626-114">Driver Functions</span></span>

<span data-ttu-id="e3626-115">Драйверы устройств ThreadX SMP включают восемь основных выполняемых функций:</span><span class="sxs-lookup"><span data-stu-id="e3626-115">ThreadX SMP device drivers are composed of eight basic functional areas, as follows:</span></span>

- <span data-ttu-id="e3626-116">**инициализация драйвера;**</span><span class="sxs-lookup"><span data-stu-id="e3626-116">**Driver Initialization**</span></span>
- <span data-ttu-id="e3626-117">**управление драйвером;**</span><span class="sxs-lookup"><span data-stu-id="e3626-117">**Driver Control**</span></span>
- <span data-ttu-id="e3626-118">**доступ к драйверу;**</span><span class="sxs-lookup"><span data-stu-id="e3626-118">**Driver Access**</span></span>
- <span data-ttu-id="e3626-119">**получение данных драйвером;**</span><span class="sxs-lookup"><span data-stu-id="e3626-119">**Driver Input**</span></span>
- <span data-ttu-id="e3626-120">**вывод данных драйвером;**</span><span class="sxs-lookup"><span data-stu-id="e3626-120">**Driver Output**</span></span>
- <span data-ttu-id="e3626-121">**прерывания драйвера;**</span><span class="sxs-lookup"><span data-stu-id="e3626-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="e3626-122">**состояние драйвера;**</span><span class="sxs-lookup"><span data-stu-id="e3626-122">**Driver Status**</span></span>
- <span data-ttu-id="e3626-123">**завершение работы драйвера.**</span><span class="sxs-lookup"><span data-stu-id="e3626-123">**Driver Termination**</span></span>

<span data-ttu-id="e3626-124">За исключением инициализации, каждая из таких выполняемых функций является необязательной.</span><span class="sxs-lookup"><span data-stu-id="e3626-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="e3626-125">Более того, обработка каждой выполняемой функции зависит от драйвера устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="e3626-126">Инициализация драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-126">Driver Initialization</span></span> 
<span data-ttu-id="e3626-127">Эта выполняемая функция отвечает за инициализацию реального аппаратного устройства и внутренних структур данных драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="e3626-128">Вызов других служб драйвера невозможен, пока не завершится этап инициализации.</span><span class="sxs-lookup"><span data-stu-id="e3626-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3626-129">Компонент функции для инициализации драйвера обычно вызывается из функции **tx_application_define** или из потока инициализации.</span><span class="sxs-lookup"><span data-stu-id="e3626-129">The driver’s initialization function component is typically called from the **tx_application_define** function or from an initialization thread.</span></span>

### <a name="driver-control"></a><span data-ttu-id="e3626-130">Управление драйвером</span><span class="sxs-lookup"><span data-stu-id="e3626-130">Driver Control</span></span> 
<span data-ttu-id="e3626-131">После того как драйвер будет инициализирован и готов к работе, эта функция отвечает за управление им во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="e3626-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="e3626-132">Обычно управление во время выполнения заключается в реализации изменений в работе базового аппаратного устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="e3626-133">Например, это может быть изменение скорости передачи (бит/с) для устройства с последовательным интерфейсом или поиск нового сектора на диске.</span><span class="sxs-lookup"><span data-stu-id="e3626-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="e3626-134">Доступ к драйверу</span><span class="sxs-lookup"><span data-stu-id="e3626-134">Driver Access</span></span> 
<span data-ttu-id="e3626-135">Некоторые драйверы устройств вызываются только из одного потока приложения.</span><span class="sxs-lookup"><span data-stu-id="e3626-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="e3626-136">В таких случаях эту функцию выполнять не требуется.</span><span class="sxs-lookup"><span data-stu-id="e3626-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="e3626-137">Но в приложениях, в которых к драйверу требуется одновременный доступ из нескольких потоков, их взаимодействием можно управлять с помощью средств назначения и освобождения в драйвере устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="e3626-138">Приложение также может использовать семафор для управления доступом к драйверу и таким образом избежать излишней нагрузки на ресурсы и усложнения кода в драйвере.</span><span class="sxs-lookup"><span data-stu-id="e3626-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span> 

### <a name="driver-input"></a><span data-ttu-id="e3626-139">Получение данных драйвером</span><span class="sxs-lookup"><span data-stu-id="e3626-139">Driver Input</span></span> 
<span data-ttu-id="e3626-140">Эта функция отвечает за все операции ввода данных на устройстве.</span><span class="sxs-lookup"><span data-stu-id="e3626-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="e3626-141">Основные проблемы, связанные с входными данными драйвера, обычно касаются способов буферизации входных данных и их ожидания потоками.</span><span class="sxs-lookup"><span data-stu-id="e3626-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span> 

### <a name="driver-output"></a><span data-ttu-id="e3626-142">Вывод данных драйвером</span><span class="sxs-lookup"><span data-stu-id="e3626-142">Driver Output</span></span> 
<span data-ttu-id="e3626-143">Эта выполняемая функция отвечает за обработку всех выходных данных устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="e3626-144">Основные проблемы, связанные с выходными данными драйвера, обычно касаются способов буферизации выходных данных и их ожидания потоками.</span><span class="sxs-lookup"><span data-stu-id="e3626-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span> 

### <a name="driver-interrupts"></a><span data-ttu-id="e3626-145">Прерывания драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-145">Driver Interrupts</span></span> 
<span data-ttu-id="e3626-146">Большинство систем, работающих в реальном времени, используют аппаратные прерывания для уведомления драйвера о событиях ввода, вывода, управления и ошибок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="e3626-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="e3626-147">Прерывания предоставляют таким внешним событиям гарантированное время отклика.</span><span class="sxs-lookup"><span data-stu-id="e3626-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="e3626-148">Вместо прерываний ПО драйвера может периодически проверять наличие таких событий на внешнем оборудовании.</span><span class="sxs-lookup"><span data-stu-id="e3626-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="e3626-149">Такая методика называется *опросом*.</span><span class="sxs-lookup"><span data-stu-id="e3626-149">This technique is called *polling*.</span></span> <span data-ttu-id="e3626-150">Так как она предъявляет меньше требований к обработке в реальном времени, опросы могут лучше подходить для соответствующих приложений.</span><span class="sxs-lookup"><span data-stu-id="e3626-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span> 

### <a name="driver-status"></a><span data-ttu-id="e3626-151">Состояние драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-151">Driver Status</span></span> 
<span data-ttu-id="e3626-152">Эта выполняемая функция отвечает за предоставление данных о состоянии и статистики среды выполнения, связанных с работой драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-152">This function area is responsible for providing runtime status and statistics associated with the driver operation.</span></span> <span data-ttu-id="e3626-153">Сведения, которые обрабатывает эта функция, обычно включают следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="e3626-153">Information managed by this function area typically includes the following:</span></span> 
- <span data-ttu-id="e3626-154">текущее состояние устройства;</span><span class="sxs-lookup"><span data-stu-id="e3626-154">Current device status</span></span>
- <span data-ttu-id="e3626-155">входные байты;</span><span class="sxs-lookup"><span data-stu-id="e3626-155">Input bytes</span></span>
- <span data-ttu-id="e3626-156">выходные байты;</span><span class="sxs-lookup"><span data-stu-id="e3626-156">Output bytes</span></span>
- <span data-ttu-id="e3626-157">число ошибок устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="e3626-158">Завершение работы драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-158">Driver Termination</span></span> 
<span data-ttu-id="e3626-159">Эта выполняемая функция необязательна.</span><span class="sxs-lookup"><span data-stu-id="e3626-159">This functional area is optional.</span></span> <span data-ttu-id="e3626-160">Она необходима только в том случае, если необходимо завершить работу драйвера и (или) физического аппаратного устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="e3626-161">После завершения работы драйвер нельзя вызвать, пока он не будет повторно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="e3626-161">After being terminated, the driver must not be called again until it is re-initialized.</span></span> 

## <a name="simple-driver-example"></a><span data-ttu-id="e3626-162">Пример простого драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-162">Simple Driver Example</span></span>

<span data-ttu-id="e3626-163">Пример позволяет лучше понять, как работает драйвер устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="e3626-164">В этом примере для драйвера предполагается простое аппаратное устройство с последовательным интерфейсом, с регистром конфигурации, регистрами входных и выходных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="e3626-165">Этот пример простого драйвера демонстрирует выполнение функций инициализации, ввода данных, вывода данных и прерываний.</span><span class="sxs-lookup"><span data-stu-id="e3626-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="e3626-166">Инициализация простого драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-166">Simple Driver Initialization</span></span> 
<span data-ttu-id="e3626-167">Функция ***tx_sdriver_initialize*** простого драйвера создает два вычислительных семафора, которые используются для управления операциями с входными и выходными данными драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver’s input and output operation.</span></span> <span data-ttu-id="e3626-168">Семафор входных данных задается обработчиком прерываний входных данных, когда аппаратное устройство с последовательным интерфейсом получает символ.</span><span class="sxs-lookup"><span data-stu-id="e3626-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="e3626-169">По этой причине семафор ввода создается со счетчиком, имеющим значение 0.</span><span class="sxs-lookup"><span data-stu-id="e3626-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="e3626-170">И наоборот, семафор вывода указывает на доступность регистра передачи для оборудования с последовательным интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="e3626-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="e3626-171">Он создается со значением 1, чтобы указать на первоначальную доступность регистра передачи.</span><span class="sxs-lookup"><span data-stu-id="e3626-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="e3626-172">Функция инициализации также отвечает за установку обработчиков векторов прерывания низкого уровня для уведомлений входных и выходных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="e3626-173">Как и другие подпрограммы службы прерываний ThreadX SMP, обработчик низкого уровня должен вызвать \* **_tx_thread_context_save** _ до вызова обработчика прерываний простого драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-173">Like other ThreadX SMP interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="e3626-174">После того как обработчик прерываний драйвера будет возвращен, обработчик низкого уровня должен вызвать _\*_ _tx_thread_context_restore_\*\*.</span><span class="sxs-lookup"><span data-stu-id="e3626-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3626-175">Важно, чтобы инициализация была вызвана до любых других функций драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-175">It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="e3626-176">Обычно инициализация драйвера вызывается из функции **tx_application_define**.</span><span class="sxs-lookup"><span data-stu-id="e3626-176">Typically, driver initialization is called from **tx_application_define**.</span></span>

<span data-ttu-id="e3626-177">Исходный код инициализации для простого драйвера см. на рис. 9 на стр. 306.</span><span class="sxs-lookup"><span data-stu-id="e3626-177">See Figure 9 on page 306 for the initialization source code of the simple driver.</span></span>

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
<span data-ttu-id="e3626-178">**Рис. 9. Инициализация простого драйвера**</span><span class="sxs-lookup"><span data-stu-id="e3626-178">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="e3626-179">Входные данные простого драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-179">Simple Driver Input</span></span> 
<span data-ttu-id="e3626-180">Входные данные для простого драйвера управляются семафором ввода.</span><span class="sxs-lookup"><span data-stu-id="e3626-180">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="e3626-181">При получении прерывания входных данных устройства задается семафор ввода.</span><span class="sxs-lookup"><span data-stu-id="e3626-181">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="e3626-182">Если один или несколько потоков ожидают получения символа от драйвера, работу продолжает поток с наибольшим временем ожидания.</span><span class="sxs-lookup"><span data-stu-id="e3626-182">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="e3626-183">Если работают все потоки, семафор сохраняется до того момента, пока поток не вызовет функцию ввода драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-183">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="e3626-184">Существует несколько ограничений при обработки входных данных простым драйвером.</span><span class="sxs-lookup"><span data-stu-id="e3626-184">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="e3626-185">Самое значительное — возможность удаления символов входных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-185">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="e3626-186">Это возможно, так как нельзя выполнить буферизацию символов входных данных, которые принимаются до завершения обработки предыдущего символа.</span><span class="sxs-lookup"><span data-stu-id="e3626-186">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="e3626-187">Эта проблема легко решается путем добавления буфера символов входных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-187">This is easily handled by adding an input character buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3626-188">Функцию **tx_sdriver_input** могут вызывать только потоки.</span><span class="sxs-lookup"><span data-stu-id="e3626-188">Only threads are allowed to call the **tx_sdriver_input** function.</span></span>

<span data-ttu-id="e3626-189">На рис. 10 приведен исходный код, связанный с входными данными простого драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-189">Figure 10 shows the source code associated with simple driver input.</span></span>

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
<span data-ttu-id="e3626-190">**Рис. 10. Входные данные простого драйвера**</span><span class="sxs-lookup"><span data-stu-id="e3626-190">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="e3626-191">Выходные данные простого драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-191">Simple Driver Output</span></span> 
<span data-ttu-id="e3626-192">При обработке выходных данных используется семафор вывода для уведомления о том, что регистр передачи устройства с последовательным интерфейсом освободился.</span><span class="sxs-lookup"><span data-stu-id="e3626-192">Output processing utilizes the output semaphore to signal when the serial device’s transmit register is free.</span></span> <span data-ttu-id="e3626-193">Перед фактической записью символа выходных данных на устройство выполняется получение семафора вывода.</span><span class="sxs-lookup"><span data-stu-id="e3626-193">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="e3626-194">Если он недоступен, возможно, предыдущая операция передачи еще не завершена.</span><span class="sxs-lookup"><span data-stu-id="e3626-194">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="e3626-195">Обработчик прерываний выходных данных отвечает за обработку прерывания завершения при передаче.</span><span class="sxs-lookup"><span data-stu-id="e3626-195">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="e3626-196">Его операции заключаются в установке семафора вывода, что позволяет выполнить вывод другого символа.</span><span class="sxs-lookup"><span data-stu-id="e3626-196">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3626-197">Вызывать функцию **tx_sdriver_output** могут только потоки.</span><span class="sxs-lookup"><span data-stu-id="e3626-197">Only threads are allowed to call the **tx_sdriver_output** function.</span></span>

<span data-ttu-id="e3626-198">На рис. 11 приведен исходный код, связанный с выходными данными простого драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-198">Figure 11 shows the source code associated with simple driver output.</span></span>

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="e3626-199">**Рис. 11. Выходные данные простого драйвера**</span><span class="sxs-lookup"><span data-stu-id="e3626-199">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="e3626-200">Недостатки простого драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-200">Simple Driver Shortcomings</span></span> 
<span data-ttu-id="e3626-201">Этот пример простого драйвера устройства иллюстрирует принцип работы драйвера со ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="e3626-201">This simple device driver example illustrates the basic idea of a ThreadX SMP device driver.</span></span> <span data-ttu-id="e3626-202">Но так как в этом простом драйвере устройства не устранены проблемы с буферизацией данных или излишней нагрузкой на ресурсы, он не полностью эквивалентен реальным драйверам со ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="e3626-202">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX SMP drivers.</span></span> <span data-ttu-id="e3626-203">В разделе ниже описаны некоторые более сложные проблемы, связанные с драйверами устройств.</span><span class="sxs-lookup"><span data-stu-id="e3626-203">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="e3626-204">Сложные проблемы с драйверами</span><span class="sxs-lookup"><span data-stu-id="e3626-204">Advanced Driver Issues</span></span>

<span data-ttu-id="e3626-205">Как было сказано ранее, требования драйверов устройств аналогичны требованиям их приложений.</span><span class="sxs-lookup"><span data-stu-id="e3626-205">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="e3626-206">Некоторым приложениям может требоваться выполнять буферизацию огромного объема данных, а другие приложения могут нуждаться в оптимизированном обработчике прерываний драйвера из-за высокой частоты прерываний устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-206">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="e3626-207">Буферизация ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="e3626-207">I/O Buffering</span></span> 
<span data-ttu-id="e3626-208">Буферизация данных во внедренных приложениях, работающих в реальном времени, требует тщательного планирования.</span><span class="sxs-lookup"><span data-stu-id="e3626-208">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="e3626-209">В некоторых случаях его реализация будет зависеть от базового аппаратного устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-209">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="e3626-210">Если устройство предоставляет базовый побайтовый ввод-вывод, вероятно, имеет смысл добавить простой циклический буфер.</span><span class="sxs-lookup"><span data-stu-id="e3626-210">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="e3626-211">Но если устройство предоставляет блочный, пакетный ввод-вывод или ввод-вывод с прямым доступом к памяти, более оптимально будет использовать схему управления буфером.</span><span class="sxs-lookup"><span data-stu-id="e3626-211">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span> 

### <a name="circular-byte-buffers"></a><span data-ttu-id="e3626-212">Циклические байтовые буферы</span><span class="sxs-lookup"><span data-stu-id="e3626-212">Circular Byte Buffers</span></span> 
<span data-ttu-id="e3626-213">Циклические байтовые буферы обычно используются в драйверах, которые управляют простым аппаратным устройством с последовательным интерфейсом, например UART.</span><span class="sxs-lookup"><span data-stu-id="e3626-213">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="e3626-214">В таких ситуациях чаще всего используются два циклических буфера — один для входных, а другой для выходных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-214">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="e3626-215">Каждый циклический байтовый буфер состоит из байтовой области памяти (обычно это массив из UCHAR), указателя на чтение и указателя на запись.</span><span class="sxs-lookup"><span data-stu-id="e3626-215">Each circular byte buffer is comprised of a byte memory area (typically an array of UCHARs), a read pointer, and a write pointer.</span></span> <span data-ttu-id="e3626-216">Буфер считается пустым, если указатель на чтение и указатели на запись ссылаются на одно расположение памяти в буфере.</span><span class="sxs-lookup"><span data-stu-id="e3626-216">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="e3626-217">Инициализация драйвера задает для указателей буфера на чтение и запись расположение в начальном адресе буфера.</span><span class="sxs-lookup"><span data-stu-id="e3626-217">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="e3626-218">Входные данные циклического буфера</span><span class="sxs-lookup"><span data-stu-id="e3626-218">Circular Buffer Input</span></span> 
<span data-ttu-id="e3626-219">Буфер ввода используется для хранения символов, которые приложение еще не готово обработать.</span><span class="sxs-lookup"><span data-stu-id="e3626-219">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="e3626-220">При получении символа входных данных (обычно в обработчике прерываний) от аппаратного устройства принимается новый символ и помещается в буфер ввода в расположении, на которое ссылается указатель на запись.</span><span class="sxs-lookup"><span data-stu-id="e3626-220">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="e3626-221">Затем указатель на запись перемещается на следующую позицию в буфере.</span><span class="sxs-lookup"><span data-stu-id="e3626-221">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="e3626-222">Если следующая позиция находится за пределами буфера, указатель на запись устанавливается на начало буфера.</span><span class="sxs-lookup"><span data-stu-id="e3626-222">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="e3626-223">Условие заполнения очереди обрабатывается путем отмены перемещения указателя на запись, если новый указатель на запись не отличается от указателя на чтение.</span><span class="sxs-lookup"><span data-stu-id="e3626-223">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="e3626-224">Побайтовые запросы к входным данным приложения, направляемые драйверу, сначала проверяют указатели на чтение и запись буфера ввода.</span><span class="sxs-lookup"><span data-stu-id="e3626-224">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="e3626-225">Если указатели на чтение и запись идентичны, это означает, что буфер пуст.</span><span class="sxs-lookup"><span data-stu-id="e3626-225">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="e3626-226">Если же указатель на чтение отличается, байт, на который ссылается указатель на чтение, копируется из буфера ввода, а указатель на чтение перемещается на следующее расположение в буфере.</span><span class="sxs-lookup"><span data-stu-id="e3626-226">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="e3626-227">Если новый указатель на чтение выходит за пределы буфера, он сбрасывается на начало.</span><span class="sxs-lookup"><span data-stu-id="e3626-227">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="e3626-228">На рис. 12 приведена логика для циклического буфера ввода.</span><span class="sxs-lookup"><span data-stu-id="e3626-228">Figure 12 shows the logic for the circular input buffer.</span></span>

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
<span data-ttu-id="e3626-229">**Рис. 12. Логика для циклического буфера ввода**</span><span class="sxs-lookup"><span data-stu-id="e3626-229">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3626-230">Для надежной работы может потребоваться заблокировать прерывания при изменении указателей на чтение и запись для циклических буферов ввода и вывода.</span><span class="sxs-lookup"><span data-stu-id="e3626-230">For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span>

### <a name="circular-output-buffer"></a><span data-ttu-id="e3626-231">Циклический буфер вывода</span><span class="sxs-lookup"><span data-stu-id="e3626-231">Circular Output Buffer</span></span> 
<span data-ttu-id="e3626-232">Буфер вывода используется для хранения символов, которые были приняты на вывод до того, как аппаратное устройство завершило отправку предыдущего байта.</span><span class="sxs-lookup"><span data-stu-id="e3626-232">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="e3626-233">Обработка буфера вывода аналогична обработке для буфера ввода, за исключением того, что обработка прерывания завершений передачи используется с указателем на чтение выходных данных, а запрос выходных данных к приложению использует указатель на запись выходных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-233">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span> <span data-ttu-id="e3626-234">В остальном обработка буфера выходных данных не отличается.</span><span class="sxs-lookup"><span data-stu-id="e3626-234">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="e3626-235">На рис. 13 приведена логика для циклического буфера вывода.</span><span class="sxs-lookup"><span data-stu-id="e3626-235">Figure 13shows the logic for the circular output buffer.</span></span>

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
<span data-ttu-id="e3626-236">**Рис. 13. Логика для циклического буфера вывода**</span><span class="sxs-lookup"><span data-stu-id="e3626-236">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="e3626-237">Управление вводом-выводом буфера</span><span class="sxs-lookup"><span data-stu-id="e3626-237">Buffer I/O Management</span></span> 
<span data-ttu-id="e3626-238">Для улучшения производительности внедренных микропроцессоров многие периферийные устройства передают и получают данные с помощью буферов, предоставляемых программным обеспечением.</span><span class="sxs-lookup"><span data-stu-id="e3626-238">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="e3626-239">В некоторых реализациях могут использоваться несколько буферов для передачи или получения отдельных пакетов данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-239">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span> 

<span data-ttu-id="e3626-240">Размер и расположение буферов ввода-вывода определяются приложением и (или) ПО драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-240">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="e3626-241">Обычно буферы имеют фиксированный размер и управляются в пуле блочной памяти ThreadX SMP.</span><span class="sxs-lookup"><span data-stu-id="e3626-241">Typically, buffers are fixed in size and managed within a ThreadX SMP block memory pool.</span></span> <span data-ttu-id="e3626-242">На рис. 14 приведен типичный буфер ввода-вывода и пул блочной памяти ThreadX SMP, который управляет их выделением.</span><span class="sxs-lookup"><span data-stu-id="e3626-242">Figure 14describes a typical I/O buffer and a ThreadX SMP block memory pool that manages their allocation.</span></span>

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
<span data-ttu-id="e3626-243">**Рис. 14. Буфер ввода-вывода**</span><span class="sxs-lookup"><span data-stu-id="e3626-243">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="e3626-244">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e3626-244">TX_IO_BUFFER</span></span> 
<span data-ttu-id="e3626-245">typedef TX_IO_BUFFER состоит из двух указателей.</span><span class="sxs-lookup"><span data-stu-id="e3626-245">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="e3626-246">Указатель \***tx_next_packet** _ используется для связывания нескольких пакетов в списке входных или выходных данных.</span><span class="sxs-lookup"><span data-stu-id="e3626-246">The \***tx_next_packet** _ pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="e3626-247">Указатель _ *_tx_next_buffer_*\* используется для связывания буферов, которые составляют отдельный пакет данных от устройства.</span><span class="sxs-lookup"><span data-stu-id="e3626-247">The _ *_tx_next_buffer_*\* pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="e3626-248">Для обоих этих указателей задано значение NULL при выделении буфера из пула.</span><span class="sxs-lookup"><span data-stu-id="e3626-248">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="e3626-249">Кроме того, некоторые устройства могут требовать дополнительное поле для указания того, насколько область буфера заполнена данными.</span><span class="sxs-lookup"><span data-stu-id="e3626-249">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="e3626-250">Преимущества буферизованного ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="e3626-250">Buffered I/O Advantage</span></span> 
<span data-ttu-id="e3626-251">Каковы преимуществ схемы ввода-вывода с буфером?</span><span class="sxs-lookup"><span data-stu-id="e3626-251">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="e3626-252">Основное преимущество — данные не копируются между регистрами устройства и памятью приложения.</span><span class="sxs-lookup"><span data-stu-id="e3626-252">The biggest advantage is that data is not copied between the device registers and the application’s memory.</span></span> <span data-ttu-id="e3626-253">Вместо этого драйвер предоставляет устройству серию указателей на буфер.</span><span class="sxs-lookup"><span data-stu-id="e3626-253">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="e3626-254">Операции ввода-вывода физического устройства используют предоставляемую память буфера напрямую.</span><span class="sxs-lookup"><span data-stu-id="e3626-254">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="e3626-255">Использование процессора для копирования входящих или исходящих пакетов данных требует большого объема ресурсов, поэтому этого следует избегать в любых ситуациях ввода-вывода с высокой пропускной способностью.</span><span class="sxs-lookup"><span data-stu-id="e3626-255">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="e3626-256">Еще одно преимущество подхода с буферизацией ввода-вывода заключается в том, что списки входных и выходных данных не имеют условий заполнения.</span><span class="sxs-lookup"><span data-stu-id="e3626-256">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="e3626-257">Все доступные буферы могут в отдельный момент времени работать с любым списком.</span><span class="sxs-lookup"><span data-stu-id="e3626-257">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="e3626-258">Этим они отличаются от простых байтовых циклических буферов, представленных ранее в этой главе.</span><span class="sxs-lookup"><span data-stu-id="e3626-258">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="e3626-259">Каждый из них имеет фиксированный размер, определяемый при компиляции.</span><span class="sxs-lookup"><span data-stu-id="e3626-259">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="e3626-260">Задачи буферизованного драйвера</span><span class="sxs-lookup"><span data-stu-id="e3626-260">Buffered Driver Responsibilities</span></span> 
<span data-ttu-id="e3626-261">Буферизованные драйверы устройства выполняют только управление связанными списками буферов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e3626-261">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="e3626-262">Список буфера входных данных поддерживается для пакетов, которые принимаются до того, как ПО приложения готово их обработать.</span><span class="sxs-lookup"><span data-stu-id="e3626-262">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="e3626-263">А список буфера выходных данных поддерживается для пакетов, которые отправляются быстрее, чем аппаратное устройством может обработать их.</span><span class="sxs-lookup"><span data-stu-id="e3626-263">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="e3626-264">На рис. 15 на стр. 314 показаны простые связанные списки входных и выходных данных для пакетов и буферы, образующие каждый пакет.</span><span class="sxs-lookup"><span data-stu-id="e3626-264">Figure 15 on page 314 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

![Задачи буферизованного драйвера](media/image11.png)

<span data-ttu-id="e3626-266">**Рис. 15. Списки входных и выходных данных**</span><span class="sxs-lookup"><span data-stu-id="e3626-266">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="e3626-267">Приложения взаимодействуют с буферизованными драйверами с аналогичными буферами ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e3626-267">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="e3626-268">При передаче данных ПО приложения предоставляет драйвер с одним или несколькими передаваемыми буферами.</span><span class="sxs-lookup"><span data-stu-id="e3626-268">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="e3626-269">Если ПО приложения запрашивает входные данные, драйвер возвращает входные данные в буферах ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="e3626-269">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3626-270">В некоторых приложениях может быть полезнее создать интерфейс входных данных драйвера, который будет требовать от приложения заменить свободный буфер на буфер входных данных от драйвера.</span><span class="sxs-lookup"><span data-stu-id="e3626-270">In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver.</span></span> <span data-ttu-id="e3626-271">Это может упростить некоторую обработку выделения буфера в драйвере.</span><span class="sxs-lookup"><span data-stu-id="e3626-271">This might alleviate some buffer allocation processing inside of the driver.</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="e3626-272">Управление прерываниями</span><span class="sxs-lookup"><span data-stu-id="e3626-272">Interrupt Management</span></span> 
<span data-ttu-id="e3626-273">В некоторых приложениях частота прерываний устройства может препятствовать написанию обработчика прерываний на C или взаимодействию со ThreadX SMP при каждом прерывании.</span><span class="sxs-lookup"><span data-stu-id="e3626-273">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX SMP on each interrupt.</span></span> <span data-ttu-id="e3626-274">Например, если для сохранения и восстановления прерванного контекста требуется 25 мкс, не рекомендуется выполнять сохранение полного контекста, если частота прерывания составляла 50 мкс.</span><span class="sxs-lookup"><span data-stu-id="e3626-274">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="e3626-275">В таких случаях для обработки большинства прерываний устройства используется обработчик прерываний языка в компактной сборке.</span><span class="sxs-lookup"><span data-stu-id="e3626-275">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="e3626-276">Такой нетребовательный к ресурсам обработчик будет взаимодействовать со ThreadX SMP только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="e3626-276">This lowoverhead ISR would only interact with ThreadX SMP when necessary.</span></span>

<span data-ttu-id="e3626-277">Подробное обсуждение можно найти в описании управления прерываниями в конце главы 3.</span><span class="sxs-lookup"><span data-stu-id="e3626-277">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

> [!NOTE]
> <span data-ttu-id="e3626-278">Если для защиты критически важных разделов в коде драйвера от кода обработчика прерываний драйвера используется блокировка прерываний, код драйвера на уровне потока должен всегда выполняться на том же ядре, на котором выполняется обработчик прерываний.</span><span class="sxs-lookup"><span data-stu-id="e3626-278">If interrupt lockout is to be used to protect critical sections of driver code from driver ISR code, the thread level driver code must always execute on the same core that the ISR is processed on.</span></span> <span data-ttu-id="e3626-279">В противном случае необходимо использовать примитивы ThreadX SMP, например TX_DISABLE и TX_RESTORE, которые также имеют встроенную защиту от перехода на другие ядра.</span><span class="sxs-lookup"><span data-stu-id="e3626-279">Otherwise, internal ThreadX SMP primitives like TX_DISABLE and TX_RESTORE should be used that also have inter-core protection built-in.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="e3626-280">Приостановка потока</span><span class="sxs-lookup"><span data-stu-id="e3626-280">Thread Suspension</span></span> 
<span data-ttu-id="e3626-281">В простом примере драйвера, представленном ранее в этой главе, вызывающий компонент службы ввода приостанавливает работу, если символ недоступен.</span><span class="sxs-lookup"><span data-stu-id="e3626-281">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="e3626-282">Для некоторых приложений это может быть недопустимым.</span><span class="sxs-lookup"><span data-stu-id="e3626-282">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="e3626-283">Например, если поток, отвечающий за обработку входных данных от драйвера, также выполняет другие задачи, приостановка только приема данных драйвером может не сработать.</span><span class="sxs-lookup"><span data-stu-id="e3626-283">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="e3626-284">В таком случае для драйвера необходимо настроить отправку запроса на обработку так же, как и отправку других запросов на обработку в поток.</span><span class="sxs-lookup"><span data-stu-id="e3626-284">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="e3626-285">В большинстве случаев это означает создание буфера ввода для связанного списка и отправку входящего сообщения о событии во входную очередь потока.</span><span class="sxs-lookup"><span data-stu-id="e3626-285">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread’s input queue.</span></span>