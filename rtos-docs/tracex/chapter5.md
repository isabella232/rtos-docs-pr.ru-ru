---
title: Глава 5. Создание буферов трассировки
description: В этой главе описано, как создать буфер событий в TraceX для ОСРВ Azure, а также содержатся сведения о базовом формате буфера.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815735"
---
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="3e48a-103">Глава 5. Создание буферов трассировки</span><span class="sxs-lookup"><span data-stu-id="3e48a-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="3e48a-104">В этой главе описано, как создать буфер событий в TraceX для ОСРВ Azure, а также содержатся сведения о базовом формате буфера.</span><span class="sxs-lookup"><span data-stu-id="3e48a-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="3e48a-105">Поддержка трассировки событий в ThreadX</span><span class="sxs-lookup"><span data-stu-id="3e48a-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="3e48a-106">ThreadX предоставляет встроенную поддержку трассировки событий для всех служб ThreadX, изменений состояния потоков и определяемых пользователем событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="3e48a-107">Возможность отслеживания событий ThreadX в основном разработана как средство заключительного анализа, позволяющее анализировать последние n действий в приложении.</span><span class="sxs-lookup"><span data-stu-id="3e48a-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="3e48a-108">С помощью этих сведений разработчик может выявить проблемы и (или) потенциальные цели для оптимизации.</span><span class="sxs-lookup"><span data-stu-id="3e48a-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="3e48a-109">TraceX графически отображает буфер трассировки событий, созданный ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3e48a-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="3e48a-110">Ниже описано, как создать буфер, а также приведены сведения о базовом формате буфера.</span><span class="sxs-lookup"><span data-stu-id="3e48a-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="3e48a-111">Включение трассировки событий</span><span class="sxs-lookup"><span data-stu-id="3e48a-111">Enabling Event Trace</span></span>

<span data-ttu-id="3e48a-112">Чтобы включить трассировку событий, определите константы метки времени, создайте библиотеку ThreadX с заданным параметром **TX_ENABLE_EVENT_TRACE** и включите трассировку, вызвав функцию **tx_trace_enable**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="3e48a-113">Определение констант метки времени</span><span class="sxs-lookup"><span data-stu-id="3e48a-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="3e48a-114">Константы метки времени предназначены для предоставления разработчику элемента контроля над меткой времени, используемой в записях трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="3e48a-115">Ниже показано две константы метки времени и их значения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3e48a-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="3e48a-116">Указанные выше константы определяются в файле **tx_port. h** и создают "фиктивную" метку времени, которая просто увеличивается на единицу при каждом событии.</span><span class="sxs-lookup"><span data-stu-id="3e48a-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="3e48a-117">Ниже приведен пример фактического определения метки времени.</span><span class="sxs-lookup"><span data-stu-id="3e48a-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="3e48a-118">Приведенные выше константы задают 32-разрядный таймер, полученный путем считывания адреса 0x13000004.</span><span class="sxs-lookup"><span data-stu-id="3e48a-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="3e48a-119">Большинство меток времени конкретного приложения следует настраивать аналогичным образом.</span><span class="sxs-lookup"><span data-stu-id="3e48a-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="3e48a-120">Экспорт буфера трассировки</span><span class="sxs-lookup"><span data-stu-id="3e48a-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="3e48a-121">Для TraceX требуется буфер трассировки в двоичном формате, шестнадцатеричном формате Intel или формате файла Motorola S-Record на узле.</span><span class="sxs-lookup"><span data-stu-id="3e48a-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="3e48a-122">Самый простой способ сделать это — приостановить работу целевого объекта и настроить отладчик для создания дампа области памяти, которую вы указали для функции ***tx_trace_enable*** в файле на узле.</span><span class="sxs-lookup"><span data-stu-id="3e48a-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="3e48a-123">***Следите за тем, чтобы не остановить целевой объект в самом коде, собирающем трассировку. Это может привести к недопустимым данным трассировки. Если программа остановлена в ThreadX, то перед созданием дампа буфера трассировки лучше выполнить шаг с обходом любым макросом вставки трассировки.***</span><span class="sxs-lookup"><span data-stu-id="3e48a-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-124">*В приложении D показано, как создать дамп буфера трассировки с помощью различных средств разработки.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="3e48a-125">API трассировки расширенных событий</span><span class="sxs-lookup"><span data-stu-id="3e48a-125">Extended Event Trace API</span></span>

