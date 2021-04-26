---
title: Глава 6. События трассировки ThreadX в ОСРВ Azure
description: В этой главе описываются события ThreadX в ОСРВ Azure.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815756"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="062ed-103">Глава 6. События трассировки ThreadX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="062ed-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="062ed-104">В этой главе описываются события ThreadX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="062ed-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="062ed-105">Список событий и значков</span><span class="sxs-lookup"><span data-stu-id="062ed-105">List of Events and Icons</span></span>

<span data-ttu-id="062ed-106">Ниже приведен список событий ThreadX, отображаемых в TraceX.</span><span class="sxs-lookup"><span data-stu-id="062ed-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="062ed-107">**Значок**:</span><span class="sxs-lookup"><span data-stu-id="062ed-107">**Icon**</span></span>                         | <span data-ttu-id="062ed-108">**Значение**</span><span class="sxs-lookup"><span data-stu-id="062ed-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![Значок возобновления внутреннего потока](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="062ed-110">Возобновление внутреннего потока</span><span class="sxs-lookup"><span data-stu-id="062ed-110">Internal thread resume</span></span>  |
| ![Значок приостановки внутреннего потока](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="062ed-112">Приостановка внутреннего потока</span><span class="sxs-lookup"><span data-stu-id="062ed-112">Internal thread suspend</span></span> |
| ![Значок входа в подпрограмму обработки прерываний](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="062ed-114">Вход в подпрограмму обработки прерываний (ISR)</span><span class="sxs-lookup"><span data-stu-id="062ed-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![Значок выхода из подпрограммы обработки прерываний](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="062ed-116">Выход из подпрограммы обработки прерываний (ISR)</span><span class="sxs-lookup"><span data-stu-id="062ed-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![Значок внутреннего временного среза](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="062ed-118">Внутренний временной срез</span><span class="sxs-lookup"><span data-stu-id="062ed-118">Internal time-slice</span></span> |
| ![Значок выполнения](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="062ed-120">Запущен</span><span class="sxs-lookup"><span data-stu-id="062ed-120">Running</span></span> |
| ![Значок выделения пула блоков](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="062ed-122">**Выделение пула блоков** (*tx_block_allocate*)</span><span class="sxs-lookup"><span data-stu-id="062ed-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![Значок создания пула блоков](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="062ed-124">**Создание пула блоков** (*tx_block_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![Значок удаления пула блоков](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="062ed-126">**Удаление пула блоков** (*tx_block_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![Значок получения сведений о пуле блоков](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="062ed-128">**Получение сведений о пуле блоков** (*tx_block_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![Значок получения сведений о производительности пула блоков](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="062ed-130">**Получение сведений о производительности пула блоков** (*tx_block_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![Значок получения сведений о производительности системы пулов блоков](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="062ed-132">**Получение сведений о производительности системы пулов блоков** (*tx_block_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![Значок назначения приоритета пулу блоков](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="062ed-134">**Назначение приоритета пулу блоков** (*tx_block_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="062ed-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![Значок освобождения блока в пуле](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="062ed-136">**Освобождение блока в пуле** (*tx_block_release*)</span><span class="sxs-lookup"><span data-stu-id="062ed-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![Значок выделения памяти для пула байтов](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="062ed-138">**Выделение памяти для пула байтов** (*tx_byte_allocate*)</span><span class="sxs-lookup"><span data-stu-id="062ed-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![Значок создания пула байтов](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="062ed-140">**Создание пула байтов** (*tx_byte_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![Значок удаления пула байтов](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="062ed-142">**Удаление пула байтов** (*tx_byte_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![Значок получения сведений о пуле байтов](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="062ed-144">**Получение сведений о пуле байтов** (*tx_byte_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![Значок получения сведений о производительности пула байтов](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="062ed-146">**Получение сведений о производительности пула байтов** (*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![Значок получения сведений о производительности системы пулов байтов](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="062ed-148">**Получение сведений о производительности системы пулов байтов** (*tx_byte_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![\* Значок назначения приоритета пулу байтов](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="062ed-150">**Назначение приоритета пулу байтов** (*tx_byte_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="062ed-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![Значок освобождения байтов памяти в пуле](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="062ed-152">**Освобождение байтов памяти в пуле** (*tx_byte_release*)</span><span class="sxs-lookup"><span data-stu-id="062ed-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![Значок создания флагов событий](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="062ed-154">**Создание флагов событий** (*tx_event_flags_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![Значок удаления флагов событий](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="062ed-156">**Удаление флагов событий** (*tx_event_flags_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![Значок получения флагов событий](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="062ed-158">**Получение флагов событий** (*tx_event_flags_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![Значок получения сведений о флагах событий](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="062ed-160">**Получение сведений о флагах событий** (*tx_event_flags_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![Значок получения сведений о производительности флагов событий](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="062ed-162">**Получение сведений о производительности флагов событий** (*tx_event_flags_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![Значок получения сведений о производительности системы флагов событий](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="062ed-164">**Получение сведений о производительности системы флагов событий** (*tx_event_flags_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![Значок установки флагов событий](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="062ed-166">**Установка флагов событий** (*tx_event_flags_set*)</span><span class="sxs-lookup"><span data-stu-id="062ed-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![Значок уведомления об установке флагов событий](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="062ed-168">**Уведомление об установке флагов событий** (*tx_event_flags_set_notify*)</span><span class="sxs-lookup"><span data-stu-id="062ed-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![Значок включения и отключения прерывания](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="062ed-170">**Включение и отключение прерывания** (*tx_interrupt_control*)</span><span class="sxs-lookup"><span data-stu-id="062ed-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![Значок создания мьютекса](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="062ed-172">**Создание мьютекса** (*tx_mutex_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![Значок удаления мьютекса](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="062ed-174">**Удаление мьютекса** (*tx_mutex_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![Значок выполнения операции Get с мьютексом](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="062ed-176">**Выполнение операции Get с мьютексом** (*tx_mutex_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![Значок получения сведений о мьютексе](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="062ed-178">**Получение сведений о мьютексе** (*tx_mutex_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![Значок получения сведений о производительности мьютекса](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="062ed-180">**Получение сведений о производительности мьютекса** (*tx_mutex_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![Значок получения сведений о производительности системы мьютексов](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="062ed-182">**Получение сведений о производительности системы мьютексов** (*tx_mutex_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![Значок назначения приоритета мьютекса](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="062ed-184">**Назначение приоритета мьютекса** (*tx_mutex_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="062ed-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![Значок выполнения операции Put с мьютексом](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="062ed-186">**Выполнение операции Put с мьютексом** (*tx_mutex_put*)</span><span class="sxs-lookup"><span data-stu-id="062ed-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![Значок создания очереди](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="062ed-188">**Создание очереди** (*tx_queue_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![Значок удаления очереди](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="062ed-190">**Удаление очереди** (*tx_queue_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![Значок освобождения очереди](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="062ed-192">**Освобождение очереди** (*tx_queue_flush*)</span><span class="sxs-lookup"><span data-stu-id="062ed-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![Значок отправки сообщения в начало очереди](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="062ed-194">**Отправка сообщения в начало очереди** (*tx_queue_front_send*)</span><span class="sxs-lookup"><span data-stu-id="062ed-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![Значок получения сведений об очереди](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="062ed-196">**Получение сведений об очереди** (*tx_queue_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![Значок получения сведений о производительности очереди](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="062ed-198">**Получение сведений о производительности очереди** (*tx_queue_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![Значок получения сведений о производительности системы очередей](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="062ed-200">**Получение сведений о производительности системы очередей** (*tx_queue_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![Значок назначения приоритета очереди](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="062ed-202">**Назначение приоритета очереди** (*tx_queue_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="062ed-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![Значок сообщения о получении очередью](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="062ed-204">**Сообщение о получении очередью** (*tx_queue_receive*)</span><span class="sxs-lookup"><span data-stu-id="062ed-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![Значок сообщения об отправке в очередь](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="062ed-206">**Сообщение об отправке в очередь** (*tx_queue_send*)</span><span class="sxs-lookup"><span data-stu-id="062ed-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![Значок уведомления об отправке в очередь](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="062ed-208">**Уведомление об отправке в очередь** (*tx_queue_send_notify*)</span><span class="sxs-lookup"><span data-stu-id="062ed-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![Значок помещения в семафор с верхним пределом](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="062ed-210">**Помещение в семафор с верхним пределом** (*tx_semaphore_ceiling_put*)</span><span class="sxs-lookup"><span data-stu-id="062ed-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![Значок создания семафора](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="062ed-212">**Создание семафора** (*tx_semaphore_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![Значок удаления семафора](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="062ed-214">**Удаление семафора** (*tx_semaphore_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![Значок выполнения операции Get с семафором](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="062ed-216">**Выполнение операции Get с семафором** (*tx_semaphore_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![Значок получения сведений о семафоре](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="062ed-218">**Получение сведений о семафоре** (*tx_semaphore_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![Значок получения сведений о производительности семафора](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="062ed-220">**Получение сведений о производительности семафора** (*tx_semaphroe_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![Значок получения сведений о производительности системы семафоров](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="062ed-222">**Получение сведений о производительности системы семафоров** (*tx_semaphore_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![Значок назначения приоритета семафора](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="062ed-224">**Назначение приоритета семафора** (*tx_semaphore_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="062ed-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![Значок выполнения операции Put с семафором](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="062ed-226">**Выполнение операции Put с семафором** (*tx_semaphore_put*)</span><span class="sxs-lookup"><span data-stu-id="062ed-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![Значок уведомления об операции Put с семафором](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="062ed-228">**Уведомление об операции Put с семафором** (*tx_semaphore_put_notify*)</span><span class="sxs-lookup"><span data-stu-id="062ed-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![Значок создания потока](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="062ed-230">**Создание потока** (*tx_thread_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![Значок удаления потока](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="062ed-232">**Удаление потока** (*tx_thread_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![Значок уведомления о выходе из потока и входе в него](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="062ed-234">**Уведомление о выходе из потока и входе в него** (*tx_thread_entry_exit_notify*)</span><span class="sxs-lookup"><span data-stu-id="062ed-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![Значок определения потока](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="062ed-236">**Определение потока** (*tx_thread_identify*)</span><span class="sxs-lookup"><span data-stu-id="062ed-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![Значок получения сведений о потоке](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="062ed-238">**Получение сведений о потоке** (*tx_thread_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![Значок получения сведений о производительности потока](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="062ed-240">**Получение сведений о производительности потока** (*tx_thread_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![Значок получения системных сведений о производительности потоков](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="062ed-242">**Получение системных сведений о производительности потоков** (*tx_thread_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![Значок изменения вытеснения потока](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="062ed-244">**Изменение вытеснения потока** (*tx_thread_preemption_change*)</span><span class="sxs-lookup"><span data-stu-id="062ed-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![Значок изменения приоритета потока](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="062ed-246">**Изменение приоритета потока** (*tx_thread_priority_change*)</span><span class="sxs-lookup"><span data-stu-id="062ed-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![Значок освобождения потока](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="062ed-248">**Освобождение потока** (*tx_thread_relinquish*)</span><span class="sxs-lookup"><span data-stu-id="062ed-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![Значок сброса потока](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="062ed-250">**Сброс потока** (*tx_thread_reset*)</span><span class="sxs-lookup"><span data-stu-id="062ed-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\* Значок возобновления потока](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="062ed-252">**Возобновление потока** (\**tx_thread_resume*)</span><span class="sxs-lookup"><span data-stu-id="062ed-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![Значок перехода потока в спящий режим](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="062ed-254">**Переход потока в спящий режим** (*tx_thread_sleep*)\*</span><span class="sxs-lookup"><span data-stu-id="062ed-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![Значок уведомления об ошибке стека потоков](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="062ed-256">**Уведомление об ошибке стека потоков** (*tx_thread_stack_error_notify*)</span><span class="sxs-lookup"><span data-stu-id="062ed-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![Значок приостановки потока](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="062ed-258">**Приостановка потока** (*tx_thread_suspend*)</span><span class="sxs-lookup"><span data-stu-id="062ed-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![Значок завершения потока](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="062ed-260">**Завершение потока** (*tx_thread_terminate*)</span><span class="sxs-lookup"><span data-stu-id="062ed-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![Значок изменения временного среза потока](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="062ed-262">**Изменение временного среза потока** (*tx_thread_time_slice_change*)</span><span class="sxs-lookup"><span data-stu-id="062ed-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![Значок прерывания ожидания потока](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="062ed-264">**Прерывание ожидания потока** (*tx_thread_wait_abort*)</span><span class="sxs-lookup"><span data-stu-id="062ed-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![Значок получения времени](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="062ed-266">**Получение времени** (*tx_time_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-266">**Time get** (*tx_time_get*)</span></span> |
| ![Значок установки времени](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="062ed-268">**Установка времени** (*tx_time_set*)</span><span class="sxs-lookup"><span data-stu-id="062ed-268">**Time set** (*tx_time_set*)</span></span> |
| ![\* Значок активации таймера](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="062ed-270">**Активация таймера** (*tx_timer_activate*)</span><span class="sxs-lookup"><span data-stu-id="062ed-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![Значок изменения таймера](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="062ed-272">**Изменение таймера** (*tx_timer_change*)</span><span class="sxs-lookup"><span data-stu-id="062ed-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![Значок создания таймера](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="062ed-274">**Создание таймера** (*tx_timer_create*)</span><span class="sxs-lookup"><span data-stu-id="062ed-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![Значок отключения таймера](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="062ed-276">**Отключение таймера** (*tx_timer_deactivate*)</span><span class="sxs-lookup"><span data-stu-id="062ed-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![Значок удаления таймера](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="062ed-278">**Удаление таймера** (*tx_timer_delete*)</span><span class="sxs-lookup"><span data-stu-id="062ed-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![Значок получения сведений о таймере](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="062ed-280">**Получение сведений о таймере** (*tx_timer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![Значок получения сведений о производительности таймера](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="062ed-282">**Получение сведений о производительности таймера** (*tx_timer_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\* Значок получения системных сведений о производительности таймеров](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="062ed-284">**Получение системных сведений о производительности таймеров** (*tx_timer_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="062ed-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![Значок определяемого пользователем события](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="062ed-286">**Определяемое пользователем событие** (см. главу 10)</span><span class="sxs-lookup"><span data-stu-id="062ed-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="062ed-287">Описания событий</span><span class="sxs-lookup"><span data-stu-id="062ed-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="062ed-288">Возобновление внутреннего потока</span><span class="sxs-lookup"><span data-stu-id="062ed-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="062ed-289">Возобновление внутреннего потока</span><span class="sxs-lookup"><span data-stu-id="062ed-289">Internal thread resume</span></span>

<span data-ttu-id="062ed-290">**Значок** ![Значок возобновления внутреннего потока](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="062ed-291">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-291">**Description**</span></span>

<span data-ttu-id="062ed-292">Это событие представляет внутреннюю обработку в ThreadX, которая возобновляет поток для выполнения.</span><span class="sxs-lookup"><span data-stu-id="062ed-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="062ed-293">Если указанный поток обладает наивысшим приоритетом, а его выполнение не блокируется из-за превышения порогового значения для вытеснения, система начнет выполнение этого нового готового потока.</span><span class="sxs-lookup"><span data-stu-id="062ed-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="062ed-294">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-294">**Information Fields**</span></span>

- <span data-ttu-id="062ed-295">Поле сведений 1. Указатель на возобновляемый поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="062ed-296">Поле сведений 2. Предыдущее состояние возобновляемого потока (см. таблицу ниже).</span><span class="sxs-lookup"><span data-stu-id="062ed-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="062ed-297">Состояние потока</span><span class="sxs-lookup"><span data-stu-id="062ed-297">Thread state</span></span>                     | <span data-ttu-id="062ed-298">Значение</span><span class="sxs-lookup"><span data-stu-id="062ed-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="062ed-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="062ed-299">TX_READY</span></span>                         | <span data-ttu-id="062ed-300">0</span><span class="sxs-lookup"><span data-stu-id="062ed-300">0</span></span>       |
  |  <span data-ttu-id="062ed-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="062ed-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="062ed-302">1</span><span class="sxs-lookup"><span data-stu-id="062ed-302">1</span></span>       |
  |  <span data-ttu-id="062ed-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="062ed-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="062ed-304">2</span><span class="sxs-lookup"><span data-stu-id="062ed-304">2</span></span>       |
  |  <span data-ttu-id="062ed-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="062ed-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="062ed-306">3</span><span class="sxs-lookup"><span data-stu-id="062ed-306">3</span></span>       |
  |  <span data-ttu-id="062ed-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="062ed-307">TX_SLEEP</span></span>                         | <span data-ttu-id="062ed-308">4</span><span class="sxs-lookup"><span data-stu-id="062ed-308">4</span></span>       |
  |  <span data-ttu-id="062ed-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="062ed-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="062ed-310">5</span><span class="sxs-lookup"><span data-stu-id="062ed-310">5</span></span>       |
  |  <span data-ttu-id="062ed-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="062ed-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="062ed-312">6</span><span class="sxs-lookup"><span data-stu-id="062ed-312">6</span></span>       |
  |  <span data-ttu-id="062ed-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="062ed-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="062ed-314">7</span><span class="sxs-lookup"><span data-stu-id="062ed-314">7</span></span>       |
  |  <span data-ttu-id="062ed-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="062ed-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="062ed-316">8</span><span class="sxs-lookup"><span data-stu-id="062ed-316">8</span></span>       |
  |  <span data-ttu-id="062ed-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="062ed-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="062ed-318">9</span><span class="sxs-lookup"><span data-stu-id="062ed-318">9</span></span>       |
  |  <span data-ttu-id="062ed-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="062ed-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="062ed-320">12</span><span class="sxs-lookup"><span data-stu-id="062ed-320">12</span></span>      |
  |  <span data-ttu-id="062ed-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="062ed-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="062ed-322">13</span><span class="sxs-lookup"><span data-stu-id="062ed-322">13</span></span>      |

- <span data-ttu-id="062ed-323">Поле сведений 3. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="062ed-324">Поле сведений 4. Указатель на следующий поток с наивысшим приоритетом для выполнения.</span><span class="sxs-lookup"><span data-stu-id="062ed-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="062ed-325">Приостановка внутреннего потока</span><span class="sxs-lookup"><span data-stu-id="062ed-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="062ed-326">Приостановка внутреннего потока</span><span class="sxs-lookup"><span data-stu-id="062ed-326">Internal thread suspend</span></span>

<span data-ttu-id="062ed-327">**Значок** ![Значок приостановки внутреннего потока](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="062ed-328">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-328">**Description**</span></span>

<span data-ttu-id="062ed-329">Это событие представляет внутреннюю обработку в ThreadX, которая приостанавливает выполнение потока.</span><span class="sxs-lookup"><span data-stu-id="062ed-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="062ed-330">В четвертое поле сведений помещается следующий готовый к выполнению поток с наивысшим приоритетом.</span><span class="sxs-lookup"><span data-stu-id="062ed-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="062ed-331">Если это значение равно NULL, другие готовые к выполнению потоки отсутствуют, поэтому система бездействует.</span><span class="sxs-lookup"><span data-stu-id="062ed-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="062ed-332">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-332">**Information Fields**</span></span>

- <span data-ttu-id="062ed-333">Поле сведений 1. Указатель на приостановленный поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="062ed-334">Поле сведений 2. Новое состояние приостановленного потока (см. таблицу ниже).</span><span class="sxs-lookup"><span data-stu-id="062ed-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="062ed-335">Состояние потока</span><span class="sxs-lookup"><span data-stu-id="062ed-335">Thread state</span></span>                     | <span data-ttu-id="062ed-336">Значение</span><span class="sxs-lookup"><span data-stu-id="062ed-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="062ed-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="062ed-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="062ed-338">1</span><span class="sxs-lookup"><span data-stu-id="062ed-338">1</span></span>       |
  |  <span data-ttu-id="062ed-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="062ed-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="062ed-340">2</span><span class="sxs-lookup"><span data-stu-id="062ed-340">2</span></span>       |
  |  <span data-ttu-id="062ed-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="062ed-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="062ed-342">3</span><span class="sxs-lookup"><span data-stu-id="062ed-342">3</span></span>       |
  |  <span data-ttu-id="062ed-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="062ed-343">TX_SLEEP</span></span>                         | <span data-ttu-id="062ed-344">4</span><span class="sxs-lookup"><span data-stu-id="062ed-344">4</span></span>       |
  |  <span data-ttu-id="062ed-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="062ed-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="062ed-346">5</span><span class="sxs-lookup"><span data-stu-id="062ed-346">5</span></span>       |
  |  <span data-ttu-id="062ed-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="062ed-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="062ed-348">6</span><span class="sxs-lookup"><span data-stu-id="062ed-348">6</span></span>       |
  |  <span data-ttu-id="062ed-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="062ed-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="062ed-350">7</span><span class="sxs-lookup"><span data-stu-id="062ed-350">7</span></span>       |
  |  <span data-ttu-id="062ed-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="062ed-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="062ed-352">8</span><span class="sxs-lookup"><span data-stu-id="062ed-352">8</span></span>       |
  |  <span data-ttu-id="062ed-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="062ed-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="062ed-354">9</span><span class="sxs-lookup"><span data-stu-id="062ed-354">9</span></span>       |
  |  <span data-ttu-id="062ed-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="062ed-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="062ed-356">12</span><span class="sxs-lookup"><span data-stu-id="062ed-356">12</span></span>      |
  |  <span data-ttu-id="062ed-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="062ed-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="062ed-358">13</span><span class="sxs-lookup"><span data-stu-id="062ed-358">13</span></span>      |

- <span data-ttu-id="062ed-359">Поле сведений 3. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="062ed-360">Поле сведений 4. Указатель на следующий поток с наивысшим приоритетом для выполнения.</span><span class="sxs-lookup"><span data-stu-id="062ed-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="062ed-361">Если значение равно NULL, система бездействует.</span><span class="sxs-lookup"><span data-stu-id="062ed-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="062ed-362">Вход в подпрограмму обработки прерываний (ISR)</span><span class="sxs-lookup"><span data-stu-id="062ed-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="062ed-363">Вход в ISR</span><span class="sxs-lookup"><span data-stu-id="062ed-363">Enter ISR</span></span> 

<span data-ttu-id="062ed-364">**Значок** ![Значок входа в ISR](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="062ed-365">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-365">**Description**</span></span>

<span data-ttu-id="062ed-366">Это событие представляет вход в подпрограмму обработки прерываний (ISR) в приложении.</span><span class="sxs-lookup"><span data-stu-id="062ed-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="062ed-367">Выполнение подпрограммы обработки прерываний продолжается до наступления события выхода из ISR.</span><span class="sxs-lookup"><span data-stu-id="062ed-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="062ed-368">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-368">**Information Fields**</span></span>

- <span data-ttu-id="062ed-369">Поле сведений 1. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="062ed-370">Поле сведений 2. Определяемый приложением номер ISR (необязательно).</span><span class="sxs-lookup"><span data-stu-id="062ed-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="062ed-371">Поле сведений 3. Число вложенных прерываний.</span><span class="sxs-lookup"><span data-stu-id="062ed-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="062ed-372">Поле сведений 4. Флаг отключения внутреннего вытеснения.</span><span class="sxs-lookup"><span data-stu-id="062ed-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="062ed-373">Выход из подпрограммы обработки прерываний (ISR)</span><span class="sxs-lookup"><span data-stu-id="062ed-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="062ed-374">Выход из ISR</span><span class="sxs-lookup"><span data-stu-id="062ed-374">Exit ISR</span></span>

<span data-ttu-id="062ed-375">**Значок** ![Значок выхода из ISR](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="062ed-376">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-376">**Description**</span></span>

<span data-ttu-id="062ed-377">Это событие представляет выход из подпрограммы обработки прерываний (ISR) в приложении.</span><span class="sxs-lookup"><span data-stu-id="062ed-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="062ed-378">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-378">**Information Fields**</span></span>

- <span data-ttu-id="062ed-379">Поле сведений 1. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="062ed-380">Поле сведений 2. Определяемый приложением номер ISR (необязательно).</span><span class="sxs-lookup"><span data-stu-id="062ed-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="062ed-381">Поле сведений 3. Число вложенных прерываний.</span><span class="sxs-lookup"><span data-stu-id="062ed-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="062ed-382">Поле сведений 4. Флаг отключения внутреннего вытеснения.</span><span class="sxs-lookup"><span data-stu-id="062ed-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="062ed-383">Внутренний временной срез</span><span class="sxs-lookup"><span data-stu-id="062ed-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="062ed-384">Внутренний временной срез</span><span class="sxs-lookup"><span data-stu-id="062ed-384">Internal time-slice</span></span>

<span data-ttu-id="062ed-385">**Значок** ![Значок внутреннего временного среза](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="062ed-386">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-386">**Description**</span></span>

<span data-ttu-id="062ed-387">Это событие представляет внутреннюю обработку в ThreadX, которая выполняет операцию временного среза.</span><span class="sxs-lookup"><span data-stu-id="062ed-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="062ed-388">В первое поле сведений помещается следующий поток с таким же приоритетом.</span><span class="sxs-lookup"><span data-stu-id="062ed-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="062ed-389">Если это значение такое же, как у текущего потока, временной срез не выполнен.</span><span class="sxs-lookup"><span data-stu-id="062ed-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="062ed-390">Поле сведений 1. Указатель на следующий поток для выполнения.</span><span class="sxs-lookup"><span data-stu-id="062ed-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="062ed-391">Поле сведений 2. Число вложенных прерываний.</span><span class="sxs-lookup"><span data-stu-id="062ed-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="062ed-392">Поле сведений 3. Флаг отключения внутреннего вытеснения.</span><span class="sxs-lookup"><span data-stu-id="062ed-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="062ed-393">Поле сведений 4. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="062ed-394">Запущен</span><span class="sxs-lookup"><span data-stu-id="062ed-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="062ed-395">Выполнение в контексте</span><span class="sxs-lookup"><span data-stu-id="062ed-395">Running in context</span></span>

<span data-ttu-id="062ed-396">**Значок** ![Значок выполнения](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="062ed-397">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-397">**Description**</span></span>

<span data-ttu-id="062ed-398">Это событие представляет выполнение в контексте потока или в бездействующей системе.</span><span class="sxs-lookup"><span data-stu-id="062ed-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="062ed-399">Оно используется для иллюстрации последующих изменений в контексте в результате прерывания.</span><span class="sxs-lookup"><span data-stu-id="062ed-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="062ed-400">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-400">**Information Fields**</span></span>
- <span data-ttu-id="062ed-401">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-402">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-403">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-404">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="062ed-405">Выделение блока</span><span class="sxs-lookup"><span data-stu-id="062ed-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="062ed-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="062ed-406">tx_block_allocate</span></span>

<span data-ttu-id="062ed-407">**Значок** ![Значок выделения блока](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="062ed-408">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-408">**Description**</span></span>

<span data-ttu-id="062ed-409">Это событие представляет выделение блока памяти с помощью tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="062ed-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="062ed-410">В случае успеха во втором поле сведений возвращается адрес выделенного блока.</span><span class="sxs-lookup"><span data-stu-id="062ed-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="062ed-411">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-411">**Information Fields**</span></span>
- <span data-ttu-id="062ed-412">Поле сведений 1. Указатель на соответствующий пул блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="062ed-413">Поле сведений 2. Указатель на возвращенный блок памяти (в случае успеха).</span><span class="sxs-lookup"><span data-stu-id="062ed-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="062ed-414">Поле сведений 3. Параметр wait, предоставляемый для вызова tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="062ed-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="062ed-415">Поле сведений 4. Оставшиеся доступные блоки в пуле после этого выделения.</span><span class="sxs-lookup"><span data-stu-id="062ed-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="062ed-416">Создание пула блоков</span><span class="sxs-lookup"><span data-stu-id="062ed-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="062ed-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="062ed-417">tx_block_pool_create</span></span>

<span data-ttu-id="062ed-418">**Значок** ![Значок создания пула блоков](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="062ed-419">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-419">**Description**</span></span>

<span data-ttu-id="062ed-420">Это событие представляет создание пула блоков памяти с помощью tx_block_pool_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="062ed-421">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-421">**Information Fields**</span></span>

- <span data-ttu-id="062ed-422">Поле сведений 1. Указатель на соответствующий блок управления пулом блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="062ed-423">Поле сведений 2. Указатель на начальную область памяти пула.</span><span class="sxs-lookup"><span data-stu-id="062ed-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="062ed-424">Поле сведений 3. Количество блоков в пуле.</span><span class="sxs-lookup"><span data-stu-id="062ed-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="062ed-425">Поле сведений 4. Размер каждого блока в пуле (в байтах).</span><span class="sxs-lookup"><span data-stu-id="062ed-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="062ed-426">Удаление пула блоков</span><span class="sxs-lookup"><span data-stu-id="062ed-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="062ed-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-427">tx_block_pool_delete</span></span>

<span data-ttu-id="062ed-428">**Значок** ![Значок удаления пула блоков](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="062ed-429">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-429">**Description**</span></span>

<span data-ttu-id="062ed-430">Это событие представляет удаление пула блоков памяти с помощью tx_block_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="062ed-431">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-431">**Information Fields**</span></span>

- <span data-ttu-id="062ed-432">Поле сведений 1. Указатель на блок управления пулом блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="062ed-433">Поле сведений 2. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="062ed-434">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-435">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="062ed-436">Получение сведений о пуле блоков</span><span class="sxs-lookup"><span data-stu-id="062ed-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="062ed-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="062ed-438">**Значок** ![Значок получения сведений о пуле блоков](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="062ed-439">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-439">**Description**</span></span>

<span data-ttu-id="062ed-440">Это событие представляет получение сведений о пуле блоков памяти с помощью tx_block_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="062ed-441">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-441">**Information Fields**</span></span>

- <span data-ttu-id="062ed-442">Поле сведений 1. Указатель на блок управления пулом блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="062ed-443">Поле сведений 2. Значение указателя стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="062ed-444">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-445">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="062ed-446">Получение сведений о производительности пула блоков</span><span class="sxs-lookup"><span data-stu-id="062ed-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="062ed-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="062ed-448">**Значок** ![Значок получения сведений о производительности пула блоков](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="062ed-449">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-449">**Description**</span></span>

<span data-ttu-id="062ed-450">Это событие представляет получение сведений о производительности пула блоков памяти с помощью tx_block_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="062ed-451">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-451">**Information Fields**</span></span>

- <span data-ttu-id="062ed-452">Поле сведений 1. Указатель на блок управления пулом блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="062ed-453">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-454">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-455">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="062ed-456">Получение системных сведений о производительности пулов блоков</span><span class="sxs-lookup"><span data-stu-id="062ed-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="062ed-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="062ed-458">**Значок** ![Значок получения системных сведений о производительности пулов блоков](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="062ed-459">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-459">**Description**</span></span>

<span data-ttu-id="062ed-460">Это событие представляет получение сведений о производительности всех пулов блоков памяти с помощью tx_block_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-461">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-461">**Information Fields**</span></span>
- <span data-ttu-id="062ed-462">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-463">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-464">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-465">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="062ed-466">Назначение приоритета пулу блоков</span><span class="sxs-lookup"><span data-stu-id="062ed-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="062ed-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="062ed-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="062ed-468">**Значок** ![Значок назначения приоритета пулу блоков](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="062ed-469">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-469">**Description**</span></span>

<span data-ttu-id="062ed-470">Это событие представляет помещение приостановленного потока с наивысшим приоритетом в начало списка приостановки пула блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="062ed-471">Если оно происходит до вызова tx_block_release, приостановленный поток с наивысшим приоритетом получит освобожденный блок.</span><span class="sxs-lookup"><span data-stu-id="062ed-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="062ed-472">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-472">**Information Fields**</span></span>
- <span data-ttu-id="062ed-473">Поле сведений 1. Указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="062ed-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="062ed-474">Поле сведений 2. Число потоков, приостановленных в этом пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="062ed-475">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="062ed-476">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="062ed-477">Освобождение блока</span><span class="sxs-lookup"><span data-stu-id="062ed-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="062ed-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="062ed-478">tx_block_release</span></span>

<span data-ttu-id="062ed-479">**Значок** ![Значок освобождения блока](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="062ed-480">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-480">**Description**</span></span>

<span data-ttu-id="062ed-481">Это событие представляет освобождение ранее выделенного блока и возврат его в пул блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="062ed-482">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-482">**Information Fields**</span></span>

- <span data-ttu-id="062ed-483">Поле сведений 1. Указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="062ed-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="062ed-484">Поле сведений 2. Указатель на блок для освобождения.</span><span class="sxs-lookup"><span data-stu-id="062ed-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="062ed-485">Поле сведений 3. Число потоков, приостановленных в этом пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="062ed-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="062ed-486">Поле сведений 4. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="062ed-487">Выделение байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="062ed-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="062ed-488">tx_byte_allocate</span></span>

<span data-ttu-id="062ed-489">**Значок** ![Значок выделения байтов](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="062ed-490">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-490">**Description**</span></span>

<span data-ttu-id="062ed-491">Это событие представляет выделение памяти с помощью tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="062ed-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="062ed-492">В случае успеха во втором поле сведений возвращается адрес выделенной памяти.</span><span class="sxs-lookup"><span data-stu-id="062ed-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="062ed-493">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-493">**Information Fields**</span></span>
- <span data-ttu-id="062ed-494">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-495">Поле сведений 2. Указатель на возвращенную память (в случае успеха).</span><span class="sxs-lookup"><span data-stu-id="062ed-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="062ed-496">Поле сведений 3. Число запрошенных байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="062ed-497">Поле сведений 4. Параметр wait, предоставляемый для вызова tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="062ed-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="062ed-498">Создание пула байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="062ed-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="062ed-499">tx_byte_pool_create</span></span>

<span data-ttu-id="062ed-500">**Значок** ![Значок создания пула байтов](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="062ed-501">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-501">**Description**</span></span>

<span data-ttu-id="062ed-502">Это событие представляет создание пула байтов с помощью tx_byte_pool_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="062ed-503">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-503">**Information Fields**</span></span>

- <span data-ttu-id="062ed-504">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-505">Поле сведений 2. Указатель на начало области памяти.</span><span class="sxs-lookup"><span data-stu-id="062ed-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="062ed-506">Поле сведений 3. Число байтов в пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="062ed-507">Поле сведений 4. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="062ed-508">Удаление пула байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="062ed-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="062ed-510">**Значок** ![Значок удаления пула байтов](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="062ed-511">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-511">**Description**</span></span>

<span data-ttu-id="062ed-512">Это событие представляет удаление пула байтов с помощью tx_byte_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="062ed-513">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-513">**Information Fields**</span></span>

- <span data-ttu-id="062ed-514">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-515">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="062ed-516">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-517">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="062ed-518">Получение сведений о пуле байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="062ed-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="062ed-520">**Значок** ![Значок получения сведений о пуле байтов](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="062ed-521">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-521">**Description**</span></span>

<span data-ttu-id="062ed-522">Это событие представляет получение сведений о пуле байтов с помощью tx_byte_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="062ed-523">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-523">**Information Fields**</span></span>

- <span data-ttu-id="062ed-524">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-525">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-526">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-527">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="062ed-528">Получение сведений о производительности пула байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="062ed-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="062ed-530">**Значок** ![Значок получения сведений о производительности пула байтов](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="062ed-531">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-531">**Description**</span></span>

<span data-ttu-id="062ed-532">Это событие представляет получение сведений о производительности пула байтов с помощью tx_byte_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="062ed-533">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-533">**Information Fields**</span></span>

- <span data-ttu-id="062ed-534">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-535">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-536">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-537">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="062ed-538">Получение системных сведений о производительности пула байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="062ed-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="062ed-540">**Значок** ![Значок получения системных сведений о производительности пула байтов](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="062ed-541">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-541">**Description**</span></span>

<span data-ttu-id="062ed-542">Это событие представляет получение системных сведений о производительности пула байтов с помощью tx_byte_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-543">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-543">**Information Fields**</span></span>

- <span data-ttu-id="062ed-544">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-545">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-546">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-547">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="062ed-548">Назначение приоритета пулу байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="062ed-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="062ed-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="062ed-550">**Значок** ![Значок назначения приоритета пулу байтов](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="062ed-551">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-551">**Description**</span></span>

<span data-ttu-id="062ed-552">Это событие представляет назначение приоритета списку приостановки пула байтов с помощью tx_byte_pool_prioritize.</span><span class="sxs-lookup"><span data-stu-id="062ed-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="062ed-553">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-553">**Information Fields**</span></span>

- <span data-ttu-id="062ed-554">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-555">Поле сведений 2. Количество потоков, приостановленных в пуле байтов в данный момент.</span><span class="sxs-lookup"><span data-stu-id="062ed-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="062ed-556">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-557">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="062ed-558">Освобождение байтов</span><span class="sxs-lookup"><span data-stu-id="062ed-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="062ed-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="062ed-559">tx_byte_release</span></span>

<span data-ttu-id="062ed-560">**Значок** ![Значок освобождения байтов](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="062ed-561">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-561">**Description**</span></span>

<span data-ttu-id="062ed-562">Это событие представляет освобождение блока памяти, выделенного из пула байтов, с помощью tx_byte_release.</span><span class="sxs-lookup"><span data-stu-id="062ed-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="062ed-563">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-563">**Information Fields**</span></span>

- <span data-ttu-id="062ed-564">Поле сведений 1. Указатель на соответствующий пул байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="062ed-565">Поле сведений 2. Указатель на ранее выделенную память в пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="062ed-566">Поле сведений 3. Число потоков, приостановленных в этом пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="062ed-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="062ed-567">Поле сведений 4. Количество доступных байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="062ed-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="062ed-568">Создание флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="062ed-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="062ed-569">tx_event_flags_create</span></span>

<span data-ttu-id="062ed-570">**Значок** ![Значок создания флагов событий](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="062ed-571">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-571">**Description**</span></span>

<span data-ttu-id="062ed-572">Это событие представляет создание новой группы флагов событий с помощью tx_event_flags_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="062ed-573">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-573">**Information Fields**</span></span> 
- <span data-ttu-id="062ed-574">Поле сведений 1. Указатель на блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="062ed-575">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-576">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-577">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="062ed-578">Удаление флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="062ed-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-579">tx_event_flags_delete</span></span>

<span data-ttu-id="062ed-580">**Значок** ![Значок удаления флагов событий](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="062ed-581">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-581">**Description**</span></span>

<span data-ttu-id="062ed-582">Это событие представляет удаление группы флагов событий с помощью tx_event_flags_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="062ed-583">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-583">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-584">Поле сведений 1. Указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="062ed-585">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-586">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-587">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="062ed-588">Получение флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="062ed-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="062ed-589">tx_event_flags_get</span></span>

<span data-ttu-id="062ed-590">**Значок** ![Значок получения флагов событий](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="062ed-591">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-591">**Description**</span></span>

<span data-ttu-id="062ed-592">Это событие представляет получение флагов событий из существующей группы флагов событий с помощью tx_event_flags_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="062ed-593">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-593">**Information Fields**</span></span>

- <span data-ttu-id="062ed-594">Поле сведений 1. Указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="062ed-595">Поле сведений 2. Запрошены флаги событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="062ed-596">Поле сведений 3. Флаги событий, установленные в данный момент в группе.</span><span class="sxs-lookup"><span data-stu-id="062ed-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="062ed-597">Поле сведений 4. Параметр, запрошенный при получении флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="062ed-598">Получение сведений о флагах событий</span><span class="sxs-lookup"><span data-stu-id="062ed-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="062ed-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="062ed-600">**Значок** ![Значок получения сведений о флагах событий](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="062ed-601">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-601">**Description**</span></span>

<span data-ttu-id="062ed-602">Это событие представляет получение сведений об имеющейся группе флагов событий с помощью tx_event_flags_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="062ed-603">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-603">**Information Fields**</span></span>

- <span data-ttu-id="062ed-604">Поле сведений 1. Указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="062ed-605">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-606">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-607">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="062ed-608">Получение сведений о производительности флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="062ed-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="062ed-610">**Значок** ![Значок получения сведений о производительности флагов событий](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="062ed-611">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-611">**Description**</span></span>

<span data-ttu-id="062ed-612">Это событие представляет получение сведений о производительности для имеющейся группы флагов событий с помощью tx_event_flags_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="062ed-613">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-613">**Information Fields**</span></span> 
- <span data-ttu-id="062ed-614">Поле сведений 1. Указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="062ed-615">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="062ed-616">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="062ed-617">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="062ed-618">Получение системных сведений о производительности флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="062ed-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="062ed-620">**Значок** ![Значок получения системных сведений о производительности флагов событий](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="062ed-621">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-621">**Description**</span></span>

<span data-ttu-id="062ed-622">Это событие представляет получение сведений о производительности для имеющейся группы флагов событий с помощью tx_event_flags_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-623">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-623">**Information Fields**</span></span>
- <span data-ttu-id="062ed-624">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-625">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-626">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-627">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="062ed-628">Установка флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="062ed-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="062ed-629">tx_event_flags_set</span></span>

<span data-ttu-id="062ed-630">**Значок** ![Значок установки флагов событий](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="062ed-631">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-631">**Description**</span></span>

<span data-ttu-id="062ed-632">Это событие представляет установку (или снятие) флагов событий в имеющейся группе флагов событий с помощью tx_event_flags_set.</span><span class="sxs-lookup"><span data-stu-id="062ed-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="062ed-633">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-633">**Information Fields**</span></span>

- <span data-ttu-id="062ed-634">Поле сведений 1. Указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="062ed-635">Поле сведений 2. Флаги событий, которые необходимо установить (или снять).</span><span class="sxs-lookup"><span data-stu-id="062ed-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="062ed-636">Поле сведений 3. Параметр флага события "И" или "ИЛИ".</span><span class="sxs-lookup"><span data-stu-id="062ed-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="062ed-637">Поле сведений 4. Число потоков, приостановленных для этой группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="062ed-638">Уведомление об установке флагов событий</span><span class="sxs-lookup"><span data-stu-id="062ed-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="062ed-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="062ed-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="062ed-640">**Значок** ![Значок уведомления об установке флагов событий](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="062ed-641">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-641">**Description**</span></span>

<span data-ttu-id="062ed-642">Это событие представляет регистрацию обратного вызова уведомления для любой операции установки флага события в имеющейся группе флагов событий с помощью tx_event_flags_set_notify.</span><span class="sxs-lookup"><span data-stu-id="062ed-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="062ed-643">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-643">**Information Fields**</span></span>

- <span data-ttu-id="062ed-644">Поле сведений 1. Указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="062ed-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="062ed-645">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-646">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-647">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="062ed-648">Управление прерываниями</span><span class="sxs-lookup"><span data-stu-id="062ed-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="062ed-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="062ed-649">tx_interrupt_control</span></span>

<span data-ttu-id="062ed-650">**Значок** ![Значок управления прерываниями](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="062ed-651">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-651">**Description**</span></span>

<span data-ttu-id="062ed-652">Это событие представляет изменение позиции блокировки прерывания работы процессора с помощью tx_interrupt_control.</span><span class="sxs-lookup"><span data-stu-id="062ed-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="062ed-653">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-653">**Information Fields**</span></span>

- <span data-ttu-id="062ed-654">Поле сведений 1. Новое положение прерывания.</span><span class="sxs-lookup"><span data-stu-id="062ed-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="062ed-655">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-656">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-657">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="062ed-658">Создание мьютекса</span><span class="sxs-lookup"><span data-stu-id="062ed-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="062ed-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="062ed-659">tx_mutex_create</span></span>

<span data-ttu-id="062ed-660">**Значок** ![Значок создания мьютекса](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="062ed-661">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-661">**Description**</span></span>

<span data-ttu-id="062ed-662">Это событие представляет создание мьютекса с помощью tx_mutex_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="062ed-663">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-663">**Information Fields**</span></span>

- <span data-ttu-id="062ed-664">Поле сведений 1. Указатель на блок управления мьютексом.</span><span class="sxs-lookup"><span data-stu-id="062ed-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="062ed-665">Поле сведений 2. Параметр наследования приоритета</span><span class="sxs-lookup"><span data-stu-id="062ed-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="062ed-666">(TX_INHERIT или TX_NO_INHERIT).</span><span class="sxs-lookup"><span data-stu-id="062ed-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="062ed-667">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-668">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="062ed-669">Удаление мьютекса</span><span class="sxs-lookup"><span data-stu-id="062ed-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="062ed-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-670">tx_mutex_delete</span></span>

<span data-ttu-id="062ed-671">**Значок** ![Значок удаления мьютекса](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="062ed-672">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-672">**Description**</span></span>

<span data-ttu-id="062ed-673">Это событие представляет удаление мьютекса с помощью tx_mutex_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="062ed-674">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-674">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-675">Поле сведений 1. Указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="062ed-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="062ed-676">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-677">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-678">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="062ed-679">Выполнение операции Get с мьютексом</span><span class="sxs-lookup"><span data-stu-id="062ed-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="062ed-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="062ed-680">tx_mutex_get</span></span>

<span data-ttu-id="062ed-681">**Значок** ![Значок выполнения операции Get с мьютексом](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="062ed-682">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-682">**Description**</span></span>

<span data-ttu-id="062ed-683">Это событие представляет получение мьютекса с помощью tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="062ed-684">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-684">**Information Fields**</span></span>

- <span data-ttu-id="062ed-685">Поле сведений 1. Указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="062ed-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="062ed-686">Поле сведений 2. Параметр wait, предоставляемый для вызова tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="062ed-687">Поле сведений 3. Указатель на поток, владеющий мьютексом (NULL означает, что мьютекс не принадлежит потоку).</span><span class="sxs-lookup"><span data-stu-id="062ed-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="062ed-688">Информационное поле 4. Количество раз, когда владеющий поток вызвал tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="062ed-689">Получение сведений о мьютексе</span><span class="sxs-lookup"><span data-stu-id="062ed-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="062ed-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-690">tx_mutex_info_get</span></span>

<span data-ttu-id="062ed-691">**Значок** ![Значок получения сведений о мьютексе](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="062ed-692">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-692">**Description**</span></span>

<span data-ttu-id="062ed-693">Это событие представляет получение сведений о мьютексе с помощью tx_mutex_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="062ed-694">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-694">**Information Fields**</span></span>

- <span data-ttu-id="062ed-695">Поле сведений 1. Указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="062ed-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="062ed-696">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-697">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-698">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="062ed-699">Получение сведений о производительности мьютекса</span><span class="sxs-lookup"><span data-stu-id="062ed-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="062ed-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="062ed-701">**Значок** ![Значок получения сведений о производительности мьютекса](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="062ed-702">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-702">**Description**</span></span>

<span data-ttu-id="062ed-703">Это событие представляет получение сведений о производительности мьютексов с помощью tx_mutex_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="062ed-704">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-704">**Information Fields**</span></span>

- <span data-ttu-id="062ed-705">Поле сведений 1. Указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="062ed-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="062ed-706">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-707">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-708">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="062ed-709">Получение системных сведений о производительности мьютекса</span><span class="sxs-lookup"><span data-stu-id="062ed-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="062ed-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="062ed-711">**Значок** ![Значок получения системных сведений о производительности мьютекса](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="062ed-712">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-712">**Description**</span></span>

<span data-ttu-id="062ed-713">Это событие представляет получение системных сведений о производительности мьютексов с помощью tx_mutex_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-714">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-714">**Information Fields**</span></span>

- <span data-ttu-id="062ed-715">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-716">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-717">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-718">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="062ed-719">Назначение приоритета мьютекса</span><span class="sxs-lookup"><span data-stu-id="062ed-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="062ed-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="062ed-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="062ed-721">**Значок** ![Значок назначения приоритета мьютекса](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="062ed-722">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-722">**Description**</span></span>

<span data-ttu-id="062ed-723">Это событие представляет назначение приоритета списка приостановки мьютекса с помощью tx_mutex_prioritize.</span><span class="sxs-lookup"><span data-stu-id="062ed-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="062ed-724">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-724">**Information Fields**</span></span>

- <span data-ttu-id="062ed-725">Поле сведений 1. Указатель на соответствующий мьютекс.</span><span class="sxs-lookup"><span data-stu-id="062ed-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="062ed-726">Поле сведений 2. Количество потоков, приостановленных для мьютекса в данный момент.</span><span class="sxs-lookup"><span data-stu-id="062ed-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="062ed-727">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-728">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="062ed-729">Выполнение операции Put с мьютексом</span><span class="sxs-lookup"><span data-stu-id="062ed-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="062ed-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="062ed-730">tx_mutex_put</span></span>

<span data-ttu-id="062ed-731">**Значок** ![Значок выполнения операции Put с мьютексом](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="062ed-732">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-732">**Description**</span></span>

<span data-ttu-id="062ed-733">Это событие представляет освобождение мьютекса, ранее принадлежащего потоку, с помощью tx_mutex_put.</span><span class="sxs-lookup"><span data-stu-id="062ed-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="062ed-734">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-734">**Information Fields**</span></span>

- <span data-ttu-id="062ed-735">Поле сведений 1. Указатель на соответствующий мьютекс.</span><span class="sxs-lookup"><span data-stu-id="062ed-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="062ed-736">Поле сведений 2. Указатель на поток, владеющий мьютексом.</span><span class="sxs-lookup"><span data-stu-id="062ed-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="062ed-737">Поле сведений 3. Количество необработанных запросов на выполнение операции Get с мьютексом.</span><span class="sxs-lookup"><span data-stu-id="062ed-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="062ed-738">Поле сведений 4. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="062ed-739">Создание очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="062ed-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="062ed-740">tx_queue_create</span></span>

<span data-ttu-id="062ed-741">**Значок** ![Значок создания очереди](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="062ed-742">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-742">**Description**</span></span>

<span data-ttu-id="062ed-743">Это событие представляет создание очереди сообщений с помощью tx_queue_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="062ed-744">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-744">**Information Fields**</span></span>

- <span data-ttu-id="062ed-745">Поле сведений 1. Указатель на блок управления очередями.</span><span class="sxs-lookup"><span data-stu-id="062ed-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="062ed-746">Поле сведений 2. Размер сообщения (измеряемый в 32-разрядных словах).</span><span class="sxs-lookup"><span data-stu-id="062ed-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="062ed-747">Поле сведений 3. Указатель на начало области памяти очереди.</span><span class="sxs-lookup"><span data-stu-id="062ed-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="062ed-748">Поле сведений 4. Число байтов в области памяти очереди.</span><span class="sxs-lookup"><span data-stu-id="062ed-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="062ed-749">Удаление очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="062ed-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-750">tx_queue_delete</span></span>

<span data-ttu-id="062ed-751">**Значок** ![Значок удаления очереди](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="062ed-752">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-752">**Description**</span></span>

<span data-ttu-id="062ed-753">Это событие представляет удаление очереди с помощью tx_queue_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="062ed-754">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-754">**Information Fields**</span></span>

- <span data-ttu-id="062ed-755">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-756">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-757">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-758">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="062ed-759">Освобождение очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="062ed-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="062ed-760">tx_queue_flush</span></span>

<span data-ttu-id="062ed-761">**Значок** ![Значок освобождения очереди](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="062ed-762">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-762">**Description**</span></span>

<span data-ttu-id="062ed-763">Это событие представляет освобождение (очистку всего содержимого) очереди с помощью tx_queue_flush.</span><span class="sxs-lookup"><span data-stu-id="062ed-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="062ed-764">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-764">**Information Fields**</span></span>

- <span data-ttu-id="062ed-765">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-766">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-767">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-768">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="062ed-769">Отправка сообщения в начало очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="062ed-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="062ed-770">tx_queue_front_send</span></span>

<span data-ttu-id="062ed-771">**Значок** ![Значок отправки сообщения в начало очереди](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="062ed-772">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-772">**Description**</span></span>

<span data-ttu-id="062ed-773">Это событие представляет отправку сообщения в начало очереди с помощью tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="062ed-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="062ed-774">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-774">**Information Fields**</span></span>

- <span data-ttu-id="062ed-775">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-776">Поле сведений 2. Указатель на начало сообщения.</span><span class="sxs-lookup"><span data-stu-id="062ed-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="062ed-777">Поле сведений 3. Параметр wait, указанный для</span><span class="sxs-lookup"><span data-stu-id="062ed-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="062ed-778">вызова tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="062ed-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="062ed-779">Поле сведений 4. Количество сообщений, уже поставленных в очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="062ed-780">Получение сведений об очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="062ed-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-781">tx_queue_info_get</span></span>

<span data-ttu-id="062ed-782">**Значок** ![Значок получения сведений об очереди](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="062ed-783">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-783">**Description**</span></span>

<span data-ttu-id="062ed-784">Это событие представляет получение сведений об очереди с помощью tx_queue_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="062ed-785">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-785">**Information Fields**</span></span> 
- <span data-ttu-id="062ed-786">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-787">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-788">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-789">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="062ed-790">Получение сведений о производительности очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="062ed-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="062ed-792">**Значок** ![Значок получения сведений о производительности очереди](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="062ed-793">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-793">**Description**</span></span>

<span data-ttu-id="062ed-794">Это событие представляет получение сведений о производительности очереди с помощью tx_queue_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="062ed-795">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-795">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-796">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-797">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-798">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-799">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="062ed-800">Получение системных сведений о производительности очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="062ed-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="062ed-802">**Значок** ![Значок получения системных сведений о производительности очереди](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="062ed-803">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-803">**Description**</span></span>

<span data-ttu-id="062ed-804">Это событие представляет получение системных сведений о производительности для всех очередей в системе.</span><span class="sxs-lookup"><span data-stu-id="062ed-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="062ed-805">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-805">**Information Fields**</span></span>

- <span data-ttu-id="062ed-806">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-807">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-808">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-809">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="062ed-810">Назначение приоритета очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="062ed-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="062ed-811">tx_queue_prioritize</span></span>

<span data-ttu-id="062ed-812">**Значок** ![Значок назначения приоритета очереди](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="062ed-813">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-813">**Description**</span></span>

<span data-ttu-id="062ed-814">Это событие представляет назначение приоритета списка приостановки очереди с помощью tx_queue_prioritize.</span><span class="sxs-lookup"><span data-stu-id="062ed-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="062ed-815">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-815">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-816">Поле сведений 1. Указатель на соответствующую очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="062ed-817">Поле сведений 2. Количество потоков, приостановленных для очереди в данный момент.</span><span class="sxs-lookup"><span data-stu-id="062ed-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="062ed-818">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-819">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="062ed-820">Получение очереди</span><span class="sxs-lookup"><span data-stu-id="062ed-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="062ed-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="062ed-821">tx_queue_receive</span></span>

<span data-ttu-id="062ed-822">**Значок** ![Значок получения очереди](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="062ed-823">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-823">**Description**</span></span>

<span data-ttu-id="062ed-824">Это событие представляет получение сообщения из очереди с помощью tx_queue_receive.</span><span class="sxs-lookup"><span data-stu-id="062ed-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="062ed-825">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-825">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-826">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-827">Поле сведений 2. Указатель на пункт назначения для сообщения.</span><span class="sxs-lookup"><span data-stu-id="062ed-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="062ed-828">Поле сведений 3. Параметр wait, указанный для вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="062ed-829">Поле сведений 4. Количество сообщений, находящихся в очереди в данный момент.</span><span class="sxs-lookup"><span data-stu-id="062ed-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="062ed-830">Отправка в очередь</span><span class="sxs-lookup"><span data-stu-id="062ed-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="062ed-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="062ed-831">tx_queue_send</span></span>

<span data-ttu-id="062ed-832">**Значок** ![Значок отправки в очередь](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="062ed-833">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-833">**Description**</span></span>

<span data-ttu-id="062ed-834">Это событие представляет отправку сообщения в очередь с помощью tx_queue_send.</span><span class="sxs-lookup"><span data-stu-id="062ed-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="062ed-835">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-835">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-836">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-837">Поле сведений 2. Указатель на сообщение.</span><span class="sxs-lookup"><span data-stu-id="062ed-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="062ed-838">Поле сведений 3. Параметр wait, указанный для вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="062ed-839">Поле сведений 4. Количество сообщений, находящихся в очереди в данный момент.</span><span class="sxs-lookup"><span data-stu-id="062ed-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="062ed-840">Уведомление об отправке в очередь</span><span class="sxs-lookup"><span data-stu-id="062ed-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="062ed-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="062ed-841">tx_queue_send_notify</span></span>

<span data-ttu-id="062ed-842">**Значок** ![Значок уведомления об отправке в очередь](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="062ed-843">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-843">**Description**</span></span>

<p><span data-ttu-id="062ed-844">Это событие представляет регистрацию обратного вызова с помощью tx_queue_send_notify, который вызывается при каждой отправке сообщения в очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="062ed-845">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-845">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-846">Поле сведений 1. Указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="062ed-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="062ed-847">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-848">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-849">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="062ed-850">Помещение в семафор с верхним пределом</span><span class="sxs-lookup"><span data-stu-id="062ed-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="062ed-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="062ed-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="062ed-852">**Значок** ![Значок помещения в семафор с верхним пределом](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="062ed-853">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-853">**Description**</span></span>

<span data-ttu-id="062ed-854">Это событие представляет помещение в семафор с помощью tx_semaphore_ceiling_put.</span><span class="sxs-lookup"><span data-stu-id="062ed-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="062ed-855">Эта служба отличается от службы tx_semaphore_put тем, что в ней проверяется максимальное значение семафора, так как операции помещения в семафор запрещено превышать максимальное значение (верхний предел).</span><span class="sxs-lookup"><span data-stu-id="062ed-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="062ed-856">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-856">**Information Fields**</span></span>

- <span data-ttu-id="062ed-857">Поле сведений 1. Указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="062ed-858">Поле сведений 2. Текущее значение счетчика семафора.</span><span class="sxs-lookup"><span data-stu-id="062ed-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="062ed-859">Поле сведений 3. Число потоков, приостановленных для этого семафора.</span><span class="sxs-lookup"><span data-stu-id="062ed-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="062ed-860">Поле сведений 4. Верхний предел, заданный для вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="062ed-861">Создание семафора</span><span class="sxs-lookup"><span data-stu-id="062ed-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="062ed-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="062ed-862">tx_semaphore_create</span></span>

<span data-ttu-id="062ed-863">**Значок** ![Значок создания семафора](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="062ed-864">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-864">**Description**</span></span>

<span data-ttu-id="062ed-865">Это событие представляет создание семафора с помощью tx_semaphore_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="062ed-866">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-866">**Information Fields**</span></span>

- <span data-ttu-id="062ed-867">Поле сведений 1. Указатель на блок управления семафором.</span><span class="sxs-lookup"><span data-stu-id="062ed-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="062ed-868">Поле сведений 2. Начальное значение счетчика семафора.</span><span class="sxs-lookup"><span data-stu-id="062ed-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="062ed-869">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-870">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="062ed-871">Удаление семафора</span><span class="sxs-lookup"><span data-stu-id="062ed-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="062ed-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-872">tx_semaphore_delete</span></span>

<span data-ttu-id="062ed-873">**Значок** ![Значок удаления семафора](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="062ed-874">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-874">**Description**</span></span>

<span data-ttu-id="062ed-875">Это событие представляет удаление семафора с помощью tx_semaphore_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="062ed-876">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-876">**Information Fields**</span></span>

- <span data-ttu-id="062ed-877">Поле сведений 1. Указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="062ed-878">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-879">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-880">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="062ed-881">Выполнение операции Get с семафором</span><span class="sxs-lookup"><span data-stu-id="062ed-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="062ed-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="062ed-882">tx_semaphore_get</span></span>

<span data-ttu-id="062ed-883">**Значок** ![](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="062ed-884">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-884">**Description**</span></span>

<span data-ttu-id="062ed-885">Это событие представляет получение семафора с помощью tx_semaphore_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="062ed-886">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-886">**Information Fields**</span></span>

- <span data-ttu-id="062ed-887">Поле сведений 1. Указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="062ed-888">Поле сведений 2. Параметр wait, указанный для вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="062ed-889">Поле сведений 3. Текущее значение счетчика семафора.</span><span class="sxs-lookup"><span data-stu-id="062ed-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="062ed-890">Поле сведений 4. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="062ed-891">Получение сведений о семафоре</span><span class="sxs-lookup"><span data-stu-id="062ed-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="062ed-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="062ed-893">**Значок** ![Значок получения сведений о семафоре](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="062ed-894">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-894">**Description**</span></span>

<span data-ttu-id="062ed-895">Это событие представляет получение сведений о семафоре с помощью tx_semaphore_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="062ed-896">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-896">**Information Fields**</span></span>

- <span data-ttu-id="062ed-897">Поле сведений 1. Указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="062ed-898">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-899">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-900">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="062ed-901">Получение сведений о производительности семафора</span><span class="sxs-lookup"><span data-stu-id="062ed-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="062ed-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="062ed-903">**Значок** ![Значок получения сведений о производительности семафора](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="062ed-904">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-904">**Description**</span></span>

<span data-ttu-id="062ed-905">Это событие представляет получение сведений о производительности семафора с помощью tx_semaphore_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="062ed-906">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-906">**Information Fields**</span></span>

- <span data-ttu-id="062ed-907">Поле сведений 1. Указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="062ed-908">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-909">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-910">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="062ed-911">Системные сведения о производительности семафора</span><span class="sxs-lookup"><span data-stu-id="062ed-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="062ed-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="062ed-913">**Значок** ![Значок системных сведений о производительности семафора](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="062ed-914">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-914">**Description**</span></span>

<span data-ttu-id="062ed-915">Это событие представляет получение сведений о производительности всех семафоров в системе с помощью tx_semaphore_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-916">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-916">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-917">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-918">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-919">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-920">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="062ed-921">Назначение приоритета семафора</span><span class="sxs-lookup"><span data-stu-id="062ed-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="062ed-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="062ed-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="062ed-923">**Значок** ![Значок назначения приоритета семафора](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="062ed-924">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-924">**Description**</span></span>

<span data-ttu-id="062ed-925">Это событие представляет приоритет списка приостановки семафора с помощью tx_semaphore_prioritize.</span><span class="sxs-lookup"><span data-stu-id="062ed-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="062ed-926">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-926">**Information Fields**</span></span>

- <span data-ttu-id="062ed-927">Поле сведений 1. Указатель на соответствующий семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="062ed-928">Поле сведений 2. Количество потоков, приостановленных для семафора в данный момент.</span><span class="sxs-lookup"><span data-stu-id="062ed-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="062ed-929">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-930">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="062ed-931">Операция Put с семафором</span><span class="sxs-lookup"><span data-stu-id="062ed-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="062ed-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="062ed-932">tx_semaphore_put</span></span>

<span data-ttu-id="062ed-933">**Значок** ![Значок выполнения операции Put с семафором](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="062ed-934">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-934">**Description**</span></span>

<span data-ttu-id="062ed-935">Это событие представляет освобождение экземпляра семафора с помощью tx_semaphore_put.</span><span class="sxs-lookup"><span data-stu-id="062ed-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="062ed-936">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-936">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-937">Поле сведений 1. Указатель на соответствующий семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="062ed-938">Поле сведений 2. Текущее значение счетчика семафора.</span><span class="sxs-lookup"><span data-stu-id="062ed-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="062ed-939">Поле сведений 3. Число потоков, приостановленных для этого семафора.</span><span class="sxs-lookup"><span data-stu-id="062ed-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="062ed-940">Поле сведений 4. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="062ed-941">Уведомление об операции Put с семафором</span><span class="sxs-lookup"><span data-stu-id="062ed-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="062ed-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="062ed-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="062ed-943">**Значок** ![Значок уведомления об операции Put с семафором](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="062ed-944">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-944">**Description**</span></span>

<span data-ttu-id="062ed-945">Это событие представляет регистрацию обратного вызова с помощью tx_semaphore_put_notify, вызываемого при каждом выполнении операции Put с семафором.</span><span class="sxs-lookup"><span data-stu-id="062ed-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="062ed-946">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-946">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-947">Поле сведений 1. Указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="062ed-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="062ed-948">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-949">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-950">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="062ed-951">Создание потока</span><span class="sxs-lookup"><span data-stu-id="062ed-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="062ed-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="062ed-952">tx_thread_create</span></span>

<span data-ttu-id="062ed-953">**Значок** ![Значок создания потока](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="062ed-954">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-954">**Description**</span></span>

<span data-ttu-id="062ed-955">Это событие представляет создание потока с помощью tx_thread_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="062ed-956">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-956">**Information Fields**</span></span>

- <span data-ttu-id="062ed-957">Поле сведений 1. Указатель на блок управления потока.</span><span class="sxs-lookup"><span data-stu-id="062ed-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="062ed-958">Поле сведений 2. Приоритет потока.</span><span class="sxs-lookup"><span data-stu-id="062ed-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="062ed-959">Поле сведений 3. Указатель стека для потока.</span><span class="sxs-lookup"><span data-stu-id="062ed-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="062ed-960">Поле сведений 4. Размер стека в байтах.</span><span class="sxs-lookup"><span data-stu-id="062ed-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="062ed-961">Удаление потока</span><span class="sxs-lookup"><span data-stu-id="062ed-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="062ed-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-962">tx_thread_delete</span></span>

<span data-ttu-id="062ed-963">**Значок** ![Значок удаления потока](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="062ed-964">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-964">**Description**</span></span>

<span data-ttu-id="062ed-965">Это событие представляет удаление потока с помощью tx_thread_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="062ed-966">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-966">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-967">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-968">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-969">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-970">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="062ed-971">Уведомление о входе из потока и выходе в него</span><span class="sxs-lookup"><span data-stu-id="062ed-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="062ed-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="062ed-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="062ed-973">**Значок** ![Значок уведомления о входе в поток и выходе из него](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="062ed-974">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-974">**Description**</span></span>

<span data-ttu-id="062ed-975">Это событие представляет регистрацию обратного вызова с помощью службы tx_thread_entry_exit_notify, вызываемой при каждом входе в поток или выходе из него.</span><span class="sxs-lookup"><span data-stu-id="062ed-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="062ed-976">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-976">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-977">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-978">Поле сведений 2. Состояние потока во время регистрации.</span><span class="sxs-lookup"><span data-stu-id="062ed-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="062ed-979">Поле сведений 3. Указатель на стек во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="062ed-980">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="062ed-981">Идентификатор потока</span><span class="sxs-lookup"><span data-stu-id="062ed-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="062ed-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="062ed-982">tx_thread_identify</span></span>

<span data-ttu-id="062ed-983">**Значок** ![Значок определения потока](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="062ed-984">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-984">**Description**</span></span>

<span data-ttu-id="062ed-985">Это событие представляет получение текущего указателя потока с помощью tx_thread_identify.</span><span class="sxs-lookup"><span data-stu-id="062ed-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="062ed-986">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-986">**Information Fields**</span></span>

- <span data-ttu-id="062ed-987">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-988">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-989">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-990">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="062ed-991">Получение сведений о потоке</span><span class="sxs-lookup"><span data-stu-id="062ed-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="062ed-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-992">tx_thread_info_get</span></span>

<span data-ttu-id="062ed-993">**Значок** ![Значок получения сведений о потоке](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="062ed-994">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-994">**Description**</span></span>

<span data-ttu-id="062ed-995">Это событие представляет получение сведений об указанном потоке с помощью tx_thread_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="062ed-996">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-996">**Information Fields**</span></span>

- <span data-ttu-id="062ed-997">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-998">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="062ed-999">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1000">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="062ed-1001">Получение сведений о производительности потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="062ed-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="062ed-1003">**Значок** ![Значок получения сведений о производительности потока](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="062ed-1004">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1004">**Description**</span></span>

<span data-ttu-id="062ed-1005">Это событие представляет получение сведений о производительности указанного потока с помощью tx_thread_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="062ed-1006">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1006">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1007">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1008">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="062ed-1009">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1010">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="062ed-1011">Получение системных сведений о производительности потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="062ed-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="062ed-1013">**Значок** ![Значок получения системных сведений о производительности потока](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="062ed-1014">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1014">**Description**</span></span>

<span data-ttu-id="062ed-1015">Это событие представляет получение сведений о производительности всех потоков с помощью tx_thread_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-1016">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1016">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-1017">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-1018">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1019">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1020">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="062ed-1021">Изменение вытеснения потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="062ed-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="062ed-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="062ed-1023">**Значок** ![Значок изменения вытеснения потока](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="062ed-1024">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1024">**Description**</span></span>

<span data-ttu-id="062ed-1025">Это событие представляет изменение порогового значения для вытеснения потока с помощью tx_thread_preemption_change.</span><span class="sxs-lookup"><span data-stu-id="062ed-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="062ed-1026">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1026">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-1027">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1028">Поле сведений 2. Новое пороговое значение вытеснения.</span><span class="sxs-lookup"><span data-stu-id="062ed-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="062ed-1029">Поле сведений 3. Предыдущее пороговое значение вытеснения.</span><span class="sxs-lookup"><span data-stu-id="062ed-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="062ed-1030">Поле сведений 4. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="062ed-1031">Изменение приоритета потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="062ed-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="062ed-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="062ed-1033">**Значок** ![Значок изменения приоритета потока](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="062ed-1034">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1034">**Description**</span></span>

<span data-ttu-id="062ed-1035">Это событие представляет изменение приоритета потока с помощью tx_thread_priority_change.</span><span class="sxs-lookup"><span data-stu-id="062ed-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="062ed-1036">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="062ed-1036">Information Fields</span></span> 
- <span data-ttu-id="062ed-1037">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1038">Поле сведений 2. Новый приоритет.</span><span class="sxs-lookup"><span data-stu-id="062ed-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="062ed-1039">Поле сведений 3. Предыдущий приоритет.</span><span class="sxs-lookup"><span data-stu-id="062ed-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="062ed-1040">Поле сведений 4. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="062ed-1041">Освобождение потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="062ed-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="062ed-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="062ed-1043">**Значок** ![Значок освобождения потока](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="062ed-1044">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1044">**Description**</span></span>

<span data-ttu-id="062ed-1045">Это событие представляет освобождение процессора от потока с помощью tx_thread_relinquish.</span><span class="sxs-lookup"><span data-stu-id="062ed-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="062ed-1046">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1046">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1047">Поле сведений 1. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1048">Поле сведений 2. Указатель на следующий поток для выполнения.</span><span class="sxs-lookup"><span data-stu-id="062ed-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="062ed-1049">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1050">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="062ed-1051">Сброс потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="062ed-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="062ed-1052">tx_thread_reset</span></span>

<span data-ttu-id="062ed-1053">**Значок** ![Значок сброса потока](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="062ed-1054">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1054">**Description**</span></span>

<span data-ttu-id="062ed-1055">Это событие представляет сброс выполненного или завершенного потока с помощью tx_thread_reset.</span><span class="sxs-lookup"><span data-stu-id="062ed-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="062ed-1056">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1056">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1057">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1058">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="062ed-1059">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1060">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="062ed-1061">Возобновление потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="062ed-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="062ed-1062">tx_thread_resume</span></span>

<span data-ttu-id="062ed-1063">**Значок** ![Значок возобновления потока](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="062ed-1064">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1064">**Description**</span></span>

<span data-ttu-id="062ed-1065">Это событие представляет возобновление приостановленного потока с помощью tx_thread_resume.</span><span class="sxs-lookup"><span data-stu-id="062ed-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="062ed-1066">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1066">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1067">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1068">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="062ed-1069">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1070">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="062ed-1071">Переход потока в спящий режим</span><span class="sxs-lookup"><span data-stu-id="062ed-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="062ed-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="062ed-1072">tx_thread_sleep</span></span>

<span data-ttu-id="062ed-1073">**Значок** ![Значок перехода потока в спящий режим](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="062ed-1074">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1074">**Description**</span></span>

<span data-ttu-id="062ed-1075">Это событие представляет приостановку текущего потока для указанного числа тактов таймера с помощью tx_thread_sleep.</span><span class="sxs-lookup"><span data-stu-id="062ed-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="062ed-1076">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1076">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1077">Поле сведений 1. Количество тактов для приостановки.</span><span class="sxs-lookup"><span data-stu-id="062ed-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="062ed-1078">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="062ed-1079">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1080">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="062ed-1081">Уведомление об ошибке стека потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="062ed-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="062ed-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="062ed-1083">**Значок** ![Значок уведомления об ошибке стека потока](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="062ed-1084">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1084">**Description**</span></span>

<span data-ttu-id="062ed-1085">Это событие представляет регистрацию подпрограммы уведомления об ошибках стека потока с помощью tx_thread_stack_error_notify_event.</span><span class="sxs-lookup"><span data-stu-id="062ed-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="062ed-1086">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1086">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-1087">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-1088">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1089">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1090">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="062ed-1091">Приостановка потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="062ed-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="062ed-1092">tx_thread_suspend</span></span>

<span data-ttu-id="062ed-1093">**Значок** ![Значок приостановки потока](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="062ed-1094">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1094">**Description**</span></span>

<span data-ttu-id="062ed-1095">Это событие представляет приостановку потока с помощью tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="062ed-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="062ed-1096">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1096">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-1097">Поле сведений 1. Указатель на приостанавливаемый поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="062ed-1098">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="062ed-1099">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1100">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="062ed-1101">Завершение потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="062ed-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="062ed-1102">tx_thread_terminate</span></span>

<span data-ttu-id="062ed-1103">**Значок** ![Значок завершения потока](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="062ed-1104">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1104">**Description**</span></span>

<span data-ttu-id="062ed-1105">Это событие представляет завершение потока с помощью tx_thread_terminate.</span><span class="sxs-lookup"><span data-stu-id="062ed-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="062ed-1106">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1106">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-1107">Поле сведений 1. Указатель на завершаемый поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="062ed-1108">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="062ed-1109">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1110">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="062ed-1111">Изменение временного среза потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="062ed-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="062ed-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="062ed-1113">**Значок** ![Значок изменения временного среза потока](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="062ed-1114">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1114">**Description**</span></span>

<span data-ttu-id="062ed-1115">Это событие представляет изменение временного среза потока с помощью tx_thread_time_slice_change.</span><span class="sxs-lookup"><span data-stu-id="062ed-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="062ed-1116">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1116">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1117">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1118">Поле сведений 2. Новый временной срез.</span><span class="sxs-lookup"><span data-stu-id="062ed-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="062ed-1119">Поле сведений 3. Предыдущий временной срез.</span><span class="sxs-lookup"><span data-stu-id="062ed-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="062ed-1120">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="062ed-1121">Прерывание ожидания потока</span><span class="sxs-lookup"><span data-stu-id="062ed-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="062ed-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="062ed-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="062ed-1123">**Значок** ![Значок прерывания ожидания потока](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="062ed-1124">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1124">**Description**</span></span>

<span data-ttu-id="062ed-1125">Это событие представляет прерывание приостановки потока с помощью tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="062ed-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="062ed-1126">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1126">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1127">Поле сведений 1. Указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="062ed-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="062ed-1128">Поле сведений 2. Состояние потока во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="062ed-1129">Поле сведений 3. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1130">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="062ed-1131">Получение времени</span><span class="sxs-lookup"><span data-stu-id="062ed-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="062ed-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="062ed-1132">tx_time_get</span></span>

<span data-ttu-id="062ed-1133">**Значок** ![Значок получения времени](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="062ed-1134">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1134">**Description**</span></span>

<span data-ttu-id="062ed-1135">Это событие представляет получение текущего числа тактов таймера с помощью tx_time_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="062ed-1136">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1136">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1137">Поле сведений 1. Текущее число тактов таймера.</span><span class="sxs-lookup"><span data-stu-id="062ed-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="062ed-1138">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1139">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1140">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="062ed-1141">Установка времени</span><span class="sxs-lookup"><span data-stu-id="062ed-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="062ed-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="062ed-1142">tx_time_set</span></span>

<span data-ttu-id="062ed-1143">**Значок** ![Значок установки времени](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="062ed-1144">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1144">**Description**</span></span>

<span data-ttu-id="062ed-1145">Это событие представляет установку текущего числа тактов таймера с помощью tx_time_set.</span><span class="sxs-lookup"><span data-stu-id="062ed-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="062ed-1146">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1146">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1147">Поле сведений 1. Новое число тактов таймера.</span><span class="sxs-lookup"><span data-stu-id="062ed-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="062ed-1148">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1149">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1150">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="062ed-1151">Активация таймера</span><span class="sxs-lookup"><span data-stu-id="062ed-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="062ed-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="062ed-1152">tx_timer_activate</span></span>

<span data-ttu-id="062ed-1153">**Значок** ![Значок активации таймера](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="062ed-1154">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1154">**Description**</span></span>

<span data-ttu-id="062ed-1155">Это событие представляет активацию указанного таймера с помощью tx_timer_activate.</span><span class="sxs-lookup"><span data-stu-id="062ed-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="062ed-1156">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1156">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1157">Поле сведений 1. Указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="062ed-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="062ed-1158">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1159">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1160">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="062ed-1161">Изменение таймера</span><span class="sxs-lookup"><span data-stu-id="062ed-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="062ed-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="062ed-1162">tx_timer_change</span></span>

<span data-ttu-id="062ed-1163">**Значок** ![Значок изменения таймера](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="062ed-1164">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1164">**Description**</span></span>

<span data-ttu-id="062ed-1165">Это событие представляет изменение указанного таймера с помощью tx_timer_change.</span><span class="sxs-lookup"><span data-stu-id="062ed-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="062ed-1166">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1166">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1167">Поле сведений 1. Указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="062ed-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="062ed-1168">Поле сведений 2. Начальное число тактов до истечения срока действия.</span><span class="sxs-lookup"><span data-stu-id="062ed-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="062ed-1169">Поле сведений 3. Перепланированное число тактов до истечения срока действия.</span><span class="sxs-lookup"><span data-stu-id="062ed-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="062ed-1170">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="062ed-1171">Создание таймера</span><span class="sxs-lookup"><span data-stu-id="062ed-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="062ed-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="062ed-1172">tx_timer_create</span></span>

<span data-ttu-id="062ed-1173">**Значок** ![Значок создания таймера](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="062ed-1174">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1174">**Description**</span></span>

<span data-ttu-id="062ed-1175">Это событие представляет создание таймера с помощью tx_timer_create.</span><span class="sxs-lookup"><span data-stu-id="062ed-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="062ed-1176">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1176">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1177">Поле сведений 1. Указатель на блок управления таймера.</span><span class="sxs-lookup"><span data-stu-id="062ed-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="062ed-1178">Поле сведений 2. Начальное число тактов до истечения срока действия.</span><span class="sxs-lookup"><span data-stu-id="062ed-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="062ed-1179">Поле сведений 3. Перепланированное число тактов до истечения срока действия.</span><span class="sxs-lookup"><span data-stu-id="062ed-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="062ed-1180">Поле сведений 4. Значение параметра автоматического включения: TX_AUTO_ACTIVATE (1) либо TX_NO_ACTIVATE (0).</span><span class="sxs-lookup"><span data-stu-id="062ed-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="062ed-1181">Отключение таймера</span><span class="sxs-lookup"><span data-stu-id="062ed-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="062ed-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="062ed-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="062ed-1183">**Значок** ![Значок отключения таймера](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="062ed-1184">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1184">**Description**</span></span>

<span data-ttu-id="062ed-1185">Это событие представляет отключение таймера с помощью tx_timer_deactivate.</span><span class="sxs-lookup"><span data-stu-id="062ed-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="062ed-1186">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1186">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1187">Поле сведений 1. Указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="062ed-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="062ed-1188">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1189">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1190">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="062ed-1191">Удаление таймера</span><span class="sxs-lookup"><span data-stu-id="062ed-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="062ed-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="062ed-1192">tx_timer_delete</span></span>

<span data-ttu-id="062ed-1193">**Значок** ![Значок удаления таймера](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="062ed-1194">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1194">**Description**</span></span>

<span data-ttu-id="062ed-1195">Это событие представляет удаление таймера с помощью tx_timer_delete.</span><span class="sxs-lookup"><span data-stu-id="062ed-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="062ed-1196">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1196">**Information Fields**</span></span> 

- <span data-ttu-id="062ed-1197">Поле сведений 1. Указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="062ed-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="062ed-1198">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1199">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1200">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="062ed-1201">Получение сведений о таймере</span><span class="sxs-lookup"><span data-stu-id="062ed-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="062ed-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-1202">tx_timer_info_get</span></span>

<span data-ttu-id="062ed-1203">**Значок** ![Значок получения сведений о таймере](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="062ed-1204">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1204">**Description**</span></span>

<span data-ttu-id="062ed-1205">Это событие представляет получение сведений о таймере с помощью tx_timer_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="062ed-1206">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1206">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1207">Поле сведений 1. Указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="062ed-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="062ed-1208">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1209">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1210">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="062ed-1211">Получение сведений о производительности таймера</span><span class="sxs-lookup"><span data-stu-id="062ed-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="062ed-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="062ed-1213">**Значок** ![Значок получения сведений о производительности таймера](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="062ed-1214">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1214">**Description**</span></span> 

<span data-ttu-id="062ed-1215">Это событие представляет получение сведений о производительности таймера с помощью tx_timer_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="062ed-1216">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1216">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1217">Поле сведений 1. Указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="062ed-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="062ed-1218">Поле сведений 2. Указатель стека во время вызова.</span><span class="sxs-lookup"><span data-stu-id="062ed-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="062ed-1219">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1220">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="062ed-1221">Получение сведений о производительности системы таймеров</span><span class="sxs-lookup"><span data-stu-id="062ed-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="062ed-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="062ed-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="062ed-1223">**Значок** ![Значок получения сведений о производительности системы таймеров](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="062ed-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="062ed-1224">**Описание**</span><span class="sxs-lookup"><span data-stu-id="062ed-1224">**Description**</span></span> 

<span data-ttu-id="062ed-1225">Это событие представляет получение всех сведений о производительности таймера с помощью tx_timer_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="062ed-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="062ed-1226">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="062ed-1226">**Information Fields**</span></span>

- <span data-ttu-id="062ed-1227">Поле сведений 1. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="062ed-1228">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="062ed-1229">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="062ed-1230">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="062ed-1230">Info Field 4: Not used.</span></span>