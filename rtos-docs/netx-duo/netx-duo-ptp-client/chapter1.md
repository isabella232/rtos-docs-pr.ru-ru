---
title: Глава 1. Введение в PTP-клиент в NetX Duo для ОСРВ Azure
description: В этой главе приведен общий обзор PTP-клиента в NetX Duo для ОСРВ Azure.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5beec64bd6d74e3bed06be15255d6bd4a940ba64
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814591"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="a091c-103">Глава 1. Введение в PTP-клиент в NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="a091c-103">Chapter 1 - Introduction to Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="a091c-104">PTP в NetX Duo для ОСРВ Azure реализует клиентскую часть протокола времени PTP (версия 2) согласно стандарту IEEE 1588-2008.</span><span class="sxs-lookup"><span data-stu-id="a091c-104">The Azure RTOS NetX Duo PTP implements the client part of the Precision Time Protocol (PTP) version 2, IEEE 1588-2008.</span></span> <span data-ttu-id="a091c-105">Он используется для синхронизации часов между микроконтроллерами в локальной сети, которые взаимодействуют друг с другом через пакеты многоадресной рассылки IPv4 или IPv6.</span><span class="sxs-lookup"><span data-stu-id="a091c-105">It is used to synchronize clocks among MCUs on the local network by communicating each other via IPv4 or IPv6 multicast packets.</span></span>

## <a name="netx-duo-ptp-client-setup"></a><span data-ttu-id="a091c-106">Настройка PTP-клиента в NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a091c-106">NetX Duo PTP Client Setup</span></span>

<span data-ttu-id="a091c-107">Для правильной работы пакета PTP-клиента требуется, чтобы экземпляр IP-адреса в NetX Duo уже был создан.</span><span class="sxs-lookup"><span data-stu-id="a091c-107">In order to function properly, the PTP client package requires that a NetX Duo IP instance has already been created.</span></span>

<span data-ttu-id="a091c-108">По умолчанию PTP-клиент присоединяется к группе многоадресной рассылки IPv4.</span><span class="sxs-lookup"><span data-stu-id="a091c-108">By default, the PTP client joins IPv4 multicast group.</span></span> <span data-ttu-id="a091c-109">Чтобы запустить PTP-клиент в сети IPv6, нужно определить `NX_ENABLE_IPV6_MULTICAST` при сборке библиотеки NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="a091c-109">In order to run the PTP client on an IPv6 network, `NX_ENABLE_IPV6_MULTICAST` must be defined when building NetX Duo library.</span></span>

<span data-ttu-id="a091c-110">При создании PTP-клиента приложение должно предоставить функцию обратного вызова для обработки меток времени входящих и исходящих пакетов.</span><span class="sxs-lookup"><span data-stu-id="a091c-110">When creating the PTP client, the application must provide a callback function to handle timestamps of incoming and outgoing packets.</span></span> <span data-ttu-id="a091c-111">Для достижения высокого разрешения мы рекомендуем создавать метки времени с использованием таймера с высоким разрешением.</span><span class="sxs-lookup"><span data-stu-id="a091c-111">To achieve high resolution, we recommend applications to generate timestamps using a high resolution timer.</span></span> <span data-ttu-id="a091c-112">Чтобы использовать PTP в симуляторе, предоставляется программная реализация `nx_ptp_client_soft_clock_callback`.</span><span class="sxs-lookup"><span data-stu-id="a091c-112">To run the PTP on simulator, a software-based implementation `nx_ptp_client_soft_clock_callback` is provided.</span></span>