<span data-ttu-id="3e48a-126">Если ThreadX создан с заданным параметром **TX_ENABLE_EVENT_TRACE**, то для приложения доступны следующие новые API-интерфейсы трассировки событий:</span><span class="sxs-lookup"><span data-stu-id="3e48a-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="3e48a-127">tx_trace_enable — *включение трассировки событий.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="3e48a-128">tx_trace_event_filter — *фильтрация указанных событий.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="3e48a-129">tx_trace_event_unfilter — *отмена фильтрации указанных событий.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="3e48a-130">tx_trace_disable — *отключение трассировки событий.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="3e48a-131">tx_trace_isr_enter_insert — *вставка события трассировки входа в ISR.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="3e48a-132">tx_trace_isr_exit_insert — *вставка события трассировки выхода ISR.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="3e48a-133">tx_trace_buffer_full_notify — *регистрация обратного вызова приложения для информирования о заполнении буфера трассировки.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="3e48a-134">tx_trace_user_event_insert — *вставка пользовательского события.*</span><span class="sxs-lookup"><span data-stu-id="3e48a-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="3e48a-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="3e48a-135">tx_trace_enable</span></span>

<span data-ttu-id="3e48a-136">Включение трассировки событий</span><span class="sxs-lookup"><span data-stu-id="3e48a-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-137">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="3e48a-138">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-138">Description</span></span>
<span data-ttu-id="3e48a-139">Эта служба включает трассировку событий в ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3e48a-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="3e48a-140">Приложение предоставляет буфер трассировки и максимальное количество объектов ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3e48a-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-141">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-142">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-142">Input Parameters</span></span>

- <span data-ttu-id="3e48a-143">**trace_buffer_start** — указатель на начало буфера трассировки, предоставляемого пользователем.</span><span class="sxs-lookup"><span data-stu-id="3e48a-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="3e48a-144">**trace_buffer_size** — общее количество байтов в памяти для буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="3e48a-145">Чем больше буфер трассировки, тем больше записей в нем можно хранить.</span><span class="sxs-lookup"><span data-stu-id="3e48a-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="3e48a-146">**registry_entries** — количество объектов приложения ThreadX, которые необходимо сохранить в реестре трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="3e48a-147">Реестр используется для сопоставления адресов объектов с именами объектов.</span><span class="sxs-lookup"><span data-stu-id="3e48a-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="3e48a-148">Это очень удобно для средств анализа трассировки графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="3e48a-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="3e48a-149">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-149">Return Values</span></span>

- <span data-ttu-id="3e48a-150">**TX_SUCCESS** (0x00) — успешное включение трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="3e48a-151">**TX_SIZE_ERROR** (0x05) — указанный размер буфера трассировки слишком мал.</span><span class="sxs-lookup"><span data-stu-id="3e48a-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="3e48a-152">Он должен вмещать заголовок трассировки, реестр объектов и хотя бы одну запись трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="3e48a-153">**TX_NOT_DONE** (0x20) — трассировка событий уже включена.</span><span class="sxs-lookup"><span data-stu-id="3e48a-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="3e48a-154">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.</span><span class="sxs-lookup"><span data-stu-id="3e48a-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-155">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-155">Allowed From</span></span>

<span data-ttu-id="3e48a-156">Инициализация и потоки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-157">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-158">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-158">See Also</span></span>

<span data-ttu-id="3e48a-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="3e48a-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="3e48a-160">tx_trace_event_filter</span></span>

<span data-ttu-id="3e48a-161">Фильтрация указанных событий</span><span class="sxs-lookup"><span data-stu-id="3e48a-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-162">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="3e48a-163">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-163">Description</span></span>

<span data-ttu-id="3e48a-164">Эта служба фильтрует указанные события от вставки в активный буфер трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="3e48a-165">Обратите внимание, что по умолчанию события не отфильтрованы после вызова *tx_trace_enable*.</span><span class="sxs-lookup"><span data-stu-id="3e48a-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-166">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-167">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-167">Input Parameters</span></span>

- <span data-ttu-id="3e48a-168">**event_filter_bits** — биты, соответствующие фильтруемым событиям.</span><span class="sxs-lookup"><span data-stu-id="3e48a-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="3e48a-169">Несколько событий можно отфильтровать простой операцией ИЛИ вместе с соответствующими константами.</span><span class="sxs-lookup"><span data-stu-id="3e48a-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="3e48a-170">Допустимые константы для этой переменной определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3e48a-170">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="3e48a-171">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-171">Return Values</span></span>

- <span data-ttu-id="3e48a-172">**TX_SUCCESS**: (0x00) — успешное применение фильтра событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="3e48a-173">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.</span><span class="sxs-lookup"><span data-stu-id="3e48a-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-174">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-174">Allowed From</span></span>

<span data-ttu-id="3e48a-175">Инициализация и потоки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-176">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-177">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-177">See Also</span></span>

