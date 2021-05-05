---
title: Общие сведения о ОСРВ Azure ThreadX
description: Azure ThreadX — это усовершенствованная операционная система реального времени (ОСРВ), разработанная специально для глубоко встраиваемых приложений.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: e786e5bf1f434ec9543823dee8784b677a2b371f
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171392"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="70839-103">Обзор ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="70839-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="70839-104">ОСРВ Azure ThreadX — это усовершенствованная промышленная операционная система реального времени (ОСРВ), разработанная корпорацией Майкрософт специально для глубоко встраиваемых приложений IoT реального времени.</span><span class="sxs-lookup"><span data-stu-id="70839-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="70839-105">ОСРВ Azure ThreadX предоставляет возможности расширенного планирования, обмен данными, синхронизацию, таймеры, управление памятью и управление прерываниями.</span><span class="sxs-lookup"><span data-stu-id="70839-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="70839-106">Кроме того, в Azure RTO ThreadX реализовано множество дополнительных функций, включая архитектуру picokernel™, технологию планирования preemption-threshold™, технологию event-chaining™, профилирование выполнения, метрики производительности и трассировку системных событий.</span><span class="sxs-lookup"><span data-stu-id="70839-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="70839-107">Благодаря чрезвычайной простоте использования ОСРВ Azure ThreadX является идеальным выбором для самых требовательных внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="70839-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="70839-108">Начиная с 2017 года было развернуто более 6 200 000 000 экземпляров ОСРВ Azure ThreadX в самых разных продуктах, включая потребительские устройства, медицинские электронные устройства и оборудование для управления производством.</span><span class="sxs-lookup"><span data-stu-id="70839-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="70839-109">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="70839-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="70839-110">Службы ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="70839-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="70839-111">Динамическое создание потоков.</span><span class="sxs-lookup"><span data-stu-id="70839-111">Dynamic thread creation</span></span>
* <span data-ttu-id="70839-112">Неограниченное число потоков.</span><span class="sxs-lookup"><span data-stu-id="70839-112">No limits on the number of threads</span></span>
* <span data-ttu-id="70839-113">Основные API потоков:</span><span class="sxs-lookup"><span data-stu-id="70839-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="70839-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="70839-114">tx_thread_create</span></span>
  * <span data-ttu-id="70839-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="70839-115">tx_thread_delete</span></span>
  * <span data-ttu-id="70839-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="70839-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="70839-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="70839-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="70839-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="70839-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="70839-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="70839-119">tx_thread_reset</span></span>
  * <span data-ttu-id="70839-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="70839-120">tx_thread_resume</span></span>
  * <span data-ttu-id="70839-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="70839-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="70839-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="70839-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="70839-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="70839-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="70839-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="70839-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="70839-125">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="70839-126">Очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="70839-126">Message Queues</span></span>

* <span data-ttu-id="70839-127">Динамическое создание очередей.</span><span class="sxs-lookup"><span data-stu-id="70839-127">Dynamic queue creation</span></span>
* <span data-ttu-id="70839-128">Неограниченное число очередей.</span><span class="sxs-lookup"><span data-stu-id="70839-128">No limits on the number of queues</span></span>
* <span data-ttu-id="70839-129">Сообщения копируются по значению (или по ссылке через указатель).</span><span class="sxs-lookup"><span data-stu-id="70839-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="70839-130">Размер сообщений от 1 до 16 32-разрядных слов.</span><span class="sxs-lookup"><span data-stu-id="70839-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="70839-131">Необязательная приостановка потоков при пустой и переполненной очереди.</span><span class="sxs-lookup"><span data-stu-id="70839-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="70839-132">Необязательное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="70839-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="70839-133">Основные API очереди сообщений:</span><span class="sxs-lookup"><span data-stu-id="70839-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="70839-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="70839-134">tx_queue_create</span></span>
  * <span data-ttu-id="70839-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="70839-135">tx_queue_delete</span></span>
  * <span data-ttu-id="70839-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="70839-136">tx_queue_flush</span></span>
  * <span data-ttu-id="70839-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="70839-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="70839-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="70839-138">tx_queue_receive</span></span>
  * <span data-ttu-id="70839-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="70839-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="70839-140">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="70839-141">Семафоры со счетчиком</span><span class="sxs-lookup"><span data-stu-id="70839-141">Counting Semaphores</span></span>

