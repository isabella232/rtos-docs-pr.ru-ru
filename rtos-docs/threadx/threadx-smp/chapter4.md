---
title: Глава 4. Описание служб ThreadX SMP для ОСРВ Azure
description: В этой главе содержится описание всех служб ThreadX SMP для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816068"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="977b2-103">Глава 4. Описание служб ThreadX SMP для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="977b2-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="977b2-104">В этой главе содержится описание всех служб ThreadX SMP для ОСРВ Azure в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="977b2-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="977b2-105">Их имена составлены таким образом, что все аналогичные службы объединены по группам.</span><span class="sxs-lookup"><span data-stu-id="977b2-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="977b2-106">В разделе "Возвращаемые значения" приведенных ниже описаний выделенные **полужирным шрифтом** значения не затрагиваются определением **TX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="977b2-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="977b2-107">Кроме того, слово **Да** под заголовком **Возможно вытеснение** указывает на то, что вызов службы может возобновить поток с более высоким приоритетом, тем самым вытесняя вызывающий поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="977b2-108">**tx_block_allocate** — *выделение блока памяти фиксированного размера*.</span><span class="sxs-lookup"><span data-stu-id="977b2-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="977b2-109">**tx_block_pool_create** — *создание пула блоков памяти фиксированного размера*.</span><span class="sxs-lookup"><span data-stu-id="977b2-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="977b2-110">**tx_block_pool_delete** — *удаление пула блоков памяти*.</span><span class="sxs-lookup"><span data-stu-id="977b2-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="977b2-111">**tx_block_pool_info_get** — *получение сведений о пуле блоков*.</span><span class="sxs-lookup"><span data-stu-id="977b2-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="977b2-112">**tx_block_pool_performance_info_get** — *получение сведений о производительности пула блоков*.</span><span class="sxs-lookup"><span data-stu-id="977b2-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="977b2-113">**tx_block_pool_performance_system_info_get** — *получение сведений о производительности пула блоков*.</span><span class="sxs-lookup"><span data-stu-id="977b2-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="977b2-114">**tx_block_pool_prioritize** — *назначение приоритета списку приостановки пула блоков*.</span><span class="sxs-lookup"><span data-stu-id="977b2-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="977b2-115">**tx_block_release** — *освобождение блока памяти фиксированного размера*.</span><span class="sxs-lookup"><span data-stu-id="977b2-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="977b2-116">**tx_byte_allocate** — *выделение байтов памяти*.</span><span class="sxs-lookup"><span data-stu-id="977b2-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="977b2-117">**tx_byte_pool_create** — *создание пула памяти в байтах*.</span><span class="sxs-lookup"><span data-stu-id="977b2-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="977b2-118">**tx_byte_pool_delete** — *удаление пула байтов памяти*.</span><span class="sxs-lookup"><span data-stu-id="977b2-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="977b2-119">**tx_byte_pool_info_get** — *получение сведений о пуле байтов*.</span><span class="sxs-lookup"><span data-stu-id="977b2-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="977b2-120">**tx_byte_pool_performance_info_get** — *получение сведений о производительности пула байтов*.</span><span class="sxs-lookup"><span data-stu-id="977b2-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="977b2-121">**tx_byte_pool_performance_system_info_get** — *получение сведений о производительности системы пула байтов*.</span><span class="sxs-lookup"><span data-stu-id="977b2-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="977b2-122">**tx_byte_pool_prioritize** — *назначение приоритета списку приостановки пула байтов*.</span><span class="sxs-lookup"><span data-stu-id="977b2-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="977b2-123">**tx_byte_release** — *освобождение байтов обратно в пул памяти*.</span><span class="sxs-lookup"><span data-stu-id="977b2-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="977b2-124">**tx_event_flags_create** — *создание группы флагов событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="977b2-125">**tx_event_flags_delete** — *удаление группы флагов событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="977b2-126">**tx_event_flags_get** — *получение флагов событий из группы флагов событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="977b2-127">**tx_event_flags_info_get** — *получение сведений о группе флагов событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="977b2-128">**tx_event_flags_performance_info_get** — *получение сведений о производительности группы флагов событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="977b2-129">**tx_event_flags_performance_system_info_get** — *получение сведений о производительности системы*.</span><span class="sxs-lookup"><span data-stu-id="977b2-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="977b2-130">**tx_event_flags_set** — *установка флагов событий в группе флагов событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="977b2-131">**tx_event_flags_set_notify** — *уведомление приложения, когда заданы флаги событий*.</span><span class="sxs-lookup"><span data-stu-id="977b2-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="977b2-132">**tx_interrupt_control** — *включение и отключение прерываний*.</span><span class="sxs-lookup"><span data-stu-id="977b2-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="977b2-133">**tx_mutex_create** — *создание мьютекса взаимного исключения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="977b2-134">**tx_mutex_delete** — *удаление мьютекса взаимного исключения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="977b2-135">**tx_mutex_get** — *получение права владения мьютексом*.</span><span class="sxs-lookup"><span data-stu-id="977b2-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="977b2-136">**tx_mutex_info_get** — *получение сведений о мьютексе*.</span><span class="sxs-lookup"><span data-stu-id="977b2-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="977b2-137">**tx_mutex_performance_info_get** — *получение сведений о производительности мьютекса*.</span><span class="sxs-lookup"><span data-stu-id="977b2-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="977b2-138">**tx_mutex_performance_system_info_get** — *получение сведений о производительности системы мьютекса*.</span><span class="sxs-lookup"><span data-stu-id="977b2-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="977b2-139">**tx_mutex_prioritize** — *назначение приоритета списку приостановки мьютексов*.</span><span class="sxs-lookup"><span data-stu-id="977b2-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="977b2-140">**tx_mutex_put** — *отказ от владения мьютексом*.</span><span class="sxs-lookup"><span data-stu-id="977b2-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="977b2-141">**tx_queue_create** — *создание очереди сообщений*.</span><span class="sxs-lookup"><span data-stu-id="977b2-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="977b2-142">**tx_queue_delete** — *удаление очереди сообщений*.</span><span class="sxs-lookup"><span data-stu-id="977b2-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="977b2-143">**tx_queue_flush** — *очистка очереди сообщений*.</span><span class="sxs-lookup"><span data-stu-id="977b2-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="977b2-144">**tx_queue_front_send** — *отправка сообщения в начало очереди*.</span><span class="sxs-lookup"><span data-stu-id="977b2-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="977b2-145">**tx_mutex_info_get** — *получение сведений об очереди*.</span><span class="sxs-lookup"><span data-stu-id="977b2-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="977b2-146">**tx_queue_performance_info_get** — *получение сведений о производительности очереди*.</span><span class="sxs-lookup"><span data-stu-id="977b2-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="977b2-147">**tx_queue_performance_info_get** — *получение сведений о производительности системы очередей*.</span><span class="sxs-lookup"><span data-stu-id="977b2-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="977b2-148">**tx_queue_prioritize** — *назначение приоритета списку приостановки очереди*.</span><span class="sxs-lookup"><span data-stu-id="977b2-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="977b2-149">**tx_queue_receive** — *получение сообщения из очереди сообщений*.</span><span class="sxs-lookup"><span data-stu-id="977b2-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="977b2-150">**tx_queue_send** — *отправка сообщения в очередь сообщений*.</span><span class="sxs-lookup"><span data-stu-id="977b2-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="977b2-151">**tx_queue_send_notify** — *уведомление приложения, когда сообщение отправлено в очередь*.</span><span class="sxs-lookup"><span data-stu-id="977b2-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="977b2-152">**tx_semaphore_ceiling_put** — *размещение экземпляра в семафоре со счетчиком с верхним пределом*.</span><span class="sxs-lookup"><span data-stu-id="977b2-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="977b2-153">**tx_semaphore_create** — *создание семафора со счетчиком*.</span><span class="sxs-lookup"><span data-stu-id="977b2-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="977b2-154">**tx_semaphore_delete** — *удаление семафора со счетчиком*.</span><span class="sxs-lookup"><span data-stu-id="977b2-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="977b2-155">**tx_semaphore_get** — *получение экземпляра из семафора со счетчиком*.</span><span class="sxs-lookup"><span data-stu-id="977b2-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="977b2-156">**tx_semaphore_info_get** — *получение сведений о семафоре*.</span><span class="sxs-lookup"><span data-stu-id="977b2-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="977b2-157">**tx_semaphore_performance_info_get** — *получение сведений о производительности семафора*.</span><span class="sxs-lookup"><span data-stu-id="977b2-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="977b2-158">**tx_semaphore_performance_system_info_get** — *получение сведений о производительности системы семафора*.</span><span class="sxs-lookup"><span data-stu-id="977b2-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="977b2-159">**tx_semaphore_prioritize** — *назначение приоритета списку приостановки семафора*.</span><span class="sxs-lookup"><span data-stu-id="977b2-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="977b2-160">**tx_semaphore_put** — *размещение экземпляра в семафоре со счетчиком*.</span><span class="sxs-lookup"><span data-stu-id="977b2-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="977b2-161">**tx_semaphore_put_notify** — *уведомление приложения при размещении семафора*.</span><span class="sxs-lookup"><span data-stu-id="977b2-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="977b2-162">**tx_thread_create** — *создание потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="977b2-163">**tx_thread_delete** — *удаление потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="977b2-164">**tx_thread_entry_exit_notify** — *уведомление приложения о входе в поток и выходе из него*.</span><span class="sxs-lookup"><span data-stu-id="977b2-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="977b2-165">**tx_thread_identify** — *получение указателя на поток текущего выполнения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="977b2-166">**tx_thread_info_get** — *получение сведений о потоке*.</span><span class="sxs-lookup"><span data-stu-id="977b2-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="977b2-167">**tx_thread_performance_info_get** — *получение сведений о производительности потока*.</span><span class="sxs-lookup"><span data-stu-id="977b2-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="977b2-168">**tx_thread_performance_system_info_get** — *получение сведений о производительности системы потока*.</span><span class="sxs-lookup"><span data-stu-id="977b2-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="977b2-169">**tx_thread_preemption_change** — *изменение порога вытеснения для потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="977b2-170">**tx_thread_priority_change** — *изменение приоритета потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="977b2-171">**tx_thread_relinquish** — *передача управления другим потокам приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="977b2-172">**tx_thread_reset** — *сброс потока*.</span><span class="sxs-lookup"><span data-stu-id="977b2-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="977b2-173">**tx_thread_resume** — *возобновление приостановленного потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="977b2-174">**tx_thread_sleep** — *приостановка текущего потока в течение указанного времени*.</span><span class="sxs-lookup"><span data-stu-id="977b2-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="977b2-175">**tx_thread_smp_core_exclude** — *исключение выполнения потока в наборе ядер*.</span><span class="sxs-lookup"><span data-stu-id="977b2-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="977b2-176">**tx_thread_smp_core_exclude_get** — *получение исключения для текущего ядра потока*.</span><span class="sxs-lookup"><span data-stu-id="977b2-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="977b2-177">**tx_thread_smp_core_get** — *получение текущего выполняемого ядра вызывающего объекта*.</span><span class="sxs-lookup"><span data-stu-id="977b2-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="977b2-178">**tx_thread_stack_error_notify** — *регистрация обратного вызова уведомления об ошибках стека потока*.</span><span class="sxs-lookup"><span data-stu-id="977b2-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="977b2-179">**tx_thread_suspend** — *приостановка потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="977b2-180">**tx_thread_terminate** — *завершение потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="977b2-181">**tx_thread_time_slice_change** — *изменение интервала времени потока приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="977b2-182">**tx_thread_wait_abort** — *прерывание приостановки указанного потока*.</span><span class="sxs-lookup"><span data-stu-id="977b2-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="977b2-183">**tx_time_get** — *получение текущего времени*.</span><span class="sxs-lookup"><span data-stu-id="977b2-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="977b2-184">**tx_time_get** — *установка текущего времени*.</span><span class="sxs-lookup"><span data-stu-id="977b2-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="977b2-185">**tx_timer_activate** — *активация таймера приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="977b2-186">**tx_timer_change** — *изменение таймера приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="977b2-187">**tx_timer_create** — *создание таймера приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="977b2-188">**tx_timer_deactivate** — *деактивация таймера приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="977b2-189">**tx_timer_delete** — *удаление таймера приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="977b2-190">**tx_timer_info_get** — *получение сведений о таймере приложения*.</span><span class="sxs-lookup"><span data-stu-id="977b2-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="977b2-191">**tx_timer_performance_info_get** — *получение сведений о производительности таймера*.</span><span class="sxs-lookup"><span data-stu-id="977b2-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="977b2-192">**tx_timer_performance_info_get** — *получение сведений о производительности системы таймера*.</span><span class="sxs-lookup"><span data-stu-id="977b2-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="977b2-193">**tx_timer_smp_core_exclude** — *исключение выполнения таймера в наборе ядер*.</span><span class="sxs-lookup"><span data-stu-id="977b2-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="977b2-194">**tx_thread_smp_core_exclude_get** — *получение исключения для текущего ядра таймера*.</span><span class="sxs-lookup"><span data-stu-id="977b2-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="977b2-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-195">tx_block_allocate</span></span>
<span data-ttu-id="977b2-196">Выделение блока памяти фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="977b2-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-197">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-198">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-198">Description</span></span>

<span data-ttu-id="977b2-199">Эта служба выделяет блок памяти фиксированного размера из указанного пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="977b2-200">Фактический размер блока памяти определяется во время создания пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="977b2-201">Важно убедиться, что код приложения не выполняет запись за пределами выделенного блока памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="977b2-202">В противном случае повреждение происходит в соседнем (обычно следующем) блоке памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="977b2-203">Результаты могут оказаться непредсказуемыми и катастрофическими!</span><span class="sxs-lookup"><span data-stu-id="977b2-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-204">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-204">Parameters</span></span>

- <span data-ttu-id="977b2-205">**pool_ptr** — указатель на созданный ранее пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="977b2-206">**block_ptr** — указатель на указатель блока назначения.</span><span class="sxs-lookup"><span data-stu-id="977b2-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="977b2-207">При успешном выделении адрес выделенного блока памяти помещается в место, куда указывает этот параметр.</span><span class="sxs-lookup"><span data-stu-id="977b2-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="977b2-208">**wait_option** — определяет поведение службы в случае, если нет доступных блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="977b2-209">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-210">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-212">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="977b2-213">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="977b2-214">Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="977b2-215">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока не станет доступен блок памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="977b2-216">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания блока памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-217">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-217">Return Values</span></span>

- <span data-ttu-id="977b2-218">**TX_SUCCESS** (0x00) — успешное выделение блока памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="977b2-219">**TX_DELETED** (0x01) — пул блоков памяти был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-220">**TX_NO_MEMORY** (0x10) — службе не удалось выделить блок памяти в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="977b2-221">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="977b2-222">TX_POOL_ERROR (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="977b2-223">TX_PTR_ERROR (0x03) — недопустимый указатель на указатель назначения.</span><span class="sxs-lookup"><span data-stu-id="977b2-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="977b2-224">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-225">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-225">Allowed From</span></span>

<span data-ttu-id="977b2-226">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-227">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-227">Preemption Possible</span></span>

<span data-ttu-id="977b2-228">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-229">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-229">Example</span></span>

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="977b2-230">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-230">See Also</span></span>

- <span data-ttu-id="977b2-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-231">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="977b2-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="977b2-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-238">tx_block_pool_create</span></span>
<span data-ttu-id="977b2-239">Создание пула блоков памяти фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="977b2-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-240">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="977b2-241">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-241">Description</span></span>

