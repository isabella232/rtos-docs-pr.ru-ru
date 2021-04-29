---
title: Глава 5. Драйверы устройств для ОСРВ Azure ThreadX
description: В этой главе приводится описание драйверов устройств для ОСРВ Azure ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2432b291f2b3fa7d6d798b8b4c187dd20b97db6b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815624"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx"></a><span data-ttu-id="5d3f3-103">Глава 5. Драйверы устройств для ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="5d3f3-103">Chapter 5 - Device Drivers for Azure RTOS ThreadX</span></span>

<span data-ttu-id="5d3f3-104">В этой главе приводится описание драйверов устройств для ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-104">This chapter contains a description of device drivers for Azure RTOS ThreadX.</span></span> <span data-ttu-id="5d3f3-105">Сведения, представленные в этой главе, призваны помочь разработчикам при написании драйверов для конкретных приложений.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-105">The information presented in this chapter is designed to help developers write application-specific drivers.</span></span>

## <a name="device-driver-introduction"></a><span data-ttu-id="5d3f3-106">Основные сведения о драйверах устройств</span><span class="sxs-lookup"><span data-stu-id="5d3f3-106">Device Driver Introduction</span></span>

<span data-ttu-id="5d3f3-107">Связь с внешней средой — это важная составляющая большинства встраиваемых приложений.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-107">Communication with the external environment is an important component of most embedded applications.</span></span> <span data-ttu-id="5d3f3-108">Такая связь осуществляется с помощью аппаратных устройств, доступных ПО встраиваемых приложений.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-108">This communication is accomplished through hardware devices that are accessible to the embedded application software.</span></span> <span data-ttu-id="5d3f3-109">Программные компоненты, которые отвечают за управление такими устройствами, обычно называются *драйверами*.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-109">The software components responsible for managing such devices are commonly called *device drivers*.</span></span>

<span data-ttu-id="5d3f3-110">Драйверы устройств представляют собой встраиваемые работающие в реальном времени системы, которые по своей природе зависимы от приложения.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-110">Device drivers in embedded, real-time systems are inherently application dependent.</span></span> <span data-ttu-id="5d3f3-111">Это так по двум основным причинам: невероятное разнообразие целевого оборудования и настолько же широкие требования к производительности, предъявляемые к работающим в реальном времени приложениям.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-111">This is true for two principal reasons: the vast diversity of target hardware and the equally vast performance requirements imposed on real-time applications.</span></span> <span data-ttu-id="5d3f3-112">Поэтому практически невозможно предоставить общий набор драйверов, удовлетворяющих требованиям любого приложения.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-112">Because of this, it is virtually impossible to provide a common set of drivers that will meet the requirements of every application.</span></span> <span data-ttu-id="5d3f3-113">В связи с этим сведения в этой главе призваны помочь пользователям настроить *стандартные* драйверы устройств ThreadX и написать собственные драйверы.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-113">For these reasons, the information in this chapter is designed to help users customize *off-the-shelf* ThreadX device drivers and write their own specific drivers.</span></span>

## <a name="driver-functions"></a><span data-ttu-id="5d3f3-114">Функции драйверов</span><span class="sxs-lookup"><span data-stu-id="5d3f3-114">Driver Functions</span></span>

<span data-ttu-id="5d3f3-115">Драйверы устройств ThreadX реализуют восемь основных выполняемых функций:</span><span class="sxs-lookup"><span data-stu-id="5d3f3-115">ThreadX device drivers are composed of eight basic functional areas, as follows.</span></span>

- <span data-ttu-id="5d3f3-116">**Инициализация драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-116">**Driver Initialization**</span></span>
- <span data-ttu-id="5d3f3-117">**Управление драйвером**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-117">**Driver Control**</span></span>
- <span data-ttu-id="5d3f3-118">**Доступ к драйверу**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-118">**Driver Access**</span></span>
- <span data-ttu-id="5d3f3-119">**Получение данных драйвером**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-119">**Driver Input**</span></span>
- <span data-ttu-id="5d3f3-120">**Вывод данных драйвером**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-120">**Driver Output**</span></span>
- <span data-ttu-id="5d3f3-121">**Прерывания драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-121">**Driver Interrupts**</span></span>
- <span data-ttu-id="5d3f3-122">**Состояние драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-122">**Driver Status**</span></span>
- <span data-ttu-id="5d3f3-123">**Завершение работы драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-123">**Driver Termination**</span></span>

<span data-ttu-id="5d3f3-124">За исключением инициализации, каждая из таких выполняемых функций является необязательной.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-124">With the exception of initialization, each driver functional area is optional.</span></span> <span data-ttu-id="5d3f3-125">Более того, обработка каждой выполняемой функции зависит от драйвера устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-125">Furthermore, the exact processing in each area is specific to the device driver.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="5d3f3-126">Инициализация драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-126">Driver Initialization</span></span>
<span data-ttu-id="5d3f3-127">Эта выполняемая функция отвечает за инициализацию реального аппаратного устройства и внутренних структур данных драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-127">This functional area is responsible for initialization of the actual hardware device and the internal data structures of the driver.</span></span> <span data-ttu-id="5d3f3-128">Вызов других служб драйвера невозможен, пока не завершится этап инициализации.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-128">Calling other driver services is not allowed until initialization is complete.</span></span>

