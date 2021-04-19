---
title: Глава 3. Параметры конфигурации ОСРВ Azure NetX Duo DHCPv6
description: Существует ряд параметров конфигурации ОСРВ Azure NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814779"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a><span data-ttu-id="c4e5b-103">Глава 3. Параметры конфигурации ОСРВ Azure NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="c4e5b-103">Chapter 3 - Azure RTOS NetX Duo DHCPv6 configuration options</span></span>

<span data-ttu-id="c4e5b-104">Существует ряд параметров конфигурации ОСРВ Azure NetX Duo DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-104">There are several configuration options for building Azure RTOS NetX Duo DHCPv6.</span></span> <span data-ttu-id="c4e5b-105">Их подробное описание приводится ниже:</span><span class="sxs-lookup"><span data-stu-id="c4e5b-105">The following list describes each in detail:</span></span>  
  
  
- <span data-ttu-id="c4e5b-106">**NX_DHCPV6_THREAD_PRIORITY** Приоритет клиентского потока.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-106">**NX_DHCPV6_THREAD_PRIORITY** Priority of the Client thread.</span></span> <span data-ttu-id="c4e5b-107">По умолчанию это значение назначает потоку клиента приоритет 2.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-107">By   default, this value specifies that   the Client thread runs at priority   2.</span></span>

- <span data-ttu-id="c4e5b-108">**NX_DHCPV6_MUTEX_WAIT** Параметр времени ожидания для получения монопольной блокировки для клиентского мьютекса DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-108">**NX_DHCPV6_MUTEX_WAIT** Time out option for obtaining an exclusive lock on a DHCPv6 Client mutex.</span></span> <span data-ttu-id="c4e5b-109">По умолчанию используется значение TX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-109">The default value is TX_WAIT_FOREVER.</span></span>

- <span data-ttu-id="c4e5b-110">**NX_DHCPV6_TICKS_PER_SECOND** Отношение тактов к секундам.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-110">**NX_DHCPV6_TICKS_PER_SECOND** Ratio of ticks to seconds.</span></span> <span data-ttu-id="c4e5b-111">Эта величина зависит от процессора.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-111">This is processor dependent.</span></span> <span data-ttu-id="c4e5b-112">Значение по умолчанию — 100.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-112">The default value is 100.</span></span>

- <span data-ttu-id="c4e5b-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL** Интервал времени в секундах, в течение которого таймер времени существования IP-адреса обновляет период времени, когда текущий IP-адрес будет назначен клиенту.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-113">**NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Time interval in seconds at which the IP lifetime timer updates the length of time the current IP address has been assigned to the Client.</span></span> <span data-ttu-id="c4e5b-114">По умолчанию используется значение 1.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-114">By default, this value is 1.</span></span>

- <span data-ttu-id="c4e5b-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL** Интервал времени в секундах, в течение которого таймер сеанса обновляет период времени, когда клиент взаимодействует с сервером.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-115">**NX_DHCPV6_SESSION_TIMER_INTERVAL**  Time interval in seconds at which the session timer updates the length of time the Client has been in session communicating with the Server.</span></span> <span data-ttu-id="c4e5b-116">По умолчанию используется значение 1.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-116">By default, this value is 1.</span></span>

- <span data-ttu-id="c4e5b-117">**NX_DHCPV6_MAX_IA_ADDRESS** Максимальное количество адресов IA, которые могут быть добавлены в запись клиента.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-117">**NX_DHCPV6_MAX_IA_ADDRESS** The maximum number of IA addresses that can be added to the Client record.</span></span> <span data-ttu-id="c4e5b-118">Значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-118">The default value is 1.</span></span> 

- <span data-ttu-id="c4e5b-119">**NX_DHCPV6_NUM_DNS_SERVERS** Число DNS-серверов для хранения в записи клиента.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-119">**NX_DHCPV6_NUM_DNS_SERVERS** Number of DNS servers to store to the client record.</span></span> <span data-ttu-id="c4e5b-120">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-120">The default value is 2.</span></span>

