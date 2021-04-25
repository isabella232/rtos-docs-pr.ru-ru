---
title: Глава 6. Демонстрационная система ThreadX для ОСРВ Azure
description: В этой главе приведено описание демонстрационной системы, которая поставляется со всеми пакетами поддержки процессора ThreadX для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814355"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="1a7d8-103">Глава 6. Демонстрационная система ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="1a7d8-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="1a7d8-104">В этой главе приведено описание демонстрационной системы, которая поставляется со всеми пакетами поддержки процессора ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="1a7d8-105">Обзор</span><span class="sxs-lookup"><span data-stu-id="1a7d8-105">Overview</span></span>

<span data-ttu-id="1a7d8-106">Каждый дистрибутив продукта ThreadX включает демонстрационную систему, которая выполняется на всех поддерживаемых микропроцессорах.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="1a7d8-107">Этот пример системы определен в файле дистрибутива ***demo_threadx.c*** и предназначен для демонстрации того, как используется ThreadX во внедренной многопоточной среде.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="1a7d8-108">Эта демонстрация состоит из инициализации, восьми потоков, одного пула байтов, одного блочного пула, одной очереди, одного семафора, одного мьютекса и одной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="1a7d8-109">*За исключением размера стека потока, демонстрационное приложение идентично для всех процессоров, поддерживаемых ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="1a7d8-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="1a7d8-110">Полный листинг файла ***demo_threadx.c***, включая номера строк, которые упоминаются далее в этой главе.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="1a7d8-111">Определение приложения</span><span class="sxs-lookup"><span data-stu-id="1a7d8-111">Application Define</span></span>

<span data-ttu-id="1a7d8-112">Функция ***tx_application_define*** выполняется после завершения базовой инициализации ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="1a7d8-113">Она отвечает за настройку всех начальных системных ресурсов, включая потоки, очереди, семафоры, мьютексы, флаги событий и пулы памяти.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="1a7d8-114">Функция ***tx_application_define** _ (_строки 60–164*) демонстрационной системы создает демонстрационные объекты в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="1a7d8-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="1a7d8-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-115">byte_pool_0</span></span>
- <span data-ttu-id="1a7d8-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-116">thread_0</span></span>
- <span data-ttu-id="1a7d8-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="1a7d8-117">thread_1</span></span>
- <span data-ttu-id="1a7d8-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="1a7d8-118">thread_2</span></span>
- <span data-ttu-id="1a7d8-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="1a7d8-119">thread_3</span></span>
- <span data-ttu-id="1a7d8-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="1a7d8-120">thread_4</span></span>
- <span data-ttu-id="1a7d8-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="1a7d8-121">thread_5</span></span>
- <span data-ttu-id="1a7d8-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="1a7d8-122">thread_6</span></span>
- <span data-ttu-id="1a7d8-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="1a7d8-123">thread_7</span></span>
- <span data-ttu-id="1a7d8-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-124">queue_0</span></span>
- <span data-ttu-id="1a7d8-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-125">semaphore_0</span></span>
- <span data-ttu-id="1a7d8-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-126">event_flags_0</span></span>
- <span data-ttu-id="1a7d8-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-127">mutex_0</span></span>
- <span data-ttu-id="1a7d8-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-128">block_pool_0</span></span>

<span data-ttu-id="1a7d8-129">Демонстрационная система не создает каких-либо других дополнительных объектов ThreadX.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="1a7d8-130">Но реальное приложение может создавать системные объекты в потоках во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="1a7d8-131">Первоначальное выполнение</span><span class="sxs-lookup"><span data-stu-id="1a7d8-131">Initial Execution</span></span>

<span data-ttu-id="1a7d8-132">Все потоки создаются с параметром **TX_AUTO_START**.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="1a7d8-133">Это делает их изначально готовыми к выполнению.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="1a7d8-134">После завершения функции ***tx_application_define*** управление передается планировщику потоков, а затем каждому отдельному потоку.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="1a7d8-135">Порядок выполнения потоков определяется их приоритетом и порядком их создания.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="1a7d8-136">В демонстрационной системе поток ***thread_0*** выполняется первым, поскольку он имеет наивысший приоритет (*он был создан с приоритетом 1*).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="1a7d8-137">После приостановки потока ***thread_0*** выполняется поток ***thread_5***, затем ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_ и, наконец, _\*_thread_2_\*\*.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="1a7d8-138">*Несмотря на то, что потоки **thread_3** и **thread_4** имеют одинаковый приоритет (оба создаются с приоритетом 8), **thread_3** выполняется первым. Это связано с тем, что **thread_3** был создан и стал готов раньше потока **thread_4**. Потоки с одинаковым приоритетом выполняются в режиме FIFO.*</span><span class="sxs-lookup"><span data-stu-id="1a7d8-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="1a7d8-139">Поток 0</span><span class="sxs-lookup"><span data-stu-id="1a7d8-139">Thread 0</span></span>

