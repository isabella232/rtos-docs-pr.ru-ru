---
title: Глава 4. Анализ производительности TraceX в ОСРВ Azure
description: В этой главе описывается средство анализа производительности TraceX в ОСРВ Azure.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815744"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a><span data-ttu-id="511d6-103">Глава 4. Анализ производительности TraceX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="511d6-103">Chapter 4 - Azure RTOS TraceX performance analysis</span></span>

<span data-ttu-id="511d6-104">В этой главе описывается средство анализа производительности TraceX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="511d6-104">This chapter describes the Azure RTOS TraceX performance analysis tool:</span></span>

## <a name="performance-analysis"></a><span data-ttu-id="511d6-105">Анализ производительности</span><span class="sxs-lookup"><span data-stu-id="511d6-105">Performance Analysis</span></span>

<span data-ttu-id="511d6-106">В TraceX имеется встроенный анализ производительности файлов трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-106">TraceX provides built-in performance analysis of trace files.</span></span> <span data-ttu-id="511d6-107">Доступны различные сведения, включая *профиль выполнения*, *популярные службы*, *использование стека потоков* и различные *статистические данные по производительности*, в том числе *статистика FileX и NetX*.</span><span class="sxs-lookup"><span data-stu-id="511d6-107">Information such as the *execution profile*, *popular services*, *thread stack usage*, and various *performance statistics,* including FileX and NetX statistics *,* are readily available.</span></span> <span data-ttu-id="511d6-108">Эта информация доступна через пункт меню ***Вид***.</span><span class="sxs-lookup"><span data-stu-id="511d6-108">This information is available via the ***View*** menu item.</span></span> 


## <a name="execution-profile"></a><span data-ttu-id="511d6-109">Профиль выполнения</span><span class="sxs-lookup"><span data-stu-id="511d6-109">Execution Profile</span></span>

<span data-ttu-id="511d6-110">При нажатии кнопки ***Создать профиль выполнения** _ или выборе пункта _*_Вид > Профиль-выполнение_\*_ открывается профиль выполнения TraceX для загруженного в данный момент файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-110">Selecting the ***Generate Execution Profile** _ button or _*_View -Execution Profile_\*_ presents the TraceX execution profile for the currently loaded trace file.</span></span> <span data-ttu-id="511d6-111">Профиль выполнения, связанный с образцом трассировки ThreadX, показан на _\*рисунке 19\*\*.</span><span class="sxs-lookup"><span data-stu-id="511d6-111">The execution profile associated with the sample ThreadX demonstration trace is shown in _\*Figure 19\*\*.</span></span>

![Снимок экрана: профиль выполнения, связанный с образцом трассировки ThreadX.](./media/user-guide/execution_profile.png)

<span data-ttu-id="511d6-113">**Рис. 19**</span><span class="sxs-lookup"><span data-stu-id="511d6-113">**FIGURE 19**</span></span>

<span data-ttu-id="511d6-114">В примере на **рисунке 19** видно, что почти 45 % процессорного времени приходится на **_поток 2_ *_ и еще почти 51 % — на _* _поток 1_**. Это логично, так как из трассировки следует, что эти потоки активно отправляют и получают сообщения.</span><span class="sxs-lookup"><span data-stu-id="511d6-114">The example shown in **Figure 19** indicates that nearly 45% of the processing time is inside of **_thread 2_*_ and nearly 51% of the processing time is inside of _*_thread 1_** This is logical since the bulk of the trace shows these threads sending and receiving messages.</span></span> <span data-ttu-id="511d6-115">На остальные контексты выполнения в этом примере приходится лишь небольшая доля времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="511d6-115">The remaining execution contexts have only a small amount of execution time in this example.</span></span>

## <a name="popular-services"></a><span data-ttu-id="511d6-116">Популярные службы</span><span class="sxs-lookup"><span data-stu-id="511d6-116">Popular Services</span></span>

<span data-ttu-id="511d6-117">Выбрав пункт \***Вид > Популярные службы**, можно просмотреть популярные службы в загруженном файле трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-117">Selecting \***View ->Popular Services** _ presents the popular services in the currently loaded trace file.</span></span> <span data-ttu-id="511d6-118">По умолчанию эта информация отображается для всей системы.</span><span class="sxs-lookup"><span data-stu-id="511d6-118">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="511d6-119">Однако также доступны популярные службы для конкретных потоков.</span><span class="sxs-lookup"><span data-stu-id="511d6-119">However, the popular services for specific threads are also available.</span></span> <span data-ttu-id="511d6-120">Популярные службы в примере трассировки ThreadX показаны на _\*рисунке 20\*\*.</span><span class="sxs-lookup"><span data-stu-id="511d6-120">The popular services in the sample ThreadX demonstration trace are shown in _\*Figure 20\*\*.</span></span>