- <span data-ttu-id="c4e5b-121">**NX_DHCPV6_NUM_TIME_SERVERS** Число серверов времени для хранения в записи клиента.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-121">**NX_DHCPV6_NUM_TIME_SERVERS** Number of time servers to store to the client record.</span></span> <span data-ttu-id="c4e5b-122">Значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-122">The default value is 1.</span></span>

- <span data-ttu-id="c4e5b-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE** Размер буфера в записи клиента для хранения доменного имени клиента.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-123">**NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Size of the buffer in the Client record to hold the client’s network domain name.</span></span> <span data-ttu-id="c4e5b-124">Значение по умолчанию — 30.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-124">The default value is 30.</span></span>

- <span data-ttu-id="c4e5b-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE** Размер буфера в записи клиента для хранения часового пояса клиента.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-125">**NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Size of the buffer in the Client record to hold the Client’s time zone.</span></span> <span data-ttu-id="c4e5b-126">Значение по умолчанию — 10.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-126">The default value is 10.</span></span>

- <span data-ttu-id="c4e5b-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Размер буфера в записи клиента для хранения параметра "сообщение о состоянии" в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-127">**NX_DHCPV6_MAX_MESSAGE_SIZE** Size of the buffer in the Client record to hold the option status message in a Server reply.</span></span> <span data-ttu-id="c4e5b-128">Значение по умолчанию — 100 байт.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-128">The default value is 100 bytes.</span></span>

- <span data-ttu-id="c4e5b-129">**NX_DHCPV6_PACKET_TIME_OUT** Время ожидания в секундах для выделения пакета из пула клиентских пакетов.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-129">**NX_DHCPV6_PACKET_TIME_OUT** Time out in seconds for allocating a packet from the Client packet pool.</span></span> <span data-ttu-id="c4e5b-130">Значение по умолчанию — 3 секунды.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-130">The default value is 3 seconds.</span></span>

- <span data-ttu-id="c4e5b-131">**NX_DHCPV6_TYPE_OF_SERVICE** Эта функция определяет тип службы для передачи пакетов UDP из сокета клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-131">**NX_DHCPV6_TYPE_OF_SERVICE** This defines the type of service for UDP packet transmission from the DHCPv6 Client socket.</span></span> <span data-ttu-id="c4e5b-132">По умолчанию используется значение **NX_IP_NORMAL**.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-132">The default value is **NX_IP_NORMAL**.</span></span>

- <span data-ttu-id="c4e5b-133">**NX_DHCPV6_TIME_TO_LIVE** Число попыток направления пакета клиента сетевым маршрутизатором до отклонения пакета.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-133">**NX_DHCPV6_TIME_TO_LIVE** The number of times a Client packet is forwarded by a network router before the packet is discarded.</span></span> <span data-ttu-id="c4e5b-134">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-134">The default value is 0x80.</span></span>

- <span data-ttu-id="c4e5b-135">**NX_DHCPV6_QUEUE_DEPTH** Указывает число пакетов, которые могут храниться в очереди получения сокета UDP клиента, прежде чем NetX Duo начнет отклонять пакеты.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-135">**NX_DHCPV6_QUEUE_DEPTH** Specifies the number of packets to keep in the Client UDP socket receive queue before NetX Duo discards packets.</span></span> <span data-ttu-id="c4e5b-136">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-136">The default value is 5.</span></span>

## <a name="dhcpv6-message-transmission"></a><span data-ttu-id="c4e5b-137">Передача сообщений DHCPv6</span><span class="sxs-lookup"><span data-stu-id="c4e5b-137">DHCPv6 Message Transmission</span></span>