* <span data-ttu-id="70839-142">Динамическое создание семафоров.</span><span class="sxs-lookup"><span data-stu-id="70839-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="70839-143">Неограниченное число семафоров.</span><span class="sxs-lookup"><span data-stu-id="70839-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="70839-144">32-разрядные семафоры со счетчиком (от 0 до 4 294 967 295).</span><span class="sxs-lookup"><span data-stu-id="70839-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="70839-145">Поддержка схемы "производитель — получатель" и защиты ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70839-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="70839-146">Необязательная приостановка потоков при недоступности семафора.</span><span class="sxs-lookup"><span data-stu-id="70839-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="70839-147">Необязательное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="70839-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="70839-148">Основные API семафоров:</span><span class="sxs-lookup"><span data-stu-id="70839-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="70839-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="70839-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="70839-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="70839-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="70839-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="70839-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="70839-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="70839-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="70839-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="70839-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="70839-154">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="70839-155">Mutexes</span><span class="sxs-lookup"><span data-stu-id="70839-155">Mutexes</span></span>

* <span data-ttu-id="70839-156">Динамическое создание мьютексов.</span><span class="sxs-lookup"><span data-stu-id="70839-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="70839-157">Неограниченное число мьютексов.</span><span class="sxs-lookup"><span data-stu-id="70839-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="70839-158">Поддержка защиты вложенных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="70839-158">Nested resource protection supported</span></span>
* <span data-ttu-id="70839-159">Поддержка необязательного наследования приоритета.</span><span class="sxs-lookup"><span data-stu-id="70839-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="70839-160">Необязательная приостановка потоков при недоступности мьютекса.</span><span class="sxs-lookup"><span data-stu-id="70839-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="70839-161">Необязательное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="70839-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="70839-162">Основные API мьютексов:</span><span class="sxs-lookup"><span data-stu-id="70839-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="70839-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="70839-163">tx_mutex_create</span></span>
  * <span data-ttu-id="70839-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="70839-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="70839-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="70839-165">tx_mutex_get</span></span>
  * <span data-ttu-id="70839-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="70839-166">tx_mutex_put</span></span>
* <span data-ttu-id="70839-167">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="70839-168">Флаги событий</span><span class="sxs-lookup"><span data-stu-id="70839-168">Event Flags</span></span>

* <span data-ttu-id="70839-169">Динамическое создание группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="70839-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="70839-170">Неограниченное количество групп флагов событий.</span><span class="sxs-lookup"><span data-stu-id="70839-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="70839-171">Синхронизация одного или нескольких потоков.</span><span class="sxs-lookup"><span data-stu-id="70839-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="70839-172">Поддержка атомарных операций get и clear.</span><span class="sxs-lookup"><span data-stu-id="70839-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="70839-173">Необязательная приостановка нескольких потоков для набора событий с логическими условиями (И, ИЛИ).</span><span class="sxs-lookup"><span data-stu-id="70839-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="70839-174">Необязательное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="70839-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="70839-175">Основные API флагов событий:</span><span class="sxs-lookup"><span data-stu-id="70839-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="70839-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="70839-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="70839-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="70839-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="70839-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="70839-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="70839-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="70839-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="70839-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="70839-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="70839-181">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="70839-182">Пулы блоков памяти</span><span class="sxs-lookup"><span data-stu-id="70839-182">Block Memory Pools</span></span>

* <span data-ttu-id="70839-183">Динамическое создание пулов блоков.</span><span class="sxs-lookup"><span data-stu-id="70839-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="70839-184">Неограниченное количество пулов блоков.</span><span class="sxs-lookup"><span data-stu-id="70839-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="70839-185">Неограниченный размер блоков фиксированного размера или пулов.</span><span class="sxs-lookup"><span data-stu-id="70839-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="70839-186">Максимально быстрое выделение и освобождение памяти.</span><span class="sxs-lookup"><span data-stu-id="70839-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="70839-187">Необязательная приостановка потоков при пустом пуле.</span><span class="sxs-lookup"><span data-stu-id="70839-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="70839-188">Необязательное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="70839-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="70839-189">Основные API пула блоков:</span><span class="sxs-lookup"><span data-stu-id="70839-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="70839-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="70839-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="70839-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="70839-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="70839-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="70839-192">tx_block_allocate</span></span>
  * <span data-ttu-id="70839-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="70839-193">tx_block_release</span></span>
* <span data-ttu-id="70839-194">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="70839-195">Пулы байтов памяти</span><span class="sxs-lookup"><span data-stu-id="70839-195">Byte Memory Pools</span></span>