![Снимок экрана: популярные службы в примере трассировки ThreadX.](./media/user-guide/popular_services.png)

<span data-ttu-id="511d6-122">**Рис. 20**</span><span class="sxs-lookup"><span data-stu-id="511d6-122">**FIGURE 20**</span></span>

<span data-ttu-id="511d6-123">В примере на **рисунке 20** видно, что двумя самыми популярными службами в этой трассировке являются **_tx_queue_send_ *_ и _* _tx_queue_receive_**.</span><span class="sxs-lookup"><span data-stu-id="511d6-123">The example shown in **Figure 20** indicates that **_tx_queue_send_*_ and _*_tx_queue_receive_** are the two most popular services in this trace.</span></span> <span data-ttu-id="511d6-124">Это согласуется с поведением стандартной демонстрации ThreadX, из которой была получена трассировка.</span><span class="sxs-lookup"><span data-stu-id="511d6-124">This is consistent with the behavior of the standard ThreadX demonstration from which this trace was captured.</span></span>

<span data-ttu-id="511d6-125">Выбрать для анализа определенные потоки можно в раскрывающемся списке в верхней части этого окна.</span><span class="sxs-lookup"><span data-stu-id="511d6-125">Specific threads can be selected for this analysis by using the drop down selection list at the top of this window.</span></span> <span data-ttu-id="511d6-126">На **рисунке 21** показан анализ для **_потока 3_**.</span><span class="sxs-lookup"><span data-stu-id="511d6-126">**Figure 21** shows this analysis for **_thread 3_**.</span></span>

![Снимок экрана: анализ для популярных служб TraceX.](./media/user-guide/popular_services_thread3.png)

<span data-ttu-id="511d6-128">**Рис. 21**</span><span class="sxs-lookup"><span data-stu-id="511d6-128">**FIGURE 21**</span></span>

## <a name="thread-stack-usage-analysis-for-thread-3"></a><span data-ttu-id="511d6-129">Использование стека потоков</span><span class="sxs-lookup"><span data-stu-id="511d6-129">Thread Stack Usage</span></span> ![Анализ для потока 3.](./media/user-guide/screen_shot_17.png)

<span data-ttu-id="511d6-131">При нажатии кнопки ***Создать данные по использованию стека потоков** _ или выборе пункта _*_Вид > Использование стека потоков_\*_ открываются данные по использованию стека для каждого потока в файле трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-131">Selecting the ***Generate Thread Stack Usage** _ button or _*_View -> Thread Stack Usage_\*_ presents the stack usage for each thread in the trace file.</span></span> <span data-ttu-id="511d6-132">Для этого ThreadX включает указатель на текущий стек потока в несколько записей трассировки в файле.</span><span class="sxs-lookup"><span data-stu-id="511d6-132">This is accomplished by ThreadX including the current thread stack pointer in many of the trace entries in the file.</span></span> <span data-ttu-id="511d6-133">Использование стека, равное 100 %, означает, что стек переполнен. Эту проблему необходимо устранить в приложении.</span><span class="sxs-lookup"><span data-stu-id="511d6-133">A stack usage of 100% indicates the stack has overflowed and must be corrected in the application.</span></span> <span data-ttu-id="511d6-134">Если в файле трассировки нет выполнения потока, использование стека для этого потока равно 0 %.</span><span class="sxs-lookup"><span data-stu-id="511d6-134">If there is no thread execution within this trace file, the stack usage for that thread is shown at 0%.</span></span> <span data-ttu-id="511d6-135">Использование стека потока в образце трассировки ThreadX показано на _\*рисунке 22\*\*.</span><span class="sxs-lookup"><span data-stu-id="511d6-135">The thread stack usage in the sample ThreadX demonstration trace is shown in _\*Figure 22\*\*.</span></span>

