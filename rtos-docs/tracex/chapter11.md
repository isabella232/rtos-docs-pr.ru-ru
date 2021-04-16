---
title: Глава 11. Формат буфера трассировки событий
description: ThreadX предоставляет встроенную поддержку трассировки событий для всех служб ThreadX для ОСРВ Azure, изменений состояния потоков и определяемых пользователем событий.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815771"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a><span data-ttu-id="0d5b6-103">Глава 11. Формат буфера трассировки событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-103">Chapter 11 - Format of event trace buffer</span></span>

<span data-ttu-id="0d5b6-104">ThreadX для ОСРВ Azure предоставляет встроенную поддержку трассировки событий для всех служб ThreadX, изменений состояния потоков и определяемых пользователем событий.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-104">Azure RTOS ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="0d5b6-105">Чтобы использовать трассировку событий, перед сборкой библиотек ThreadX, NetX и FileX определите параметр **TX_ENABLE_EVENT_TRACE** и включите трассировку, вызвав функцию **_tx_trace_enable_**.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-105">To use event trace, simply build the ThreadX, NetX, and FileX libraries with **TX_ENABLE_EVENT_TRACE** defined and enable tracing by calling the **_tx_trace_enable_** function.</span></span> <span data-ttu-id="0d5b6-106">В этой главе подробно описывается этот процесс.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-106">This chapter describes that process.</span></span>

## <a name="event-trace-format"></a><span data-ttu-id="0d5b6-107">Формат трассировки событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-107">Event Trace Format</span></span>

<span data-ttu-id="0d5b6-108">Формат буфера трассировки событий в ThreadX включает три раздела: заголовок управления, реестр объектов и записи трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-108">The format of the ThreadX event trace buffer is divided into three sections, namely the control header, object registry, and the trace entries.</span></span> <span data-ttu-id="0d5b6-109">Ниже описан общий макет буфера трассировки событий в ThreadX:</span><span class="sxs-lookup"><span data-stu-id="0d5b6-109">The following describes the general layout of the ThreadX event trace buffer:</span></span>

<span data-ttu-id="0d5b6-110">**Заголовок управления**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-110">**Control Header**</span></span>

<span data-ttu-id="0d5b6-111">**Запись 0 в реестре объектов**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-111">**Object Registry Entry 0**</span></span>

<span data-ttu-id="0d5b6-112">**…**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-112">**…**</span></span>

<span data-ttu-id="0d5b6-113">**Запись "n" в реестре объектов**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-113">**Object Register Entry "n"**</span></span>

<span data-ttu-id="0d5b6-114">**Запись 0 в трассировке событий**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-114">**Event Trace Entry 0**</span></span>

<span data-ttu-id="0d5b6-115">**…**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-115">**…**</span></span>

<span data-ttu-id="0d5b6-116">**Запись "n" в трассировке событий**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-116">**Event Trace Entry "n"**</span></span>

### <a name="event-trace-control-header"></a><span data-ttu-id="0d5b6-117">Заголовок управления для трассировки событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-117">Event Trace Control Header</span></span>

<span data-ttu-id="0d5b6-118">Заголовок управления определяет точный макет буфера трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-118">The control header defines the exact layout of the event trace buffer.</span></span> <span data-ttu-id="0d5b6-119">Среди прочего здесь указывается, сколько объектов ThreadX можно зарегистрировать и сколько событий можно записать.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-119">This includes how many ThreadX objects can be registered as well as how many events can be recorded.</span></span> <span data-ttu-id="0d5b6-120">Кроме того, заголовок управления определяет расположение каждого элемента буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-120">In addition, the control header defines where each of the elements of the trace buffer resides.</span></span> <span data-ttu-id="0d5b6-121">Заголовок управления имеет формат следующей структуры данных:</span><span class="sxs-lookup"><span data-stu-id="0d5b6-121">The following data structure defines the control header:</span></span>

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a><span data-ttu-id="0d5b6-122">Идентификатор заголовка управления</span><span class="sxs-lookup"><span data-stu-id="0d5b6-122">Control Header ID</span></span>