* <span data-ttu-id="70839-196">Динамическое создание пулов байтов.</span><span class="sxs-lookup"><span data-stu-id="70839-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="70839-197">Неограниченное количество пулов байтов.</span><span class="sxs-lookup"><span data-stu-id="70839-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="70839-198">Неограниченный размер пула байтов.</span><span class="sxs-lookup"><span data-stu-id="70839-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="70839-199">Наиболее гибкое выделение и освобождение областей памяти переменной длины.</span><span class="sxs-lookup"><span data-stu-id="70839-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="70839-200">Поддержка сосредоточения выделяемой области.</span><span class="sxs-lookup"><span data-stu-id="70839-200">Allocation size locality supported</span></span>
* <span data-ttu-id="70839-201">Необязательная приостановка потоков при пустом пуле.</span><span class="sxs-lookup"><span data-stu-id="70839-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="70839-202">Необязательное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="70839-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="70839-203">Основные API пула байтов:</span><span class="sxs-lookup"><span data-stu-id="70839-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="70839-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="70839-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="70839-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="70839-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="70839-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="70839-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="70839-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="70839-207">tx_byte_release</span></span>
* <span data-ttu-id="70839-208">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="70839-209">Таймеры приложения</span><span class="sxs-lookup"><span data-stu-id="70839-209">Application Timers</span></span>

* <span data-ttu-id="70839-210">Динамическое создание таймеров.</span><span class="sxs-lookup"><span data-stu-id="70839-210">Dynamic timer creation</span></span>
* <span data-ttu-id="70839-211">Неограниченное число таймеров.</span><span class="sxs-lookup"><span data-stu-id="70839-211">No limits on the number of timers</span></span>
* <span data-ttu-id="70839-212">Поддержка периодических или одноразовых таймеров.</span><span class="sxs-lookup"><span data-stu-id="70839-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="70839-213">Периодические таймеры могут иметь разные начальные значения срока действия.</span><span class="sxs-lookup"><span data-stu-id="70839-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="70839-214">Отсутствие поиска по активации или деактивации таймеров.</span><span class="sxs-lookup"><span data-stu-id="70839-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="70839-215">Всеми таймерами управляет одно прерывание аппаратного таймера.</span><span class="sxs-lookup"><span data-stu-id="70839-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="70839-216">Основные API таймеров:</span><span class="sxs-lookup"><span data-stu-id="70839-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="70839-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="70839-217">tx_timer_create</span></span>
  * <span data-ttu-id="70839-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="70839-218">tx_timer_delete</span></span>
  * <span data-ttu-id="70839-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="70839-219">tx_timer_activate</span></span>
  * <span data-ttu-id="70839-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="70839-220">tx_timer_change</span></span>
  * <span data-ttu-id="70839-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="70839-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="70839-222">Интерфейсы API для получения дополнительных сведений и данных о производительности.</span><span class="sxs-lookup"><span data-stu-id="70839-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="70839-223">Базовый планировщик ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="70839-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="70839-224">Минимальная занимаемая память: 2 КБ флэш-памяти и 1 КБ ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="70839-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="70839-225">Быстрое переключение контекста меньше чем за микросекунду.</span><span class="sxs-lookup"><span data-stu-id="70839-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="70839-226">Полностью детерминированная платформа независимо от количества потоков.</span><span class="sxs-lookup"><span data-stu-id="70839-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="70839-227">Планирование с полным вытеснением на основе приоритета.</span><span class="sxs-lookup"><span data-stu-id="70839-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="70839-228">32 уровней приоритета по умолчанию (при необходимости можно использовать до 1024 уровней).</span><span class="sxs-lookup"><span data-stu-id="70839-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="70839-229">Координированное планирование на уровне приоритета (FIFO).</span><span class="sxs-lookup"><span data-stu-id="70839-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="70839-230">Технология preemption-threshold.</span><span class="sxs-lookup"><span data-stu-id="70839-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="70839-231">Необязательные службы таймеров, включая:</span><span class="sxs-lookup"><span data-stu-id="70839-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="70839-232">создание временных срезов для потоков;</span><span class="sxs-lookup"><span data-stu-id="70839-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="70839-233">задание времени ожидания для всех блокировок;</span><span class="sxs-lookup"><span data-stu-id="70839-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="70839-234">для интерфейсов API требуется прерывание аппаратного таймера.</span><span class="sxs-lookup"><span data-stu-id="70839-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="70839-235">Профилирование выполнения.</span><span class="sxs-lookup"><span data-stu-id="70839-235">Execution profiling</span></span>