<span data-ttu-id="1a7d8-140">Функция ***thread_0_entry*** помечает точку входа потока *(строки 167–190*).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="1a7d8-141">***Thread_0*** — это первый поток в демонстрационной системе для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="1a7d8-142">Его обработка очень проста: он увеличивает свой счетчик на единицу, ждет 10 тактов таймера, устанавливает флаг события для пробуждения ***thread_5***, а затем повторяет последовательность.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="1a7d8-143">***Thread_0*** — это поток с самым высоким приоритетом в системе.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="1a7d8-144">После истечения срока запрошенного спящего режима он будет выполнятся перед всеми остальными потоками в демонстрации.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="1a7d8-145">Поток 1</span><span class="sxs-lookup"><span data-stu-id="1a7d8-145">Thread 1</span></span>

<span data-ttu-id="1a7d8-146">Функция ***thread_1_entry** _ помечает точку входа потока _(строки 193–216 *). Поток ***thread_1*** является предпоследним потоком для выполнения в демонстрационной системе. Его обработка состоит из приращения своего счетчика, отправки сообщения потоку ***thread_2*** (* через* ***queue_0***) и повторения последовательности. Обратите внимание, что поток \***thread_1**_ приостанавливает работу, когда очередь _*_queue_0_*_ переполняется (строка 207\*).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="1a7d8-147">Поток 2</span><span class="sxs-lookup"><span data-stu-id="1a7d8-147">Thread 2</span></span>

<span data-ttu-id="1a7d8-148">Функция ***thread_2_entry*** помечает точку входа потока *(строки 219–243*).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="1a7d8-149">***Thread_2*** — это последний поток в демонстрационной системе для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="1a7d8-150">Его обработка включает увеличение соответствующего счетчика на единицу, получение сообщения от ***thread_1*** (через ***queue_0***) и повтор последовательности.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="1a7d8-151">Обратите внимание, что поток ***thread_2** _ приостанавливается при каждом полном освобождении _*_queue_0_*_ (_строка 233*).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="1a7d8-152">Хотя потоки ***thread_1** _ и _ *_thread_2_** имеют самый низкий приоритет в демонстрационной системе (\* приоритет 16\*), они являются *потоками 3 и 4*.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="1a7d8-153">Они также являются единственными потоками, готовыми к выполнению большую часть времени.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="1a7d8-154">Они также являются единственными потоками, созданными с использованием временных срезов (*строки 87 и 93*).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="1a7d8-155">Каждый поток может выполняться не более 4 тактов таймера, прежде чем будет выполнен другой поток.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="1a7d8-156">Потоки 3 и 4</span><span class="sxs-lookup"><span data-stu-id="1a7d8-156">Threads 3 and 4</span></span>

<span data-ttu-id="1a7d8-157">Функция ***thread_3_and_4_entry*** помечает точку входа потоков ***thread_3** _ и _ *_thread_4_** (строки 246–280).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="1a7d8-158">Оба потока имеют приоритет 8, что делает их третьим и четвертым потоками для выполнения в демонстрационной системе.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="1a7d8-159">Обработка каждого потока одинакова: увеличение счетчика, получение ***semaphore_0***, засыпание на 2 такта таймера, освобождение ***semaphore_0*** и повтор последовательности.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="1a7d8-160">Обратите внимание, что каждый поток приостанавливается при недоступности ***semaphore_0*** (строка 264).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="1a7d8-161">Кроме того, оба потока используют одну и ту же функцию для основной обработки.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="1a7d8-162">Это не создает проблем, так как они оба имеют собственный уникальный стек, а язык C по природе поддерживает реентерабельный код.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="1a7d8-163">Каждый поток определяет свой номер, проверяя входной параметр потока (строка 258), который задается при их создании (строки 102 и 109).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="1a7d8-164">*Также имеет смысл получить текущую точку потока во время его выполнения и сравнить ее с адресом управляющего блока, чтобы определить идентификатор потока.*</span><span class="sxs-lookup"><span data-stu-id="1a7d8-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="1a7d8-165">Поток 5</span><span class="sxs-lookup"><span data-stu-id="1a7d8-165">Thread 5</span></span>