<span data-ttu-id="3e48a-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="3e48a-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="3e48a-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="3e48a-180">Отмена фильтрации указанных событий</span><span class="sxs-lookup"><span data-stu-id="3e48a-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-181">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="3e48a-182">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-182">Description</span></span>

<span data-ttu-id="3e48a-183">Эта служба отменяет фильтрацию указанных событий, поэтому они будут вставлены в активный буфер трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-184">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-185">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-185">Input Parameters</span></span>

- <span data-ttu-id="3e48a-186">**event_unfilter_bits** — биты, соответствующие нефильтруемым событиям.</span><span class="sxs-lookup"><span data-stu-id="3e48a-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="3e48a-187">Фильтрацию нескольких событий можно отменить простой операцией ИЛИ вместе с соответствующими константами.</span><span class="sxs-lookup"><span data-stu-id="3e48a-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="3e48a-188">Допустимые константы для этой переменной определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3e48a-188">Valid constants for this variable are defined as follows:</span></span>

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a><span data-ttu-id="3e48a-189">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-189">Return Values</span></span>

- <span data-ttu-id="3e48a-190">**TX_SUCCESS**: (0x00) — успешная отмена фильтрации событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="3e48a-191">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.</span><span class="sxs-lookup"><span data-stu-id="3e48a-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-192">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-192">Allowed From</span></span>

<span data-ttu-id="3e48a-193">Инициализация и потоки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-194">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-195">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-195">See Also</span></span>

<span data-ttu-id="3e48a-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="3e48a-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="3e48a-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="3e48a-198">Отключение трассировки событий</span><span class="sxs-lookup"><span data-stu-id="3e48a-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-199">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="3e48a-200">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-200">Description</span></span>

<span data-ttu-id="3e48a-201">Эта служба отключает трассировку событий в ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3e48a-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="3e48a-202">Это может пригодиться, если для приложения нужно заморозить текущий буфер трассировки событий и, возможно, передать его на внешний ресурс во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="3e48a-203">После отключения можно вызвать **tx_trace_enable**, чтобы снова начать трассировку.</span><span class="sxs-lookup"><span data-stu-id="3e48a-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-204">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-205">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-205">Input Parameters</span></span>

<span data-ttu-id="3e48a-206">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3e48a-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="3e48a-207">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-207">Return Values</span></span>

- <span data-ttu-id="3e48a-208">**TX_SUCCESS** (0x00) — успешное отключение трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="3e48a-209">**TX_NOT_DONE** (0x20) — трассировка событий не была включена.</span><span class="sxs-lookup"><span data-stu-id="3e48a-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="3e48a-210">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.</span><span class="sxs-lookup"><span data-stu-id="3e48a-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-211">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-211">Allowed From</span></span>

<span data-ttu-id="3e48a-212">Инициализация и потоки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-213">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-214">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-214">See Also</span></span>

<span data-ttu-id="3e48a-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="3e48a-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="3e48a-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="3e48a-217">Вставка события ввода ISR</span><span class="sxs-lookup"><span data-stu-id="3e48a-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-218">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="3e48a-219">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-219">Description</span></span>

<span data-ttu-id="3e48a-220">Эта служба вставляет событие ввода ISR в буфер трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="3e48a-221">Ее следует вызывать через приложение в начале обработки ISR.</span><span class="sxs-lookup"><span data-stu-id="3e48a-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="3e48a-222">Заданный параметр должен определять конкретную ISR для приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-223">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-224">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-224">Input Parameters</span></span> 
- <span data-ttu-id="3e48a-225">**isr_id** — значение конкретного приложения для определения ISR.</span><span class="sxs-lookup"><span data-stu-id="3e48a-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="3e48a-226">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-226">Return Values</span></span>

<span data-ttu-id="3e48a-227">**None**</span><span class="sxs-lookup"><span data-stu-id="3e48a-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-228">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-228">Allowed From</span></span> 

<span data-ttu-id="3e48a-229">Подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="3e48a-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-230">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-231">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-231">See Also</span></span>

<span data-ttu-id="3e48a-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="3e48a-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="3e48a-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="3e48a-234">Вставка события выхода ISR</span><span class="sxs-lookup"><span data-stu-id="3e48a-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-235">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="3e48a-236">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-236">Description</span></span>

<span data-ttu-id="3e48a-237">Эта служба вставляет событие записи ISR в буфер трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="3e48a-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="3e48a-238">Ее следует вызывать через приложение в начале обработки ISR.</span><span class="sxs-lookup"><span data-stu-id="3e48a-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="3e48a-239">Заданный параметр должен определять ISR для приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-240">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-241">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-241">Input Parameters</span></span> 