* <span data-ttu-id="70839-236">Трассировка на уровне системы.</span><span class="sxs-lookup"><span data-stu-id="70839-236">System-level Trace</span></span>
* <span data-ttu-id="70839-237">Сертифицированная безопасность, соответствующая множеству стандартов.</span><span class="sxs-lookup"><span data-stu-id="70839-237">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="70839-238">Наиболее развертываемая ОСРВ</span><span class="sxs-lookup"><span data-stu-id="70839-238">Most deployed RTOS</span></span>

<span data-ttu-id="70839-239">Согласно данным компании VDC Research, занимающейся исследованиями рынка технологий M2M, по всему миру развернуто более 6 200 000 000 экземпляров ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-239">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="70839-240">Популярность ОСРВ Azure ThreadX — свидетельство ее надежности, качества, размера, производительности, расширенных функций, простоты использования и общих преимуществ для выхода на рынок.</span><span class="sxs-lookup"><span data-stu-id="70839-240">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="70839-241">*"Мы составили траекторию роста присутствия ThreadX на рынках беспроводных технологий и Интернета вещей с момента основания этой компании и были очень впечатлены тем, с какой скоростью ее продукты распространяются в этой отрасли,"*</span><span class="sxs-lookup"><span data-stu-id="70839-241">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="70839-242">— Крис Роммель, исполнительный вице-президент VDC Research.</span><span class="sxs-lookup"><span data-stu-id="70839-242">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="70839-243">Компактность</span><span class="sxs-lookup"><span data-stu-id="70839-243">Small footprint</span></span>

<span data-ttu-id="70839-244">ОСРВ Azure ThreadX требуется очень мало занимаемой памяти — всего 2 КБ области инструкций и 1 КБ ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="70839-244">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="70839-245">В основном это обусловлено одноуровневой архитектурой picokernel™ и автоматическим масштабированием.</span><span class="sxs-lookup"><span data-stu-id="70839-245">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="70839-246">Автоматическое масштабирование означает, что во время компоновки в окончательный образ добавляются только службы (и поддерживающая инфраструктура), используемые приложением.</span><span class="sxs-lookup"><span data-stu-id="70839-246">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="70839-247">Ниже приведены типичные размеры для ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-247">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="70839-248">Служба ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="70839-248">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="70839-249">Типичный размер в байтах</span><span class="sxs-lookup"><span data-stu-id="70839-249">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="70839-250">Основные службы (обязательные)</span><span class="sxs-lookup"><span data-stu-id="70839-250">Core Services (Require)</span></span> |<span data-ttu-id="70839-251">2 000</span><span class="sxs-lookup"><span data-stu-id="70839-251">2,000</span></span>  |
|<span data-ttu-id="70839-252">Службы очередей</span><span class="sxs-lookup"><span data-stu-id="70839-252">Queue Services</span></span>  |<span data-ttu-id="70839-253">900</span><span class="sxs-lookup"><span data-stu-id="70839-253">900</span></span>  |
|<span data-ttu-id="70839-254">Службы флагов событий</span><span class="sxs-lookup"><span data-stu-id="70839-254">Event Flag Services</span></span>  |<span data-ttu-id="70839-255">900</span><span class="sxs-lookup"><span data-stu-id="70839-255">900</span></span>  |
|<span data-ttu-id="70839-256">Службы семафоров</span><span class="sxs-lookup"><span data-stu-id="70839-256">Semaphore Services</span></span>  |<span data-ttu-id="70839-257">450</span><span class="sxs-lookup"><span data-stu-id="70839-257">450</span></span>  |
|<span data-ttu-id="70839-258">Службы мьютексов</span><span class="sxs-lookup"><span data-stu-id="70839-258">Mutex Services</span></span>  |<span data-ttu-id="70839-259">1200</span><span class="sxs-lookup"><span data-stu-id="70839-259">1,200</span></span>  |
|<span data-ttu-id="70839-260">Службы блоков памяти</span><span class="sxs-lookup"><span data-stu-id="70839-260">Block Memory Services</span></span>  |<span data-ttu-id="70839-261">550</span><span class="sxs-lookup"><span data-stu-id="70839-261">550</span></span>  |
|<span data-ttu-id="70839-262">Службы управления байтами памяти</span><span class="sxs-lookup"><span data-stu-id="70839-262">Byte Memory Services</span></span>  |<span data-ttu-id="70839-263">900</span><span class="sxs-lookup"><span data-stu-id="70839-263">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="70839-264">Быстрое выполнение</span><span class="sxs-lookup"><span data-stu-id="70839-264">Fast execution</span></span>