<span data-ttu-id="c4e5b-138">Существует набор параметров клиента DHCPv6 для настройки передачи сообщений DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-138">There are a set of DHCPv6 Client options for setting parameters on DHCPv6 message transmission.</span></span> <span data-ttu-id="c4e5b-139">А именно:</span><span class="sxs-lookup"><span data-stu-id="c4e5b-139">These are:</span></span> 

  - <span data-ttu-id="c4e5b-140">начальное время ожидания</span><span class="sxs-lookup"><span data-stu-id="c4e5b-140">initial timeout</span></span>

  - <span data-ttu-id="c4e5b-141">максимальная задержка при первой передаче</span><span class="sxs-lookup"><span data-stu-id="c4e5b-141">maximum delay on the first transmission</span></span>

  - <span data-ttu-id="c4e5b-142">максимальное время ожидания повторной передачи</span><span class="sxs-lookup"><span data-stu-id="c4e5b-142">maximum retransmission timeout</span></span> 

  - <span data-ttu-id="c4e5b-143">максимальное число повторных передач</span><span class="sxs-lookup"><span data-stu-id="c4e5b-143">maximum number of retransmissions</span></span> 

  - <span data-ttu-id="c4e5b-144">максимальная длительность ожидания ответа от сервера</span><span class="sxs-lookup"><span data-stu-id="c4e5b-144">maximum duration to wait for server response</span></span>

<span data-ttu-id="c4e5b-145">Эти параметры применяются к каждому из сообщений клиента DHCPv6:</span><span class="sxs-lookup"><span data-stu-id="c4e5b-145">These parameters apply to each of the DHCPv6 Client messages:</span></span>

- <span data-ttu-id="c4e5b-146">SOLICIT</span><span class="sxs-lookup"><span data-stu-id="c4e5b-146">SOLICIT</span></span>

- <span data-ttu-id="c4e5b-147">REQUEST</span><span class="sxs-lookup"><span data-stu-id="c4e5b-147">REQUEST</span></span>

- <span data-ttu-id="c4e5b-148">RENEW</span><span class="sxs-lookup"><span data-stu-id="c4e5b-148">RENEW</span></span>

- <span data-ttu-id="c4e5b-149">REBIND</span><span class="sxs-lookup"><span data-stu-id="c4e5b-149">REBIND</span></span>

- <span data-ttu-id="c4e5b-150">RELEASE</span><span class="sxs-lookup"><span data-stu-id="c4e5b-150">RELEASE</span></span>

- <span data-ttu-id="c4e5b-151">DECLINE</span><span class="sxs-lookup"><span data-stu-id="c4e5b-151">DECLINE</span></span>

- <span data-ttu-id="c4e5b-152">ПОДТВЕРДИТЬ</span><span class="sxs-lookup"><span data-stu-id="c4e5b-152">CONFIRM</span></span>

- <span data-ttu-id="c4e5b-153">INFORM</span><span class="sxs-lookup"><span data-stu-id="c4e5b-153">INFORM</span></span>

<span data-ttu-id="c4e5b-154">Ниже приведен полный список этих настраиваемых параметров и их значения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="c4e5b-154">The following is a complete list of these configurable options and their default</span></span> 

<span data-ttu-id="c4e5b-155">values:</span><span class="sxs-lookup"><span data-stu-id="c4e5b-155">values:</span></span>

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

<span data-ttu-id="c4e5b-156">Чтобы отменить ограничение времени ожидания повторной передачи, установите значение 0 для счетчика передаваемых сообщений.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-156">For no limit on a retransmission timeout, set the message retransmission count to 0.</span></span> <span data-ttu-id="c4e5b-157">Чтобы отменить ограничение количества попыток передачи сообщения клиента DHCPv6, установите значение 0 для счетчика передаваемых сообщений.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-157">For no limit on the number of times a DHCPv6 Client message is retransmitted (retries), set the message retransmission count to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="c4e5b-158">Независимо от длительности ожидания или количества повторных попыток, когда истекает срок действия IPv6-адреса, он удаляется из таблицы IP-адресов, и клиент не сможет его больше использовать.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-158">Regardless of length of timeout or number of retries, when an IPv6 address valid lifetime expires, it is removed from the IP address table and can no longer be used by the Client.</span></span> <span data-ttu-id="c4e5b-159">Клиент NetX Duo DHCPv6 автоматически начнет отправлять сообщения SOLICIT, запрашивающие новый IPv6-адрес.</span><span class="sxs-lookup"><span data-stu-id="c4e5b-159">The NetX Duo DHCPv6 Client will automatically begin sending SOLICIT messages requesting a new IPv6 address.</span></span>