> [!NOTE]
> <span data-ttu-id="5d3f3-129">\*Компонент функции для инициализации драйвера обычно вызывается из функции \***tx_application_define** _ или из потока инициализации._</span><span class="sxs-lookup"><span data-stu-id="5d3f3-129">\*The driver's initialization function component is typically called from the \***tx_application_define** _ function or from an initialization thread._</span></span>

### <a name="driver-control"></a><span data-ttu-id="5d3f3-130">Управление драйвером</span><span class="sxs-lookup"><span data-stu-id="5d3f3-130">Driver Control</span></span>

<span data-ttu-id="5d3f3-131">После того как драйвер будет инициализирован и готов к работе, эта функция отвечает за управление им во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-131">After the driver is initialized and ready for operation, this functional area is responsible for run-time control.</span></span> <span data-ttu-id="5d3f3-132">Обычно управление во время выполнения заключается в реализации изменений в работе базового аппаратного устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-132">Typically, run-time control consists of making changes to the underlying hardware device.</span></span> <span data-ttu-id="5d3f3-133">Например, это может быть изменение скорости передачи (бит/с) для устройства с последовательным интерфейсом или поиск нового сектора на диске.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-133">Examples include changing the baud rate of a serial device or seeking a new sector on a disk.</span></span>

### <a name="driver-access"></a><span data-ttu-id="5d3f3-134">Доступ к драйверу</span><span class="sxs-lookup"><span data-stu-id="5d3f3-134">Driver Access</span></span>

<span data-ttu-id="5d3f3-135">Некоторые драйверы устройств вызываются только из одного потока приложения.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-135">Some device drivers are called only from a single application thread.</span></span> <span data-ttu-id="5d3f3-136">В таких случаях эту функцию выполнять не требуется.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-136">In such cases, this functional area is not needed.</span></span> <span data-ttu-id="5d3f3-137">Но в приложениях, в которых к драйверу требуется одновременный доступ из нескольких потоков, их взаимодействием можно управлять с помощью средств назначения и освобождения в драйвере устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-137">However, in applications where multiple threads need simultaneous driver access, their interaction must be controlled by adding assign/ release facilities in the device driver.</span></span> <span data-ttu-id="5d3f3-138">Приложение также может использовать семафор для управления доступом к драйверу и таким образом избежать излишней нагрузки на ресурсы и усложнения кода в драйвере.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-138">Alternatively, the application may use a semaphore to control driver access and avoid extra overhead and complication inside the driver.</span></span>

### <a name="driver-input"></a><span data-ttu-id="5d3f3-139">Получение данных драйвером</span><span class="sxs-lookup"><span data-stu-id="5d3f3-139">Driver Input</span></span>

<span data-ttu-id="5d3f3-140">Эта функция отвечает за все операции ввода данных на устройстве.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-140">This functional area is responsible for all device input.</span></span> <span data-ttu-id="5d3f3-141">Основные проблемы, связанные с получением данных драйвером, обычно касаются способов буферизации входных данных и их ожидания потоками.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-141">The principal issues associated with driver input usually involve how the input is buffered and how threads wait for such input.</span></span>

### <a name="driver-output"></a><span data-ttu-id="5d3f3-142">Вывод данных драйвером</span><span class="sxs-lookup"><span data-stu-id="5d3f3-142">Driver Output</span></span>

<span data-ttu-id="5d3f3-143">Эта выполняемая функция отвечает за обработку всех выходных данных устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-143">This functional area is responsible for all device output.</span></span> <span data-ttu-id="5d3f3-144">Основные проблемы, связанные с выводом данных драйвером, обычно касаются способов буферизации выходных данных и их ожидания потоками.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-144">The principal issues associated with driver output usually involve how the output is buffered and how threads wait to perform output.</span></span>

### <a name="driver-interrupts"></a><span data-ttu-id="5d3f3-145">Прерывания драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-145">Driver Interrupts</span></span>

<span data-ttu-id="5d3f3-146">Большинство систем, работающих в реальном времени, используют аппаратные прерывания для уведомления драйвера о событиях ввода, вывода, управления и ошибок на устройстве.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-146">Most real-time systems rely on hardware interrupts to notify the driver of device input, output, control, and error events.</span></span> <span data-ttu-id="5d3f3-147">Прерывания предоставляют таким внешним событиям гарантированное время отклика.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-147">Interrupts provide a guaranteed response time to such external events.</span></span> <span data-ttu-id="5d3f3-148">Вместо прерываний ПО драйвера может периодически проверять наличие таких событий на внешнем оборудовании.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-148">Instead of interrupts, the driver software may periodically check the external hardware for such events.</span></span> <span data-ttu-id="5d3f3-149">Такая методика называется *опросом*.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-149">This technique is called *polling*.</span></span> <span data-ttu-id="5d3f3-150">Так как она предъявляет меньше требований к обработке в реальном времени, опросы могут лучше подходить для соответствующих приложений.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-150">It is less real-time than interrupts, but polling may make sense for some less real-time applications.</span></span>

### <a name="driver-status"></a><span data-ttu-id="5d3f3-151">Состояние драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-151">Driver Status</span></span>

<span data-ttu-id="5d3f3-152">Эта выполняемая функция отвечает за предоставление данных о состоянии и статистики среды выполнения, связанных с работой драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-152">This function area is responsible for providing run-time status and statistics associated with the driver operation.</span></span> <span data-ttu-id="5d3f3-153">Сведения, которые обрабатывает эта функция, обычно включают следующую информацию:</span><span class="sxs-lookup"><span data-stu-id="5d3f3-153">Information managed by this function area typically includes the following.</span></span>