<span data-ttu-id="70839-265">ОСРВ Azure ThreadX достигает переключения контекста меньше чем за микросекунду на самых популярных процессорах, значительно опережая другие коммерческие ОСРВ по этому параметру.</span><span class="sxs-lookup"><span data-stu-id="70839-265">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="70839-266">В дополнение к быстроте ОСРВ Azure ThreadX также является высокодетерминированной.</span><span class="sxs-lookup"><span data-stu-id="70839-266">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="70839-267">Она обеспечивает одинаковую производительность как для 200 потоков, так и для 1 потока.</span><span class="sxs-lookup"><span data-stu-id="70839-267">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="70839-268">Ниже приведены типичные характеристики производительности ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-268">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="70839-269">Быстрая загрузка: ОСРВ Azure ThreadX загружается менее чем за 120 циклов.</span><span class="sxs-lookup"><span data-stu-id="70839-269">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="70839-270">Необязательное отключение базовой проверки на ошибки: базовая проверка на ошибки ОСРВ Azure ThreadX может быть пропущена во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="70839-270">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="70839-271">Это может быть удобно, когда код приложения проверен и больше не требует проверки на наличие ошибок для каждого параметра.</span><span class="sxs-lookup"><span data-stu-id="70839-271">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="70839-272">Обратите внимание на то, что это можно сделать на уровне компилируемого модуля, а не всей системы.</span><span class="sxs-lookup"><span data-stu-id="70839-272">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="70839-273">Структура picokernel™: службы не размещаются на разных уровнях, что устраняет ненужные временные затраты при вызове функций.</span><span class="sxs-lookup"><span data-stu-id="70839-273">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="70839-274">\* Оптимизированная обработка прерываний: только временные регистры сохраняются или восстанавливаются при входе в подпрограммы ISR и выходе из них, если только не требуется вытеснение.</span><span class="sxs-lookup"><span data-stu-id="70839-274">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="70839-275">Оптимизированная обработка API.</span><span class="sxs-lookup"><span data-stu-id="70839-275">Optimized API Processing:</span></span>

    |<span data-ttu-id="70839-276">Служба ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="70839-276">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="70839-277">Время работы службы в микросекундах\*</span><span class="sxs-lookup"><span data-stu-id="70839-277">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="70839-278">Приостановка потока</span><span class="sxs-lookup"><span data-stu-id="70839-278">Thread Suspend</span></span>  |<span data-ttu-id="70839-279">0,6</span><span class="sxs-lookup"><span data-stu-id="70839-279">0.6</span></span>  |
    |<span data-ttu-id="70839-280">Возобновление потока</span><span class="sxs-lookup"><span data-stu-id="70839-280">Thread Resume</span></span>  |<span data-ttu-id="70839-281">0,6</span><span class="sxs-lookup"><span data-stu-id="70839-281">0.6</span></span>  |
    |<span data-ttu-id="70839-282">Отправка в очередь</span><span class="sxs-lookup"><span data-stu-id="70839-282">Queue Send</span></span>  |<span data-ttu-id="70839-283">0,3</span><span class="sxs-lookup"><span data-stu-id="70839-283">0.3</span></span>  |
    |<span data-ttu-id="70839-284">Получение в очередь</span><span class="sxs-lookup"><span data-stu-id="70839-284">Queue Receive</span></span>  |<span data-ttu-id="70839-285">0,3</span><span class="sxs-lookup"><span data-stu-id="70839-285">0.3</span></span>  |
    |<span data-ttu-id="70839-286">Получение семафора</span><span class="sxs-lookup"><span data-stu-id="70839-286">Get Semaphore</span></span>  |<span data-ttu-id="70839-287">0,2</span><span class="sxs-lookup"><span data-stu-id="70839-287">0.2</span></span>  |
    |<span data-ttu-id="70839-288">Задание семафора</span><span class="sxs-lookup"><span data-stu-id="70839-288">Put Semaphore</span></span>  |<span data-ttu-id="70839-289">0,2</span><span class="sxs-lookup"><span data-stu-id="70839-289">0.2</span></span>  |
    |<span data-ttu-id="70839-290">Переключение контекста</span><span class="sxs-lookup"><span data-stu-id="70839-290">Context Switch</span></span>  |<span data-ttu-id="70839-291">0,4</span><span class="sxs-lookup"><span data-stu-id="70839-291">0.4</span></span>  |
    |<span data-ttu-id="70839-292">Реагирование на прерывание</span><span class="sxs-lookup"><span data-stu-id="70839-292">Interrupt Response</span></span>  |<span data-ttu-id="70839-293">0,0–0,6</span><span class="sxs-lookup"><span data-stu-id="70839-293">0.0 – 0.6</span></span>  |

    <span data-ttu-id="70839-294">\**Показатели производительности приведены для типичного процессора с частотой 200 МГц*.</span><span class="sxs-lookup"><span data-stu-id="70839-294">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="70839-295">Усовершенствованные технологии</span><span class="sxs-lookup"><span data-stu-id="70839-295">Advanced technology</span></span>