<span data-ttu-id="0d5b6-123">Идентификатор заголовка управления состоит из 32-разрядного шестнадцатеричного значения 0x54585442, которое соответствует знакам ASCII ***TXTB***.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-123">The control header ID consists of the 32-bit HEX value of 0x54585442, which corresponds to the ASCII characters ***TXTB***.</span></span> <span data-ttu-id="0d5b6-124">Так как это значение сохраняется в формате 32-разрядной переменной без знака, оно позволяет определить порядок следования байтов в буфере трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-124">Since this value is written as a 32-bit unsigned variable, it can also be used to detect the endianness of the event trace buffer.</span></span> <span data-ttu-id="0d5b6-125">Например, если в первых четырех байтах памяти размещены значения 0x54, 0x58, 0x54 и 0x42, значит буфер трассировки событий сохранялся в формате с обратным порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-125">For example, if the value in the first four byes of memory is 0x54, 0x58, 0x54, 0x42, the event trace buffer was written in big endian format.</span></span> <span data-ttu-id="0d5b6-126">В противном случае для буфера трассировки событий применялся прямой порядок байтов.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-126">Otherwise, the event trace buffer was written in little endian format.</span></span>

### <a name="timer-valid-mask"></a><span data-ttu-id="0d5b6-127">Допустимая маска таймера</span><span class="sxs-lookup"><span data-stu-id="0d5b6-127">Timer Valid Mask</span></span>

<span data-ttu-id="0d5b6-128">Допустимая маска таймера определяет, сколько битов метки времени учитываются в записях трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-128">The timer valid mask defines how many bits of the timestamp in the actual event trace entries are valid.</span></span> <span data-ttu-id="0d5b6-129">Например, если источник метки времени предоставляет 16-разрядное значение, в этом поле должно размещаться значение 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-129">For example, if the time-stamp source has 16-bits, the value in this field should be 0xFFFF.</span></span> <span data-ttu-id="0d5b6-130">Для 32-разрядного источника метки времени здесь указывается 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-130">A 32-bit time-stamp source would have a value of 0xFFFFFFFF.</span></span> <span data-ttu-id="0d5b6-131">Это значение определяется константой ***TX_TRACE_TIME_MASK** _ в файле _*_tx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-131">This value is defined by the ***TX_TRACE_TIME_MASK** _ constant in _*_tx_port.h_\*\*.</span></span>

### <a name="trace-base-address"></a><span data-ttu-id="0d5b6-132">Базовый адрес трассировки</span><span class="sxs-lookup"><span data-stu-id="0d5b6-132">Trace Base Address</span></span>

<span data-ttu-id="0d5b6-133">Базовый адрес буфера трассировки представляет собой адрес, который приложение указывает в качестве начала буфера трассировки в вызове ***tx_trace_enable***.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-133">The trace buffer base address is the address the application specified as the start of the trace buffer in the ***tx_trace_enable*** call.</span></span> <span data-ttu-id="0d5b6-134">Этот адрес нужен только для того, чтобы средство анализа могло получить значения смещений элементов в буфере относительно начала буфера.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-134">This address is maintained for the sole use of the analysis tool to derive bufferrelative offsets for the various elements in the buffer.</span></span> <span data-ttu-id="0d5b6-135">Например, относительное смещение текущего события в буфере трассировки вычисляется простым вычитанием базового адреса из адреса текущего события.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-135">For example, the buffer relative offset of the current event in the trace buffer is calculated by simple subtraction of the base address from the current event address.</span></span>

### <a name="registry-start-and-end-pointers"></a><span data-ttu-id="0d5b6-136">Указатели начала и конца реестра</span><span class="sxs-lookup"><span data-stu-id="0d5b6-136">Registry Start and End Pointers</span></span>

<span data-ttu-id="0d5b6-137">Указатель начала реестра указывает на адрес первой записи в реестре объектов, а указатель конца реестра — на адрес сразу за последней записью реестра.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-137">The registry start pointer points to the address of the first object registry entry, while the registry end pointer points to the address im../mediately following the last register entry.</span></span> <span data-ttu-id="0d5b6-138">Эти значения устанавливаются во время обработки службы *tx_trace_enable* и не изменяются на всем протяжении трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-138">These values are setup during the *tx_trace_enable* processing and are not changed throughout the duration of tracing.</span></span>

### <a name="registry-name-size"></a><span data-ttu-id="0d5b6-139">Размер имени реестра</span><span class="sxs-lookup"><span data-stu-id="0d5b6-139">Registry Name Size</span></span>