- <span data-ttu-id="5d3f3-154">Текущее состояние устройства</span><span class="sxs-lookup"><span data-stu-id="5d3f3-154">Current device status</span></span>
- <span data-ttu-id="5d3f3-155">Входные байты</span><span class="sxs-lookup"><span data-stu-id="5d3f3-155">Input bytes</span></span>
- <span data-ttu-id="5d3f3-156">Выходные байты</span><span class="sxs-lookup"><span data-stu-id="5d3f3-156">Output bytes</span></span>
- <span data-ttu-id="5d3f3-157">Число ошибок устройства</span><span class="sxs-lookup"><span data-stu-id="5d3f3-157">Device error counts</span></span>

### <a name="driver-termination"></a><span data-ttu-id="5d3f3-158">Завершение работы драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-158">Driver Termination</span></span>

<span data-ttu-id="5d3f3-159">Эта выполняемая функция необязательна.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-159">This functional area is optional.</span></span> <span data-ttu-id="5d3f3-160">Она необходима только в том случае, если необходимо завершить работу драйвера и (или) физического аппаратного устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-160">It is only required if the driver and/or the physical hardware device need to be shut down.</span></span> <span data-ttu-id="5d3f3-161">После завершения работы драйвер нельзя вызвать, пока он не будет повторно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-161">After being terminated, the driver must not be called again until it is reinitialized.</span></span>

## <a name="simple-driver-example"></a><span data-ttu-id="5d3f3-162">Пример простого драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-162">Simple Driver Example</span></span>

<span data-ttu-id="5d3f3-163">Пример позволяет лучше понять, как работает драйвер устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-163">An example is the best way to describe a device driver.</span></span> <span data-ttu-id="5d3f3-164">В этом примере для драйвера предполагается простое аппаратное устройство с последовательным интерфейсом, с регистром конфигурации, регистрами входных и выходных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-164">In this example, the driver assumes a simple serial hardware device with a configuration register, an input register, and an output register.</span></span> <span data-ttu-id="5d3f3-165">Этот пример простого драйвера демонстрирует выполнение функций инициализации, ввода данных, вывода данных и прерываний.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-165">This simple driver example illustrates the initialization, input, output, and interrupt functional areas.</span></span>

### <a name="simple-driver-initialization"></a><span data-ttu-id="5d3f3-166">Инициализация простого драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-166">Simple Driver Initialization</span></span>

<span data-ttu-id="5d3f3-167">Функция ***tx_sdriver_initialize*** простого драйвера создает два вычислительных семафора, которые используются для управления операциями с входными и выходными данными драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-167">The ***tx_sdriver_initialize*** function of the simple driver creates two counting semaphores that are used to manage the driver's input and output operation.</span></span> <span data-ttu-id="5d3f3-168">Семафор входных данных задается обработчиком прерываний входных данных, когда аппаратное устройство с последовательным интерфейсом получает символ.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-168">The input semaphore is set by the input ISR when a character is received by the serial hardware device.</span></span> <span data-ttu-id="5d3f3-169">По этой причине семафор ввода создается со счетчиком, имеющим значение 0.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-169">Because of this, the input semaphore is created with an initial count of zero.</span></span>

<span data-ttu-id="5d3f3-170">И наоборот, семафор вывода указывает на доступность регистра передачи для оборудования с последовательным интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-170">Conversely, the output semaphore indicates the availability of the serial hardware transmit register.</span></span> <span data-ttu-id="5d3f3-171">Он создается со значением 1, чтобы указать на первоначальную доступность регистра передачи.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-171">It is created with a value of one to indicate the transmit register is initially available.</span></span>

<span data-ttu-id="5d3f3-172">Функция инициализации также отвечает за установку обработчиков векторов прерывания низкого уровня для уведомлений входных и выходных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-172">The initialization function is also responsible for installing the low-level interrupt vector handlers for input and output notifications.</span></span> <span data-ttu-id="5d3f3-173">Как и другие подпрограммы службы прерываний ThreadX, обработчик низкого уровня должен вызвать \* **_tx_thread_context_save** _ до вызова обработчика прерываний простого драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-173">Like other ThreadX interrupt service routines, the low-level handler must call \***_tx_thread_context_save** _ before calling the simple driver ISR.</span></span> <span data-ttu-id="5d3f3-174">После того как обработчик прерываний драйвера будет возвращен, обработчик низкого уровня должен вызвать _\*_ _tx_thread_context_restore_\*\*.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-174">After the driver ISR returns, the low-level handler must call _\*_ _tx_thread_context_restore_\*\*.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d3f3-175">\* Важно, чтобы инициализация была вызвана до любых других функций драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-175">\*It is important that initialization is called before any of the other driver functions.</span></span> <span data-ttu-id="5d3f3-176">Обычно инициализация драйвера вызывается из функции ***tx_application_define***.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-176">Typically, driver initialization is called from ***tx_application_define***.</span></span>