<span data-ttu-id="a091c-113">PTP-клиенту нужен пул пакетов для передачи сообщений PTP.</span><span class="sxs-lookup"><span data-stu-id="a091c-113">The PTP client requires a packet pool for transmitting PTP messages.</span></span> <span data-ttu-id="a091c-114">Размер полезных данных пула пакетов должен быть не меньше `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, что составляет 108 байт для IPv4 или 128 байт для IPv6.</span><span class="sxs-lookup"><span data-stu-id="a091c-114">The payload size of packet pool must be no less than `NX_UDP_PACKET + NX_PTP_CLIENT_PACKET_DATA_SIZE`, which is 108 bytes for IPv4, and 128 bytes if IPv6 is enabled.</span></span>

<span data-ttu-id="a091c-115">После создания PTP-клиента приложение может запустить этот PTP-клиент.</span><span class="sxs-lookup"><span data-stu-id="a091c-115">After creating the PTP Client, the application can start the PTP client.</span></span> <span data-ttu-id="a091c-116">Синхронизация выполняется во вспомогательном потоке PTP.</span><span class="sxs-lookup"><span data-stu-id="a091c-116">The synchronization is done in the PTP helper thread.</span></span> <span data-ttu-id="a091c-117">Можно указать функцию обратного вызова для событий.</span><span class="sxs-lookup"><span data-stu-id="a091c-117">An event callback function can be specified.</span></span> <span data-ttu-id="a091c-118">Она будет вызываться, когда происходит одно из следующих событий:</span><span class="sxs-lookup"><span data-stu-id="a091c-118">It will be invoked when any one of the following events happen.</span></span>
* <span data-ttu-id="a091c-119">выбор основных часов;</span><span class="sxs-lookup"><span data-stu-id="a091c-119">A master is selected;</span></span> 
* <span data-ttu-id="a091c-120">калибровка времени;</span><span class="sxs-lookup"><span data-stu-id="a091c-120">The time is calibrated.</span></span>
* <span data-ttu-id="a091c-121">истечение времени ожидания основных часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-121">A master times out.</span></span>

## <a name="netx-duo-ptp-client-messages"></a><span data-ttu-id="a091c-122">Сообщения PTP-клиента в NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a091c-122">NetX Duo PTP Client Messages</span></span>

<span data-ttu-id="a091c-123">PTP-клиент в NetX Duo реализует только механизм запроса задержки и ответа.</span><span class="sxs-lookup"><span data-stu-id="a091c-123">The NetX Duo PTP client implements the delay request-response mechanism only.</span></span> <span data-ttu-id="a091c-124">PTP-клиент открывает два UDP-порта:</span><span class="sxs-lookup"><span data-stu-id="a091c-124">The PTP client  opens two UDP ports.</span></span> <span data-ttu-id="a091c-125">*319* для сообщений **событий** и *320* для **общих** сообщений.</span><span class="sxs-lookup"><span data-stu-id="a091c-125">*319* for **event** message and *320* for **general** message.</span></span> <span data-ttu-id="a091c-126">Существует пять типов сообщений для этого механизма:</span><span class="sxs-lookup"><span data-stu-id="a091c-126">There are five types of message for this mechanism.</span></span>

* <span data-ttu-id="a091c-127">**Announce** (Объявление).</span><span class="sxs-lookup"><span data-stu-id="a091c-127">**Announce**.</span></span> <span data-ttu-id="a091c-128">Это сообщение события.</span><span class="sxs-lookup"><span data-stu-id="a091c-128">This is an event message.</span></span> <span data-ttu-id="a091c-129">Оно используется для выбора основных часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-129">It is used for master clock selection.</span></span>
* <span data-ttu-id="a091c-130">**Sync** (Синхронизация). Это сообщение события.</span><span class="sxs-lookup"><span data-stu-id="a091c-130">**Sync**. This is an event message.</span></span> <span data-ttu-id="a091c-131">Оно используется для отправки отметок времени источника и вычисления задержки в пути от основных часов к клиенту.</span><span class="sxs-lookup"><span data-stu-id="a091c-131">It is used to send origin timestamp and calculate the path delay from master to client.</span></span>
* <span data-ttu-id="a091c-132">**Follow_Up** (Уточнение).</span><span class="sxs-lookup"><span data-stu-id="a091c-132">**Follow_Up**.</span></span> <span data-ttu-id="a091c-133">Это общее событие.</span><span class="sxs-lookup"><span data-stu-id="a091c-133">This is a general message.</span></span> <span data-ttu-id="a091c-134">Оно является необязательным и используется для корретировки меток времени источника в связанном сообщении синхронизации.</span><span class="sxs-lookup"><span data-stu-id="a091c-134">It is optional and used to correct the origin timestamp in related Sync message.</span></span> <span data-ttu-id="a091c-135">Оно отправляется только в том случае, если установлен флаг двухэтапной синхронизации в Sync.</span><span class="sxs-lookup"><span data-stu-id="a091c-135">It is sent only when the two step bit in Sync flag is set.</span></span>
* <span data-ttu-id="a091c-136">**Delay_Req** (Запрос задержки).</span><span class="sxs-lookup"><span data-stu-id="a091c-136">**Delay_Req**.</span></span> <span data-ttu-id="a091c-137">Это сообщение события.</span><span class="sxs-lookup"><span data-stu-id="a091c-137">This is an event message.</span></span> <span data-ttu-id="a091c-138">Оно отправляется PTP-клиентом, чтобы при получении ответа Delay_Resp вычислить задержку в пути от клиента к основным часам.</span><span class="sxs-lookup"><span data-stu-id="a091c-138">It is sent from PTP client to calculate the path delay from client to master, on receiving Delay_Resp.</span></span>
* <span data-ttu-id="a091c-139">**Delay_Resp** (Ответ задержки).</span><span class="sxs-lookup"><span data-stu-id="a091c-139">**Delay_Resp**.</span></span> <span data-ttu-id="a091c-140">Это сообщение события.</span><span class="sxs-lookup"><span data-stu-id="a091c-140">This is an event message.</span></span> <span data-ttu-id="a091c-141">Оно отправляется от основных часов клиенту, чтобы он мог вычислить задержку в пути от клиента к основным часам.</span><span class="sxs-lookup"><span data-stu-id="a091c-141">It is sent from master to client to calculate the path delay from client to master.</span></span>

<span data-ttu-id="a091c-142">*Обратите внимание, что в реализации отсутствует алгоритм выбора лучших основных часов. Когда PTP-клиент находится в состоянии прослушивания, он принимает только первый ответ от основных часов.*</span><span class="sxs-lookup"><span data-stu-id="a091c-142">*Note, "best master clock" algorithm is not implemented. Only the first master clock is accepted when the PTP client is in listening state.*</span></span>

## <a name="netx-duo-ptp-client-clock-callback"></a><span data-ttu-id="a091c-143">Обратный вызов часов в PTP-клиенте в NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a091c-143">NetX Duo PTP Client Clock Callback</span></span>
<span data-ttu-id="a091c-144">Чтобы синхронизировать время по основным часам, PTP-клиенту требуются локальные часы.</span><span class="sxs-lookup"><span data-stu-id="a091c-144">To synchronize clock from master, PTP client needs a local clock.</span></span> <span data-ttu-id="a091c-145">Функция обратного вызова часов передается в PTP-клиент во время его создания.</span><span class="sxs-lookup"><span data-stu-id="a091c-145">A clock callback function is passed into PTP client during creation.</span></span> <span data-ttu-id="a091c-146">Формат подпрограммы обратного вызова часов определен ниже.</span><span class="sxs-lookup"><span data-stu-id="a091c-146">The format of the clock callback routine is  defined below.</span></span>
```C
UINT ptp_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```
<span data-ttu-id="a091c-147">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a091c-147">The input parameters are defined as follows:</span></span>
* <span data-ttu-id="a091c-148">*client_ptr* — указывает на PTP-клиент.</span><span class="sxs-lookup"><span data-stu-id="a091c-148">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="a091c-149">*operation* — определяет операцию обратного вызова, допустимые значения которой приведены ниже.</span><span class="sxs-lookup"><span data-stu-id="a091c-149">*operation* specifies the callback operation, valid values are defined as shown in the list below.</span></span>
  * <span data-ttu-id="a091c-150">**NX_PTP_CLIENT_CLOCK_INIT** — инициализация часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-150">**NX_PTP_CLIENT_CLOCK_INIT** Initialize clock.</span></span>
  * <span data-ttu-id="a091c-151">**NX_PTP_CLIENT_CLOCK_SET** — настройка текущей метки времени, которая задана `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="a091c-151">**NX_PTP_CLIENT_CLOCK_SET** Set current timestamp specified by `time_ptr`.</span></span>
  * <span data-ttu-id="a091c-152">**NX_PTP_CLIENT_CLOCK_GET** — передача текущей метки времени в `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="a091c-152">**NX_PTP_CLIENT_CLOCK_GET** Return current timestamp to `time_ptr`.</span></span>
  * <span data-ttu-id="a091c-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** — извлечение метки времени из `packet_ptr` в `time_ptr`.</span><span class="sxs-lookup"><span data-stu-id="a091c-153">**NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Extract timestamp from `packet_ptr` to `time_ptr`.</span></span>
  * <span data-ttu-id="a091c-154">**NX_PTP_CLIENT_CLOCK_ADJUST** — корректировка текущей метки времени менее чем на *1* секунду.</span><span class="sxs-lookup"><span data-stu-id="a091c-154">**NX_PTP_CLIENT_CLOCK_ADJUST** Adjust current timestamp less than *1* second.</span></span>
  * <span data-ttu-id="a091c-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** — пометка `packet_ptr`, для которой нужно известить PTP-клиента о метке времени при ее передаче.</span><span class="sxs-lookup"><span data-stu-id="a091c-155">**NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Mark the `packet_ptr` which requires to notify PTP client the timestamp when it is transmitted.</span></span>
  * <span data-ttu-id="a091c-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** — обновление программного таймера.</span><span class="sxs-lookup"><span data-stu-id="a091c-156">**NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Update soft timer.</span></span> <span data-ttu-id="a091c-157">Может игнорироваться аппаратными часами.</span><span class="sxs-lookup"><span data-stu-id="a091c-157">It can be ignored by hardware clock.</span></span>
* <span data-ttu-id="a091c-158">*time_ptr* — указывает на метку времени.</span><span class="sxs-lookup"><span data-stu-id="a091c-158">*time_ptr* points to timestamp.</span></span>
* <span data-ttu-id="a091c-159">*packet_ptr* — указывает на пакет.</span><span class="sxs-lookup"><span data-stu-id="a091c-159">*packet_ptr* points to packet.</span></span>
* <span data-ttu-id="a091c-160">*callback_data* — указывает на непрозрачные данные обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="a091c-160">*callback_data* points to opaque callback data.</span></span>

<span data-ttu-id="a091c-161">Тип данных NX_PTP_TIME определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a091c-161">The NX_PTP_TIME data type is defined as follows.</span></span>
```C
typedef struct NX_PTP_TIME_STRUCT
{
    /* The MSB of the number of seconds */
    LONG  second_high;

    /* The LSB of the number of seconds */
    ULONG second_low;

    /* The number of nanoseconds */
    LONG  nanosecond;
} NX_PTP_TIME;
```

## <a name="netx-duo-ptp-client-event-callback"></a><span data-ttu-id="a091c-162">Обратный вызов для события PTP-клиента в NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a091c-162">NetX Duo PTP Client Event Callback</span></span>
<span data-ttu-id="a091c-163">Функция обратного вызова для события позволяет оповещать приложение о смене состояния PTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="a091c-163">The event callback function can be setup to notify application the state of PTP client.</span></span> <span data-ttu-id="a091c-164">Формат подпрограммы обратного вызова для события представлен ниже.</span><span class="sxs-lookup"><span data-stu-id="a091c-164">The format of the event callback routine is defined as shown below.</span></span>
```C
UINT event_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT event, 
    VOID *event_data, 
    VOID *callback_data);
