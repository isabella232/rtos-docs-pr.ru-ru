---
title: Глава 8. События трассировки NetX в ОСРВ Azure
description: В этой главе содержится описание событий NetX в ОСРВ Azure.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: ce355d86d7db0b7e259ae58e306d990277b77a8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816288"
---
# <a name="chapter-8---azure-rtos-netx-trace-events"></a><span data-ttu-id="63ec4-103">Глава 8. События трассировки NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="63ec4-103">Chapter 8 - Azure RTOS NetX trace events</span></span>

<span data-ttu-id="63ec4-104">В этой главе содержится описание событий NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="63ec4-104">This chapter contains a description of the Azure RTOS NetX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="63ec4-105">Список событий и значков</span><span class="sxs-lookup"><span data-stu-id="63ec4-105">List of Events and Icons</span></span>

<span data-ttu-id="63ec4-106">Ниже приведен список событий NetX, отображаемых в TraceX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-106">The following is a list of NetX events displayed by TraceX.</span></span>

| <span data-ttu-id="63ec4-107">Значок</span><span class="sxs-lookup"><span data-stu-id="63ec4-107">Icon</span></span>                                           | <span data-ttu-id="63ec4-108">Значение</span><span class="sxs-lookup"><span data-stu-id="63ec4-108">Meaning</span></span>                 |
| -------------------------------- | ------------------------------------- |
| ![Значок получения внутренних запросов ARP](./media/user-guide/netx-events/image1.png)    | <span data-ttu-id="63ec4-110">Получение внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-110">Internal ARP Request Receive</span></span> |
| ![Значок отправки внутренних запросов ARP](./media/user-guide/netx-events/image2.png)    | <span data-ttu-id="63ec4-112">Отправка внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-112">Internal ARP Request Send</span></span> |
| ![Значок получения внутреннего ответа ARP](./media/user-guide/netx-events/image3.png)    | <span data-ttu-id="63ec4-114">Получение внутреннего ответа ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-114">Internal ARP Response Receive</span></span> |
| ![Значок отправки внутреннего ответа ARP](./media/user-guide/netx-events/image4.png)    | <span data-ttu-id="63ec4-116">Отправка внутреннего ответа ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-116">Internal ARP Response Send</span></span> |
| ![Значок получения внутреннего протокола ICMP](./media/user-guide/netx-events/image5.png)    | <span data-ttu-id="63ec4-118">Получение внутреннего протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-118">Internal ICMP Receive</span></span> |
| ![Значок отправки внутреннего протокола ICMP](./media/user-guide/netx-events/image6.png)    | <span data-ttu-id="63ec4-120">Отправка внутреннего протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-120">Internal ICMP Send</span></span> |
| ![Значок получения внутреннего протокола IGMP NetX](./media/user-guide/netx-events/image7.png)    | <span data-ttu-id="63ec4-122">Получение внутреннего протокола IGMP NetX</span><span class="sxs-lookup"><span data-stu-id="63ec4-122">Internal NetX IGMP Receive</span></span> |
| ![Значок получения внутреннего IP](./media/user-guide/netx-events/image8.png)    | <span data-ttu-id="63ec4-124">Получение внутреннего IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-124">Internal IP Receive</span></span> |
| ![Значок отправки внутреннего IP](./media/user-guide/netx-events/image9.png)    | <span data-ttu-id="63ec4-126">Отправка внутреннего IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-126">Internal IP Send</span></span> |
| ![Значок получения данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image10.png)    | <span data-ttu-id="63ec4-128">Получение данных по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-128">Internal TCP Data Receive</span></span> |
| ![Значок отправки данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image11.png)    | <span data-ttu-id="63ec4-130">Отправка данных по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-130">Internal TCP Data Send</span></span> |
| ![Значок получения флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image12.png)    | <span data-ttu-id="63ec4-132">Получение флага FIN внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-132">Internal TCP FIN Receive</span></span> |
| ![Значок отправки флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image13.png)    | <span data-ttu-id="63ec4-134">Отправка флага FIN внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-134">Internal TCP FIN Send</span></span> |
| ![Значок получения флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image14.png)    | <span data-ttu-id="63ec4-136">Получение флага RST внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-136">Internal TCP RST Receive</span></span> |
| ![Значок отправки флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image15.png)    | <span data-ttu-id="63ec4-138">Отправка флага RST внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-138">Internal TCP RST Send</span></span> |
| ![Значок получения SYN внутреннего TCP](./media/user-guide/netx-events/image16.png)    | <span data-ttu-id="63ec4-140">Получение SYN внутреннего TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-140">Internal TCP SYN Receive</span></span> |
| ![Значок отправки SYN внутреннего TCP](./media/user-guide/netx-events/image17.png)    | <span data-ttu-id="63ec4-142">Отправка SYN внутреннего TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-142">Internal TCP SYN Send</span></span> |
| ![Значок получения внутреннего протокола UDP](./media/user-guide/netx-events/image18.png)    | <span data-ttu-id="63ec4-144">Получение внутреннего протокола UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-144">Internal UDP Receive</span></span> |
| ![Значок отправки внутреннего протокола UDP](./media/user-guide/netx-events/image19.png)    | <span data-ttu-id="63ec4-146">Отправка внутреннего протокола UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-146">Internal UDP Send</span></span> |
| ![Значок получения внутреннего протокола RARP](./media/user-guide/netx-events/image20.png)    | <span data-ttu-id="63ec4-148">Получение внутреннего протокола RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-148">Internal RARP Receive</span></span> |
| ![Значок отправки внутреннего протокола RARP](./media/user-guide/netx-events/image21.png)    | <span data-ttu-id="63ec4-150">Отправка внутреннего протокола RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-150">Internal RARP Send</span></span> |
| ![Значок повторной попытки подключения по внутреннему протоколу TCP](./media/user-guide/netx-events/image22.png)    | <span data-ttu-id="63ec4-152">Повторная попытка подключения по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-152">Internal TCP Retry</span></span> |
| ![Значок изменения состояния внутреннего протокола TCP](./media/user-guide/netx-events/image23.png)    | <span data-ttu-id="63ec4-154">Изменение состояния внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-154">Internal TCP State Change</span></span> |
| ![Значок отправки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image24.png)    | <span data-ttu-id="63ec4-156">Отправка пакета внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-156">Internal I/O Driver Packet Send</span></span> |
| ![icon](./media/user-guide/netx-events/image25.png)    | <span data-ttu-id="63ec4-158">Инициализация внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-158">Internal I/O Driver Initialize</span></span> |
| ![Значок инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image26.png)    | <span data-ttu-id="63ec4-160">Включение ссылки на внутренний драйвер устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-160">Internal I/O Driver Link Enable</span></span> |
| ![Значок отключения ссылки на внутренний драйвер устройств ввода-вывода](./media/user-guide/netx-events/image27.png)    | <span data-ttu-id="63ec4-162">Отключение ссылки на внутренний драйвер устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-162">Internal I/O Driver Link Disable</span></span> |
| ![Значок широковещательной рассылки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image28.png)    | <span data-ttu-id="63ec4-164">Широковещательная рассылка пакета внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-164">Internal I/O Driver Packet Broadcast</span></span> |
| ![Значок отправки ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image29.png)    | <span data-ttu-id="63ec4-166">Отправка ARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-166">Internal I/O Driver ARP Send</span></span> |
| ![Значок отправки ответа ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image30.png)    | <span data-ttu-id="63ec4-168">Отправка ответа ARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-168">Internal I/O Driver ARP Response Send</span></span> |
| ![Значок отправки RARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image31.png)    | <span data-ttu-id="63ec4-170">Отправка RARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-170">Internal I/O Driver RARP Send</span></span> |
| ![Значок подключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image32.png)    | <span data-ttu-id="63ec4-172">Подключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-172">Internal I/O Driver Multicast Join</span></span> |
| ![Значок отключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image33.png)    | <span data-ttu-id="63ec4-174">Отключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-174">Internal I/O Driver Multicast Leave</span></span> |
| ![Значок получения состояния внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image34.png)    | <span data-ttu-id="63ec4-176">Получение состояния внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-176">Internal I/O Driver Get Status</span></span> |
| ![Значок получения скорости внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image35.png)    | <span data-ttu-id="63ec4-178">Получение скорости внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-178">Internal I/O Driver Get Speed</span></span> |
| ![Значок получения дуплексного типа внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image36.png)    | <span data-ttu-id="63ec4-180">Получение дуплексного типа внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-180">Internal I/O Driver Get Duplex Type</span></span> |
| ![Значок получения количества ошибок внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image37.png)    | <span data-ttu-id="63ec4-182">Получение количества ошибок внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-182">Internal I/O Driver Get Error Count</span></span> |
| ![Значок получения количества RX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image38.png)    | <span data-ttu-id="63ec4-184">Получение количества RX внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-184">Internal I/O Driver Get RX Count</span></span> |
| ![Значок получения количества TX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image39.png)    | <span data-ttu-id="63ec4-186">Получение количества TX внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-186">Internal I/O Driver Get TX Count</span></span> |
| ![Значок получения ошибок выделения внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image40.png)    | <span data-ttu-id="63ec4-188">Получение ошибок выделения внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-188">Internal I/O Driver Get Allocation Errors</span></span> |
| ![Значок отмены инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image41.png)    | <span data-ttu-id="63ec4-190">Отмена инициализации внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-190">Internal I/O Driver Un-initialize</span></span> |
| ![Значок отложенной обработки внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image42.png)    | <span data-ttu-id="63ec4-192">Отложенная обработка внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-192">Internal I/O Driver Deferred Processing</span></span> |
| ![Значок недопустимости динамических записей ARP](./media/user-guide/netx-events/image43.png)    | <span data-ttu-id="63ec4-194">**Недопустимые динамические записи ARP** (*nx_arp_dynamic_entries_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-194">**ARP Dynamic Entries Invalidate** (*nx_arp_dynamic_entries_invalidate*)</span></span> |
| ![Значок набора динамических записей ARP](./media/user-guide/netx-events/image44.png)    | <span data-ttu-id="63ec4-196">**Задание динамических записей ARP** (*nx_arp_dynamic_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-196">**ARP Dynamic Entry Set** (*nx_arp_dynamic_entry_set*)</span></span> |
| ![Значок включения ARP](./media/user-guide/netx-events/image45.png)    | <span data-ttu-id="63ec4-198">**Включение ARP** (*nx_arp_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-198">**ARP Enable** (*nx_arp_enable*)</span></span> |
| ![Значок необязательной отправки ARP](./media/user-guide/netx-events/image46.png)    | <span data-ttu-id="63ec4-200">**Необязательная отправка ARP** (*nx_arp_gratuitous_send*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-200">**ARP Gratuitous Send** (*nx_arp_gratuitous_send*)</span></span> |
| ![Значок поиска адреса оборудования ARP](./media/user-guide/netx-events/image47.png)    | <span data-ttu-id="63ec4-202">**Поиск адреса оборудования ARP** (*nx_arp_hardware_address_find*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-202">**ARP Hardware Address Find** (*nx_arp_hardware_address_find*)</span></span> |
| ![Значок получения сведений об ARP](./media/user-guide/netx-events/image48.png)    | <span data-ttu-id="63ec4-204">**Получение сведений об ARP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-204">**ARP Information Get** (*nx_arp_info_get*)</span></span> |
| ![Значок поиска IP-адреса ARP](./media/user-guide/netx-events/image49.png)    | <span data-ttu-id="63ec4-206">**Поиск IP-адреса ARP** (*nx_arp_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-206">**ARP IP Address Find** (*nx_arp_ip_address_find*)</span></span> |
| ![Значок создания статической записи ARP](./media/user-guide/netx-events/image50.png)    | <span data-ttu-id="63ec4-208">**Создание статической записи ARP** (*nx_arp_static_entry_create*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-208">**ARP Static Entry Create** (*nx_arp_static_entry_create*)</span></span> |
| ![Значок удаления статических записей ARP](./media/user-guide/netx-events/image51.png)    | <span data-ttu-id="63ec4-210">**Удаление статических записей ARP** (*nx_arp_static_entries_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-210">**ARP Static Entries Delete** (*nx_arp_static_entries_delete*)</span></span> |
| ![Значок удаления статической записи ARP](./media/user-guide/netx-events/image52.png)    | <span data-ttu-id="63ec4-212">**Удаление статической записи ARP** (*nx_arp_static_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-212">**ARP Static Entry Delete** (*nx_arp_static_entry_delete*)</span></span> |
| ![Значок удаления записи кэша Duo](./media/user-guide/netx-events/image53.png)    | <span data-ttu-id="63ec4-214">**Операция удаления записи кэша Duo** (*nxd_nd_cache_entry_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-214">**Duo Cache Entry Delete** (*nxd_nd_cache_entry_delete*)</span></span> |
| ![Значок набора записей кэша Duo](./media/user-guide/netx-events/image54.png)    | <span data-ttu-id="63ec4-216">**Набор записей кэша Duo** (*nxd_nd_cache_entry_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-216">**Duo Cache Entry Set** (*nxd_nd_cache_entry_set*)</span></span> |
| ![Значок недействительности кэша Duo](./media/user-guide/netx-events/image55.png)    | <span data-ttu-id="63ec4-218">**Недействительность кэша Duo** (*nxd_nd_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-218">**Duo Cache Invalidate** (*nxd_nd_cache_invalidate*)</span></span> |
| ![Значок поиска IP-адреса кэша Duo](./media/user-guide/netx-events/image56.png)    | <span data-ttu-id="63ec4-220">**Поиск IP-адреса кэша Duo** (*nxd_nd_cache_ip_address_find*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-220">**Duo Cache IP Address Find** (*nxd_nd_cache_ip_address_find*)</span></span> |
| ![Значок включения протокола ICMP Duo](./media/user-guide/netx-events/image57.png)    | <span data-ttu-id="63ec4-222">**Включение протокола ICMP Duo** (*nxd_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-222">**Duo ICMP Enable** (*nxd_icmp_enable*)</span></span> |
| ![Значок проверки связи ICMP Duo для IPv6](./media/user-guide/netx-events/image58.png)    | <span data-ttu-id="63ec4-224">**Проверка связи ICMP Duo для IPv6** (*nxd_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-224">**Duo ICMP IPv6 Ping** (*nxd_icmp_ping*)</span></span> |
| ![Значок поиска максимального размера полезных данных в IP-адресе типа Duo](./media/user-guide/netx-events/image59.png)    | <span data-ttu-id="63ec4-226">**Поиск максимального размера полезных данных в IP-адресе типа Duo** (*nx_max_payload_size_find*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-226">**Duo IP Max Payload Size Find** (*nx_max_payload_size_find*)</span></span> |
| ![Значок отправки необработанного пакета IP-адреса типа Duo](./media/user-guide/netx-events/image60.png)    | <span data-ttu-id="63ec4-228">**Отправка необработанного пакета IP-адреса типа Duo** (*nxd_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-228">**Duo IP Raw Packet Send** (*nxd_ip_raw_packet_send*)</span></span> |
| ![Значок добавления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image61.png)    | <span data-ttu-id="63ec4-230">**Добавление стандартного маршрутизатора для IPv6 типа Duo** (*nxd_ipv6_default_router_add*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-230">**Duo IPv6 Default Router Add** (*nxd_ipv6_default_router_add*)</span></span> |
| ![Значок удаления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image62.png)    | <span data-ttu-id="63ec4-232">**Удаление стандартного маршрутизатора для IPv6 типа Duo** (*nxd_ipv6_default_router_delete)*</span><span class="sxs-lookup"><span data-stu-id="63ec4-232">**Duo IPv6 Default Router Delete** (*nxd_ipv6_default_router_delete)*</span></span> |
| ![Значок включения IPv6 типа Duo](./media/user-guide/netx-events/image63.png)    | <span data-ttu-id="63ec4-234">**Включение IPv6 типа Duo** (*nxd_ipv6_enable)*</span><span class="sxs-lookup"><span data-stu-id="63ec4-234">**Duo IPv6 Enable** (*nxd_ipv6_enable)*</span></span> |
| ![Значок получения глобального адреса IPv6 типа Duo](./media/user-guide/netx-events/image64.png)    | <span data-ttu-id="63ec4-236">**Получение глобального адреса IPv6 типа Duo** (*nxd_ipv6_global_address_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-236">**Duo IPv6 Global Address Get** (*nxd_ipv6_global_address_get*)</span></span> |
| ![Значок установки глобальных адресов IPv6 типа Duo](./media/user-guide/netx-events/image65.png)    | <span data-ttu-id="63ec4-238">**Набор глобальных адресов IPv6 типа Duo** (*nxd_ipv6_global_address_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-238">**Duo IPv6 Global Address Set** (*nxd_ipv6_global_address_set*)</span></span> |
| ![Значок инициации процесса Dad для IPv6 типа Duo](./media/user-guide/netx-events/image66.png)    | <span data-ttu-id="63ec4-240">**Инициация процесса Dad для IPv6 типа Duo** (*nxd_ipv6_initiate_dad_process*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-240">**Duo IPv6 Initiate Dad Process** (*nxd_ipv6_initiate_dad_process*)</span></span> |
| ![Значок получения адреса интерфейса IPv6 типа Duo](./media/user-guide/netx-events/image67.png)    | <span data-ttu-id="63ec4-242">**Получение адреса интерфейса IPv6 типа Duo** (*nxd_ipv6_interface_address_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-242">**Duo IPv6 Interface Address Get** (*nxd_ipv6_interface_address_get*)</span></span> |
| ![Значок набора адресов интерфейса IPv6 типа Duo](./media/user-guide/netx-events/image68.png)    | <span data-ttu-id="63ec4-244">**Набор адресов интерфейса IPv6 типа Duo** (*nxd_ipv6_interface_address_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-244">**Duo IPv6 Interface Address Set** (*nxd_ipv6_interface_address_set*)</span></span> |
| ![Значок получения ссылки на локальный адрес IPv6 типа Duo](./media/user-guide/netx-events/image69.png)    | <span data-ttu-id="63ec4-246">**Получение локального адреса канала связи IPv6 типа Duo** (*nxd_ipv6_linklocal_address_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-246">**Duo IPv6 Link Local Address Get** (*nxd_ipv6_linklocal_address_get*)</span></span> |
| ![Значок набора локальных адресов канала связи IPv6 типа Duo](./media/user-guide/netx-events/image70.png)    | <span data-ttu-id="63ec4-248">**Набор локальных адресов канала связи IPv6 типа Duo** (*nxd_ipv6_linklocal_address_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-248">**Duo IPv6 Link Local Address Set** (*nxd_ipv6_linklocal_address_set*)</span></span> |
| ![Значок отправки необработанного пакета IPv6 типа Duo](./media/user-guide/netx-events/image71.png)    | <span data-ttu-id="63ec4-250">**Отправка необработанного пакета IPv6 типа Duo** (*nxd_ipv6_raw_packet_send)*</span><span class="sxs-lookup"><span data-stu-id="63ec4-250">**Duo IPv6 Raw Packet Send** (*nxd_ipv6_raw_packet_send)*</span></span> |
| ![Значок получения сведений об одноранговом узле сокета TCP Duo](./media/user-guide/netx-events/image72.png)    | <span data-ttu-id="63ec4-252">**Получение сведений об одноранговом узле сокета TCP Duo** (*nxd_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-252">**Duo TCP Socket Peer Info Get** (*nxd_tcp_socket_peer_info_get*)</span></span> |
| ![Значок интерфейса установки сокетов TCP Duo](./media/user-guide/netx-events/image73.png)    | <span data-ttu-id="63ec4-254">**Интерфейс установки сокетов TCP Duo** (*nxd_tcp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-254">**Duo TCP Socket Set Interface** (*nxd_tcp_socket_set_interface*)</span></span> |
| ![Значок отправки UDP-сокета Duo](./media/user-guide/netx-events/image74.png)    | <span data-ttu-id="63ec4-256">**Отправка UDP-сокета Duo** (*nxd_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-256">**Duo UDP Socket Send** (*nxd_udp_socket_send*)</span></span> |
| ![Значок интерфейса установки сокетов UDP Duo](./media/user-guide/netx-events/image75.png)    | <span data-ttu-id="63ec4-258">**Интерфейс набора сокетов UDP Duo** (*nxd_udp_socket_set_interface*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-258">**Duo UDP Socket Set Interface** (*nxd_udp_socket_set_interface*)</span></span> |
| ![Значок извлечения источника UDP Duo](./media/user-guide/netx-events/image76.png)    | <span data-ttu-id="63ec4-260">**Извлечение источника UDP Duo** (*nxd_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-260">**Duo UDP Source Extract** (*nxd_udp_source_extract*)</span></span> |
| ![Значок включения ICMP](./media/user-guide/netx-events/image77.png)    | <span data-ttu-id="63ec4-262">**Включение ICMP** (*nx_icmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-262">**ICMP Enable** (*nx_icmp_enable*)</span></span> |
| ![Значок получения сведений об ICMP](./media/user-guide/netx-events/image78.png)    | <span data-ttu-id="63ec4-264">**Получение сведений об ICMP** (*nx_icmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-264">**ICMP Information Get** (*nx_icmp_info_get*)</span></span> |
| ![Значок проверки связи ICMP](./media/user-guide/netx-events/image79.png)    | <span data-ttu-id="63ec4-266">**Проверка связи ICMP** (*nx_icmp_ping*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-266">**ICMP Ping** (*nx_icmp_ping*)</span></span> |
| ![Значок включения IGMP](./media/user-guide/netx-events/image80.png)    | <span data-ttu-id="63ec4-268">**Включение протокола IGMP** (*nx_igmp_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-268">**IGMP Enable** (*nx_igmp_enable*)</span></span> |
| ![Значок получения сведений об IGMP](./media/user-guide/netx-events/image81.png)    | <span data-ttu-id="63ec4-270">**Получение сведений об IGMP** (*nx_icmp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-270">**IGMP Information Get** (*nx_igmp_info_get*)</span></span> |
| ![Значок отключения замыкания на себя для IGMP](./media/user-guide/netx-events/image82.png)    | <span data-ttu-id="63ec4-272">**Отключение замыкания на себя для IGMP** (*nx_igmp_loopback_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-272">**IGMP Loopback Disable** (*nx_igmp_loopback_disable*)</span></span> |
| ![Значок включения замыкания на себя для IGMP](./media/user-guide/netx-events/image83.png)    | <span data-ttu-id="63ec4-274">**Включение замыкания на себя для IGMP** (*nx_igmp_loopback_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-274">**IGMP Loopback Enable** (*nx_igmp_loopback_enable*)</span></span> |
| ![Значок подключения IGMP к многоадресной рассылке](./media/user-guide/netx-events/image84.png)    | <span data-ttu-id="63ec4-276">**Подключение IGMP к многоадресной рассылке** (*nx_igmp_multicast_join*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-276">**IGMP Multicast Join** (*nx_igmp_multicast_join*)</span></span> |
| ![Значок отключения IGMP от многоадресной рассылки](./media/user-guide/netx-events/image85.png)    | <span data-ttu-id="63ec4-278">**Отключение IGMP от многоадресной рассылки** (*nx_igmp_multicast_leave*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-278">**IGMP Multicast Leave** (*nx_igmp_multicast_leave*)</span></span> |
| ![Значок уведомления об изменении IP-адреса](./media/user-guide/netx-events/image86.png)    | <span data-ttu-id="63ec4-280">**Уведомление об изменении IP-адреса** (*nx_ip_address_change_notify*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-280">**IP Address Change Notify** (*nx_ip_address_change_notify*)</span></span> |
| ![Значок получения IP-адреса](./media/user-guide/netx-events/image87.png)    | <span data-ttu-id="63ec4-282">**Получение IP-адреса** (*nx_ip_address_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-282">**IP Address Get** (*nx_ip_address_get*)</span></span> |
| ![Значок набора IP-адресов](./media/user-guide/netx-events/image88.png)    | <span data-ttu-id="63ec4-284">**Набор IP-адресов** (*nx_ip_address_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-284">**IP Address Set** (*nx_ip_address_set*)</span></span> |
| ![Значок создания IP-адреса](./media/user-guide/netx-events/image89.png)    | <span data-ttu-id="63ec4-286">**Создание IP-адреса** (*nx_ip_create*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-286">**IP Create** (*nx_ip_create*)</span></span> |
| ![Значок удаления IP-адреса](./media/user-guide/netx-events/image90.png)    | <span data-ttu-id="63ec4-288">**Удаление IP-адреса** (*nx_ip_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-288">**IP Delete** (*nx_ip_delete*)</span></span> |
| ![Значок команды прямого доступа к драйверу протокола IP](./media/user-guide/netx-events/image91.png)    | <span data-ttu-id="63ec4-290">**Команда прямого доступа к драйверу протокола IP** (*nx_ip_driver_direct_command*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-290">**IP Driver Direct Command** (*nx_ip_driver_direct_command*)</span></span> |
| ![Значок отключения IP-пересылки](./media/user-guide/netx-events/image92.png)    | <span data-ttu-id="63ec4-292">**Отключение IP-пересылки** (*nx_ip_forwarding_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-292">**IP Forwarding Disable** (*nx_ip_forwarding_disable*)</span></span> |
| ![Значок включения IP-пересылки](./media/user-guide/netx-events/image93.png)    | <span data-ttu-id="63ec4-294">**Включение IP-пересылки** (*nx_ip_forwarding_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-294">**IP Forwarding Enable** (*nx_ip_forwarding_enable*)</span></span> |
| ![Значок отключения фрагмента IP](./media/user-guide/netx-events/image94.png)    | <span data-ttu-id="63ec4-296">**Отключение фрагмента IP** (*nx_ip_fragment_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-296">**IP Fragment Disable** (*nx_ip_fragment_disable*)</span></span> |
| ![Значок включения фрагмента IP](./media/user-guide/netx-events/image95.png)    | <span data-ttu-id="63ec4-298">**Включение фрагмента IP** (*nx_ip_fragment_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-298">**IP Fragment Enable** (*nx_ip_fragment_enable*)</span></span>  |
| ![Значок набора адресов шлюза IP](./media/user-guide/netx-events/image96.png)    | <span data-ttu-id="63ec4-300">**Набор адресов шлюза IP** (*nx_ip_gateway_address_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-300">**IP Gateway Address Set** (*nx_ip_gateway_address_set*)</span></span> |
| ![Значок получения сведений об IP](./media/user-guide/netx-events/image97.png)    | <span data-ttu-id="63ec4-302">**Получение сведений об IP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-302">**IP Information Get** (*nx_ip_info_get*)</span></span> |
| ![Значок подключения интерфейса IP](./media/user-guide/netx-events/image98.png)    | <span data-ttu-id="63ec4-304">**Подключение интерфейса IP** (*nx_ip_interface_attach*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-304">**IP Interface Attach** (*nx_ip_interface_attach*)</span></span> |
| ![Значок получения сведений об интерфейсе IP](./media/user-guide/netx-events/image99.png)    | <span data-ttu-id="63ec4-306">**Получение сведений об интерфейсе IP** (*nx_ip_interface_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-306">**IP Interface Info Get** (*nx_ip_interface_info_get*)</span></span> |
| ![Значок отключения необработанных пакетов IP](./media/user-guide/netx-events/image100.png)    | <span data-ttu-id="63ec4-308">**Отключение необработанных пакетов IP** (*nx_ip_raw_packet_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-308">**IP Raw Packet Disable** (*nx_ip_raw_packet_disable*)</span></span> |
| ![Значок включения необработанных пакетов IP](./media/user-guide/netx-events/image101.png)    | <span data-ttu-id="63ec4-310">**Включение необработанных пакетов IP** (*nx_ip_raw_packet_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-310">**IP Raw Packet Enable** (*nx_ip_raw_packet_enable*)</span></span> |
| ![Значок получения необработанных пакетов IP](./media/user-guide/netx-events/image102.png)    | <span data-ttu-id="63ec4-312">**Получение необработанных пакетов IP** (*nx_ip_raw_packet_receive*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-312">**IP Raw Packet Receive** (*nx_ip_raw_packet_receive*)</span></span> |
| ![Значок отправки необработанного пакета IP](./media/user-guide/netx-events/image103.png)    | <span data-ttu-id="63ec4-314">**Отправка необработанных пакетов IP** (*nxd_ip_raw_packet_send*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-314">**IP Raw Packet Send** (*nx_ip_raw_packet_send*)</span></span> |
| ![Значок добавления статического маршрута IP](./media/user-guide/netx-events/image104.png)    | <span data-ttu-id="63ec4-316">**Добавление статического маршрута IP** (*nx_ip_static_route_add*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-316">**IP Static Route Add** (*nx_ip_static_route_add*)</span></span> |
| ![Значок удаления статического маршрута IP](./media/user-guide/netx-events/image105.png)    | <span data-ttu-id="63ec4-318">**Удаление статического маршрута IP** (*nx_ip_static_route_add*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-318">**IP Static Route Delete** (*nx_ip_static_route_delete)*</span></span> |
| ![Значок проверки состояния IP](./media/user-guide/netx-events/image106.png)    | <span data-ttu-id="63ec4-320">**Проверка состояния IP** (*nx_ip_status_check*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-320">**IP Status Check** (*nx_ip_status_check*)</span></span>|
| ![Значок включения IPSEC](./media/user-guide/netx-events/image107.png)    | <span data-ttu-id="63ec4-322">**Включение IPSEC** (*nx_ipsec_enable)*</span><span class="sxs-lookup"><span data-stu-id="63ec4-322">**IPSEC Enable** (*nx_ipsec_enable)*</span></span> |
| ![Значок выделения пакетов](./media/user-guide/netx-events/image108.png)    | <span data-ttu-id="63ec4-324">**Выделение пакетов** (*nx_packet_allocate*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-324">**Packet Allocate** (*nx_packet_allocate*)</span></span> |
| ![Значок копирования пакета](./media/user-guide/netx-events/image109.png)    | <span data-ttu-id="63ec4-326">**Копирование пакета** (*nx_packet_copy*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-326">**Packet Copy** (*nx_packet_copy*)</span></span> |
| ![Значок добавления пакетных данных](./media/user-guide/netx-events/image110.png)    | <span data-ttu-id="63ec4-328">**Добавление данных пакета** (*nx_packet_data_append*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-328">**Packet Data Append** (*nx_packet_data_append*)</span></span> |
| ![Значок смещения при извлечении данных пакетов](./media/user-guide/netx-events/image111.png)    | <span data-ttu-id="63ec4-330">**Смещение при извлечении данных пакета** (*nx_packet_data_extract_offset*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-330">**Packet Data Extract Offset** (*nx_packet_data_extract_offset*)</span></span> |
| ![Значок извлечения данных пакета](./media/user-guide/netx-events/image112.png)    | <span data-ttu-id="63ec4-332">**Извлечение данных пакета** (*nx_packet_data_retrieve*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-332">**Packet Data Retrieve** (*nx_packet_data_retrieve*)</span></span> |
| ![Значок получения длины пакета](./media/user-guide/netx-events/image113.png)    | <span data-ttu-id="63ec4-334">**Получение длины пакета** (*nx_packet_length_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-334">**Packet Length Get** (*nx_packet_length_get*)</span></span> |
| ![Значок создания пула пакетов](./media/user-guide/netx-events/image114.png)    | <span data-ttu-id="63ec4-336">**Создание пула пакетов** (*nx_packet_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-336">**Packet Pool Create** (*nx_packet_pool_create*)</span></span> |
| ![Значок удаления пула пакетов](./media/user-guide/netx-events/image115.png)    | <span data-ttu-id="63ec4-338">**Удаление пула пакетов** (*nx_packet_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-338">**Packet Pool Delete** (*nx_packet_pool_delete*)</span></span> |
| ![Значок получения сведений о пуле пакетов](./media/user-guide/netx-events/image116.png)    | <span data-ttu-id="63ec4-340">**Получение сведений о пуле пакетов** (*nx_packet_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-340">**Packet Pool Information Get** (*nx_packet_pool_info_get*)</span></span> |
| ![Значок выпуска пакета](./media/user-guide/netx-events/image117.png)    | <span data-ttu-id="63ec4-342">**Выпуск пакета** (*nx_packet_release*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-342">**Packet Release** (*nx_packet_release*)</span></span> |
| ![Значок выпуска передачи пакетов](./media/user-guide/netx-events/image118.png)    | <span data-ttu-id="63ec4-344">**Выпуск передачи пакетов** (*nx_packet_transmit_release*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-344">**Packet Transmit Release** (*nx_packet_transmit_release*)</span></span> |
| ![Значок отключения RARP](./media/user-guide/netx-events/image119.png)    | <span data-ttu-id="63ec4-346">**Отключение RARP** (*nx_rarp_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-346">**RARP Disable** (*nx_rarp_disable*)</span></span> |
| ![Значок включения RARP](./media/user-guide/netx-events/image120.png)    | <span data-ttu-id="63ec4-348">**Включение RARP** (*nx_rarp_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-348">**RARP Enable** (*nx_rarp_enable*)</span></span> |
| ![Значок получения сведений о RARP](./media/user-guide/netx-events/image121.png)    | <span data-ttu-id="63ec4-350">**Получение сведений о RARP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-350">**RARP Information Get** (*nx_rarp_info_get*)</span></span> |
| ![Значок инициализации системы](./media/user-guide/netx-events/image122.png)    | <span data-ttu-id="63ec4-352">**Инициализация системы** (*nx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-352">**System Initialize** (*nx_system_initialize*)</span></span> |
| ![Значок привязки к сокету клиента TCP](./media/user-guide/netx-events/image123.png)    | <span data-ttu-id="63ec4-354">**Привязка к сокету клиента TCP** (*nx_tcp_client_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-354">**TCP Client Socket Bind** (*nx_tcp_client_socket_bind*)</span></span> |
| ![Значок подключения к сокету клиента TCP](./media/user-guide/netx-events/image124.png)    | <span data-ttu-id="63ec4-356">**Подключение к сокету клиента TCP** (*nx_tcp_client_socket_connect*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-356">**TCP Client Socket Connect** (*nx_tcp_client_socket_connect*)</span></span> |
| ![Значок получения порта сокета клиента TCP](./media/user-guide/netx-events/image125.png)    | <span data-ttu-id="63ec4-358">**Получение порта сокета клиента TCP** (*nx_tcp_client_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-358">**TCP Client Socket Port Get** (*nx_tcp_client_socket_port_get*)</span></span> |
| ![Значок отмены привязки сокета клиента TCP](./media/user-guide/netx-events/image126.png)    | <span data-ttu-id="63ec4-360">**Отмена привязки сокета клиента TCP** (*nx_tcp_client_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-360">**TCP Client Socket Unbind** (*nx_tcp_client_socket_unbind*)</span></span> |
| ![Значок включения TCP](./media/user-guide/netx-events/image127.png)    | <span data-ttu-id="63ec4-362">**Включение TCP** (*nx_tcp_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-362">**TCP Enable** (*nx_tcp_enable*)</span></span> |
| ![Значок поиска свободных портов TCP](./media/user-guide/netx-events/image128.png)    | <span data-ttu-id="63ec4-364">**Поиск свободных TCP-портов** (*nx_tcp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-364">**TCP Free Port Find** (*nx_tcp_free_port_find*)</span></span> |
| ![Значок получения сведений о TCP](./media/user-guide/netx-events/image129.png)    | <span data-ttu-id="63ec4-366">**Получение сведений о TCP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-366">**TCP Information Get** (*nx_tcp_info_get*)</span></span> |
| ![Значок принятия сокета сервера TCP](./media/user-guide/netx-events/image130.png)    | <span data-ttu-id="63ec4-368">**Принятие сокета сервера TCP** (*nx_tcp_server_socket_accept*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-368">**TCP Server Socket Accept** (*nx_tcp_server_socket_accept*)</span></span> |
| ![Значок прослушивания сокета сервера TCP](./media/user-guide/netx-events/image131.png)    | <span data-ttu-id="63ec4-370">**Прослушивание сокета сервера TCP** (*nx_tcp_server_socket_listen*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-370">**TCP Server Socket Listen** (*nx_tcp_server_socket_listen*)</span></span> |
| ![Значок повторного прослушивания сокета сервера TCP](./media/user-guide/netx-events/image132.png)    | <span data-ttu-id="63ec4-372">**Повторное прослушивание сокета сервера TCP** (*nx_tcp_server_socket_relisten*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-372">**TCP Server Socket Relisten** (*nx_tcp_server_socket_relisten*)</span></span> |
| ![Значок отклонения сокета сервера TCP](./media/user-guide/netx-events/image133.png)    | <span data-ttu-id="63ec4-374">**Отклонение сокета сервера TCP** (*nx_tcp_server_socket_unaccept*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-374">**TCP Server Socket Unaccept** (*nx_tcp_server_socket_unaccept*)</span></span> |
| ![Значок отсутствия прослушивания сервера TCP](./media/user-guide/netx-events/image134.png)    | <span data-ttu-id="63ec4-376">**Отсутствие прослушивания сокета сервера TCP** (*nx_tcp_server_socket_relisten*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-376">**TCP Server Socket Unlisten** (*nx_tcp_server_socket_unlisten*)</span></span> |
| ![Значок доступных байтов сокета TCP](./media/user-guide/netx-events/image135.png)    | <span data-ttu-id="63ec4-378">**Доступные байты сокета TCP** (*nx_tcp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-378">**TCP Socket Bytes Available** (*nx_tcp_socket_bytes_available*)</span></span> |
| ![Значок создания сокета TCP](./media/user-guide/netx-events/image136.png)    | <span data-ttu-id="63ec4-380">**Создание сокета TCP** (*nx_tcp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-380">**TCP Socket Create** (*nx_tcp_socket_create*)</span></span> |
| ![Значок удаления сокета TCP](./media/user-guide/netx-events/image137.png)    | <span data-ttu-id="63ec4-382">**Удаление сокета TCP** (*nx_tcp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-382">**TCP Socket Delete** (*nx_tcp_socket_delete*)</span></span> |
| ![Значок отключения сокета TCP](./media/user-guide/netx-events/image138.png)    | <span data-ttu-id="63ec4-384">**Отключение сокета TCP** (*nx_tcp_socket_disconnect*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-384">**TCP Socket Disconnect** (*nx_tcp_socket_disconnect*)</span></span> |
| ![Значок получения сведений о сокете TCP](./media/user-guide/netx-events/image139.png)    | <span data-ttu-id="63ec4-386">**Получение сведений о сокете TCP** (*nx_tcp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-386">**TCP Socket Information Get** (*nx_tcp_socket_info_get*)</span></span> |
| ![Значок получения MSS для сокета TCP](./media/user-guide/netx-events/image140.png)    | <span data-ttu-id="63ec4-388">**Получение MSS для сокета TCP** (*nx_tcp_socket_mss_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-388">**TCP Socket MSS Get** (*nx_tcp_socket_mss_get*)</span></span> |
| ![Значок получения значения MSS однорангового узла сокета](./media/user-guide/netx-events/image141.png)    | <span data-ttu-id="63ec4-390">**Получение для однорангового узла MSS сокета TCP** (*nx_tcp_socket_mss_peer_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-390">**TCP Socket MSS Peer Get** (*nx_tcp_socket_mss_peer_get*)</span></span> |
| ![Значок установки MSS для сокета TCP](./media/user-guide/netx-events/image142.png)    | <span data-ttu-id="63ec4-392">**Установка MSS для сокета TCP** (*nx_tcp_socket_mss_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-392">**TCP Socket MSS Set** (*nx_tcp_socket_mss_set*)</span></span> |
| ![Значок получения для однорангового узла сведений о сокете TCP](./media/user-guide/netx-events/image143.png)    | <span data-ttu-id="63ec4-394">**Получение для однорангового узла сведений о сокете TCP** (*nx_tcp_socket_peer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-394">**TCP Socket Peer Info Get** (*nx_tcp_socket_peer_info_get*)</span></span> |
| ![Значок получения сокета TCP](./media/user-guide/netx-events/image144.png)    | <span data-ttu-id="63ec4-396">**Получение сокета TCP** (*nx_tcp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-396">**TCP Socket Receive** (*nx_tcp_socket_receive*)</span></span> |
| ![Значок уведомления о получении сокета TCP](./media/user-guide/netx-events/image145.png)    | <span data-ttu-id="63ec4-398">**Уведомление о получении сокета TCP** (*nx_tcp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-398">**TCP Socket Receive Notify** (*nx_tcp_socket_receive_notify*)</span></span> |
| ![Значок отправки сокета TCP](./media/user-guide/netx-events/image146.png)    | <span data-ttu-id="63ec4-400">**Отправка сокета TCP** (*nx_tcp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-400">**TCP Socket Send** (*nx_tcp_socket_send*)</span></span> |
| ![Значок пребывания в состоянии ожидания для сокета TCP](./media/user-guide/netx-events/image147.png)    | <span data-ttu-id="63ec4-402">**Состояние ожидания сокета TCP** (*nx_tcp_socket_state_wait*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-402">**TCP Socket State Wait** (*nx_tcp_socket_state_wait*)</span></span> |
| ![Значок настройки передачи сокета TCP](./media/user-guide/netx-events/image148.png)    | <span data-ttu-id="63ec4-404">**Настройка передачи сокета TCP** (*nx_tcp_socket_transmit_configure*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-404">**TCP Socket Transmit Configure** (*nx_tcp_socket_transmit_configure*)</span></span> |
| ![Значок установки уведомления об обновлении окна сокета TCP](./media/user-guide/netx-events/image149.png)    | <span data-ttu-id="63ec4-406">**Установка уведомления об обновлении окна сокета TCP** (*nx_tcp_socket_window_update_notify_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-406">**TCP Socket Window Update Notify Set** (*nx_tcp_socket_window_update_notify_set*)</span></span>  |
| ![Значок включения UDP](./media/user-guide/netx-events/image150.png)    | <span data-ttu-id="63ec4-408">**Включение UDP** (*nx_udp_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-408">**UDP Enable** (*nx_udp_enable*)</span></span> |
| ![Значок поиска свободных портов UDP](./media/user-guide/netx-events/image151.png)    | <span data-ttu-id="63ec4-410">**Поиск свободных портов UDP** (*nx_tcp_free_port_find*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-410">**UDP Free Port Find** (*nx_udp_free_port_find*)</span></span> |
| ![Значок получения сведений о UDP](./media/user-guide/netx-events/image152.png)    | <span data-ttu-id="63ec4-412">**Получение сведений о UDP** (*nx_arp_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-412">**UDP Information Get** (*nx_udp_info_get*)</span></span> |
| ![Значок привязки UDP-сокета](./media/user-guide/netx-events/image153.png)    | <span data-ttu-id="63ec4-414">**Привязка UDP-сокета** (*nx_udp_socket_bind*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-414">**UDP Socket Bind** (*nx_udp_socket_bind*)</span></span> |
| ![Значок доступных байтов UDP-сокета](./media/user-guide/netx-events/image154.png)    | <span data-ttu-id="63ec4-416">**Доступные байты UDP-сокета** (*nx_tcp_socket_bytes_available*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-416">**UDP Socket Bytes Available** (*nx_udp_socket_bytes_available*)</span></span> |
| ![Значок отключения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image155.png)    | <span data-ttu-id="63ec4-418">**Отключение контрольной суммы UDP-сокета** (*nx_udp_socket_checksum_disable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-418">**UDP Socket Checksum Disable** (*nx_udp_socket_checksum_disable*)</span></span> |
| ![Значок включения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image156.png)    | <span data-ttu-id="63ec4-420">**Включение контрольной суммы UDP-сокета** (*nx_udp_socket_checksum_enable*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-420">**UDP Socket Checksum Enable** *(nx_udp_socket_checksum_enable)*</span></span> |
| ![Значок создания UDP-сокета](./media/user-guide/netx-events/image157.png)    | <span data-ttu-id="63ec4-422">**Создание UDP-сокета** (*nx_udp_socket_create*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-422">**UDP Socket Create** (*nx_udp_socket_create*)</span></span> |
| ![Значок удаления UDP-сокета](./media/user-guide/netx-events/image158.png)    | <span data-ttu-id="63ec4-424">**Удаление UDP-сокета** (*nx_udp_socket_delete*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-424">**UDP Socket Delete** (*nx_udp_socket_delete*)</span></span> |
| ![Значок получения сведений о сокете UDP](./media/user-guide/netx-events/image159.png)    | <span data-ttu-id="63ec4-426">**Получение сведений о сокете UDP** (*nx_tcp_socket_info_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-426">**UDP Socket Information Get** (*nx_udp_socket_info_get*)</span></span> |
| ![Значок набора интерфейсов UDP-сокета](./media/user-guide/netx-events/image160.png)    | <span data-ttu-id="63ec4-428">**Набор интерфейсов UDP-сокета** (*nx_udp_socket_interface_set*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-428">**UDP Socket Interface Set** (*nx_udp_socket_interface_set*)</span></span> |
| ![Значок получения порта для UDP-сокета](./media/user-guide/netx-events/image161.png)    | <span data-ttu-id="63ec4-430">**Получение порта UDP-сокета** (*nx_udp_socket_port_get*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-430">**UDP Socket Port Get** (*nx_udp_socket_port_get*)</span></span> |
| ![Значок получения UDP-сокета](./media/user-guide/netx-events/image162.png)    | <span data-ttu-id="63ec4-432">**Получение UDP-сокета** (*nx_udp_socket_receive*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-432">**UDP Socket Receive** (*nx_udp_socket_receive*)</span></span> |
| ![Значок уведомления о получении UDP-сокета](./media/user-guide/netx-events/image163.png)    | <span data-ttu-id="63ec4-434">**Уведомление о получении UDP-сокета** (*nx_tcp_socket_receive_notify*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-434">**UDP Socket Receive Notify** (*nx_udp_socket_receive_notify*)</span></span> |
| ![Значок отправки UDP-сокета](./media/user-guide/netx-events/image164.png)    | <span data-ttu-id="63ec4-436">**Отправка UDP-сокета** (*nx_udp_socket_send*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-436">**UDP Socket Send** (*nx_udp_socket_send*)</span></span> |
| ![Значок отмены привязки для UDP-сокета](./media/user-guide/netx-events/image165.png)    | <span data-ttu-id="63ec4-438">**Отмена привязки UDP-сокета** (*nx_udp_socket_unbind*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-438">**UDP Socket Unbind** (*nx_udp_socket_unbind*)</span></span> |
| ![Значок извлечения источника UDP](./media/user-guide/netx-events/image166.png)    | <span data-ttu-id="63ec4-440">**Извлечение источника UDP** (*nxd_udp_source_extract*)</span><span class="sxs-lookup"><span data-stu-id="63ec4-440">**UDP Source Extract** (*nx_udp_source_extract*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="63ec4-441">Описания событий</span><span class="sxs-lookup"><span data-stu-id="63ec4-441">Event Descriptions</span></span>

<span data-ttu-id="63ec4-442">На следующих страницах описаны события трассировки NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-442">The following pages describe the NetX Trace Events.</span></span>

### <a name="internal-arp-request-receive"></a><span data-ttu-id="63ec4-443">Получение внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-443">Internal ARP Request Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="63ec4-444">Получение внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-444">Internal ARP request receive</span></span>

<span data-ttu-id="63ec4-445">**Значок** ![Значок получения внутренних запросов ARP](./media/user-guide/netx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-445">**Icon** ![Internal ARP request receive icon](./media/user-guide/netx-events/image1.png)</span></span>

<span data-ttu-id="63ec4-446">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-446">**Description**</span></span>

<span data-ttu-id="63ec4-447">Это событие представляет собой событие получения внутренних запросов ARP для NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-447">This event represents an internal NetX ARP request receive event.</span></span>

<span data-ttu-id="63ec4-448">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-448">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-449">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-449">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-450">Поле сведений 2. Исходный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-450">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="63ec4-451">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-451">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-452">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-452">Info Field 4: Not used</span></span>

### <a name="internal-arp-request-send"></a><span data-ttu-id="63ec4-453">Отправка внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-453">Internal ARP Request Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="63ec4-454">Отправка внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-454">Internal ARP request send</span></span>

<span data-ttu-id="63ec4-455">**Значок** ![Значок отправки внутренних запросов ARP](./media/user-guide/netx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-455">**Icon** ![Internal ARP request send icon](./media/user-guide/netx-events/image2.png)</span></span>

<span data-ttu-id="63ec4-456">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-456">**Description**</span></span>

<span data-ttu-id="63ec4-457">Это событие представляет собой событие отправки внутренних запросов ARP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-457">This event represents an internal NetX ARP request send event.</span></span>

<span data-ttu-id="63ec4-458">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-458">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-459">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-459">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-460">Поле сведений 2. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-460">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="63ec4-461">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-461">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-462">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-462">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-receive"></a><span data-ttu-id="63ec4-463">Получение внутреннего ответа ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-463">Internal ARP Response Receive</span></span> 

#### <a name="internal-arp-request-receive"></a><span data-ttu-id="63ec4-464">Получение внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-464">Internal ARP request receive</span></span>

<span data-ttu-id="63ec4-465">**Значок** ![Значок получения внутренних запросов ARP](./media/user-guide/netx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-465">**Icon** ![The Internal ARP request receive icon](./media/user-guide/netx-events/image3.png)</span></span>

<span data-ttu-id="63ec4-466">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-466">**Description**</span></span>

<span data-ttu-id="63ec4-467">Это событие представляет собой событие получения ответа на внутренние запросы ARP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-467">This event represents an internal NetX ARP response receive event.</span></span>

<span data-ttu-id="63ec4-468">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-468">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-469">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-469">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-470">Поле сведений 2. Исходный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-470">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="63ec4-471">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-471">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-472">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-472">Info Field 4: Not used</span></span>

### <a name="internal-arp-response-send"></a><span data-ttu-id="63ec4-473">Отправка внутреннего ответа ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-473">Internal ARP Response Send</span></span> 

#### <a name="internal-arp-request-send"></a><span data-ttu-id="63ec4-474">Отправка внутренних запросов ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-474">Internal ARP request send</span></span>

<span data-ttu-id="63ec4-475">**Значок** ![Значок отправки внутренних запросов ARP](./media/user-guide/netx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-475">**Icon** ![The Internal ARP request send icon](./media/user-guide/netx-events/image4.png)</span></span>

<span data-ttu-id="63ec4-476">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-476">**Description**</span></span>

<span data-ttu-id="63ec4-477">Это событие представляет собой событие ответа на внутренние запросы ARP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-477">This event represents an internal NetX response send event.</span></span>

<span data-ttu-id="63ec4-478">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-478">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-479">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-479">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-480">Поле сведений 2. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-480">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="63ec4-481">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-481">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-482">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-482">Info Field 4: Not used</span></span>

### <a name="internal-icmp-receive"></a><span data-ttu-id="63ec4-483">Получение внутреннего протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-483">Internal ICMP Receive</span></span> 

#### <a name="internal-icmp-receive"></a><span data-ttu-id="63ec4-484">Получение внутреннего протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-484">Internal ICMP receive</span></span>

<span data-ttu-id="63ec4-485">**Значок** ![Значок получения внутреннего протокола ICMP](./media/user-guide/netx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-485">**Icon** ![Internal I C M P receive icon](./media/user-guide/netx-events/image5.png)</span></span>

<span data-ttu-id="63ec4-486">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-486">**Description**</span></span>

<span data-ttu-id="63ec4-487">Это событие представляет собой событие получения внутреннего протокола ICMP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-487">This event represents an internal NetX ICMP receive event.</span></span>

<span data-ttu-id="63ec4-488">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-488">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-489">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-489">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-490">Поле сведений 2. Исходный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-490">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="63ec4-491">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-491">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-492">Поле сведений 4. Поле "0 слов из" для заголовка ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-492">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-icmp-send"></a><span data-ttu-id="63ec4-493">Отправка внутреннего протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-493">Internal ICMP Send</span></span> 

#### <a name="internal-icmp-send"></a><span data-ttu-id="63ec4-494">Отправка внутреннего протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-494">Internal ICMP send</span></span>

<span data-ttu-id="63ec4-495">**Значок** ![Значок отправки внутреннего протокола ICMP](./media/user-guide/netx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-495">**Icon** ![Internal I C M P send icon](./media/user-guide/netx-events/image6.png)</span></span>

<span data-ttu-id="63ec4-496">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-496">**Description**</span></span>

<span data-ttu-id="63ec4-497">Это событие представляет собой событие отправки внутреннего протокола ICMP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-497">This event represents an internal NetX ICMP send event.</span></span>

<span data-ttu-id="63ec4-498">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-498">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-499">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-499">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-500">Поле сведений 2. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-500">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="63ec4-501">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-501">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-502">Поле сведений 4. Поле "0 слов из" для заголовка ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-502">Info Field 4: Word 0 of ICMP header</span></span>

### <a name="internal-igmp-receive"></a><span data-ttu-id="63ec4-503">Получение внутреннего протокола IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-503">Internal IGMP Receive</span></span> 

#### <a name="internal-igmp-receive"></a><span data-ttu-id="63ec4-504">Получение внутреннего протокола IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-504">Internal IGMP receive</span></span>

<span data-ttu-id="63ec4-505">**Значок** ![Значок получения внутреннего протокола IGMP](./media/user-guide/netx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-505">**Icon** ![Internal I G M P receive icon](./media/user-guide/netx-events/image7.png)</span></span>

<span data-ttu-id="63ec4-506">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-506">**Description**</span></span>

<span data-ttu-id="63ec4-507">Это событие представляет собой событие получения внутреннего протокола IGMP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-507">This event represents an internal NetX IGMP receive event.</span></span>

<span data-ttu-id="63ec4-508">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-508">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-509">Поле сведений 1. Указатель на IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-509">Info Field 1: IP Pointer</span></span>
- <span data-ttu-id="63ec4-510">Поле сведений 2. Исходный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-510">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="63ec4-511">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-511">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-512">Поле сведений 4. Поле "0 слов из" для заголовка IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-512">Info Field 4: Word 0 of IGMP header</span></span>

### <a name="internal-ip-receive"></a><span data-ttu-id="63ec4-513">Получение внутреннего IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-513">Internal IP Receive</span></span> 

#### <a name="internal-ip-receive"></a><span data-ttu-id="63ec4-514">Получение внутреннего IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-514">Internal IP receive</span></span>

<span data-ttu-id="63ec4-515">**Значок** ![Значок получения внутреннего IP](./media/user-guide/netx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-515">**Icon** ![Internal I P receive icon](./media/user-guide/netx-events/image8.png)</span></span>

<span data-ttu-id="63ec4-516">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-516">**Description**</span></span>

<span data-ttu-id="63ec4-517">Это событие представляет собой событие получения внутреннего протокола IP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-517">This event represents an internal NetX IP receive event.</span></span>

<span data-ttu-id="63ec4-518">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-518">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-519">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-519">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-520">Поле сведений 2. Исходный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-520">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="63ec4-521">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-521">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-522">Поле сведений 4. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-522">Info Field 4: Packet length</span></span>

### <a name="internal-ip-send"></a><span data-ttu-id="63ec4-523">Отправка внутреннего IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-523">Internal IP Send</span></span>

#### <a name="internal-ip-send"></a><span data-ttu-id="63ec4-524">Отправка внутреннего IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-524">Internal IP send</span></span>

<span data-ttu-id="63ec4-525">**Значок** ![Значок отправки внутреннего IP](./media/user-guide/netx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-525">**Icon** ![Internal I P send icon](./media/user-guide/netx-events/image9.png)</span></span>

<span data-ttu-id="63ec4-526">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-526">**Description**</span></span>

<span data-ttu-id="63ec4-527">Это событие представляет собой событие отправки внутреннего протокола IP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-527">This event represents an internal NetX IP send event.</span></span>

<span data-ttu-id="63ec4-528">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-528">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-529">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-529">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-530">Поле сведений 2. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-530">Info Field 2: Destination IP address</span></span>
- <span data-ttu-id="63ec4-531">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-531">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-532">Поле сведений 4. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-532">Info Field 4: Packet length</span></span>

### <a name="internal-tcp-data-receive"></a><span data-ttu-id="63ec4-533">Получение данных по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-533">Internal TCP Data Receive</span></span> 

#### <a name="internal-tcp-data-receive"></a><span data-ttu-id="63ec4-534">Получение данных по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-534">Internal TCP Data Receive</span></span>

<span data-ttu-id="63ec4-535">**Значок** ![Значок получения данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-535">**Icon** ![Internal T C P data receive icon](./media/user-guide/netx-events/image10.png)</span></span>

<span data-ttu-id="63ec4-536">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-536">**Description**</span></span>

<span data-ttu-id="63ec4-537">Это событие представляет собой событие получения данных по внутреннему протоколу TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-537">This event represents an internal NetX TCP data receive event.</span></span>

<span data-ttu-id="63ec4-538">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-538">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-539">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-539">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-540">Поле сведений 2. Исходный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-540">Info Field 2: Source IP address</span></span>
- <span data-ttu-id="63ec4-541">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-541">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-542">Поле сведений 4. Получение порядкового номера</span><span class="sxs-lookup"><span data-stu-id="63ec4-542">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-data-send"></a><span data-ttu-id="63ec4-543">Отправка данных по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-543">Internal TCP data send</span></span> 

#### <a name="internal-tcp-data-send"></a><span data-ttu-id="63ec4-544">Отправка данных по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-544">Internal TCP Data Send</span></span>

<span data-ttu-id="63ec4-545">**Значок** ![Значок отправки данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-545">**Icon** ![Internal T C P data send icon](./media/user-guide/netx-events/image11.png)</span></span>

<span data-ttu-id="63ec4-546">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-546">**Description**</span></span>

<span data-ttu-id="63ec4-547">Это событие представляет собой событие отправки данных по внутреннему протоколу TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-547">This event represents an internal NetX TCP data send event.</span></span>

<span data-ttu-id="63ec4-548">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-548">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-549">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-549">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-550">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-550">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-551">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-551">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-552">Поле сведений 4. Порядковый номер передачи</span><span class="sxs-lookup"><span data-stu-id="63ec4-552">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="63ec4-553">Получение флага FIN внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-553">Internal TCP FIN Receive</span></span> 

#### <a name="internal-tcp-fin-receive"></a><span data-ttu-id="63ec4-554">Получение флага FIN внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-554">Internal TCP fin receive</span></span>

<span data-ttu-id="63ec4-555">**Значок** ![Значок получения флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-555">**Icon** ![Internal T C P F I N receive icon](./media/user-guide/netx-events/image12.png)</span></span>

<span data-ttu-id="63ec4-556">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-556">**Description**</span></span>

<span data-ttu-id="63ec4-557">Это событие представляет собой событие получения флага FIN внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-557">This event represents an internal NetX TCP FIN receive event.</span></span>

<span data-ttu-id="63ec4-558">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-558">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-559">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-559">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-560">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-560">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-561">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-561">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-562">Поле сведений 4. Получение порядкового номера</span><span class="sxs-lookup"><span data-stu-id="63ec4-562">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-fin-send"></a><span data-ttu-id="63ec4-563">Отправка флага FIN внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-563">Internal TCP FIN Send</span></span> 

#### <a name="internal-tcp-fin-send"></a><span data-ttu-id="63ec4-564">Отправка флага FIN внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-564">Internal TCP fin send</span></span>

<span data-ttu-id="63ec4-565">**Значок** ![Значок отправки флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-565">**Icon** ![Internal T C P F I N send icon](./media/user-guide/netx-events/image13.png)</span></span>

<span data-ttu-id="63ec4-566">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-566">**Description**</span></span>

<span data-ttu-id="63ec4-567">Это событие представляет собой событие отправки флага FIN внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-567">This event represents an internal NetX TCP FIN send event.</span></span>

<span data-ttu-id="63ec4-568">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-568">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-569">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-569">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-570">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-570">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-571">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-571">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-572">Поле сведений 4. Порядковый номер передачи</span><span class="sxs-lookup"><span data-stu-id="63ec4-572">Info Field 4:Transmit sequence number</span></span>

### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="63ec4-573">Получение флага RST внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-573">Internal TCP RST Receive</span></span> 

#### <a name="internal-tcp-rst-receive"></a><span data-ttu-id="63ec4-574">Получение флага RST внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-574">Internal TCP RST receive</span></span>

<span data-ttu-id="63ec4-575">**Значок** ![Значок получения флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-575">**Icon** ![Internal T C P R S T receive icon](./media/user-guide/netx-events/image14.png)</span></span>

<span data-ttu-id="63ec4-576">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-576">**Description**</span></span>

<span data-ttu-id="63ec4-577">Это событие представляет собой событие получения сброса внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-577">This event represents an internal NetX TCP reset receive event.</span></span>

<span data-ttu-id="63ec4-578">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-578">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-579">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-579">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="63ec4-580">Поле сведений 2. Указатель на сокет.</span><span class="sxs-lookup"><span data-stu-id="63ec4-580">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="63ec4-581">Поле сведений 3. Указатель на пакет.</span><span class="sxs-lookup"><span data-stu-id="63ec4-581">Info Field 3: Pointer to packet.</span></span>
- <span data-ttu-id="63ec4-582">Поле сведений 4. Получение порядкового номера.</span><span class="sxs-lookup"><span data-stu-id="63ec4-582">Info Field 4: Receive sequence number.</span></span>

### <a name="internal-tcp-rst-send"></a><span data-ttu-id="63ec4-583">Отправка флага RST внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-583">Internal TCP RST Send</span></span> 

#### <a name="internal-tcp-rst-send"></a><span data-ttu-id="63ec4-584">Отправка флага RST внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-584">Internal TCP RST send</span></span>

<span data-ttu-id="63ec4-585">**Значок** ![Значок отправки флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-585">**Icon** ![Internal T C P R S T send icon](./media/user-guide/netx-events/image15.png)</span></span>

<span data-ttu-id="63ec4-586">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-586">**Description**</span></span>

<span data-ttu-id="63ec4-587">Это событие представляет собой событие отправки сброса внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-587">This event represents an internal NetX TCP reset send event.</span></span>

<span data-ttu-id="63ec4-588">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-588">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-589">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-589">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-590">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-590">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-591">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-591">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-592">Поле сведений 4. Порядковый номер передачи</span><span class="sxs-lookup"><span data-stu-id="63ec4-592">Info Field 4: Transmit sequence number</span></span>

### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="63ec4-593">Получение SYN внутреннего TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-593">Internal TCP SYN Receive</span></span> 

#### <a name="internal-tcp-syn-receive"></a><span data-ttu-id="63ec4-594">Получение SYN внутреннего TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-594">Internal TCP SYN receive</span></span>

<span data-ttu-id="63ec4-595">**Значок** ![Значок получения SYN внутреннего TCP](./media/user-guide/netx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-595">**Icon** ![Internal T C P S Y N receive icon](./media/user-guide/netx-events/image16.png)</span></span>

<span data-ttu-id="63ec4-596">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-596">**Description**</span></span>

<span data-ttu-id="63ec4-597">Это событие представляет собой событие получения SYN внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-597">This event represents an internal NetX TCP SYN receive event.</span></span>

<span data-ttu-id="63ec4-598">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-598">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-599">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-599">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-600">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-600">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-601">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-601">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-602">Поле сведений 4. Получение порядкового номера</span><span class="sxs-lookup"><span data-stu-id="63ec4-602">Info Field 4: Receive sequence number</span></span>

### <a name="internal-tcp-syn-send"></a><span data-ttu-id="63ec4-603">Отправка SYN внутреннего TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-603">Internal TCP SYN Send</span></span> 

#### <a name="internal-tcp-syn-send"></a><span data-ttu-id="63ec4-604">Отправка SYN внутреннего TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-604">Internal TCP SYN send</span></span>

<span data-ttu-id="63ec4-605">**Значок** ![Значок отправки SYN внутреннего TCP](./media/user-guide/netx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-605">**Icon** ![Internal T C P S Y N send icon](./media/user-guide/netx-events/image17.png)</span></span>

<span data-ttu-id="63ec4-606">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-606">**Description**</span></span>

<span data-ttu-id="63ec4-607">Это событие представляет собой событие отправки SYN внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-607">This event represents an internal NetX TCP SYN send event.</span></span>

<span data-ttu-id="63ec4-608">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="63ec4-608">Information Fields</span></span> 

- <span data-ttu-id="63ec4-609">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-609">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-610">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-610">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-611">Поле сведений 3. Указатель на пакет. Поле сведений 4. Порядковый номер передачи</span><span class="sxs-lookup"><span data-stu-id="63ec4-611">Info Field 3: Pointer to packet -Info Field 4: Transmit sequence number</span></span>

### <a name="internal-udp-receive"></a><span data-ttu-id="63ec4-612">Получение внутреннего протокола UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-612">Internal UDP Receive</span></span> 

#### <a name="internal-udp-receive"></a><span data-ttu-id="63ec4-613">Получение внутреннего протокола UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-613">Internal UDP receive</span></span>

<span data-ttu-id="63ec4-614">**Значок** ![Значок получения внутреннего протокола UDP](./media/user-guide/netx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-614">**Icon** ![Internal U D P receive icon](./media/user-guide/netx-events/image18.png)</span></span>

<span data-ttu-id="63ec4-615">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-615">**Description**</span></span>

<span data-ttu-id="63ec4-616">Это событие представляет собой событие получения внутреннего протокола UDP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-616">This event represents an internal NetX UDP receive event.</span></span>

<span data-ttu-id="63ec4-617">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-617">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-618">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-618">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-619">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-619">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-620">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-620">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-621">Поле сведений 4. Поле "0 слов из" для заголовка UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-621">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-udp-send"></a><span data-ttu-id="63ec4-622">Отправка внутреннего протокола UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-622">Internal UDP Send</span></span> 

#### <a name="internal-udp-send"></a><span data-ttu-id="63ec4-623">Отправка внутреннего протокола UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-623">Internal UDP send</span></span>

<span data-ttu-id="63ec4-624">**Значок** ![Значок отправки внутреннего протокола UDP](./media/user-guide/netx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-624">**Icon** ![Internal U D P send icon](./media/user-guide/netx-events/image19.png)</span></span>

<span data-ttu-id="63ec4-625">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-625">**Description**</span></span>

<span data-ttu-id="63ec4-626">Это событие представляет собой событие отправки внутреннего протокола UDP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-626">This event represents an internal NetX UDP send event.</span></span>

<span data-ttu-id="63ec4-627">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-627">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-628">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-628">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-629">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-629">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-630">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-630">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-631">Поле сведений 4. Поле "0 слов из" для заголовка UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-631">Info Field 4: Word 0 of UDP header</span></span>

### <a name="internal-rarp-receive"></a><span data-ttu-id="63ec4-632">Получение внутреннего протокола RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-632">Internal RARP Receive</span></span> 

#### <a name="internal-rarp-receive"></a><span data-ttu-id="63ec4-633">Получение внутреннего протокола RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-633">Internal RARP receive</span></span> 

<span data-ttu-id="63ec4-634">**Значок** ![Значок получения внутреннего протокола RARP](./media/user-guide/netx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-634">**Icon** ![Internal R A R P receive icon](./media/user-guide/netx-events/image20.png)</span></span>

<span data-ttu-id="63ec4-635">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-635">**Description**</span></span>

<span data-ttu-id="63ec4-636">Это событие представляет собой событие получения внутреннего протокола RARP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-636">This event represents an internal NetX RARP receive event.</span></span>

<span data-ttu-id="63ec4-637">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-637">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-638">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-638">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-639">Поле сведений 2. Целевой IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-639">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="63ec4-640">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-640">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-641">Поле сведений 4. Поле "1 слово из" для заголовка RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-641">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-rarp-send"></a><span data-ttu-id="63ec4-642">Отправка внутреннего протокола RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-642">Internal RARP Send</span></span> 

#### <a name="internal-rarp-send"></a><span data-ttu-id="63ec4-643">Отправка внутреннего протокола RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-643">Internal RARP send</span></span> 

<span data-ttu-id="63ec4-644">**Значок** ![Значок отправки внутреннего протокола RARP](./media/user-guide/netx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-644">**Icon** ![Internal R A R P send icon](./media/user-guide/netx-events/image21.png)</span></span>

<span data-ttu-id="63ec4-645">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-645">**Description**</span></span>

<span data-ttu-id="63ec4-646">Это событие представляет собой событие отправки внутреннего протокола RARP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-646">This event represents an internal NetX RARP send event.</span></span>

<span data-ttu-id="63ec4-647">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-647">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-648">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-648">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-649">Поле сведений 2. Целевой IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-649">Info Field 2: Target IP address</span></span>
- <span data-ttu-id="63ec4-650">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-650">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-651">Поле сведений 4. Поле "1 слово из" для заголовка RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-651">Info Field 4: Word 1 of RARP header</span></span>

### <a name="internal-tcp-retry"></a><span data-ttu-id="63ec4-652">Повторная попытка подключения по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-652">Internal TCP Retry</span></span> 

#### <a name="internal-tcp-retry"></a><span data-ttu-id="63ec4-653">Повторная попытка подключения по внутреннему протоколу TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-653">Internal TCP retry</span></span> 

<span data-ttu-id="63ec4-654">**Значок** ![Значок повторной попытки подключения по внутреннему протоколу TCP](./media/user-guide/netx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-654">**Icon** ![Internal T C P retry icon](./media/user-guide/netx-events/image22.png)</span></span>

<span data-ttu-id="63ec4-655">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-655">**Description**</span></span>

<span data-ttu-id="63ec4-656">Это событие представляет собой событие повторной попытки подключения по внутреннему протоколу TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-656">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="63ec4-657">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-657">**Information Fields**</span></span>
- <span data-ttu-id="63ec4-658">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-658">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-659">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-659">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-660">Поле сведений 3. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-660">Info Field 3: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-661">Поле сведений 4. Число повторных попыток</span><span class="sxs-lookup"><span data-stu-id="63ec4-661">Info Field 4: Number of retries</span></span>

### <a name="internal-tcp-state-change"></a><span data-ttu-id="63ec4-662">Изменение состояния внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-662">Internal TCP State Change</span></span> 

#### <a name="internal-tcp-state-change"></a><span data-ttu-id="63ec4-663">Изменение состояния внутреннего протокола TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-663">Internal TCP state change</span></span> 

<span data-ttu-id="63ec4-664">**Значок** ![Значок изменения состояния внутреннего протокола TCP](./media/user-guide/netx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-664">**Icon** ![Internal T C P state change icon](./media/user-guide/netx-events/image23.png)</span></span>

<span data-ttu-id="63ec4-665">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-665">**Description**</span></span>

<span data-ttu-id="63ec4-666">Это событие представляет собой событие изменения состояния внутреннего протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-666">This event represents an internal NetX TCP socket state change event.</span></span>

<span data-ttu-id="63ec4-667">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-667">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-668">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-668">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-669">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-669">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-670">Поле сведений 3. Предыдущее состояние</span><span class="sxs-lookup"><span data-stu-id="63ec4-670">Info Field 3: Previous state</span></span>
- <span data-ttu-id="63ec4-671">Поле сведений 4. Новое состояние</span><span class="sxs-lookup"><span data-stu-id="63ec4-671">Info Field 4: New state</span></span>

### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="63ec4-672">Отправка пакета внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-672">Internal I/O Driver Packet Send</span></span> 

#### <a name="internal-io-driver-packet-send"></a><span data-ttu-id="63ec4-673">Отправка пакета внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-673">Internal I/O driver packet send</span></span>

<span data-ttu-id="63ec4-674">**Значок** ![Значок отправки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-674">**Icon** ![Internal I / O driver packet send icon](./media/user-guide/netx-events/image24.png)</span></span>

<span data-ttu-id="63ec4-675">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-675">**Description**</span></span>

<span data-ttu-id="63ec4-676">Это событие представляет собой событие отправки пакета внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-676">This event represents an internal NetX I/O driver packet send event.</span></span>

<span data-ttu-id="63ec4-677">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-677">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-678">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-678">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-679">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-679">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-680">Поле сведений 3. Размер пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-680">Info Field 3: Packet size</span></span>
- <span data-ttu-id="63ec4-681">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-681">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="63ec4-682">Инициализация внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-682">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="63ec4-683">Инициализация внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-683">Internal I/O driver initialize</span></span>

<span data-ttu-id="63ec4-684">**Значок** ![Значок инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-684">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/netx-events/image25.png)</span></span>

<span data-ttu-id="63ec4-685">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-685">**Description**</span></span>

<span data-ttu-id="63ec4-686">Это событие представляет собой событие инициализации внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-686">This event represents an internal NetX I/O driver initialize event.</span></span>

<span data-ttu-id="63ec4-687">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-687">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-688">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-688">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="63ec4-689">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-689">Info Field 2: Not used.</span></span>
- <span data-ttu-id="63ec4-690">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-690">Info Field 3: Not used.</span></span>
- <span data-ttu-id="63ec4-691">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-691">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="63ec4-692">Включение ссылки на внутренний драйвер устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-692">Internal I/O Driver Link Enable</span></span> 

#### <a name="internal-io-driver-link-enable"></a><span data-ttu-id="63ec4-693">Включение ссылки на внутренний драйвер устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-693">Internal I/O driver link enable</span></span>

<span data-ttu-id="63ec4-694">**Значок** ![Значок включения ссылки на внутренний драйвер устройств ввода-вывода](./media/user-guide/netx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-694">**Icon** ![Internal I / O driver link enable icon](./media/user-guide/netx-events/image26.png)</span></span>

<span data-ttu-id="63ec4-695">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-695">**Description**</span></span>

<span data-ttu-id="63ec4-696">Это событие представляет собой событие включения ссылки на внутренний драйвер устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-696">This event represents an internal NetX I/O driver link enable event.</span></span>

<span data-ttu-id="63ec4-697">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-697">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-698">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-698">Info Field 1: Pointer to the IP instance.</span></span>
- <span data-ttu-id="63ec4-699">Поле сведений 2. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-699">Info Field 2: Not used.</span></span>
- <span data-ttu-id="63ec4-700">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-700">Info Field 3: Not used.</span></span>
- <span data-ttu-id="63ec4-701">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-701">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="63ec4-702">Отключение ссылки на внутренний драйвер устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-702">Internal I/O Driver Link Disable</span></span> 

#### <a name="internal-io-driver-link-disable"></a><span data-ttu-id="63ec4-703">Отключение ссылки на внутренний драйвер устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-703">Internal I/O driver link disable</span></span>

<span data-ttu-id="63ec4-704">**Значок** ![Значок отключения ссылки на внутренний драйвер устройств ввода-вывода](./media/user-guide/netx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-704">**Icon** ![Internal I / O driver link disable icon](./media/user-guide/netx-events/image27.png)</span></span>

<span data-ttu-id="63ec4-705">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-705">**Description**</span></span>

<span data-ttu-id="63ec4-706">Это событие представляет собой событие отключения ссылки на внутренний драйвер устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-706">This event represents an internal NetX I/O driver link disable event.</span></span>

<span data-ttu-id="63ec4-707">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-707">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-708">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-708">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-709">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-709">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-710">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-710">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-711">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-711">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="63ec4-712">Широковещательная рассылка пакета внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-712">Internal I/O Driver Packet Broadcast</span></span> 

#### <a name="internal-io-driver-packet-broadcast"></a><span data-ttu-id="63ec4-713">Широковещательная рассылка пакета внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-713">Internal I/O driver packet broadcast</span></span>

<span data-ttu-id="63ec4-714">**Значок** ![Значок широковещательной рассылки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-714">**Icon** ![Internal I / O driver packet broadcast icon](./media/user-guide/netx-events/image28.png)</span></span>

<span data-ttu-id="63ec4-715">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-715">**Description**</span></span>

<span data-ttu-id="63ec4-716">Это событие представляет собой событие широковещательной рассылки пакета внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-716">This event represents an internal NetX I/O driver packet broadcast event.</span></span>

<span data-ttu-id="63ec4-717">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-717">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-718">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-718">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-719">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-719">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-720">Поле сведений 3. Размер пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-720">Info Field 3: Packet size</span></span>
- <span data-ttu-id="63ec4-721">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-721">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="63ec4-722">Отправка ARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-722">Internal I/O Driver ARP Send</span></span> 

#### <a name="internal-io-driver-arp-send"></a><span data-ttu-id="63ec4-723">Отправка ARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-723">Internal I/O driver ARP send</span></span>

<span data-ttu-id="63ec4-724">**Значок** ![Значок отправки ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-724">**Icon** ![Internal I / O driver ARP send icon](./media/user-guide/netx-events/image29.png)</span></span>

<span data-ttu-id="63ec4-725">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-725">**Description**</span></span>

<span data-ttu-id="63ec4-726">Это событие представляет собой событие отправки ARP для внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-726">This event represents an internal NetX I/O driver ARP send event.</span></span>

<span data-ttu-id="63ec4-727">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-727">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-728">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-728">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-729">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-729">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-730">Поле сведений 3. Размер пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-730">Info Field 3: Packet size</span></span>
- <span data-ttu-id="63ec4-731">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-731">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="63ec4-732">Отправка ответа ARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-732">Internal I/O Driver ARP Response Send</span></span> 

#### <a name="internal-io-driver-arp-response-send"></a><span data-ttu-id="63ec4-733">Отправка ответа ARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-733">Internal I/O driver ARP response send</span></span>

<span data-ttu-id="63ec4-734">**Значок** ![Значок отправки ответа ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-734">**Icon** ![Internal I / O driver ARP response send icon](./media/user-guide/netx-events/image30.png)</span></span>

<span data-ttu-id="63ec4-735">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-735">**Description**</span></span>

<span data-ttu-id="63ec4-736">Это событие представляет собой событие отправки ответа ARP для внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-736">This event represents an internal NetX I/O driver ARP response send event.</span></span>

<span data-ttu-id="63ec4-737">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-737">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-738">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-738">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-739">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-739">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-740">Поле сведений 3. Размер пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-740">Info Field 3: Packet size</span></span>
- <span data-ttu-id="63ec4-741">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-741">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="63ec4-742">Отправка RARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-742">Internal I/O Driver RARP Send</span></span> 

#### <a name="internal-io-driver-rarp-send"></a><span data-ttu-id="63ec4-743">Отправка RARP для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-743">Internal I/O driver RARP send</span></span>

<span data-ttu-id="63ec4-744">**Значок** ![Значок отправки RARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-744">**Icon** ![Internal I / O driver RARP send icon](./media/user-guide/netx-events/image31.png)</span></span>

<span data-ttu-id="63ec4-745">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-745">**Description**</span></span>

<span data-ttu-id="63ec4-746">Это событие представляет собой событие отправки RARP для внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-746">This event represents an internal NetX I/O driver RARP send event.</span></span>

<span data-ttu-id="63ec4-747">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-747">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-748">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-748">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-749">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-749">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-750">Поле сведений 3. Размер пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-750">Info Field 3: Packet size</span></span>
- <span data-ttu-id="63ec4-751">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-751">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="63ec4-752">Подключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-752">Internal I/O Driver Multicast Join</span></span> 

#### <a name="internal-io-driver-multicast-join"></a><span data-ttu-id="63ec4-753">Подключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-753">Internal I/O driver multicast join</span></span>

<span data-ttu-id="63ec4-754">**Значок** ![Значок подключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-754">**Icon** ![Internal I / O driver multicast join icon](./media/user-guide/netx-events/image32.png)</span></span>

<span data-ttu-id="63ec4-755">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-755">**Description**</span></span>

<span data-ttu-id="63ec4-756">Это событие представляет собой событие подключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-756">This event represents an internal NetX I/O driver multicast join event.</span></span>

<span data-ttu-id="63ec4-757">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-757">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-758">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-758">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-759">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-759">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-760">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-760">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-761">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-761">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="63ec4-762">Отключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-762">Internal I/O Driver Multicast Leave</span></span> 

#### <a name="internal-io-driver-multicast-leave"></a><span data-ttu-id="63ec4-763">Отключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-763">Internal I/O driver multicast leave</span></span>

<span data-ttu-id="63ec4-764">**Значок** ![Значок отключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-764">**Icon** ![Internal I / O driver multicast leave icon](./media/user-guide/netx-events/image33.png)</span></span>

<span data-ttu-id="63ec4-765">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-765">**Description**</span></span>

<span data-ttu-id="63ec4-766">Это событие представляет собой событие отключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-766">This event represents an internal NetX I/O driver multicast leave event.</span></span>

<span data-ttu-id="63ec4-767">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-767">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-768">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-768">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-769">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-769">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-770">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-770">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-771">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-771">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-status"></a><span data-ttu-id="63ec4-772">Получение состояния внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-772">Internal I/O Driver Get Status</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="63ec4-773">Получение состояния внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-773">Internal I/O driver get status</span></span>

<span data-ttu-id="63ec4-774">**Значок** ![Значок получения состояния внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-774">**Icon** ![Internal I / O driver get status icon](./media/user-guide/netx-events/image34.png)</span></span>

<span data-ttu-id="63ec4-775">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-775">**Description**</span></span>

<span data-ttu-id="63ec4-776">Это событие представляет собой событие получения состояния внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-776">This event represents an internal NetX I/O driver get status event.</span></span>

<span data-ttu-id="63ec4-777">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-777">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-778">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-778">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-779">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-779">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-780">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-780">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-781">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-781">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="63ec4-782">Получение скорости внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-782">Internal I/O Driver Get Speed</span></span> 

#### <a name="internal-io-driver-get-speed"></a><span data-ttu-id="63ec4-783">Получение скорости внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-783">Internal I/O driver get speed</span></span>

<span data-ttu-id="63ec4-784">**Значок** ![Значок получения скорости внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-784">**Icon** ![Internal I / O driver get speed icon](./media/user-guide/netx-events/image35.png)</span></span>

<span data-ttu-id="63ec4-785">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-785">**Description**</span></span>

<span data-ttu-id="63ec4-786">Это событие представляет собой событие получения сведений о скорости получения внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-786">This event represents an internal NetX I/O driver get speed event.</span></span>

<span data-ttu-id="63ec4-787">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-787">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-788">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-788">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-789">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-789">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-790">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-790">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-791">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-791">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="63ec4-792">Получение дуплексного типа внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-792">Internal I/O Driver Get Duplex Type</span></span> 

#### <a name="internal-io-driver-get-duplex-type"></a><span data-ttu-id="63ec4-793">Получение дуплексного типа внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-793">Internal I/O driver get duplex type</span></span>

<span data-ttu-id="63ec4-794">**Значок** ![Значок получения дуплексного типа внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-794">**Icon** ![Internal I / O driver get duplex type icon](./media/user-guide/netx-events/image36.png)</span></span>

<span data-ttu-id="63ec4-795">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-795">**Description**</span></span>

<span data-ttu-id="63ec4-796">Это событие представляет собой событие получения дуплексного типа внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-796">This event represents an internal NetX I/O driver get duplex type event.</span></span>

<span data-ttu-id="63ec4-797">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-797">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-798">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-798">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-799">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-799">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-800">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-800">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-801">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-801">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="63ec4-802">Получение количества ошибок внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-802">Internal I/O Driver Get Error Count</span></span>

#### <a name="internal-io-driver-get-error-count"></a><span data-ttu-id="63ec4-803">Получение количества ошибок внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-803">Internal I/O driver get error count</span></span>

<span data-ttu-id="63ec4-804">**Значок** ![Значок получения количества ошибок внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-804">**Icon** ![Internal I / O driver get error count icon](./media/user-guide/netx-events/image37.png)</span></span>

<span data-ttu-id="63ec4-805">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-805">**Description**</span></span>

<span data-ttu-id="63ec4-806">Это событие представляет собой событие получения количества ошибок внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-806">This event represents an internal NetX I/O driver get error count event.</span></span>

<span data-ttu-id="63ec4-807">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-807">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-808">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-808">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-809">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-809">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-810">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-810">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-811">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-811">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="63ec4-812">Получение количества RX внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-812">Internal I/O Driver Get RX Count</span></span> 

#### <a name="internal-io-driver-get-rx-count"></a><span data-ttu-id="63ec4-813">Получение количества RX внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-813">Internal I/O driver get RX count</span></span>

<span data-ttu-id="63ec4-814">**Значок** ![Значок получения количества RX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-814">**Icon** ![Internal I / O driver get RX count icon](./media/user-guide/netx-events/image38.png)</span></span>

<span data-ttu-id="63ec4-815">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-815">**Description**</span></span>

<span data-ttu-id="63ec4-816">Это событие представляет собой событие получения количества RX внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-816">This event represents an internal NetX I/O driver get RX count event.</span></span>

<span data-ttu-id="63ec4-817">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-817">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-818">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-818">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-819">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-819">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-820">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-820">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-821">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-821">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="63ec4-822">Получение количества TX внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-822">Internal I/O Driver Get TX Count</span></span> 

#### <a name="internal-io-driver-get-tx-count"></a><span data-ttu-id="63ec4-823">Получение количества TX внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-823">Internal I/O driver get TX count</span></span>

<span data-ttu-id="63ec4-824">**Значок** ![Значок получения количества TX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-824">**Icon** ![Internal I / O driver get T X count icon](./media/user-guide/netx-events/image39.png)</span></span>

<span data-ttu-id="63ec4-825">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-825">**Description**</span></span>

<span data-ttu-id="63ec4-826">Это событие представляет собой событие получения количества TX внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-826">This event represents an internal NetX I/O driver get TX count event.</span></span>

<span data-ttu-id="63ec4-827">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-827">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-828">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-828">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-829">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-829">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-830">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-830">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-831">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-831">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="63ec4-832">Получение ошибок выделения внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-832">Internal I/O Driver Get Allocation Errors</span></span> 

#### <a name="internal-io-driver-get-allocation-errors"></a><span data-ttu-id="63ec4-833">Получение ошибок выделения внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-833">Internal I/O driver get allocation errors</span></span>

<span data-ttu-id="63ec4-834">**Значок** ![Значок получения ошибок выделения внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-834">**Icon** ![Internal I / O driver get allocation errors icon](./media/user-guide/netx-events/image40.png)</span></span>

<span data-ttu-id="63ec4-835">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-835">**Description**</span></span>

<span data-ttu-id="63ec4-836">Это событие представляет собой событие получения ошибок выделения внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-836">This event represents an internal NetX I/O driver get allocation errors event.</span></span>

<span data-ttu-id="63ec4-837">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-837">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-838">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-838">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-839">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-839">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-840">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-840">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-841">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-841">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="63ec4-842">Отмена инициализации внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-842">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="63ec4-843">Отмена инициализации внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-843">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="63ec4-844">**Значок** ![Значок отмены инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-844">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/netx-events/image41.png)</span></span>

<span data-ttu-id="63ec4-845">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-845">**Description**</span></span>

<span data-ttu-id="63ec4-846">Это событие представляет собой событие отмены инициализации внутреннего драйвера устройств ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-846">This event represents an internal NetX I/O driver un-initialize event.</span></span>

<span data-ttu-id="63ec4-847">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-847">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-848">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-848">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-849">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-849">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-850">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-850">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-851">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-851">Info Field 4: Not used</span></span>

### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="63ec4-852">Отложенная обработка внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-852">Internal I/O Driver Deferred Processing</span></span> 

#### <a name="internal-io-driver-deferred-processing"></a><span data-ttu-id="63ec4-853">Отложенная обработка внутреннего драйвера устройств ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="63ec4-853">Internal I/O driver deferred processing</span></span> 

<span data-ttu-id="63ec4-854">**Значок** ![Значок отложенной обработки внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-854">**Icon** ![Internal I / O driver deferred processing icon](./media/user-guide/netx-events/image42.png)</span></span>

<span data-ttu-id="63ec4-855">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-855">**Description**</span></span>

<span data-ttu-id="63ec4-856">Это событие представляет собой событие отложенной обработки внутреннего драйвера ввода-вывода в NetX.</span><span class="sxs-lookup"><span data-stu-id="63ec4-856">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="63ec4-857">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-857">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-858">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-858">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-859">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-859">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-860">Поле сведений 3. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-860">Info Field 3: Packet length</span></span>
- <span data-ttu-id="63ec4-861">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-861">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entries-invalidate"></a><span data-ttu-id="63ec4-862">Недействительность динамических записей ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-862">ARP Dynamic Entries Invalidate</span></span> 

#### <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="63ec4-863">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="63ec4-863">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="63ec4-864">**Значок** ![Значок недействительности динамических записей ARP](./media/user-guide/netx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-864">**Icon** ![A R P Dynamic Entries Invalidate icon](./media/user-guide/netx-events/image43.png)</span></span>

<span data-ttu-id="63ec4-865">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-865">**Description**</span></span>

<span data-ttu-id="63ec4-866">Это событие представляет собой событие недействительности всех динамических записей ARP через nx_arp_dynamic_entries_invalidate.</span><span class="sxs-lookup"><span data-stu-id="63ec4-866">This event represents invalidating all dynamic ARP entires via nx_arp_dynamic_entries_invalidate.</span></span>

<span data-ttu-id="63ec4-867">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-867">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-868">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-868">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-869">Поле сведений 2. Недействительные записи</span><span class="sxs-lookup"><span data-stu-id="63ec4-869">Info Field 2: Entries invalidated</span></span>
- <span data-ttu-id="63ec4-870">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-870">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-871">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-871">Info Field 4: Not used</span></span>

### <a name="arp-dynamic-entry-set"></a><span data-ttu-id="63ec4-872">Задание динамических записей ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-872">ARP Dynamic Entry Set</span></span> 

#### <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="63ec4-873">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-873">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="63ec4-874">**Значок** ![Значок набора динамических записей ARP](./media/user-guide/netx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-874">**Icon** ![A R P Dynamic Entry Set icon](./media/user-guide/netx-events/image44.png)</span></span>

<span data-ttu-id="63ec4-875">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-875">**Description**</span></span>

<span data-ttu-id="63ec4-876">Это событие представляет собой событие задания динамической записи ARP через nx_arp_dynamic_entry_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-876">This event represents setting a dynamic ARP entry via nx_arp_dynamic_entry_set.</span></span>

<span data-ttu-id="63ec4-877">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-877">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-878">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-878">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-879">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-879">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-880">Поле сведений 3. Физический адрес (MSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-880">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="63ec4-881">Поле сведений 4. Физический адрес (LSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-881">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-enable"></a><span data-ttu-id="63ec4-882">Включение ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-882">ARP Enable</span></span> 

#### <a name="nx_arp_enable"></a><span data-ttu-id="63ec4-883">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-883">nx_arp_enable</span></span>

<span data-ttu-id="63ec4-884">**Значок** ![Значок включения ARP](./media/user-guide/netx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-884">**Icon** ![A R P enable icon](./media/user-guide/netx-events/image45.png)</span></span>

<span data-ttu-id="63ec4-885">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-885">**Description**</span></span>

<span data-ttu-id="63ec4-886">Это событие представляет собой событие включения ARP через nx_arp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-886">This event represents enabling ARP via nx_arp_enable.</span></span>

<span data-ttu-id="63ec4-887">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-887">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-888">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-888">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-889">Поле сведений 2. Указатель на кэш ЦП ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-889">Info Field 2: ARP cache memory pointer</span></span>
- <span data-ttu-id="63ec4-890">Поле сведений 3. Размер кэша ЦП ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-890">Info Field 3: ARP cache memory size</span></span>
- <span data-ttu-id="63ec4-891">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-891">Info Field 4: Not used</span></span>

### <a name="arp-gratuitous-send"></a><span data-ttu-id="63ec4-892">Необязательная отправка ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-892">ARP Gratuitous Send</span></span> 

#### <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="63ec4-893">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-893">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="63ec4-894">**Значок** ![Значок необязательной отправки ARP](./media/user-guide/netx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-894">**Icon** ![A R P gratuitous send icon](./media/user-guide/netx-events/image46.png)</span></span>

<span data-ttu-id="63ec4-895">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-895">**Description**</span></span>

<span data-ttu-id="63ec4-896">Это событие представляет собой событие необязательной отправки ARP через nx_arp_gratuitous_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-896">This event represents a gratuitous ARP send via nx_arp_gratuitous_send.</span></span>

<span data-ttu-id="63ec4-897">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-897">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-898">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-898">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-899">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-899">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-900">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-900">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-901">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-901">Info Field 4: Not used</span></span>

### <a name="arp-hardware-address-find"></a><span data-ttu-id="63ec4-902">Поиск адреса оборудования ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-902">ARP Hardware Address Find</span></span> 

#### <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="63ec4-903">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="63ec4-903">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="63ec4-904">**Значок** ![Значок поиска адреса оборудования ARP](./media/user-guide/netx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-904">**Icon** ![A R P Hardware Address Find icon](./media/user-guide/netx-events/image47.png)</span></span>

<span data-ttu-id="63ec4-905">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-905">**Description**</span></span>

<span data-ttu-id="63ec4-906">Это событие представляет собой событие поиска физического адреса с помощью nx_arp_hardware_address_find.</span><span class="sxs-lookup"><span data-stu-id="63ec4-906">This event represents finding a physical address via nx_arp_hardware_address_find.</span></span>

<span data-ttu-id="63ec4-907">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-907">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-908">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-908">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-909">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-909">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-910">Поле сведений 3. Физический адрес (MSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-910">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="63ec4-911">Поле сведений 4. Физический адрес (LSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-911">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-information-get"></a><span data-ttu-id="63ec4-912">Получение сведений об ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-912">ARP Information Get</span></span> 

#### <a name="nx_arp_info_get"></a><span data-ttu-id="63ec4-913">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-913">nx_arp_info_get</span></span>

<span data-ttu-id="63ec4-914">**Значок** ![Значок получения сведений об ARP](./media/user-guide/netx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-914">**Icon** ![A R P informition get icon](./media/user-guide/netx-events/image48.png)</span></span>

<span data-ttu-id="63ec4-915">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-915">**Description**</span></span>

<span data-ttu-id="63ec4-916">Это событие представляет собой событие получения сведений об ARP с помощью nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-916">This event represents getting information via nx_arp_info_get.</span></span>

<span data-ttu-id="63ec4-917">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-917">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-918">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-918">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-919">Поле сведений 2. Отправка ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-919">Info Field 2: ARPs sent</span></span>
- <span data-ttu-id="63ec4-920">Поле сведений 3. Отклики ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-920">Info Field 3: ARP responses</span></span>
- <span data-ttu-id="63ec4-921">Поле сведений 4. Количество полученных ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-921">Info Field 4: ARPs received</span></span>

### <a name="arp-ip-address-find"></a><span data-ttu-id="63ec4-922">Поиск IP-адреса ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-922">ARP IP Address Find</span></span> 

#### <a name="nx_arp_ip_address_find"></a><span data-ttu-id="63ec4-923">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="63ec4-923">nx_arp_ip_address_find</span></span>

<span data-ttu-id="63ec4-924">**Значок** ![Значок поиска IP-адреса ARP](./media/user-guide/netx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-924">**Icon** ![A R P I P address find icon](./media/user-guide/netx-events/image49.png)</span></span>

<span data-ttu-id="63ec4-925">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-925">**Description**</span></span>

<span data-ttu-id="63ec4-926">Это событие представляет собой событие поиска IP-адреса, связанного с физическим адресом, переданным через nx_arp_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="63ec4-926">This event represents finding an IP address associated with the supplied physical address via nx_arp_ip_address_find.</span></span>

<span data-ttu-id="63ec4-927">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-927">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-928">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-928">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-929">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-929">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-930">Поле сведений 3. Физический адрес (MSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-930">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="63ec4-931">Поле сведений 4. Физический адрес (LSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-931">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entry-create"></a><span data-ttu-id="63ec4-932">Создание статической записи ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-932">ARP Static Entry Create</span></span> 

#### <a name="nx_arp_static_entry_create"></a><span data-ttu-id="63ec4-933">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="63ec4-933">nx_arp_static_entry_create</span></span>

<span data-ttu-id="63ec4-934">**Значок** ![Значок создания статической записи ARP](./media/user-guide/netx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-934">**Icon** ![A R P static entry create icon](./media/user-guide/netx-events/image50.png)</span></span>

<span data-ttu-id="63ec4-935">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-935">**Description**</span></span>

<span data-ttu-id="63ec4-936">Это событие представляет собой событие создания статической записи ARP через nx_arp_static_entry_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-936">This event represents creating a static ARP entry via nx_arp_static_entry_create.</span></span>

<span data-ttu-id="63ec4-937">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-937">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-938">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-938">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-939">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-939">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-940">Поле сведений 3. Физический адрес (MSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-940">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="63ec4-941">Поле сведений 4. Физический адрес (LSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-941">Info Field 4: Physical address (LSW)</span></span>

### <a name="arp-static-entries-delete"></a><span data-ttu-id="63ec4-942">Удаление статических записей ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-942">ARP Static Entries Delete</span></span> 

#### <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="63ec4-943">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-943">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="63ec4-944">**Значок** ![Значок удаления статических записей ARP](./media/user-guide/netx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-944">**Icon** ![A R P static entries delete icon](./media/user-guide/netx-events/image51.png)</span></span>

<span data-ttu-id="63ec4-945">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-945">**Description**</span></span>

<span data-ttu-id="63ec4-946">Это событие представляет собой событие удаления всех статических записей ARP через nx_arp_static_entries_delete.</span><span class="sxs-lookup"><span data-stu-id="63ec4-946">This event represents deleting all ARP static entries via nx_arp_static_entries_delete.</span></span>

<span data-ttu-id="63ec4-947">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-947">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-948">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-948">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-949">Поле сведений 2. Удаленные записи</span><span class="sxs-lookup"><span data-stu-id="63ec4-949">Info Field 2: Entries deleted</span></span>
- <span data-ttu-id="63ec4-950">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-950">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-951">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-951">Info Field 4: Not used</span></span>

### <a name="arp-static-entry-delete"></a><span data-ttu-id="63ec4-952">Удаление статической записи ARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-952">ARP Static Entry Delete</span></span> 

### <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="63ec4-953">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-953">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="63ec4-954">**Значок** ![Значок удаления статической записи ARP](./media/user-guide/netx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-954">**Icon** ![A R P static entry delete icon](./media/user-guide/netx-events/image52.png)</span></span>

<span data-ttu-id="63ec4-955">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-955">**Description**</span></span>

<span data-ttu-id="63ec4-956">Это событие представляет собой удаление статической записи ARP через nx_arp_static_entry_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-956">This event represents deleting a static ARP entry via nx_arp_static_entry_delete.</span></span>

<span data-ttu-id="63ec4-957">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-957">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-958">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-958">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-959">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-959">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-960">Поле сведений 3. Физический адрес (MSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-960">Info Field 3: Physical address (MSW)</span></span>
- <span data-ttu-id="63ec4-961">Поле сведений 4. Физический адрес (LSW)</span><span class="sxs-lookup"><span data-stu-id="63ec4-961">Info Field 4: Physical address (LSW)</span></span>

### <a name="duo-cache-entry-delete"></a><span data-ttu-id="63ec4-962">Удаление записи кэша Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-962">Duo Cache Entry Delete</span></span> 

#### <a name="nxd_und_cache_entry_delete"></a><span data-ttu-id="63ec4-963">nxd_und_cache_entry_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-963">nxd_und_cache_entry_delete</span></span>

<span data-ttu-id="63ec4-964">**Значок** ![Значок удаления записи кэша Duo](./media/user-guide/netx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-964">**Icon** ![Duo cache entry delete icon](./media/user-guide/netx-events/image53.png)</span></span>

<span data-ttu-id="63ec4-965">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-965">**Description**</span></span>

<span data-ttu-id="63ec4-966">Это событие представляет собой удаление записи в соседней таблице кэша с помощью nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-966">This event represents deleting an entry in the neighbor cache table via nx_udp_socket_create.</span></span>

<span data-ttu-id="63ec4-967">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-967">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-968">Поле сведений 1. Четвертое (наименее значимое) слово локального адреса канала связи IPv6 для удаления</span><span class="sxs-lookup"><span data-stu-id="63ec4-968">Info Field 1: Fourth (least significant) word of the IPv6 link local address to delete</span></span>
- <span data-ttu-id="63ec4-969">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-969">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-970">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-970">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-971">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-971">Info Field 4: Not used</span></span>

### <a name="duo-cache-entry-set"></a><span data-ttu-id="63ec4-972">Набор записей кэша Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-972">Duo Cache Entry Set</span></span> 

#### <a name="nxd_nd_cache_entry_set"></a><span data-ttu-id="63ec4-973">nxd_nd_cache_entry_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-973">nxd_nd_cache_entry_set</span></span>

<span data-ttu-id="63ec4-974">**Значок** ![Значок набора записей кэша Duo](./media/user-guide/netx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-974">**Icon** ![Duo cache entry set icon](./media/user-guide/netx-events/image54.png)</span></span>

<span data-ttu-id="63ec4-975">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-975">**Description**</span></span>

<span data-ttu-id="63ec4-976">Это событие представляет собой создание записи кэша и добавление ее в соседнюю таблицу кэша с помощью nxd_nd_cache_entry_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-976">This event represents creating a cache entry and adding to the neighbor cache table via nxd_nd_cache_entry_set.</span></span>

<span data-ttu-id="63ec4-977">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-977">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-978">Поле сведений 1. Четвертое (наименее значимое) слово адреса IPv6 для добавления</span><span class="sxs-lookup"><span data-stu-id="63ec4-978">Info Field 1: Fourth (least significant) word of the IPv6 address to add</span></span>
- <span data-ttu-id="63ec4-979">Поле сведений 2. Физический адрес msb</span><span class="sxs-lookup"><span data-stu-id="63ec4-979">Info Field 2: Physical address msb</span></span>
- <span data-ttu-id="63ec4-980">Поле сведений 3. Физический адрес lsb</span><span class="sxs-lookup"><span data-stu-id="63ec4-980">Info Field 3: Physical address lsb</span></span>
- <span data-ttu-id="63ec4-981">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-981">Info Field 4: Not used</span></span>

### <a name="duo-cache-invalidate"></a><span data-ttu-id="63ec4-982">Недействительность кэша Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-982">Duo Cache Invalidate</span></span> 

#### <a name="nxd_nd_cache_invalidate"></a><span data-ttu-id="63ec4-983">nxd_nd_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="63ec4-983">nxd_nd_cache_invalidate</span></span>

<span data-ttu-id="63ec4-984">**Значок** ![Значок недействительности кэша Duo](./media/user-guide/netx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-984">**Icon** ![Duo cache invalidate icon](./media/user-guide/netx-events/image55.png)</span></span>

<span data-ttu-id="63ec4-985">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-985">**Description**</span></span>

<span data-ttu-id="63ec4-986">Это событие представляет недействительность всей соседней таблицы кэша через nxd_nd_cache_invalidate.</span><span class="sxs-lookup"><span data-stu-id="63ec4-986">This event represents invalidating the entire neighbor cache table via nxd_nd_cache_invalidate.</span></span>

<span data-ttu-id="63ec4-987">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-987">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-988">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-988">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-989">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-989">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-990">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-990">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-991">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-991">Info Field 4: Not used</span></span>

### <a name="duo-cache-ip-address-find"></a><span data-ttu-id="63ec4-992">Поиск IP-адреса кэша Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-992">Duo Cache IP Address Find</span></span> 

#### <a name="nxd_nd_cache_ip_address_find"></a><span data-ttu-id="63ec4-993">nxd_nd_cache_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="63ec4-993">nxd_nd_cache_ip_address_find</span></span>

<span data-ttu-id="63ec4-994">**Значок** ![Значок поиска IP-адреса кэша Duo](./media/user-guide/netx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-994">**Icon** ![Duo cache I P address find icon](./media/user-guide/netx-events/image56.png)</span></span>

<span data-ttu-id="63ec4-995">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-995">**Description**</span></span>

<span data-ttu-id="63ec4-996">Это событие представляет собой получение IP-адреса, соответствующего физическому адресу, переданному из таблицы кэша с помощью nxd_nd_cache_ip_address_find.</span><span class="sxs-lookup"><span data-stu-id="63ec4-996">This event represents retrieving an IP address matching the supplied physical address from the cache table via nxd_nd_cache_ip_address_find.</span></span>

<span data-ttu-id="63ec4-997">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-997">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-998">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-998">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-999">Поле сведений 2. Четвертое (наименее значимое) слово адреса IPv6</span><span class="sxs-lookup"><span data-stu-id="63ec4-999">Info Field 2: Fourth (least significant) word of the IPv6 address</span></span>
- <span data-ttu-id="63ec4-1000">Поле сведений 3. Физический адрес msb</span><span class="sxs-lookup"><span data-stu-id="63ec4-1000">Info Field 3: Physical address msb</span></span>
- <span data-ttu-id="63ec4-1001">Поле сведений 4. Физический адрес lsb</span><span class="sxs-lookup"><span data-stu-id="63ec4-1001">Info Field 4: Physical address lsb</span></span>

### <a name="duo-icmp-enable"></a><span data-ttu-id="63ec4-1002">Включение протокола ICMP Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1002">Duo ICMP Enable</span></span> 

#### <a name="nxd_icmp_enable"></a><span data-ttu-id="63ec4-1003">nxd_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1003">nxd_icmp_enable</span></span>

<span data-ttu-id="63ec4-1004">**Значок** ![Значок включения протокола ICMP Duo](./media/user-guide/netx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1004">**Icon** ![Duo I C M P enable icon](./media/user-guide/netx-events/image57.png)</span></span>

<span data-ttu-id="63ec4-1005">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1005">**Description**</span></span>

<span data-ttu-id="63ec4-1006">Это событие представляет собой включение служб ICMPv4 и ICMPv6 на указанном экземпляре IP-адреса через nxd_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1006">This event represents ICMPv4 and ICMPv6 services being enabled on the specified IP instance via nxd_icmp_enable.</span></span>

<span data-ttu-id="63ec4-1007">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1007">**Information Fields**</span></span>
- <span data-ttu-id="63ec4-1008">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1008">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1009">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1009">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1010">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1010">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1011">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1011">Info Field 4: Not used</span></span>

### <a name="duo-icmp-ping"></a><span data-ttu-id="63ec4-1012">Проверка связи ICMP Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1012">Duo ICMP Ping</span></span> 

#### <a name="nxd_icmp_ping"></a><span data-ttu-id="63ec4-1013">nxd_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="63ec4-1013">nxd_icmp_ping</span></span>

<span data-ttu-id="63ec4-1014">**Значок** ![Значок проверки связи ICMP Duo](./media/user-guide/netx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1014">**Icon** ![Duo I C M P ping icon](./media/user-guide/netx-events/image58.png)</span></span>

<span data-ttu-id="63ec4-1015">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1015">**Description**</span></span>

<span data-ttu-id="63ec4-1016">Это событие представляет собой отправку запроса на проверку связи (эхо-запроса) узлу IPv6 через nxd_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1016">This event represents sending a ping (echo request) to an IPv6 host via nxd_icmp_ping.</span></span>

<span data-ttu-id="63ec4-1017">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1017">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1018">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1018">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1019">Поле сведений 2. Адрес IPv6</span><span class="sxs-lookup"><span data-stu-id="63ec4-1019">Info Field 2: IPv6 address</span></span>
- <span data-ttu-id="63ec4-1020">Поле сведений 3. Указатель на данные для проверки связи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1020">Info Field 3: Pointer to echo data</span></span>
- <span data-ttu-id="63ec4-1021">Поле сведений 4. Размер данных для проверки связи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1021">Info Field 4: Size of echo data</span></span>

### <a name="duo-ip-max-payload-size-find"></a><span data-ttu-id="63ec4-1022">Поиск максимального размера полезных данных для IP-адреса типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1022">Duo IP Max Payload Size Find</span></span> 

#### <a name="nxd_ip_max_payload_size"></a><span data-ttu-id="63ec4-1023">nxd_ip_max_payload_size</span><span class="sxs-lookup"><span data-stu-id="63ec4-1023">nxd_ip_max_payload_size</span></span>

<span data-ttu-id="63ec4-1024">**Значок** ![Значок поиска максимального размера полезных данных в IP-адресе типа Duo](./media/user-guide/netx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1024">**Icon** ![Duo I P max payload size find icon](./media/user-guide/netx-events/image59.png)</span></span>

<span data-ttu-id="63ec4-1025">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1025">**Description**</span></span>

<span data-ttu-id="63ec4-1026">Это событие позволяет вычислить максимальное количество полезных данных, которые может содержать указанный пакет, не требуя фрагментации.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1026">This event computes the max payload the specified packet can carry without requiring fragmentation.</span></span>

<span data-ttu-id="63ec4-1027">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1027">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1028">Поле сведений 1. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1028">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="63ec4-1029">Поле сведений 2. IP-адрес однорангового узла</span><span class="sxs-lookup"><span data-stu-id="63ec4-1029">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="63ec4-1030">Поле сведений 3. Поле сведений об одноранговом узле. Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1030">Info Field 3: Peer port Info Field 4: Not used</span></span>

### <a name="duo-ip-raw-packet-send"></a><span data-ttu-id="63ec4-1031">Отправка необработанных пакетов IP типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1031">Duo IP Raw Packet Send</span></span> 

#### <a name="nxd_ip_max_packet_send"></a><span data-ttu-id="63ec4-1032">nxd_ip_max_packet_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-1032">nxd_ip_max_packet_send</span></span>

<span data-ttu-id="63ec4-1033">**Значок** ![Значок отправки необработанного пакета IP-адреса типа Duo](./media/user-guide/netx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1033">**Icon** ![Duo I P raw packet send icon](./media/user-guide/netx-events/image60.png)</span></span>

<span data-ttu-id="63ec4-1034">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1034">**Description**</span></span>

<span data-ttu-id="63ec4-1035">Это событие представляет собой отправку необработанного пакета IP из указанного сетевого интерфейса в предоставленный IP-адрес пункта назначения с помощью nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1035">This event represents sending a raw IP packet out the specified network interface to the supplied IP destination addressvia nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="63ec4-1036">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1036">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1037">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1037">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1038">Поле сведений 2. Указатель на пакет, который нужно отправить</span><span class="sxs-lookup"><span data-stu-id="63ec4-1038">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="63ec4-1039">Поле сведений 3. Указатель на адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-1039">Info Field 3: Pointer to destination address</span></span>
- <span data-ttu-id="63ec4-1040">Поле сведений 4. Протокол пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1040">Info Field 4: Packet protocol</span></span>

### <a name="duo-ipv6-default-router-add"></a><span data-ttu-id="63ec4-1041">Добавление стандартного маршрутизатора для IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1041">Duo IPv6 Default Router Add</span></span> 

#### <a name="nxd_ipv6_default_router_add"></a><span data-ttu-id="63ec4-1042">nxd_ipv6_default_router_add</span><span class="sxs-lookup"><span data-stu-id="63ec4-1042">nxd_ipv6_default_router_add</span></span>

<span data-ttu-id="63ec4-1043">**Значок** ![Значок добавления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1043">**Icon** ![Duo I P v 6 default router add icon](./media/user-guide/netx-events/image61.png)</span></span>

<span data-ttu-id="63ec4-1044">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1044">**Description**</span></span>

<span data-ttu-id="63ec4-1045">Это событие представляет собой добавление маршрутизатора по умолчанию в таблицу маршрутизации IPv6 экземпляра IP с помощью nxd_ipv6_default_router_add.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1045">This event represents adding a default router to the IP instance's IPv6 routing table via nxd_ipv6_default_router_add.</span></span>

<span data-ttu-id="63ec4-1046">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1046">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1047">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1047">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="63ec4-1048">Поле сведений 2. Адрес сети назначения.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1048">Info Field 2: Destination Network address.</span></span>
- <span data-ttu-id="63ec4-1049">Поле сведений 3. Сведения о времени существования.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1049">Info Field 3: Life time information.</span></span>
- <span data-ttu-id="63ec4-1050">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1050">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-default-router-delete"></a><span data-ttu-id="63ec4-1051">Удаление стандартного маршрутизатора для IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1051">Duo IPv6 Default Router Delete</span></span> 

#### <a name="nxd_ipv6_default_router_delete"></a><span data-ttu-id="63ec4-1052">nxd_ipv6_default_router_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-1052">nxd_ipv6_default_router_delete</span></span>

<span data-ttu-id="63ec4-1053">**Значок** ![Значок удаления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1053">**Icon** ![Duo I P v 6 default router delete icon](./media/user-guide/netx-events/image62.png)</span></span>

<span data-ttu-id="63ec4-1054">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1054">**Description**</span></span>

<span data-ttu-id="63ec4-1055">Это событие представляет удаление маршрутизатора по умолчанию из таблицы маршрутизации IPv6 экземпляра IP с помощью nxd_ipv6_default_router_delete.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1055">This event represents removing a default router from the IP instance's IPv6 routing table via nxd_ipv6_default_router_delete.</span></span>

<span data-ttu-id="63ec4-1056">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1056">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1057">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1057">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="63ec4-1058">Поле сведений 2. Четвертое слово (наименее значимое) стандартного маршрутизатора адреса IPv6.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1058">Info Field 2: Fourth word (least significant) of the default router IPv6 address.</span></span>
- <span data-ttu-id="63ec4-1059">Поле сведений 3. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="63ec4-1060">Поле сведений 4. Не используется.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1060">Info Field 4: Not used.</span></span>

### <a name="duo-ipv6-enable"></a><span data-ttu-id="63ec4-1061">Включение протокола IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1061">Duo IPv6 Enable</span></span> 

#### <a name="nxd_ipv6_enable"></a><span data-ttu-id="63ec4-1062">nxd_ipv6_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1062">nxd_ipv6_enable</span></span>

<span data-ttu-id="63ec4-1063">**Значок** ![Значок включения IPv6 типа Duo](./media/user-guide/netx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1063">**Icon** ![Duo I P v 6 enable icon](./media/user-guide/netx-events/image63.png)</span></span>

<span data-ttu-id="63ec4-1064">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1064">**Description**</span></span>

<span data-ttu-id="63ec4-1065">Это событие представляет собой включение служб IPv6 в предоставленном экземпляре IP с помощью nxd_ipv6_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1065">This event represents enabling IPv6 services on the supplied IP instance via nxd_ipv6_enable.</span></span>

<span data-ttu-id="63ec4-1066">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1066">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1067">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1067">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1068">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1068">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1069">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1069">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1070">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1070">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-global-address-get"></a><span data-ttu-id="63ec4-1071">Получение глобального адреса IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1071">Duo IPv6 Global Address Get</span></span> 

#### <a name="nxd_ipv6_global_address_get"></a><span data-ttu-id="63ec4-1072">nxd_ipv6_global_address_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1072">nxd_ipv6_global_address_get</span></span>

<span data-ttu-id="63ec4-1073">**Значок** ![Значок получения глобального адреса IPv6 типа Duo](./media/user-guide/netx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1073">**Icon** ![Duo I P v 6 global address get icon](./media/user-guide/netx-events/image64.png)</span></span>

<span data-ttu-id="63ec4-1074">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1074">**Description**</span></span>

<span data-ttu-id="63ec4-1075">Это событие представляет собой получение глобального (основного) IP-адреса для экземпляра IP, расположенного по индексу 1 в таблице интерфейса экземпляра IP, с помощью nxd_ipv6_global_address_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1075">This event represents retrieving the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_get.</span></span>

<span data-ttu-id="63ec4-1076">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1076">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1077">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1077">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="63ec4-1078">Поле сведений 2. Четвертое слово (наименее значимое) глобального адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1078">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="63ec4-1079">Поле сведений 3. Длина префикса адреса IPv6.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1079">Info Field 3: IPv6 address prefix length.</span></span>
- <span data-ttu-id="63ec4-1080">Поле сведений 4. Индекс в таблице IP-интерфейса (1).</span><span class="sxs-lookup"><span data-stu-id="63ec4-1080">Info Field 4: Index into IP interface table (1).</span></span>

### <a name="duo-ipv6-global-address-set"></a><span data-ttu-id="63ec4-1081">Установка глобальных адресов IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1081">Duo IPv6 Global Address Set</span></span> 

#### <a name="nxd_ipv6_global_address_set"></a><span data-ttu-id="63ec4-1082">nxd_ipv6_global_address_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1082">nxd_ipv6_global_address_set</span></span>

<span data-ttu-id="63ec4-1083">**Значок** ![Значок установки глобальных адресов IPv6 типа Duo](./media/user-guide/netx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1083">**Icon** ![Duo I P v 6 global address set icon](./media/user-guide/netx-events/image65.png)</span></span>

<span data-ttu-id="63ec4-1084">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1084">**Description**</span></span>

<span data-ttu-id="63ec4-1085">Это событие представляет собой установку глобального (основного) IP-адреса для экземпляра IP, расположенного по индексу 1 в таблице интерфейса экземпляра IP, с помощью nxd_ipv6_global_address_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1085">This event represents setting the global (primary) IP address on the IP instance located at index 1 in the IP instance interface table via nxd_ipv6_global_address_set.</span></span>

<span data-ttu-id="63ec4-1086">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1086">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1087">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1087">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1088">Поле сведений 2. Четвертое слово (наименее значимое) глобального адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1088">Info Field 2: Fourth word (least significant) of the global address</span></span>
- <span data-ttu-id="63ec4-1089">Поле сведений 3. Длина префикса адреса IPv6.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1089">Info Field 3: IPv6 address prefix length</span></span>
- <span data-ttu-id="63ec4-1090">Поле сведений 4. Индекс в таблице IP-интерфейса (1).</span><span class="sxs-lookup"><span data-stu-id="63ec4-1090">Info Field 4: Index into IP interface table (1)</span></span>

### <a name="duo-ipv6-initiate-dad-process"></a><span data-ttu-id="63ec4-1091">Процесс инициализации процесса Dad для IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1091">Duo IPv6 Initiate Dad Process</span></span> 

#### <a name="nxd_ipv6_initiate_dad_process"></a><span data-ttu-id="63ec4-1092">nxd_ipv6_initiate_dad_process</span><span class="sxs-lookup"><span data-stu-id="63ec4-1092">nxd_ipv6_initiate_dad_process</span></span>

<span data-ttu-id="63ec4-1093">**Значок** ![Значок инициации процесса Dad для IPv6 типа Duo](./media/user-guide/netx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1093">**Icon** ![Duo I P v 6 initiate dad process icon](./media/user-guide/netx-events/image66.png)</span></span>

<span data-ttu-id="63ec4-1094">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1094">**Description**</span></span>

<span data-ttu-id="63ec4-1095">Это событие представляет собой начало процесса обнаружения дубликатов адресов (DAD), если экземпляру IP-адреса назначен локальный или IP-адрес интерфейса через nxd_ipv6_initiate_dad_process.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1095">This event represents the start of the Duplicate Address Detection (DAD) process when the IP instance is assigned a link local or an IP interface address via nxd_ipv6_initiate_dad_process.</span></span>

<span data-ttu-id="63ec4-1096">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1096">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1097">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1097">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1098">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1098">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1099">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1099">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1100">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1100">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-interface-address-get"></a><span data-ttu-id="63ec4-1101">Получение адреса интерфейса IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1101">Duo IPv6 Interface Address Get</span></span> 

#### <a name="nxd_ipv6_interface_address_get"></a><span data-ttu-id="63ec4-1102">nxd_ipv6_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1102">nxd_ipv6_interface_address_get</span></span>

<span data-ttu-id="63ec4-1103">**Значок** ![Значок получения адреса интерфейса IPv6 типа Duo](./media/user-guide/netx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1103">**Icon** ![Duo I P v 6 interface address get icon](./media/user-guide/netx-events/image67.png)</span></span>

<span data-ttu-id="63ec4-1104">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1104">**Description**</span></span>

<span data-ttu-id="63ec4-1105">Это событие представляет собой извлечение IP-адреса и префикса по указанному индексу в таблицу адресов интерфейса экземпляра IP с помощью nxd_ipv6_interface_address_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1105">This event represents retrieving the IP address and prefix at the specified index into the IP instance interface address table via nxd_ipv6_interface_address_get.</span></span>

<span data-ttu-id="63ec4-1106">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1106">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1107">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1107">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1108">Поле сведений 2. Четвертое слово (наименее значимое) адреса IPv6, который нужно возвратить</span><span class="sxs-lookup"><span data-stu-id="63ec4-1108">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="63ec4-1109">Поле сведений 4. Индекс интерфейса в таблице интерфейса экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1109">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-interface-address-set"></a><span data-ttu-id="63ec4-1110">Установка адреса интерфейса для IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1110">Duo IPv6 Interface Address Set</span></span> 

### <a name="nxd_ipv6_interface_address_set"></a><span data-ttu-id="63ec4-1111">nxd_ipv6_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1111">nxd_ipv6_interface_address_set</span></span>

<span data-ttu-id="63ec4-1112">**Значок** ![Значок установки адреса интерфейса для IPv6 типа Duo](./media/user-guide/netx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1112">**Icon** ![Duo I P v 6 interface addresss et icon](./media/user-guide/netx-events/image68.png)</span></span>

<span data-ttu-id="63ec4-1113">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1113">**Description**</span></span>

<span data-ttu-id="63ec4-1114">Это событие представляет собой установку IP-адреса и префикса по указанному индексу в таблице адресов интерфейса экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1114">This event represents setting the IP address and prefix at the specified index into the IP instance interface address table.</span></span> <span data-ttu-id="63ec4-1115">Не разрешено для индекса размером ноль (локальный адрес канала связи) через nxd_ipv6_interface_address_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1115">Not permitted on index zero (link local address) via nxd_ipv6_interface_address_set.</span></span>

<span data-ttu-id="63ec4-1116">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1116">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1117">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1117">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1118">Поле сведений 2. Четвертое слово (наименее значимое) адреса IPv6, который нужно возвратить</span><span class="sxs-lookup"><span data-stu-id="63ec4-1118">Info Field 2: Fourth word (least significant) of the IPv6 address to return</span></span>
- <span data-ttu-id="63ec4-1119">Поле сведений 3. Длина префикса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1119">Info Field 3: Prefix length</span></span>
- <span data-ttu-id="63ec4-1120">Поле сведений 4. Индекс интерфейса в таблице интерфейса экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1120">Info Field 4: Index of interface into the IP instance interface table</span></span>

### <a name="duo-ipv6-link-local-address-get"></a><span data-ttu-id="63ec4-1121">Получение локального адреса канала связи IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1121">Duo IPv6 Link Local Address Get</span></span> 

#### <a name="nxd_ipv6_linklocal_address_get"></a><span data-ttu-id="63ec4-1122">nxd_ipv6_linklocal_address_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1122">nxd_ipv6_linklocal_address_get</span></span>

<span data-ttu-id="63ec4-1123">**Значок** ![Значок получения локального адреса ссылки на IPv6 типа Duo](./media/user-guide/netx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1123">**Icon** ![Duo I P v 6 link local address get icon](./media/user-guide/netx-events/image69.png)</span></span>

<span data-ttu-id="63ec4-1124">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1124">**Description**</span></span>

<span data-ttu-id="63ec4-1125">Это событие представляет собой получение локального адреса канала связи указанного экземпляра IP через nxd_ipv6_linklocal_address_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1125">This event represents retrieving the link local address of the specified IP instance via nxd_ipv6_linklocal_address_get.</span></span>

<span data-ttu-id="63ec4-1126">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1126">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1127">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1127">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1128">Поле сведений 2. Четвертое слово (наименее значимое) локального адреса ссылки на IPv6</span><span class="sxs-lookup"><span data-stu-id="63ec4-1128">Info Field 2: Fourth word (least significant) of the IP v6 link local address</span></span>
- <span data-ttu-id="63ec4-1129">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1129">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1130">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1130">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-link-local-address-set"></a><span data-ttu-id="63ec4-1131">Установка локальных адресов для канала связи IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1131">Duo IPv6 Link Local Address Set</span></span> 

#### <a name="nxd_ipv6_linklocal_address_set"></a><span data-ttu-id="63ec4-1132">nxd_ipv6_linklocal_address_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1132">nxd_ipv6_linklocal_address_set</span></span>

<span data-ttu-id="63ec4-1133">**Значок** ![Значок набора локальных адресов для ссылки на IPv6 типа Duo](./media/user-guide/netx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1133">**Icon** ![Duo I P v 6 link local address set icon](./media/user-guide/netx-events/image70.png)</span></span>

<span data-ttu-id="63ec4-1134">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1134">**Description**</span></span>

<span data-ttu-id="63ec4-1135">Это событие представляет собой установку локального адреса канала связи указанного экземпляра IP через nxd_ipv6_linklocal_address_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1135">This event represents setting the link local address of the IP instance via nxd_ipv6_linklocal_address_set.</span></span>

<span data-ttu-id="63ec4-1136">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1136">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1137">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1137">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1138">Поле сведений 2. Четвертое (наименее значимое) слово локального адреса канала связи IPv6</span><span class="sxs-lookup"><span data-stu-id="63ec4-1138">Info Field 2: Fourth (least significant) word of the IPv6 link local address</span></span>
- <span data-ttu-id="63ec4-1139">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1139">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1140">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1140">Info Field 4: Not used</span></span>

### <a name="duo-ipv6-raw-packet-send"></a><span data-ttu-id="63ec4-1141">Отправка необработанных пакетов IPv6 типа Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1141">Duo IPv6 Raw Packet Send</span></span> 

#### <a name="nxd_ipv6_raw_packet_send"></a><span data-ttu-id="63ec4-1142">nxd_ipv6_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-1142">nxd_ipv6_raw_packet_send</span></span>

<span data-ttu-id="63ec4-1143">**Значок** ![Значок отправки необработанного пакета IPv6 типа Duo](./media/user-guide/netx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1143">**Icon** ![Duo I P v 6 raw packet send icon](./media/user-guide/netx-events/image71.png)</span></span>

<span data-ttu-id="63ec4-1144">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1144">**Description**</span></span>

<span data-ttu-id="63ec4-1145">Это событие представляет собой отправку необработанного пакета IP через основной IP-интерфейс в указанный пункт назначения с помощью nxd_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1145">This event represents sending a raw IP packet through the primary IP interface to the speficied destination via nxd_ip_raw_packet_send.</span></span>

<span data-ttu-id="63ec4-1146">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1146">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1147">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1147">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1148">Поле сведений 2. Указатель на пакет, который нужно отправить</span><span class="sxs-lookup"><span data-stu-id="63ec4-1148">Info Field 2: Pointer to packet to send</span></span>
- <span data-ttu-id="63ec4-1149">Поле сведений 3. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-1149">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="63ec4-1150">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1150">Info Field 4: Not used</span></span>

### <a name="duo-tcp-socket-peer-info-get"></a><span data-ttu-id="63ec4-1151">Получение сведений об узле сокета TCP Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1151">Duo TCP Socket Peer Info Get</span></span> 

#### <a name="nxd_tcp_socket_peer_info_get"></a><span data-ttu-id="63ec4-1152">nxd_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1152">nxd_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="63ec4-1153">**Значок** ![Значок получения сведений об узле сокета TCP Duo](./media/user-guide/netx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1153">**Icon** ![Duo T C P socket peer info get icon](./media/user-guide/netx-events/image72.png)</span></span>

<span data-ttu-id="63ec4-1154">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1154">**Description**</span></span>

<span data-ttu-id="63ec4-1155">Это событие извлекает данные отправителя из полученного пакета TCP в указанный сокет.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1155">This event extracts the sender data from a received TCP packet on the specified socket.</span></span> <span data-ttu-id="63ec4-1156">Во время этого возвращается IP-адрес и порт отправителя.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1156">It returns the IP address and port of the sender.</span></span>

<span data-ttu-id="63ec4-1157">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1157">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1158">Поле сведений 1. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1158">Info Field 1: Socket pointer</span></span>
- <span data-ttu-id="63ec4-1159">Поле сведений 2. IP-адрес однорангового узла</span><span class="sxs-lookup"><span data-stu-id="63ec4-1159">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="63ec4-1160">Поле сведений 3. Порт однорангового узла</span><span class="sxs-lookup"><span data-stu-id="63ec4-1160">Info Field 3: Peer port</span></span>
- <span data-ttu-id="63ec4-1161">Поле сведений 4. Наименее значимые 32-бита IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1161">Info Field 4: The lease significant 32-bit of the IP address</span></span>

### <a name="duo-tcp-socket-set-interface"></a><span data-ttu-id="63ec4-1162">Интерфейс установки сокета TCP Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1162">Duo TCP Socket Set Interface</span></span> 

#### <a name="nxd_tcp_socket_set_interface"></a><span data-ttu-id="63ec4-1163">nxd_tcp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="63ec4-1163">nxd_tcp_socket_set_interface</span></span>

<span data-ttu-id="63ec4-1164">**Значок** ![Значок интерфейса установки сокетов TCP Duo](./media/user-guide/netx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1164">**Icon** ![Duo T C P socket set interface icon](./media/user-guide/netx-events/image73.png)</span></span>

<span data-ttu-id="63ec4-1165">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1165">**Description**</span></span>

<span data-ttu-id="63ec4-1166">Это событие представляет собой настройку исходящего интерфейса сокета после подключения клиента к серверу TCP по указанному IP-адресу сервера с помощью nxd_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1166">This event represents setting the outgoing socket interface after a client connects with a TCP server on the specified server IP address via nxd_tcp_client_socket_connect.</span></span>

<span data-ttu-id="63ec4-1167">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1167">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1168">Поле сведений 1. Указатель на сокет TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1168">Info Field 1: Pointer to TCP Socket</span></span>
- <span data-ttu-id="63ec4-1169">Поле сведений 2. Идентификатор интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1169">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="63ec4-1170">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1170">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1171">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1171">Info Field 4: Not used</span></span>

### <a name="duo-udp-socket-send"></a><span data-ttu-id="63ec4-1172">Отправка UDP-сокета Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1172">Duo UDP Socket Send</span></span> 

#### <a name="nxd_udp_socket_send"></a><span data-ttu-id="63ec4-1173">nxd_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-1173">nxd_udp_socket_send</span></span>

<span data-ttu-id="63ec4-1174">**Значок** ![Значок отправки UDP-сокета Duo](./media/user-guide/netx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1174">**Icon** ![Duo U D P socket send icon](./media/user-guide/netx-events/image74.png)</span></span>

<span data-ttu-id="63ec4-1175">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1175">**Description**</span></span>

<span data-ttu-id="63ec4-1176">Это событие представляет собой отправку пакета UDP через указанный сокет с IP-адресом входных данных и портом через nxd_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1176">This event represents sending a UDP packet through the specified socket with the input IP address and port via nxd_udp_socket_send.</span></span>

<span data-ttu-id="63ec4-1177">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1177">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1178">Поле сведений 1. Указатель на сокет UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1178">Info Field 1: Pointer UDP Socket</span></span>
- <span data-ttu-id="63ec4-1179">Поле сведений 2. Указатель на пакет UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1179">Info Field 2: Pointer to UDP packet</span></span>
- <span data-ttu-id="63ec4-1180">Поле сведений 3. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1180">Info Field 3: Packet length</span></span>
- <span data-ttu-id="63ec4-1181">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1181">Info Field 4: Not used</span></span>


### <a name="duo-udp-socket-set-interface"></a><span data-ttu-id="63ec4-1182">Интерфейс установки UDP-сокета Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1182">Duo UDP Socket Set Interface</span></span> 

#### <a name="nxd_udp_socket_set_interface"></a><span data-ttu-id="63ec4-1183">nxd_udp_socket_set_interface</span><span class="sxs-lookup"><span data-stu-id="63ec4-1183">nxd_udp_socket_set_interface</span></span>

<span data-ttu-id="63ec4-1184">**Значок** ![Значок интерфейса установки сокетов UDP Duo](./media/user-guide/netx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1184">**Icon** ![Duo U D P socket set interface icon](./media/user-guide/netx-events/image75.png)</span></span>

<span data-ttu-id="63ec4-1185">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1185">**Description**</span></span>

<span data-ttu-id="63ec4-1186">Это событие представляет собой установку указанного исходящего интерфейса UDP-сокета для интерфейса, соответствующего идентификатору интерфейса ввода, через nxd_udp_socket_set_interface.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1186">This event represents setting the specified UDP socket outgoing interface to the interface corresponding to the input interface ID via nxd_udp_socket_set_interface.</span></span>

<span data-ttu-id="63ec4-1187">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1187">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1188">Поле сведений 1. Указатель на сокет UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1188">Info Field 1: Pointer to UDP Socket</span></span>
- <span data-ttu-id="63ec4-1189">Поле сведений 2. Идентификатор интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1189">Info Field 2: Interface ID</span></span>
- <span data-ttu-id="63ec4-1190">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1190">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1191">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1191">Info Field 4: Not used</span></span>

### <a name="duo-udp-source-extract"></a><span data-ttu-id="63ec4-1192">Извлечение источника UDP Duo</span><span class="sxs-lookup"><span data-stu-id="63ec4-1192">Duo UDP Source Extract</span></span> 

#### <a name="nxd_udp_socket_extract"></a><span data-ttu-id="63ec4-1193">nxd_udp_socket_extract</span><span class="sxs-lookup"><span data-stu-id="63ec4-1193">nxd_udp_socket_extract</span></span>

<span data-ttu-id="63ec4-1194">**Значок** ![Значок извлечения источника UDP Duo](./media/user-guide/netx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1194">**Icon** ![Duo U D P source extract icon](./media/user-guide/netx-events/image76.png)</span></span>

<span data-ttu-id="63ec4-1195">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1195">**Description**</span></span>

<span data-ttu-id="63ec4-1196">Это событие представляет собой извлечение IP-адреса и исходного порта полученного пакета (IPv4 или IPv6).</span><span class="sxs-lookup"><span data-stu-id="63ec4-1196">This event represents extracting the IP address and source port of a received packet (either IPv4 or IPv6).</span></span> <span data-ttu-id="63ec4-1197">Если используется IPv6, четвертое слово (наименьшее значение) IP-адреса возвращается через nxd_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1197">If IPv6, the fourth word (least significant) of the IP address is returned via nxd_udp_source_extract.</span></span>

<span data-ttu-id="63ec4-1198">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1198">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1199">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1199">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="63ec4-1200">Поле сведений 2. Версия IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1200">Info Field 2: IP version</span></span>
- <span data-ttu-id="63ec4-1201">Поле сведений 3. Исходный IP-адрес (IPv4 или IPv6)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1201">Info Field 3: Source IP address (IPv4 or IPv6)</span></span>
- <span data-ttu-id="63ec4-1202">Поле сведений 4. Исходный порт</span><span class="sxs-lookup"><span data-stu-id="63ec4-1202">Info Field 4: Source port</span></span>

### <a name="icmp-enable"></a><span data-ttu-id="63ec4-1203">Включение ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1203">ICMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="63ec4-1204">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1204">nx_icmp_enable</span></span>

<span data-ttu-id="63ec4-1205">**Значок** ![Значок включения протокола ICMP](./media/user-guide/netx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1205">**Icon** ![I C M P enable icon](./media/user-guide/netx-events/image77.png)</span></span>

<span data-ttu-id="63ec4-1206">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1206">**Description**</span></span>

<span data-ttu-id="63ec4-1207">Это событие представляет собой включение протокола ICMP через nx_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1207">This event represents enabling ICMP via nx_icmp_enable.</span></span>

<span data-ttu-id="63ec4-1208">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1208">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1209">Поле сведений 1. Указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1209">Info Field 1: Pointer to the IP instance l;</span></span>
- <span data-ttu-id="63ec4-1210">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1210">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1211">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1211">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1212">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1212">Info Field 4: Not used</span></span>

### <a name="icmp-information-get"></a><span data-ttu-id="63ec4-1213">Получение сведений о ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1213">ICMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="63ec4-1214">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1214">nx_icmp_info_get</span></span>

<span data-ttu-id="63ec4-1215">**Значок** ![Значок получения сведений об ICMP](./media/user-guide/netx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1215">**Icon** ![I C M P information get icon](./media/user-guide/netx-events/image78.png)</span></span>

<span data-ttu-id="63ec4-1216">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1216">**Description**</span></span>

<span data-ttu-id="63ec4-1217">Это событие представляет собой получение сведений с помощью nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1217">This event represents getting information via nx_icmp_info_get.</span></span>

<span data-ttu-id="63ec4-1218">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1218">**Information Fields**</span></span>
- <span data-ttu-id="63ec4-1219">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1219">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1220">Поле сведений 2. Количество отправленных запросов на проверку связи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1220">Info Field 2: Pings sent</span></span>
- <span data-ttu-id="63ec4-1221">Поле сведений 3. Количество откликов на запросы на проверку связи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1221">Info Field 3: Ping responses</span></span>
- <span data-ttu-id="63ec4-1222">Поле сведений 4. Количество полученных запросов на проверку связи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1222">Info Field 4: Pings received</span></span>

### <a name="icmp-ping"></a><span data-ttu-id="63ec4-1223">Проверка связи ICMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1223">ICMP Ping</span></span> 

#### <a name="nx_icmp_ping"></a><span data-ttu-id="63ec4-1224">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="63ec4-1224">nx_icmp_ping</span></span>

<span data-ttu-id="63ec4-1225">**Значок** ![Значок проверки связи ICМP](./media/user-guide/netx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1225">**Icon** ![I C M P ping icon](./media/user-guide/netx-events/image79.png)</span></span>

<span data-ttu-id="63ec4-1226">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1226">**Description**</span></span>

<span data-ttu-id="63ec4-1227">Это событие представляет собой проверку связи для целевого IP-адреса через nx_icmp_ping.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1227">This event represents pinging a target IP address via nx_icmp_ping.</span></span>

<span data-ttu-id="63ec4-1228">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1228">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1229">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1229">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1230">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-1230">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-1231">Поле сведений 3. Указатель на данные</span><span class="sxs-lookup"><span data-stu-id="63ec4-1231">Info Field 3: Pointer to data</span></span>
- <span data-ttu-id="63ec4-1232">Поле сведений 4. Размер данных</span><span class="sxs-lookup"><span data-stu-id="63ec4-1232">Info Field 4: Size of data</span></span>

### <a name="igmp-enable"></a><span data-ttu-id="63ec4-1233">Включение IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1233">IGMP Enable</span></span> 

#### <a name="nx_icmp_enable"></a><span data-ttu-id="63ec4-1234">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1234">nx_icmp_enable</span></span>

<span data-ttu-id="63ec4-1235">**Значок** ![Значок включения IGMP](./media/user-guide/netx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1235">**Icon** ![I G M P enable icon](./media/user-guide/netx-events/image80.png)</span></span>

<span data-ttu-id="63ec4-1236">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1236">**Description**</span></span>

<span data-ttu-id="63ec4-1237">Это событие представляет собой включение протокола IGMP через nx_icmp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1237">This event represents enabling IGMP via nx_igmp_enable.</span></span>

<span data-ttu-id="63ec4-1238">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1238">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1239">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1239">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1240">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1240">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1241">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1241">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1242">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1242">Info Field 4: Not used</span></span>

### <a name="igmp-information-get"></a><span data-ttu-id="63ec4-1243">Получение сведений об IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1243">IGMP Information Get</span></span> 

#### <a name="nx_icmp_info_get"></a><span data-ttu-id="63ec4-1244">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1244">nx_icmp_info_get</span></span>

<span data-ttu-id="63ec4-1245">**Значок** ![Значок получения сведений об IGMP](./media/user-guide/netx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1245">**Icon** ![I G M P information get icon](./media/user-guide/netx-events/image81.png)</span></span>

<span data-ttu-id="63ec4-1246">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1246">**Description**</span></span>

<span data-ttu-id="63ec4-1247">Это событие представляет собой получение сведений с помощью nx_igmp_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1247">This event represents getting information via nx_igmp_info_get.</span></span>

<span data-ttu-id="63ec4-1248">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1248">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1249">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1249">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1250">Поле сведений 2. Количество отправленных отчетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1250">Info Field 2: Reports sent</span></span>
- <span data-ttu-id="63ec4-1251">Поле сведений 3. Количество полученных запросов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1251">Info Field 3: Queries received</span></span>
- <span data-ttu-id="63ec4-1252">Поле сведений 4. Количество присоединенных групп</span><span class="sxs-lookup"><span data-stu-id="63ec4-1252">Info Field 4: Groups joined</span></span>

### <a name="igmp-loopback-disable"></a><span data-ttu-id="63ec4-1253">Отключение замыкания на себя для IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1253">IGMP Loopback Disable</span></span> 

#### <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="63ec4-1254">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1254">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="63ec4-1255">**Значок** ![Значок отключения замыкания на себя для IGMP](./media/user-guide/netx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1255">**Icon** ![I G M P loopback disable icon](./media/user-guide/netx-events/image82.png)</span></span>

<span data-ttu-id="63ec4-1256">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1256">**Description**</span></span>

<span data-ttu-id="63ec4-1257">Это событие представляет собой отключение замыкания на себя для IGMP через nx_igmp_loopback_disable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1257">This event represents disabling IGMP loopback via nx_igmp_loopback_disable.</span></span>

<span data-ttu-id="63ec4-1258">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1258">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1259">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1259">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1260">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1260">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1261">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1261">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1262">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1262">Info Field 4: Not used</span></span>

### <a name="igmp-loopback-enable"></a><span data-ttu-id="63ec4-1263">Включение замыкания на себя для IGMP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1263">IGMP Loopback Enable</span></span> 

#### <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="63ec4-1264">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1264">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="63ec4-1265">**Значок** ![Значок включения замыкания на себя для IGMP](./media/user-guide/netx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1265">**Icon** ![I G M P loopback enable icon](./media/user-guide/netx-events/image83.png)</span></span>

<span data-ttu-id="63ec4-1266">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1266">**Description**</span></span>

<span data-ttu-id="63ec4-1267">Это событие представляет собой включение замыкания на себя для IGMP через nx_igmp_loopback_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1267">This event represents enabling IGMP loopback via nx_igmp_loopback_enable.</span></span>

<span data-ttu-id="63ec4-1268">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1268">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1269">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1269">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1270">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1270">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1271">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1271">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1272">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1272">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-join"></a><span data-ttu-id="63ec4-1273">Подключение IGMP к многоадресной рассылке</span><span class="sxs-lookup"><span data-stu-id="63ec4-1273">IGMP Multicast Join</span></span> 

#### <a name="nx_igmp_multicast_join"></a><span data-ttu-id="63ec4-1274">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="63ec4-1274">nx_igmp_multicast_join</span></span>

<span data-ttu-id="63ec4-1275">**Значок** ![Значок подключения IGMP к многоадресной рассылке](./media/user-guide/netx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1275">**Icon** ![I G M P multicast join icon](./media/user-guide/netx-events/image84.png)</span></span>

<span data-ttu-id="63ec4-1276">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1276">**Description**</span></span>

<span data-ttu-id="63ec4-1277">Это событие представляет собой подключение группы к многоадресной рассылке через nx_igmp_multicast_join.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1277">This event represents joining a multicast group via nx_igmp_multicast_join.</span></span>

<span data-ttu-id="63ec4-1278">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1278">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1279">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1279">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1280">Поле сведений 2. IP-адрес группы</span><span class="sxs-lookup"><span data-stu-id="63ec4-1280">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="63ec4-1281">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1281">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1282">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1282">Info Field 4: Not used</span></span>

### <a name="igmp-multicast-leave"></a><span data-ttu-id="63ec4-1283">Отключение IGMP от многоадресной рассылки</span><span class="sxs-lookup"><span data-stu-id="63ec4-1283">IGMP Multicast Leave</span></span> 

#### <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="63ec4-1284">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="63ec4-1284">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="63ec4-1285">**Значок** ![Значок отключения IGMP от многоадресной рассылки](./media/user-guide/netx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1285">**Icon** ![I G M P multicast leave icon](./media/user-guide/netx-events/image85.png)</span></span>

<span data-ttu-id="63ec4-1286">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1286">**Description**</span></span>

<span data-ttu-id="63ec4-1287">Это событие представляет собой отключение IGMP от многоадресной рассылки с помощью nx_igmp_multicast_leave.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1287">This event represents leaving a multicast group via nx_igmp_multicast_leave.</span></span>

<span data-ttu-id="63ec4-1288">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1288">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1289">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1289">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1290">Поле сведений 2. IP-адрес группы</span><span class="sxs-lookup"><span data-stu-id="63ec4-1290">Info Field 2: Group IP address</span></span>
- <span data-ttu-id="63ec4-1291">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1291">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1292">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1292">Info Field 4: Not used</span></span>

### <a name="ip-address-change-notify"></a><span data-ttu-id="63ec4-1293">Уведомление об изменении IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1293">IP Address Change Notify</span></span> 

#### <a name="nx_ip_address_change_notify"></a><span data-ttu-id="63ec4-1294">nx_ip_address_change_notify</span><span class="sxs-lookup"><span data-stu-id="63ec4-1294">nx_ip_address_change_notify</span></span>

<span data-ttu-id="63ec4-1295">**Значок** ![Значок уведомления об изменении IP-адреса](./media/user-guide/netx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1295">**Icon** ![I P address change notify icon](./media/user-guide/netx-events/image86.png)</span></span>

<span data-ttu-id="63ec4-1296">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1296">**Description**</span></span>

<span data-ttu-id="63ec4-1297">Это событие представляет собой регистрацию для получения уведомлений об изменении IP-адреса с помощью nx_ip_address_change_notify.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1297">This event represents registering for IP change notification via nx_ip_address_change_notify.</span></span>

<span data-ttu-id="63ec4-1298">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1298">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1299">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1299">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1300">Поле сведений 2. Указатель на функцию обратного вызова</span><span class="sxs-lookup"><span data-stu-id="63ec4-1300">Info Field 2: Callback function pointer</span></span>
- <span data-ttu-id="63ec4-1301">Поле сведений 3. Указатель на дополнительную информацию</span><span class="sxs-lookup"><span data-stu-id="63ec4-1301">Info Field 3: Additional information pointer</span></span>
- <span data-ttu-id="63ec4-1302">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1302">Info Field 4: Not used</span></span>

### <a name="ip-address-get"></a><span data-ttu-id="63ec4-1303">Получение IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1303">IP Address Get</span></span> 

#### <a name="nx_ip_address_get"></a><span data-ttu-id="63ec4-1304">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1304">nx_ip_address_get</span></span>

<span data-ttu-id="63ec4-1305">**Значок** ![Значок получения IP-адреса](./media/user-guide/netx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1305">**Icon** ![I P address get icon](./media/user-guide/netx-events/image87.png)</span></span>

<span data-ttu-id="63ec4-1306">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1306">**Description**</span></span>

<span data-ttu-id="63ec4-1307">Это событие представляет собой получение IP-адреса через nx_ip_address_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1307">This event represents getting the IP address via nx_ip_address_get.</span></span>

<span data-ttu-id="63ec4-1308">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1308">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1309">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1309">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1310">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-1310">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-1311">Поле сведений 3. Маска сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1311">Info Field 3: Network mask</span></span>
- <span data-ttu-id="63ec4-1312">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1312">Info Field 4: Not used</span></span>

### <a name="ip-address-set"></a><span data-ttu-id="63ec4-1313">Установка IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1313">IP Address Set</span></span> 

#### <a name="nx_ip_address_set"></a><span data-ttu-id="63ec4-1314">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1314">nx_ip_address_set</span></span>

<span data-ttu-id="63ec4-1315">**Значок** ![Значок установки IP-адреса](./media/user-guide/netx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1315">**Icon** ![I P address set icon](./media/user-guide/netx-events/image88.png)</span></span>

<span data-ttu-id="63ec4-1316">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1316">**Description**</span></span>

<span data-ttu-id="63ec4-1317">Это событие представляет собой установку IP-адреса через nx_ip_address_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1317">This event represents setting the IP address via nx_ip_address_set.</span></span>

<span data-ttu-id="63ec4-1318">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1318">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1319">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1319">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1320">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-1320">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-1321">Поле сведений 3. Маска сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1321">Info Field 3: Network mask</span></span>
- <span data-ttu-id="63ec4-1322">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1322">Info Field 4: Not used</span></span>

### <a name="ip-create"></a><span data-ttu-id="63ec4-1323">Создание IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1323">IP Create</span></span> 

#### <a name="nx_ip_create"></a><span data-ttu-id="63ec4-1324">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="63ec4-1324">nx_ip_create</span></span>

<span data-ttu-id="63ec4-1325">**Значок** ![Значок создания IP-адреса](./media/user-guide/netx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1325">**Icon** ![I P create icon](./media/user-guide/netx-events/image89.png)</span></span>

<span data-ttu-id="63ec4-1326">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1326">**Description**</span></span>

<span data-ttu-id="63ec4-1327">Это событие представляет собой создание экземпляра IP-адреса с помощью nx_ip_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1327">This event represents creating an IP instance via nx_ip_create.</span></span>

<span data-ttu-id="63ec4-1328">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1328">**Information Fields**</span></span> 
- <span data-ttu-id="63ec4-1329">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1329">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1330">Поле сведений 2. IP-адрес</span><span class="sxs-lookup"><span data-stu-id="63ec4-1330">Info Field 2: IP address</span></span>
- <span data-ttu-id="63ec4-1331">Поле сведений 3. Маска сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1331">Info Field 3: Network mask</span></span>
- <span data-ttu-id="63ec4-1332">Поле сведений 4. Указатель на пул пакетов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="63ec4-1332">Info Field 4: Default packet pool pointer</span></span>

### <a name="ip-delete"></a><span data-ttu-id="63ec4-1333">Удаление IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1333">IP Delete</span></span> 

#### <a name="nx_ip_delete"></a><span data-ttu-id="63ec4-1334">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-1334">nx_ip_delete</span></span>

<span data-ttu-id="63ec4-1335">**Значок** ![Значок удаления IP-адреса](./media/user-guide/netx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1335">**Icon** ![I P delete icon](./media/user-guide/netx-events/image90.png)</span></span>

<span data-ttu-id="63ec4-1336">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1336">**Description**</span></span>

<span data-ttu-id="63ec4-1337">Это событие представляет собой удаление экземпляра IP-адреса с помощью nx_ip_delete.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1337">This event represents deleting an IP instance via nx_ip_delete.</span></span>

<span data-ttu-id="63ec4-1338">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1338">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1339">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1339">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1340">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1340">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1341">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1341">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1342">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1342">Info Field 4: Not used</span></span>

### <a name="ip-driver-direct-command"></a><span data-ttu-id="63ec4-1343">Команда прямого доступа к драйверу протокола IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1343">IP Driver Direct Command</span></span> 

#### <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="63ec4-1344">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="63ec4-1344">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="63ec4-1345">**Значок** ![Значок команды прямого доступа к драйверу протокола IP](./media/user-guide/netx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1345">**Icon** ![I P driver direct command icon](./media/user-guide/netx-events/image91.png)</span></span>

<span data-ttu-id="63ec4-1346">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1346">**Description**</span></span>

<span data-ttu-id="63ec4-1347">Это событие представляет собой команду прямого доступа к драйверу ввода-вывода с помощью nx_ip_driver_direct_command.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1347">This event represents a direct I/O driver command via nx_ip_driver_direct_command.</span></span>

<span data-ttu-id="63ec4-1348">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1348">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1349">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1349">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1350">Поле сведений 2. Команда драйвера</span><span class="sxs-lookup"><span data-stu-id="63ec4-1350">Info Field 2: Driver command</span></span>
- <span data-ttu-id="63ec4-1351">Поле сведений 3. Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="63ec4-1351">Info Field 3: Return value</span></span>
- <span data-ttu-id="63ec4-1352">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1352">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-disable"></a><span data-ttu-id="63ec4-1353">Отключение IP-пересылки</span><span class="sxs-lookup"><span data-stu-id="63ec4-1353">IP Forwarding Disable</span></span> 

#### <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="63ec4-1354">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1354">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="63ec4-1355">**Значок** ![Значок отключения IP-пересылки](./media/user-guide/netx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1355">**Icon** ![I P forwarding disable icon](./media/user-guide/netx-events/image92.png)</span></span>

<span data-ttu-id="63ec4-1356">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1356">**Description**</span></span>

<span data-ttu-id="63ec4-1357">Это событие представляет собой отключение IP-пересылки через nx_ip_forwarding_disable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1357">This event represents disabling IP forwarding via nx_ip_forwarding_disable.</span></span>

<span data-ttu-id="63ec4-1358">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1358">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1359">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1359">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1360">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1360">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1361">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1361">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1362">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1362">Info Field 4: Not used</span></span>

### <a name="ip-forwarding-enable"></a><span data-ttu-id="63ec4-1363">Включение IP-пересылки</span><span class="sxs-lookup"><span data-stu-id="63ec4-1363">IP Forwarding Enable</span></span> 

#### <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="63ec4-1364">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1364">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="63ec4-1365">**Значок** ![Значок включения IP-пересылки](./media/user-guide/netx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1365">**Icon** ![I P forwarding enable icon](./media/user-guide/netx-events/image93.png)</span></span>

<span data-ttu-id="63ec4-1366">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1366">**Description**</span></span>

<span data-ttu-id="63ec4-1367">Это событие представляет собой включение IP-пересылки через nx_ip_forwarding_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1367">This event represents enabling IP forwarding via nx_ip_forwarding_enable.</span></span>

<span data-ttu-id="63ec4-1368">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1368">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1369">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1369">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1370">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1370">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1371">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1371">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1372">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1372">Info Field 4: Not used</span></span>

### <a name="ip-fragment-disable"></a><span data-ttu-id="63ec4-1373">Отключение фрагмента IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1373">IP Fragment Disable</span></span> 

#### <a name="nx_ip_fragment_disable"></a><span data-ttu-id="63ec4-1374">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1374">nx_ip_fragment_disable</span></span>

<span data-ttu-id="63ec4-1375">**Значок** ![Значок отключения фрагмента IP-адреса](./media/user-guide/netx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1375">**Icon** ![I P fragment disable icon](./media/user-guide/netx-events/image94.png)</span></span>

<span data-ttu-id="63ec4-1376">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1376">**Description**</span></span>

<span data-ttu-id="63ec4-1377">Это событие представляет собой отключение фрагментации IP-адресов с помощью nx_ip_fragment_disable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1377">This event represents disabling IP fragmenting via nx_ip_fragment_disable.</span></span>

<span data-ttu-id="63ec4-1378">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1378">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1379">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1379">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1380">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1380">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1381">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1381">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1382">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1382">Info Field 4: Not used</span></span>

### <a name="ip-fragment-enable"></a><span data-ttu-id="63ec4-1383">Включение фрагмента IP-адреса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1383">IP Fragment Enable</span></span> 

#### <a name="nx_ip_fragment_enable"></a><span data-ttu-id="63ec4-1384">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1384">nx_ip_fragment_enable</span></span>

<span data-ttu-id="63ec4-1385">**Значок** ![Значок включения фрагмента IP-адреса](./media/user-guide/netx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1385">**Icon** ![I P fragment enable icon](./media/user-guide/netx-events/image95.png)</span></span>

<span data-ttu-id="63ec4-1386">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1386">**Description**</span></span>

<span data-ttu-id="63ec4-1387">Это событие представляет собой включение фрагментации IP-адресов с помощью nx_ip_fragment_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1387">This event represents enabling IP fragmenting via nx_ip_fragment_enable.</span></span>

<span data-ttu-id="63ec4-1388">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1388">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1389">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1389">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1390">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1390">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1391">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1391">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1392">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1392">Info Field 4: Not used</span></span>

### <a name="ip-gateway-address-set"></a><span data-ttu-id="63ec4-1393">Установка адреса шлюза IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1393">IP Gateway Address Set</span></span> 

#### <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="63ec4-1394">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1394">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="63ec4-1395">**Значок** ![Значок установки адреса шлюза IP](./media/user-guide/netx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1395">**Icon** ![I P gateway address set icon](./media/user-guide/netx-events/image96.png)</span></span>

<span data-ttu-id="63ec4-1396">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1396">**Description**</span></span>

<span data-ttu-id="63ec4-1397">Это событие представляет собой установку IP-адреса шлюза с помощью nx_ip_gateway_address_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1397">This event represents setting the gateway IP address via nx_ip_gateway_address_set.</span></span>

<span data-ttu-id="63ec4-1398">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1398">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1399">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1399">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1400">Поле сведений 2. IP-адрес шлюза</span><span class="sxs-lookup"><span data-stu-id="63ec4-1400">Info Field 2: Gateway IP address</span></span>
- <span data-ttu-id="63ec4-1401">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1401">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1402">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1402">Info Field 4: Not used</span></span>

### <a name="ip-information-get"></a><span data-ttu-id="63ec4-1403">Получение сведений об IP-адресе</span><span class="sxs-lookup"><span data-stu-id="63ec4-1403">IP Information Get</span></span> 

#### <a name="nx_ip_info_get"></a><span data-ttu-id="63ec4-1404">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1404">nx_ip_info_get</span></span>

<span data-ttu-id="63ec4-1405">**Значок** ![Значок получения сведений об IP](./media/user-guide/netx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1405">**Icon** ![I P information get icon](./media/user-guide/netx-events/image97.png)</span></span>

<span data-ttu-id="63ec4-1406">**Описание**. Это событие представляет собой получение сведений об IP-адресе через nx_ip_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1406">**Description** This event represents getting IP information via nx_ip_info_get.</span></span>

<span data-ttu-id="63ec4-1407">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1407">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1408">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1408">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1409">Поле сведений 2. Байты, отправленные через IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1409">Info Field 2: IP bytes sent</span></span>
- <span data-ttu-id="63ec4-1410">Поле сведений 3. Байты, полученные через IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1410">Info Field 3: IP bytes received</span></span>
- <span data-ttu-id="63ec4-1411">Поле сведений 4. Удаленные пакеты IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1411">Info Field 4: IP packets dropped</span></span>

### <a name="ip-interface-attach"></a><span data-ttu-id="63ec4-1412">Подключение интерфейса IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1412">IP Interface Attach</span></span> 

#### <a name="nx_interface_attach"></a><span data-ttu-id="63ec4-1413">nx_interface_attach</span><span class="sxs-lookup"><span data-stu-id="63ec4-1413">nx_interface_attach</span></span>

<span data-ttu-id="63ec4-1414">**Значок** ![Значок подключения интерфейса IP](./media/user-guide/netx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1414">**Icon** ![I P iterface attach icon](./media/user-guide/netx-events/image98.png)</span></span>

<span data-ttu-id="63ec4-1415">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1415">**Description**</span></span>

<span data-ttu-id="63ec4-1416">Это событие представляет собой дополнительный сетевой интерфейс, который присоединяется к экземпляру IP через nx_ip_interface_attach.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1416">This event represents a secondary network interface being attached to the IP instance via nx_ip_interface_attach.</span></span>

<span data-ttu-id="63ec4-1417">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1417">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1418">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1418">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1419">Поле сведений 2. IP-адрес интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1419">Info Field 2: Interface IP Address</span></span>
- <span data-ttu-id="63ec4-1420">Поле сведений 3. Индекс в таблице IP-интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1420">Info Field 3: Index into IP interface table</span></span>
- <span data-ttu-id="63ec4-1421">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1421">Info Field 4: Not used</span></span>

### <a name="ip-interface-info-get"></a><span data-ttu-id="63ec4-1422">Получение сведений об интерфейсе IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1422">IP Interface Info Get</span></span> 

#### <a name="nx_ip_interface_info_get"></a><span data-ttu-id="63ec4-1423">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1423">nx_ip_interface_info_get</span></span>

<span data-ttu-id="63ec4-1424">**Значок** ![Значок получения сведений об интерфейсе IP](./media/user-guide/netx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1424">**Icon** ![ IP interface info get icon](./media/user-guide/netx-events/image99.png)</span></span>

<span data-ttu-id="63ec4-1425">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1425">**Description**</span></span>

<span data-ttu-id="63ec4-1426">Это событие представляет собой сведения, полученные из указанного сетевого интерфейса через nx_ip_interface_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1426">This event represents information retrieved from the specified network interface via nx_ip_interface_info_get.</span></span>

<span data-ttu-id="63ec4-1427">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1427">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1428">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1428">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1429">Поле сведений 2. IP-адрес интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1429">Info Field 2: Interface IP address</span></span>
- <span data-ttu-id="63ec4-1430">Поле сведений 3. MAC-адрес msb интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1430">Info Field 3: Interface MAC address msb</span></span>
- <span data-ttu-id="63ec4-1431">Поле сведений 4. MAC-адрес lsb интерфейса</span><span class="sxs-lookup"><span data-stu-id="63ec4-1431">Info Field 4: Interface MAC address lsb</span></span>

### <a name="ip-raw-packet-disable"></a><span data-ttu-id="63ec4-1432">Отключение необработанных пакетов IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1432">IP Raw Packet Disable</span></span> 

#### <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="63ec4-1433">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1433">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="63ec4-1434">**Значок** ![Значок отключения необработанных пакетов IP](./media/user-guide/netx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1434">**Icon** ![I P raw packet disable icon](./media/user-guide/netx-events/image100.png)</span></span>

<span data-ttu-id="63ec4-1435">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1435">**Description**</span></span>

<span data-ttu-id="63ec4-1436">Это событие представляет собой отключение необработанного пакета IP через nx_ip_raw_packet_disable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1436">This event represents disabling raw IP packet communication via nx_ip_raw_packet_disable.</span></span>

<span data-ttu-id="63ec4-1437">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1437">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1438">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1438">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1439">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1439">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1440">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1440">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1441">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1441">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-enable"></a><span data-ttu-id="63ec4-1442">Включение необработанных пакетов IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1442">IP Raw Packet Enable</span></span> 

#### <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="63ec4-1443">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1443">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="63ec4-1444">**Значок** ![Значок включения необработанных пакетов IP](./media/user-guide/netx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1444">**Icon** ![I P raw packet enable icon](./media/user-guide/netx-events/image101.png)</span></span>

<span data-ttu-id="63ec4-1445">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1445">**Description**</span></span>

<span data-ttu-id="63ec4-1446">Это событие представляет собой включение необработанного пакета IP с помощью nx_ip_raw_packet_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1446">This event represents enabling raw IP packet communication via nx_ip_raw_packet_enable.</span></span>

<span data-ttu-id="63ec4-1447">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1447">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1448">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1448">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1449">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1449">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1450">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1450">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1451">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1451">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-receive"></a><span data-ttu-id="63ec4-1452">Получение необработанных пакетов IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1452">IP Raw Packet Receive</span></span> 

#### <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="63ec4-1453">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="63ec4-1453">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="63ec4-1454">**Значок** ![Значок получения необработанных пакетов IP](./media/user-guide/netx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1454">**Icon** ![I P raw packet receive icon](./media/user-guide/netx-events/image102.png)</span></span>

<span data-ttu-id="63ec4-1455">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1455">**Description**</span></span>

<span data-ttu-id="63ec4-1456">Это событие представляет собой получение необработанного пакета IP через nx_ip_raw_packet_receive.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1456">This event represents receiving a raw IP packet via nx_ip_raw_packet_receive.</span></span>

<span data-ttu-id="63ec4-1457">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1457">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1458">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1458">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1459">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1459">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-1460">Поле сведений 3. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1460">Info Field 3: Wait option</span></span>
- <span data-ttu-id="63ec4-1461">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1461">Info Field 4: Not used</span></span>

### <a name="ip-raw-packet-send"></a><span data-ttu-id="63ec4-1462">Отправка необработанных пакетов IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1462">IP Raw Packet Send</span></span> 

#### <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="63ec4-1463">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-1463">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="63ec4-1464">**Значок** ![Значок отправки необработанных пакетов IP](./media/user-guide/netx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1464">**Icon** ![I P raw packet send icon](./media/user-guide/netx-events/image103.png)</span></span>

<span data-ttu-id="63ec4-1465">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1465">**Description**</span></span>

<span data-ttu-id="63ec4-1466">Это событие представляет собой отправку необработанного пакета IP через nx_ip_raw_packet_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1466">This event represents sending a raw IP packet via nx_ip_raw_packet_send.</span></span>

<span data-ttu-id="63ec4-1467">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1467">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1468">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1468">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1469">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1469">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-1470">Поле сведений 3. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-1470">Info Field 3: Destination IP address</span></span>
- <span data-ttu-id="63ec4-1471">Поле сведений 4. Тип службы.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1471">Info Field 4: Type of service</span></span>

### <a name="ip-static-route-add"></a><span data-ttu-id="63ec4-1472">Добавление статического маршрута IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1472">IP Static Route Add</span></span> 

#### <a name="nx_ip_static_route_add"></a><span data-ttu-id="63ec4-1473">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="63ec4-1473">nx_ip_static_route_add</span></span>

<span data-ttu-id="63ec4-1474">**Значок** ![Значок добавления статического маршрута IP](./media/user-guide/netx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1474">**Icon** ![I P static route add icon](./media/user-guide/netx-events/image104.png)</span></span>

<span data-ttu-id="63ec4-1475">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1475">**Description**</span></span>

<span data-ttu-id="63ec4-1476">Это событие представляет собой добавление статического маршрута в таблицу маршрутизации экземпляра IP с помощью nx_ip_static_route_add.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1476">This event represents a static route being added to the IP instance routing table via nx_ip_static_route_add.</span></span>

<span data-ttu-id="63ec4-1477">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1477">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1478">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1478">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1479">Поле сведений 2. Адрес сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1479">Info Field 2: Network address</span></span>
- <span data-ttu-id="63ec4-1480">Поле сведений 3. Маска сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1480">Info Field 3: Network mask</span></span>
- <span data-ttu-id="63ec4-1481">Поле сведений 4. Следующий прыжок</span><span class="sxs-lookup"><span data-stu-id="63ec4-1481">Info Field 4: Next hop</span></span>

### <a name="ip-static-route-delete"></a><span data-ttu-id="63ec4-1482">Удаление статического маршрута IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1482">IP Static Route Delete</span></span> 

#### <a name="nx_ip_static_route_delete"></a><span data-ttu-id="63ec4-1483">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-1483">nx_ip_static_route_delete</span></span>

<span data-ttu-id="63ec4-1484">**Значок** ![Значок удаления статического маршрута IP](./media/user-guide/netx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1484">**Icon** ![I P static rute delete icon](./media/user-guide/netx-events/image105.png)</span></span>

<span data-ttu-id="63ec4-1485">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1485">**Description**</span></span>

<span data-ttu-id="63ec4-1486">Это событие представляет собой удаление статического маршрута из таблицы маршрутизации экземпляра IP с помощью nx_ip_static_route_add.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1486">This event represents a static route being removed from the IP instance routing table via nx_ip_static_route_delete.</span></span>

<span data-ttu-id="63ec4-1487">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1487">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1488">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1488">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1489">Поле сведений 2. Адрес сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1489">Info Field 2: Network address</span></span>
- <span data-ttu-id="63ec4-1490">Поле сведений 3. Маска сети</span><span class="sxs-lookup"><span data-stu-id="63ec4-1490">Info Field 3: Network mask</span></span>
- <span data-ttu-id="63ec4-1491">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1491">Info Field 4: Not used</span></span>

### <a name="ip-status-check"></a><span data-ttu-id="63ec4-1492">Проверка состояния IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1492">IP Status Check</span></span> 

#### <a name="nx_ip_status_check"></a><span data-ttu-id="63ec4-1493">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="63ec4-1493">nx_ip_status_check</span></span>

<span data-ttu-id="63ec4-1494">**Значок** ![Значок проверки состояния IP](./media/user-guide/netx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1494">**Icon** ![I P status check icon](./media/user-guide/netx-events/image106.png)</span></span>

<span data-ttu-id="63ec4-1495">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1495">**Description**</span></span>

<span data-ttu-id="63ec4-1496">Это событие представляет собой проверку состояния IP с помощью nx_ip_status_check.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1496">This event represents checking for an IP status via nx_ip_status_check.</span></span>

<span data-ttu-id="63ec4-1497">Поля сведений</span><span class="sxs-lookup"><span data-stu-id="63ec4-1497">Information Fields</span></span> 

- <span data-ttu-id="63ec4-1498">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1498">Info Field 1: Pointer to the IP instance</span></span>
- <span data-ttu-id="63ec4-1499">Поле сведений 2. Запрошенное состояние</span><span class="sxs-lookup"><span data-stu-id="63ec4-1499">Info Field 2: Requested status</span></span>
- <span data-ttu-id="63ec4-1500">Поле сведений 3. Фактическое состояние</span><span class="sxs-lookup"><span data-stu-id="63ec4-1500">Info Field 3: Actual status</span></span>
- <span data-ttu-id="63ec4-1501">Поле сведений 4. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1501">Info Field 4: Wait option</span></span>

### <a name="ipsec-enable"></a><span data-ttu-id="63ec4-1502">Включение IPSEC</span><span class="sxs-lookup"><span data-stu-id="63ec4-1502">IPSEC Enable</span></span> 

#### <a name="nx_ipsec_enable"></a><span data-ttu-id="63ec4-1503">nx_ipsec_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1503">nx_ipsec_enable</span></span>

<span data-ttu-id="63ec4-1504">**Значок** ![Значок включения IPSEC](./media/user-guide/netx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1504">**Icon** ![I P S E C enable icon](./media/user-guide/netx-events/image107.png)</span></span>

<span data-ttu-id="63ec4-1505">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1505">**Description**</span></span>

<span data-ttu-id="63ec4-1506">Это событие представляет собой включение служб IPSec в предоставленном экземпляре IP с помощью nx_ipsec_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1506">This event represents enabling IPSec services on the supplied IP instance via nx_ipsec_enable.</span></span>

<span data-ttu-id="63ec4-1507">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1507">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1508">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1508">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1509">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1509">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1510">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1510">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1511">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1511">Info Field 4: Not used</span></span>

### <a name="packet-allocate"></a><span data-ttu-id="63ec4-1512">Выделение пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1512">Packet Allocate</span></span> 

#### <a name="nx_packet_allocate"></a><span data-ttu-id="63ec4-1513">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="63ec4-1513">nx_packet_allocate</span></span>

<span data-ttu-id="63ec4-1514">**Значок** ![Значок выделения пакета](./media/user-guide/netx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1514">**Icon** ![Packet allocate icon](./media/user-guide/netx-events/image108.png)</span></span>

<span data-ttu-id="63ec4-1515">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1515">**Description**</span></span>

<span data-ttu-id="63ec4-1516">Это событие представляет собой выделение пакета с помощью nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1516">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="63ec4-1517">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1517">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1518">Поле сведений 1. Указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1518">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="63ec4-1519">Поле сведений 2. Указатель на выделенный пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1519">Info Field 2: Pointer to packet allocated</span></span>
- <span data-ttu-id="63ec4-1520">Поле сведений 3. Тип пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1520">Info Field 3: Packet type</span></span>
- <span data-ttu-id="63ec4-1521">Поле сведений 4. Доступные пакеты</span><span class="sxs-lookup"><span data-stu-id="63ec4-1521">Info Field 4: Available packets</span></span>

### <a name="packet-copy"></a><span data-ttu-id="63ec4-1522">Копирование пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1522">Packet Copy</span></span> 

#### <a name="nx_packet_copy"></a><span data-ttu-id="63ec4-1523">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="63ec4-1523">nx_packet_copy</span></span>

<span data-ttu-id="63ec4-1524">**Значок** ![Значок копирования пакета](./media/user-guide/netx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1524">**Icon** ![Packet cpy icon](./media/user-guide/netx-events/image109.png)</span></span>

<span data-ttu-id="63ec4-1525">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1525">**Description**</span></span>

<span data-ttu-id="63ec4-1526">Это событие представляет собой копирование пакета с помощью nx_packet_copy.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1526">This event represents copying a packet via nx_packet_copy.</span></span>

<span data-ttu-id="63ec4-1527">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1527">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1528">Поле сведений 2. Указатель на новый пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1528">Info Field 2: New packet pointer</span></span>
- <span data-ttu-id="63ec4-1529">Поле сведений 3. Указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1529">Info Field 3: Pointer to packet pool</span></span>
- <span data-ttu-id="63ec4-1530">Поле сведений 4. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1530">Info Field 4: Wait option</span></span>

### <a name="packet-data-append"></a><span data-ttu-id="63ec4-1531">Добавление пакетных данных</span><span class="sxs-lookup"><span data-stu-id="63ec4-1531">Packet Data Append</span></span> 

#### <a name="nx_packet_data_append"></a><span data-ttu-id="63ec4-1532">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="63ec4-1532">nx_packet_data_append</span></span>

<span data-ttu-id="63ec4-1533">**Значок** ![Значок добавления пакетных данных](./media/user-guide/netx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1533">**Icon** ![Packet data append icon](./media/user-guide/netx-events/image110.png)</span></span>

<span data-ttu-id="63ec4-1534">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1534">**Description**</span></span>

<span data-ttu-id="63ec4-1535">Это событие представляет собой добавление данных в пакет с помощью nx_packet_data_append.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1535">This event represents appending data to a packet via nx_packet_data_append.</span></span>

<span data-ttu-id="63ec4-1536">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1536">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1537">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1537">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="63ec4-1538">Поле сведений 2. Указатель на данные</span><span class="sxs-lookup"><span data-stu-id="63ec4-1538">Info Field 2: Pointer to data</span></span>
- <span data-ttu-id="63ec4-1539">Поле сведений 3. Размер данных</span><span class="sxs-lookup"><span data-stu-id="63ec4-1539">Info Field 3: Size of data</span></span>
- <span data-ttu-id="63ec4-1540">Поле сведений 4. Указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1540">Info Field 4: Pointer to packet pool</span></span>

### <a name="packet-data-extract-offset"></a><span data-ttu-id="63ec4-1541">Смещение при извлечении данных пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1541">Packet Data Extract Offset</span></span> 

#### <a name="nx_udp_source_extract_offset"></a><span data-ttu-id="63ec4-1542">nx_udp_source_extract_offset</span><span class="sxs-lookup"><span data-stu-id="63ec4-1542">nx_udp_source_extract_offset</span></span>

<span data-ttu-id="63ec4-1543">**Значок** ![Значок смещения при извлечении данных пакета](./media/user-guide/netx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1543">**Icon** ![Packet data extract offset icon](./media/user-guide/netx-events/image111.png)</span></span>

<span data-ttu-id="63ec4-1544">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1544">**Description**</span></span>

<span data-ttu-id="63ec4-1545">Это событие представляет собой извлечение данных из пакета в указанный буфер с помощью nx_udp_source_extract_offset.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1545">This event represents packet data that is extracted into a supplied buffer from a packet via nx_udp_source_extract_offset.</span></span>

<span data-ttu-id="63ec4-1546">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1546">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1547">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1547">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-1548">Поле сведений 2. Размер указанного буфера</span><span class="sxs-lookup"><span data-stu-id="63ec4-1548">Info Field 2: Size of specified buffer</span></span>
- <span data-ttu-id="63ec4-1549">Поле сведений 3. Число скопированных байтов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1549">Info Field 3: Number of bytes copied</span></span>
- <span data-ttu-id="63ec4-1550">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1550">Info Field 4: Not used</span></span>

### <a name="packet-data-retrieve"></a><span data-ttu-id="63ec4-1551">Получение пакетных данных</span><span class="sxs-lookup"><span data-stu-id="63ec4-1551">Packet Data Retrieve</span></span> 

#### <a name="nx_packet_data_retrieve"></a><span data-ttu-id="63ec4-1552">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="63ec4-1552">nx_packet_data_retrieve</span></span>

<span data-ttu-id="63ec4-1553">**Значок** ![Значок получения пакетных данных](./media/user-guide/netx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1553">**Icon** ![Packet data retrieve icon](./media/user-guide/netx-events/image112.png)</span></span>

<span data-ttu-id="63ec4-1554">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1554">**Description**</span></span>

<span data-ttu-id="63ec4-1555">Это событие представляет собой получение данных из пакета с помощью nx_packet_data_retrieve.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1555">This event represents retrieving data from a packet via nx_packet_data_retrieve.</span></span>

<span data-ttu-id="63ec4-1556">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1556">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1557">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1557">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="63ec4-1558">Поле сведений 2. Указатель на запуск буфера</span><span class="sxs-lookup"><span data-stu-id="63ec4-1558">Info Field 2: Pointer to start of buffer</span></span>
- <span data-ttu-id="63ec4-1559">Поле сведений 3. Скопированные байты</span><span class="sxs-lookup"><span data-stu-id="63ec4-1559">Info Field 3: Bytes copied</span></span>
- <span data-ttu-id="63ec4-1560">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1560">Info Field 4: Not used</span></span>

### <a name="packet-length-get"></a><span data-ttu-id="63ec4-1561">Получение длины пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1561">Packet Length Get</span></span> 

#### <a name="nx_packet_length_get"></a><span data-ttu-id="63ec4-1562">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1562">nx_packet_length_get</span></span>

<span data-ttu-id="63ec4-1563">**Значок** ![Значок получения длины пакета](./media/user-guide/netx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1563">**Icon** ![Packet length get icon](./media/user-guide/netx-events/image113.png)</span></span>

<span data-ttu-id="63ec4-1564">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1564">**Description**</span></span>

<span data-ttu-id="63ec4-1565">Это событие представляет собой получение длины пакета через nx_packet_length_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1565">This event represents getting the length of a packet via nx_packet_length_get.</span></span>

<span data-ttu-id="63ec4-1566">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1566">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1567">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1567">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="63ec4-1568">Поле сведений 2. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1568">Info Field 2: Packet length</span></span>
- <span data-ttu-id="63ec4-1569">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1569">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1570">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1570">Info Field 4: Not used</span></span>

### <a name="packet-pool-create"></a><span data-ttu-id="63ec4-1571">Создание пула пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1571">Packet Pool Create</span></span> 

#### <a name="nx_packet_pool_create"></a><span data-ttu-id="63ec4-1572">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="63ec4-1572">nx_packet_pool_create</span></span>

<span data-ttu-id="63ec4-1573">**Значок** ![Значок создания пула пакетов](./media/user-guide/netx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1573">**Icon** ![Packet pool create icon](./media/user-guide/netx-events/image114.png)</span></span>

<span data-ttu-id="63ec4-1574">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1574">**Description**</span></span>

<span data-ttu-id="63ec4-1575">Это событие представляет собой создание пула пакетов с помощью nx_packet_pool_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1575">This event represents creating a packet pool via nx_packet_pool_create.</span></span>

<span data-ttu-id="63ec4-1576">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1576">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1577">Поле сведений 1. Указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1577">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="63ec4-1578">Поле сведений 2. Размер полезных данных пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1578">Info Field 2: Packet payload size</span></span>
- <span data-ttu-id="63ec4-1579">Поле сведений 3. Указатель на область памяти пула</span><span class="sxs-lookup"><span data-stu-id="63ec4-1579">Info Field 3: Pointer to pool memory area</span></span>
- <span data-ttu-id="63ec4-1580">Поле сведений 4. Размер области памяти пула</span><span class="sxs-lookup"><span data-stu-id="63ec4-1580">Info Field 4: Size of pool memory area</span></span>

### <a name="packet-pool-delete"></a><span data-ttu-id="63ec4-1581">Удаление пула пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1581">Packet Pool Delete</span></span> 

#### <a name="nx_packet_pool_delete"></a><span data-ttu-id="63ec4-1582">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-1582">nx_packet_pool_delete</span></span>

<span data-ttu-id="63ec4-1583">**Значок** ![Значок удаления пула пакетов](./media/user-guide/netx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1583">**Icon** ![Packet pool delete icon](./media/user-guide/netx-events/image115.png)</span></span>

<span data-ttu-id="63ec4-1584">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1584">**Description**</span></span>

<span data-ttu-id="63ec4-1585">Это событие представляет собой удаление пула пакетов с помощью nx_packet_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1585">This event represents deleting a packet pool via nx_packet_pool_delete.</span></span>

<span data-ttu-id="63ec4-1586">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1586">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1587">Поле сведений 1. Указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1587">Info Field 1: Pointer to the packet pool</span></span>
- <span data-ttu-id="63ec4-1588">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1588">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1589">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1589">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1590">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1590">Info Field 4: Not used</span></span>

#### <a name="packet-pool-information-get"></a><span data-ttu-id="63ec4-1591">Получение сведений о пуле пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1591">Packet Pool Information Get</span></span> 

#### <a name="nx_packet_pool_info_get"></a><span data-ttu-id="63ec4-1592">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1592">nx_packet_pool_info_get</span></span>

<span data-ttu-id="63ec4-1593">**Значок** ![Значок получения сведений о пуле пакетов](./media/user-guide/netx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1593">**Icon** ![Packet pool information get icon](./media/user-guide/netx-events/image116.png)</span></span>

<span data-ttu-id="63ec4-1594">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1594">**Description**</span></span>

<span data-ttu-id="63ec4-1595">Это событие представляет собой получение сведений о пуле пакетов с помощью nx_packet_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1595">This event represents getting packet pool information via nx_packet_pool_info_get.</span></span>

<span data-ttu-id="63ec4-1596">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1596">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1597">Поле сведений 1. Указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1597">Info Field 1: Pointer to packet pool</span></span>
- <span data-ttu-id="63ec4-1598">Поле сведений 2. Общее количество пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1598">Info Field 2: Total packets</span></span>
- <span data-ttu-id="63ec4-1599">Поле сведений 3. Доступные пакеты</span><span class="sxs-lookup"><span data-stu-id="63ec4-1599">Info Field 3: Available packets</span></span>
- <span data-ttu-id="63ec4-1600">Поле сведений 4. Пустые запросы</span><span class="sxs-lookup"><span data-stu-id="63ec4-1600">Info Field 4: Empty requests</span></span>

### <a name="packet-release"></a><span data-ttu-id="63ec4-1601">Выпуск пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1601">Packet Release</span></span> 

#### <a name="nx_packet_data_release"></a><span data-ttu-id="63ec4-1602">nx_packet_data_release</span><span class="sxs-lookup"><span data-stu-id="63ec4-1602">nx_packet_data_release</span></span>

<span data-ttu-id="63ec4-1603">**Значок** ![Значок выпуска пакета](./media/user-guide/netx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1603">**Icon** ![Packet release icon](./media/user-guide/netx-events/image117.png)</span></span>

<span data-ttu-id="63ec4-1604">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1604">**Description**</span></span>

<span data-ttu-id="63ec4-1605">Это событие представляет собой выпуск пакета с помощью nx_packet_release.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1605">This event represents releasing a packet via nx_packet_release.</span></span>

<span data-ttu-id="63ec4-1606">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1606">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1607">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1607">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="63ec4-1608">Поле сведений 2. Состояние пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1608">Info Field 2: Packet status</span></span>
- <span data-ttu-id="63ec4-1609">Поле сведений 3. Доступные пакеты</span><span class="sxs-lookup"><span data-stu-id="63ec4-1609">Info Field 3: Available packets</span></span>
- <span data-ttu-id="63ec4-1610">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1610">Info Field 4: Not used</span></span>

### <a name="packet-transmit-release"></a><span data-ttu-id="63ec4-1611">Выпуск передачи пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1611">Packet Transmit Release</span></span> 

#### <a name="nx_packet_transmit_release"></a><span data-ttu-id="63ec4-1612">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="63ec4-1612">nx_packet_transmit_release</span></span>

<span data-ttu-id="63ec4-1613">**Значок** ![Значок выпуска передачи пакетов](./media/user-guide/netx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1613">**Icon** ![Packet transmit release icon](./media/user-guide/netx-events/image118.png)</span></span>

<span data-ttu-id="63ec4-1614">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1614">**Description**</span></span>

<span data-ttu-id="63ec4-1615">Это событие представляет собой выпуск передачи пакета с помощью nx_packet_transmit_release.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1615">This event represents releasing a transmit packet via nx_packet_transmit_release.</span></span>

<span data-ttu-id="63ec4-1616">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1616">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1617">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1617">Info Field 1: Pointer to the packet</span></span>
- <span data-ttu-id="63ec4-1618">Поле сведений 2. Состояние пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1618">Info Field 2: Packet status</span></span>
- <span data-ttu-id="63ec4-1619">Поле сведений 3. Доступные пакеты</span><span class="sxs-lookup"><span data-stu-id="63ec4-1619">Info Field 3: Available packets</span></span>
- <span data-ttu-id="63ec4-1620">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1620">Info Field 4: Not used</span></span>

### <a name="rarp-disable"></a><span data-ttu-id="63ec4-1621">Отключение RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1621">RARP Disable</span></span> 

#### <a name="nx_rarp_disable"></a><span data-ttu-id="63ec4-1622">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1622">nx_rarp_disable</span></span>

<span data-ttu-id="63ec4-1623">**Значок** ![Значок отключения RARP](./media/user-guide/netx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1623">**Icon** ![R A R P disable icon](./media/user-guide/netx-events/image119.png)</span></span>

<span data-ttu-id="63ec4-1624">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1624">**Description**</span></span>

<span data-ttu-id="63ec4-1625">Это событие представляет собой отключение RARP через nx_rarp_disable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1625">This event represents disabling RARP via nx_rarp_disable.</span></span>

<span data-ttu-id="63ec4-1626">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1626">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1627">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1627">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1628">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1628">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1629">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1629">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1630">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1630">Info Field 4: Not used</span></span>

### <a name="rarp-enable"></a><span data-ttu-id="63ec4-1631">Включение RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1631">RARP Enable</span></span> 

#### <a name="nx_rarp_enable"></a><span data-ttu-id="63ec4-1632">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1632">nx_rarp_enable</span></span>

<span data-ttu-id="63ec4-1633">**Значок** ![Значок включения RARP](./media/user-guide/netx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1633">**Icon** ![R A R P enable icon](./media/user-guide/netx-events/image120.png)</span></span>

<span data-ttu-id="63ec4-1634">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1634">**Description**</span></span>

<span data-ttu-id="63ec4-1635">Это событие представляет собой включение RARP через nx_arp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1635">This event represents enabling RARP via nx_rarp_enable.</span></span>

<span data-ttu-id="63ec4-1636">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1636">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1637">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1637">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1638">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1638">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1639">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1639">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1640">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1640">Info Field 4: Not used</span></span>

### <a name="rarp-information-get"></a><span data-ttu-id="63ec4-1641">Получение сведений о RARP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1641">RARP Information Get</span></span> 

#### <a name="nx_rarp_info_get"></a><span data-ttu-id="63ec4-1642">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1642">nx_rarp_info_get</span></span>

<span data-ttu-id="63ec4-1643">**Значок** ![Значок получения сведений о RARP](./media/user-guide/netx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1643">**Icon** ![R A R P information get icon](./media/user-guide/netx-events/image121.png)</span></span>

<span data-ttu-id="63ec4-1644">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1644">**Description**</span></span>

<span data-ttu-id="63ec4-1645">Это событие представляет собой получение сведений о RARP с помощью nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1645">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="63ec4-1646">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1646">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1647">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1647">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1648">Поле сведений 2. Количество отправленных запросов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1648">Info Field 2: Requests sent</span></span>
- <span data-ttu-id="63ec4-1649">Поле сведений 3. Количество полученных ответов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1649">Info Field 3: Responses received</span></span>
- <span data-ttu-id="63ec4-1650">Поле сведений 4. Недопустимые ответы</span><span class="sxs-lookup"><span data-stu-id="63ec4-1650">Info Field 4: Invalid responses</span></span>

### <a name="system-initialize"></a><span data-ttu-id="63ec4-1651">Инициализация системы</span><span class="sxs-lookup"><span data-stu-id="63ec4-1651">System Initialize</span></span> 

#### <a name="nx_system_initialize"></a><span data-ttu-id="63ec4-1652">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="63ec4-1652">nx_system_initialize</span></span>

<span data-ttu-id="63ec4-1653">**Значок** ![Значок инициализации системы](./media/user-guide/netx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1653">**Icon** ![System initialize icon](./media/user-guide/netx-events/image122.png)</span></span>

<span data-ttu-id="63ec4-1654">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1654">**Description**</span></span>

<span data-ttu-id="63ec4-1655">Это событие представляет собой инициализацию NetX через nx_system_initialize.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1655">This event represents initializing NetX via nx_system_initialize.</span></span>

<span data-ttu-id="63ec4-1656">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1656">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1657">Поле сведений 1. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1657">Info Field 1: Not used</span></span>
- <span data-ttu-id="63ec4-1658">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1658">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1659">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1659">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1660">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1660">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-bind"></a><span data-ttu-id="63ec4-1661">Привязка сокета клиента TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1661">TCP Client Socket Bind</span></span> 

#### <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="63ec4-1662">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="63ec4-1662">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="63ec4-1663">**Значок** ![Значок привязки сокета клиента TCP](./media/user-guide/netx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1663">**Icon** ![T  P client socket bind icon](./media/user-guide/netx-events/image123.png)</span></span>

<span data-ttu-id="63ec4-1664">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1664">**Description**</span></span>

<span data-ttu-id="63ec4-1665">Это событие представляет собой привязку сокета клиента к порту с помощью nx_tcp_client_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1665">This event represents binding a client socket to a port via nx_tcp_client_socket_bind.</span></span>

<span data-ttu-id="63ec4-1666">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1666">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1667">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1667">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1668">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1668">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1669">Поле сведений 3. Запрошенный порт</span><span class="sxs-lookup"><span data-stu-id="63ec4-1669">Info Field 3: Port requested</span></span>
- <span data-ttu-id="63ec4-1670">Поле сведений 4. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1670">Info Field 4: Wait option</span></span>

### <a name="tcp-client-socket-connect"></a><span data-ttu-id="63ec4-1671">Подключение сокета клиента TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1671">TCP Client Socket Connect</span></span> 

#### <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="63ec4-1672">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="63ec4-1672">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="63ec4-1673">**Значок** ![Значок подключения сокета клиента TCP](./media/user-guide/netx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1673">**Icon** ![T C P client socket connect icon](./media/user-guide/netx-events/image124.png)</span></span>

<span data-ttu-id="63ec4-1674">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1674">**Description**</span></span>

<span data-ttu-id="63ec4-1675">Это событие представляет собой подключение сокета клиента через nx_tcp_client_socket_connect.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1675">This event represents making a client socket connection via nx_tcp_client_socket_connect.</span></span>

<span data-ttu-id="63ec4-1676">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1676">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1677">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1677">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1678">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1678">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1679">Поле сведений 3. IP-адрес сервера</span><span class="sxs-lookup"><span data-stu-id="63ec4-1679">Info Field 3: Server IP address</span></span>
- <span data-ttu-id="63ec4-1680">Поле сведений 4. Запрошенный порт сервера</span><span class="sxs-lookup"><span data-stu-id="63ec4-1680">Info Field 4: Server port requested</span></span>

### <a name="tcp-client-socket-port-get"></a><span data-ttu-id="63ec4-1681">Получение порта сокета клиента TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1681">TCP Client Socket Port Get</span></span> 

#### <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="63ec4-1682">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1682">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="63ec4-1683">**Значок** ![Значок получения порта сокета клиента TCP](./media/user-guide/netx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1683">**Icon** ![T C P client socket port get icon](./media/user-guide/netx-events/image125.png)</span></span>

<span data-ttu-id="63ec4-1684">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1684">**Description**</span></span>

<span data-ttu-id="63ec4-1685">Это событие представляет собой получение номера порта сокета клиента помощью nx_tcp_client_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1685">This event represents getting the client socket port number via nx_tcp_client_socket_port_get.</span></span>

<span data-ttu-id="63ec4-1686">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1686">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1687">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1687">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1688">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1688">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1689">Поле сведений 3. Номер порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1689">Info Field 3: Port number</span></span>
- <span data-ttu-id="63ec4-1690">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1690">Info Field 4: Not used</span></span>

### <a name="tcp-client-socket-unbind"></a><span data-ttu-id="63ec4-1691">Отмена привязки сокета клиента TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1691">TCP Client Socket Unbind</span></span> 

#### <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="63ec4-1692">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="63ec4-1692">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="63ec4-1693">**Значок** ![Значок отмены привязки сокета клиента TCP](./media/user-guide/netx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1693">**Icon** ![T C P client socket unbind icon](./media/user-guide/netx-events/image126.png)</span></span>

<span data-ttu-id="63ec4-1694">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1694">**Description**</span></span>

<span data-ttu-id="63ec4-1695">Это событие представляет собой отмену привязки порта, связанного с сокетом, через nx_tcp_client_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1695">This event represents unbinding the port associated with the socket via nx_tcp_client_socket_unbind.</span></span>

<span data-ttu-id="63ec4-1696">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1696">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1697">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1697">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1698">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1698">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1699">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1699">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1700">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1700">Info Field 4: Not used</span></span>

### <a name="tcp-enable"></a><span data-ttu-id="63ec4-1701">Включение TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1701">TCP Enable</span></span> 

#### <a name="nx_tcp_enable"></a><span data-ttu-id="63ec4-1702">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1702">nx_tcp_enable</span></span>

<span data-ttu-id="63ec4-1703">**Значок** ![Значок включения TCP](./media/user-guide/netx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1703">**Icon** ![T C P enable icon](./media/user-guide/netx-events/image127.png)</span></span>

<span data-ttu-id="63ec4-1704">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1704">**Description**</span></span>

<span data-ttu-id="63ec4-1705">Это событие представляет собой включение TCP через nx_tcp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1705">This event represents enabling TCP via nx_tcp_enable.</span></span>

<span data-ttu-id="63ec4-1706">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1706">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1707">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1707">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1708">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1708">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1709">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1709">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1710">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1710">Info Field 4: Not used</span></span>

###  <a name="tcp-free-port-find-tcp-free-port-find"></a><span data-ttu-id="63ec4-1711">Поиск свободных TCP-портов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1711">TCP Free Port Find TCP Free Port Find</span></span> 

#### <a name="nx_tcp_free_port_find"></a><span data-ttu-id="63ec4-1712">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="63ec4-1712">nx_tcp_free_port_find</span></span>

<span data-ttu-id="63ec4-1713">**Значок** ![Значок поиска свободных портов TCP](./media/user-guide/netx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1713">**Icon** ![T  CP free port find icon](./media/user-guide/netx-events/image128.png)</span></span>

<span data-ttu-id="63ec4-1714">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1714">**Description**</span></span>

<span data-ttu-id="63ec4-1715">Это событие представляет собой поиск свободного TCP-порта с помощью nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1715">This event represents finding a free TCP port via nx_tcp_free_port_find.</span></span>

<span data-ttu-id="63ec4-1716">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1716">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1717">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1717">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1718">Поле сведений 2. Запуск поиска номера порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1718">Info Field 2: Starting search port number</span></span>
- <span data-ttu-id="63ec4-1719">Поле сведений 3. Номер свободного порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1719">Info Field 3: Free port number</span></span>
- <span data-ttu-id="63ec4-1720">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1720">Info Field 4: Not used</span></span>

###  <a name="tcp-infomation-get"></a><span data-ttu-id="63ec4-1721">Получение сведений о TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1721">TCP Infomation Get</span></span> 

#### <a name="nx_tcp_info_get"></a><span data-ttu-id="63ec4-1722">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1722">nx_tcp_info_get</span></span>

<span data-ttu-id="63ec4-1723">**Значок** ![Значок получения сведений о TCP](./media/user-guide/netx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1723">**Icon** ![T C P infomation get icon](./media/user-guide/netx-events/image129.png)</span></span>

<span data-ttu-id="63ec4-1724">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1724">**Description**</span></span>

<span data-ttu-id="63ec4-1725">Это событие представляет собой получение сведений о TCP для указанного экземпляра IP с помощью nx_tcp_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1725">This event represents retrieving TCP information for the specified IP instance via nx_tcp_info_get.</span></span>

<span data-ttu-id="63ec4-1726">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1726">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1727">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1727">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1728">Поле сведений 2. Число отправленных байтов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1728">Info Field 2: Number of bytes sent</span></span>
- <span data-ttu-id="63ec4-1729">Поле сведений 3. Число полученных байтов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1729">Info Field 3: Number of bytes received</span></span>
- <span data-ttu-id="63ec4-1730">Поле сведений 4. Число недопустимых пакетов</span><span class="sxs-lookup"><span data-stu-id="63ec4-1730">Info Field 4: Number of invalid packets</span></span>

###  <a name="tcp-server-socket-accept"></a><span data-ttu-id="63ec4-1731">Принятие сокета сервера TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1731">TCP Server Socket Accept</span></span> 

#### <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="63ec4-1732">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="63ec4-1732">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="63ec4-1733">**Значок** ![Значок принятия сокета сервера TCP](./media/user-guide/netx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1733">**Icon** ![T C P server socket accept icon](./media/user-guide/netx-events/image130.png)</span></span>

<span data-ttu-id="63ec4-1734">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1734">**Description**</span></span>

<span data-ttu-id="63ec4-1735">Это событие представляет собой настройку сокета сервера после получения активного запроса на подключение через nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1735">This event represents setting up the server socket after an active connection request was received via nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="63ec4-1736">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1736">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1737">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1737">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1738">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1738">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1739">Поле сведений 3. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1739">Info Field 3: Wait option</span></span>
- <span data-ttu-id="63ec4-1740">Поле сведений 4. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1740">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-listen"></a><span data-ttu-id="63ec4-1741">Прослушивание сокета сервера TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1741">TCP Server Socket Listen</span></span> 

#### <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="63ec4-1742">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="63ec4-1742">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="63ec4-1743">**Значок** ![Значок прослушивания сервера TCP](./media/user-guide/netx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1743">**Icon** ![T C P server socket lsten icon](./media/user-guide/netx-events/image131.png)</span></span>

<span data-ttu-id="63ec4-1744">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1744">**Description**</span></span>

<span data-ttu-id="63ec4-1745">Это событие представляет собой регистрацию запроса на прослушивание и сокета сервера для указанного TCP-порта с помощью nx_tcp_server_socket_listen.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1745">This event represents register a listen request and a server socket for the specified TCP port via nx_tcp_server_socket_listen.</span></span>

<span data-ttu-id="63ec4-1746">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1746">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1747">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1747">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1748">Поле сведений 2. Номер TCP-порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1748">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="63ec4-1749">Поле сведений 3. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1749">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1750">Поле сведений 4. Максимальное число подключений, которые можно поставить в очередь</span><span class="sxs-lookup"><span data-stu-id="63ec4-1750">Info Field 4: Maximum number of connections that can be queued</span></span>

###  <a name="tcp-server-socket-relisten"></a><span data-ttu-id="63ec4-1751">Повторное прослушивание сокета сервера TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1751">TCP Server Socket Relisten</span></span> 

#### <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="63ec4-1752">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="63ec4-1752">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="63ec4-1753">**Значок** ![Значок повторного прослушивания сокета сервера TCP](./media/user-guide/netx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1753">**Icon** ![T C P server socket relisten icon](./media/user-guide/netx-events/image132.png)</span></span>

<span data-ttu-id="63ec4-1754">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1754">**Description**</span></span>

<span data-ttu-id="63ec4-1755">Это событие представляет собой регистрацию другого сокета сервера для существующего запроса на прослушивание по указанному TCP-порту с помощью nx_tcp_server_socket_relisten.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1755">This event represents register another server socket for an existing listen request on the specified TCP port via nx_tcp_server_socket_relisten.</span></span>

<span data-ttu-id="63ec4-1756">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1756">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1757">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1757">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1758">Поле сведений 2. Номер TCP-порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1758">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="63ec4-1759">Поле сведений 3. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1759">Info Field 3: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1760">Поле сведений 4. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1760">Info Field 4: Socket state</span></span>

###  <a name="tcp-server-socket-unaccept"></a><span data-ttu-id="63ec4-1761">Отклонение сокета сервера TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1761">TCP Server Socket Unaccept</span></span> 

#### <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="63ec4-1762">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="63ec4-1762">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="63ec4-1763">**Значок** ![Значок отклонения сокета сервера TCP](./media/user-guide/netx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1763">**Icon** ![T C P server socket unaccept icon](./media/user-guide/netx-events/image133.png)</span></span>

<span data-ttu-id="63ec4-1764">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1764">**Description**</span></span>

<span data-ttu-id="63ec4-1765">Это событие представляет собой удаление сокета сервера из связи с портом, получающим предыдущее пассивное подключение через nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1765">This event represents removing the server socket from association with the port receiving an earlier passive connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="63ec4-1766">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1766">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1767">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1767">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1768">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1768">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1769">Поле сведений 3. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1769">Info Field 3: Socket state</span></span>
- <span data-ttu-id="63ec4-1770">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1770">Info Field 4: Not used</span></span>

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a><span data-ttu-id="63ec4-1771">Отмена прослушивания сокета сервера TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1771">TCP Server Socket Unlisten TCP Server Socket Unlisten</span></span> 

#### <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="63ec4-1772">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="63ec4-1772">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="63ec4-1773">**Значок** ![Значок отмены прослушивания сервера TCP](./media/user-guide/netx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1773">**Icon** ![T C P server socket unlisten icon](./media/user-guide/netx-events/image134.png)</span></span>

<span data-ttu-id="63ec4-1774">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1774">**Description**</span></span>

<span data-ttu-id="63ec4-1775">Это событие представляет собой удаление предыдущего запроса на прослушивание для указанного TCP-порта с помощью nx_tcp_server_socket_unlisten.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1775">This event represents removing a previous listen request for the specified TCP port via nx_tcp_server_socket_unlisten.</span></span>

<span data-ttu-id="63ec4-1776">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1776">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1777">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1777">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1778">Поле сведений 2. Номер TCP-порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1778">Info Field 2: TCP port number</span></span>
- <span data-ttu-id="63ec4-1779">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1779">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1780">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1780">Info Field 4: Not used</span></span>

### <a name="tcp-socket-bytes-available"></a><span data-ttu-id="63ec4-1781">Доступные байты сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1781">TCP Socket Bytes Available</span></span> 

#### <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="63ec4-1782">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="63ec4-1782">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="63ec4-1783">**Значок** ![Значок доступных байтов сокета TCP](./media/user-guide/netx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1783">**Icon** ![T C P socket bytes available icon](./media/user-guide/netx-events/image135.png)</span></span>

<span data-ttu-id="63ec4-1784">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1784">**Description**</span></span>

<span data-ttu-id="63ec4-1785">Это событие представляет собой получение числа байтов, доступных в настоящее время в указанном сокете TCP, с помощью nx_tcp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1785">This event represents the number of bytes currently available on the specified TCP receiving socket via nx_tcp_socket_bytes_available.</span></span>

<span data-ttu-id="63ec4-1786">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1786">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1787">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1787">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1788">Поле сведений 2. Указатель на сокет TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1788">Info Field 2: Pointer to TCP socket</span></span>
- <span data-ttu-id="63ec4-1789">Поле сведений 3. Количество байтов, полученных для сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1789">Info Field 3: Bytes received on the socket</span></span>
- <span data-ttu-id="63ec4-1790">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1790">Info Field 4: Not used</span></span>

### <a name="tcp-socket-create"></a><span data-ttu-id="63ec4-1791">Создание сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1791">TCP Socket Create</span></span> 

#### <a name="nx_tcp_socket_create"></a><span data-ttu-id="63ec4-1792">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="63ec4-1792">nx_tcp_socket_create</span></span>

<span data-ttu-id="63ec4-1793">**Значок** ![Значок создания сокета TCP](./media/user-guide/netx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1793">**Icon** ![T C P socket create icon](./media/user-guide/netx-events/image136.png)</span></span>

<span data-ttu-id="63ec4-1794">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1794">**Description**</span></span>

<span data-ttu-id="63ec4-1795">Это событие представляет собой создание сокета TCP через nx_tcp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1795">This event represents creating a TCP socket via nx_tcp_socket_create.</span></span>

<span data-ttu-id="63ec4-1796">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1796">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1797">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1797">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1798">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1798">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1799">Поле сведений 3. Тип службы</span><span class="sxs-lookup"><span data-stu-id="63ec4-1799">Info Field 3: Type of service</span></span>
- <span data-ttu-id="63ec4-1800">Поле сведений 4. Размер окна приема</span><span class="sxs-lookup"><span data-stu-id="63ec4-1800">Info Field 4: Receive window size</span></span>

### <a name="tcp-socket-delete"></a><span data-ttu-id="63ec4-1801">Удаление сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1801">TCP Socket Delete</span></span> 

#### <a name="nx_tcp_socket_delete"></a><span data-ttu-id="63ec4-1802">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-1802">nx_tcp_socket_delete</span></span>

<span data-ttu-id="63ec4-1803">**Значок** ![Значок удаления сокета TCP](./media/user-guide/netx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1803">**Icon** ![T C P socket delete icon](./media/user-guide/netx-events/image137.png)</span></span>

<span data-ttu-id="63ec4-1804">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1804">**Description**</span></span>

<span data-ttu-id="63ec4-1805">Это событие представляет собой удаление сокета с помощью nx_tcp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1805">This event represents deleting a socket via nx_tcp_socket_delete.</span></span>

<span data-ttu-id="63ec4-1806">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1806">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1807">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1807">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1808">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1808">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1809">Поле сведений 3. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1809">Info Field 3: Socket state</span></span>
- <span data-ttu-id="63ec4-1810">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1810">Info Field 4: Not used</span></span>

### <a name="tcp-socket-disconnect"></a><span data-ttu-id="63ec4-1811">Отсоединение сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1811">TCP Socket Disconnect</span></span> 

#### <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="63ec4-1812">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="63ec4-1812">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="63ec4-1813">**Значок** ![Значок отсоединения сокета TCP](./media/user-guide/netx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1813">**Icon** ![T C P socket disconnect icon](./media/user-guide/netx-events/image138.png)</span></span>

<span data-ttu-id="63ec4-1814">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1814">**Description**</span></span>

<span data-ttu-id="63ec4-1815">Это событие представляет собой отсоединение сокета через nx_tcp_socket_disconnect.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1815">This event represents disconnecting a socket via nx_tcp_socket_disconnect.</span></span>

<span data-ttu-id="63ec4-1816">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1816">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1817">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1817">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1818">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1818">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1819">Поле сведений 3. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1819">Info Field 3: Wait option</span></span>
- <span data-ttu-id="63ec4-1820">Поле сведений 4. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1820">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-information-get"></a><span data-ttu-id="63ec4-1821">Получение сведений о сокете TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1821">TCP Socket Information Get</span></span> 

#### <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="63ec4-1822">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1822">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="63ec4-1823">**Значок** ![Значок получения сведений о сокете TCP](./media/user-guide/netx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1823">**Icon** ![T C P socket information get icon](./media/user-guide/netx-events/image139.png)</span></span>

<span data-ttu-id="63ec4-1824">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1824">**Description**</span></span>

<span data-ttu-id="63ec4-1825">Это событие представляет собой получение сведений о сокете через nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1825">This event represents getting information about a socket via nx_tcp_socket_info_get.</span></span>

<span data-ttu-id="63ec4-1826">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1826">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1827">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1827">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1828">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1828">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1829">Поле сведений 3. Количество байтов, отправленных через этот сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1829">Info Field 3: Bytes sent through this socket</span></span>
- <span data-ttu-id="63ec4-1830">Поле сведений 4. Количество байтов, полученных через этот сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1830">Info Field 4: Bytes received through this socket</span></span>

### <a name="tcp-socket-mss-get"></a><span data-ttu-id="63ec4-1831">Получение MSS сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1831">TCP Socket MSS Get</span></span> 

#### <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="63ec4-1832">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1832">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="63ec4-1833">**Значок** ![Значок получения MSS сокета TCP](./media/user-guide/netx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1833">**Icon** ![T C P socket M S S get icon](./media/user-guide/netx-events/image140.png)</span></span>

<span data-ttu-id="63ec4-1834">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1834">**Description**</span></span>

<span data-ttu-id="63ec4-1835">Это событие представляет собой получение MSS сокета через nx_tcp_socket_mss_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1835">This event represents getting the socket's MSS via nx_tcp_socket_mss_get.</span></span>

<span data-ttu-id="63ec4-1836">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1836">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1837">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1837">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1838">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1838">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1839">Поле сведений 3. Максимальный размер сегмента (MSS)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1839">Info Field 3: Maximum Segment Size (MSS)</span></span>
- <span data-ttu-id="63ec4-1840">Поле сведений 4. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1840">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-peer-get"></a><span data-ttu-id="63ec4-1841">Получение значения MSS однорангового узла сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1841">TCP Socket MSS Peer Get</span></span> 

#### <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="63ec4-1842">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1842">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="63ec4-1843">**Значок** ![Значок получения значения MSS однорангового узла сокета](./media/user-guide/netx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1843">**Icon** ![T C P socket M S S peer get icon](./media/user-guide/netx-events/image141.png)</span></span>

<span data-ttu-id="63ec4-1844">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1844">**Description**</span></span>

<span data-ttu-id="63ec4-1845">Это событие представляет собой получение значения MSS однорангового узла сокета через nx_tcp_socket_mss_peer_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1845">This event represents getting the MSS value of the socket's peer via nx_tcp_socket_mss_peer_get.</span></span>

<span data-ttu-id="63ec4-1846">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1846">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1847">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1847">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1848">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1848">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1849">Поле сведений 3. MSS однорангового узла</span><span class="sxs-lookup"><span data-stu-id="63ec4-1849">Info Field 3: Peer's MSS</span></span>
- <span data-ttu-id="63ec4-1850">Поле сведений 4. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1850">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-mss-set"></a><span data-ttu-id="63ec4-1851">Задание значения MSS сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1851">TCP Socket MSS Set</span></span> 

#### <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="63ec4-1852">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1852">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="63ec4-1853">**Значок** ![Значок задания значения MSS сокета TCP](./media/user-guide/netx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1853">**Icon** ![T C P socket M S S set icon](./media/user-guide/netx-events/image142.png)</span></span>

<span data-ttu-id="63ec4-1854">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1854">**Description**</span></span>

<span data-ttu-id="63ec4-1855">Это событие представляет собой задание значения MSS сокета через nx_tcp_socket_mss_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1855">This event represents setting a socket's MSS via nx_tcp_socket_mss_set.</span></span>

<span data-ttu-id="63ec4-1856">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1856">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1857">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1857">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1858">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1858">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1859">Поле сведений 3. MSS</span><span class="sxs-lookup"><span data-stu-id="63ec4-1859">Info Field 3: MSS</span></span>
- <span data-ttu-id="63ec4-1860">Поле сведений 4. Состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1860">Info Field 4: Socket state</span></span>

### <a name="tcp-socket-peer-info-get"></a><span data-ttu-id="63ec4-1861">Получение сведений об одноранговом узле сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1861">TCP Socket Peer Info Get</span></span> 

#### <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="63ec4-1862">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1862">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="63ec4-1863">**Значок** ![Значок получения сведений об одноранговом узле сокета TCP](./media/user-guide/netx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1863">**Icon** ![T C P socket peer info get icon](./media/user-guide/netx-events/image143.png)</span></span>

<span data-ttu-id="63ec4-1864">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1864">**Description**</span></span>

<span data-ttu-id="63ec4-1865">Это событие представляет собой извлечение из сокета TCP сведений относительно узла (например, узел подключения), IP-адреса и порта через nx_tcp_socket_peer_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1865">This event represents information retrieved from the TCP socket regarding the peer (e.g. >connecting host) IP address and port via nx_tcp_socket_peer_info_get.</span></span>

<span data-ttu-id="63ec4-1866">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1866">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1867">Поле сведений 1. Указатель на сокет TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1867">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="63ec4-1868">Поле сведений 2. IP-адрес однорангового узла</span><span class="sxs-lookup"><span data-stu-id="63ec4-1868">Info Field 2: Peer IP address</span></span>
- <span data-ttu-id="63ec4-1869">Поле сведений 3. Номер порта однорангового узла</span><span class="sxs-lookup"><span data-stu-id="63ec4-1869">Info Field 3: Peer port number</span></span>
- <span data-ttu-id="63ec4-1870">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1870">Info Field 4: Not used</span></span>

### <a name="tcp-socket-receive"></a><span data-ttu-id="63ec4-1871">Получение сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1871">TCP Socket Receive</span></span> 

#### <a name="nx_tcp_socket_receive"></a><span data-ttu-id="63ec4-1872">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="63ec4-1872">nx_tcp_socket_receive</span></span>

<span data-ttu-id="63ec4-1873">**Значок** ![Значок получения сокета TCP](./media/user-guide/netx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1873">**Icon** ![T C P socket receive icon](./media/user-guide/netx-events/image144.png)</span></span>

<span data-ttu-id="63ec4-1874">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1874">**Description**</span></span>

<span data-ttu-id="63ec4-1875">Это событие представляет собой получение данных от сокета через nx_tcp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1875">This event represents receiving data from a socket via nx_tcp_socket_receive.</span></span>

<span data-ttu-id="63ec4-1876">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1876">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1877">Поле сведений 1. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1877">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1878">Поле сведений 2. Указатель на полученный пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1878">Info Field 2: Pointer to received packet</span></span>
- <span data-ttu-id="63ec4-1879">Поле сведений 3. Длина полученного пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1879">Info Field 3: Received packet length</span></span>
- <span data-ttu-id="63ec4-1880">Поле сведений 4. Получение порядкового номера</span><span class="sxs-lookup"><span data-stu-id="63ec4-1880">Info Field 4: Receive sequence number</span></span>

### <a name="tcp-socket-receive-notify"></a><span data-ttu-id="63ec4-1881">Уведомление о получении сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1881">TCP Socket Receive Notify</span></span> 

#### <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="63ec4-1882">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="63ec4-1882">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="63ec4-1883">**Значок** ![Значок уведомления о получении сокета TCP](./media/user-guide/netx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1883">**Icon** ![T C P socket receive notify icon](./media/user-guide/netx-events/image145.png)</span></span>

<span data-ttu-id="63ec4-1884">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1884">**Description**</span></span>

<span data-ttu-id="63ec4-1885">Это событие представляет собой регистрацию обратного вызова уведомления о получении сокета через nx_tcp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1885">This event represents registering a receive notify callback for a socket via nx_tcp_socket_receive_notify.</span></span>

<span data-ttu-id="63ec4-1886">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1886">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1887">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1887">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1888">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1888">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1889">Поле сведений 3. Указатель обратный вызов уведомления о получении. Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1889">Info Field 3: Pointer to receive notify callback Info Field 4: Not used</span></span>

### <a name="tcp-socket-send"></a><span data-ttu-id="63ec4-1890">Отправка сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1890">TCP Socket Send</span></span> 

#### <a name="nx_tcp_socket_send"></a><span data-ttu-id="63ec4-1891">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-1891">nx_tcp_socket_send</span></span>

<span data-ttu-id="63ec4-1892">**Значок** ![Значок отправки сокета TCP](./media/user-guide/netx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1892">**Icon** ![T C P socket send icon](./media/user-guide/netx-events/image146.png)</span></span>

<span data-ttu-id="63ec4-1893">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1893">**Description**</span></span>

<span data-ttu-id="63ec4-1894">Это событие представляет собой отправку данных через сокет с помощью nx_tcp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1894">This event represents sending data on a socket via nx_tcp_socket_send.</span></span>

<span data-ttu-id="63ec4-1895">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1895">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1896">Поле сведений 1. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1896">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1897">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1897">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-1898">Поле сведений 3. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1898">Info Field 3: Length of packet</span></span>
- <span data-ttu-id="63ec4-1899">Поле сведений 4. Порядковый номер передачи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1899">Info Field 4: Transmit sequence number</span></span>

### <a name="tcp-socket-state-wait"></a><span data-ttu-id="63ec4-1900">Пребывание в состоянии ожидания для сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1900">TCP Socket State Wait</span></span> 

#### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="63ec4-1901">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1901">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="63ec4-1902">**Значок** ![Значок пребывания в состоянии ожидания для сокета TCP](./media/user-guide/netx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1902">**Icon** ![T C P socket state wait icon](./media/user-guide/netx-events/image147.png)</span></span>

<span data-ttu-id="63ec4-1903">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1903">**Description**</span></span>

<span data-ttu-id="63ec4-1904">Это событие представляет собой ожидание сокетом на переход в определенное состояние через nx_tcp_socket_state_wait.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1904">This event represents waiting for a socket to enter a particular state via nx_tcp_socket_state_wait.</span></span>

<span data-ttu-id="63ec4-1905">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1905">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1906">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1906">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1907">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1907">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1908">Поле сведений 3. Требуемое состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1908">Info Field 3: Desired socket state</span></span>
- <span data-ttu-id="63ec4-1909">Поле сведений 4. Предыдущее состояние сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1909">Info Field 4: Previous socket state</span></span>

### <a name="tcp-socket-transmit-configure"></a><span data-ttu-id="63ec4-1910">Настройка передачи сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1910">TCP Socket Transmit Configure</span></span> 

#### <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="63ec4-1911">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="63ec4-1911">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="63ec4-1912">**Значок** ![Значок настройки передачи сокета TCP](./media/user-guide/netx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1912">**Icon** ![T C P socket transmit configure icon](./media/user-guide/netx-events/image148.png)</span></span>

<span data-ttu-id="63ec4-1913">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1913">**Description**</span></span>

<span data-ttu-id="63ec4-1914">Это событие представляет собой настройку параметров передачи сокета через nx_tcp_socket_transmit_configure.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1914">This event represents configuring the transmit options for a socket via nx_tcp_socket_transmit_configure.</span></span>

<span data-ttu-id="63ec4-1915">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1915">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1916">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1916">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1917">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1917">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1918">Поле сведений 3. Длина очереди передачи</span><span class="sxs-lookup"><span data-stu-id="63ec4-1918">Info Field 3: Transmit queue depth</span></span>
- <span data-ttu-id="63ec4-1919">Поле сведений 4. Значение времени ожидания</span><span class="sxs-lookup"><span data-stu-id="63ec4-1919">Info Field 4: Timeout value</span></span>

### <a name="tcp-socket-window-update-notify-set"></a><span data-ttu-id="63ec4-1920">Установка уведомления об обновлении окна сокета TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1920">TCP Socket Window Update Notify Set</span></span> 

#### <a name="nx_tcp_window_update_notify_set"></a><span data-ttu-id="63ec4-1921">nx_tcp_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-1921">nx_tcp_window_update_notify_set</span></span>

<span data-ttu-id="63ec4-1922">**Значок** ![Значок установки уведомления об обновлении окна сокета TCP](./media/user-guide/netx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1922">**Icon** ![T C P socket window update notify set icon](./media/user-guide/netx-events/image149.png)</span></span>

<span data-ttu-id="63ec4-1923">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1923">**Description**</span></span>

<span data-ttu-id="63ec4-1924">Это событие представляет собой TCP-сокет, получающий уведомление об увеличении окна приема на удаленном узле через nx_tcp_window_update_notify_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1924">This event represents a TCP socket receiving notification of an increase in the remote host receive window via nx_tcp_window_update_notify_set.</span></span>

<span data-ttu-id="63ec4-1925">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1925">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1926">Поле сведений 1. Указатель на сокет TCP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1926">Info Field 1: Pointer to TCP socket</span></span>
- <span data-ttu-id="63ec4-1927">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1927">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1928">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1928">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1929">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1929">Info Field 4: Not used</span></span>

### <a name="udp-enable"></a><span data-ttu-id="63ec4-1930">Включение UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1930">UDP Enable</span></span> 

#### <a name="nx_udp_enable"></a><span data-ttu-id="63ec4-1931">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1931">nx_udp_enable</span></span>

<span data-ttu-id="63ec4-1932">**Значок** ![Значок включения UDP](./media/user-guide/netx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1932">**Icon** ![U D P enable icon](./media/user-guide/netx-events/image150.png)</span></span>

<span data-ttu-id="63ec4-1933">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1933">**Description**</span></span>

<span data-ttu-id="63ec4-1934">Это событие представляет собой включение UDP через nx_udp_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1934">This event represents enabling UDP via nx_udp_enable.</span></span>

<span data-ttu-id="63ec4-1935">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1935">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1936">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1936">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1937">Поле сведений 2. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1937">Info Field 2: Not used</span></span>
- <span data-ttu-id="63ec4-1938">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1938">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1939">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1939">Info Field 4: Not used</span></span>

### <a name="udp-free-port-find"></a><span data-ttu-id="63ec4-1940">Поиск свободных портов UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1940">UDP Free Port Find</span></span> 

#### <a name="nx_udp_free_port_find"></a><span data-ttu-id="63ec4-1941">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="63ec4-1941">nx_udp_free_port_find</span></span>

<span data-ttu-id="63ec4-1942">**Значок** ![Значок поиска свободных портов UDP](./media/user-guide/netx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1942">**Icon** ![U D P free port find icon](./media/user-guide/netx-events/image151.png)</span></span>

<span data-ttu-id="63ec4-1943">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1943">**Description**</span></span>

<span data-ttu-id="63ec4-1944">Это событие представляет собой поиск свободного UDP-порта с помощью nx_tcp_free_port_find.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1944">This event represents finding a free UDP port via nx_udp_free_port_find.</span></span>

<span data-ttu-id="63ec4-1945">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1945">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1946">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1946">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1947">Поле сведений 2. Запуск порта для поиска</span><span class="sxs-lookup"><span data-stu-id="63ec4-1947">Info Field 2: Starting port to search from</span></span>
- <span data-ttu-id="63ec4-1948">Поле сведений 3. Свободный порт</span><span class="sxs-lookup"><span data-stu-id="63ec4-1948">Info Field 3: Free port</span></span>
- <span data-ttu-id="63ec4-1949">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1949">Info Field 4: Not used</span></span>

### <a name="udp-information-get"></a><span data-ttu-id="63ec4-1950">Получение сведений о UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1950">UDP Information Get</span></span> 

#### <a name="nx_udp_info_get"></a><span data-ttu-id="63ec4-1951">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-1951">nx_udp_info_get</span></span>

<span data-ttu-id="63ec4-1952">**Значок** ![Значок получения сведений о UDP](./media/user-guide/netx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1952">**Icon** ![U D P information get icon](./media/user-guide/netx-events/image152.png)</span></span>

<span data-ttu-id="63ec4-1953">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1953">**Description**</span></span>

<span data-ttu-id="63ec4-1954">Это событие представляет собой получение сведений о UDP с помощью nx_udp_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1954">This event represents getting information via nx_udp_info_get.</span></span>

<span data-ttu-id="63ec4-1955">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1955">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1956">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1956">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1957">Поле сведений 2. Количество отправленных байтов UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1957">Info Field 2: UDP bytes sent</span></span>
- <span data-ttu-id="63ec4-1958">Поле сведений 3. Количество полученных байтов UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1958">Info Field 3: UDP bytes received</span></span>
- <span data-ttu-id="63ec4-1959">Поле сведений 4. Недопустимые пакеты</span><span class="sxs-lookup"><span data-stu-id="63ec4-1959">Info Field 4: Invalid packets</span></span>

### <a name="udp-socket-bind"></a><span data-ttu-id="63ec4-1960">Привязка UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1960">UDP Socket Bind</span></span> 

#### <a name="nx_udp_socket_bind"></a><span data-ttu-id="63ec4-1961">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="63ec4-1961">nx_udp_socket_bind</span></span>

<span data-ttu-id="63ec4-1962">**Значок** ![Значок привязки UDP-сокета](./media/user-guide/netx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1962">**Icon** ![U D P socket bind icon](./media/user-guide/netx-events/image153.png)</span></span>

<span data-ttu-id="63ec4-1963">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1963">**Description**</span></span>

<span data-ttu-id="63ec4-1964">Это событие представляет собой привязку UDP-сокета к порту с помощью nx_udp_socket_bind.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1964">This event represents binding a UDP socket to a port via nx_udp_socket_bind.</span></span>

<span data-ttu-id="63ec4-1965">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1965">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1966">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1966">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1967">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1967">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1968">Поле сведений 3. Номер порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-1968">Info Field 3: Port number</span></span>
- <span data-ttu-id="63ec4-1969">Поле сведений 4. Параметр Wait</span><span class="sxs-lookup"><span data-stu-id="63ec4-1969">Info Field 4: Wait option</span></span>

### <a name="udp-socket-bytes-available"></a><span data-ttu-id="63ec4-1970">Доступные байты UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1970">UDP Socket Bytes Available</span></span> 

#### <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="63ec4-1971">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="63ec4-1971">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="63ec4-1972">**Значок** ![Значок доступных байтов UDP-сокета](./media/user-guide/netx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1972">**Icon** ![U D P socket bytes available icon](./media/user-guide/netx-events/image154.png)</span></span>

<span data-ttu-id="63ec4-1973">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1973">**Description**</span></span>

<span data-ttu-id="63ec4-1974">Это событие представляет собой текущее число байтов, полученных через сокет UDP с помощью nx_udp_socket_bytes_available.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1974">This event represents the current number of bytes received on the UDP socket via nx_udp_socket_bytes_available.</span></span>

<span data-ttu-id="63ec4-1975">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1975">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1976">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1976">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1977">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1977">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1978">Поле сведений 3. Количество байтов, полученных для сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1978">Info Field 3: Bytes received on socket</span></span>
- <span data-ttu-id="63ec4-1979">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1979">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-disable"></a><span data-ttu-id="63ec4-1980">Отключение контрольной суммы UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1980">UDP Socket Checksum Disable</span></span> 

#### <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="63ec4-1981">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1981">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="63ec4-1982">**Значок** ![Значок отключения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1982">**Icon** ![U D P socket checksum disable icon](./media/user-guide/netx-events/image155.png)</span></span>

<span data-ttu-id="63ec4-1983">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1983">**Description**</span></span>

<span data-ttu-id="63ec4-1984">Это событие представляет собой отключение контрольной суммы для данных в сокете UDP через nx_udp_socket_checksum_disable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1984">This event represents disabling the checksum for data on a UDP socket via nx_udp_socket_checksum_disable.</span></span>

<span data-ttu-id="63ec4-1985">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1985">**Information Fields**</span></span> 

- <span data-ttu-id="63ec4-1986">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1986">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1987">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1987">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1988">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1988">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1989">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1989">Info Field 4: Not used</span></span>

### <a name="udp-socket-checksum-enable"></a><span data-ttu-id="63ec4-1990">Включение контрольной суммы UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-1990">UDP Socket Checksum Enable</span></span> 

#### <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="63ec4-1991">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="63ec4-1991">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="63ec4-1992">**Значок** ![Значок включения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-1992">**Icon** ![U D P socket checksum enable icon](./media/user-guide/netx-events/image156.png)</span></span>

<span data-ttu-id="63ec4-1993">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1993">**Description**</span></span>

<span data-ttu-id="63ec4-1994">Это событие представляет собой включение обработки контрольной суммы в сокете с помощью nx_udp_socket_checksum_enable.</span><span class="sxs-lookup"><span data-stu-id="63ec4-1994">This event represents enabling checksum processing on a socket via nx_udp_socket_checksum_enable.</span></span>

<span data-ttu-id="63ec4-1995">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-1995">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-1996">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-1996">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-1997">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-1997">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-1998">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1998">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-1999">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-1999">Info Field 4: Not used</span></span>

### <a name="udp-socket-create"></a><span data-ttu-id="63ec4-2000">Создание UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2000">UDP Socket Create</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="63ec4-2001">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="63ec4-2001">nx_udp_socket_create</span></span>

<span data-ttu-id="63ec4-2002">**Значок** ![Значок создания UDP-сокета](./media/user-guide/netx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2002">**Icon** ![U D P socket create icon](./media/user-guide/netx-events/image157.png)</span></span>

<span data-ttu-id="63ec4-2003">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2003">**Description**</span></span>

<span data-ttu-id="63ec4-2004">Это событие представляет собой создание UDP-сокета с помощью nx_udp_socket_create.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2004">This event represents creating a UDP socket via nx_udp_socket_create.</span></span>

<span data-ttu-id="63ec4-2005">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2005">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2006">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2006">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2007">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2007">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-2008">Поле сведений 3. Тип службы</span><span class="sxs-lookup"><span data-stu-id="63ec4-2008">Info Field 3: Type of service</span></span>
- <span data-ttu-id="63ec4-2009">Поле сведений 4. Максимальная очередь получения</span><span class="sxs-lookup"><span data-stu-id="63ec4-2009">Info Field 4: Maximum receive queue</span></span>

### <a name="udp-socket-delete-event"></a><span data-ttu-id="63ec4-2010">Событие удаления UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2010">UDP Socket Delete Event</span></span> 

#### <a name="nx_udp_socket_delete-event"></a><span data-ttu-id="63ec4-2011">Событие nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="63ec4-2011">nx_udp_socket_delete event</span></span>

<span data-ttu-id="63ec4-2012">**Значок** ![Значок события удаления UDP-сокета](./media/user-guide/netx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2012">**Icon** ![U D P socket delete event icon](./media/user-guide/netx-events/image158.png)</span></span>

<span data-ttu-id="63ec4-2013">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2013">**Description**</span></span>

<span data-ttu-id="63ec4-2014">Это событие представляет собой удаление UDP-сокета с помощью nx_tcp_socket_delete.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2014">This event represents deleting a UDP socket via nx_udp_socket_delete.</span></span>

<span data-ttu-id="63ec4-2015">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2015">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2016">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2016">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2017">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2017">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-2018">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2018">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-2019">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2019">Info Field 4: Not used</span></span>

### <a name="udp-socket-information-get-event"></a><span data-ttu-id="63ec4-2020">Событие получения сведений о сокете UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2020">UDP Socket Information Get Event</span></span> 

#### <a name="nx_udp_socket_info_get-event"></a><span data-ttu-id="63ec4-2021">Событие nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-2021">nx_udp_socket_info_get event</span></span>

<span data-ttu-id="63ec4-2022">**Значок** ![Значок события получения сведений о сокете UDP](./media/user-guide/netx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2022">**Icon** ![U D P socket information get event icon](./media/user-guide/netx-events/image159.png)</span></span>

<span data-ttu-id="63ec4-2023">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2023">**Description**</span></span>

<span data-ttu-id="63ec4-2024">Это событие представляет собой получение сведений о сокете UDP через nx_tcp_socket_info_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2024">This event represents getting information about a UDP socket via nx_udp_socket_info_get.</span></span>

<span data-ttu-id="63ec4-2025">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2025">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2026">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2026">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2027">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2027">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-2028">Поле сведений 3. Количество байтов, отправленных через сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2028">Info Field 3: Bytes sent through socket</span></span>
- <span data-ttu-id="63ec4-2029">Поле сведений 4. Количество байтов, полученных через сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2029">Info Field 4: Bytes received through socket</span></span>

### <a name="udp-socket-interface-set"></a><span data-ttu-id="63ec4-2030">Установка интерфейса сокетов UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2030">UDP Socket Interface Set</span></span> 

#### <a name="nx_udp_socket_interface_set-event"></a><span data-ttu-id="63ec4-2031">Событие nx_udp_socket_interface_set</span><span class="sxs-lookup"><span data-stu-id="63ec4-2031">nx_udp_socket_interface_set event</span></span>

<span data-ttu-id="63ec4-2032">**Значок** ![Значок установки интерфейса сокетов UDP](./media/user-guide/netx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2032">**Icon** ![U D P socket interface set icon](./media/user-guide/netx-events/image160.png)</span></span>

<span data-ttu-id="63ec4-2033">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2033">**Description**</span></span>

<span data-ttu-id="63ec4-2034">Это событие представляет собой установку исходящего интерфейса указанного UDP-сокета с указанным интерфейсом через nx_udp_socket_interface_set.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2034">This event represents setting the outgoing interface of the specified UDP socket with the specified interface via nx_udp_socket_interface_set.</span></span>

<span data-ttu-id="63ec4-2035">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2035">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2036">Поле сведений 1. Указатель на сокет UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2036">Info Field 1: Pointer to UDP socket</span></span>
- <span data-ttu-id="63ec4-2037">Поле сведений 2. Индекс, соответствующий интерфейсу для сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2037">Info Field 2: Index corresponding to the interface for the socket</span></span>
- <span data-ttu-id="63ec4-2038">Поле сведений 3. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2038">Info Field 3: Not used</span></span>
- <span data-ttu-id="63ec4-2039">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2039">Info Field 4: Not used</span></span>

### <a name="udp-socket-port-get"></a><span data-ttu-id="63ec4-2040">Получение порта UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2040">UDP Socket Port Get</span></span> 

#### <a name="nx_udp_socket_port_get"></a><span data-ttu-id="63ec4-2041">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="63ec4-2041">nx_udp_socket_port_get</span></span>

<span data-ttu-id="63ec4-2042">**Значок** ![Значок получения порта UDP-сокета](./media/user-guide/netx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2042">**Icon** ![U D P socket port get icon](./media/user-guide/netx-events/image161.png)</span></span>

<span data-ttu-id="63ec4-2043">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2043">**Description**</span></span>

<span data-ttu-id="63ec4-2044">Это событие представляет собой получение UDP-порта, к которому привязан указанный сокет UDP, через nx_udp_socket_port_get.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2044">This event represents retrieving the UDP port the specified UDP socket is bound to via nx_udp_socket_port_get.</span></span>

<span data-ttu-id="63ec4-2045">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2045">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2046">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2046">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2047">Поле сведений 2. Указатель на сокет UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2047">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="63ec4-2048">Поле сведений 3. Номер порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-2048">Info Field 3: Port number</span></span>
- <span data-ttu-id="63ec4-2049">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2049">Info Field 4: Not used</span></span>

### <a name="udp-socket-receive"></a><span data-ttu-id="63ec4-2050">Получение UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2050">UDP Socket Receive</span></span> 

#### <a name="nx_udp_socket_receive"></a><span data-ttu-id="63ec4-2051">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="63ec4-2051">nx_udp_socket_receive</span></span>

<span data-ttu-id="63ec4-2052">**Значок** ![Значок получения UDP-сокета](./media/user-guide/netx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2052">**Icon** ![U D P socket receive icon](./media/user-guide/netx-events/image162.png)</span></span>

<span data-ttu-id="63ec4-2053">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2053">**Description**</span></span>

<span data-ttu-id="63ec4-2054">Это событие представляет собой получение данных по указанному сокету UDP через nx_udp_socket_receive.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2054">This event represents receiving data on the specified UDP socket via nx_udp_socket_receive.</span></span>

<span data-ttu-id="63ec4-2055">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2055">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2056">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2056">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2057">Поле сведений 2. Указатель на сокет UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2057">Info Field 2: Pointer to UDP socket</span></span>
- <span data-ttu-id="63ec4-2058">Поле сведений 3. Указатель на полученный пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2058">Info Field 3: Pointer to received packet</span></span>
- <span data-ttu-id="63ec4-2059">Поле сведений 4. Размер полученного пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2059">Info Field 4: Received packet size</span></span>

### <a name="udp-socket-receive-notify"></a><span data-ttu-id="63ec4-2060">Уведомление о получении UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2060">UDP Socket Receive Notify</span></span> 

#### <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="63ec4-2061">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="63ec4-2061">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="63ec4-2062">**Значок** ![Значок уведомления о получении UDP-сокета](./media/user-guide/netx-events/image163.png) **Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2062">**Icon** ![U D P socket receive notify icon](./media/user-guide/netx-events/image163.png)s **Description**</span></span>

<span data-ttu-id="63ec4-2063">Это событие представляет собой регистрацию обратного вызова уведомления о получении через nx_udp_socket_receive_notify.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2063">This event represents registering a receive notify callback via nx_udp_socket_receive_notify.</span></span>

<span data-ttu-id="63ec4-2064">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2064">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2065">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2065">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2066">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2066">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-2067">Поле сведений 3. Указатель на функцию получения уведомлений. Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2067">Info Field 3: Pointer to receive notify function Info Field 4: Not used</span></span>

### <a name="udp-socket-send"></a><span data-ttu-id="63ec4-2068">Отправка UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2068">UDP Socket Send</span></span> 

#### <a name="nx_udp_socket_send"></a><span data-ttu-id="63ec4-2069">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="63ec4-2069">nx_udp_socket_send</span></span>

<span data-ttu-id="63ec4-2070">**Значок** ![Значок отправки UDP-сокета](./media/user-guide/netx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2070">**Icon** ![U D P socket send icon](./media/user-guide/netx-events/image164.png)</span></span>

<span data-ttu-id="63ec4-2071">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2071">**Description**</span></span>

<span data-ttu-id="63ec4-2072">Это событие представляет собой отправку данных через сокет UDP с помощью nx_udp_socket_send.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2072">This event represents sending data through a UDP socket via nx_udp_socket_send.</span></span>

<span data-ttu-id="63ec4-2073">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2073">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2074">Поле сведений 1. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2074">Info Field 1: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-2075">Поле сведений 2. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2075">Info Field 2: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-2076">Поле сведений 3. Длина пакета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2076">Info Field 3: Packet length</span></span>
- <span data-ttu-id="63ec4-2077">Поле сведений 4. IP-адрес пункта назначения</span><span class="sxs-lookup"><span data-stu-id="63ec4-2077">Info Field 4: Destination IP address</span></span>

### <a name="udp-socket-unbind"></a><span data-ttu-id="63ec4-2078">Отмена привязки UDP-сокета</span><span class="sxs-lookup"><span data-stu-id="63ec4-2078">UDP Socket Unbind</span></span> 

#### <a name="nx_udp_socket_unbind"></a><span data-ttu-id="63ec4-2079">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="63ec4-2079">nx_udp_socket_unbind</span></span>

<span data-ttu-id="63ec4-2080">**Значок** ![Значок отмены привязки UDP-сокета](./media/user-guide/netx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2080">**Icon** ![U D P socket unbind icon](./media/user-guide/netx-events/image165.png)</span></span>

<span data-ttu-id="63ec4-2081">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2081">**Description**</span></span>

<span data-ttu-id="63ec4-2082">Это событие представляет собой отмену привязки UDP-порта к сокету через nx_udp_socket_unbind.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2082">This event represents unbinding a UDP port with a socket via nx_udp_socket_unbind.</span></span>

<span data-ttu-id="63ec4-2083">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2083">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2084">Поле сведений 1. Указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2084">Info Field 1: Pointer to IP instance</span></span>
- <span data-ttu-id="63ec4-2085">Поле сведений 2. Указатель на сокет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2085">Info Field 2: Pointer to socket</span></span>
- <span data-ttu-id="63ec4-2086">Поле сведений 3. Номер порта</span><span class="sxs-lookup"><span data-stu-id="63ec4-2086">Info Field 3: Port number</span></span>
- <span data-ttu-id="63ec4-2087">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2087">Info Field 4: Not used</span></span>

### <a name="udp-source-extract"></a><span data-ttu-id="63ec4-2088">Извлечение источника UDP</span><span class="sxs-lookup"><span data-stu-id="63ec4-2088">UDP Source Extract</span></span> 

#### <a name="nx_udp_socket_create"></a><span data-ttu-id="63ec4-2089">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="63ec4-2089">nx_udp_socket_create</span></span>

<span data-ttu-id="63ec4-2090">**Значок** ![Значок извлечения источника UDP](./media/user-guide/netx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="63ec4-2090">**Icon** ![U D P source extract icon](./media/user-guide/netx-events/image166.png)</span></span>

<span data-ttu-id="63ec4-2091">**Описание**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2091">**Description**</span></span>

<span data-ttu-id="63ec4-2092">Это событие представляет собой получение IP-адреса и номера порта полученного пакета UDP через nx_udp_source_extract.</span><span class="sxs-lookup"><span data-stu-id="63ec4-2092">This event represents getting the IP address and port number of a received UDP packet via nx_udp_source_extract.</span></span>

<span data-ttu-id="63ec4-2093">**Поля сведений**</span><span class="sxs-lookup"><span data-stu-id="63ec4-2093">**Information Fields**</span></span>

- <span data-ttu-id="63ec4-2094">Поле сведений 1. Указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="63ec4-2094">Info Field 1: Pointer to packet</span></span>
- <span data-ttu-id="63ec4-2095">Поле сведений 2. IP-адрес отправителя</span><span class="sxs-lookup"><span data-stu-id="63ec4-2095">Info Field 2: Sender's IP address</span></span>
- <span data-ttu-id="63ec4-2096">Поле сведений 3. Номер порта отправителя</span><span class="sxs-lookup"><span data-stu-id="63ec4-2096">Info Field 3: Sender's port number</span></span>
- <span data-ttu-id="63ec4-2097">Поле сведений 4. Не используется</span><span class="sxs-lookup"><span data-stu-id="63ec4-2097">Info Field 4: Not used</span></span>