- <span data-ttu-id="3e48a-242">**isr_id** — значение конкретного приложения для определения ISR.</span><span class="sxs-lookup"><span data-stu-id="3e48a-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="3e48a-243">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-243">Return Values</span></span>

<span data-ttu-id="3e48a-244">**None**</span><span class="sxs-lookup"><span data-stu-id="3e48a-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-245">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-245">Allowed From</span></span>

<span data-ttu-id="3e48a-246">Подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="3e48a-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-247">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-248">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-248">See Also</span></span>

<span data-ttu-id="3e48a-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="3e48a-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="3e48a-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="3e48a-251">Регистрация обратного вызова приложения для информирования о заполнении буфера трассировки</span><span class="sxs-lookup"><span data-stu-id="3e48a-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-252">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="3e48a-253">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-253">Description</span></span>

<span data-ttu-id="3e48a-254">Эта служба регистрирует функцию обратного вызова приложения, вызываемую ThreadX при заполнении буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="3e48a-255">Затем приложение может отключить трассировку и (или) настроить новый буфер трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-256">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-257">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-257">Input Parameters</span></span>

- <span data-ttu-id="3e48a-258">**full_buffer_callback** — функция приложения для вызова при заполнении буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="3e48a-259">Значение NULL отключает обратный вызов уведомления.</span><span class="sxs-lookup"><span data-stu-id="3e48a-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="3e48a-260">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-260">Return Values</span></span>

<span data-ttu-id="3e48a-261">**None**</span><span class="sxs-lookup"><span data-stu-id="3e48a-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-262">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-262">Allowed From</span></span>

<span data-ttu-id="3e48a-263">Подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="3e48a-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-264">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-265">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-265">See Also</span></span>

<span data-ttu-id="3e48a-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert.</span><span class="sxs-lookup"><span data-stu-id="3e48a-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="3e48a-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="3e48a-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="3e48a-268">Вставка пользовательского события</span><span class="sxs-lookup"><span data-stu-id="3e48a-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="3e48a-269">Прототип</span><span class="sxs-lookup"><span data-stu-id="3e48a-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="3e48a-270">Описание</span><span class="sxs-lookup"><span data-stu-id="3e48a-270">Description</span></span>

<span data-ttu-id="3e48a-271">Эта служба вставляет пользовательское событие в буфер трассировки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="3e48a-272">Идентификаторы пользовательских событий должны быть больше константы **TX_TRACE_USER_EVENT_START**, которая определена со значением 4096.</span><span class="sxs-lookup"><span data-stu-id="3e48a-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="3e48a-273">Максимальное пользовательское событие определяется константой **TX_TRACE_USER_EVENT_END** со значением 65535.</span><span class="sxs-lookup"><span data-stu-id="3e48a-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="3e48a-274">Все события в этом диапазоне доступны для приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-274">All events within this range are available to the application.</span></span> <span data-ttu-id="3e48a-275">Поля сведений зависят от приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e48a-276">Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="3e48a-277">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="3e48a-277">Input Parameters</span></span>

- <span data-ttu-id="3e48a-278">**event_id** — идентификация события конкретного приложения должна начинаться со значения большего чем **TX_TRACE_USER_EVENT_START**, но не большего чем **TX_TRACE_USER_EVENT_END**.</span><span class="sxs-lookup"><span data-stu-id="3e48a-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="3e48a-279">**info_field_1** — поле сведений конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="3e48a-280">**info_field_2** — поле сведений конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="3e48a-281">**info_field_3** — поле сведений конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="3e48a-282">**info_field_4** — поле сведений конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="3e48a-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="3e48a-283">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3e48a-283">Return Values</span></span>
- <span data-ttu-id="3e48a-284">**TX_SUCCESS** (0X00) — успешная вставка пользовательского события.</span><span class="sxs-lookup"><span data-stu-id="3e48a-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="3e48a-285">**TX_NOT_DONE** (0x20) — трассировка событий не включена.</span><span class="sxs-lookup"><span data-stu-id="3e48a-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="3e48a-286">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.</span><span class="sxs-lookup"><span data-stu-id="3e48a-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="3e48a-287">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3e48a-287">Allowed From</span></span>

<span data-ttu-id="3e48a-288">Инициализация и потоки.</span><span class="sxs-lookup"><span data-stu-id="3e48a-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="3e48a-289">Пример</span><span class="sxs-lookup"><span data-stu-id="3e48a-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="3e48a-290">См. также:</span><span class="sxs-lookup"><span data-stu-id="3e48a-290">See Also</span></span>

<span data-ttu-id="3e48a-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify.</span><span class="sxs-lookup"><span data-stu-id="3e48a-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>