![Снимок экрана: использование стека потока TraceX.](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="511d6-137">**Рис. 22**</span><span class="sxs-lookup"><span data-stu-id="511d6-137">**FIGURE 22**</span></span>

<span data-ttu-id="511d6-138">В примере на **рисунке 22** видно, что большинство потоков в этой трассировке имеют значение использования стека от 9 до 12 %.</span><span class="sxs-lookup"><span data-stu-id="511d6-138">The example shown in **Figure 22** indicates that most threads in this trace have between 9% and 12% stack usage.</span></span>

## <a name="performance-statistics"></a><span data-ttu-id="511d6-139">статистика производительности</span><span class="sxs-lookup"><span data-stu-id="511d6-139">Performance Statistics</span></span>

<span data-ttu-id="511d6-140">При нажатии кнопки ***Создать статистику производительности** _ или выборе пункта _ *_Вид > Статистика производительности_** открывается статистика производительности для загруженного файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-140">Selecting the ***Generate Performance Statistics** _ button or _ *_View -> Performance Statistics_** presents the performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="511d6-141">По умолчанию эта информация отображается для всей системы.</span><span class="sxs-lookup"><span data-stu-id="511d6-141">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="511d6-142">Однако статистика производительности также доступна для каждого конкретного потока.</span><span class="sxs-lookup"><span data-stu-id="511d6-142">However, the performance statistics are also available for each specific thread.</span></span>

<span data-ttu-id="511d6-143">Статистика производительности для образца трассировки ThreadX представлена на **рисунке 23**.</span><span class="sxs-lookup"><span data-stu-id="511d6-143">The performance statistics of the sample ThreadX demonstration trace are shown in **Figure 23**.</span></span>

![Снимок экрана: статистика производительности TraceX.](./media/user-guide/performance_statistics.png)

<span data-ttu-id="511d6-145">**Рис. 23**</span><span class="sxs-lookup"><span data-stu-id="511d6-145">**FIGURE 23**</span></span>

<span data-ttu-id="511d6-146">В примере на **рисунке 23** видно, что в этом файле трассировки было 18 переключений контекста, а также пять вытеснений потоков, 16 приостановок потоков, 19 возобновлений потоков и три прерывания.</span><span class="sxs-lookup"><span data-stu-id="511d6-146">The example shown in **Figure 23** indicates that there were 18 context switches in this trace file, as well as five thread preemptions, 16 thread suspensions, 19 thread resumptions, and three interrupts.</span></span> <span data-ttu-id="511d6-147">Инверсий приоритета в этом файле трассировки не найдено.</span><span class="sxs-lookup"><span data-stu-id="511d6-147">There were no priority inversions found in this trace file.</span></span> <span data-ttu-id="511d6-148">Обратите внимание, что существует две категории инверсий приоритета, а именно *детерминированные* и *недетерминированные*.</span><span class="sxs-lookup"><span data-stu-id="511d6-148">Notice there are two categories of priority inversions, namely, *deterministic* and *nondeterministic*.</span></span> <span data-ttu-id="511d6-149">Детерминированные инверсии приоритета — это инверсия, при которых поток блокируется в мьютексе, принадлежащем потоку с более низким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="511d6-149">Deterministic priority inversions are priority inversion in which a thread is blocked on a mutex owned by a lower priority thread.</span></span> <span data-ttu-id="511d6-150">Недетерминированная инверсия приоритета происходит, когда другой поток с более низким приоритетом выполняется во время детерминированной инверсии приоритета.</span><span class="sxs-lookup"><span data-stu-id="511d6-150">An nondeterministic priority inversion is where a different lower priority thread runs during a deterministic priority inversion.</span></span> <span data-ttu-id="511d6-151">Это может привести к непредвиденному расчету времени в приложении и требует особого внимания.</span><span class="sxs-lookup"><span data-stu-id="511d6-151">The later can cause unforeseen timing behavior in the application and should be studied carefully.</span></span>

## <a name="filex-statistics"></a><span data-ttu-id="511d6-152">Статистика FileX</span><span class="sxs-lookup"><span data-stu-id="511d6-152">FileX Statistics</span></span>

<span data-ttu-id="511d6-153">При выборе пункта \***Вид > Статистика FileX** _ открывается статистика производительности FileX для загруженного файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-153">Selecting \***View -> FileX Statistics** _ presents the FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="511d6-154">Эта информация отображается для всей системы сразу, то есть по всем открытым объектам ../media.</span><span class="sxs-lookup"><span data-stu-id="511d6-154">This information is displayed for the entire system, on all opened ../media objects.</span></span> <span data-ttu-id="511d6-155">Статистика производительности для образца трассировки FileX представлена на _\*рисунке 24\*\*.</span><span class="sxs-lookup"><span data-stu-id="511d6-155">The performance statistics of the sample FileX demonstration trace are shown in _\*Figure 24\*\*.</span></span>

![Снимок экрана: статистика FileX.](./media/user-guide/filex_statistics.png)

<span data-ttu-id="511d6-157">**Рис. 24**</span><span class="sxs-lookup"><span data-stu-id="511d6-157">**FIGURE 24**</span></span>

<span data-ttu-id="511d6-158">В примере на **рисунке 27** видно, чтоб было открыто 19 объектов ../media, закрыто 19 объектов ../media, записано на диск 19 объектов ../media, выполнено 18 операций чтения из каталога, 19 операций записи в каталог и произошло 18 промахов кэша для каталогов.</span><span class="sxs-lookup"><span data-stu-id="511d6-158">The example shown in **Figure 27** indicates there were 19 ../media opens, 19 ../media closes, 19 ../media flushes, 18 directory reads, 19 directory writes, and 18 directory cache misses.</span></span> <span data-ttu-id="511d6-159">Дополнительные сведения можно получить, прокрутив окно статистики вниз.</span><span class="sxs-lookup"><span data-stu-id="511d6-159">Additonal information can be viewed by scrolling down in the statistics window.</span></span>

## <a name="netx-statistics"></a><span data-ttu-id="511d6-160">Статистика NetX</span><span class="sxs-lookup"><span data-stu-id="511d6-160">NetX Statistics</span></span>

<span data-ttu-id="511d6-161">При выборе пункта \***Вид > Статистика NetX** _ открывается статистика производительности NetX для загруженного файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-161">Selecting \***View -NetX Statistics** _ presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="511d6-162">Эта информация отображается для всей системы.</span><span class="sxs-lookup"><span data-stu-id="511d6-162">This information is displayed for the entire system.</span></span> <span data-ttu-id="511d6-163">Статистика производительности для образца трассировки NetX представлена на _\*рисунке 25\*\*.</span><span class="sxs-lookup"><span data-stu-id="511d6-163">The performance statistics of the sample NetX demonstration trace are shown in _\*Figure 25\*\*.</span></span>

![Снимок экрана: статистика NetX.](./media/user-guide/netx_statistics.png)

<span data-ttu-id="511d6-165">**Рис. 25**</span><span class="sxs-lookup"><span data-stu-id="511d6-165">**FIGURE 25**</span></span>

<span data-ttu-id="511d6-166">В примере на **рисунке 25** показано, что событий ARP, проверки связи или UDP не было, но было отправлено 30 IP-пакетов на 1368 байтов и получено 30 IP-пакетов на 1360 байтов.</span><span class="sxs-lookup"><span data-stu-id="511d6-166">The example shown in **Figure 25** indicates there were no ARP, Ping, or UDP events, but there were 30 IP packets sent, 1,368 IP bytes sent, 30 IP packets received, and 1,360 IP bytes received.</span></span>

## <a name="trace-file-information"></a><span data-ttu-id="511d6-167">Сведения о файле трассировки</span><span class="sxs-lookup"><span data-stu-id="511d6-167">Trace File Information</span></span>

<span data-ttu-id="511d6-168">При выборе пункта \***Вид > Сведения о файле трассировки** _ открываются основные сведения о загруженном файле трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-168">Selecting \***View -> Trace File Information** _ presents some basic information about the opened trace file.</span></span> <span data-ttu-id="511d6-169">Эти сведения включают в себя порядок байтов файла, размер источника времени, максимальное число байтов для каждого объекта и базовый адрес каждого указателя файла трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-169">This information includes the byte order of the file, size of the time source, maximum number of bytes for each object name, and the base address of all trace file pointers.</span></span> <span data-ttu-id="511d6-170">На _ *рисунке 26*\* представлены сведения о стандартном файле трассировки **_demo_threadx.trx_**.</span><span class="sxs-lookup"><span data-stu-id="511d6-170">_ *Figure 26*\* shows the trace file information for the standard **_demo_threadx.trx_** trace file.</span></span>

![Снимок экрана: сведения о файле TraceX.](./media/user-guide/trace_file_info.png)

<span data-ttu-id="511d6-172">**Рис. 26**</span><span class="sxs-lookup"><span data-stu-id="511d6-172">**FIGURE 26**</span></span>

## <a name="raw-trace-dump"></a><span data-ttu-id="511d6-173">Необработанный дамп трассировки</span><span class="sxs-lookup"><span data-stu-id="511d6-173">Raw Trace Dump</span></span>

<span data-ttu-id="511d6-174">При выборе пункта \***Вид > Необработанный дамп трассировки** _ открывается диалоговое окно для указания имени файла с необработанным дампом трассировки.</span><span class="sxs-lookup"><span data-stu-id="511d6-174">Selecting \***View -> Raw Trace Dump** _ presents a dialog to name the file containing the raw trace dump.</span></span> <span data-ttu-id="511d6-175">После ввода имени файла и пути к нему TraceX создает необработанный файл трассировки в текстовом формате и открывает его в _*_notepad.exe_*_.</span><span class="sxs-lookup"><span data-stu-id="511d6-175">After the file name and path are entered, TraceX builds the raw trace file in text format and launches _*_notepad.exe_*_ to display it.</span></span> <span data-ttu-id="511d6-176">На _ *рисунке 27*\* представлен необработанный дамп для стандартного файла трассировки **_demo_threadx.trx_**.</span><span class="sxs-lookup"><span data-stu-id="511d6-176">_ *Figure 27*\* shows the raw trace file dump for the standard **_demo_threadx.trx_** trace file.</span></span>

![Снимок экрана: необработанный дамп трассировки.](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="511d6-178">**Рис. 27**</span><span class="sxs-lookup"><span data-stu-id="511d6-178">**FIGURE 27**</span></span>