<span data-ttu-id="977b2-242">Эта служба создает пул блоков памяти фиксированного размера.</span><span class="sxs-lookup"><span data-stu-id="977b2-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="977b2-243">Указанная область памяти разделяется на максимально возможное количество блоков памяти фиксированного размера по формуле:</span><span class="sxs-lookup"><span data-stu-id="977b2-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="977b2-244">**всего блоков** = (**всего байтов**) / (**размер блока** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="977b2-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-245">Каждый блок памяти содержит один указатель на служебные данные, который невидим для пользователя и представлен в предыдущей формуле аргументом "sizeof(void \*)".</span><span class="sxs-lookup"><span data-stu-id="977b2-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-246">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-246">Parameters</span></span>

- <span data-ttu-id="977b2-247">**pool_ptr** — указатель на блок управления пулом блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="977b2-248">**name_ptr** — указатель на имя пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="977b2-249">**block_size** — количество байтов в каждом блоке памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="977b2-250">**pool_start** — начальный адрес пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="977b2-251">Начальный адрес должен быть выровнен по размеру типа данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="977b2-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="977b2-252">**pool_size** — общее количество байтов, доступных для пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-253">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-253">Return Values</span></span>

- <span data-ttu-id="977b2-254">**TX_SUCCESS** (0x00) — успешное создание пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="977b2-255">TX_POOL_ERROR (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="977b2-256">Либо указатель имеет значение NULL, либо пул уже создан.</span><span class="sxs-lookup"><span data-stu-id="977b2-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="977b2-257">TX_PTR_ERROR (0x03) — недопустимый начальный адрес пула.</span><span class="sxs-lookup"><span data-stu-id="977b2-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="977b2-258">TX_SIZE_ERROR (0x05) — недопустимый размер пула.</span><span class="sxs-lookup"><span data-stu-id="977b2-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="977b2-259">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-260">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-260">Allowed From</span></span>

<span data-ttu-id="977b2-261">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-262">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-262">Preemption Possible</span></span>

<span data-ttu-id="977b2-263">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-263">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-264">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-264">Example</span></span>

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-265">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-265">See Also</span></span>

- <span data-ttu-id="977b2-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-266">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="977b2-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="977b2-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-273">tx_block_pool_delete</span></span>

<span data-ttu-id="977b2-274">Удаление пула блоков памяти</span><span class="sxs-lookup"><span data-stu-id="977b2-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-275">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-276">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-276">Description</span></span>

<span data-ttu-id="977b2-277">Эта служба удаляет указанный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="977b2-278">Все потоки, приостановленные в ожидании блока памяти из этого пула, возобновляются и получают статус возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="977b2-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-279">Обязанность по управлению областью памяти, связанной с пулом, который станет доступным после завершения этой службы, лежит на приложении.</span><span class="sxs-lookup"><span data-stu-id="977b2-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="977b2-280">Кроме того, приложение должно предотвращать использование удаленного пула или его прежних блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-281">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-281">Parameters</span></span>

- <span data-ttu-id="977b2-282">**pool_ptr** — указатель на созданный ранее пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-283">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-283">Return Values</span></span>

- <span data-ttu-id="977b2-284">**TX_SUCCESS** (0x00) — успешное удаление пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="977b2-285">TX_POOL_ERROR (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="977b2-286">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-287">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-287">Allowed From</span></span>

<span data-ttu-id="977b2-288">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-289">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-289">Preemption Possible</span></span>

<span data-ttu-id="977b2-290">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-291">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-291">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-292">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-292">See Also</span></span>

- <span data-ttu-id="977b2-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-293">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-294">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="977b2-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="977b2-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="977b2-301">Получение сведений о пуле блоков</span><span class="sxs-lookup"><span data-stu-id="977b2-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-302">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="977b2-303">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-303">Description</span></span>

<span data-ttu-id="977b2-304">Эта служба получает сведения об указанном пуле блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-305">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-305">Parameters</span></span>

- <span data-ttu-id="977b2-306">**pool_ptr** — указатель на созданный ранее пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="977b2-307">**name** — указатель на назначение для указателя имени пула блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="977b2-308">**available** — указатель на назначение для количества доступных блоков в пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="977b2-309">**total_blocks** — указатель на назначение для общего количества блоков в пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="977b2-310">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого пула блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="977b2-311">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этом пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="977b2-312">**next_pool** — указатель на назначение для указателя следующего созданного пула блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-313">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-314">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-314">Return Values</span></span>

- <span data-ttu-id="977b2-315">**TX_SUCCESS** (0x00) — получение информации об успешном пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="977b2-316">TX_POOL_ERROR (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-317">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-317">Allowed From</span></span>

<span data-ttu-id="977b2-318">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-319">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-319">Example</span></span>

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-320">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-320">See Also</span></span>

- <span data-ttu-id="977b2-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-321">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-322">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="977b2-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="977b2-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="977b2-330">Получение сведений о производительности пула блоков</span><span class="sxs-lookup"><span data-stu-id="977b2-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-331">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="977b2-332">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-332">Description</span></span>

<span data-ttu-id="977b2-333">Эта служба получает сведения о производительности указанного пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-334">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO**, чтобы эта служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-335">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-335">Parameters</span></span>

- <span data-ttu-id="977b2-336">**pool_ptr** — указатель на созданный ранее пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="977b2-337">**allocates** — указатель на назначение для количества запросов на выделение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="977b2-338">**releases** — указатель на назначение для количества запросов на выход, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="977b2-339">**suspensions** — указатель на назначение для количества приостановок выделения потоков в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="977b2-340">**timeouts** — указатель на назначение для количества истечений выделенного времени для размещения в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-341">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-342">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-342">Return Values</span></span>

- <span data-ttu-id="977b2-343">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="977b2-344">**TX_PTR_ERROR** (0x03) — недопустимый указатель на пул блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="977b2-345">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-346">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-346">Allowed From</span></span>

<span data-ttu-id="977b2-347">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-348">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-348">Example</span></span>

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-349">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-349">See Also</span></span>

- <span data-ttu-id="977b2-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-350">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-351">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="977b2-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="977b2-358">Получение сведений о производительности системы пулов блоков</span><span class="sxs-lookup"><span data-stu-id="977b2-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-359">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-360">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-360">Description</span></span>

<span data-ttu-id="977b2-361">Эта служба получает сведения о производительности всех пулов блоков памяти в приложении.</span><span class="sxs-lookup"><span data-stu-id="977b2-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-362">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO**, чтобы эта служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-363">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-363">Parameters</span></span>

- <span data-ttu-id="977b2-364">**allocates** — указатель на назначение для общего количества запросов на выделение, выполненных во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="977b2-365">**releases** — указатель на назначение для общего количества запросов на освобождение, выполненных во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="977b2-366">**suspensions** — указатель на назначение для общего количества приостановок потоков для выделения во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="977b2-367">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки для выделения во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-368">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-369">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-369">Return Values</span></span>

- <span data-ttu-id="977b2-370">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы пулов блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="977b2-371">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-372">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-372">Allowed From</span></span>

<span data-ttu-id="977b2-373">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-374">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-374">Example</span></span>

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-375">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-375">See Also</span></span>

- <span data-ttu-id="977b2-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-376">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-377">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="977b2-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="977b2-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="977b2-384">Назначение приоритета списку приостановки пула блоков</span><span class="sxs-lookup"><span data-stu-id="977b2-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-385">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-386">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-386">Description</span></span>

<span data-ttu-id="977b2-387">Эта служба помещает поток с наивысшим приоритетом, приостановленный для блока памяти в этом пуле, в начале списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="977b2-388">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="977b2-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-389">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-389">Parameters</span></span> 

- <span data-ttu-id="977b2-390">**pool_ptr** — указатель на блок управления пулом блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-391">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-391">Return Values</span></span>

- <span data-ttu-id="977b2-392">**TX_SUCCESS** (0x00) — успешное назначение приоритета в пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="977b2-393">TX_POOL_ERROR (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-394">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-394">Allowed From</span></span>

<span data-ttu-id="977b2-395">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-396">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-396">Preemption Possible</span></span>

<span data-ttu-id="977b2-397">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-397">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-398">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-398">Example</span></span>

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-399">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-399">See Also</span></span>

- <span data-ttu-id="977b2-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-400">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-401">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="977b2-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="977b2-407">tx_block_release</span></span>

<span data-ttu-id="977b2-408">Освобождение блока памяти фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="977b2-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-409">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-410">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-410">Description</span></span>

<span data-ttu-id="977b2-411">Эта служба освобождает ранее выделенный блок обратно в соответствующий пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="977b2-412">Если один или несколько потоков приостановлены в ожидании блоков памяти из этого пула, первый приостановленный поток получает этот блок памяти и возобновляется.</span><span class="sxs-lookup"><span data-stu-id="977b2-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-413">Приложение должно предотвратить использование области блока памяти после ее освобождения в пул.</span><span class="sxs-lookup"><span data-stu-id="977b2-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-414">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-414">Parameters</span></span>

- <span data-ttu-id="977b2-415">**block_ptr** — указатель на ранее выделенный блок памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-416">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-416">Return Values</span></span>

- <span data-ttu-id="977b2-417">**TX_SUCCESS** (0x00) — успешное освобождение блока памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="977b2-418">TX_PTR_ERROR (0x03) — недопустимый указатель на блок памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-419">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-419">Allowed From</span></span>

<span data-ttu-id="977b2-420">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-421">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-421">Preemption Possible</span></span>

<span data-ttu-id="977b2-422">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-423">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-423">Example</span></span>

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-424">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-424">See Also</span></span>

- <span data-ttu-id="977b2-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-425">tx_block_allocate</span></span>
- <span data-ttu-id="977b2-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-426">tx_block_pool_create</span></span>
- <span data-ttu-id="977b2-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="977b2-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="977b2-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="977b2-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-432">tx_byte_allocate</span></span>

<span data-ttu-id="977b2-433">Выделение байтов памяти</span><span class="sxs-lookup"><span data-stu-id="977b2-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-434">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-435">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-435">Description</span></span>

<span data-ttu-id="977b2-436">Эта служба выделяет указанное число байтов из указанного пула байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="977b2-437">Важно убедиться, что код приложения не выполняет запись за пределами выделенного блока памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="977b2-438">В противном случае повреждение происходит в соседнем (обычно следующем) блоке памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="977b2-439">Результаты могут оказаться непредсказуемыми и катастрофическими!</span><span class="sxs-lookup"><span data-stu-id="977b2-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-440">Производительность этой службы является функцией размера блока и объемом фрагментации в пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="977b2-441">Следовательно, эту службу не следует использовать во время критических по времени потоков выполнения.</span><span class="sxs-lookup"><span data-stu-id="977b2-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-442">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-442">Parameters</span></span>

- <span data-ttu-id="977b2-443">**pool_ptr** — указатель на ранее созданный пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="977b2-444">**memory_ptr** — указатель на указатель целевой памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="977b2-445">При успешном выделении адрес выделенной области памяти помещается в место, куда указывает этот параметр.</span><span class="sxs-lookup"><span data-stu-id="977b2-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="977b2-446">**memory_size** — количество запрошенных байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="977b2-447">**wait_option** — определяет поведение службы, если недостаточно памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="977b2-448">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-449">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-451">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-452">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-453">*Это единственный допустимый параметр, если служба вызывается из инициализации.*</span><span class="sxs-lookup"><span data-stu-id="977b2-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="977b2-454">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока не станет доступным достаточный объем памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="977b2-455">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-456">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-456">Return Values</span></span>

- <span data-ttu-id="977b2-457">**TX_SUCCESS** (0x00) — успешное выделение памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="977b2-458">**TX_DELETED** (0x01) — пул памяти был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-459">**TX_NO_MEMORY** (0x10) — службе не удалось выделить память в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="977b2-460">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-461">TX_POOL_ERROR (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="977b2-462">TX_PTR_ERROR (0x03) — недопустимый указатель на указатель назначения.</span><span class="sxs-lookup"><span data-stu-id="977b2-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="977b2-463">TX_SIZE_ERROR (0x05) — запрошенный размер равен нулю или превышает размер пула.</span><span class="sxs-lookup"><span data-stu-id="977b2-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="977b2-464">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="977b2-465">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-466">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-466">Allowed From</span></span>

<span data-ttu-id="977b2-467">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-468">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-468">Preemption Possible</span></span>

<span data-ttu-id="977b2-469">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-470">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-470">Example</span></span>

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-471">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-471">See Also</span></span>

- <span data-ttu-id="977b2-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="977b2-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="977b2-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-479">tx_byte_pool_create</span></span>

<span data-ttu-id="977b2-480">Создание пула памяти в байтах</span><span class="sxs-lookup"><span data-stu-id="977b2-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-481">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="977b2-482">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-482">Description</span></span>

<span data-ttu-id="977b2-483">Эта служба создает пул байтов памяти в указанной области.</span><span class="sxs-lookup"><span data-stu-id="977b2-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="977b2-484">Изначально пул состоит из одного очень большого свободного блока.</span><span class="sxs-lookup"><span data-stu-id="977b2-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="977b2-485">Однако при выделении памяти пул разбивается на более мелкие блоки.</span><span class="sxs-lookup"><span data-stu-id="977b2-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-486">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-486">Parameters</span></span>

- <span data-ttu-id="977b2-487">**pool_ptr** — указатель на блок управления пулом памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="977b2-488">**name_ptr** — указатель на имя пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="977b2-489">**pool_start** — начальный адрес пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="977b2-490">Начальный адрес должен быть выровнен по размеру типа данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="977b2-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="977b2-491">**pool_size** — общее количество байтов, доступных для пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-492">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-492">Return Values</span></span>

- <span data-ttu-id="977b2-493">**TX_SUCCESS** (0x00) — успешное создание пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="977b2-494">TX_POOL_ERROR (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="977b2-495">Либо указатель имеет значение NULL, либо пул уже создан.</span><span class="sxs-lookup"><span data-stu-id="977b2-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="977b2-496">TX_PTR_ERROR (0x03) — недопустимый начальный адрес пула.</span><span class="sxs-lookup"><span data-stu-id="977b2-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="977b2-497">TX_SIZE_ERROR (0x05) — недопустимый размер пула.</span><span class="sxs-lookup"><span data-stu-id="977b2-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="977b2-498">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-499">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-499">Allowed From</span></span>

<span data-ttu-id="977b2-500">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-501">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-501">Preemption Possible</span></span>

<span data-ttu-id="977b2-502">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-502">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-503">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-503">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-504">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-504">See Also</span></span>

- <span data-ttu-id="977b2-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-505">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="977b2-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="977b2-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="977b2-513">Удаление пула байтов памяти</span><span class="sxs-lookup"><span data-stu-id="977b2-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-514">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-515">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-515">Description</span></span>

<span data-ttu-id="977b2-516">Эта служба удаляет указанный пул байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="977b2-517">Все потоки, приостановленные в ожидании памяти из этого пула, возобновляются и получают состояние возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="977b2-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-518">Обязанность по управлению областью памяти, связанной с пулом, который станет доступным после завершения этой службы, лежит на приложении.</span><span class="sxs-lookup"><span data-stu-id="977b2-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="977b2-519">Кроме того, приложение должно предотвратить использование удаленного пула или памяти, выделенной ранее.</span><span class="sxs-lookup"><span data-stu-id="977b2-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-520">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-520">Parameters</span></span> 

- <span data-ttu-id="977b2-521">**pool_ptr** — указатель на ранее созданный пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-522">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-522">Return Values</span></span>

- <span data-ttu-id="977b2-523">**TX_SUCCESS** (0x00) — успешное удаление пула памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="977b2-524">TX_POOL_ERROR (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="977b2-525">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-526">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-526">Allowed From</span></span>

<span data-ttu-id="977b2-527">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-528">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-528">Preemption Possible</span></span>

<span data-ttu-id="977b2-529">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-530">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-531">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-531">See Also</span></span>

- <span data-ttu-id="977b2-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-532">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="977b2-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="977b2-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="977b2-540">Получение сведений о пуле байтов</span><span class="sxs-lookup"><span data-stu-id="977b2-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-541">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="977b2-542">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-542">Description</span></span>

<span data-ttu-id="977b2-543">Эта служба получает сведения об указанном пуле байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-544">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-544">Parameters</span></span>

- <span data-ttu-id="977b2-545">**pool_ptr** — указатель на ранее созданный пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="977b2-546">**name** — указатель на назначение для указателя на имя пула байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="977b2-547">**available** — указатель на назначение для количества доступных байтов в пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="977b2-548">**fragments** — указатель на назначение для общего количества фрагментов памяти в пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="977b2-549">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого пула байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="977b2-550">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этом пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="977b2-551">**next_pool** — указатель на назначение для указателя следующего созданного пула байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-552">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-553">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-553">Return Values</span></span>

- <span data-ttu-id="977b2-554">**TX_SUCCESS** (0x00) — успешное получение сведений о пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="977b2-555">TX_POOL_ERROR (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-556">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-556">Allowed From</span></span>

<span data-ttu-id="977b2-557">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-558">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-558">Preemption Possible</span></span>

<span data-ttu-id="977b2-559">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-559">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-560">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-560">Example</span></span>

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-561">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-561">See Also</span></span>

- <span data-ttu-id="977b2-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-562">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="977b2-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="977b2-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="977b2-570">Получение сведений о производительности пула байтов</span><span class="sxs-lookup"><span data-stu-id="977b2-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-571">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-572">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-572">Description</span></span>

<span data-ttu-id="977b2-573">Эта служба получает сведения о производительности указанного пула байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-574">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**, чтобы эта служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-575">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-575">Parameters</span></span>

- <span data-ttu-id="977b2-576">**pool_ptr** — указатель на ранее созданный пул байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="977b2-577">**allocates** — указатель на назначение для количества запросов на выделение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="977b2-578">**releases** — указатель на назначение для количества запросов на выход, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="977b2-579">**fragments_searched** — указатель на назначение для количества фрагментов внутренней памяти, поиск которых выполнялся во время запросов на выделение в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="977b2-580">**merges** — указатель на назначение для количества блоков внутренней памяти, объединенных во время запросов на выделение в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="977b2-581">**splits** — указатель на назначение для количества разделенных блоков внутренней памяти (фрагментов), созданных во время запросов на выделение в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="977b2-582">**suspensions** — указатель на назначение для количества приостановок выделения потоков в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="977b2-583">**timeouts** — указатель на назначение для количества истечений выделенного времени для размещения в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-584">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-585">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-585">Return Values</span></span>

- <span data-ttu-id="977b2-586">TX_SUCCESS (0x00) — успешное получение сведений о производительности пула байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="977b2-587">**TX_PTR_ERROR** (0x03) — недопустимый указатель на пул байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="977b2-588">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-589">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-589">Allowed From</span></span>

<span data-ttu-id="977b2-590">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-591">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-591">Example</span></span>

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-592">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-592">See Also</span></span>

- <span data-ttu-id="977b2-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-593">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="977b2-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="977b2-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="977b2-601">Получение сведений о производительности системы пула байтов</span><span class="sxs-lookup"><span data-stu-id="977b2-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-602">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="977b2-603">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-603">Description</span></span>

<span data-ttu-id="977b2-604">Эта служба получает сведения о производительности всех пулов байтов памяти в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-605">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**, чтобы эта служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-606">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-606">Parameters</span></span>

- <span data-ttu-id="977b2-607">**allocates** — указатель на назначение для количества запросов на выделение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="977b2-608">**releases** — указатель на назначение для количества запросов на выход, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="977b2-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="977b2-609">**fragments_searched** — указатель на назначение для общего количества фрагментов внутренней памяти, поиск которых выполнялся во время запросов на выделение во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="977b2-610">**merges** — указатель на назначение для общего количества внутренних блоков памяти, объединенных во время запросов на выделение во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="977b2-611">**splits** — указатель на назначение для общего количества разделенных блоков внутренней памяти (фрагментов), созданных во время запросов на выделение во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="977b2-612">**suspensions** — указатель на назначение для общего количества приостановок выделения потоков во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="977b2-613">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки для выделения во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-614">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-615">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-615">Return Values</span></span>

- <span data-ttu-id="977b2-616">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула байтов.</span><span class="sxs-lookup"><span data-stu-id="977b2-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="977b2-617">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-618">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-618">Allowed From</span></span>

<span data-ttu-id="977b2-619">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-620">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-620">Example</span></span>

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-621">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-621">See Also</span></span>

- <span data-ttu-id="977b2-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-622">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="977b2-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="977b2-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="977b2-630">Назначение приоритета списку приостановки пула байтов</span><span class="sxs-lookup"><span data-stu-id="977b2-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-631">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-632">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-632">Description</span></span>

<span data-ttu-id="977b2-633">Эта служба размещает поток с наивысшим приоритетом, приостановленный для выделения памяти в этом пуле, в начале списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="977b2-634">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="977b2-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-635">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-635">Parameters</span></span> 

- <span data-ttu-id="977b2-636">**pool_ptr** — указатель на блок управления пулом памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-637">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-637">Return Values</span></span>

- <span data-ttu-id="977b2-638">**TX_SUCCESS** (0x00) — успешное назначение приоритета в пуле памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="977b2-639">TX_POOL_ERROR (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-640">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-640">Allowed From</span></span>

<span data-ttu-id="977b2-641">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-642">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-642">Preemption Possible</span></span>

<span data-ttu-id="977b2-643">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-643">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-644">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-644">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-645">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-645">See Also</span></span>

- <span data-ttu-id="977b2-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-646">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="977b2-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="977b2-653">tx_byte_release</span></span>

<span data-ttu-id="977b2-654">Выход байтов обратно в пул памяти</span><span class="sxs-lookup"><span data-stu-id="977b2-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-655">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-656">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-656">Description</span></span>

<span data-ttu-id="977b2-657">Эта служба освобождает ранее выделенную память обратно в соответствующий пул.</span><span class="sxs-lookup"><span data-stu-id="977b2-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="977b2-658">Если один или несколько потоков приостановили работу в ожидании памяти из этого пула, то каждому приостановленному потоку выделяется память и он возобновляет работу. Этот процесс продолжается, пока не исчерпается память или не закончатся все приостановленные потоки.</span><span class="sxs-lookup"><span data-stu-id="977b2-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="977b2-659">Этот процесс выделения памяти для приостановленных потоков всегда начинается с первого приостановленного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-660">Приложение должно предотвращать использование области памяти после ее освобождения.</span><span class="sxs-lookup"><span data-stu-id="977b2-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-661">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-661">Parameters</span></span>

- <span data-ttu-id="977b2-662">**memory_ptr** — указатель на ранее выделенную область памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-663">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-663">Return Values</span></span>

- <span data-ttu-id="977b2-664">**TX_SUCCESS** (0x00) — успешное освобождение памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="977b2-665">TX_PTR_ERROR (0x03) — недопустимый указатель на область памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="977b2-666">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-667">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-667">Allowed From</span></span>

<span data-ttu-id="977b2-668">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-669">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-669">Preemption Possible</span></span>

<span data-ttu-id="977b2-670">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-671">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-672">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-672">See Also</span></span>

- <span data-ttu-id="977b2-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="977b2-673">tx_byte_allocate</span></span>
- <span data-ttu-id="977b2-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="977b2-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="977b2-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="977b2-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="977b2-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="977b2-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="977b2-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-680">tx_event_flags_create</span></span>

<span data-ttu-id="977b2-681">Создание группы флагов событий</span><span class="sxs-lookup"><span data-stu-id="977b2-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-682">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-683">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-683">Description</span></span>

<span data-ttu-id="977b2-684">Эта служба создает группу из 32 флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="977b2-685">Все 32 флага событий в группе инициализируются значением 0.</span><span class="sxs-lookup"><span data-stu-id="977b2-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="977b2-686">Каждый флаг события представлен одним битом.</span><span class="sxs-lookup"><span data-stu-id="977b2-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-687">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-687">Parameters</span></span>

- <span data-ttu-id="977b2-688">**group_ptr** — указатель на блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="977b2-689">**name_ptr** — указатель для имени группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-690">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-690">Return Values</span></span>

- <span data-ttu-id="977b2-691">**TX_SUCCESS** (0x00) — успешное создание группы событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="977b2-692">TX_GROUP_ERROR (0x06) — недопустимый указатель на группу событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="977b2-693">Либо указатель имеет значение NULL, либо группа событий уже создана.</span><span class="sxs-lookup"><span data-stu-id="977b2-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="977b2-694">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-695">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-695">Allowed From</span></span>

<span data-ttu-id="977b2-696">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-697">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-697">Preemption Possible</span></span>

<span data-ttu-id="977b2-698">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-698">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-699">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-700">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-700">See Also</span></span>

- <span data-ttu-id="977b2-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-702">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-706">tx_event_flags_set</span></span>
- <span data-ttu-id="977b2-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="977b2-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-708">tx_event_flags_delete</span></span>

<span data-ttu-id="977b2-709">Удаление группы флагов событий</span><span class="sxs-lookup"><span data-stu-id="977b2-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-710">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-711">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-711">Description</span></span>

<span data-ttu-id="977b2-712">Эта служба удаляет указанную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="977b2-713">Все потоки, приостановленные в ожидании событий из этой группы, возобновляются и получают статус возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="977b2-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-714">Перед удалением группы флагов событий приложение должно убедиться, что обратный вызов уведомления об установке значения для этой группы флагов событий завершен (или отключен).</span><span class="sxs-lookup"><span data-stu-id="977b2-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="977b2-715">Кроме того, приложение должно предотвращать все последующие использования удаленной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-716">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-716">Parameters</span></span> 

- <span data-ttu-id="977b2-717">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-718">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-718">Return Values</span></span>

- <span data-ttu-id="977b2-719">**TX_SUCCESS** (0x00) — успешное удаление группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="977b2-720">TX_GROUP_ERROR (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="977b2-721">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-722">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-722">Allowed From</span></span>

<span data-ttu-id="977b2-723">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-724">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-724">Preemption Possible</span></span>

<span data-ttu-id="977b2-725">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-726">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-726">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-727">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-727">See Also</span></span>

- <span data-ttu-id="977b2-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-728">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-729">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-733">tx_event_flags_set</span></span>
- <span data-ttu-id="977b2-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="977b2-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-735">tx_event_flags_get</span></span>

<span data-ttu-id="977b2-736">Получение флагов событий из группы флагов событий</span><span class="sxs-lookup"><span data-stu-id="977b2-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-737">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-738">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-738">Description</span></span>

<span data-ttu-id="977b2-739">Эта служба получает флаги событий из указанной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="977b2-740">Каждая группа флагов событий содержит 32 флага событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="977b2-741">Каждый флаг представлен одним битом.</span><span class="sxs-lookup"><span data-stu-id="977b2-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="977b2-742">Эта служба может получать различные сочетания флагов событий, указанные входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="977b2-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-743">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-743">Parameters</span></span>

- <span data-ttu-id="977b2-744">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="977b2-745">**requested_flags** — 32-разрядная переменная без знака, представляющая флаги запрошенных событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="977b2-746">**get_option** — указывает, требуются ли все или какие-либо из запрошенных флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="977b2-747">Допустимые варианты:</span><span class="sxs-lookup"><span data-stu-id="977b2-747">The following are valid selections:</span></span>
    - <span data-ttu-id="977b2-748">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="977b2-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="977b2-749">**TX_AND_CLEAR**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="977b2-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="977b2-750">**TX_OR**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="977b2-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="977b2-751">**TX_OR_CLEAR**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="977b2-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="977b2-752">TX_AND или TX_AND_CLEAR указывают, что все флаги событий должны присутствовать в группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="977b2-753">TX_OR или TX_OR_CLEAR указывают, что какой-либо флаг события удовлетворяет условию.</span><span class="sxs-lookup"><span data-stu-id="977b2-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="977b2-754">Флаги событий, соответствующие запросу, очищаются (устанавливается значение 0), если указаны TX_AND_CLEAR или TX_OR_CLEAR.</span><span class="sxs-lookup"><span data-stu-id="977b2-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="977b2-755">**actual_flags_ptr** — указатель на место назначения, куда помещаются полученные флаги событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="977b2-756">Обратите внимание, что фактические полученные флаги могут содержать флаги, которые не были запрошены.</span><span class="sxs-lookup"><span data-stu-id="977b2-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="977b2-757">**wait_option** — определяет поведение службы, если выбранные флаги событий не установлены.</span><span class="sxs-lookup"><span data-stu-id="977b2-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="977b2-758">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-759">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-761">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-762">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-763">Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="977b2-764">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока не станут доступными флаги событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="977b2-765">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-766">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-766">Return Values</span></span>

- <span data-ttu-id="977b2-767">**TX_SUCCESS** (0x00) — успешное получение флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="977b2-768">**TX_DELETED** (0x01) — группа флагов событий была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-769">**TX_NO_EVENTS** (0x07) — службе не удалось получить указанные события в течение заданного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="977b2-770">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-771">TX_GROUP_ERROR (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="977b2-772">TX_PTR_ERROR (0x03) — недопустимый указатель для фактических флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="977b2-773">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="977b2-774">TX_OPTION_ERROR (0x08). Указан недопустимый параметр получения.</span><span class="sxs-lookup"><span data-stu-id="977b2-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-775">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-775">Allowed From</span></span>

<span data-ttu-id="977b2-776">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-777">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-777">Preemption Possible</span></span>

<span data-ttu-id="977b2-778">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-779">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-779">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-780">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-780">See Also</span></span>

- <span data-ttu-id="977b2-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-781">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-786">tx_event_flags_set</span></span>
- <span data-ttu-id="977b2-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="977b2-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="977b2-789">Получение сведений о группе флагов событий</span><span class="sxs-lookup"><span data-stu-id="977b2-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-790">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="977b2-791">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-791">Description</span></span>

<span data-ttu-id="977b2-792">Эта служба получает сведения об указанной группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-793">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-793">Parameters</span></span>

- <span data-ttu-id="977b2-794">**group_ptr** — указатель на блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="977b2-795">**name** — указатель на назначение для указателя на имя группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="977b2-796">**current_flags** — указатель на назначение для текущего набора флагов в группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="977b2-797">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этой группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="977b2-798">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этой группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="977b2-799">**next_group** — указатель на назначение для указателя следующей созданной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-800">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-801">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-801">Return Values</span></span>

- <span data-ttu-id="977b2-802">**TX_SUCCESS** (0x00) — успешное получение сведений о группе событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="977b2-803">TX_GROUP_ERROR (0x06) — недопустимый указатель на группу событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-804">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-804">Allowed From</span></span>

<span data-ttu-id="977b2-805">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-806">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-806">Preemption Possible</span></span>

<span data-ttu-id="977b2-807">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-807">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-808">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-808">Example</span></span>

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-809">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-809">See Also</span></span>

- <span data-ttu-id="977b2-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-810">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-812">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-815">tx_event_flags_set</span></span>
- <span data-ttu-id="977b2-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="977b2-817">tx_event_flags_performance info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="977b2-818">Получение сведений о производительности группы флагов событий</span><span class="sxs-lookup"><span data-stu-id="977b2-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-819">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-820">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-820">Description</span></span>

<span data-ttu-id="977b2-821">Эта служба получает сведения о производительности указанной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-822">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-823">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-823">Parameters</span></span>

- <span data-ttu-id="977b2-824">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="977b2-825">**sets** — указатель на назначение для количества запросов на установку флагов событий, выполненных в этой группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="977b2-826">**gets** — указатель на назначение для количества запросов на получение флагов событий, выполненных в этой группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="977b2-827">**suspensions** — указатель на назначение для количества приостановок потоков для получения флагов событий в этой группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="977b2-828">**timeouts** — указатель на назначение для количества истечений времени ожидания во время приостановки для получения флагов событий в этой группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-829">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-830">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-830">Return Values</span></span>

- <span data-ttu-id="977b2-831">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="977b2-832">**TX_PTR_ERROR** (0x03) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="977b2-833">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-834">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-834">Allowed From</span></span>

<span data-ttu-id="977b2-835">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-836">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-836">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-837">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-837">See Also</span></span>

- <span data-ttu-id="977b2-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-838">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-840">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-843">tx_event_flags_set</span></span>
- <span data-ttu-id="977b2-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="977b2-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="977b2-846">Получение сведений о производительности системы</span><span class="sxs-lookup"><span data-stu-id="977b2-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-847">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-848">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-848">Description</span></span>

<span data-ttu-id="977b2-849">Эта служба получает сведения о производительности всех групп флагов событий в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-850">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-851">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-851">Parameters</span></span>

- <span data-ttu-id="977b2-852">**sets** — указатель на назначение для общего количества запросов на установку флагов событий, выполненных для всех групп.</span><span class="sxs-lookup"><span data-stu-id="977b2-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="977b2-853">**gets** — указатель на назначение для общего количества запросов на получение флагов событий, выполненных для всех групп.</span><span class="sxs-lookup"><span data-stu-id="977b2-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="977b2-854">**suspensions** — указатель на назначение для общего количества приостановок получения флагов событий потока во всех группах.</span><span class="sxs-lookup"><span data-stu-id="977b2-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="977b2-855">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки для получения флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-856">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-857">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-857">Return Values</span></span>

- <span data-ttu-id="977b2-858">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="977b2-859">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-860">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-860">Allowed From</span></span>

<span data-ttu-id="977b2-861">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-862">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-862">Example</span></span>

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-863">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-863">See Also</span></span>

- <span data-ttu-id="977b2-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-864">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-866">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-869">tx_event_flags_set</span></span>
- <span data-ttu-id="977b2-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="977b2-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-871">tx_event_flags_set</span></span>

<span data-ttu-id="977b2-872">Установка флагов событий в группе флагов событий</span><span class="sxs-lookup"><span data-stu-id="977b2-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-873">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="977b2-874">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-874">Description</span></span>

<span data-ttu-id="977b2-875">Эта служба устанавливает или очищает флаги событий в группе флагов событий в зависимости от указанного параметра установки.</span><span class="sxs-lookup"><span data-stu-id="977b2-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="977b2-876">Все приостановленные потоки, чей запрос флагов событий удовлетворен, возобновляются.</span><span class="sxs-lookup"><span data-stu-id="977b2-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-877">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-877">Parameters</span></span>

- <span data-ttu-id="977b2-878">**group_ptr** — указатель на созданный ранее блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="977b2-879">**flags_to_set** — указывает флаги событий, которые нужно установить или очистить в зависимости от выбранного установленного параметра.</span><span class="sxs-lookup"><span data-stu-id="977b2-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="977b2-880">**set_option** — указывает, объединены ли указанные флаги событий логическим И или ИЛИ с текущими флагами событий группы.</span><span class="sxs-lookup"><span data-stu-id="977b2-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="977b2-881">Допустимые варианты:</span><span class="sxs-lookup"><span data-stu-id="977b2-881">The following are valid selections:</span></span>
    - <span data-ttu-id="977b2-882">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="977b2-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="977b2-883">**TX_OR** (0x00) — параметр TX_AND означает, что указанные флаги событий объединяются логическим **И** с текущими флагами событий в группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="977b2-884">Этот параметр часто используют для очистки флагов событий в группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="977b2-885">В противном случае, если указан параметр TX_OR, указанные флаги событий объединяются логическим **ИЛИ** с текущими флагами событий в группе.</span><span class="sxs-lookup"><span data-stu-id="977b2-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-886">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-886">Return Values</span></span>

- <span data-ttu-id="977b2-887">**TX_SUCCESS** (0x00) — успешная установка флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="977b2-888">TX_GROUP_ERROR (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="977b2-889">TX_OPTION_ERROR (0x08) — указан недопустимый установленный параметр.</span><span class="sxs-lookup"><span data-stu-id="977b2-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-890">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-890">Allowed From</span></span>

<span data-ttu-id="977b2-891">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-892">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-892">Preemption Possible</span></span>

<span data-ttu-id="977b2-893">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-894">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-894">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-895">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-895">See Also</span></span>

- <span data-ttu-id="977b2-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-896">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-898">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="977b2-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="977b2-904">Уведомление приложения, когда установлены флаги событий</span><span class="sxs-lookup"><span data-stu-id="977b2-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-905">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="977b2-906">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-906">Description</span></span>

<span data-ttu-id="977b2-907">Эта служба регистрирует функцию обратного вызова уведомления, которая вызывается каждый раз, когда один или несколько флагов событий устанавливаются в указанной группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="977b2-908">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="977b2-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-909">Обратному вызову уведомления об установленных флагах событий приложения не разрешено вызывать какой-либо API ThreadX SMP с параметром приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-910">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-910">Parameters</span></span> 
- <span data-ttu-id="977b2-911">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="977b2-912">**events_set_notify** — указатель на функцию уведомления об установленных флагах событий приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="977b2-913">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-914">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-914">Return Values</span></span>

- <span data-ttu-id="977b2-915">**TX_SUCCESS** (0x00) — успешная регистрация уведомления об установке флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="977b2-916">TX_GROUP_ERROR (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="977b2-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="977b2-917">TX_FEATURE_NOT_ENABLED (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="977b2-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-918">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-918">Allowed From</span></span>

<span data-ttu-id="977b2-919">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-920">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-920">Example</span></span>

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a><span data-ttu-id="977b2-921">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-921">See Also</span></span>

- <span data-ttu-id="977b2-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="977b2-922">tx_event_flags_create</span></span>
- <span data-ttu-id="977b2-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="977b2-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="977b2-924">tx_event_flags_get</span></span>
- <span data-ttu-id="977b2-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="977b2-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="977b2-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="977b2-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="977b2-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="977b2-929">tx_interrupt_control</span></span>

<span data-ttu-id="977b2-930">Включение и отключение прерываний</span><span class="sxs-lookup"><span data-stu-id="977b2-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-931">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="977b2-932">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-932">Description</span></span>

<span data-ttu-id="977b2-933">Эта служба включает или отключает прерывания, как указано во входном параметре **new_posture**.</span><span class="sxs-lookup"><span data-stu-id="977b2-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-934">Если эта служба вызывается из потока приложения, состояние прерывания остается частью контекста этого потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="977b2-935">Например, если поток вызывает эту подпрограмму для отключения прерываний, а затем приостанавливает работу, то после возобновления прерывания снова отключаются.</span><span class="sxs-lookup"><span data-stu-id="977b2-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="977b2-936">Эту службу нельзя использовать для включения прерываний во время инициализации!</span><span class="sxs-lookup"><span data-stu-id="977b2-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="977b2-937">Это может привести к непредсказуемым последствиям.</span><span class="sxs-lookup"><span data-stu-id="977b2-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-938">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-938">Parameters</span></span>

- <span data-ttu-id="977b2-939">**new_posture** — этот параметр указывает, отключены или включены прерывания.</span><span class="sxs-lookup"><span data-stu-id="977b2-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="977b2-940">Допустимые значения: **TX_INT_DISABLE и TX_INT_ENABLE.**</span><span class="sxs-lookup"><span data-stu-id="977b2-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="977b2-941">Фактические значения для этих параметров зависят от порта.</span><span class="sxs-lookup"><span data-stu-id="977b2-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="977b2-942">Кроме того, некоторые архитектуры обработки могут поддерживать дополнительные положения отключения прерывания.</span><span class="sxs-lookup"><span data-stu-id="977b2-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="977b2-943">Дополнительные сведения см. в файле **_readme_threadx.txt_** на диске дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="977b2-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-944">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-944">Return Values</span></span>

- <span data-ttu-id="977b2-945">Предыдущее состояние. Эта служба возвращает вызывающему объекту предыдущее состояние прерывания.</span><span class="sxs-lookup"><span data-stu-id="977b2-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="977b2-946">Дает возможность пользователям службы восстанавливать предыдущее состояние после отключения прерываний.</span><span class="sxs-lookup"><span data-stu-id="977b2-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-947">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-947">Allowed From</span></span>

<span data-ttu-id="977b2-948">Потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-949">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-949">Preemption Possible</span></span>

<span data-ttu-id="977b2-950">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-950">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-951">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="977b2-952">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-952">See Also</span></span>

<span data-ttu-id="977b2-953">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="977b2-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-954">tx_mutex_create</span></span>

<span data-ttu-id="977b2-955">Создание мьютекса взаимного исключения</span><span class="sxs-lookup"><span data-stu-id="977b2-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-956">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="977b2-957">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-957">Description</span></span>
    
<span data-ttu-id="977b2-958">Эта служба создает мьютекс для взаимного исключения между потоками для защиты ресурсов.</span><span class="sxs-lookup"><span data-stu-id="977b2-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-959">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-959">Parameters</span></span>

- <span data-ttu-id="977b2-960">**mutex_ptr** — указатель на блок управления мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="977b2-961">**name_ptr** — указатель на имя мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="977b2-962">**priority_inherit** обозначает, поддерживает ли этот мьютекс наследование приоритета.</span><span class="sxs-lookup"><span data-stu-id="977b2-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="977b2-963">Если указано значение TX_INHERIT, то наследование приоритета поддерживается.</span><span class="sxs-lookup"><span data-stu-id="977b2-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="977b2-964">Если же указано TX_NO_INHERIT, то наследование приоритета мьютексом не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="977b2-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-965">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-965">Return Values</span></span>

- <span data-ttu-id="977b2-966">**TX_SUCCESS** (0x00) — успешное создание мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="977b2-967">TX_MUTEX_ERROR (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="977b2-968">Либо указатель имеет значение NULL, либо мьютекс уже создан.</span><span class="sxs-lookup"><span data-stu-id="977b2-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="977b2-969">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="977b2-970">TX_INHERIT_ERROR (0x1F) — недопустимый параметр наследования приоритета.</span><span class="sxs-lookup"><span data-stu-id="977b2-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-971">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-971">Allowed From</span></span>

<span data-ttu-id="977b2-972">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-973">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-973">Preemption Possible</span></span>

<span data-ttu-id="977b2-974">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-974">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-975">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-975">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-976">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-976">See Also</span></span>

- <span data-ttu-id="977b2-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-977">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-978">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="977b2-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="977b2-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-984">tx_mutex_delete</span></span>

<span data-ttu-id="977b2-985">Удаление мьютекса взаимного исключения</span><span class="sxs-lookup"><span data-stu-id="977b2-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-986">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-987">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-987">Description</span></span>

<span data-ttu-id="977b2-988">Эта служба удаляет указанный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="977b2-989">Все потоки, приостановленные в ожидании мьютекса, возобновляются и получают статус возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="977b2-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-990">Приложение должно предотвратить использование удаленного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-991">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-991">Parameters</span></span>

- <span data-ttu-id="977b2-992">**mutex_ptr** — указатель на созданный ранее мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-993">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-993">Return Values</span></span>

- <span data-ttu-id="977b2-994">**TX_SUCCESS** (0x00) — успешное удаление мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="977b2-995">TX_MUTEX_ERROR (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="977b2-996">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-997">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-997">Allowed From</span></span>

<span data-ttu-id="977b2-998">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-999">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-999">Preemption Possible</span></span>

<span data-ttu-id="977b2-1000">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1001">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1002">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1002">See Also</span></span>

- <span data-ttu-id="977b2-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1003">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1004">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="977b2-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="977b2-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1010">tx_mutex_get</span></span>

<span data-ttu-id="977b2-1011">Получение прав на владение мьютексом</span><span class="sxs-lookup"><span data-stu-id="977b2-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1012">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-1013">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1013">Description</span></span>

<span data-ttu-id="977b2-1014">Эта служба пытается получить право на монопольное владение указанным мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="977b2-1015">Если вызывающий поток уже владеет мьютексом, внутренний счетчик увеличивается и возвращается состояние "Успешно выполнено".</span><span class="sxs-lookup"><span data-stu-id="977b2-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="977b2-1016">Если мьютекс принадлежит другому потоку, а текущий поток имеет более высокий приоритет и при создании мьютекса было задано наследование приоритета, приоритет потока с более низким значением будет временно повышен до приоритета вызывающего потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1017">Приоритет потока с более низким значением, владеющий мьютексом с наследованием приоритета, никогда не должен изменяться внешним потоком во время владения мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1018">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1018">Parameters</span></span>

- <span data-ttu-id="977b2-1019">**mutex_ptr** — указатель на созданный ранее мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="977b2-1020">**wait_option** — определяет поведение службы, если мьютекс уже принадлежит другому потоку.</span><span class="sxs-lookup"><span data-stu-id="977b2-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="977b2-1021">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-1022">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-1024">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-1025">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-1026">*Это единственный допустимый параметр, если служба вызывается из инициализации.*</span><span class="sxs-lookup"><span data-stu-id="977b2-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="977b2-1027">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока не станет доступным мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="977b2-1028">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1029">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1029">Return Values</span></span>

- <span data-ttu-id="977b2-1030">**TX_SUCCESS** (0x00) — успешная операция получения мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="977b2-1031">**TX_DELETED** (0x01) — мьютекс был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-1032">**TX_NOT_AVAILABLE** (0x1D) — службе не удалось получить владение мьютексом в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="977b2-1033">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-1034">TX_MUTEX_ERROR (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="977b2-1035">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="977b2-1036">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1037">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1037">Allowed From</span></span>

<span data-ttu-id="977b2-1038">Инициализация, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1039">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1039">Preemption Possible</span></span>

<span data-ttu-id="977b2-1040">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1041">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="977b2-1042">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1042">See Also</span></span>

- <span data-ttu-id="977b2-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1043">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="977b2-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="977b2-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="977b2-1051">Получение сведений о мьютексе</span><span class="sxs-lookup"><span data-stu-id="977b2-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1052">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="977b2-1053">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1053">Description</span></span>

<span data-ttu-id="977b2-1054">Эта служба получает сведения из указанного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1055">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1055">Parameters</span></span>

- <span data-ttu-id="977b2-1056">**mutex_ptr** — указатель на блок управления мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="977b2-1057">**name** — указатель на назначение для указателя на имя мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="977b2-1058">**count** — указатель на назначение для счетчика владения мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="977b2-1059">**owner** — указатель на назначение для указателя потока-владельца.</span><span class="sxs-lookup"><span data-stu-id="977b2-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="977b2-1060">**first_suspended** — указатель на назначение для указателя на поток, который идет первым в списке приостановки этого мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="977b2-1061">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="977b2-1062">**next_mutex** — указатель на назначение для указателя следующего созданного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1063">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1064">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1064">Return Values</span></span>

- <span data-ttu-id="977b2-1065">**TX_SUCCESS** (0x00) — успешное получение сведений о мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="977b2-1066">TX_MUTEX_ERROR (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1067">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1067">Allowed From</span></span>

<span data-ttu-id="977b2-1068">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1069">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1069">Preemption Possible</span></span>

<span data-ttu-id="977b2-1070">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1071">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1071">Example</span></span>

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1072">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1072">See Also</span></span>

- <span data-ttu-id="977b2-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1073">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1075">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="977b2-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="977b2-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="977b2-1081">Получение сведений о производительности мьютекса</span><span class="sxs-lookup"><span data-stu-id="977b2-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1082">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="977b2-1083">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1083">Description</span></span>

<span data-ttu-id="977b2-1084">Эта служба получает сведения о производительности указанного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1085">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_MUTEX_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1086">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1086">Parameters</span></span>

- <span data-ttu-id="977b2-1087">**mutex_ptr** — указатель на созданный ранее мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="977b2-1088">**puts** — указатель на назначение для количества запросов на размещение, выполненных в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="977b2-1089">**gets** — указатель на назначение для количества запросов на получение, выполненных в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="977b2-1090">**suspensions** — указатель на назначение для количества приостановок потоков для получения мьютекса в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="977b2-1091">**timeouts** — указатель на назначение для количества истечений времени ожидания во время приостановки для получения мьютекса в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="977b2-1092">**inversions** — указатель на назначение для количества инверсий приоритета потока в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="977b2-1093">**inheritances** — указатель на назначение для количества операций наследования приоритета потоков для этого мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1094">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1095">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1095">Return Values</span></span>

- <span data-ttu-id="977b2-1096">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="977b2-1097">**TX_PTR_ERROR** (0x03) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="977b2-1098">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1099">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1099">Allowed From</span></span>

<span data-ttu-id="977b2-1100">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1101">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1101">Example</span></span>

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1102">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1102">See Also</span></span>

- <span data-ttu-id="977b2-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1103">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1105">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="977b2-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="977b2-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="977b2-1111">Получение сведений о производительности системы мьютексов</span><span class="sxs-lookup"><span data-stu-id="977b2-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1112">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="977b2-1113">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1113">Description</span></span>

<span data-ttu-id="977b2-1114">Эта служба получает сведения о производительности всех мьютексов в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1115">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_MUTEX_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1116">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1116">Parameters</span></span>

- <span data-ttu-id="977b2-1117">**puts** — указатель на назначение для общего количества запросов на размещение, выполненных во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="977b2-1118">**gets** — указатель на назначение для общего количества запросов на получение, выполненных во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="977b2-1119">**suspensions** — указатель на назначение для общего количества приостановок потоков для получения мьютекса во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="977b2-1120">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки для получения мьютекса во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="977b2-1121">**inversions** — указатель на назначение для общего количества инверсий приоритета потока во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="977b2-1122">**inheritances** — указатель на назначение для общего количества операций наследования приоритета потоков во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1123">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1124">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1124">Return Values</span></span>

- <span data-ttu-id="977b2-1125">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы мьютексов.</span><span class="sxs-lookup"><span data-stu-id="977b2-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="977b2-1126">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1127">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1127">Allowed From</span></span>

<span data-ttu-id="977b2-1128">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1129">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1129">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1130">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1130">See Also</span></span>

- <span data-ttu-id="977b2-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1131">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1133">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="977b2-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="977b2-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="977b2-1139">Назначение приоритета списку приостановки мьютекса</span><span class="sxs-lookup"><span data-stu-id="977b2-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1140">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1141">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1141">Description</span></span>

<span data-ttu-id="977b2-1142">Эта служба размещает поток с наивысшим приоритетом, приостановленный для получения права владения мьютексом, в начале списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="977b2-1143">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="977b2-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1144">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1144">Parameters</span></span> 

- <span data-ttu-id="977b2-1145">**mutex_ptr** — указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1146">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1146">Return Values</span></span>

- <span data-ttu-id="977b2-1147">**TX_SUCCESS** (0x00) — успешное назначение приоритета в мьютексе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="977b2-1148">TX_MUTEX_ERROR (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1149">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1149">Allowed From</span></span>

<span data-ttu-id="977b2-1150">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1151">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1151">Preemption Possible</span></span>

<span data-ttu-id="977b2-1152">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1153">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1153">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1154">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1154">See Also</span></span>

- <span data-ttu-id="977b2-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1155">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1157">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="977b2-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1162">tx_mutex_put</span></span>

<span data-ttu-id="977b2-1163">Освобождение владения мьютексом</span><span class="sxs-lookup"><span data-stu-id="977b2-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1164">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1165">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1165">Description</span></span>

<span data-ttu-id="977b2-1166">Эта служба уменьшает количество владений указанным мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="977b2-1167">Если значение владения равно нулю, мьютекс становится доступным.</span><span class="sxs-lookup"><span data-stu-id="977b2-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1168">Если во время создания мьютекса было выбрано наследование приоритета, приоритет освобождающего потока будет восстановлен до приоритета, который у него был тогда, когда он изначально получил право владения мьютексом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="977b2-1169">Любые другие изменения приоритета, внесенные в освобождающий поток во время владения мьютексом, могут быть отменены.</span><span class="sxs-lookup"><span data-stu-id="977b2-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1170">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1170">Parameters</span></span>

- <span data-ttu-id="977b2-1171">**mutex_ptr** — указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1172">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1172">Return Values</span></span>

- <span data-ttu-id="977b2-1173">**TX_SUCCESS** (0x00) — успешное освобождение мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="977b2-1174">**TX_NOT_OWNED** (0x1E) — мьютекс не принадлежит вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="977b2-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="977b2-1175">TX_MUTEX_ERROR (0x1C). Недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="977b2-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="977b2-1176">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1177">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1177">Allowed From</span></span>

<span data-ttu-id="977b2-1178">Инициализация, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1179">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1179">Preemption Possible</span></span>

<span data-ttu-id="977b2-1180">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1181">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1182">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1182">See Also</span></span>

- <span data-ttu-id="977b2-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1183">tx_mutex_create</span></span>
- <span data-ttu-id="977b2-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="977b2-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1185">tx_mutex_get</span></span>
- <span data-ttu-id="977b2-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="977b2-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="977b2-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="977b2-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1190">tx_queue_create</span></span>

<span data-ttu-id="977b2-1191">Создание очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="977b2-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1192">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="977b2-1193">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1193">Description</span></span>

<span data-ttu-id="977b2-1194">Эта служба создает очередь сообщений, которая обычно используется для взаимодействия между потоками.</span><span class="sxs-lookup"><span data-stu-id="977b2-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="977b2-1195">Общее количество сообщений вычисляется на основе указанного размера сообщения и общего количества байтов в очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1196">Если общее количество байтов, указанное в области памяти очереди, не делится на указанный размер сообщения, оставшиеся байты в области памяти не используются.</span><span class="sxs-lookup"><span data-stu-id="977b2-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1197">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1197">Parameters</span></span>

- <span data-ttu-id="977b2-1198">**queue_ptr** — указатель на блок управления очередью сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="977b2-1199">**name_ptr** — указатель на имя пула очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="977b2-1200">**message_size** задает размер каждого сообщения в очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="977b2-1201">Размеры сообщений варьируются от 1 32-битного слова до 16 32-битных слов.</span><span class="sxs-lookup"><span data-stu-id="977b2-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="977b2-1202">Допустимые параметры размера сообщения — это числовые значения от 1 до 16 включительно.</span><span class="sxs-lookup"><span data-stu-id="977b2-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="977b2-1203">**queue_start** — начальный адрес очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="977b2-1204">Начальный адрес должен быть выровнен по размеру типа данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="977b2-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="977b2-1205">**queue_size** — общее количество байтов, доступных для очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1206">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1206">Return Values</span></span>

- <span data-ttu-id="977b2-1207">**TX_SUCCESS** (0x00) — успешное создание очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="977b2-1208">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="977b2-1209">Либо указатель имеет значение NULL, либо очередь уже создана.</span><span class="sxs-lookup"><span data-stu-id="977b2-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="977b2-1210">TX_PTR_ERROR (0x03) — недопустимый начальный адрес очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="977b2-1211">TX_SIZE_ERROR (0x05) — недопустимый размер очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="977b2-1212">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1213">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1213">Allowed From</span></span>

<span data-ttu-id="977b2-1214">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1215">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1215">Preemption Possible</span></span>

<span data-ttu-id="977b2-1216">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1217">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1217">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1218">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1218">See Also</span></span>

- <span data-ttu-id="977b2-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1219">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1220">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1226">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1227">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="977b2-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1229">tx_queue_delete</span></span>

<span data-ttu-id="977b2-1230">Удаление очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="977b2-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1231">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1232">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1232">Description</span></span>

<span data-ttu-id="977b2-1233">Эта служба удаляет указанную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="977b2-1234">Все потоки, приостановленные в ожидании сообщения из этой очереди, возобновляются и получают статус возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="977b2-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1235">Перед удалением очереди приложение должно убедиться, что любой обратный вызов с уведомлением об отправке для этой очереди завершен (или отключен).</span><span class="sxs-lookup"><span data-stu-id="977b2-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="977b2-1236">Кроме того, приложение должно предотвратить использование удаленной очереди в будущем.</span><span class="sxs-lookup"><span data-stu-id="977b2-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="977b2-1237">*Кроме того, обязанность по управлению областью памяти, связанной с очередью, которая становится доступной после завершения этой службы, лежит на приложении.*</span><span class="sxs-lookup"><span data-stu-id="977b2-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1238">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1238">Parameters</span></span> 

- <span data-ttu-id="977b2-1239">**queue_ptr** — указатель на созданную ранее очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1240">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1240">Return Values</span></span>

- <span data-ttu-id="977b2-1241">**TX_SUCCESS** (0x00) — успешное удаление очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="977b2-1242">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="977b2-1243">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1244">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1244">Allowed From</span></span>

<span data-ttu-id="977b2-1245">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1246">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1246">Preemption Possible</span></span>

<span data-ttu-id="977b2-1247">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1248">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1248">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1249">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1249">See Also</span></span>

- <span data-ttu-id="977b2-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1250">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1251">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1257">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1258">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="977b2-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1260">tx_queue_flush</span></span>

<span data-ttu-id="977b2-1261">Очистка сообщений в очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="977b2-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1262">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1263">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1263">Description</span></span>

<span data-ttu-id="977b2-1264">Эта служба удаляет все сообщения, хранящиеся в указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="977b2-1265">Если очередь заполнена, сообщения о всех приостановленных потоках будут удалены.</span><span class="sxs-lookup"><span data-stu-id="977b2-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="977b2-1266">Затем каждый приостановленный поток возобновляется со статусом возврата, который указывает, что отправка сообщения прошла успешно.</span><span class="sxs-lookup"><span data-stu-id="977b2-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="977b2-1267">Если очередь пуста, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="977b2-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1268">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1268">Parameters</span></span> 

- <span data-ttu-id="977b2-1269">**queue_ptr** — указатель на созданную ранее очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1270">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1270">Return Values</span></span>

- <span data-ttu-id="977b2-1271">**TX_SUCCESS** (0x00) — успешная очистка очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="977b2-1272">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1273">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1273">Allowed From</span></span>

<span data-ttu-id="977b2-1274">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1275">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1275">Preemption Possible</span></span>

<span data-ttu-id="977b2-1276">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1277">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1277">Example</span></span>

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1278">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1278">See Also</span></span>

- <span data-ttu-id="977b2-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1279">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1280">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1286">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1287">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="977b2-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1289">tx_queue_front_send</span></span>

<span data-ttu-id="977b2-1290">Отправка сообщения в начало очереди</span><span class="sxs-lookup"><span data-stu-id="977b2-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1291">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-1292">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1292">Description</span></span>

<span data-ttu-id="977b2-1293">Эта служба отправляет сообщение в начало указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="977b2-1294">Сообщение **копируется** в начало очереди из области памяти, заданной указателем источника.</span><span class="sxs-lookup"><span data-stu-id="977b2-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1295">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1295">Parameters</span></span>

- <span data-ttu-id="977b2-1296">**queue_ptr** — указатель на блок управления очередью сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="977b2-1297">**source_ptr** — указатель на сообщение.</span><span class="sxs-lookup"><span data-stu-id="977b2-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="977b2-1298">**wait_option** — определяет, как работает служба, если очередь сообщений заполнена.</span><span class="sxs-lookup"><span data-stu-id="977b2-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="977b2-1299">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-1300">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-1302">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-1303">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-1304">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*</span><span class="sxs-lookup"><span data-stu-id="977b2-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="977b2-1305">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенный срок, пока в очереди не появится место.</span><span class="sxs-lookup"><span data-stu-id="977b2-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="977b2-1306">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера для того, чтобы оставаться в состоянии приостановки во время ожидания мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1307">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1307">Return Values</span></span>

- <span data-ttu-id="977b2-1308">**TX_SUCCESS** (0x00) — успешная отправка сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="977b2-1309">**TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-1310">**TX_QUEUE_FULL** (0x0B) — службе не удалось отправить сообщение, так как очередь была заполнена в течение всего указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="977b2-1311">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-1312">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="977b2-1313">TX_PTR_ERROR (0x03) — недопустимый указатель источника для сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="977b2-1314">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1315">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1315">Allowed From</span></span>

<span data-ttu-id="977b2-1316">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1317">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1317">Preemption Possible</span></span>

<span data-ttu-id="977b2-1318">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1319">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1319">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1320">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1320">See Also</span></span>

- <span data-ttu-id="977b2-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1321">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1322">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1323">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1328">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1329">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="977b2-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1331">tx_queue_info_get</span></span>

<span data-ttu-id="977b2-1332">Получение сведений об очереди</span><span class="sxs-lookup"><span data-stu-id="977b2-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1333">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="977b2-1334">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1334">Description</span></span>

<span data-ttu-id="977b2-1335">Эта служба получает сведения об указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1336">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1336">Parameters</span></span>

- <span data-ttu-id="977b2-1337">**queue_ptr** — указатель на созданную ранее очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="977b2-1338">**name** — указатель на назначение для указателя на имя очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="977b2-1339">**enqueued** — указатель на назначение для количества сообщений, находящихся в очереди в данный момент.</span><span class="sxs-lookup"><span data-stu-id="977b2-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="977b2-1340">**available_storage** — указатель на назначение для количества сообщений в очереди, для которых в данный момент есть свободное место.</span><span class="sxs-lookup"><span data-stu-id="977b2-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="977b2-1341">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="977b2-1342">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="977b2-1343">**next_queue** — указатель на назначение для указателя следующей созданной очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1344">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1345">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1345">Return Values</span></span>

- <span data-ttu-id="977b2-1346">**TX_SUCCESS** (0x00) — успешное получение сведений об очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="977b2-1347">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1348">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1348">Allowed From</span></span>

<span data-ttu-id="977b2-1349">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1350">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1350">Preemption Possible</span></span>

<span data-ttu-id="977b2-1351">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1352">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1352">Example</span></span>

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1353">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1353">See Also</span></span>

- <span data-ttu-id="977b2-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1354">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1355">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1356">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1361">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1362">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="977b2-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="977b2-1365">Получение сведений о производительности очереди</span><span class="sxs-lookup"><span data-stu-id="977b2-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1366">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-1367">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1367">Description</span></span>

<span data-ttu-id="977b2-1368">Эта служба получает сведения о производительности указанной очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1369">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_QUEUE_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1370">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1370">Parameters</span></span>

- <span data-ttu-id="977b2-1371">**queue_ptr** — указатель на созданную ранее очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="977b2-1372">**messages_sent** — указатель на назначение для количества запросов на отправку, выполненных в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="977b2-1373">**messages_received** — указатель на назначение для количества запросов на получение, выполненных в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="977b2-1374">**empty_suspensions** — указатель на назначение для количества приостановок при пустой очереди в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="977b2-1375">**full_suspensions** — указатель на назначение для количества приостановок при заполненной очереди в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="977b2-1376">**full_errors** — указатель на назначение для количества ошибок при заполненной очереди в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="977b2-1377">**timeouts** — указатель на назначение для количества истечений времени ожидания во время приостановки потока в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1378">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1379">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1379">Return Values</span></span>

- <span data-ttu-id="977b2-1380">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="977b2-1381">**TX_PTR_ERROR** (0x03) — недопустимый указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="977b2-1382">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1383">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1383">Allowed From</span></span>

<span data-ttu-id="977b2-1384">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1385">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1385">Example</span></span>

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1386">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1386">See Also</span></span>

- <span data-ttu-id="977b2-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1387">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1388">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1389">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1394">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1395">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="977b2-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="977b2-1398">Получение сведений о производительности системы очередей</span><span class="sxs-lookup"><span data-stu-id="977b2-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1399">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-1400">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1400">Description</span></span>

<span data-ttu-id="977b2-1401">Эта служба получает сведения о производительности всех очередей в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1402">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_QUEUE_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1403">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1403">Parameters</span></span>

- <span data-ttu-id="977b2-1404">**messages_sent** — указатель на назначение для общего количества запросов на отправку, выполненных во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="977b2-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="977b2-1405">**messages_received** — указатель на назначение для общего количества запросов на получение, выполненных во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="977b2-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="977b2-1406">**empty_suspensions** — указатель на назначение для общего количества приостановок при пустой очереди во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="977b2-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="977b2-1407">**full_suspensions** — указатель на назначение для общего количества приостановок при заполненной очереди во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="977b2-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="977b2-1408">**full_errors** — указатель на назначение для общего количества ошибок при заполненной очереди во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="977b2-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="977b2-1409">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки потока во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="977b2-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1410">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1411">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1411">Return Values</span></span>

- <span data-ttu-id="977b2-1412">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы очередей.</span><span class="sxs-lookup"><span data-stu-id="977b2-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="977b2-1413">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1414">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1414">Allowed From</span></span>

<span data-ttu-id="977b2-1415">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1416">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1416">Example</span></span>

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1417">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1417">See Also</span></span>

- <span data-ttu-id="977b2-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1418">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1419">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1420">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1425">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1426">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="977b2-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="977b2-1429">Назначение приоритета в списке приостановки очереди</span><span class="sxs-lookup"><span data-stu-id="977b2-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1430">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="977b2-1431">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1431">Description</span></span>

<span data-ttu-id="977b2-1432">Эта служба помещает поток с наивысшим приоритетом, приостановленный для сообщения (или для размещения сообщения) в этой очереди, в начало списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="977b2-1433">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="977b2-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1434">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1434">Parameters</span></span> 

- <span data-ttu-id="977b2-1435">**queue_ptr** — указатель на созданную ранее очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1436">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1436">Return Values</span></span>

- <span data-ttu-id="977b2-1437">**TX_SUCCESS** (0x00) — успешное назначение приоритета в очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="977b2-1438">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1439">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1439">Allowed From</span></span>

<span data-ttu-id="977b2-1440">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1441">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1441">Preemption Possible</span></span>

<span data-ttu-id="977b2-1442">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1443">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1443">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1444">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1444">See Also</span></span>

- <span data-ttu-id="977b2-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1445">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1446">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1447">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1452">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1453">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="977b2-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1455">tx_queue_receive</span></span>

<span data-ttu-id="977b2-1456">Получение сообщения из очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="977b2-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1457">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-1458">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1458">Description</span></span>

<span data-ttu-id="977b2-1459">Эта служба получает сообщение из указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="977b2-1460">Полученное сообщение **копируется** из очереди в область памяти, заданную указателем назначения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="977b2-1461">Затем это сообщение удаляется из очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="977b2-1462">Указанная область памяти назначения должна быть достаточно большой, чтобы вместить сообщение. То есть место назначения сообщения, на которое указывает **destination_ptr**, должно быть не меньше размера сообщения для этой очереди.</span><span class="sxs-lookup"><span data-stu-id="977b2-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="977b2-1463">В противном случае, если места назначения недостаточно, происходит повреждение памяти в следующей области памяти.</span><span class="sxs-lookup"><span data-stu-id="977b2-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1464">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1464">Parameters</span></span>

- <span data-ttu-id="977b2-1465">**queue_ptr** — указатель на созданную ранее очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="977b2-1466">**destination_ptr** — расположение для копирования сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="977b2-1467">**wait_option** — определяет, как работает служба, если очередь сообщений пуста.</span><span class="sxs-lookup"><span data-stu-id="977b2-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="977b2-1468">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-1469">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="977b2-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="977b2-1471">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-1472">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-1473">Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="977b2-1474">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока не станет доступным сообщение.</span><span class="sxs-lookup"><span data-stu-id="977b2-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="977b2-1475">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера для того, чтобы оставаться в состоянии приостановки во время ожидания мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1476">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1476">Return Values</span></span>

- <span data-ttu-id="977b2-1477">**TX_SUCCESS** (0x00) — успешное получение сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="977b2-1478">**TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-1479">**TX_QUEUE_EMPTY** (0x0A) — службе не удалось получить сообщение, так как очередь была пуста в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="977b2-1480">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-1481">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="977b2-1482">TX_PTR_ERROR (0x03) — недопустимый указатель назначения для сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="977b2-1483">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1484">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1484">Allowed From</span></span>

<span data-ttu-id="977b2-1485">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1486">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1486">Preemption Possible</span></span>

<span data-ttu-id="977b2-1487">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1488">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1488">Example</span></span>

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1489">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1489">See Also</span></span>

- <span data-ttu-id="977b2-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1490">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1491">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1492">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1498">tx_queue_send</span></span>
- <span data-ttu-id="977b2-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="977b2-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1500">tx_queue_send</span></span>

<span data-ttu-id="977b2-1501">Отправка сообщения в очередь сообщений</span><span class="sxs-lookup"><span data-stu-id="977b2-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1502">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="977b2-1503">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1503">Description</span></span>

<span data-ttu-id="977b2-1504">Эта служба отправляет сообщение в указанную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="977b2-1505">Отправленное сообщение **копируется** в очередь из области памяти, заданной указателем источника.</span><span class="sxs-lookup"><span data-stu-id="977b2-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1506">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1506">Parameters</span></span>

- <span data-ttu-id="977b2-1507">**queue_ptr** — указатель на созданную ранее очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="977b2-1508">**source_ptr** — указатель на сообщение.</span><span class="sxs-lookup"><span data-stu-id="977b2-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="977b2-1509">**wait_option** — определяет, как работает служба, если очередь сообщений заполнена.</span><span class="sxs-lookup"><span data-stu-id="977b2-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="977b2-1510">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-1511">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-1513">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-1514">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-1515">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*</span><span class="sxs-lookup"><span data-stu-id="977b2-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="977b2-1516">В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенный срок, пока в очереди не появится место.</span><span class="sxs-lookup"><span data-stu-id="977b2-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="977b2-1517">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера для того, чтобы оставаться в состоянии приостановки во время ожидания мьютекса.</span><span class="sxs-lookup"><span data-stu-id="977b2-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1518">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1518">Return Values</span></span>

- <span data-ttu-id="977b2-1519">**TX_SUCCESS** (0x00) — успешная отправка сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="977b2-1520">**TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-1521">**TX_QUEUE_FULL** (0x0B) — службе не удалось отправить сообщение, так как очередь была заполнена в течение всего указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="977b2-1522">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-1523">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="977b2-1524">TX_PTR_ERROR (0x03) — недопустимый указатель источника для сообщения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="977b2-1525">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, указан для вызова из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1526">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1526">Allowed From</span></span>

<span data-ttu-id="977b2-1527">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1528">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1528">Preemption Possible</span></span>

<span data-ttu-id="977b2-1529">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1530">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1530">Example</span></span>

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1531">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1531">See Also</span></span>

- <span data-ttu-id="977b2-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1532">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1533">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1534">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1540">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="977b2-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="977b2-1543">Уведомление приложения при отправке сообщения в очередь</span><span class="sxs-lookup"><span data-stu-id="977b2-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1544">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="977b2-1545">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1545">Description</span></span>

<span data-ttu-id="977b2-1546">Эта служба регистрирует функцию обратного вызова уведомления, которая вызывается всякий раз, когда сообщение отправляется в указанную очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="977b2-1547">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="977b2-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-1548">Обратному вызову уведомления об отправке очереди приложения не разрешено вызывать API ThreadX SMP с параметром приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1549">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1549">Parameters</span></span> 

- <span data-ttu-id="977b2-1550">**queue_ptr** — указатель на созданную ранее очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="977b2-1551">**queue_send_notify** — указатель на функцию уведомления приложения об отправке в очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="977b2-1552">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1553">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1553">Return Values</span></span>

- <span data-ttu-id="977b2-1554">**TX_SUCCESS** (0x00) — успешная регистрация уведомления об отправке в очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="977b2-1555">TX_QUEUE_ERROR (0x09) — недопустимый указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="977b2-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="977b2-1556">TX_FEATURE_NOT_ENABLED (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1557">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1557">Allowed From</span></span>

<span data-ttu-id="977b2-1558">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1559">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1559">Example</span></span>

```C
TX_QUEUE         my_queue;

/* Register the "my_queue_send_notify" function for monitoring
   messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
   successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
/* A message was just sent to this queue! */
}
```
### <a name="see-also"></a><span data-ttu-id="977b2-1560">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1560">See Also</span></span>

- <span data-ttu-id="977b2-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1561">tx_queue_create</span></span>
- <span data-ttu-id="977b2-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1562">tx_queue_delete</span></span>
- <span data-ttu-id="977b2-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="977b2-1563">tx_queue_flush</span></span>
- <span data-ttu-id="977b2-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="977b2-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="977b2-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="977b2-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="977b2-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="977b2-1569">tx_queue_receive</span></span>
- <span data-ttu-id="977b2-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="977b2-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="977b2-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="977b2-1572">Размещение экземпляра в семафоре со счетчиком с верхним пределом</span><span class="sxs-lookup"><span data-stu-id="977b2-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1573">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="977b2-1574">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1574">Description</span></span>

<span data-ttu-id="977b2-1575">Эта служба помещает экземпляр в указанный семафор со счетчиком, который в действительности увеличивает семафор со счетчиком на единицу.</span><span class="sxs-lookup"><span data-stu-id="977b2-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="977b2-1576">Если текущее значение семафора со счетчиком превышает указанный верхний предел или равно ему, экземпляр не будет размещен и будет возвращена ошибка TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="977b2-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1577">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1577">Parameters</span></span> 

- <span data-ttu-id="977b2-1578">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="977b2-1579">**ceiling** — максимально допустимый предел для семафора (допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="977b2-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1580">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1580">Return Values</span></span>

- <span data-ttu-id="977b2-1581">**TX_SUCCESS** (0x00) — успешное размещение верхнего предела семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="977b2-1582">**TX_CEILING_EXCEEDED** (0x21) — запрос на размещение превышает допустимый предел.</span><span class="sxs-lookup"><span data-stu-id="977b2-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="977b2-1583">TX_INVALID_CEILING (0x22) — для верхнего значения указано недопустимое нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="977b2-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="977b2-1584">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1585">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1585">Allowed From</span></span>

<span data-ttu-id="977b2-1586">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1587">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="977b2-1588">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1588">See Also</span></span>

- <span data-ttu-id="977b2-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="977b2-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1598">tx_semaphore_create</span></span>

<span data-ttu-id="977b2-1599">Создание семафора со счетчиком</span><span class="sxs-lookup"><span data-stu-id="977b2-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1600">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="977b2-1601">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1601">Description</span></span>

<span data-ttu-id="977b2-1602">Эта служба создает семафор со счетчиком для синхронизации между потоками.</span><span class="sxs-lookup"><span data-stu-id="977b2-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="977b2-1603">Начальное значение семафора указывается в качестве входного параметра.</span><span class="sxs-lookup"><span data-stu-id="977b2-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1604">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1604">Parameters</span></span> 

- <span data-ttu-id="977b2-1605">**semaphore_ptr** — указатель на блок управления семафором.</span><span class="sxs-lookup"><span data-stu-id="977b2-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="977b2-1606">**name_ptr** — указатель на имя семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="977b2-1607">**initial_count** — указывает начальное значение счетчика для семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="977b2-1608">Допустимые значения находятся в диапазоне от 0x00000000 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1609">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1609">Return Values</span></span>

- <span data-ttu-id="977b2-1610">**TX_SUCCESS** (0x00) — успешное создание семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="977b2-1611">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="977b2-1612">Либо указатель имеет значение NULL, либо семафор уже создан.</span><span class="sxs-lookup"><span data-stu-id="977b2-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="977b2-1613">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1614">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1614">Allowed From</span></span>

<span data-ttu-id="977b2-1615">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1616">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1616">Preemption Possible</span></span>

<span data-ttu-id="977b2-1617">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1618">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1618">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1619">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1619">See Also</span></span>

- <span data-ttu-id="977b2-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="977b2-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="977b2-1630">Удаление вычисляющего семафора</span><span class="sxs-lookup"><span data-stu-id="977b2-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1631">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1632">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1632">Description</span></span>

<span data-ttu-id="977b2-1633">Эта служба удаляет указанный семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="977b2-1634">Все потоки, приостановленные в ожидании экземпляра семафора, возобновляются и получают статус возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="977b2-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1635">Перед удалением семафора приложение должно убедиться, что обратный вызов с уведомлением о размещении для этого семафора завершен (или отключен).</span><span class="sxs-lookup"><span data-stu-id="977b2-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="977b2-1636">Кроме того, приложение должно предотвратить любое использование удаленного семафора в будущем.</span><span class="sxs-lookup"><span data-stu-id="977b2-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1637">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1637">Parameters</span></span> 

- <span data-ttu-id="977b2-1638">**semaphore_ptr** — указатель на созданный ранее семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1639">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1639">Return Values</span></span>

- <span data-ttu-id="977b2-1640">**TX_SUCCESS** (0x00) — успешное удаление семафора со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="977b2-1641">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="977b2-1642">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1643">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1643">Allowed From</span></span>

<span data-ttu-id="977b2-1644">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1645">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1645">Preemption Possible</span></span>

<span data-ttu-id="977b2-1646">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1647">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1648">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1648">See Also</span></span>

- <span data-ttu-id="977b2-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="977b2-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1658">tx_semaphore_get</span></span>

<span data-ttu-id="977b2-1659">Получение экземпляра из вычисляющего семафора</span><span class="sxs-lookup"><span data-stu-id="977b2-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1660">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="977b2-1661">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1661">Description</span></span>

<span data-ttu-id="977b2-1662">Эта служба получает экземпляр (одиночный счетчик) из указанного семафора со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="977b2-1663">В результате значение указанного семафора уменьшается на единицу.</span><span class="sxs-lookup"><span data-stu-id="977b2-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1664">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1664">Parameters</span></span>

- <span data-ttu-id="977b2-1665">**semaphore_ptr** — указатель на созданный ранее семафор с подсчетом.</span><span class="sxs-lookup"><span data-stu-id="977b2-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="977b2-1666">**wait_option** — определяет, как работает служба, если нет доступных экземпляров семафора. То есть значение семафора равно нулю.</span><span class="sxs-lookup"><span data-stu-id="977b2-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="977b2-1667">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="977b2-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="977b2-1668">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="977b2-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="977b2-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="977b2-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="977b2-1670">значение времени ожидания: (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="977b2-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="977b2-1671">В случае выбора TX_NO_WAIT будет выполнен немедленный возврат из этой службы независимо от того, было ли выделение успешным или нет.</span><span class="sxs-lookup"><span data-stu-id="977b2-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="977b2-1672">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*</span><span class="sxs-lookup"><span data-stu-id="977b2-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="977b2-1673">При выборе TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока не станет доступен экземпляр семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="977b2-1674">Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, которые будут оставаться приостановленными во время ожидания экземпляра семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1675">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1675">Return Values</span></span>

- <span data-ttu-id="977b2-1676">**TX_SUCCESS** (0x00) — успешное получение экземпляра семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="977b2-1677">**TX_DELETED** (0x01) — семафор со счетчиком был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="977b2-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="977b2-1678">**TX_NO_INSTANCE** (0x0D) — службе не удалось получить экземпляр семафора со счетчиком (значение семафора в течение всего заданного времени ожидания было равно нулю).</span><span class="sxs-lookup"><span data-stu-id="977b2-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="977b2-1679">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-1680">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="977b2-1681">TX_WAIT_ERROR (0x04) — параметр ожидания, отличный от TX_NO_WAIT, был указан при вызове из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1682">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1682">Allowed From</span></span>

<span data-ttu-id="977b2-1683">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1684">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1684">Preemption Possible</span></span>

<span data-ttu-id="977b2-1685">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1686">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1686">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1687">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1687">See Also</span></span>

- <span data-ttu-id="977b2-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="977b2-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="977b2-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="977b2-1697">Получение сведений о семафоре</span><span class="sxs-lookup"><span data-stu-id="977b2-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1698">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="977b2-1699">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1699">Description</span></span>

<span data-ttu-id="977b2-1700">Эта служба получает сведения об указанном семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1701">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1701">Parameters</span></span>

- <span data-ttu-id="977b2-1702">**semaphore_ptr** — указатель на блок управления семафором.</span><span class="sxs-lookup"><span data-stu-id="977b2-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="977b2-1703">**name** — указатель на назначение для указателя на имя семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="977b2-1704">**current_value** — указатель на назначение для текущего значения семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="977b2-1705">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="977b2-1706">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="977b2-1707">**next_semaphore** — указатель на назначение для указателя следующего созданного семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1708">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1709">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1709">Return Values</span></span>

- <span data-ttu-id="977b2-1710">**TX_SUCCESS** (0x00) — успешное получение сведений о семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="977b2-1711">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1712">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1712">Allowed From</span></span>

<span data-ttu-id="977b2-1713">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1714">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1714">Preemption Possible</span></span>

<span data-ttu-id="977b2-1715">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1716">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1716">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1717">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1717">See Also</span></span>

- <span data-ttu-id="977b2-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="977b2-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="977b2-1728">Получение сведений о производительности семафоров</span><span class="sxs-lookup"><span data-stu-id="977b2-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1729">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-1730">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1730">Description</span></span>

<span data-ttu-id="977b2-1731">Эта служба получает сведения о производительности указанного семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-1732">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**, чтобы служба могла возвращать сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1733">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1733">Parameters</span></span>

- <span data-ttu-id="977b2-1734">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="977b2-1735">**puts** — указатель на назначение для количества запросов на размещение, выполненных в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="977b2-1736">**gets** — указатель на назначение для количества запросов на получение, выполненных в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="977b2-1737">**suspensions** — указатель на назначение для количества приостановок потоков в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="977b2-1738">**timeouts** — указатель на назначение для количества истечений времени ожидания во время приостановки потока в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1739">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1740">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1740">Return Values</span></span>

- <span data-ttu-id="977b2-1741">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="977b2-1742">**TX_PTR_ERROR** (0x03) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="977b2-1743">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1744">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1744">Allowed From</span></span>

<span data-ttu-id="977b2-1745">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1746">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1746">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1747">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1747">See Also</span></span>

- <span data-ttu-id="977b2-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="977b2-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="977b2-1758">Получение сведений о производительности системы семафоров</span><span class="sxs-lookup"><span data-stu-id="977b2-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1759">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="977b2-1760">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1760">Description</span></span>

<span data-ttu-id="977b2-1761">Эта служба получает сведения о производительности всех семафоров в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1762">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**, чтобы служба могла возвращать сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1763">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1763">Parameters</span></span>

- <span data-ttu-id="977b2-1764">**puts** — указатель на назначение для общего количества запросов на размещение, выполненных во всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="977b2-1765">**gets** — указатель на назначение для общего количества запросов на получение, выполненных во всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="977b2-1766">**suspensions** — указатель на назначение для общего количества приостановок потоков во всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="977b2-1767">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки потока на всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="977b2-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1768">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1769">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1769">Return Values</span></span>

- <span data-ttu-id="977b2-1770">TX_SUCCESS (0x00) — успешное получение сведений о производительности системы семафоров.</span><span class="sxs-lookup"><span data-stu-id="977b2-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="977b2-1771">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1772">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1772">Allowed From</span></span>

<span data-ttu-id="977b2-1773">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1774">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1774">Example</span></span>

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1775">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1775">See Also</span></span>

- <span data-ttu-id="977b2-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="977b2-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="977b2-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="977b2-1786">Назначение приоритета списку приостановки семафора</span><span class="sxs-lookup"><span data-stu-id="977b2-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1787">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1788">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1788">Description</span></span>

<span data-ttu-id="977b2-1789">Эта служба размещает поток с наивысшим приоритетом, приостановленный для получения экземпляра семафора, в начале списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="977b2-1790">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="977b2-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1791">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1791">Parameters</span></span> 

- <span data-ttu-id="977b2-1792">**semaphore_ptr** — указатель на созданный ранее семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1793">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1793">Return Values</span></span>

- <span data-ttu-id="977b2-1794">**TX_SUCCESS** (0x00) — успешное назначение приоритета в семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="977b2-1795">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1796">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1796">Allowed From</span></span>

<span data-ttu-id="977b2-1797">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1798">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1798">Preemption Possible</span></span>

<span data-ttu-id="977b2-1799">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1800">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1800">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1801">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1801">See Also</span></span>

- <span data-ttu-id="977b2-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="977b2-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1807">tx_semaphore_put</span></span>

<span data-ttu-id="977b2-1808">Размещение экземпляра в вычисляющем семафоре</span><span class="sxs-lookup"><span data-stu-id="977b2-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1809">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1810">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1810">Description</span></span>

<span data-ttu-id="977b2-1811">Эта служба помещает экземпляр в указанный семафор со счетчиком, который в действительности увеличивает семафор со счетчиком на единицу.</span><span class="sxs-lookup"><span data-stu-id="977b2-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1812">Если эта служба вызывается, когда семафор представляет собой единое целое (OxFFFFFFFF), новая операция размещения приведет к сбросу семафора на нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="977b2-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1813">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1813">Parameters</span></span>

- <span data-ttu-id="977b2-1814">**semaphore_ptr** — указатель на ранее созданный блок управления семафором со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1815">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1815">Return Values</span></span>

- <span data-ttu-id="977b2-1816">**TX_SUCCESS** (0x00) — успешная операция размещения в семафоре.</span><span class="sxs-lookup"><span data-stu-id="977b2-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="977b2-1817">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1818">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1818">Allowed From</span></span>

<span data-ttu-id="977b2-1819">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1820">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1820">Preemption Possible</span></span>

<span data-ttu-id="977b2-1821">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1822">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1823">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1823">See Also</span></span>

- <span data-ttu-id="977b2-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="977b2-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="977b2-1834">Уведомление приложения об установке семафора</span><span class="sxs-lookup"><span data-stu-id="977b2-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1835">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="977b2-1836">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1836">Description</span></span>

<span data-ttu-id="977b2-1837">Эта служба регистрирует функцию обратного вызова уведомлений, которая вызывается всякий раз, когда помещается указанный семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="977b2-1838">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="977b2-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-1839">Обратному вызову уведомления семафоров приложения не разрешено вызывать какой-либо API ThreadX SMP с параметром приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1840">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1840">Parameters</span></span> 

- <span data-ttu-id="977b2-1841">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="977b2-1842">**semaphore_put_notify** — указатель на функцию уведомления приложения о размещении семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="977b2-1843">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1844">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1844">Return Values</span></span>

- <span data-ttu-id="977b2-1845">**TX_SUCCESS** (0x00) — успешная регистрация уведомления о размещении семафора.</span><span class="sxs-lookup"><span data-stu-id="977b2-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="977b2-1846">TX_SEMAPHORE_ERROR (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="977b2-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="977b2-1847">**TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1848">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1848">Allowed From</span></span>

<span data-ttu-id="977b2-1849">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1850">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1850">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a><span data-ttu-id="977b2-1851">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1851">See Also</span></span>

- <span data-ttu-id="977b2-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="977b2-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="977b2-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="977b2-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="977b2-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="977b2-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="977b2-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="977b2-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="977b2-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="977b2-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="977b2-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1861">tx_thread_create</span></span>

<span data-ttu-id="977b2-1862">Создание потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1863">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="977b2-1864">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1864">Description</span></span>

<span data-ttu-id="977b2-1865">Эта служба создает поток приложения, который начинает выполнение с указанной функции входа в задачу.</span><span class="sxs-lookup"><span data-stu-id="977b2-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="977b2-1866">Стек, приоритет, порог вытеснения и интервал времени являются атрибутами, задаваемыми входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="977b2-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="977b2-1867">Кроме того, указывается также начальное состояние выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1868">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1868">Parameters</span></span>

- <span data-ttu-id="977b2-1869">**thread_ptr** — указатель на блок управления потоком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="977b2-1870">**name_ptr** — указатель на имя потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="977b2-1871">**entry_function** задает начальную функцию C для выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="977b2-1872">Когда поток возвращается из этой функции входа, он переводится в состояние завершения и приостанавливается на неопределенное время.</span><span class="sxs-lookup"><span data-stu-id="977b2-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="977b2-1873">**entry_input** — 32-разрядное значение, которое передается функции входа в поток при первом выполнении.</span><span class="sxs-lookup"><span data-stu-id="977b2-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="977b2-1874">Использование этих входных данных определяется исключительно приложением.</span><span class="sxs-lookup"><span data-stu-id="977b2-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="977b2-1875">**stack_start** — начальный адрес области памяти стека.</span><span class="sxs-lookup"><span data-stu-id="977b2-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="977b2-1876">**stack_size** — количество байтов в области памяти стека.</span><span class="sxs-lookup"><span data-stu-id="977b2-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="977b2-1877">Область стека потока должна быть достаточно большой, чтобы справиться с вложением вызовов функций и использованием локальных переменных в худшем случае.</span><span class="sxs-lookup"><span data-stu-id="977b2-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="977b2-1878">**priority** — числовой приоритет потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="977b2-1879">Допустимые значения варьируются от 0 до (TX_MAX_PRIORITES-1), где значение 0 соответствует наивысшему приоритету.</span><span class="sxs-lookup"><span data-stu-id="977b2-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="977b2-1880">**preempt_threshold** — уровень наивысшего приоритета (от 0 до (TX_MAX_PRIORITIES-1)) при отключенном вытеснении.</span><span class="sxs-lookup"><span data-stu-id="977b2-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="977b2-1881">Только приоритеты выше этого уровня могут вытеснять этот поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="977b2-1882">Это значение должно быть меньше указанного приоритета или равно ему.</span><span class="sxs-lookup"><span data-stu-id="977b2-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="977b2-1883">Значение, равное приоритету потока, отключает порог вытеснения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="977b2-1884">**time_slice** — количество тактов таймера, которое этот поток может выполнять до того, как другие готовые потоки с таким же приоритетом получают возможность запуска.</span><span class="sxs-lookup"><span data-stu-id="977b2-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="977b2-1885">Необходимо отметить, что при использовании порогового значения вытеснения интервалы времени отключаются.</span><span class="sxs-lookup"><span data-stu-id="977b2-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="977b2-1886">Допустимые значение интервала времени варьируются от 1 до 0xFFFFFFFF (включительно).</span><span class="sxs-lookup"><span data-stu-id="977b2-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="977b2-1887">Значение **TX_NO_TIME_SLICE** (значение 0) отключает интервалы времени для этого потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="977b2-1888">Использование интервалов времени немного увеличивает нагрузку на систему.</span><span class="sxs-lookup"><span data-stu-id="977b2-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="977b2-1889">Так как интервалы времени эффективны только в случаях, когда несколько потоков имеют одинаковый приоритет, назначать интервал времени для потоков с уникальным приоритетом не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="977b2-1890">**auto_start** — указывает, запускается ли поток немедленно или помещается в состояние приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="977b2-1891">Допустимые значения: **TX_AUTO_START** (0x01) и **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="977b2-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="977b2-1892">Если указано TX_DONT_START, приложение должно затем вызвать tx_thread_resume для того, чтобы запустить поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1893">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1893">Return Values</span></span>

- <span data-ttu-id="977b2-1894">**TX_SUCCESS** (0x00) — успешное создание потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="977b2-1895">TX_THREAD_ERROR (0x0E) — недопустимый указатель на управление потоком.</span><span class="sxs-lookup"><span data-stu-id="977b2-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="977b2-1896">Либо указатель имеет значение NULL, либо поток уже создан.</span><span class="sxs-lookup"><span data-stu-id="977b2-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="977b2-1897">TX_PTR_ERROR (0x03) — недопустимый начальный адрес точки входа или недопустимая область стека, обычно имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="977b2-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="977b2-1898">TX_SIZE_ERROR (0x05) — недопустимый размер области стека.</span><span class="sxs-lookup"><span data-stu-id="977b2-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="977b2-1899">Минимальное количество байтов для выполнения потоков: **TX_MINIMUM_STACK**.</span><span class="sxs-lookup"><span data-stu-id="977b2-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="977b2-1900">TX_PRIORITY_ERROR (0x0F) — недопустимый приоритет потока, значение которого выходит за пределы диапазона (от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="977b2-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="977b2-1901">TX_THRESH_ERROR (0x18) — указан недопустимый порог вытеснения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="977b2-1902">Это значение должно быть допустимым приоритетом, меньшим или равным начальному приоритету потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="977b2-1903">TX_START_ERROR (0x10) — недопустимое значение параметра автозапуска.</span><span class="sxs-lookup"><span data-stu-id="977b2-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="977b2-1904">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1905">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1905">Allowed From</span></span>

<span data-ttu-id="977b2-1906">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1907">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1907">Preemption Possible</span></span>

<span data-ttu-id="977b2-1908">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1909">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1909">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
                my_thread_entry, 0x1234,
                (VOID *) 0x400000, 1000,
                15, 15, TX_NO_TIME_SLICE,
                TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
   for execution! */
...

/* Thread’s entry function. When "my_thread" actually
   begins execution, control is transferred to this
   function. */
VOID my_thread_entry (ULONG initial_input)
{

    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */

    /* The real work of the thread, including calls to
    other function should be called from here! */

    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```
### <a name="see-also"></a><span data-ttu-id="977b2-1910">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1910">See Also</span></span>

- <span data-ttu-id="977b2-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1911">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-1913">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-1920">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-1921">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="977b2-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1928">tx_thread_delete</span></span>

<span data-ttu-id="977b2-1929">Удаление потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1930">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-1931">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1931">Description</span></span>

<span data-ttu-id="977b2-1932">Эта служба удаляет указанный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="977b2-1933">Так как указанный поток должен находиться в состоянии прекращения или завершения, эту службу нельзя вызвать из потока, пытающегося удалить самого себя.</span><span class="sxs-lookup"><span data-stu-id="977b2-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-1934">Обязанность по управлению областью памяти, связанной со стеком потока, который станет доступным после завершения этой службы, лежит на приложении.</span><span class="sxs-lookup"><span data-stu-id="977b2-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="977b2-1935">Кроме того, приложение должно предотвратить использование удаленного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1936">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1936">Parameters</span></span>

- <span data-ttu-id="977b2-1937">**thread_ptr** — указатель на созданный ранее поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1938">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1938">Return Values</span></span>

- <span data-ttu-id="977b2-1939">**TX_SUCCESS** (0x00) — успешное удаление потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="977b2-1940">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-1941">**TX_DELETE_ERROR** (0x11) — указанный поток не находится в состоянии прекращения или завершения.</span><span class="sxs-lookup"><span data-stu-id="977b2-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="977b2-1942">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1943">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1943">Allowed From</span></span>

<span data-ttu-id="977b2-1944">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-1945">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-1945">Preemption Possible</span></span>

<span data-ttu-id="977b2-1946">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1947">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1947">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-1948">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1948">See Also</span></span>

- <span data-ttu-id="977b2-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1949">tx_thread_create</span></span>
- <span data-ttu-id="977b2-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-1951">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-1958">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-1959">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="977b2-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="977b2-1967">Уведомление приложения о входе в поток и выходе из него</span><span class="sxs-lookup"><span data-stu-id="977b2-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-1968">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="977b2-1969">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-1969">Description</span></span>

<span data-ttu-id="977b2-1970">Эта служба регистрирует функцию обратного вызова уведомления, которая вызывается при входе в указанный поток или выходе из него.</span><span class="sxs-lookup"><span data-stu-id="977b2-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="977b2-1971">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="977b2-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-1972">Обратный вызов уведомления о входе в поток приложения (или выходе из него) не может вызывать какой-либо API ThreadX SMP с параметром приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-1973">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-1973">Parameters</span></span>

- <span data-ttu-id="977b2-1974">**ip_ptr** — указатель на созданный ранее поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="977b2-1975">**entry_exit_notify** — указатель на функцию уведомления приложения о входе в поток или выходе из него.</span><span class="sxs-lookup"><span data-stu-id="977b2-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="977b2-1976">Второй параметр функции уведомления о входе или выходе указывает, присутствует ли вход или выход.</span><span class="sxs-lookup"><span data-stu-id="977b2-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="977b2-1977">Значение TX_THREAD_ENTRY (0x00) свидетельствует о выполнении входа в поток, а значение TX_THREAD_EXIT (0x01) — о выходе из него.</span><span class="sxs-lookup"><span data-stu-id="977b2-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="977b2-1978">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-1979">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-1979">Return Values</span></span>

- <span data-ttu-id="977b2-1980">**TX_SUCCESS** (0x00) — успешная регистрация функции уведомления о входе в поток или выходе из него.</span><span class="sxs-lookup"><span data-stu-id="977b2-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="977b2-1981">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="977b2-1982">**TX_FEATURE_NOT_ENABLED(0xFF)**  — система была скомпилирована с отключенными возможностями для уведомлений.</span><span class="sxs-lookup"><span data-stu-id="977b2-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-1983">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-1983">Allowed From</span></span>

<span data-ttu-id="977b2-1984">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-1985">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-1985">Example</span></span>

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
                my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
   successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{

    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
                 /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
         /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="977b2-1986">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-1986">See Also</span></span>

- <span data-ttu-id="977b2-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-1987">tx_thread_create</span></span>
- <span data-ttu-id="977b2-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-1988">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-1990">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-1997">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-1998">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="977b2-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2005">tx_thread_identify</span></span>

<span data-ttu-id="977b2-2006">Получает указатель на выполняющийся в данный момент поток</span><span class="sxs-lookup"><span data-stu-id="977b2-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2007">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="977b2-2008">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2008">Description</span></span>

<span data-ttu-id="977b2-2009">Эта служба возвращает указатель на выполняющийся в данный момент поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="977b2-2010">Если не выполняется ни один поток, служба возвращает пустой указатель.</span><span class="sxs-lookup"><span data-stu-id="977b2-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2011">Если эта служба вызывается из ISR, возвращаемое значение представляет поток, запущенный до выполнения обработчика прерываний.</span><span class="sxs-lookup"><span data-stu-id="977b2-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2012">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2012">Parameters</span></span>

<span data-ttu-id="977b2-2013">None</span><span class="sxs-lookup"><span data-stu-id="977b2-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2014">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2014">Return Values</span></span>

- <span data-ttu-id="977b2-2015">Указатель потока — указатель на выполняющийся в данный момент поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="977b2-2016">Если не выполняется ни один поток, возвращается значение TX_NULL.</span><span class="sxs-lookup"><span data-stu-id="977b2-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2017">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2017">Allowed From</span></span>

<span data-ttu-id="977b2-2018">Потоки и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2019">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2019">Preemption Possible</span></span>

<span data-ttu-id="977b2-2020">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2021">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2021">Example</span></span>

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2022">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2022">See Also</span></span>

- <span data-ttu-id="977b2-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2023">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2024">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2032">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2033">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="977b2-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2040">tx_thread_info_get</span></span>

<span data-ttu-id="977b2-2041">Получение сведений о потоке</span><span class="sxs-lookup"><span data-stu-id="977b2-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2042">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="977b2-2043">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2043">Description</span></span>

<span data-ttu-id="977b2-2044">Эта служба получает сведения об указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="977b2-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2045">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2045">Parameters</span></span> 

- <span data-ttu-id="977b2-2046">**thread_ptr** — указатель на блок управления потоком.</span><span class="sxs-lookup"><span data-stu-id="977b2-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="977b2-2047">**name** — указатель на назначение для указателя на имя потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="977b2-2048">**state** — указатель на назначение для текущего состояния выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="977b2-2049">Возможные значения:</span><span class="sxs-lookup"><span data-stu-id="977b2-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="977b2-2050">**TX_READY**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="977b2-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="977b2-2051">**TX_COMPLETED**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="977b2-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="977b2-2052">**TX_TERMINATED**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="977b2-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="977b2-2053">**TX_SUSPENDED**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="977b2-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="977b2-2054">**TX_SLEEP**: (0x04)</span><span class="sxs-lookup"><span data-stu-id="977b2-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="977b2-2055">**TX_QUEUE_SUSP**: (0x05)</span><span class="sxs-lookup"><span data-stu-id="977b2-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="977b2-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span><span class="sxs-lookup"><span data-stu-id="977b2-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="977b2-2057">**TX_EVENT_FLAG**: (0x07)</span><span class="sxs-lookup"><span data-stu-id="977b2-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="977b2-2058">**TX_BLOCK_MEMORY**: (0x08)</span><span class="sxs-lookup"><span data-stu-id="977b2-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="977b2-2059">**TX_BYTE_MEMORY**: (0x09)</span><span class="sxs-lookup"><span data-stu-id="977b2-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="977b2-2060">**TX_MUTEX_SUSP**: (0x0D)</span><span class="sxs-lookup"><span data-stu-id="977b2-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="977b2-2061">**run_count** — указатель на назначение для счетчика выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="977b2-2062">**priority** — указатель на назначение для приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="977b2-2063">**preemption_threshold** — указатель на назначение для порога вытеснения потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="977b2-2064">**time_slice** — указатель на назначение для интервала времени потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="977b2-2065">**next_thread** — указатель на назначение для указателя на следующий созданный поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="977b2-2066">**suspended_thread** — указатель на назначение для указателя на следующий поток в списке приостановки.</span><span class="sxs-lookup"><span data-stu-id="977b2-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2067">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2068">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2068">Return Values</span></span>

- <span data-ttu-id="977b2-2069">**TX_SUCCESS** (0x00) — успешное получение сведений о потоке.</span><span class="sxs-lookup"><span data-stu-id="977b2-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="977b2-2070">TX_THREAD_ERROR (0x0E) — недопустимый указатель на управление потоком.</span><span class="sxs-lookup"><span data-stu-id="977b2-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2071">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2071">Allowed From</span></span>

<span data-ttu-id="977b2-2072">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2073">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2073">Preemption Possible</span></span>

<span data-ttu-id="977b2-2074">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2075">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2075">Example</span></span>

```C
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
   thread "my_thread." */
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2076">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2076">See Also</span></span>

- <span data-ttu-id="977b2-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2077">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2078">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2080">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2086">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2087">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="977b2-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="977b2-2095">Получение информации о производительности потока</span><span class="sxs-lookup"><span data-stu-id="977b2-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2096">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="977b2-2097">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2097">Description</span></span>

<span data-ttu-id="977b2-2098">Эта служба получает сведения о производительности указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2099">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_THREAD_ENABLE_PERFORMANCE_INFO**, чтобы эта служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2100">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2100">Parameters</span></span> 

- <span data-ttu-id="977b2-2101">**ip_ptr** — указатель на созданный ранее поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="977b2-2102">**resumptions** — указатель на назначение для количества возобновлений этого потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="977b2-2103">**suspensions** — указатель на назначение для количества приостановок этого потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="977b2-2104">**solicited_preemptions** — указатель на назначение для количества вытеснений в результате вызова службы API ThreadX, выполненного этим потоком.</span><span class="sxs-lookup"><span data-stu-id="977b2-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="977b2-2105">**interrupt_preemptions** — указатель на назначение для количества вытеснений этого потока в результате обработки прерываний.</span><span class="sxs-lookup"><span data-stu-id="977b2-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="977b2-2106">**inversions** — указатель на назначение для количества инверсий приоритета для этого потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="977b2-2107">**time_slices** — указатель на назначение для количества интервалов времени для этого потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="977b2-2108">**relinquishes** — указатель на назначение для количества отказов потока, выполненных этим потоком.</span><span class="sxs-lookup"><span data-stu-id="977b2-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="977b2-2109">**timeouts** — указатель на назначение для количества истечений времени ожидания во время приостановки в этом потоке.</span><span class="sxs-lookup"><span data-stu-id="977b2-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="977b2-2110">**wait_aborts** — указатель на назначение для количества прерываний ожидания, выполненных в этом потоке.</span><span class="sxs-lookup"><span data-stu-id="977b2-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="977b2-2111">**last_preempted_by** — указатель на назначение для указателя на поток, который последним вытеснял этот поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2112">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2113">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2113">Return Values</span></span>

- <span data-ttu-id="977b2-2114">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="977b2-2115">**TX_PTR_ERROR** (0x03) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="977b2-2116">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2117">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2117">Allowed From</span></span>

<span data-ttu-id="977b2-2118">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2119">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2119">Example</span></span>

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

/* Retrieve performance information on the previously created
   thread. */
status = tx_thread_performance_info_get(&my_thread, &resumptions,
               &suspensions,
               &solicited_preemptions, &interrupt_preemptions,
               &priority_inversions, &time_slices,
               &relinquishes, &timeouts,
               &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2120">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2120">See Also</span></span>

- <span data-ttu-id="977b2-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2121">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2122">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2124">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2130">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2131">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="977b2-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="977b2-2139">Получение сведений о производительности системы потоков</span><span class="sxs-lookup"><span data-stu-id="977b2-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2140">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="977b2-2141">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2141">Description</span></span>

<span data-ttu-id="977b2-2142">Эта служба получает сведения о производительности всех потоков в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2143">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром **TX_THREAD_ENABLE_PERFORMANCE_INFO**, чтобы эта служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2144">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2144">Parameters</span></span>

- <span data-ttu-id="977b2-2145">**resumptions** — указатель на назначение для общего количества возобновлений потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="977b2-2146">**suspensions** — указатель на назначение для общего количества приостановок потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="977b2-2147">**solicited_preemptions** — указатель на назначение для общего количества вытеснений потоков в результате вызова потоком службы API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="977b2-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="977b2-2148">**interrupt_preemptions** — указатель на назначение для общего количества вытеснений потоков в результате обработки прерываний.</span><span class="sxs-lookup"><span data-stu-id="977b2-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="977b2-2149">**priority_inversions** — указатель на назначение для общего количества инверсий приоритета потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="977b2-2150">**time_slices** — указатель на назначение для общего количества интервалов времени потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="977b2-2151">**relinquishes** — указатель на назначение для общего количества освобождений потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="977b2-2152">**timeouts** — указатель на назначение для общего количества истечений времени ожидания во время приостановки потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="977b2-2153">**wait_aborts** — указатель на назначение для общего количества прерываний ожидания потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="977b2-2154">**non_idle_returns** — указатель на назначение, указывающее, сколько раз поток возвращался в систему, когда другой поток был готов к выполнению.</span><span class="sxs-lookup"><span data-stu-id="977b2-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="977b2-2155">**idle_returns** — указатель на назначение, указывающее, сколько раз поток возвращался в систему, когда не было других потоков, готовых к выполнению (простаивающая система).</span><span class="sxs-lookup"><span data-stu-id="977b2-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2156">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2157">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2157">Return Values</span></span>

- <span data-ttu-id="977b2-2158">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="977b2-2159">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2160">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2160">Allowed From</span></span>

<span data-ttu-id="977b2-2161">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2162">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2162">Example</span></span>

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

/* Retrieve performance information on all previously created
   thread. */
status = tx_thread_performance_system_info_get(&resumptions,
                &suspensions,
                &solicited_preemptions, &interrupt_preemptions,
                &priority_inversions, &time_slices, &relinquishes,
                &timeouts, &wait_aborts, &non_idle_returns,
                &idle_returns);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2163">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2163">See Also</span></span>

- <span data-ttu-id="977b2-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2164">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2165">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2167">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2173">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2174">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="977b2-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="977b2-2182">Изменение порога вытеснения потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2183">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="977b2-2184">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2184">Description</span></span>

<span data-ttu-id="977b2-2185">Эта служба изменяет порог вытеснения указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="977b2-2186">Порог вытеснения предотвращает вытеснение указанного потока потоками, не превышающими значение порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2187">При использовании порога вытеснения отключаются интервалы времени для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2188">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2188">Parameters</span></span>

- <span data-ttu-id="977b2-2189">**thread_ptr** — указатель на созданный ранее поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="977b2-2190">**new_threshold** — новый уровень приоритета для порога вытеснения (от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="977b2-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="977b2-2191">**old_threshold** — указатель на расположение для возврата предыдущего значения порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2192">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2192">Return Values</span></span>

- <span data-ttu-id="977b2-2193">**TX_SUCCESS** (0x00) — успешное изменение порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="977b2-2194">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2195">**TX_THRESH_ERROR** (0x18) — указанный новый порог вытеснения либо не является допустимым приоритетом потока (значение вне диапазона от 0 до (TX_MAX_PRIORITIES-1)), либо больше (низкий приоритет), чем текущее значение приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="977b2-2196">TX_PTR_ERROR (0x03) — недопустимый указатель на предыдущее место хранения preemptionthreshold.</span><span class="sxs-lookup"><span data-stu-id="977b2-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="977b2-2197">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2198">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2198">Allowed From</span></span>

<span data-ttu-id="977b2-2199">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2200">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2200">Preemption Possible</span></span>

<span data-ttu-id="977b2-2201">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2202">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2202">Example</span></span>

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

/* Disable all preemption of the specified thread. The
   current preemption-threshold is returned in
   "my_old_threshold". Assume that "my_thread" has
   already been created. */
status = tx_thread_preemption_change(&my_thread,
                             0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
   non-preemptable by another thread. Note that ISRs are
   not prevented by preemption disabling. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2203">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2203">See Also</span></span>

- <span data-ttu-id="977b2-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2204">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2205">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2207">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2213">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2214">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="977b2-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="977b2-2222">Изменение приоритета потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2223">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="977b2-2224">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2224">Description</span></span>

<span data-ttu-id="977b2-2225">Эта служба изменяет приоритет указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="977b2-2226">Допустимые значения приоритета находятся в диапазоне от 0 до (TX_MAX_PRIORITES-1), где значение 0 соответствует уровню наивысшего приоритета.</span><span class="sxs-lookup"><span data-stu-id="977b2-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2227">Порог вытеснения указанного потока автоматически устанавливается в соответствии с новым приоритетом.</span><span class="sxs-lookup"><span data-stu-id="977b2-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="977b2-2228">Если требуется новый порог, после этого вызова должна использоваться служба **tx_thread_preemption_change**.</span><span class="sxs-lookup"><span data-stu-id="977b2-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2229">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2229">Parameters</span></span>

- <span data-ttu-id="977b2-2230">**thread_ptr** — указатель на созданный ранее поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="977b2-2231">**new_priority** — новый уровень приоритета потока (от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="977b2-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="977b2-2232">**old_priority** — указатель на расположение для возврата предыдущего приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2233">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2233">Return Values</span></span>

- <span data-ttu-id="977b2-2234">**TX_SUCCESS** (0x00) — успешное изменение приоритета.</span><span class="sxs-lookup"><span data-stu-id="977b2-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="977b2-2235">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2236">TX_PRIORITY_ERROR (0x0F) — указан недопустимый новый приоритет (значение вне диапазона от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="977b2-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="977b2-2237">TX_PTR_ERROR (0x03) — недопустимый указатель на предыдущее приоритетное место хранения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="977b2-2238">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2239">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2239">Allowed From</span></span>

<span data-ttu-id="977b2-2240">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2241">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2241">Preemption Possible</span></span>

<span data-ttu-id="977b2-2242">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2243">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2243">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2244">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2244">See Also</span></span>

- <span data-ttu-id="977b2-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2245">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2246">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2248">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2254">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2255">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="977b2-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="977b2-2263">Передача управления другим потокам приложений</span><span class="sxs-lookup"><span data-stu-id="977b2-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2264">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="977b2-2265">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2265">Description</span></span>

<span data-ttu-id="977b2-2266">Эта служба передает управление процессором другим готовым к запуску потокам с аналогичным или более высоким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="977b2-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2267">В дополнение к передаче управления потокам с аналогичным приоритетом эта служба также передает управление потоку с наивысшим приоритетом, выполнение которого запрещено из-за настройки порога вытеснения текущего потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2268">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2268">Parameters</span></span>

<span data-ttu-id="977b2-2269">None</span><span class="sxs-lookup"><span data-stu-id="977b2-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2270">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2270">Return Values</span></span>

<span data-ttu-id="977b2-2271">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2272">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2272">Allowed From</span></span>

<span data-ttu-id="977b2-2273">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2274">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2274">Preemption Possible</span></span>

<span data-ttu-id="977b2-2275">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2276">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2276">Example</span></span>

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {

        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```
### <a name="see-also"></a><span data-ttu-id="977b2-2277">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2277">See Also</span></span>

- <span data-ttu-id="977b2-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2278">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2279">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2281">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2287">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2288">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="977b2-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2295">tx_thread_reset</span></span>

<span data-ttu-id="977b2-2296">Сброс потока</span><span class="sxs-lookup"><span data-stu-id="977b2-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2297">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2298">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2298">Description</span></span>

<span data-ttu-id="977b2-2299">Эта служба сбрасывает указанный поток для выполнения в точке входа, определенной при создании потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="977b2-2300">Для сброса поток должен находиться в состоянии **TX_COMPLETED** или **TX_TERMINATED**.</span><span class="sxs-lookup"><span data-stu-id="977b2-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2301">Для повторного выполнения поток необходимо возобновить.</span><span class="sxs-lookup"><span data-stu-id="977b2-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2302">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2302">Parameters</span></span> 

- <span data-ttu-id="977b2-2303">**thread_ptr** — указатель на созданный ранее поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2304">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2304">Return Values</span></span>

- <span data-ttu-id="977b2-2305">**TX_SUCCESS** (0x00) — успешный сброс потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="977b2-2306">**TX_NOT_DONE** (0x20) — указанный поток не находится в состоянии TX_COMPLETED или TX_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="977b2-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="977b2-2307">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="977b2-2308">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2309">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2309">Allowed From</span></span>

<span data-ttu-id="977b2-2310">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2311">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2312">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2312">See Also</span></span>

- <span data-ttu-id="977b2-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2313">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2314">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2316">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2323">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="977b2-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2330">tx_thread_resume</span></span>

<span data-ttu-id="977b2-2331">Возобновление приостановленного потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2332">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2333">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2333">Description</span></span>

<span data-ttu-id="977b2-2334">Эта служба возобновляет или подготавливает к выполнению поток, который ранее был приостановлен вызовом ***tx_thread_suspend***.</span><span class="sxs-lookup"><span data-stu-id="977b2-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="977b2-2335">Кроме того, эта служба возобновляет потоки, созданные без автоматического запуска.</span><span class="sxs-lookup"><span data-stu-id="977b2-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2336">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2336">Parameters</span></span>

- <span data-ttu-id="977b2-2337">**thread_ptr** — указатель на приостановленный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2338">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2338">Return Values</span></span>

- <span data-ttu-id="977b2-2339">**TX_SUCCESS** (0x00) — успешное возобновление потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="977b2-2340">**TX_SUSPEND_LIFTED** (0x19) — предустановленная отложенная приостановка была снята.</span><span class="sxs-lookup"><span data-stu-id="977b2-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="977b2-2341">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2342">**TX_RESUME_ERROR** (0x12) — указанный поток не приостановлен или приостановлен службой, отличной от **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="977b2-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2343">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2343">Allowed From</span></span>

<span data-ttu-id="977b2-2344">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2345">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2345">Preemption Possible</span></span>

<span data-ttu-id="977b2-2346">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2347">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2348">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2348">See Also</span></span>

- <span data-ttu-id="977b2-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2349">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2350">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2352">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2359">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="977b2-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2366">tx_thread_sleep</span></span>

<span data-ttu-id="977b2-2367">Приостановка текущего потока на указанное время</span><span class="sxs-lookup"><span data-stu-id="977b2-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2368">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="977b2-2369">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2369">Description</span></span>

<span data-ttu-id="977b2-2370">Эта служба приводит к приостановке вызывающего потока на указанное количество тактов таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="977b2-2371">Количество физического времени, связанное с тактом таймера, зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="977b2-2372">Эту службу можно вызывать только из потока приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2373">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2373">Parameters</span></span>

- <span data-ttu-id="977b2-2374">**timer_ticks** — количество тактов таймера для приостановки вызывающего потока приложения в диапазоне от 0 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="977b2-2375">Если указано значение 0, служба незамедлительно завершает работу.</span><span class="sxs-lookup"><span data-stu-id="977b2-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2376">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2376">Return Values</span></span>

- <span data-ttu-id="977b2-2377">**TX_SUCCESS** (0x00) — успешная приостановка работы потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="977b2-2378">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="977b2-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="977b2-2379">**TX_CALLER_ERROR** (0x13) — служба вызывается из непотока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2380">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2380">Allowed From</span></span>

<span data-ttu-id="977b2-2381">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2382">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2382">Preemption Possible</span></span>

<span data-ttu-id="977b2-2383">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2384">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2385">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2385">See Also</span></span>

- <span data-ttu-id="977b2-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2386">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2387">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2389">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2396">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2397">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="977b2-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="977b2-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="977b2-2404">Исключение выполнения потока в наборе ядер</span><span class="sxs-lookup"><span data-stu-id="977b2-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2405">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="977b2-2406">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2406">Description</span></span>

<span data-ttu-id="977b2-2407">Эта функция исключает выполнение указанного потока в ядрах, указанных в битовой карте, называемой "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="977b2-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="977b2-2408">Каждый бит в "*exclusion_map*" представляет собой ядро (бит 0 представляет ядро 0 и т. д.).</span><span class="sxs-lookup"><span data-stu-id="977b2-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="977b2-2409">Если бит установлен, соответствующее ядро исключается из выполнения указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2410">При использовании исключения процессора может потребоваться дополнительная обработка в логике сопоставления потока с ядром для поиска оптимального соответствия.</span><span class="sxs-lookup"><span data-stu-id="977b2-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="977b2-2411">Эта обработка ограничивается количеством готовых потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2412">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2412">Parameters</span></span> 

- <span data-ttu-id="977b2-2413">**thread_ptr** — указатель на поток для изменения исключения ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="977b2-2414">**exclusion_map** — битовая схема, где заданный бит указывает, что ядро исключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="977b2-2415">Если задать значение 0, поток будет выполняться в любом ядре (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="977b2-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2416">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2416">Return Values</span></span>

- <span data-ttu-id="977b2-2417">TX_SUCCESS (0x00) — успешное исключение ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="977b2-2418">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2419">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2419">Allowed From</span></span>

<span data-ttu-id="977b2-2420">Инициализация, подпрограммы ISR, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2421">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="977b2-2422">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2422">See Also</span></span>

- <span data-ttu-id="977b2-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="977b2-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="977b2-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="977b2-2426">Получает текущее исключение ядра потока</span><span class="sxs-lookup"><span data-stu-id="977b2-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2427">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2428">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2428">Description</span></span>

<span data-ttu-id="977b2-2429">Эта функция возвращает текущий список исключений ядер.</span><span class="sxs-lookup"><span data-stu-id="977b2-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2430">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2430">Parameters</span></span>

- <span data-ttu-id="977b2-2431">**thread_ptr** — указатель на поток, из которого извлекается исключение ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="977b2-2432">**exclusion_map_ptr** — назначение для текущей битовой карты исключения ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2433">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2433">Return Values</span></span>

- <span data-ttu-id="977b2-2434">TX_SUCCESS (0x00) — успешное извлечение исключения ядра потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="977b2-2435">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="977b2-2436">TX_PTR_ERROR (0x03) — недопустимый указатель на назначение исключения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2437">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2437">Allowed From</span></span>

<span data-ttu-id="977b2-2438">Инициализация, подпрограммы ISR, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2439">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="977b2-2440">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2440">See Also</span></span>

- <span data-ttu-id="977b2-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="977b2-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="977b2-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="977b2-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="977b2-2444">Получение текущего выполняемого ядра вызывающего объекта</span><span class="sxs-lookup"><span data-stu-id="977b2-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2445">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="977b2-2446">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2446">Description</span></span>

<span data-ttu-id="977b2-2447">Эта функция возвращает идентификатор ядра, которое выполняет эту службу.</span><span class="sxs-lookup"><span data-stu-id="977b2-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2448">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2448">Parameters</span></span>

<span data-ttu-id="977b2-2449">None</span><span class="sxs-lookup"><span data-stu-id="977b2-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2450">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2450">Return Values</span></span>

- <span data-ttu-id="977b2-2451">core_id: идентификатор ядра, выполняющегося в данный момент, (от 0 до TX_THREAD_SMP_MAX_CORES-1)</span><span class="sxs-lookup"><span data-stu-id="977b2-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2452">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2452">Allowed From</span></span>

<span data-ttu-id="977b2-2453">Инициализация, подпрограммы ISR, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2454">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2455">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2455">See Also</span></span>

- <span data-ttu-id="977b2-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="977b2-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="977b2-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="977b2-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="977b2-2459">Регистрация обратного вызова уведомления об ошибках стека потока</span><span class="sxs-lookup"><span data-stu-id="977b2-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2460">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="977b2-2461">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2461">Description</span></span>

<span data-ttu-id="977b2-2462">Эта служба регистрирует функцию обратного вызова уведомления для обработки ошибок стека потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="977b2-2463">Когда ThreadX SMP обнаруживает ошибку стека потока во время выполнения, он вызывает эту функцию уведомления для обработки ошибки.</span><span class="sxs-lookup"><span data-stu-id="977b2-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="977b2-2464">Порядок обработки ошибки полностью определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="977b2-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="977b2-2465">Может быть выполнено все, что угодно — от приостановки нарушающего потока до перезагрузки всей системы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2466">Библиотека ThreadX SMP должна быть создана с определенным параметром **TX_ENABLE_STACK_CHECKING**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2467">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2467">Parameters</span></span>

- <span data-ttu-id="977b2-2468">**error_handler** — указатель на функцию обработки ошибок стека приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="977b2-2469">Если этим значением является TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2470">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2470">Return Values</span></span>

- <span data-ttu-id="977b2-2471">**TX_SUCCESS** (0x00) — успешный сброс потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="977b2-2472">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2473">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2473">Allowed From</span></span>

<span data-ttu-id="977b2-2474">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2475">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="977b2-2476">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2476">See Also</span></span>

- <span data-ttu-id="977b2-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2477">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2478">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2480">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2487">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2488">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="977b2-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2494">tx_thread_suspend</span></span>

<span data-ttu-id="977b2-2495">Приостановка потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2496">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2497">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2497">Description</span></span>

<span data-ttu-id="977b2-2498">Эта служба приостанавливает указанный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="977b2-2499">Поток может вызывать эту службу для приостановки самого себя.</span><span class="sxs-lookup"><span data-stu-id="977b2-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2500">Если указанный поток уже приостановлен по другой причине, эта приостановка сохраняется до тех пор, пока не будет снята предыдущая.</span><span class="sxs-lookup"><span data-stu-id="977b2-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="977b2-2501">Когда это происходит, выполняется безусловная приостановка указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="977b2-2502">Дальнейшие запросы на безусловную приостановку безрезультатны.</span><span class="sxs-lookup"><span data-stu-id="977b2-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="977b2-2503">После приостановки поток необходимо возобновить с помощью ***tx_thread_resume*** для повторного выполнения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="977b2-2504">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2504">Parameters</span></span>

- <span data-ttu-id="977b2-2505">**thread_ptr** — указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2506">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2506">Return Values</span></span>

- <span data-ttu-id="977b2-2507">**TX_SUCCESS** (0x00) — успешная приостановка потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="977b2-2508">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2509">**TX_SUSPEND_ERROR** (0x14) — указанный поток находится в состоянии прекращения или завершения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="977b2-2510">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2511">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2511">Allowed From</span></span>

<span data-ttu-id="977b2-2512">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2513">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2513">Preemption Possible</span></span>

<span data-ttu-id="977b2-2514">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2515">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2516">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2516">See Also</span></span>

- <span data-ttu-id="977b2-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2517">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2518">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2520">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2527">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2528">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="977b2-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2534">tx_thread_terminate</span></span>

<span data-ttu-id="977b2-2535">Прекращение потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2536">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2537">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2537">Description</span></span>

<span data-ttu-id="977b2-2538">Эта служба прекращает указанный поток приложения независимо от того, приостановлен ли он.</span><span class="sxs-lookup"><span data-stu-id="977b2-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="977b2-2539">Поток может вызывать эту службу для своего прекращения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2540">После прекращения работы поток необходимо сбросить для повторного выполнения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="977b2-2541">Ответственность за то, что поток находится в состоянии, подходящем для завершения, лежит на приложении.</span><span class="sxs-lookup"><span data-stu-id="977b2-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="977b2-2542">Например, поток не должен прекращаться во время выполнения критической обработки приложения или внутри других компонентов ПО промежуточного слоя, где он может оставить такую обработку в неизвестном состоянии.</span><span class="sxs-lookup"><span data-stu-id="977b2-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2543">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2543">Parameters</span></span>

- <span data-ttu-id="977b2-2544">**thread_ptr** — указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2545">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2545">Return Values</span></span>

- <span data-ttu-id="977b2-2546">**TX_SUCCESS** (0x00) — успешное прекращение потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="977b2-2547">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2548">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2549">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2549">Allowed From</span></span>

<span data-ttu-id="977b2-2550">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2551">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2551">Preemption Possible</span></span>

<span data-ttu-id="977b2-2552">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2553">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2554">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2554">See Also</span></span>

- <span data-ttu-id="977b2-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2555">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2556">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2558">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2565">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2566">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="977b2-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="977b2-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="977b2-2573">Изменение интервала времени потока приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2574">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="977b2-2575">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2575">Description</span></span>

<span data-ttu-id="977b2-2576">Эта служба изменяет интервал времени указанного потока приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="977b2-2577">Выбор интервала времени для потока гарантирует, что он не будет выполняться больше указанного количества тактов таймера, прежде чем другие потоки с такими же или более высокими приоритетами получат возможность запуска.</span><span class="sxs-lookup"><span data-stu-id="977b2-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2578">При использовании порога вытеснения отключаются интервалы времени для указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2579">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2579">Parameters</span></span>

- <span data-ttu-id="977b2-2580">**thread_ptr** — указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="977b2-2581">**new_time_slice** — новое значение интервала времени.</span><span class="sxs-lookup"><span data-stu-id="977b2-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="977b2-2582">Допустимые значения: TX_NO_TIME_SLICE и числовые значения от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="977b2-2583">**old_time_slice** — указатель на расположение для хранения предыдущего значения интервала времени указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2584">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2584">Return Values</span></span>

- <span data-ttu-id="977b2-2585">**TX_SUCCESS** (0x00) — успешное изменение интервала времени.</span><span class="sxs-lookup"><span data-stu-id="977b2-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="977b2-2586">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2587">TX_PTR_ERROR (0x03) — недопустимый указатель на расположения для хранения предыдущего значения интервала времени.</span><span class="sxs-lookup"><span data-stu-id="977b2-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="977b2-2588">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2589">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2589">Allowed From</span></span>

<span data-ttu-id="977b2-2590">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2591">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2591">Preemption Possible</span></span>

<span data-ttu-id="977b2-2592">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2593">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2593">Example</span></span>

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

/* Change the time-slice of the thread associated with
   "my_thread" to 20. This will mean that "my_thread"
   can only run for 20 timer-ticks consecutively before
   other threads of equal or higher priority get a chance
   to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
                             &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
   has been changed to 20 and the previous time-slice is
   in "my_old_time_slice." */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2594">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2594">See Also</span></span>

- <span data-ttu-id="977b2-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2595">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2596">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2598">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2605">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2606">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="977b2-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="977b2-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="977b2-2613">Прерывание приостановки указанного потока</span><span class="sxs-lookup"><span data-stu-id="977b2-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2614">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="977b2-2615">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2615">Description</span></span>

<span data-ttu-id="977b2-2616">Эта служба прерывает спящий режим или приостановку любого другого объекта указанного потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="977b2-2617">Если ожидание прерывается, значение TX_WAIT_ABORTED возвращается из службы, которую ожидал поток.</span><span class="sxs-lookup"><span data-stu-id="977b2-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2618">Эта служба не освобождает явную приостановку, выполняемую службой tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="977b2-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2619">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2619">Parameters</span></span>

- <span data-ttu-id="977b2-2620">**thread_ptr** — указатель на созданный ранее поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2621">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2621">Return Values</span></span>

- <span data-ttu-id="977b2-2622">**TX_SUCCESS** (0x00) — успешное прерывание ожидания потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="977b2-2623">TX_THREAD_ERROR (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="977b2-2624">**TX_WAIT_ABORT_ERROR** (0x1B) — указанный поток не находится в состоянии ожидания.</span><span class="sxs-lookup"><span data-stu-id="977b2-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2625">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2625">Allowed From</span></span>

<span data-ttu-id="977b2-2626">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2627">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2627">Preemption Possible</span></span>

<span data-ttu-id="977b2-2628">Да</span><span class="sxs-lookup"><span data-stu-id="977b2-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2629">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2630">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2630">See Also</span></span>

- <span data-ttu-id="977b2-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2631">tx_thread_create</span></span>
- <span data-ttu-id="977b2-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2632">tx_thread_delete</span></span>
- <span data-ttu-id="977b2-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="977b2-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="977b2-2634">tx_thread_identify</span></span>
- <span data-ttu-id="977b2-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="977b2-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="977b2-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="977b2-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="977b2-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="977b2-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="977b2-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="977b2-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="977b2-2641">tx_thread_reset</span></span>
- <span data-ttu-id="977b2-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="977b2-2642">tx_thread_resume</span></span>
- <span data-ttu-id="977b2-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="977b2-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="977b2-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="977b2-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="977b2-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="977b2-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="977b2-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="977b2-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="977b2-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="977b2-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2648">tx_time_get</span></span>

<span data-ttu-id="977b2-2649">Получение текущего времени</span><span class="sxs-lookup"><span data-stu-id="977b2-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2650">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="977b2-2651">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2651">Description</span></span>

<span data-ttu-id="977b2-2652">Эта служба возвращает информацию, содержащуюся во внутренних системных часах.</span><span class="sxs-lookup"><span data-stu-id="977b2-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="977b2-2653">Каждый такт таймера увеличивает значение внутренних системных часов на единицу.</span><span class="sxs-lookup"><span data-stu-id="977b2-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="977b2-2654">Во время инициализации для системных часов задается нулевое значение, которое можно изменить с помощью службы ***tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="977b2-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2655">Фактическое время, представленное каждым тактом таймера, зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2656">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2656">Parameters</span></span>

<span data-ttu-id="977b2-2657">None</span><span class="sxs-lookup"><span data-stu-id="977b2-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2658">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2658">Return Values</span></span>

- <span data-ttu-id="977b2-2659">Такты системных часов — значение внутренних автономных системных часов.</span><span class="sxs-lookup"><span data-stu-id="977b2-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2660">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2660">Allowed From</span></span>

<span data-ttu-id="977b2-2661">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2662">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2662">Preemption Possible</span></span>

<span data-ttu-id="977b2-2663">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2664">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2665">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2665">See Also</span></span>

- <span data-ttu-id="977b2-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="977b2-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="977b2-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="977b2-2667">tx_time_set</span></span>

<span data-ttu-id="977b2-2668">Установка текущего времени</span><span class="sxs-lookup"><span data-stu-id="977b2-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2669">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="977b2-2670">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2670">Description</span></span>

<span data-ttu-id="977b2-2671">Эта служба устанавливает для внутренних системных часов указанное значение.</span><span class="sxs-lookup"><span data-stu-id="977b2-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="977b2-2672">Каждый такт таймера увеличивает значение внутренних системных часов на единицу.</span><span class="sxs-lookup"><span data-stu-id="977b2-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2673">Фактическое время, представленное каждым тактом таймера, зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2674">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2674">Parameters</span></span>

- <span data-ttu-id="977b2-2675">**new_time** — новое значение времени для размещения в системных часах, допустимы значения от 0 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2676">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2676">Return Values</span></span>

<span data-ttu-id="977b2-2677">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2678">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2678">Allowed From</span></span>

<span data-ttu-id="977b2-2679">Потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2680">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2680">Preemption Possible</span></span>

<span data-ttu-id="977b2-2681">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2682">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2683">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2683">See Also</span></span>

- <span data-ttu-id="977b2-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="977b2-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2685">tx_timer_activate</span></span>

<span data-ttu-id="977b2-2686">Активация таймера приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2687">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2688">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2688">Description</span></span>

<span data-ttu-id="977b2-2689">Эта служба активирует указанный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="977b2-2690">Подпрограммы после истечения срока действия таймеров, которые истекают одновременно, выполняются в том порядке, в котором они были активированы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-2691">Одноразовый таймер с истекшим сроком действия необходимо сбросить с помощью **tx_timer_change**, прежде чем его можно будет снова активировать.</span><span class="sxs-lookup"><span data-stu-id="977b2-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2692">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2692">Parameters</span></span>

- <span data-ttu-id="977b2-2693">**timer_ptr** — указатель на созданный ранее таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2694">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2694">Return Values</span></span>

- <span data-ttu-id="977b2-2695">**TX_SUCCESS** (0x00) — успешная активация таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="977b2-2696">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="977b2-2697">**TX_ACTIVATE_ERROR** (0x17) — таймер уже активен или является одноразовым таймером, срок действия которого уже истек.</span><span class="sxs-lookup"><span data-stu-id="977b2-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2698">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2698">Allowed From</span></span>

<span data-ttu-id="977b2-2699">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2700">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2700">Preemption Possible</span></span>

<span data-ttu-id="977b2-2701">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2702">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2703">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2703">See Also</span></span>

- <span data-ttu-id="977b2-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2704">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2705">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2707">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="977b2-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="977b2-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2711">tx_timer_change</span></span>

<span data-ttu-id="977b2-2712">Изменение таймера приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2713">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="977b2-2714">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2714">Description</span></span>

<span data-ttu-id="977b2-2715">Эта служба изменяет характеристики истечения срока действия указанного таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="977b2-2716">Перед вызовом этой службы таймер необходимо отключить.</span><span class="sxs-lookup"><span data-stu-id="977b2-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2717">После вызова этой службы требуется вызов службы **tx_timer_activate**, чтобы снова запустить таймер.</span><span class="sxs-lookup"><span data-stu-id="977b2-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2718">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2718">Parameters</span></span>

- <span data-ttu-id="977b2-2719">**timer_ptr** — указатель на блок управления таймером.</span><span class="sxs-lookup"><span data-stu-id="977b2-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="977b2-2720">**initial_ticks** указывает начальное количество тактов для истечения срока действия таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="977b2-2721">Допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="977b2-2722">**reschedule_ticks** указывает количество тактов для истечений срока действия всех таймеров после первого.</span><span class="sxs-lookup"><span data-stu-id="977b2-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="977b2-2723">Нулевое значение этого параметра делает таймер одноразовым.</span><span class="sxs-lookup"><span data-stu-id="977b2-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="977b2-2724">В противном случае для периодических таймеров допустимы значения от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="977b2-2725">Одноразовый таймер с истекшим сроком действия необходимо сбросить с помощью **tx_timer_change**, прежде чем его можно будет снова активировать.</span><span class="sxs-lookup"><span data-stu-id="977b2-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2726">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2726">Return Values</span></span>

- <span data-ttu-id="977b2-2727">**TX_SUCCESS** (0x00) — успешное изменение таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="977b2-2728">TX_TIMER_ERROR (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="977b2-2729">TX_TICK_ERROR (0x16) — указано недопустимое значение (ноль) для начальных тактов.</span><span class="sxs-lookup"><span data-stu-id="977b2-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="977b2-2730">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2731">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2731">Allowed From</span></span>

<span data-ttu-id="977b2-2732">Потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2733">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2733">Preemption Possible</span></span>

<span data-ttu-id="977b2-2734">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2735">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2735">Example</span></span>

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a><span data-ttu-id="977b2-2736">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2736">See Also</span></span>

- <span data-ttu-id="977b2-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2737">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2738">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2740">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="977b2-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="977b2-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2744">tx_timer_create</span></span>

<span data-ttu-id="977b2-2745">Создание таймера приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2746">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="977b2-2747">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2747">Description</span></span>

<span data-ttu-id="977b2-2748">Эта служба создает таймер приложения с указанной функцией истечения времени, а также периодичностью.</span><span class="sxs-lookup"><span data-stu-id="977b2-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2749">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2749">Parameters</span></span>

- <span data-ttu-id="977b2-2750">**timer_ptr** — указатель на блок управления таймером.</span><span class="sxs-lookup"><span data-stu-id="977b2-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="977b2-2751">**name_ptr** — указатель на имя таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="977b2-2752">**expiration_function** — функция приложения, вызываемая по истечении времени таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="977b2-2753">**expiration_input** — входные данные для передачи в функцию истечения времени по истечении времени таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="977b2-2754">**initial_ticks** указывает начальное количество тактов для истечения срока действия таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="977b2-2755">Допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="977b2-2756">**reschedule_ticks** указывает количество тактов для истечений срока действия всех таймеров после первого.</span><span class="sxs-lookup"><span data-stu-id="977b2-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="977b2-2757">Нулевое значение этого параметра делает таймер одноразовым.</span><span class="sxs-lookup"><span data-stu-id="977b2-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="977b2-2758">В противном случае для периодических таймеров допустимы значения от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="977b2-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="977b2-2759">По истечении времени одноразового таймера его необходимо сбросить с помощью tx_timer_change, прежде чем снова активировать.</span><span class="sxs-lookup"><span data-stu-id="977b2-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="977b2-2760">**auto_activate** определяет, активируется ли таймер автоматически во время создания.</span><span class="sxs-lookup"><span data-stu-id="977b2-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="977b2-2761">Если этим значением является **TX_AUTO_ACTIVATE** (0x01), таймер активирован.</span><span class="sxs-lookup"><span data-stu-id="977b2-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="977b2-2762">В противном случае, если выбрано значение **TX_NO_ACTIVATE** (0x00), таймер создается в неактивном состоянии.</span><span class="sxs-lookup"><span data-stu-id="977b2-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="977b2-2763">В этом случае для фактического запуска таймера необходим последующий сервисный вызов **_tx_timer_activate_**.</span><span class="sxs-lookup"><span data-stu-id="977b2-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2764">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2764">Return Values</span></span>

- <span data-ttu-id="977b2-2765">**TX_SUCCESS** (0x00) — успешное создание таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="977b2-2766">TX_TIMER_ERROR (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="977b2-2767">Либо указатель имеет значение NULL, либо таймер уже создан.</span><span class="sxs-lookup"><span data-stu-id="977b2-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="977b2-2768">TX_TICK_ERROR (0x16) — указано недопустимое значение (ноль) для начальных тактов.</span><span class="sxs-lookup"><span data-stu-id="977b2-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="977b2-2769">TX_ACTIVATE_ERROR (0x17) — выбрана недопустимая активация.</span><span class="sxs-lookup"><span data-stu-id="977b2-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="977b2-2770">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2771">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2771">Allowed From</span></span>

<span data-ttu-id="977b2-2772">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2773">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2773">Preemption Possible</span></span>

<span data-ttu-id="977b2-2774">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2775">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2775">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2776">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2776">See Also</span></span>

- <span data-ttu-id="977b2-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2777">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2778">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2780">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="977b2-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="977b2-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="977b2-2785">Деактивация таймера приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2786">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="977b2-2787">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2787">Description</span></span>

<span data-ttu-id="977b2-2788">Эта служба деактивирует указанный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="977b2-2789">Если таймер уже деактивирован, эта служба не действует.</span><span class="sxs-lookup"><span data-stu-id="977b2-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2790">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2790">Parameters</span></span> 

- <span data-ttu-id="977b2-2791">**timer_ptr** — указатель на созданный ранее таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2792">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2792">Return Values</span></span>

- <span data-ttu-id="977b2-2793">**TX_SUCCESS** (0x00) — успешная деактивация таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="977b2-2794">TX_TIMER_ERROR (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2795">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2795">Allowed From</span></span>

<span data-ttu-id="977b2-2796">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2797">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2797">Preemption Possible</span></span>

<span data-ttu-id="977b2-2798">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2799">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2800">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2800">See Also</span></span>

- <span data-ttu-id="977b2-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2801">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2802">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2803">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2804">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="977b2-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="977b2-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2808">tx_timer_delete</span></span>

<span data-ttu-id="977b2-2809">Удаление таймера приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2810">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2811">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2811">Description</span></span>

<span data-ttu-id="977b2-2812">Эта служба удаляет указанный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2813">Ответственность за предотвращение использования удаленного таймера лежит на приложении.</span><span class="sxs-lookup"><span data-stu-id="977b2-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2814">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2814">Parameters</span></span> 

- <span data-ttu-id="977b2-2815">**timer_ptr** — указатель на созданный ранее таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2816">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2816">Return Values</span></span>

- <span data-ttu-id="977b2-2817">**TX_SUCCESS** (0x00) — успешное удаление таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="977b2-2818">TX_TIMER_ERROR (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="977b2-2819">TX_CALLER_ERROR (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="977b2-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2820">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2820">Allowed From</span></span>

<span data-ttu-id="977b2-2821">Потоки</span><span class="sxs-lookup"><span data-stu-id="977b2-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2822">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2822">Preemption Possible</span></span>

<span data-ttu-id="977b2-2823">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2824">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2825">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2825">See Also</span></span>

- <span data-ttu-id="977b2-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2826">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2827">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2828">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="977b2-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="977b2-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2833">tx_timer_info_get</span></span>

<span data-ttu-id="977b2-2834">Получение сведений о таймере приложения</span><span class="sxs-lookup"><span data-stu-id="977b2-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2835">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="977b2-2836">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2836">Description</span></span>

<span data-ttu-id="977b2-2837">Эта служба получает сведения об указанном таймере приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2838">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2838">Parameters</span></span>

- <span data-ttu-id="977b2-2839">**timer_ptr** — указатель на созданный ранее таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="977b2-2840">**name** — указатель на назначение для указателя на имя таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="977b2-2841">**active** — указатель на назначение для указания активности таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="977b2-2842">Если таймер неактивен или эта служба вызывается из самого таймера, возвращается значение TX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="977b2-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="977b2-2843">В противном случае, если таймер активен, возвращается значение TX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="977b2-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="977b2-2844">**remaining_ticks** — указатель на назначение для количества тактов таймера, оставшихся до истечения его срока действия.</span><span class="sxs-lookup"><span data-stu-id="977b2-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="977b2-2845">**reschedule_ticks** — указатель на назначение для количества тактов таймера, которые будут использоваться для автоматического перепланирования этого таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="977b2-2846">Если значение равно нулю, то таймер является одноразовым и не будет перепланирован.</span><span class="sxs-lookup"><span data-stu-id="977b2-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="977b2-2847">**next_timer** — указатель на назначение для указателя следующего созданного таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="977b2-2848">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2849">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2849">Return Values</span></span>

- <span data-ttu-id="977b2-2850">**TX_SUCCESS** (0x00) — успешное получение сведений о таймере.</span><span class="sxs-lookup"><span data-stu-id="977b2-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="977b2-2851">TX_TIMER_ERROR (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2852">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2852">Allowed From</span></span>

<span data-ttu-id="977b2-2853">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="977b2-2854">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="977b2-2854">Preemption Possible</span></span>

<span data-ttu-id="977b2-2855">Нет</span><span class="sxs-lookup"><span data-stu-id="977b2-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2856">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2856">Example</span></span>

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2857">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2857">See Also</span></span>

- <span data-ttu-id="977b2-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2858">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2859">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2860">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2862">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="977b2-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="977b2-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="977b2-2867">Получение сведений о производительности таймера</span><span class="sxs-lookup"><span data-stu-id="977b2-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2868">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="977b2-2869">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2869">Description</span></span>

<span data-ttu-id="977b2-2870">Эта служба получает сведения о производительности указанного таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2871">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром  **TX_TIMER_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2872">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2872">Parameters</span></span> 

- <span data-ttu-id="977b2-2873">**timer_ptr** — указатель на созданный ранее таймер.</span><span class="sxs-lookup"><span data-stu-id="977b2-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="977b2-2874">**activates** — указатель на назначение для количества запросов на активацию, выполненных для этого таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="977b2-2875">**reactivates** — указатель на назначение для количества автоматических повторных активаций, выполненных для этого периодического таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="977b2-2876">**deactivates** — указатель на назначение для количества запросов на деактивацию, выполненных для этого таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="977b2-2877">**expirations** — указатель на назначение для количества истечений срока действия этого таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="977b2-2878">**expiration_adjusts** — указатель на назначение для количества внутренних корректировок срока действия, выполненных для этого таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="977b2-2879">Эти корректировки выполняются при обработке прерывания таймера для таймеров, размер которых превышает размер списка таймеров по умолчанию (таймеры по умолчанию с истечением срока более 32 тактов).</span><span class="sxs-lookup"><span data-stu-id="977b2-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2880">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2881">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2881">Return Values</span></span>

- <span data-ttu-id="977b2-2882">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="977b2-2883">**TX_PTR_ERROR** (0x03) — недопустимый указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="977b2-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="977b2-2884">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2885">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2885">Allowed From</span></span>

<span data-ttu-id="977b2-2886">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2887">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2887">Example</span></span>

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2888">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2888">See Also</span></span>

- <span data-ttu-id="977b2-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2889">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2890">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2891">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2893">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="977b2-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="977b2-2897">Получение сведений о производительности системы таймеров</span><span class="sxs-lookup"><span data-stu-id="977b2-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2898">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="977b2-2899">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2899">Description</span></span>

<span data-ttu-id="977b2-2900">Эта служба получает сведения о производительности всех таймеров приложений в системе.</span><span class="sxs-lookup"><span data-stu-id="977b2-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2901">Библиотека и приложение ThreadX SMP должны быть созданы с определенным параметром  **TX_TIMER_ENABLE_PERFORMANCE_INFO**, чтобы служба могла вернуть сведения о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2902">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2902">Parameters</span></span>

- <span data-ttu-id="977b2-2903">**activates** — указатель на назначение для общего количества запросов на активацию, выполненных для всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="977b2-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="977b2-2904">**reactivates** — указатель на назначение для общего количества автоматических повторных активаций, выполненных для всех периодических таймеров.</span><span class="sxs-lookup"><span data-stu-id="977b2-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="977b2-2905">**deactivates** — указатель на назначение для общего количества запросов на деактивацию, выполненных для всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="977b2-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="977b2-2906">**expirations** — указатель на назначение для общего количества истечений срока действия всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="977b2-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="977b2-2907">**expiration_adjusts** — указатель на назначение для общего количества внутренних корректировок срока действия, выполненных для всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="977b2-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="977b2-2908">Эти корректировки выполняются при обработке прерывания таймера для таймеров, размер которых превышает размер списка таймеров по умолчанию (таймеры по умолчанию с истечением срока более 32 тактов).</span><span class="sxs-lookup"><span data-stu-id="977b2-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2909">Если для любого параметра задано значение TX_NULL, это означает, что параметр не требуется.</span><span class="sxs-lookup"><span data-stu-id="977b2-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2910">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2910">Return Values</span></span>

- <span data-ttu-id="977b2-2911">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы таймеров.</span><span class="sxs-lookup"><span data-stu-id="977b2-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="977b2-2912">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована так, чтобы можно было располагать сведениями о производительности.</span><span class="sxs-lookup"><span data-stu-id="977b2-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2913">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2913">Allowed From</span></span>

<span data-ttu-id="977b2-2914">Инициализация, потоки, таймеры и подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="977b2-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2915">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2915">Example</span></span>

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="977b2-2916">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2916">See Also</span></span>

- <span data-ttu-id="977b2-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="977b2-2917">tx_timer_activate</span></span>
- <span data-ttu-id="977b2-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="977b2-2918">tx_timer_change</span></span>
- <span data-ttu-id="977b2-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="977b2-2919">tx_timer_create</span></span>
- <span data-ttu-id="977b2-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="977b2-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="977b2-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="977b2-2921">tx_timer_delete</span></span>
- <span data-ttu-id="977b2-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="977b2-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="977b2-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="977b2-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="977b2-2925">Исключение выполнения таймера для набора ядер</span><span class="sxs-lookup"><span data-stu-id="977b2-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2926">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="977b2-2927">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2927">Description</span></span>

<span data-ttu-id="977b2-2928">Эта функция исключает выполнение указанного таймера в ядрах, указанных в битовой карте, которая называется "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="977b2-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="977b2-2929">Каждый бит в "*exclusion_map*" представляет собой ядро (бит 0 представляет ядро 0 и т. д.).</span><span class="sxs-lookup"><span data-stu-id="977b2-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="977b2-2930">Если бит установлен, соответствующее ядро исключается из выполнения указанного таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="977b2-2931">При использовании исключения процессора может потребоваться дополнительная обработка в логике сопоставления потока с ядром для поиска оптимального соответствия.</span><span class="sxs-lookup"><span data-stu-id="977b2-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="977b2-2932">Эта обработка ограничивается количеством готовых потоков.</span><span class="sxs-lookup"><span data-stu-id="977b2-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2933">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2933">Parameters</span></span>

- <span data-ttu-id="977b2-2934">**timer_ptr** — указатель на таймер для изменения исключения ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="977b2-2935">**exclusion_map** — битовая схема, где заданный бит указывает, что ядро исключено.</span><span class="sxs-lookup"><span data-stu-id="977b2-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="977b2-2936">Если задать значение 0, таймер будет работать на любом ядре (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="977b2-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2937">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2937">Return Values</span></span>

- <span data-ttu-id="977b2-2938">**TX_SUCCESS** (0x00) — успешное исключение ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="977b2-2939">**TX_TIMER_ERROR** (0x0E) — недопустимый указатель таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2940">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2940">Allowed From</span></span>

<span data-ttu-id="977b2-2941">Инициализация, подпрограммы ISR, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2942">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="977b2-2943">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2943">See Also</span></span>

- <span data-ttu-id="977b2-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="977b2-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="977b2-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="977b2-2946">Получает текущее исключение текущего ядра таймера</span><span class="sxs-lookup"><span data-stu-id="977b2-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="977b2-2947">Прототип</span><span class="sxs-lookup"><span data-stu-id="977b2-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="977b2-2948">Описание</span><span class="sxs-lookup"><span data-stu-id="977b2-2948">Description</span></span>

<span data-ttu-id="977b2-2949">Эта функция возвращает текущий список исключений ядер.</span><span class="sxs-lookup"><span data-stu-id="977b2-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="977b2-2950">Параметры</span><span class="sxs-lookup"><span data-stu-id="977b2-2950">Parameters</span></span>

- <span data-ttu-id="977b2-2951">**timer_ptr** — указатель на таймер, из которого извлекается исключение ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="977b2-2952">**exclusion_map_ptr** — назначение для текущей битовой карты исключения ядра.</span><span class="sxs-lookup"><span data-stu-id="977b2-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="977b2-2953">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="977b2-2953">Return Values</span></span>

- <span data-ttu-id="977b2-2954">TX_SUCCESS: (0x00) —успешное получение исключения ядра потока.</span><span class="sxs-lookup"><span data-stu-id="977b2-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="977b2-2955">TX_TIMER_ERROR: (0x0E) — недопустимый указатель таймера.</span><span class="sxs-lookup"><span data-stu-id="977b2-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="977b2-2956">TX_PTR_ERROR (0x03) — недопустимый указатель на назначение исключения.</span><span class="sxs-lookup"><span data-stu-id="977b2-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="977b2-2957">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="977b2-2957">Allowed From</span></span>

<span data-ttu-id="977b2-2958">Инициализация, подпрограммы ISR, потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="977b2-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="977b2-2959">Пример</span><span class="sxs-lookup"><span data-stu-id="977b2-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="977b2-2960">См. также:</span><span class="sxs-lookup"><span data-stu-id="977b2-2960">See Also</span></span>

- <span data-ttu-id="977b2-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="977b2-2961">tx_timer_smp_core_exclude</span></span>