```c
VOID tx_sdriver_initialize(VOID)
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
<span data-ttu-id="5d3f3-177">**РИС. 9. Инициализация простого драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-177">**FIGURE 9. Simple Driver Initialization**</span></span>

### <a name="simple-driver-input"></a><span data-ttu-id="5d3f3-178">Входные данные простого драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-178">Simple Driver Input</span></span>

<span data-ttu-id="5d3f3-179">Входные данные для простого драйвера управляются семафором ввода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-179">Input for the simple driver centers around the input semaphore.</span></span> <span data-ttu-id="5d3f3-180">При получении прерывания входных данных устройства задается семафор ввода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-180">When a serial device input interrupt is received, the input semaphore is set.</span></span> <span data-ttu-id="5d3f3-181">Если один или несколько потоков ожидают получения символа от драйвера, работу продолжает поток с наибольшим временем ожидания.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-181">If one or more threads are waiting for a character from the driver, the thread waiting the longest is resumed.</span></span> <span data-ttu-id="5d3f3-182">Если работают все потоки, семафор сохраняется до того момента, пока поток не вызовет функцию ввода драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-182">If no threads are waiting, the semaphore simply remains set until a thread calls the drive input function.</span></span>

<span data-ttu-id="5d3f3-183">Существует несколько ограничений при обработке входных данных простым драйвером.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-183">There are several limitations to the simple driver input handling.</span></span> <span data-ttu-id="5d3f3-184">Самое значительное — возможность удаления символов входных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-184">The most significant is the potential for dropping input characters.</span></span> <span data-ttu-id="5d3f3-185">Это возможно, так как нельзя выполнить буферизацию символов входных данных, которые принимаются до завершения обработки предыдущего символа.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-185">This is possible because there is no ability to buffer input characters that arrive before the previous character is processed.</span></span> <span data-ttu-id="5d3f3-186">Эта проблема легко решается путем добавления буфера символов входных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-186">This is easily handled by adding an input character buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="5d3f3-187">*Вызывать функцию*  ***tx_sdriver_input** _ _ могут только потоки*.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-187">*Only threads are allowed to call the* ***tx_sdriver_input** _ _function.*</span></span>

<span data-ttu-id="5d3f3-188">На рис. 10 приведен исходный код, связанный с входными данными простого драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-188">Figure 10 shows the source code associated with simple driver input.</span></span>

```c
UCHAR tx_sdriver_input(VOID)
{
  /* Determine if there is a character waiting. If not,
  suspend. */
  tx_semaphore_get(&tx_sdriver_input_semaphore,
  TX_WAIT_FOREVER;

  /* Return character from serial RX hardware register. */
  return(*serial_hardware_input_ptr);
}
  VOID tx_sdriver_input_ISR(VOID)
{
  /* See if an input character notification is pending. */
  if (!tx_sdriver_input_semaphore.tx_semaphore_count)
  {
    /* If not, notify thread of an input character. */
    tx_semaphore_put(&tx_sdriver_input_semaphore);
  }
}
```
<span data-ttu-id="5d3f3-189">**РИС. 10. Входные данные простого драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-189">**FIGURE 10. Simple Driver Input**</span></span>

### <a name="simple-driver-output"></a><span data-ttu-id="5d3f3-190">Выходные данные простого драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-190">Simple Driver Output</span></span>

<span data-ttu-id="5d3f3-191">При обработке выходных данных используется семафор вывода для уведомления о том, что регистр передачи устройства с последовательным интерфейсом освободился.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-191">Output processing utilizes the output semaphore to signal when the serial device's transmit register is free.</span></span> <span data-ttu-id="5d3f3-192">Перед фактической записью символа выходных данных на устройство выполняется получение семафора вывода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-192">Before an output character is actually written to the device, the output semaphore is obtained.</span></span> <span data-ttu-id="5d3f3-193">Если он недоступен, возможно, предыдущая операция передачи еще не завершена.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-193">If it is not available, the previous transmit is not yet complete.</span></span>

<span data-ttu-id="5d3f3-194">Обработчик прерываний выходных данных отвечает за обработку прерывания завершения при передаче.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-194">The output ISR is responsible for handling the transmit complete interrupt.</span></span> <span data-ttu-id="5d3f3-195">Его операции заключаются в установке семафора вывода, что позволяет выполнить вывод другого символа.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-195">Processing of the output ISR amounts to setting the output semaphore, thereby allowing output of another character.</span></span>

> [!NOTE]
> <span data-ttu-id="5d3f3-196">*Вызывать функцию*  ***tx_sdriver_output** _ _ могут только потоки*.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-196">*Only threads are allowed to call the* ***tx_sdriver_output** _ _function.*</span></span>

<span data-ttu-id="5d3f3-197">На рис. 11 приведен исходный код, связанный с выходными данными простого драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-197">Figure 11 shows the source code associated with simple driver output.</span></span>

```c
VOID tx_sdriver_output(UCHAR alpha)
{
  /* Determine if the hardware is ready to transmit a
  character. If not, suspend until the previous output
  completes. */
  tx_semaphore_get(&tx_sdriver_output_semaphore,
                                          TX_WAIT_FOREVER);

  /* Send the character through the hardware. */
  *serial_hardware_output_ptr = alpha;
}
  
VOID tx_sdriver_output_ISR(VOID)
{
  /* Notify thread last character transmit is
  complete. */
  tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
<span data-ttu-id="5d3f3-198">**РИС. 11. Выходные данные простого драйвера**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-198">**FIGURE 11. Simple Driver Output**</span></span>

### <a name="simple-driver-shortcomings"></a><span data-ttu-id="5d3f3-199">Недостатки простого драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-199">Simple Driver Shortcomings</span></span>

<span data-ttu-id="5d3f3-200">Этот пример простого драйвера устройства иллюстрирует принцип работы драйвера с ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-200">This simple device driver example illustrates the basic idea of a ThreadX device driver.</span></span> <span data-ttu-id="5d3f3-201">Но так как в этом простом драйвере устройства не устранены проблемы с буферизацией данных или излишней нагрузкой на ресурсы, он не полностью эквивалентен реальным драйверам с ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-201">However, because the simple device driver does not address data buffering or any overhead issues, it does not fully represent real-world ThreadX drivers.</span></span> <span data-ttu-id="5d3f3-202">В разделе ниже описаны некоторые более сложные проблемы, связанные с драйверами устройств.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-202">The following section describes some of the more advanced issues associated with device drivers.</span></span>

## <a name="advanced-driver-issues"></a><span data-ttu-id="5d3f3-203">Сложные проблемы с драйверами</span><span class="sxs-lookup"><span data-stu-id="5d3f3-203">Advanced Driver Issues</span></span>

<span data-ttu-id="5d3f3-204">Как было сказано ранее, требования драйверов устройств аналогичны требованиям их приложений.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-204">As mentioned previously, device drivers have requirements as unique as their applications.</span></span> <span data-ttu-id="5d3f3-205">Некоторым приложениям может требоваться выполнять буферизацию огромного объема данных, а другие приложения могут нуждаться в оптимизированном обработчике прерываний драйвера из-за высокой частоты прерываний устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-205">Some applications may require an enormous amount of data buffering while another application may require optimized driver ISRs because of high-frequency device interrupts.</span></span>

### <a name="io-buffering"></a><span data-ttu-id="5d3f3-206">Буферизация ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="5d3f3-206">I/O Buffering</span></span>

<span data-ttu-id="5d3f3-207">Буферизация данных во встраиваемых приложениях, работающих в реальном времени, требует тщательного планирования.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-207">Data buffering in real-time embedded applications requires considerable planning.</span></span> <span data-ttu-id="5d3f3-208">В некоторых случаях его реализация будет зависеть от базового аппаратного устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-208">Some of the design is dictated by the underlying hardware device.</span></span> <span data-ttu-id="5d3f3-209">Если устройство предоставляет базовый побайтовый ввод-вывод, вероятно, имеет смысл добавить простой циклический буфер.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-209">If the device provides basic byte I/O, a simple circular buffer is probably in order.</span></span> <span data-ttu-id="5d3f3-210">Но если устройство предоставляет блочный, пакетный ввод-вывод или ввод-вывод с прямым доступом к памяти, более оптимально будет использовать схему управления буфером.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-210">However, if the device provides block, DMA, or packet I/O, a buffer management scheme is probably warranted.</span></span>

### <a name="circular-byte-buffers"></a><span data-ttu-id="5d3f3-211">Циклические байтовые буферы</span><span class="sxs-lookup"><span data-stu-id="5d3f3-211">Circular Byte Buffers</span></span>

<span data-ttu-id="5d3f3-212">Циклические байтовые буферы обычно используются в драйверах, которые управляют простым аппаратным устройством с последовательным интерфейсом, например UART.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-212">Circular byte buffers are typically used in drivers that manage a simple serial hardware device like a UART.</span></span> <span data-ttu-id="5d3f3-213">В таких ситуациях чаще всего используются два циклических буфера — один для входных, а другой для выходных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-213">Two circular buffers are most often used in such situations—one for input and one for output.</span></span>

<span data-ttu-id="5d3f3-214">Каждый циклический байтовый буфер состоит из байтовой области памяти (обычно это массив из **UCHAR**), указателя на чтение и указателя на запись.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-214">Each circular byte buffer is comprised of a byte memory area (typically an array of **UCHAR** s), a read pointer, and a write pointer.</span></span> <span data-ttu-id="5d3f3-215">Буфер считается пустым, если указатель на чтение и указатели на запись ссылаются на одно расположение памяти в буфере.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-215">A buffer is considered empty when the read pointer and the write pointers reference the same memory location in the buffer.</span></span> <span data-ttu-id="5d3f3-216">Инициализация драйвера задает для указателей буфера на чтение и запись расположение в начальном адресе буфера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-216">Driver initialization sets both the read and write buffer pointers to the beginning address of the buffer.</span></span>

### <a name="circular-buffer-input"></a><span data-ttu-id="5d3f3-217">Входные данные циклического буфера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-217">Circular Buffer Input</span></span>

<span data-ttu-id="5d3f3-218">Буфер ввода используется для хранения символов, которые приложение еще не готово обработать.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-218">The input buffer is used to hold characters that arrive before the application is ready for them.</span></span> <span data-ttu-id="5d3f3-219">При получении символа входных данных (обычно в обработчике прерываний) от аппаратного устройства принимается новый символ и помещается в буфер ввода в расположении, на которое ссылается указатель на запись.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-219">When an input character is received (usually in an interrupt service routine), the new character is retrieved from the hardware device and placed into the input buffer at the location pointed to by the write pointer.</span></span> <span data-ttu-id="5d3f3-220">Затем указатель на запись перемещается на следующую позицию в буфере.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-220">The write pointer is then advanced to the next position in the buffer.</span></span> <span data-ttu-id="5d3f3-221">Если следующая позиция находится за пределами буфера, указатель на запись устанавливается на начало буфера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-221">If the next position is past the end of the buffer, the write pointer is set to the beginning of the buffer.</span></span> <span data-ttu-id="5d3f3-222">Условие заполнения очереди обрабатывается путем отмены перемещения указателя на запись, если новый указатель на запись не отличается от указателя на чтение.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-222">The queue full condition is handled by canceling the write pointer advancement if the new write pointer is the same as the read pointer.</span></span>

<span data-ttu-id="5d3f3-223">Побайтовые запросы к входным данным приложения, направляемые драйверу, сначала проверяют указатели на чтение и запись буфера ввода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-223">Application input byte requests to the driver first examine the read and write pointers of the input buffer.</span></span> <span data-ttu-id="5d3f3-224">Если указатели на чтение и запись идентичны, это означает, что буфер пуст.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-224">If the read and write pointers are identical, the buffer is empty.</span></span> <span data-ttu-id="5d3f3-225">Если же указатель на чтение отличается, байт, на который ссылается указатель на чтение, копируется из буфера ввода, а указатель на чтение перемещается на следующее расположение в буфере.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-225">Otherwise, if the read pointer is not the same, the byte pointed to by the read pointer is copied from the input buffer and the read pointer is advanced to the next buffer location.</span></span> <span data-ttu-id="5d3f3-226">Если новый указатель на чтение выходит за пределы буфера, он сбрасывается на начало.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-226">If the new read pointer is past the end of the buffer, it is reset to the beginning.</span></span> <span data-ttu-id="5d3f3-227">На рис. 12 приведена логика для циклического буфера ввода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-227">Figure 12 shows the logic for the circular input buffer.</span></span>

```c
UCHAR   tx_input_buffer[MAX_SIZE];
UCHAR   tx_input_write_ptr;
UCHAR   tx_input_read_ptr;

/* Initialization. */
tx_input_write_ptr =    &tx_input_buffer[0];
tx_input_read_ptr =     &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr = tx_input_write_ptr;
*tx_input_write_ptr++ = alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr = &tx_input_buffer[0]; /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr = save_ptr; /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
  alpha = *tx_input_read_ptr++;
  if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
      tx_input_read_ptr = &tx_input_buffer[0];
}
```
<span data-ttu-id="5d3f3-228">**РИС. 12. Логика для циклического буфера ввода**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-228">**FIGURE 12. Logic for Circular Input Buffer**</span></span>

> [!NOTE]
> <span data-ttu-id="5d3f3-229">\*Для надежной работы может потребоваться заблокировать прерывания при изменении указателей на чтение и запись для циклических буферов ввода и вывода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-229">\*For reliable operation, it may be necessary to lockout interrupts when manipulating the read and write pointers of both the input and output circular buffers.</span></span> *

### <a name="circular-output-buffer"></a><span data-ttu-id="5d3f3-230">Циклический буфер вывода</span><span class="sxs-lookup"><span data-stu-id="5d3f3-230">Circular Output Buffer</span></span>

<span data-ttu-id="5d3f3-231">Буфер вывода используется для хранения символов, которые были приняты на вывод до того, как аппаратное устройство завершило отправку предыдущего байта.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-231">The output buffer is used to hold characters that have arrived for output before the hardware device finished sending the previous byte.</span></span> <span data-ttu-id="5d3f3-232">Обработка буфера вывода аналогична обработке для буфера ввода, за исключением того, что обработка прерывания завершения передачи используется с указателем на чтение выходных данных, а запрос выходных данных к приложению использует указатель на запись выходных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-232">Output buffer processing is similar to input buffer processing, except the transmit complete interrupt processing manipulates the output read pointer, while the application output request utilizes the output write pointer.</span></span>
<span data-ttu-id="5d3f3-233">В остальном обработка буфера вывода не отличается.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-233">Otherwise, the output buffer processing is the same.</span></span> <span data-ttu-id="5d3f3-234">На рис. 13 приведена логика для циклического буфера вывода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-234">Figure 13 shows the logic for the circular output buffer.</span></span>

```c
UCHAR   tx_output_buffer[MAX_SIZE];
UCHAR   tx_output_write_ptr;
UCHAR   tx_output_read_ptr;

/* Initialization. */
tx_output_write_ptr = &tx_output_buffer[0];
tx_output_read_ptr = &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
  *device_reg = *tx_output_read_ptr++;
  if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
      tx_output_read_ptr = &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr = tx_output_write_ptr;
*tx_output_write_ptr++ = alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr = &tx_output_buffer[0]; /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr = save_ptr; /* Buffer full! */
```
<span data-ttu-id="5d3f3-235">**РИС. 13. Логика для циклического буфера вывода**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-235">**FIGURE 13. Logic for Circular Output Buffer**</span></span>

### <a name="buffer-io-management"></a><span data-ttu-id="5d3f3-236">Управление вводом-выводом буфера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-236">Buffer I/O Management</span></span>

<span data-ttu-id="5d3f3-237">Для улучшения производительности внедренных микропроцессоров многие периферийные устройства передают и получают данные с помощью буферов, предоставляемых программным обеспечением.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-237">To improve the performance of embedded microprocessors, many peripheral device devices transmit and receive data with buffers supplied by software.</span></span> <span data-ttu-id="5d3f3-238">В некоторых реализациях могут использоваться несколько буферов для передачи или получения отдельных пакетов данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-238">In some implementations, multiple buffers may be used to transmit or receive individual packets of data.</span></span>

<span data-ttu-id="5d3f3-239">Размер и расположение буферов ввода-вывода определяются приложением и (или) ПО драйвера.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-239">The size and location of I/O buffers is determined by the application and/or driver software.</span></span> <span data-ttu-id="5d3f3-240">Обычно буферы имеют фиксированный размер и управляются в пуле блочной памяти ThreadX.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-240">Typically, buffers are fixed in size and managed within a ThreadX block memory pool.</span></span> <span data-ttu-id="5d3f3-241">На рис. 14 приведен типичный буфер ввода-вывода и пул блочной памяти ThreadX, который управляет их выделением.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-241">Figure 14 describes a typical I/O buffer and a ThreadX block memory pool that manages their allocation.</span></span>

```c
typedef struct TX_IO_BUFFER_STRUCT
{
      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
      struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR tx_buffer_area[TX_MAX_BUFFER_SIZE];
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

<span data-ttu-id="5d3f3-242">**РИС. 14. Буфер ввода-вывода**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-242">**FIGURE 14. I/O Buffer**</span></span>

### <a name="tx_io_buffer"></a><span data-ttu-id="5d3f3-243">TX_IO_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5d3f3-243">TX_IO_BUFFER</span></span>

<span data-ttu-id="5d3f3-244">typedef TX_IO_BUFFER состоит из двух указателей.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-244">The typedef TX_IO_BUFFER consists of two pointers.</span></span> <span data-ttu-id="5d3f3-245">Указатель **tx_next_packet** используется для связывания нескольких пакетов в списке входных или выходных данных.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-245">The **tx_next_packet** pointer is used to link multiple packets on either the input or output list.</span></span> <span data-ttu-id="5d3f3-246">Указатель **tx_next_buffer** используется для связывания буферов, которые составляют отдельный пакет данных от устройства.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-246">The **tx_next_buffer** pointer is used to link together buffers that make up an individual packet of data from the device.</span></span> <span data-ttu-id="5d3f3-247">Для обоих этих указателей задано значение NULL при выделении буфера из пула.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-247">Both of these pointers are set to NULL when the buffer is allocated from the pool.</span></span> <span data-ttu-id="5d3f3-248">Кроме того, некоторые устройства могут требовать дополнительное поле для указания того, насколько область буфера заполнена данными.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-248">In addition, some devices may require another field to indicate how much of the buffer area actually contains data.</span></span>

### <a name="buffered-io-advantage"></a><span data-ttu-id="5d3f3-249">Преимущества буферизованного ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="5d3f3-249">Buffered I/O Advantage</span></span>

<span data-ttu-id="5d3f3-250">Каковы преимуществ схемы ввода-вывода с буфером?</span><span class="sxs-lookup"><span data-stu-id="5d3f3-250">What are the advantages of a buffer I/O scheme?</span></span> <span data-ttu-id="5d3f3-251">Основное преимущество — данные не копируются между регистрами устройства и памятью приложения.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-251">The biggest advantage is that data is not copied between the device registers and the application's memory.</span></span> <span data-ttu-id="5d3f3-252">Вместо этого драйвер предоставляет устройству серию указателей на буфер.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-252">Instead, the driver provides the device with a series of buffer pointers.</span></span> <span data-ttu-id="5d3f3-253">Операции ввода-вывода физического устройства используют предоставляемую память буфера напрямую.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-253">Physical device I/O utilizes the supplied buffer memory directly.</span></span>

<span data-ttu-id="5d3f3-254">Использование процессора для копирования входящих или исходящих пакетов данных требует большого объема ресурсов, поэтому этого следует избегать в любых ситуациях ввода-вывода с высокой пропускной способностью.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-254">Using the processor to copy input or output packets of information is extremely costly and should be avoided in any high throughput I/O situation.</span></span>

<span data-ttu-id="5d3f3-255">Еще одно преимущество подхода с буферизацией ввода-вывода заключается в том, что списки входных и выходных данных не имеют условий заполнения.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-255">Another advantage to the buffered I/O approach is that the input and output lists do not have full conditions.</span></span> <span data-ttu-id="5d3f3-256">Все доступные буферы могут в отдельный момент времени работать с любым списком.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-256">All of the available buffers can be on either list at any one time.</span></span> <span data-ttu-id="5d3f3-257">Этим они отличаются от простых байтовых циклических буферов, представленных ранее в этой главе.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-257">This contrasts with the simple byte circular buffers presented earlier in the chapter.</span></span> <span data-ttu-id="5d3f3-258">Каждый из них имеет фиксированный размер, определяемый при компиляции.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-258">Each had a fixed size determined at compilation.</span></span>

### <a name="buffered-driver-responsibilities"></a><span data-ttu-id="5d3f3-259">Задачи буферизованного драйвера</span><span class="sxs-lookup"><span data-stu-id="5d3f3-259">Buffered Driver Responsibilities</span></span>

<span data-ttu-id="5d3f3-260">Буферизованные драйверы устройства выполняют только управление связанными списками буферов ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-260">Buffered device drivers are only concerned with managing linked lists of I/O buffers.</span></span> <span data-ttu-id="5d3f3-261">Список буфера ввода поддерживается для пакетов, которые принимаются до того, как ПО приложения готово их обработать.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-261">An input buffer list is maintained for packets that are received before the application software is ready.</span></span> <span data-ttu-id="5d3f3-262">А список буфера вывода поддерживается для пакетов, которые отправляются быстрее, чем аппаратное устройство может обработать их.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-262">Conversely, an output buffer list is maintained for packets being sent faster than the hardware device can handle them.</span></span> <span data-ttu-id="5d3f3-263">На рис. 15 показаны простые связанные списки входных и выходных данных для пакетов и буферы, образующие каждый пакет.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-263">Figure 15 shows simple input and output linked lists of data packets and the buffer(s) that make up each packet.</span></span>

<span data-ttu-id="5d3f3-264">**Список входных данных**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-264">**Input List**</span></span>

![Список входных данных](./media/user-guide/input-list.png)

<span data-ttu-id="5d3f3-266">**Итоговый список**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-266">**Output List**</span></span>

![Итоговый список](./media/user-guide/output-list.png)

<span data-ttu-id="5d3f3-268">**РИС. 15. Списки входных и выходных данных**</span><span class="sxs-lookup"><span data-stu-id="5d3f3-268">**FIGURE 15. Input-Output Lists**</span></span>

<span data-ttu-id="5d3f3-269">Приложения взаимодействуют с буферизованными драйверами с аналогичными буферами ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-269">Applications interface with buffered drivers with the same I/O buffers.</span></span> <span data-ttu-id="5d3f3-270">При передаче данных ПО приложения предоставляет драйвер с одним или несколькими передаваемыми буферами.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-270">On transmit, application software provides the driver with one or more buffers to transmit.</span></span> <span data-ttu-id="5d3f3-271">Если ПО приложения запрашивает входные данные, драйвер возвращает входные данные в буферах ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-271">When the application software requests input, the driver returns the input data in I/O buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="5d3f3-272">*В некоторых приложениях может быть полезнее создать интерфейс входных данных драйвера, который будет требовать от приложения заменить свободный буфер на буфер ввода от драйвера. Это может упростить некоторую обработку выделения буфера в драйвере.*</span><span class="sxs-lookup"><span data-stu-id="5d3f3-272">*In some applications, it may be useful to build a driver input interface that requires the application to exchange a free buffer for an input buffer from the driver. This might alleviate some buffer allocation processing inside of the driver.*</span></span>

### <a name="interrupt-management"></a><span data-ttu-id="5d3f3-273">Управление прерываниями</span><span class="sxs-lookup"><span data-stu-id="5d3f3-273">Interrupt Management</span></span>

<span data-ttu-id="5d3f3-274">В некоторых приложениях частота прерываний устройства может препятствовать написанию обработчика прерываний на C или взаимодействию с ThreadX при каждом прерывании.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-274">In some applications, the device interrupt frequency may prohibit writing the ISR in C or to interact with ThreadX on each interrupt.</span></span> <span data-ttu-id="5d3f3-275">Например, если для сохранения и восстановления прерванного контекста требуется 25 мкс, не рекомендуется выполнять сохранение полного контекста, если частота прерывания составляла 50 мкс.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-275">For example, if it takes 25us to save and restore the interrupted context, it would not be advisable to perform a full context save if the interrupt frequency was 50us.</span></span> <span data-ttu-id="5d3f3-276">В таких случаях для обработки большинства прерываний устройства используется обработчик прерываний языка в компактной сборке.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-276">In such cases, a small assembly language ISR is used to handle most of the device interrupts.</span></span> <span data-ttu-id="5d3f3-277">Такой нетребовательный к ресурсам обработчик будет взаимодействовать с ThreadX только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-277">This low-overhead ISR would only interact with ThreadX when necessary.</span></span>

<span data-ttu-id="5d3f3-278">Подробное обсуждение можно найти в описании управления прерываниями в конце главы 3.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-278">A similar discussion can be found in the interrupt management discussion at the end of Chapter 3.</span></span>

### <a name="thread-suspension"></a><span data-ttu-id="5d3f3-279">Приостановка потока</span><span class="sxs-lookup"><span data-stu-id="5d3f3-279">Thread Suspension</span></span>

<span data-ttu-id="5d3f3-280">В простом примере драйвера, представленном ранее в этой главе, вызывающий компонент службы ввода приостанавливает работу, если символ недоступен.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-280">In the simple driver example presented earlier in this chapter, the caller of the input service suspends if a character is not available.</span></span> <span data-ttu-id="5d3f3-281">Для некоторых приложений это может быть недопустимым.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-281">In some applications, this might not be acceptable.</span></span>

<span data-ttu-id="5d3f3-282">Например, если поток, отвечающий за обработку входных данных от драйвера, также выполняет другие задачи, приостановка только приема данных драйвером может не сработать.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-282">For example, if the thread responsible for processing input from a driver also has other duties, suspending on just the driver input is probably not going to work.</span></span> <span data-ttu-id="5d3f3-283">В таком случае для драйвера необходимо настроить отправку запроса на обработку так же, как и отправку других запросов на обработку в поток.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-283">Instead, the driver needs to be customized to request processing similar to the way other processing requests are made to the thread.</span></span>

<span data-ttu-id="5d3f3-284">В большинстве случаев это означает создание буфера ввода для связанного списка и отправку входящего сообщения о событии во входную очередь потока.</span><span class="sxs-lookup"><span data-stu-id="5d3f3-284">In most cases, the input buffer is placed on a linked list and an input event message is sent to the thread's input queue.</span></span>