<span data-ttu-id="1a7d8-166">Функция ***thread_5_entry*** помечает точку входа этого потока (строки 283–305).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="1a7d8-167">***Thread_5*** — это второй поток в демонстрационной системе для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="1a7d8-168">Его обработка включает увеличение соответствующего счетчика на единицу, получение флага события от потока ***thread_0*** (через ***event_flags_0***) и повтор последовательности.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="1a7d8-169">Обратите внимание, что поток ***thread_5*** приостанавливается, если флаг события в ***event_flags_0*** недоступен (строка 298).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="1a7d8-170">Потоки 6 и 7</span><span class="sxs-lookup"><span data-stu-id="1a7d8-170">Threads 6 and 7</span></span>

<span data-ttu-id="1a7d8-171">Функция ***thread_6_and_7_entry*** помечает точку входа потоков ***thread_6** _ и _ *_thread_7_** (строки 307–358).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="1a7d8-172">Оба потока имеют приоритет 8, что делает их пятым и шестым потоками для выполнения в демонстрационной системе.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="1a7d8-173">Обработка каждого потока одинакова: увеличение счетчика, дважды получение ***mutex_0***, засыпание на 2 такта таймера, дважды освобождение ***mutex_0*** и повтор последовательности.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="1a7d8-174">Обратите внимание, что каждый поток приостанавливается, если ***mutex_0*** недоступен (строка 325).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="1a7d8-175">Кроме того, оба потока используют одну и ту же функцию для основной обработки.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="1a7d8-176">Это не создает проблем, так как они оба имеют собственный уникальный стек, а язык C по природе поддерживает реентерабельный код.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="1a7d8-177">Каждый поток определяет свой номер, проверяя входной параметр потока (строка 319), который задается при их создании (строки 126 и 133).</span><span class="sxs-lookup"><span data-stu-id="1a7d8-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="1a7d8-178">Наблюдение за демонстрацией</span><span class="sxs-lookup"><span data-stu-id="1a7d8-178">Observing the Demonstration</span></span>

<span data-ttu-id="1a7d8-179">Каждый из демонстрационных потоков увеличивает соответствующий уникальный счетчик на единицу.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="1a7d8-180">Для проверки работы демонстрации можно просмотреть данные следующих счетчиков:</span><span class="sxs-lookup"><span data-stu-id="1a7d8-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="1a7d8-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-181">thread_0_counter</span></span>
- <span data-ttu-id="1a7d8-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-182">thread_1_counter</span></span>
- <span data-ttu-id="1a7d8-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-183">thread_2_counter</span></span>
- <span data-ttu-id="1a7d8-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-184">thread_3_counter</span></span>
- <span data-ttu-id="1a7d8-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-185">thread_4_counter</span></span>
- <span data-ttu-id="1a7d8-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-186">thread_5_counter</span></span>
- <span data-ttu-id="1a7d8-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-187">thread_6_counter</span></span>
- <span data-ttu-id="1a7d8-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="1a7d8-188">thread_7_counter</span></span>

<span data-ttu-id="1a7d8-189">Значение каждого из этих счетчиков должно увеличиваться при выполнении демонстрации, при этом значения счетчиков ***thread_1_counter** _ и _ *_thread_2_counter_** должны увеличиваться быстрее остальных.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="1a7d8-190">Файл дистрибутива: demo_threadx.c</span><span class="sxs-lookup"><span data-stu-id="1a7d8-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="1a7d8-191">В этом разделе приведен полный листинг файла ***demo_threadx.c***, включая номера строк, которые упоминаются в этой главе.</span><span class="sxs-lookup"><span data-stu-id="1a7d8-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
void thread_0_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {

        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}


void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}


void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;


    /* This function is executed from thread 3 and thread 4. As the loop
    below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;


    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
            &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
        below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