<span data-ttu-id="70839-296">ОСРВ Azure ThreadX — это усовершенствованная технология, наиболее важная функция которой — планирование с порогом вытеснения.</span><span class="sxs-lookup"><span data-stu-id="70839-296">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="70839-297">Это уникальная функция ОСРВ Azure ThreadX, которая была предметом обширных научных исследований.</span><span class="sxs-lookup"><span data-stu-id="70839-297">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="70839-298">Например, ознакомьтесь со статьей [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf) (Планирование задач с фиксированным приоритетом с использованием порога вытеснения), написанной Юнь Ванем, Университет Конкордия, и Манасом Саксеной, 
Питтсбургский Университет.</span><span class="sxs-lookup"><span data-stu-id="70839-298">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="70839-299">Рассмотрим возможности ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-299">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="70839-300">Полные и исчерпывающие средства многозадачности:</span><span class="sxs-lookup"><span data-stu-id="70839-300">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="70839-301">потоки, таймеры приложения, очереди сообщений, семафоры со счетчиком, мьютексы, флаги событий, пулы блоков и байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="70839-301">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="70839-302">Планирование с вытеснением на основе приоритета.</span><span class="sxs-lookup"><span data-stu-id="70839-302">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="70839-303">Гибкость приоритетов — до 1024 уровней приоритета.</span><span class="sxs-lookup"><span data-stu-id="70839-303">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="70839-304">Координированное планирование.</span><span class="sxs-lookup"><span data-stu-id="70839-304">Cooperative Scheduling</span></span>
* <span data-ttu-id="70839-305">Preemption-threshold™ — уникальная технология ОСРВ Azure ThreadX, которая помогает сократить число переключений контекста и обеспечить применение расписаний (согласно научным исследованиям).</span><span class="sxs-lookup"><span data-stu-id="70839-305">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="70839-306">Защита памяти с помощью модулей ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-306">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="70839-307">Полностью детерминированные операции.</span><span class="sxs-lookup"><span data-stu-id="70839-307">Fully Deterministic</span></span>
* <span data-ttu-id="70839-308">Трассировка событий — запись *n* последних событий системы или приложения.</span><span class="sxs-lookup"><span data-stu-id="70839-308">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="70839-309">Технология event-chaining™ позволяет зарегистрировать функцию обратного вызова уведомления, зависящую от приложения, для каждого объекта связи или синхронизации ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-309">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="70839-310">Модули ОСРВ Azure ThreadX с необязательной защитой памяти.</span><span class="sxs-lookup"><span data-stu-id="70839-310">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="70839-311">Метрики производительности времени выполнения:</span><span class="sxs-lookup"><span data-stu-id="70839-311">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="70839-312">число возобновлений потоков;</span><span class="sxs-lookup"><span data-stu-id="70839-312">Number of thread resumptions</span></span>
  * <span data-ttu-id="70839-313">число приостановок потоков;</span><span class="sxs-lookup"><span data-stu-id="70839-313">Number of thread suspensions</span></span>
  * <span data-ttu-id="70839-314">число запрошенных вытеснений потоков;</span><span class="sxs-lookup"><span data-stu-id="70839-314">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="70839-315">число асинхронных прерываний с вытеснением потоков;</span><span class="sxs-lookup"><span data-stu-id="70839-315">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="70839-316">число инверсий приоритета потоков;</span><span class="sxs-lookup"><span data-stu-id="70839-316">Number of thread priority inversions</span></span>
  * <span data-ttu-id="70839-317">число освобождений потоков.</span><span class="sxs-lookup"><span data-stu-id="70839-317">Number of thread relinquishes</span></span>