```
<span data-ttu-id="a091c-165">Принимаются следующие входные параметры:</span><span class="sxs-lookup"><span data-stu-id="a091c-165">The input parameters are.</span></span>
* <span data-ttu-id="a091c-166">*client_ptr* — указывает на PTP-клиент.</span><span class="sxs-lookup"><span data-stu-id="a091c-166">*client_ptr* points to PTP client.</span></span>
* <span data-ttu-id="a091c-167">*event* — определяет событие для обратного вызова, для которого допускаются следующие значения:</span><span class="sxs-lookup"><span data-stu-id="a091c-167">*event* specifies the callback event, valid values are defined as:</span></span>
  * <span data-ttu-id="a091c-168">**NX_PTP_CLIENT_EVENT_MASTER** — выбор основных часов;</span><span class="sxs-lookup"><span data-stu-id="a091c-168">**NX_PTP_CLIENT_EVENT_MASTER** A master clock is selected.</span></span>
  * <span data-ttu-id="a091c-169">**NX_PTP_CLIENT_EVENT_SYNC** — калибровка PTP-клиента;</span><span class="sxs-lookup"><span data-stu-id="a091c-169">**NX_PTP_CLIENT_EVENT_SYNC** PTP client is calibrated.</span></span>
  * <span data-ttu-id="a091c-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** — истечение времени ожидания главных часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-170">**NX_PTP_CLIENT_EVENT_TIMEOUT** Master clock is timeout.</span></span>
* <span data-ttu-id="a091c-171">*event_data* — определяет данные для конкретного события.</span><span class="sxs-lookup"><span data-stu-id="a091c-171">*event_data* specifies the data related to event.</span></span> <span data-ttu-id="a091c-172">Если это событие **NX_PTP_CLIENT_EVENT_MASTER**, event_data указывает на экземпляр `NX_PTP_CLIENT_MASTER`.</span><span class="sxs-lookup"><span data-stu-id="a091c-172">When event is **NX_PTP_CLIENT_EVENT_MASTER**, event_data points to `NX_PTP_CLIENT_MASTER` instance.</span></span> <span data-ttu-id="a091c-173">Если это событие **NX_PTP_CLIENT_EVENT_SYNC**, event_data указывает на экземпляр `NX_PTP_CLIENT_SYNC`.</span><span class="sxs-lookup"><span data-stu-id="a091c-173">When event is **NX_PTP_CLIENT_EVENT_SYNC**, event data points to `NX_PTP_CLIENT_SYNC` instance.</span></span>

## <a name="netx-duo-ptp-client-communication"></a><span data-ttu-id="a091c-174">Взаимодействие с PTP-клиентом в NetX Duo</span><span class="sxs-lookup"><span data-stu-id="a091c-174">NetX Duo PTP Client Communication</span></span>
<span data-ttu-id="a091c-175">Как уже упоминалось, PTP-клиент в NetX Duo поддерживает только механизм запроса задержки и ответа.</span><span class="sxs-lookup"><span data-stu-id="a091c-175">As mentioned previously, NetX Duo PTP client only supports delay request-response mechanism.</span></span> <span data-ttu-id="a091c-176">Этот механизм измеряет задержку в пути между клиентом и основными часами следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a091c-176">This mechanism measures the mean path delay between the client and the master clock as below:</span></span>
1. <span data-ttu-id="a091c-177">Клиент получает сообщение *Announce* от основных часов и сразу выбирает их как лучшие основные часы.</span><span class="sxs-lookup"><span data-stu-id="a091c-177">Client receives *Announce* message from master and select it as best master.</span></span>
1. <span data-ttu-id="a091c-178">Клиент получает сообщение *Sync* от основных часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-178">Client receives *Sync* message from master.</span></span> <span data-ttu-id="a091c-179">Метка времени *t1* в этом сообщении обозначает метку времени источника.</span><span class="sxs-lookup"><span data-stu-id="a091c-179">The timestamp *t1* is the origin timestamp in this message.</span></span> <span data-ttu-id="a091c-180">Метка времени *t2* заполняется по данным местных часов в момент получения сообщения.</span><span class="sxs-lookup"><span data-stu-id="a091c-180">The timestamp *t2* is read from local clock when this message is received.</span></span>
1. <span data-ttu-id="a091c-181">Клиент получает сообщение *Follow_Up* от основных часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-181">Client receives *Follow_Up* message from master.</span></span> <span data-ttu-id="a091c-182">Это необязательное сообщение, которое учитывается только при установленном флаге двухэтапной синхронизации в *Sync*.</span><span class="sxs-lookup"><span data-stu-id="a091c-182">This message is optional and valid only when two step in *Sync* flag is set.</span></span> <span data-ttu-id="a091c-183">Теперь метка времени *t1* в этом сообщении заменяется меткой времени источника.</span><span class="sxs-lookup"><span data-stu-id="a091c-183">Then the timestamp *t1* is updated to the origin timestamp in this message.</span></span>
1. <span data-ttu-id="a091c-184">Клиент отправляет сообщение *Delay_Req* на основные часы.</span><span class="sxs-lookup"><span data-stu-id="a091c-184">Client sends *Delay_Req* message to master.</span></span> <span data-ttu-id="a091c-185">Метка времени *t3* заполняется по данным местных часов в момент отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="a091c-185">The timestamp *t3* is read from local clock when the message is transmitted.</span></span>
1. <span data-ttu-id="a091c-186">Клиент получает сообщение *Delay_Resp* от основных часов.</span><span class="sxs-lookup"><span data-stu-id="a091c-186">Client receives *Delay_Resp* message from master.</span></span> <span data-ttu-id="a091c-187">Метка времени *t4* обозначает момент получения этого сообщения.</span><span class="sxs-lookup"><span data-stu-id="a091c-187">The timestamp *t4* is the receive timestamp in this message.</span></span>

<span data-ttu-id="a091c-188">Вычисляется средняя задержка в пути, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="a091c-188">The mean path delay is computed as shown below.</span></span>
```C
<meanPathDelay>=[(t2-t1)+(t4-t3)]/2
```
<span data-ttu-id="a091c-189">Вычисляется смещение относительно основных часов, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="a091c-189">The offset from master is computed as shown below.</span></span>
```C
<offsetFromMaster>=client_clock-master_clock
                  =(t2-t1)-<meanPathDelay>
```

> [!NOTE]
> <span data-ttu-id="a091c-190">\*Значение \***correctionField** _ в этих вычислениях игнорируется._</span><span class="sxs-lookup"><span data-stu-id="a091c-190">\*The \***correctionField** _ is ignored during the calculation._</span></span>