<span data-ttu-id="0d5b6-140">Размер имени реестра определяет максимальный размер в байтах для каждого имени объекта в записи реестра и определяется символом \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-140">The registry name size defines maximum size in bytes for each object name in the registry entry and is defined by the symbol \***TX_TRACE_OBJECT_REGISTRY_NAME** _.</span></span> <span data-ttu-id="0d5b6-141">По умолчанию используется значение 32, которое определено в файле _*_tx_trace.h_*_.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-141">The default value is 32 and is defined in _*_tx_trace.h_*_.</span></span> <span data-ttu-id="0d5b6-142">Имя объекта соответствует имени, которое приложение указывает при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-142">The object name corresponds to the name given by the application when the object was created.</span></span> <span data-ttu-id="0d5b6-143">Например, имя реестра объектов для потока совпадает с именем, предоставленным приложением при вызове _\*_tx_thread_create_\*\*.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-143">For example, the object registry name for a thread is the name supplied by the application to the _\*_tx_thread_create_\*\*call.</span></span>

### <a name="buffer-start-and-end-pointers"></a><span data-ttu-id="0d5b6-144">Указатели начала и конца буфера</span><span class="sxs-lookup"><span data-stu-id="0d5b6-144">Buffer Start and End Pointers</span></span>

<span data-ttu-id="0d5b6-145">Указатель начала буфера трассировки событий указывает на адрес первой записи трассировки, а указатель конца буфера — на адрес сразу за последней записью трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-145">The event trace buffer start pointer points to the address of the first trace entry, while the registry end pointer points to the address im../mediately following the last trace entry.</span></span> <span data-ttu-id="0d5b6-146">Эти значения устанавливаются во время обработки службы ***tx_trace_enable*** и не изменяются на всем протяжении трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-146">These values are setup during the ***tx_trace_enable</*** processing and are not changed throughout the duration of tracing.</span></span>

### <a name="current-buffer-pointer"></a><span data-ttu-id="0d5b6-147">Указатель текущего буфера</span><span class="sxs-lookup"><span data-stu-id="0d5b6-147">Current Buffer Pointer</span></span>

<span data-ttu-id="0d5b6-148">Указатель текущего буфера трассировки событий указывает на адрес самой старой записи трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-148">The event trace buffer current pointer points to the address of the oldest trace entry.</span></span> <span data-ttu-id="0d5b6-149">Так как записи трассировки сохраняются в циклическом списке, указатель текущего буфера одновременно обозначает позицию для сохранения следующей записи трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-149">Since the trace entries are maintained in a circular list, the current buffer pointer is also represents the next trace entry to be written.</span></span> |

## <a name="event-trace-object-registry"></a><span data-ttu-id="0d5b6-150">Реестр объектов трассировки событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-150">Event Trace Object Registry</span></span>

<span data-ttu-id="0d5b6-151">Реестр объектов трассировки событий содержит \***n** _ элементов реестра объектов, которые соответствуют созданным приложением объектам.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-151">The event trace object registry contains \***n** _ object registry entries that correspond to the objects created by the application.</span></span> <span data-ttu-id="0d5b6-152">Реестр объектов предназначен в первую очередь для того, чтобы внешние средства анализа могли соотнести реальные имена объектов с адресами записей в буфере трассировки.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-152">The main purpose of the object registry is for external analysis tools to correlate actual object names with the object addresses of the trace buffer entries.</span></span> <span data-ttu-id="0d5b6-153">Число записей реестра задается приложением в вызове _ \*_tx_trace_enable_\*\*.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-153">The number of registry entries is specified by the application in the _ *_tx_trace_enable_*\* call.</span></span>

<span data-ttu-id="0d5b6-154">Каждая запись реестра объектов содержит сведения о конкретном объекте ThreadX, ранее созданном приложением.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-154">Each object register entry contains information about a specific ThreadX object previously created by the application.</span></span> <span data-ttu-id="0d5b6-155">Следующая структура данных определяет каждую запись реестра объектов:</span><span class="sxs-lookup"><span data-stu-id="0d5b6-155">The following data structure defines each object registry entry:</span></span>

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a><span data-ttu-id="0d5b6-156">Флаг доступности объекта</span><span class="sxs-lookup"><span data-stu-id="0d5b6-156">Object Available Flag</span></span>

<span data-ttu-id="0d5b6-157">Флаг доступности объекта получает значение 1, если доступна запись реестра объектов.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-157">The object available flag is set to 1 if the object registry entry is available.</span></span> <span data-ttu-id="0d5b6-158">В противном случае (значение отличается от 1) запись в реестре объектов недоступна.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-158">Otherwise, if the value is not 1, the object registry entry is not available.</span></span> <span data-ttu-id="0d5b6-159">Обратите внимание, что даже недоступная запись может содержать допустимые сведения.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-159">Note that the entry could still contain valid information even though it is available.</span></span>

### <a name="object-entry-type"></a><span data-ttu-id="0d5b6-160">Тип записи объекта</span><span class="sxs-lookup"><span data-stu-id="0d5b6-160">Object Entry Type</span></span>

<span data-ttu-id="0d5b6-161">Тип записи объекта определяет тип объекта в этой записи.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-161">The object entry type identifies the type of object in this entry.</span></span> <span data-ttu-id="0d5b6-162">Ниже представлен полный список допустимых типов объекта:</span><span class="sxs-lookup"><span data-stu-id="0d5b6-162">The following is a list of the valid object types:</span></span>

| <span data-ttu-id="0d5b6-163">**Значение**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-163">**Value**</span></span> | <span data-ttu-id="0d5b6-164">**Тип объекта**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-164">**Object Type**</span></span> |
|---------- | --------------- |
| <span data-ttu-id="0d5b6-165">0</span><span class="sxs-lookup"><span data-stu-id="0d5b6-165">0</span></span>         | <span data-ttu-id="0d5b6-166">Недействительно</span><span class="sxs-lookup"><span data-stu-id="0d5b6-166">Not Valid</span></span>       |
| <span data-ttu-id="0d5b6-167">1</span><span class="sxs-lookup"><span data-stu-id="0d5b6-167">1</span></span>         | <span data-ttu-id="0d5b6-168">Thread</span><span class="sxs-lookup"><span data-stu-id="0d5b6-168">Thread</span></span>          |
| <span data-ttu-id="0d5b6-169">2</span><span class="sxs-lookup"><span data-stu-id="0d5b6-169">2</span></span>         | <span data-ttu-id="0d5b6-170">Таймер</span><span class="sxs-lookup"><span data-stu-id="0d5b6-170">Timer</span></span> |
| <span data-ttu-id="0d5b6-171">3</span><span class="sxs-lookup"><span data-stu-id="0d5b6-171">3</span></span>         | <span data-ttu-id="0d5b6-172">Очередь</span><span class="sxs-lookup"><span data-stu-id="0d5b6-172">Queue</span></span> |
| <span data-ttu-id="0d5b6-173">4</span><span class="sxs-lookup"><span data-stu-id="0d5b6-173">4</span></span>         | <span data-ttu-id="0d5b6-174">Semaphore</span><span class="sxs-lookup"><span data-stu-id="0d5b6-174">Semaphore</span></span> |
| <span data-ttu-id="0d5b6-175">5</span><span class="sxs-lookup"><span data-stu-id="0d5b6-175">5</span></span>         | <span data-ttu-id="0d5b6-176">Mutex</span><span class="sxs-lookup"><span data-stu-id="0d5b6-176">Mutex</span></span> |
| <span data-ttu-id="0d5b6-177">6</span><span class="sxs-lookup"><span data-stu-id="0d5b6-177">6</span></span>         | <span data-ttu-id="0d5b6-178">Группа флагов событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-178">Event Flags Group</span></span> |
| <span data-ttu-id="0d5b6-179">7</span><span class="sxs-lookup"><span data-stu-id="0d5b6-179">7</span></span>         | <span data-ttu-id="0d5b6-180">Пул блоков</span><span class="sxs-lookup"><span data-stu-id="0d5b6-180">Block Pool</span></span> |
| <span data-ttu-id="0d5b6-181">8</span><span class="sxs-lookup"><span data-stu-id="0d5b6-181">8</span></span>         | <span data-ttu-id="0d5b6-182">Пул байтов</span><span class="sxs-lookup"><span data-stu-id="0d5b6-182">Byte Pool</span></span> |
| <span data-ttu-id="0d5b6-183">9</span><span class="sxs-lookup"><span data-stu-id="0d5b6-183">9</span></span>         | <span data-ttu-id="0d5b6-184">../media</span><span class="sxs-lookup"><span data-stu-id="0d5b6-184">../media</span></span> |
| <span data-ttu-id="0d5b6-185">10</span><span class="sxs-lookup"><span data-stu-id="0d5b6-185">10</span></span>        | <span data-ttu-id="0d5b6-186">Файл</span><span class="sxs-lookup"><span data-stu-id="0d5b6-186">File</span></span> |
| <span data-ttu-id="0d5b6-187">11</span><span class="sxs-lookup"><span data-stu-id="0d5b6-187">11</span></span>        | <span data-ttu-id="0d5b6-188">IP-адрес</span><span class="sxs-lookup"><span data-stu-id="0d5b6-188">IP</span></span> |
| <span data-ttu-id="0d5b6-189">12</span><span class="sxs-lookup"><span data-stu-id="0d5b6-189">12</span></span>        | <span data-ttu-id="0d5b6-190">Пул пакетов</span><span class="sxs-lookup"><span data-stu-id="0d5b6-190">Packet Pool</span></span> |
| <span data-ttu-id="0d5b6-191">13</span><span class="sxs-lookup"><span data-stu-id="0d5b6-191">13</span></span>        | <span data-ttu-id="0d5b6-192">Сокет TCP</span><span class="sxs-lookup"><span data-stu-id="0d5b6-192">TCP Socket</span></span> |
| <span data-ttu-id="0d5b6-193">14</span><span class="sxs-lookup"><span data-stu-id="0d5b6-193">14</span></span>        | <span data-ttu-id="0d5b6-194">Сокет UDP</span><span class="sxs-lookup"><span data-stu-id="0d5b6-194">UDP Socket</span></span> |
| <span data-ttu-id="0d5b6-195">15–20</span><span class="sxs-lookup"><span data-stu-id="0d5b6-195">15-20</span></span>     | <span data-ttu-id="0d5b6-196">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="0d5b6-196">Reserved</span></span> |  
| <span data-ttu-id="0d5b6-197">21</span><span class="sxs-lookup"><span data-stu-id="0d5b6-197">21</span></span>        | <span data-ttu-id="0d5b6-198">Устройство стека узла USB</span><span class="sxs-lookup"><span data-stu-id="0d5b6-198">USB Host Stack Device</span></span> |
| <span data-ttu-id="0d5b6-199">22</span><span class="sxs-lookup"><span data-stu-id="0d5b6-199">22</span></span>        | <span data-ttu-id="0d5b6-200">Интерфейс стека узла USB</span><span class="sxs-lookup"><span data-stu-id="0d5b6-200">USB Host Stack Interface</span></span> |
| <span data-ttu-id="0d5b6-201">23</span><span class="sxs-lookup"><span data-stu-id="0d5b6-201">23</span></span>        | <span data-ttu-id="0d5b6-202">Конечная точка узла USB</span><span class="sxs-lookup"><span data-stu-id="0d5b6-202">USB Host Endpoint</span></span> |
| <span data-ttu-id="0d5b6-203">24</span><span class="sxs-lookup"><span data-stu-id="0d5b6-203">24</span></span>        | <span data-ttu-id="0d5b6-204">Класс узла USB</span><span class="sxs-lookup"><span data-stu-id="0d5b6-204">USB Host Class</span></span> |
| <span data-ttu-id="0d5b6-205">25</span><span class="sxs-lookup"><span data-stu-id="0d5b6-205">25</span></span>        | <span data-ttu-id="0d5b6-206">USB-устройство</span><span class="sxs-lookup"><span data-stu-id="0d5b6-206">USB Device</span></span> |
| <span data-ttu-id="0d5b6-207">26</span><span class="sxs-lookup"><span data-stu-id="0d5b6-207">26</span></span>        | <span data-ttu-id="0d5b6-208">Интерфейс USB-устройства</span><span class="sxs-lookup"><span data-stu-id="0d5b6-208">USB Device Interface</span></span> |
| <span data-ttu-id="0d5b6-209">27</span><span class="sxs-lookup"><span data-stu-id="0d5b6-209">27</span></span>        | <span data-ttu-id="0d5b6-210">Конечная точка USB-устройства</span><span class="sxs-lookup"><span data-stu-id="0d5b6-210">USB Device Endpoint</span></span> |
| <span data-ttu-id="0d5b6-211">28</span><span class="sxs-lookup"><span data-stu-id="0d5b6-211">28</span></span>        | <span data-ttu-id="0d5b6-212">Класс USB-устройства</span><span class="sxs-lookup"><span data-stu-id="0d5b6-212">USB Device Class</span></span> |

### <a name="object-pointer"></a><span data-ttu-id="0d5b6-213">Указатель объекта</span><span class="sxs-lookup"><span data-stu-id="0d5b6-213">Object Pointer</span></span>

<span data-ttu-id="0d5b6-214">Указатель объекта определяет адрес объекта, который используется для доступа к этому объекту через API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-214">The object pointer specifies the object address that is used for accessing the object using the ThreadX API.</span></span>

### <a name="object-reserved-fields"></a><span data-ttu-id="0d5b6-215">Зарезервированные поля объекта</span><span class="sxs-lookup"><span data-stu-id="0d5b6-215">Object Reserved Fields</span></span>

<span data-ttu-id="0d5b6-216">Для всех объектов, кроме потоков, зарезервированные поля должны иметь значение 0.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-216">For all objects other than threads, these reserved fields should be 0.</span></span> <span data-ttu-id="0d5b6-217">Для потоков выполняется сохранение приоритета потока в два зарезервированных поля на момент его помещения в реестр.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-217">For threads, the priority of the thread at the time it is entered into the registry is placed in these two reserved fields.</span></span>

### <a name="object-parameters"></a><span data-ttu-id="0d5b6-218">Параметры объекта</span><span class="sxs-lookup"><span data-stu-id="0d5b6-218">Object Parameters</span></span>

<span data-ttu-id="0d5b6-219">Параметры объекта содержат дополнительные сведения об этом объекте.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-219">The object parameters contain supplemental information about the object.</span></span> <span data-ttu-id="0d5b6-220">Ниже описаны дополнительные сведения для каждого объекта ThreadX:</span><span class="sxs-lookup"><span data-stu-id="0d5b6-220">The following describes the supplemental information for each ThreadX object:</span></span>

| <span data-ttu-id="0d5b6-221">**Тип объекта**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-221">**Object Type**</span></span>        | <span data-ttu-id="0d5b6-222">**Параметр 1**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-222">**Parameter 1**</span></span>  | <span data-ttu-id="0d5b6-223">**Параметр 2**</span><span class="sxs-lookup"><span data-stu-id="0d5b6-223">**Parameter 2**</span></span> |
|----------------------- | ---------------- | --------------- |
| <span data-ttu-id="0d5b6-224">Thread</span><span class="sxs-lookup"><span data-stu-id="0d5b6-224">Thread</span></span>                 | <span data-ttu-id="0d5b6-225">Начало стека</span><span class="sxs-lookup"><span data-stu-id="0d5b6-225">Stack Start</span></span>      | <span data-ttu-id="0d5b6-226">Размер стека</span><span class="sxs-lookup"><span data-stu-id="0d5b6-226">Stack Size</span></span> |
| <span data-ttu-id="0d5b6-227">Таймер</span><span class="sxs-lookup"><span data-stu-id="0d5b6-227">Timer</span></span>                  | <span data-ttu-id="0d5b6-228">Начальные такты</span><span class="sxs-lookup"><span data-stu-id="0d5b6-228">Initial Ticks</span></span> | <span data-ttu-id="0d5b6-229">Такты переназначения</span><span class="sxs-lookup"><span data-stu-id="0d5b6-229">Reschedule Ticks</span></span> |
| <span data-ttu-id="0d5b6-230">Очередь</span><span class="sxs-lookup"><span data-stu-id="0d5b6-230">Queue</span></span>                  | <span data-ttu-id="0d5b6-231">Размер очереди</span><span class="sxs-lookup"><span data-stu-id="0d5b6-231">Queue Size</span></span> | <span data-ttu-id="0d5b6-232">Размер сообщения</span><span class="sxs-lookup"><span data-stu-id="0d5b6-232">Message Size</span></span> |
| <span data-ttu-id="0d5b6-233">Semaphore</span><span class="sxs-lookup"><span data-stu-id="0d5b6-233">Semaphore</span></span>              | <span data-ttu-id="0d5b6-234">Начальные экземпляры</span><span class="sxs-lookup"><span data-stu-id="0d5b6-234">Initial Instances</span></span> | - |
| <span data-ttu-id="0d5b6-235">Mutex</span><span class="sxs-lookup"><span data-stu-id="0d5b6-235">Mutex</span></span>                  | <span data-ttu-id="0d5b6-236">Флаг наследования</span><span class="sxs-lookup"><span data-stu-id="0d5b6-236">Inheritance Flag</span></span> | - |
| <span data-ttu-id="0d5b6-237">Группа флагов событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-237">Event Flags Group</span></span>      | - | - |
| <span data-ttu-id="0d5b6-238">Пул блоков</span><span class="sxs-lookup"><span data-stu-id="0d5b6-238">Block Pool</span></span>             | <span data-ttu-id="0d5b6-239">Общее количество блоков</span><span class="sxs-lookup"><span data-stu-id="0d5b6-239">Total Blocks</span></span> | <span data-ttu-id="0d5b6-240">Размер блока</span><span class="sxs-lookup"><span data-stu-id="0d5b6-240">Block Size</span></span> |
| <span data-ttu-id="0d5b6-241">Пул байтов</span><span class="sxs-lookup"><span data-stu-id="0d5b6-241">Byte Pool</span></span>              | <span data-ttu-id="0d5b6-242">Всего байт</span><span class="sxs-lookup"><span data-stu-id="0d5b6-242">Total Bytes</span></span> | - |
| <span data-ttu-id="0d5b6-243">../media</span><span class="sxs-lookup"><span data-stu-id="0d5b6-243">../media</span></span>                  | <span data-ttu-id="0d5b6-244">Объем кэша FAT</span><span class="sxs-lookup"><span data-stu-id="0d5b6-244">Fat Cache Size</span></span> | <span data-ttu-id="0d5b6-245">Размер кэша секторов</span><span class="sxs-lookup"><span data-stu-id="0d5b6-245">Sector Cache Size</span></span> |
| <span data-ttu-id="0d5b6-246">Файл</span><span class="sxs-lookup"><span data-stu-id="0d5b6-246">File</span></span>                   | - | - |
| <span data-ttu-id="0d5b6-247">IP-адрес</span><span class="sxs-lookup"><span data-stu-id="0d5b6-247">IP</span></span>                     | <span data-ttu-id="0d5b6-248">Начало стека</span><span class="sxs-lookup"><span data-stu-id="0d5b6-248">Stack Start</span></span> | <span data-ttu-id="0d5b6-249">Размер стека</span><span class="sxs-lookup"><span data-stu-id="0d5b6-249">Stack Size</span></span> |
| <span data-ttu-id="0d5b6-250">Пул пакетов</span><span class="sxs-lookup"><span data-stu-id="0d5b6-250">Packet Pool</span></span>            | <span data-ttu-id="0d5b6-251">Packet Size</span><span class="sxs-lookup"><span data-stu-id="0d5b6-251">Packet Size</span></span> | <span data-ttu-id="0d5b6-252">Количество пакетов</span><span class="sxs-lookup"><span data-stu-id="0d5b6-252">Number of Packets</span></span> |
| <span data-ttu-id="0d5b6-253">Сокет TCP</span><span class="sxs-lookup"><span data-stu-id="0d5b6-253">TCP Socket</span></span>             | <span data-ttu-id="0d5b6-254">IP-адрес</span><span class="sxs-lookup"><span data-stu-id="0d5b6-254">IP address</span></span> | <span data-ttu-id="0d5b6-255">Размер окна</span><span class="sxs-lookup"><span data-stu-id="0d5b6-255">Window Size</span></span> |
| <span data-ttu-id="0d5b6-256">Сокет UDP</span><span class="sxs-lookup"><span data-stu-id="0d5b6-256">UDP Socket</span></span>             | <span data-ttu-id="0d5b6-257">IP-адрес</span><span class="sxs-lookup"><span data-stu-id="0d5b6-257">IP address</span></span> | <span data-ttu-id="0d5b6-258">Предел очереди RX</span><span class="sxs-lookup"><span data-stu-id="0d5b6-258">RX Queue Max</span></span> |

### <a name="object-name"></a><span data-ttu-id="0d5b6-259">Имени объекта</span><span class="sxs-lookup"><span data-stu-id="0d5b6-259">Object Name</span></span>

<span data-ttu-id="0d5b6-260">Имя объекта содержит имя объекта ThreadX.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-260">The object name contains the name of the ThreadX object.</span></span> <span data-ttu-id="0d5b6-261">Это то же имя, которое передается в ThreadX при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-261">The name is the name provided to ThreadX at the time the object was created.</span></span> <span data-ttu-id="0d5b6-262">По умолчанию имя объекта ограничивается длиной 32 символа.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-262">By default, the object name has a maximum of 32 characters.</span></span> <span data-ttu-id="0d5b6-263">Если реальное имя длиннее 32 символов, оно усекается.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-263">Actual names greater than 32 characters are truncated.</span></span>

## <a name="event-trace-entries"></a><span data-ttu-id="0d5b6-264">Записи трассировки событий</span><span class="sxs-lookup"><span data-stu-id="0d5b6-264">Event Trace Entries</span></span>

<span data-ttu-id="0d5b6-265">Записи трассировки событий находятся в нижнем сегменте буфера трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-265">The event trace entries are found in the bottom portion of the event trace buffer.</span></span> <span data-ttu-id="0d5b6-266">Эти записи хранятся в циклическом списке, в котором указатель текущей записи указывает на самую старую запись.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-266">The entries are maintained in a circular list, with the current entry pointer pointing to the oldest entry.</span></span> <span data-ttu-id="0d5b6-267">Количество записей в этом списке вычисляется с помощью вызова ***tx_trace_enable***.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-267">The number of entries in the list is calculated by the ***tx_trace_enable*** call.</span></span>

<span data-ttu-id="0d5b6-268">Каждая запись в реестре объектов содержит сведения о конкретном событии трассировки ThreadX.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-268">Each object register entry contains information about a specific ThreadX trace event.</span></span> <span data-ttu-id="0d5b6-269">Следующая структура данных определяет каждую запись событий трассировки:</span><span class="sxs-lookup"><span data-stu-id="0d5b6-269">The following data structure defines each trace event entry:</span></span>

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a><span data-ttu-id="0d5b6-270">Указатель потока</span><span class="sxs-lookup"><span data-stu-id="0d5b6-270">Thread Pointer</span></span>

<span data-ttu-id="0d5b6-271">Указатель потока содержит адрес потока, который выполнялся при наступлении текущего события.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-271">The thread pointer contains the address of the thread running at the time of this event.</span></span> <span data-ttu-id="0d5b6-272">Если событие наступило на этапе инициализации (когда еще нет потоков), в этот указатель сохраняется значение 0xF0F0F0F0.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-272">If the event occurred during initialization (no thread running), the value of this pointer is 0xF0F0F0F0.</span></span> <span data-ttu-id="0d5b6-273">Если событие наступило при выполнении обработчика прерываний (ISR), в этот указатель сохраняется значение 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-273">If the event occurred during an Interrupt Service Routine (ISR), the value of this pointer is 0xFFFFFFFF.</span></span> <span data-ttu-id="0d5b6-274">Если запись еще не использовалась, значение этого указателя равно 0.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-274">If the entry has not yet been used, the value of this pointer is 0.</span></span>

### <a name="thread-priority"></a><span data-ttu-id="0d5b6-275">Приоритет потока</span><span class="sxs-lookup"><span data-stu-id="0d5b6-275">Thread Priority</span></span>

<span data-ttu-id="0d5b6-276">Поле приоритета потока содержит значения приоритета и порога вытеснения для того потока, который выполнялся при наступлении этого события.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-276">The thread priority field contains the thread priority and preemption-threshold of the thread that was running at the time of this event.</span></span> <span data-ttu-id="0d5b6-277">Если присутствует контекст прерывания (указатель потока равен 0xFFFFFFFF), значение этого поля содержит не приоритет, а значение ***_tx_thread_current_ptr*** на момент наступления события.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-277">If an interrupt context is present (thread pointer is 0xFFFFFFFF), the value of this field is not the priority but instead the value of ***_tx_thread_current_ptr*** at the time of the event.</span></span> <span data-ttu-id="0d5b6-278">В противном случае значение этого поля равно 0.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-278">Otherwise, the value of this field is 0.</span></span>

### <a name="event-id"></a><span data-ttu-id="0d5b6-279">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="0d5b6-279">Event ID</span></span>

<span data-ttu-id="0d5b6-280">Идентификатор события определяет событие, которое произошло.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-280">The event ID specifies the event that took place.</span></span> <span data-ttu-id="0d5b6-281">В среде ThreadX допускаются идентификаторы событий трассировки в диапазоне от 1 до 1024.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-281">Valid ThreadX trace event IDs range from 1 through 1024.</span></span> <span data-ttu-id="0d5b6-282">Значения 1025 и выше зарезервированы для пользовательских событий.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-282">Values starting at 1025 and above are reserved for user-specific events.</span></span> <span data-ttu-id="0d5b6-283">Полное описание идентификаторов событий ThreadX размещено в файле ***tx_trace.h***.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-283">Please refer to the ***tx_trace.h*** file for the complete definition of ThreadX event IDs.</span></span></td>

### <a name="information-fields-1-4"></a><span data-ttu-id="0d5b6-284">Информационные поля (1–4)</span><span class="sxs-lookup"><span data-stu-id="0d5b6-284">Information Fields (1-4)</span></span>

<span data-ttu-id="0d5b6-285">Информационные поля содержат дополнительные сведения о конкретном событии.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-285">The information fields contain additional information about the specific event.</span></span> <span data-ttu-id="0d5b6-286">Полное описание информационных полей для каждого из определенных идентификаторов событий ThreadX размещено в файле ***tx_trace.h***.</span><span class="sxs-lookup"><span data-stu-id="0d5b6-286">Please refer to the ***tx_trace.h*** file for the complete description of the information fields for each of the defined ThreadX event IDs.</span></span>