* <span data-ttu-id="70839-318">Набор профилей выполнения (EPK).</span><span class="sxs-lookup"><span data-stu-id="70839-318">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="70839-319">Отдельный с стек прерываний.</span><span class="sxs-lookup"><span data-stu-id="70839-319">Separate Interrupt Stack</span></span>
* <span data-ttu-id="70839-320">Анализ стека во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="70839-320">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="70839-321">Оптимизированная обработка прерываний таймера.</span><span class="sxs-lookup"><span data-stu-id="70839-321">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="70839-322">Поддержка многоядерных платформ (AMP и SMP)</span><span class="sxs-lookup"><span data-stu-id="70839-322">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="70839-323">Стандартная ОСРВ Azure ThreadX часто используется для асимметричной многопроцессорной обработки (AMP), где отдельная копия ОСРВ Azure ThreadX и приложение (или ОС Linux) выполняются на каждом ядре и взаимодействуют друг с другом через общую память либо какой-либо механизм межпроцессорного взаимодействия, например OpenAMP (ОСРВ Azure ThreadX поддерживает OpenAMP).</span><span class="sxs-lookup"><span data-stu-id="70839-323">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="70839-324">Это самая типичная многоядерная конфигурация на основе ОСРВ Azure ThreadX, которая будет наиболее производительной, если приложение сможет эффективно загружать все процессоры.</span><span class="sxs-lookup"><span data-stu-id="70839-324">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="70839-325">Для сред, в которых загрузка процессоров отличается высокой динамичностью, доступна ОСРВ Azure ThreadX Symetric Multiprocessing (SMP) для симметричной многопроцессорной обработки, поддерживающая следующие семейства процессоров:</span><span class="sxs-lookup"><span data-stu-id="70839-325">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="70839-326">ARM Cortex-Ax;</span><span class="sxs-lookup"><span data-stu-id="70839-326">ARM Cortex-Ax</span></span>
* <span data-ttu-id="70839-327">ARM Cortex-Rx;</span><span class="sxs-lookup"><span data-stu-id="70839-327">ARM Cortex-Rx</span></span>
* <span data-ttu-id="70839-328">ARM Cortex-A5x (64-разрядные версии);</span><span class="sxs-lookup"><span data-stu-id="70839-328">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="70839-329">MIPS 34K, 1004K и interAptiv;</span><span class="sxs-lookup"><span data-stu-id="70839-329">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="70839-330">PowerPC;</span><span class="sxs-lookup"><span data-stu-id="70839-330">PowerPC</span></span>
* <span data-ttu-id="70839-331">Synopsys ARC HS;</span><span class="sxs-lookup"><span data-stu-id="70839-331">Synopsys ARC HS</span></span>
* <span data-ttu-id="70839-332">x86.</span><span class="sxs-lookup"><span data-stu-id="70839-332">x86</span></span>

<span data-ttu-id="70839-333">ОСРВ Azure ThreadX SMP выполняет динамическую балансировку нагрузки для *n* процессоров и позволяет любому потоку на любом ядре обращаться ко всем ресурсам ОСРВ Azure ThreadX (очереди, семафоры, флаги событий, пулы памяти и т. д.).</span><span class="sxs-lookup"><span data-stu-id="70839-333">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="70839-334">ОСРВ Azure ThreadX SMP обеспечивает полный набор API ОСРВ Azure ThreadX на всех ядрах и предоставляет следующие новые API, предназначенные для операций SMP:</span><span class="sxs-lookup"><span data-stu-id="70839-334">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="70839-335">Защита памяти с помощью модулей ОСРВ Azure ThreadX</span><span class="sxs-lookup"><span data-stu-id="70839-335">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="70839-336">Дополнительный продукт, называемый модулями ОСРВ Azure ThreadX, позволяет объединить один или несколько потоков приложения в модуль, который можно загружать динамически и запускать (или выполнять на месте) на целевом оборудовании.</span><span class="sxs-lookup"><span data-stu-id="70839-336">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="70839-337">Модули позволяют выполнять обновление на месте, устранять ошибки и секционировать программы, чтобы большие приложения занимали только тот объем памяти, который необходимым для активных потоков.</span><span class="sxs-lookup"><span data-stu-id="70839-337">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="70839-338">Модули также используют адресное пространство, отдельное от ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-338">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="70839-339">Это позволяет ОСРВ Azure ThreadX применять защиту памяти (посредством MPU или MMU) для модуля, которая не позволяет непреднамеренному обращению извне модуля повредить какой-либо другой программный компонент.</span><span class="sxs-lookup"><span data-stu-id="70839-339">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>


## <a name="misra-compliant"></a><span data-ttu-id="70839-340">Соответствие требованиям MISRA</span><span class="sxs-lookup"><span data-stu-id="70839-340">MISRA compliant</span></span>

<span data-ttu-id="70839-341">Исходный код ОСРВ Azure ThreadX и ОСРВ Azure ThreadX SMP соответствует требованиям MISRA-C:2004 и MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="70839-341">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="70839-342">MISRA C — это набор руководств по программированию критических систем с использованием языка программирования C.</span><span class="sxs-lookup"><span data-stu-id="70839-342">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="70839-343">Первоначальные рекомендации MISRA C главным образом были нацелены на приложения для автомобилестроения, но теперь MISRA C широко признается стандартом, применимым к любому приложению со строгими требованиями к безопасности.</span><span class="sxs-lookup"><span data-stu-id="70839-343">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="70839-344">ОСРВ Azure SMP ThreadX соответствует всем требуемым и обязательным правилам стандартов MISRA-C:2004 и MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="70839-344">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Сертификация MISRA":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="70839-346">Поддержка большинства популярных архитектур</span><span class="sxs-lookup"><span data-stu-id="70839-346">Supports most popular architectures</span></span>

<span data-ttu-id="70839-347">ОСРВ Azure ThreadX работает на большинстве популярных 32- или 64-разрядных микропроцессоров. Она не требует дополнительной настройки, полностью протестирована и поддерживается на разных архитектурах, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="70839-347">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="70839-348">Analog Devices: SHARC, Blackfin, CM4xx;</span><span class="sxs-lookup"><span data-stu-id="70839-348">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="70839-349">Andes Core: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="70839-349">Andes Core: RISC-V</span></span>
* <span data-ttu-id="70839-350">Ambiqmicro: микроконтроллеры Apollo;</span><span class="sxs-lookup"><span data-stu-id="70839-350">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="70839-351">ARM: ARM7, ARM9, ARM11; Cortex-M0, M3, M4, M7, A15, A5, A7, A8, A9, A5x (64-разрядные версии), A7x (64-разрядные версии), R4, R5; TrustZone ARMv8-M;</span><span class="sxs-lookup"><span data-stu-id="70839-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="70839-352">Cadence: Xtensa, Diamond;</span><span class="sxs-lookup"><span data-stu-id="70839-352">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="70839-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi;</span><span class="sxs-lookup"><span data-stu-id="70839-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="70839-354">Cypress: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="70839-354">Cypress: RISC-V</span></span>
* <span data-ttu-id="70839-355">EnSilica: eSi-RISC;</span><span class="sxs-lookup"><span data-stu-id="70839-355">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="70839-356">Infineon: XMC1000, XMC4000, TriCore;</span><span class="sxs-lookup"><span data-stu-id="70839-356">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="70839-357">Intel и Intel FPGA: x36 и Pentium, XScale, NIOS II, Cyclone, Arria 10;</span><span class="sxs-lookup"><span data-stu-id="70839-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="70839-358">Microchip: AVR32, ARM7, ARM9; Cortex-M3, M4, M7; SAM3, 4, 7, 9, A, C, D, E, G, L, SV; PIC24 и PIC32;</span><span class="sxs-lookup"><span data-stu-id="70839-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="70839-359">Microsemi: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="70839-359">Microsemi: RISC-V</span></span>
* <span data-ttu-id="70839-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3 и M4;</span><span class="sxs-lookup"><span data-stu-id="70839-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="70839-361">Renesas: SH, HS, V850, RX, RZ, Synergy;</span><span class="sxs-lookup"><span data-stu-id="70839-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="70839-362">Silicon Labs: EFM32;</span><span class="sxs-lookup"><span data-stu-id="70839-362">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="70839-363">Synopsys: ARC 600, 700, ARC EM, ARC HS;</span><span class="sxs-lookup"><span data-stu-id="70839-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="70839-364">ST: STM32, ARM7, ARM9, Cortex-M3, M4, M7;</span><span class="sxs-lookup"><span data-stu-id="70839-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="70839-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C;</span><span class="sxs-lookup"><span data-stu-id="70839-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="70839-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class;</span><span class="sxs-lookup"><span data-stu-id="70839-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="70839-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE.</span><span class="sxs-lookup"><span data-stu-id="70839-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="70839-368">Поддержка большинства популярных инструментов</span><span class="sxs-lookup"><span data-stu-id="70839-368">Supports most popular tools</span></span>

<span data-ttu-id="70839-369">ОСРВ Azure ThreadX поддерживает большинство популярных внедренных инструментов разработки, включая решение Embedded Workbench™ от IAR, которое также лучше всего совместимо с ядром ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="70839-369">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="70839-370">Возможна интеграция с дополнительными средства, включая инструменты GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore и все аналоговые устройства.</span><span class="sxs-lookup"><span data-stu-id="70839-370">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>
