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
# <a name="chapter-8---azure-rtos-netx-trace-events"></a>Глава 8. События трассировки NetX в ОСРВ Azure

В этой главе содержится описание событий NetX в ОСРВ Azure. 

## <a name="list-of-events-and-icons"></a>Список событий и значков

Ниже приведен список событий NetX, отображаемых в TraceX.

| Значок                                           | Значение                 |
| -------------------------------- | ------------------------------------- |
| ![Значок получения внутренних запросов ARP](./media/user-guide/netx-events/image1.png)    | Получение внутренних запросов ARP |
| ![Значок отправки внутренних запросов ARP](./media/user-guide/netx-events/image2.png)    | Отправка внутренних запросов ARP |
| ![Значок получения внутреннего ответа ARP](./media/user-guide/netx-events/image3.png)    | Получение внутреннего ответа ARP |
| ![Значок отправки внутреннего ответа ARP](./media/user-guide/netx-events/image4.png)    | Отправка внутреннего ответа ARP |
| ![Значок получения внутреннего протокола ICMP](./media/user-guide/netx-events/image5.png)    | Получение внутреннего протокола ICMP |
| ![Значок отправки внутреннего протокола ICMP](./media/user-guide/netx-events/image6.png)    | Отправка внутреннего протокола ICMP |
| ![Значок получения внутреннего протокола IGMP NetX](./media/user-guide/netx-events/image7.png)    | Получение внутреннего протокола IGMP NetX |
| ![Значок получения внутреннего IP](./media/user-guide/netx-events/image8.png)    | Получение внутреннего IP |
| ![Значок отправки внутреннего IP](./media/user-guide/netx-events/image9.png)    | Отправка внутреннего IP |
| ![Значок получения данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image10.png)    | Получение данных по внутреннему протоколу TCP |
| ![Значок отправки данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image11.png)    | Отправка данных по внутреннему протоколу TCP |
| ![Значок получения флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image12.png)    | Получение флага FIN внутреннего протокола TCP |
| ![Значок отправки флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image13.png)    | Отправка флага FIN внутреннего протокола TCP |
| ![Значок получения флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image14.png)    | Получение флага RST внутреннего протокола TCP |
| ![Значок отправки флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image15.png)    | Отправка флага RST внутреннего протокола TCP |
| ![Значок получения SYN внутреннего TCP](./media/user-guide/netx-events/image16.png)    | Получение SYN внутреннего TCP |
| ![Значок отправки SYN внутреннего TCP](./media/user-guide/netx-events/image17.png)    | Отправка SYN внутреннего TCP |
| ![Значок получения внутреннего протокола UDP](./media/user-guide/netx-events/image18.png)    | Получение внутреннего протокола UDP |
| ![Значок отправки внутреннего протокола UDP](./media/user-guide/netx-events/image19.png)    | Отправка внутреннего протокола UDP |
| ![Значок получения внутреннего протокола RARP](./media/user-guide/netx-events/image20.png)    | Получение внутреннего протокола RARP |
| ![Значок отправки внутреннего протокола RARP](./media/user-guide/netx-events/image21.png)    | Отправка внутреннего протокола RARP |
| ![Значок повторной попытки подключения по внутреннему протоколу TCP](./media/user-guide/netx-events/image22.png)    | Повторная попытка подключения по внутреннему протоколу TCP |
| ![Значок изменения состояния внутреннего протокола TCP](./media/user-guide/netx-events/image23.png)    | Изменение состояния внутреннего протокола TCP |
| ![Значок отправки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image24.png)    | Отправка пакета внутреннего драйвера устройств ввода-вывода |
| ![icon](./media/user-guide/netx-events/image25.png)    | Инициализация внутреннего драйвера устройств ввода-вывода |
| ![Значок инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image26.png)    | Включение ссылки на внутренний драйвер устройств ввода-вывода |
| ![Значок отключения ссылки на внутренний драйвер устройств ввода-вывода](./media/user-guide/netx-events/image27.png)    | Отключение ссылки на внутренний драйвер устройств ввода-вывода |
| ![Значок широковещательной рассылки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image28.png)    | Широковещательная рассылка пакета внутреннего драйвера устройств ввода-вывода |
| ![Значок отправки ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image29.png)    | Отправка ARP для внутреннего драйвера устройств ввода-вывода |
| ![Значок отправки ответа ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image30.png)    | Отправка ответа ARP для внутреннего драйвера устройств ввода-вывода |
| ![Значок отправки RARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image31.png)    | Отправка RARP для внутреннего драйвера устройств ввода-вывода |
| ![Значок подключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image32.png)    | Подключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода |
| ![Значок отключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image33.png)    | Отключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода |
| ![Значок получения состояния внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image34.png)    | Получение состояния внутреннего драйвера устройств ввода-вывода |
| ![Значок получения скорости внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image35.png)    | Получение скорости внутреннего драйвера устройств ввода-вывода |
| ![Значок получения дуплексного типа внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image36.png)    | Получение дуплексного типа внутреннего драйвера устройств ввода-вывода |
| ![Значок получения количества ошибок внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image37.png)    | Получение количества ошибок внутреннего драйвера устройств ввода-вывода |
| ![Значок получения количества RX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image38.png)    | Получение количества RX внутреннего драйвера устройств ввода-вывода |
| ![Значок получения количества TX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image39.png)    | Получение количества TX внутреннего драйвера устройств ввода-вывода |
| ![Значок получения ошибок выделения внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image40.png)    | Получение ошибок выделения внутреннего драйвера устройств ввода-вывода |
| ![Значок отмены инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image41.png)    | Отмена инициализации внутреннего драйвера устройств ввода-вывода |
| ![Значок отложенной обработки внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image42.png)    | Отложенная обработка внутреннего драйвера устройств ввода-вывода |
| ![Значок недопустимости динамических записей ARP](./media/user-guide/netx-events/image43.png)    | **Недопустимые динамические записи ARP** (*nx_arp_dynamic_entries_invalidate*) |
| ![Значок набора динамических записей ARP](./media/user-guide/netx-events/image44.png)    | **Задание динамических записей ARP** (*nx_arp_dynamic_entry_set*) |
| ![Значок включения ARP](./media/user-guide/netx-events/image45.png)    | **Включение ARP** (*nx_arp_enable*) |
| ![Значок необязательной отправки ARP](./media/user-guide/netx-events/image46.png)    | **Необязательная отправка ARP** (*nx_arp_gratuitous_send*) |
| ![Значок поиска адреса оборудования ARP](./media/user-guide/netx-events/image47.png)    | **Поиск адреса оборудования ARP** (*nx_arp_hardware_address_find*) |
| ![Значок получения сведений об ARP](./media/user-guide/netx-events/image48.png)    | **Получение сведений об ARP** (*nx_arp_info_get*) |
| ![Значок поиска IP-адреса ARP](./media/user-guide/netx-events/image49.png)    | **Поиск IP-адреса ARP** (*nx_arp_ip_address_find*) |
| ![Значок создания статической записи ARP](./media/user-guide/netx-events/image50.png)    | **Создание статической записи ARP** (*nx_arp_static_entry_create*) |
| ![Значок удаления статических записей ARP](./media/user-guide/netx-events/image51.png)    | **Удаление статических записей ARP** (*nx_arp_static_entries_delete*) |
| ![Значок удаления статической записи ARP](./media/user-guide/netx-events/image52.png)    | **Удаление статической записи ARP** (*nx_arp_static_entry_delete*) |
| ![Значок удаления записи кэша Duo](./media/user-guide/netx-events/image53.png)    | **Операция удаления записи кэша Duo** (*nxd_nd_cache_entry_delete*) |
| ![Значок набора записей кэша Duo](./media/user-guide/netx-events/image54.png)    | **Набор записей кэша Duo** (*nxd_nd_cache_entry_set*) |
| ![Значок недействительности кэша Duo](./media/user-guide/netx-events/image55.png)    | **Недействительность кэша Duo** (*nxd_nd_cache_invalidate*) |
| ![Значок поиска IP-адреса кэша Duo](./media/user-guide/netx-events/image56.png)    | **Поиск IP-адреса кэша Duo** (*nxd_nd_cache_ip_address_find*) |
| ![Значок включения протокола ICMP Duo](./media/user-guide/netx-events/image57.png)    | **Включение протокола ICMP Duo** (*nxd_icmp_enable*) |
| ![Значок проверки связи ICMP Duo для IPv6](./media/user-guide/netx-events/image58.png)    | **Проверка связи ICMP Duo для IPv6** (*nxd_icmp_ping*) |
| ![Значок поиска максимального размера полезных данных в IP-адресе типа Duo](./media/user-guide/netx-events/image59.png)    | **Поиск максимального размера полезных данных в IP-адресе типа Duo** (*nx_max_payload_size_find*) |
| ![Значок отправки необработанного пакета IP-адреса типа Duo](./media/user-guide/netx-events/image60.png)    | **Отправка необработанного пакета IP-адреса типа Duo** (*nxd_ip_raw_packet_send*) |
| ![Значок добавления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image61.png)    | **Добавление стандартного маршрутизатора для IPv6 типа Duo** (*nxd_ipv6_default_router_add*) |
| ![Значок удаления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image62.png)    | **Удаление стандартного маршрутизатора для IPv6 типа Duo** (*nxd_ipv6_default_router_delete)* |
| ![Значок включения IPv6 типа Duo](./media/user-guide/netx-events/image63.png)    | **Включение IPv6 типа Duo** (*nxd_ipv6_enable)* |
| ![Значок получения глобального адреса IPv6 типа Duo](./media/user-guide/netx-events/image64.png)    | **Получение глобального адреса IPv6 типа Duo** (*nxd_ipv6_global_address_get*) |
| ![Значок установки глобальных адресов IPv6 типа Duo](./media/user-guide/netx-events/image65.png)    | **Набор глобальных адресов IPv6 типа Duo** (*nxd_ipv6_global_address_set*) |
| ![Значок инициации процесса Dad для IPv6 типа Duo](./media/user-guide/netx-events/image66.png)    | **Инициация процесса Dad для IPv6 типа Duo** (*nxd_ipv6_initiate_dad_process*) |
| ![Значок получения адреса интерфейса IPv6 типа Duo](./media/user-guide/netx-events/image67.png)    | **Получение адреса интерфейса IPv6 типа Duo** (*nxd_ipv6_interface_address_get*) |
| ![Значок набора адресов интерфейса IPv6 типа Duo](./media/user-guide/netx-events/image68.png)    | **Набор адресов интерфейса IPv6 типа Duo** (*nxd_ipv6_interface_address_get*) |
| ![Значок получения ссылки на локальный адрес IPv6 типа Duo](./media/user-guide/netx-events/image69.png)    | **Получение локального адреса канала связи IPv6 типа Duo** (*nxd_ipv6_linklocal_address_get*) |
| ![Значок набора локальных адресов канала связи IPv6 типа Duo](./media/user-guide/netx-events/image70.png)    | **Набор локальных адресов канала связи IPv6 типа Duo** (*nxd_ipv6_linklocal_address_set*) |
| ![Значок отправки необработанного пакета IPv6 типа Duo](./media/user-guide/netx-events/image71.png)    | **Отправка необработанного пакета IPv6 типа Duo** (*nxd_ipv6_raw_packet_send)* |
| ![Значок получения сведений об одноранговом узле сокета TCP Duo](./media/user-guide/netx-events/image72.png)    | **Получение сведений об одноранговом узле сокета TCP Duo** (*nxd_tcp_socket_peer_info_get*) |
| ![Значок интерфейса установки сокетов TCP Duo](./media/user-guide/netx-events/image73.png)    | **Интерфейс установки сокетов TCP Duo** (*nxd_tcp_socket_set_interface*) |
| ![Значок отправки UDP-сокета Duo](./media/user-guide/netx-events/image74.png)    | **Отправка UDP-сокета Duo** (*nxd_udp_socket_send*) |
| ![Значок интерфейса установки сокетов UDP Duo](./media/user-guide/netx-events/image75.png)    | **Интерфейс набора сокетов UDP Duo** (*nxd_udp_socket_set_interface*) |
| ![Значок извлечения источника UDP Duo](./media/user-guide/netx-events/image76.png)    | **Извлечение источника UDP Duo** (*nxd_udp_source_extract*) |
| ![Значок включения ICMP](./media/user-guide/netx-events/image77.png)    | **Включение ICMP** (*nx_icmp_enable*) |
| ![Значок получения сведений об ICMP](./media/user-guide/netx-events/image78.png)    | **Получение сведений об ICMP** (*nx_icmp_info_get*) |
| ![Значок проверки связи ICMP](./media/user-guide/netx-events/image79.png)    | **Проверка связи ICMP** (*nx_icmp_ping*) |
| ![Значок включения IGMP](./media/user-guide/netx-events/image80.png)    | **Включение протокола IGMP** (*nx_igmp_enable*) |
| ![Значок получения сведений об IGMP](./media/user-guide/netx-events/image81.png)    | **Получение сведений об IGMP** (*nx_icmp_info_get*) |
| ![Значок отключения замыкания на себя для IGMP](./media/user-guide/netx-events/image82.png)    | **Отключение замыкания на себя для IGMP** (*nx_igmp_loopback_disable*) |
| ![Значок включения замыкания на себя для IGMP](./media/user-guide/netx-events/image83.png)    | **Включение замыкания на себя для IGMP** (*nx_igmp_loopback_enable*) |
| ![Значок подключения IGMP к многоадресной рассылке](./media/user-guide/netx-events/image84.png)    | **Подключение IGMP к многоадресной рассылке** (*nx_igmp_multicast_join*) |
| ![Значок отключения IGMP от многоадресной рассылки](./media/user-guide/netx-events/image85.png)    | **Отключение IGMP от многоадресной рассылки** (*nx_igmp_multicast_leave*) |
| ![Значок уведомления об изменении IP-адреса](./media/user-guide/netx-events/image86.png)    | **Уведомление об изменении IP-адреса** (*nx_ip_address_change_notify*) |
| ![Значок получения IP-адреса](./media/user-guide/netx-events/image87.png)    | **Получение IP-адреса** (*nx_ip_address_get*) |
| ![Значок набора IP-адресов](./media/user-guide/netx-events/image88.png)    | **Набор IP-адресов** (*nx_ip_address_set*) |
| ![Значок создания IP-адреса](./media/user-guide/netx-events/image89.png)    | **Создание IP-адреса** (*nx_ip_create*) |
| ![Значок удаления IP-адреса](./media/user-guide/netx-events/image90.png)    | **Удаление IP-адреса** (*nx_ip_delete*) |
| ![Значок команды прямого доступа к драйверу протокола IP](./media/user-guide/netx-events/image91.png)    | **Команда прямого доступа к драйверу протокола IP** (*nx_ip_driver_direct_command*) |
| ![Значок отключения IP-пересылки](./media/user-guide/netx-events/image92.png)    | **Отключение IP-пересылки** (*nx_ip_forwarding_disable*) |
| ![Значок включения IP-пересылки](./media/user-guide/netx-events/image93.png)    | **Включение IP-пересылки** (*nx_ip_forwarding_enable*) |
| ![Значок отключения фрагмента IP](./media/user-guide/netx-events/image94.png)    | **Отключение фрагмента IP** (*nx_ip_fragment_disable*) |
| ![Значок включения фрагмента IP](./media/user-guide/netx-events/image95.png)    | **Включение фрагмента IP** (*nx_ip_fragment_enable*)  |
| ![Значок набора адресов шлюза IP](./media/user-guide/netx-events/image96.png)    | **Набор адресов шлюза IP** (*nx_ip_gateway_address_set*) |
| ![Значок получения сведений об IP](./media/user-guide/netx-events/image97.png)    | **Получение сведений об IP** (*nx_arp_info_get*) |
| ![Значок подключения интерфейса IP](./media/user-guide/netx-events/image98.png)    | **Подключение интерфейса IP** (*nx_ip_interface_attach*) |
| ![Значок получения сведений об интерфейсе IP](./media/user-guide/netx-events/image99.png)    | **Получение сведений об интерфейсе IP** (*nx_ip_interface_info_get*) |
| ![Значок отключения необработанных пакетов IP](./media/user-guide/netx-events/image100.png)    | **Отключение необработанных пакетов IP** (*nx_ip_raw_packet_disable*) |
| ![Значок включения необработанных пакетов IP](./media/user-guide/netx-events/image101.png)    | **Включение необработанных пакетов IP** (*nx_ip_raw_packet_disable*) |
| ![Значок получения необработанных пакетов IP](./media/user-guide/netx-events/image102.png)    | **Получение необработанных пакетов IP** (*nx_ip_raw_packet_receive*) |
| ![Значок отправки необработанного пакета IP](./media/user-guide/netx-events/image103.png)    | **Отправка необработанных пакетов IP** (*nxd_ip_raw_packet_send*) |
| ![Значок добавления статического маршрута IP](./media/user-guide/netx-events/image104.png)    | **Добавление статического маршрута IP** (*nx_ip_static_route_add*) |
| ![Значок удаления статического маршрута IP](./media/user-guide/netx-events/image105.png)    | **Удаление статического маршрута IP** (*nx_ip_static_route_add*) |
| ![Значок проверки состояния IP](./media/user-guide/netx-events/image106.png)    | **Проверка состояния IP** (*nx_ip_status_check*)|
| ![Значок включения IPSEC](./media/user-guide/netx-events/image107.png)    | **Включение IPSEC** (*nx_ipsec_enable)* |
| ![Значок выделения пакетов](./media/user-guide/netx-events/image108.png)    | **Выделение пакетов** (*nx_packet_allocate*) |
| ![Значок копирования пакета](./media/user-guide/netx-events/image109.png)    | **Копирование пакета** (*nx_packet_copy*) |
| ![Значок добавления пакетных данных](./media/user-guide/netx-events/image110.png)    | **Добавление данных пакета** (*nx_packet_data_append*) |
| ![Значок смещения при извлечении данных пакетов](./media/user-guide/netx-events/image111.png)    | **Смещение при извлечении данных пакета** (*nx_packet_data_extract_offset*) |
| ![Значок извлечения данных пакета](./media/user-guide/netx-events/image112.png)    | **Извлечение данных пакета** (*nx_packet_data_retrieve*) |
| ![Значок получения длины пакета](./media/user-guide/netx-events/image113.png)    | **Получение длины пакета** (*nx_packet_length_get*) |
| ![Значок создания пула пакетов](./media/user-guide/netx-events/image114.png)    | **Создание пула пакетов** (*nx_packet_pool_create*) |
| ![Значок удаления пула пакетов](./media/user-guide/netx-events/image115.png)    | **Удаление пула пакетов** (*nx_packet_pool_delete*) |
| ![Значок получения сведений о пуле пакетов](./media/user-guide/netx-events/image116.png)    | **Получение сведений о пуле пакетов** (*nx_packet_pool_info_get*) |
| ![Значок выпуска пакета](./media/user-guide/netx-events/image117.png)    | **Выпуск пакета** (*nx_packet_release*) |
| ![Значок выпуска передачи пакетов](./media/user-guide/netx-events/image118.png)    | **Выпуск передачи пакетов** (*nx_packet_transmit_release*) |
| ![Значок отключения RARP](./media/user-guide/netx-events/image119.png)    | **Отключение RARP** (*nx_rarp_disable*) |
| ![Значок включения RARP](./media/user-guide/netx-events/image120.png)    | **Включение RARP** (*nx_rarp_disable*) |
| ![Значок получения сведений о RARP](./media/user-guide/netx-events/image121.png)    | **Получение сведений о RARP** (*nx_arp_info_get*) |
| ![Значок инициализации системы](./media/user-guide/netx-events/image122.png)    | **Инициализация системы** (*nx_system_initialize*) |
| ![Значок привязки к сокету клиента TCP](./media/user-guide/netx-events/image123.png)    | **Привязка к сокету клиента TCP** (*nx_tcp_client_socket_bind*) |
| ![Значок подключения к сокету клиента TCP](./media/user-guide/netx-events/image124.png)    | **Подключение к сокету клиента TCP** (*nx_tcp_client_socket_connect*) |
| ![Значок получения порта сокета клиента TCP](./media/user-guide/netx-events/image125.png)    | **Получение порта сокета клиента TCP** (*nx_tcp_client_socket_port_get*) |
| ![Значок отмены привязки сокета клиента TCP](./media/user-guide/netx-events/image126.png)    | **Отмена привязки сокета клиента TCP** (*nx_tcp_client_socket_unbind*) |
| ![Значок включения TCP](./media/user-guide/netx-events/image127.png)    | **Включение TCP** (*nx_tcp_enable*) |
| ![Значок поиска свободных портов TCP](./media/user-guide/netx-events/image128.png)    | **Поиск свободных TCP-портов** (*nx_tcp_free_port_find*) |
| ![Значок получения сведений о TCP](./media/user-guide/netx-events/image129.png)    | **Получение сведений о TCP** (*nx_arp_info_get*) |
| ![Значок принятия сокета сервера TCP](./media/user-guide/netx-events/image130.png)    | **Принятие сокета сервера TCP** (*nx_tcp_server_socket_accept*) |
| ![Значок прослушивания сокета сервера TCP](./media/user-guide/netx-events/image131.png)    | **Прослушивание сокета сервера TCP** (*nx_tcp_server_socket_listen*) |
| ![Значок повторного прослушивания сокета сервера TCP](./media/user-guide/netx-events/image132.png)    | **Повторное прослушивание сокета сервера TCP** (*nx_tcp_server_socket_relisten*) |
| ![Значок отклонения сокета сервера TCP](./media/user-guide/netx-events/image133.png)    | **Отклонение сокета сервера TCP** (*nx_tcp_server_socket_unaccept*) |
| ![Значок отсутствия прослушивания сервера TCP](./media/user-guide/netx-events/image134.png)    | **Отсутствие прослушивания сокета сервера TCP** (*nx_tcp_server_socket_relisten*) |
| ![Значок доступных байтов сокета TCP](./media/user-guide/netx-events/image135.png)    | **Доступные байты сокета TCP** (*nx_tcp_socket_bytes_available*) |
| ![Значок создания сокета TCP](./media/user-guide/netx-events/image136.png)    | **Создание сокета TCP** (*nx_tcp_socket_create*) |
| ![Значок удаления сокета TCP](./media/user-guide/netx-events/image137.png)    | **Удаление сокета TCP** (*nx_tcp_socket_delete*) |
| ![Значок отключения сокета TCP](./media/user-guide/netx-events/image138.png)    | **Отключение сокета TCP** (*nx_tcp_socket_disconnect*) |
| ![Значок получения сведений о сокете TCP](./media/user-guide/netx-events/image139.png)    | **Получение сведений о сокете TCP** (*nx_tcp_socket_info_get*) |
| ![Значок получения MSS для сокета TCP](./media/user-guide/netx-events/image140.png)    | **Получение MSS для сокета TCP** (*nx_tcp_socket_mss_get*) |
| ![Значок получения значения MSS однорангового узла сокета](./media/user-guide/netx-events/image141.png)    | **Получение для однорангового узла MSS сокета TCP** (*nx_tcp_socket_mss_peer_get*) |
| ![Значок установки MSS для сокета TCP](./media/user-guide/netx-events/image142.png)    | **Установка MSS для сокета TCP** (*nx_tcp_socket_mss_set*) |
| ![Значок получения для однорангового узла сведений о сокете TCP](./media/user-guide/netx-events/image143.png)    | **Получение для однорангового узла сведений о сокете TCP** (*nx_tcp_socket_peer_info_get*) |
| ![Значок получения сокета TCP](./media/user-guide/netx-events/image144.png)    | **Получение сокета TCP** (*nx_tcp_socket_receive*) |
| ![Значок уведомления о получении сокета TCP](./media/user-guide/netx-events/image145.png)    | **Уведомление о получении сокета TCP** (*nx_tcp_socket_receive_notify*) |
| ![Значок отправки сокета TCP](./media/user-guide/netx-events/image146.png)    | **Отправка сокета TCP** (*nx_tcp_socket_send*) |
| ![Значок пребывания в состоянии ожидания для сокета TCP](./media/user-guide/netx-events/image147.png)    | **Состояние ожидания сокета TCP** (*nx_tcp_socket_state_wait*) |
| ![Значок настройки передачи сокета TCP](./media/user-guide/netx-events/image148.png)    | **Настройка передачи сокета TCP** (*nx_tcp_socket_transmit_configure*) |
| ![Значок установки уведомления об обновлении окна сокета TCP](./media/user-guide/netx-events/image149.png)    | **Установка уведомления об обновлении окна сокета TCP** (*nx_tcp_socket_window_update_notify_set*)  |
| ![Значок включения UDP](./media/user-guide/netx-events/image150.png)    | **Включение UDP** (*nx_udp_enable*) |
| ![Значок поиска свободных портов UDP](./media/user-guide/netx-events/image151.png)    | **Поиск свободных портов UDP** (*nx_tcp_free_port_find*) |
| ![Значок получения сведений о UDP](./media/user-guide/netx-events/image152.png)    | **Получение сведений о UDP** (*nx_arp_info_get*) |
| ![Значок привязки UDP-сокета](./media/user-guide/netx-events/image153.png)    | **Привязка UDP-сокета** (*nx_udp_socket_bind*) |
| ![Значок доступных байтов UDP-сокета](./media/user-guide/netx-events/image154.png)    | **Доступные байты UDP-сокета** (*nx_tcp_socket_bytes_available*) |
| ![Значок отключения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image155.png)    | **Отключение контрольной суммы UDP-сокета** (*nx_udp_socket_checksum_disable*) |
| ![Значок включения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image156.png)    | **Включение контрольной суммы UDP-сокета** (*nx_udp_socket_checksum_enable*) |
| ![Значок создания UDP-сокета](./media/user-guide/netx-events/image157.png)    | **Создание UDP-сокета** (*nx_udp_socket_create*) |
| ![Значок удаления UDP-сокета](./media/user-guide/netx-events/image158.png)    | **Удаление UDP-сокета** (*nx_udp_socket_delete*) |
| ![Значок получения сведений о сокете UDP](./media/user-guide/netx-events/image159.png)    | **Получение сведений о сокете UDP** (*nx_tcp_socket_info_get*) |
| ![Значок набора интерфейсов UDP-сокета](./media/user-guide/netx-events/image160.png)    | **Набор интерфейсов UDP-сокета** (*nx_udp_socket_interface_set*) |
| ![Значок получения порта для UDP-сокета](./media/user-guide/netx-events/image161.png)    | **Получение порта UDP-сокета** (*nx_udp_socket_port_get*) |
| ![Значок получения UDP-сокета](./media/user-guide/netx-events/image162.png)    | **Получение UDP-сокета** (*nx_udp_socket_receive*) |
| ![Значок уведомления о получении UDP-сокета](./media/user-guide/netx-events/image163.png)    | **Уведомление о получении UDP-сокета** (*nx_tcp_socket_receive_notify*) |
| ![Значок отправки UDP-сокета](./media/user-guide/netx-events/image164.png)    | **Отправка UDP-сокета** (*nx_udp_socket_send*) |
| ![Значок отмены привязки для UDP-сокета](./media/user-guide/netx-events/image165.png)    | **Отмена привязки UDP-сокета** (*nx_udp_socket_unbind*) |
| ![Значок извлечения источника UDP](./media/user-guide/netx-events/image166.png)    | **Извлечение источника UDP** (*nxd_udp_source_extract*) |

## <a name="event-descriptions"></a>Описания событий

На следующих страницах описаны события трассировки NetX.

### <a name="internal-arp-request-receive"></a>Получение внутренних запросов ARP 

#### <a name="internal-arp-request-receive"></a>Получение внутренних запросов ARP

**Значок** ![Значок получения внутренних запросов ARP](./media/user-guide/netx-events/image1.png)

**Описание**

Это событие представляет собой событие получения внутренних запросов ARP для NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Исходный IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Не используется

### <a name="internal-arp-request-send"></a>Отправка внутренних запросов ARP 

#### <a name="internal-arp-request-send"></a>Отправка внутренних запросов ARP

**Значок** ![Значок отправки внутренних запросов ARP](./media/user-guide/netx-events/image2.png)

**Описание**

Это событие представляет собой событие отправки внутренних запросов ARP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес пункта назначения
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Не используется

### <a name="internal-arp-response-receive"></a>Получение внутреннего ответа ARP 

#### <a name="internal-arp-request-receive"></a>Получение внутренних запросов ARP

**Значок** ![Значок получения внутренних запросов ARP](./media/user-guide/netx-events/image3.png)

**Описание**

Это событие представляет собой событие получения ответа на внутренние запросы ARP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Исходный IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Не используется

### <a name="internal-arp-response-send"></a>Отправка внутреннего ответа ARP 

#### <a name="internal-arp-request-send"></a>Отправка внутренних запросов ARP

**Значок** ![Значок отправки внутренних запросов ARP](./media/user-guide/netx-events/image4.png)

**Описание**

Это событие представляет собой событие ответа на внутренние запросы ARP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес пункта назначения
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Не используется

### <a name="internal-icmp-receive"></a>Получение внутреннего протокола ICMP 

#### <a name="internal-icmp-receive"></a>Получение внутреннего протокола ICMP

**Значок** ![Значок получения внутреннего протокола ICMP](./media/user-guide/netx-events/image5.png)

**Описание**

Это событие представляет собой событие получения внутреннего протокола ICMP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Исходный IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "0 слов из" для заголовка ICMP

### <a name="internal-icmp-send"></a>Отправка внутреннего протокола ICMP 

#### <a name="internal-icmp-send"></a>Отправка внутреннего протокола ICMP

**Значок** ![Значок отправки внутреннего протокола ICMP](./media/user-guide/netx-events/image6.png)

**Описание**

Это событие представляет собой событие отправки внутреннего протокола ICMP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес пункта назначения
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "0 слов из" для заголовка ICMP

### <a name="internal-igmp-receive"></a>Получение внутреннего протокола IGMP 

#### <a name="internal-igmp-receive"></a>Получение внутреннего протокола IGMP

**Значок** ![Значок получения внутреннего протокола IGMP](./media/user-guide/netx-events/image7.png)

**Описание**

Это событие представляет собой событие получения внутреннего протокола IGMP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на IP
- Поле сведений 2. Исходный IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "0 слов из" для заголовка IGMP

### <a name="internal-ip-receive"></a>Получение внутреннего IP 

#### <a name="internal-ip-receive"></a>Получение внутреннего IP

**Значок** ![Значок получения внутреннего IP](./media/user-guide/netx-events/image8.png)

**Описание**

Это событие представляет собой событие получения внутреннего протокола IP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Исходный IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Длина пакета

### <a name="internal-ip-send"></a>Отправка внутреннего IP

#### <a name="internal-ip-send"></a>Отправка внутреннего IP

**Значок** ![Значок отправки внутреннего IP](./media/user-guide/netx-events/image9.png)

**Описание**

Это событие представляет собой событие отправки внутреннего протокола IP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес пункта назначения
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Длина пакета

### <a name="internal-tcp-data-receive"></a>Получение данных по внутреннему протоколу TCP 

#### <a name="internal-tcp-data-receive"></a>Получение данных по внутреннему протоколу TCP

**Значок** ![Значок получения данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image10.png)

**Описание**

Это событие представляет собой событие получения данных по внутреннему протоколу TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Исходный IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Получение порядкового номера

### <a name="internal-tcp-data-send"></a>Отправка данных по внутреннему протоколу TCP 

#### <a name="internal-tcp-data-send"></a>Отправка данных по внутреннему протоколу TCP

**Значок** ![Значок отправки данных по внутреннему протоколу TCP](./media/user-guide/netx-events/image11.png)

**Описание**

Это событие представляет собой событие отправки данных по внутреннему протоколу TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Порядковый номер передачи

### <a name="internal-tcp-fin-receive"></a>Получение флага FIN внутреннего протокола TCP 

#### <a name="internal-tcp-fin-receive"></a>Получение флага FIN внутреннего протокола TCP

**Значок** ![Значок получения флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image12.png)

**Описание**

Это событие представляет собой событие получения флага FIN внутреннего протокола TCP в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Получение порядкового номера

### <a name="internal-tcp-fin-send"></a>Отправка флага FIN внутреннего протокола TCP 

#### <a name="internal-tcp-fin-send"></a>Отправка флага FIN внутреннего протокола TCP

**Значок** ![Значок отправки флага FIN внутреннего протокола TCP](./media/user-guide/netx-events/image13.png)

**Описание**

Это событие представляет собой событие отправки флага FIN внутреннего протокола TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Порядковый номер передачи

### <a name="internal-tcp-rst-receive"></a>Получение флага RST внутреннего протокола TCP 

#### <a name="internal-tcp-rst-receive"></a>Получение флага RST внутреннего протокола TCP

**Значок** ![Значок получения флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image14.png)

**Описание**

Это событие представляет собой событие получения сброса внутреннего протокола TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Указатель на сокет.
- Поле сведений 3. Указатель на пакет.
- Поле сведений 4. Получение порядкового номера.

### <a name="internal-tcp-rst-send"></a>Отправка флага RST внутреннего протокола TCP 

#### <a name="internal-tcp-rst-send"></a>Отправка флага RST внутреннего протокола TCP

**Значок** ![Значок отправки флага RST внутреннего протокола TCP](./media/user-guide/netx-events/image15.png)

**Описание**

Это событие представляет собой событие отправки сброса внутреннего протокола TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Порядковый номер передачи

### <a name="internal-tcp-syn-receive"></a>Получение SYN внутреннего TCP 

#### <a name="internal-tcp-syn-receive"></a>Получение SYN внутреннего TCP

**Значок** ![Значок получения SYN внутреннего TCP](./media/user-guide/netx-events/image16.png)

**Описание**

Это событие представляет собой событие получения SYN внутреннего протокола TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Получение порядкового номера

### <a name="internal-tcp-syn-send"></a>Отправка SYN внутреннего TCP 

#### <a name="internal-tcp-syn-send"></a>Отправка SYN внутреннего TCP

**Значок** ![Значок отправки SYN внутреннего TCP](./media/user-guide/netx-events/image17.png)

**Описание**

Это событие представляет собой событие отправки SYN внутреннего протокола TCP в NetX.

Поля сведений 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет. Поле сведений 4. Порядковый номер передачи

### <a name="internal-udp-receive"></a>Получение внутреннего протокола UDP 

#### <a name="internal-udp-receive"></a>Получение внутреннего протокола UDP

**Значок** ![Значок получения внутреннего протокола UDP](./media/user-guide/netx-events/image18.png)

**Описание**

Это событие представляет собой событие получения внутреннего протокола UDP в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "0 слов из" для заголовка UDP

### <a name="internal-udp-send"></a>Отправка внутреннего протокола UDP 

#### <a name="internal-udp-send"></a>Отправка внутреннего протокола UDP

**Значок** ![Значок отправки внутреннего протокола UDP](./media/user-guide/netx-events/image19.png)

**Описание**

Это событие представляет собой событие отправки внутреннего протокола UDP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "0 слов из" для заголовка UDP

### <a name="internal-rarp-receive"></a>Получение внутреннего протокола RARP 

#### <a name="internal-rarp-receive"></a>Получение внутреннего протокола RARP 

**Значок** ![Значок получения внутреннего протокола RARP](./media/user-guide/netx-events/image20.png)

**Описание**

Это событие представляет собой событие получения внутреннего протокола RARP в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Целевой IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "1 слово из" для заголовка RARP

### <a name="internal-rarp-send"></a>Отправка внутреннего протокола RARP 

#### <a name="internal-rarp-send"></a>Отправка внутреннего протокола RARP 

**Значок** ![Значок отправки внутреннего протокола RARP](./media/user-guide/netx-events/image21.png)

**Описание**

Это событие представляет собой событие отправки внутреннего протокола RARP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Целевой IP-адрес
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Поле "1 слово из" для заголовка RARP

### <a name="internal-tcp-retry"></a>Повторная попытка подключения по внутреннему протоколу TCP 

#### <a name="internal-tcp-retry"></a>Повторная попытка подключения по внутреннему протоколу TCP 

**Значок** ![Значок повторной попытки подключения по внутреннему протоколу TCP](./media/user-guide/netx-events/image22.png)

**Описание**

Это событие представляет собой событие повторной попытки подключения по внутреннему протоколу TCP в NetX.

**Поля сведений**
- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на пакет
- Поле сведений 4. Число повторных попыток

### <a name="internal-tcp-state-change"></a>Изменение состояния внутреннего протокола TCP 

#### <a name="internal-tcp-state-change"></a>Изменение состояния внутреннего протокола TCP 

**Значок** ![Значок изменения состояния внутреннего протокола TCP](./media/user-guide/netx-events/image23.png)

**Описание**

Это событие представляет собой событие изменения состояния внутреннего протокола TCP в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Предыдущее состояние
- Поле сведений 4. Новое состояние

### <a name="internal-io-driver-packet-send"></a>Отправка пакета внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-packet-send"></a>Отправка пакета внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок отправки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image24.png)

**Описание**

Это событие представляет собой событие отправки пакета внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Размер пакета
- Поле сведений 4. Не используется

### <a name="internal-io-driver-initialize"></a>Инициализация внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-initialize"></a>Инициализация внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image25.png)

**Описание**

Это событие представляет собой событие инициализации внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="internal-io-driver-link-enable"></a>Включение ссылки на внутренний драйвер устройств ввода-вывода 

#### <a name="internal-io-driver-link-enable"></a>Включение ссылки на внутренний драйвер устройств ввода-вывода

**Значок** ![Значок включения ссылки на внутренний драйвер устройств ввода-вывода](./media/user-guide/netx-events/image26.png)

**Описание**

Это событие представляет собой событие включения ссылки на внутренний драйвер устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Не используется.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="internal-io-driver-link-disable"></a>Отключение ссылки на внутренний драйвер устройств ввода-вывода 

#### <a name="internal-io-driver-link-disable"></a>Отключение ссылки на внутренний драйвер устройств ввода-вывода

**Значок** ![Значок отключения ссылки на внутренний драйвер устройств ввода-вывода](./media/user-guide/netx-events/image27.png)

**Описание**

Это событие представляет собой событие отключения ссылки на внутренний драйвер устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-packet-broadcast"></a>Широковещательная рассылка пакета внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-packet-broadcast"></a>Широковещательная рассылка пакета внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок широковещательной рассылки пакета внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image28.png)

**Описание**

Это событие представляет собой событие широковещательной рассылки пакета внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Размер пакета
- Поле сведений 4. Не используется

### <a name="internal-io-driver-arp-send"></a>Отправка ARP для внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-arp-send"></a>Отправка ARP для внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок отправки ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image29.png)

**Описание**

Это событие представляет собой событие отправки ARP для внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Размер пакета
- Поле сведений 4. Не используется

### <a name="internal-io-driver-arp-response-send"></a>Отправка ответа ARP для внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-arp-response-send"></a>Отправка ответа ARP для внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок отправки ответа ARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image30.png)

**Описание**

Это событие представляет собой событие отправки ответа ARP для внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Размер пакета
- Поле сведений 4. Не используется

### <a name="internal-io-driver-rarp-send"></a>Отправка RARP для внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-rarp-send"></a>Отправка RARP для внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок отправки RARP для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image31.png)

**Описание**

Это событие представляет собой событие отправки RARP для внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Размер пакета
- Поле сведений 4. Не используется

### <a name="internal-io-driver-multicast-join"></a>Подключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-multicast-join"></a>Подключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок подключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image32.png)

**Описание**

Это событие представляет собой событие подключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-multicast-leave"></a>Отключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-multicast-leave"></a>Отключение многоадресной рассылки для внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок отключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image33.png)

**Описание**

Это событие представляет собой событие отключения многоадресной рассылки для внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-status"></a>Получение состояния внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-get-status"></a>Получение состояния внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения состояния внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image34.png)

**Описание**

Это событие представляет собой событие получения состояния внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-speed"></a>Получение скорости внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-get-speed"></a>Получение скорости внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения скорости внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image35.png)

**Описание**

Это событие представляет собой событие получения сведений о скорости получения внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-duplex-type"></a>Получение дуплексного типа внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-get-duplex-type"></a>Получение дуплексного типа внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения дуплексного типа внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image36.png)

**Описание**

Это событие представляет собой событие получения дуплексного типа внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-error-count"></a>Получение количества ошибок внутреннего драйвера устройств ввода-вывода

#### <a name="internal-io-driver-get-error-count"></a>Получение количества ошибок внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения количества ошибок внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image37.png)

**Описание**

Это событие представляет собой событие получения количества ошибок внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-rx-count"></a>Получение количества RX внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-get-rx-count"></a>Получение количества RX внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения количества RX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image38.png)

**Описание**

Это событие представляет собой событие получения количества RX внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-tx-count"></a>Получение количества TX внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-get-tx-count"></a>Получение количества TX внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения количества TX внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image39.png)

**Описание**

Это событие представляет собой событие получения количества TX внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-get-allocation-errors"></a>Получение ошибок выделения внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-get-allocation-errors"></a>Получение ошибок выделения внутреннего драйвера устройств ввода-вывода

**Значок** ![Значок получения ошибок выделения внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image40.png)

**Описание**

Это событие представляет собой событие получения ошибок выделения внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-un-initialize"></a>Отмена инициализации внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-un-initialize"></a>Отмена инициализации внутреннего драйвера устройств ввода-вывода 

**Значок** ![Значок отмены инициализации внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image41.png)

**Описание**

Это событие представляет собой событие отмены инициализации внутреннего драйвера устройств ввода-вывода в NetX.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="internal-io-driver-deferred-processing"></a>Отложенная обработка внутреннего драйвера устройств ввода-вывода 

#### <a name="internal-io-driver-deferred-processing"></a>Отложенная обработка внутреннего драйвера устройств ввода-вывода 

**Значок** ![Значок отложенной обработки внутреннего драйвера устройств ввода-вывода](./media/user-guide/netx-events/image42.png)

**Описание**

Это событие представляет собой событие отложенной обработки внутреннего драйвера ввода-вывода в NetX.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Длина пакета
- Поле сведений 4. Не используется

### <a name="arp-dynamic-entries-invalidate"></a>Недействительность динамических записей ARP 

#### <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

**Значок** ![Значок недействительности динамических записей ARP](./media/user-guide/netx-events/image43.png)

**Описание**

Это событие представляет собой событие недействительности всех динамических записей ARP через nx_arp_dynamic_entries_invalidate.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Недействительные записи
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="arp-dynamic-entry-set"></a>Задание динамических записей ARP 

#### <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

**Значок** ![Значок набора динамических записей ARP](./media/user-guide/netx-events/image44.png)

**Описание**

Это событие представляет собой событие задания динамической записи ARP через nx_arp_dynamic_entry_set.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Физический адрес (MSW)
- Поле сведений 4. Физический адрес (LSW)

### <a name="arp-enable"></a>Включение ARP 

#### <a name="nx_arp_enable"></a>nx_arp_enable

**Значок** ![Значок включения ARP](./media/user-guide/netx-events/image45.png)

**Описание**

Это событие представляет собой событие включения ARP через nx_arp_enable.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на кэш ЦП ARP
- Поле сведений 3. Размер кэша ЦП ARP
- Поле сведений 4. Не используется

### <a name="arp-gratuitous-send"></a>Необязательная отправка ARP 

#### <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

**Значок** ![Значок необязательной отправки ARP](./media/user-guide/netx-events/image46.png)

**Описание**

Это событие представляет собой событие необязательной отправки ARP через nx_arp_gratuitous_send.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="arp-hardware-address-find"></a>Поиск адреса оборудования ARP 

#### <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

**Значок** ![Значок поиска адреса оборудования ARP](./media/user-guide/netx-events/image47.png)

**Описание**

Это событие представляет собой событие поиска физического адреса с помощью nx_arp_hardware_address_find.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Физический адрес (MSW)
- Поле сведений 4. Физический адрес (LSW)

### <a name="arp-information-get"></a>Получение сведений об ARP 

#### <a name="nx_arp_info_get"></a>nx_arp_info_get

**Значок** ![Значок получения сведений об ARP](./media/user-guide/netx-events/image48.png)

**Описание**

Это событие представляет собой событие получения сведений об ARP с помощью nx_rarp_info_get.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Отправка ARP
- Поле сведений 3. Отклики ARP
- Поле сведений 4. Количество полученных ARP

### <a name="arp-ip-address-find"></a>Поиск IP-адреса ARP 

#### <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

**Значок** ![Значок поиска IP-адреса ARP](./media/user-guide/netx-events/image49.png)

**Описание**

Это событие представляет собой событие поиска IP-адреса, связанного с физическим адресом, переданным через nx_arp_ip_address_find.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Физический адрес (MSW)
- Поле сведений 4. Физический адрес (LSW)

### <a name="arp-static-entry-create"></a>Создание статической записи ARP 

#### <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

**Значок** ![Значок создания статической записи ARP](./media/user-guide/netx-events/image50.png)

**Описание**

Это событие представляет собой событие создания статической записи ARP через nx_arp_static_entry_create.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Физический адрес (MSW)
- Поле сведений 4. Физический адрес (LSW)

### <a name="arp-static-entries-delete"></a>Удаление статических записей ARP 

#### <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

**Значок** ![Значок удаления статических записей ARP](./media/user-guide/netx-events/image51.png)

**Описание**

Это событие представляет собой событие удаления всех статических записей ARP через nx_arp_static_entries_delete.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Удаленные записи
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="arp-static-entry-delete"></a>Удаление статической записи ARP 

### <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

**Значок** ![Значок удаления статической записи ARP](./media/user-guide/netx-events/image52.png)

**Описание**

Это событие представляет собой удаление статической записи ARP через nx_arp_static_entry_create.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Физический адрес (MSW)
- Поле сведений 4. Физический адрес (LSW)

### <a name="duo-cache-entry-delete"></a>Удаление записи кэша Duo 

#### <a name="nxd_und_cache_entry_delete"></a>nxd_und_cache_entry_delete

**Значок** ![Значок удаления записи кэша Duo](./media/user-guide/netx-events/image53.png)

**Описание**

Это событие представляет собой удаление записи в соседней таблице кэша с помощью nx_udp_socket_create.

**Поля сведений** 

- Поле сведений 1. Четвертое (наименее значимое) слово локального адреса канала связи IPv6 для удаления
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-cache-entry-set"></a>Набор записей кэша Duo 

#### <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set

**Значок** ![Значок набора записей кэша Duo](./media/user-guide/netx-events/image54.png)

**Описание**

Это событие представляет собой создание записи кэша и добавление ее в соседнюю таблицу кэша с помощью nxd_nd_cache_entry_set.

**Поля сведений** 

- Поле сведений 1. Четвертое (наименее значимое) слово адреса IPv6 для добавления
- Поле сведений 2. Физический адрес msb
- Поле сведений 3. Физический адрес lsb
- Поле сведений 4. Не используется

### <a name="duo-cache-invalidate"></a>Недействительность кэша Duo 

#### <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate

**Значок** ![Значок недействительности кэша Duo](./media/user-guide/netx-events/image55.png)

**Описание**

Это событие представляет недействительность всей соседней таблицы кэша через nxd_nd_cache_invalidate.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-cache-ip-address-find"></a>Поиск IP-адреса кэша Duo 

#### <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find

**Значок** ![Значок поиска IP-адреса кэша Duo](./media/user-guide/netx-events/image56.png)

**Описание**

Это событие представляет собой получение IP-адреса, соответствующего физическому адресу, переданному из таблицы кэша с помощью nxd_nd_cache_ip_address_find.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Четвертое (наименее значимое) слово адреса IPv6
- Поле сведений 3. Физический адрес msb
- Поле сведений 4. Физический адрес lsb

### <a name="duo-icmp-enable"></a>Включение протокола ICMP Duo 

#### <a name="nxd_icmp_enable"></a>nxd_icmp_enable

**Значок** ![Значок включения протокола ICMP Duo](./media/user-guide/netx-events/image57.png)

**Описание**

Это событие представляет собой включение служб ICMPv4 и ICMPv6 на указанном экземпляре IP-адреса через nxd_icmp_enable.

**Поля сведений**
- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-icmp-ping"></a>Проверка связи ICMP Duo 

#### <a name="nxd_icmp_ping"></a>nxd_icmp_ping

**Значок** ![Значок проверки связи ICMP Duo](./media/user-guide/netx-events/image58.png)

**Описание**

Это событие представляет собой отправку запроса на проверку связи (эхо-запроса) узлу IPv6 через nxd_icmp_ping.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Адрес IPv6
- Поле сведений 3. Указатель на данные для проверки связи
- Поле сведений 4. Размер данных для проверки связи

### <a name="duo-ip-max-payload-size-find"></a>Поиск максимального размера полезных данных для IP-адреса типа Duo 

#### <a name="nxd_ip_max_payload_size"></a>nxd_ip_max_payload_size

**Значок** ![Значок поиска максимального размера полезных данных в IP-адресе типа Duo](./media/user-guide/netx-events/image59.png)

**Описание**

Это событие позволяет вычислить максимальное количество полезных данных, которые может содержать указанный пакет, не требуя фрагментации.

**Поля сведений**

- Поле сведений 1. Указатель на сокет
- Поле сведений 2. IP-адрес однорангового узла
- Поле сведений 3. Поле сведений об одноранговом узле. Поле сведений 4. Не используется

### <a name="duo-ip-raw-packet-send"></a>Отправка необработанных пакетов IP типа Duo 

#### <a name="nxd_ip_max_packet_send"></a>nxd_ip_max_packet_send

**Значок** ![Значок отправки необработанного пакета IP-адреса типа Duo](./media/user-guide/netx-events/image60.png)

**Описание**

Это событие представляет собой отправку необработанного пакета IP из указанного сетевого интерфейса в предоставленный IP-адрес пункта назначения с помощью nxd_ip_raw_packet_send.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет, который нужно отправить
- Поле сведений 3. Указатель на адрес пункта назначения
- Поле сведений 4. Протокол пакетов

### <a name="duo-ipv6-default-router-add"></a>Добавление стандартного маршрутизатора для IPv6 типа Duo 

#### <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add

**Значок** ![Значок добавления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image61.png)

**Описание**

Это событие представляет собой добавление маршрутизатора по умолчанию в таблицу маршрутизации IPv6 экземпляра IP с помощью nxd_ipv6_default_router_add.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Адрес сети назначения.
- Поле сведений 3. Сведения о времени существования.
- Поле сведений 4. Не используется.

### <a name="duo-ipv6-default-router-delete"></a>Удаление стандартного маршрутизатора для IPv6 типа Duo 

#### <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete

**Значок** ![Значок удаления стандартного маршрутизатора для IPv6 типа Duo](./media/user-guide/netx-events/image62.png)

**Описание**

Это событие представляет удаление маршрутизатора по умолчанию из таблицы маршрутизации IPv6 экземпляра IP с помощью nxd_ipv6_default_router_delete.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Четвертое слово (наименее значимое) стандартного маршрутизатора адреса IPv6.
- Поле сведений 3. Не используется.
- Поле сведений 4. Не используется.

### <a name="duo-ipv6-enable"></a>Включение протокола IPv6 типа Duo 

#### <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable

**Значок** ![Значок включения IPv6 типа Duo](./media/user-guide/netx-events/image63.png)

**Описание**

Это событие представляет собой включение служб IPv6 в предоставленном экземпляре IP с помощью nxd_ipv6_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-ipv6-global-address-get"></a>Получение глобального адреса IPv6 типа Duo 

#### <a name="nxd_ipv6_global_address_get"></a>nxd_ipv6_global_address_get

**Значок** ![Значок получения глобального адреса IPv6 типа Duo](./media/user-guide/netx-events/image64.png)

**Описание**

Это событие представляет собой получение глобального (основного) IP-адреса для экземпляра IP, расположенного по индексу 1 в таблице интерфейса экземпляра IP, с помощью nxd_ipv6_global_address_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Четвертое слово (наименее значимое) глобального адреса
- Поле сведений 3. Длина префикса адреса IPv6.
- Поле сведений 4. Индекс в таблице IP-интерфейса (1).

### <a name="duo-ipv6-global-address-set"></a>Установка глобальных адресов IPv6 типа Duo 

#### <a name="nxd_ipv6_global_address_set"></a>nxd_ipv6_global_address_set

**Значок** ![Значок установки глобальных адресов IPv6 типа Duo](./media/user-guide/netx-events/image65.png)

**Описание**

Это событие представляет собой установку глобального (основного) IP-адреса для экземпляра IP, расположенного по индексу 1 в таблице интерфейса экземпляра IP, с помощью nxd_ipv6_global_address_set.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Четвертое слово (наименее значимое) глобального адреса
- Поле сведений 3. Длина префикса адреса IPv6.
- Поле сведений 4. Индекс в таблице IP-интерфейса (1).

### <a name="duo-ipv6-initiate-dad-process"></a>Процесс инициализации процесса Dad для IPv6 типа Duo 

#### <a name="nxd_ipv6_initiate_dad_process"></a>nxd_ipv6_initiate_dad_process

**Значок** ![Значок инициации процесса Dad для IPv6 типа Duo](./media/user-guide/netx-events/image66.png)

**Описание**

Это событие представляет собой начало процесса обнаружения дубликатов адресов (DAD), если экземпляру IP-адреса назначен локальный или IP-адрес интерфейса через nxd_ipv6_initiate_dad_process.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-ipv6-interface-address-get"></a>Получение адреса интерфейса IPv6 типа Duo 

#### <a name="nxd_ipv6_interface_address_get"></a>nxd_ipv6_interface_address_get

**Значок** ![Значок получения адреса интерфейса IPv6 типа Duo](./media/user-guide/netx-events/image67.png)

**Описание**

Это событие представляет собой извлечение IP-адреса и префикса по указанному индексу в таблицу адресов интерфейса экземпляра IP с помощью nxd_ipv6_interface_address_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Четвертое слово (наименее значимое) адреса IPv6, который нужно возвратить
- Поле сведений 4. Индекс интерфейса в таблице интерфейса экземпляра IP

### <a name="duo-ipv6-interface-address-set"></a>Установка адреса интерфейса для IPv6 типа Duo 

### <a name="nxd_ipv6_interface_address_set"></a>nxd_ipv6_interface_address_set

**Значок** ![Значок установки адреса интерфейса для IPv6 типа Duo](./media/user-guide/netx-events/image68.png)

**Описание**

Это событие представляет собой установку IP-адреса и префикса по указанному индексу в таблице адресов интерфейса экземпляра IP. Не разрешено для индекса размером ноль (локальный адрес канала связи) через nxd_ipv6_interface_address_set.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Четвертое слово (наименее значимое) адреса IPv6, который нужно возвратить
- Поле сведений 3. Длина префикса
- Поле сведений 4. Индекс интерфейса в таблице интерфейса экземпляра IP

### <a name="duo-ipv6-link-local-address-get"></a>Получение локального адреса канала связи IPv6 типа Duo 

#### <a name="nxd_ipv6_linklocal_address_get"></a>nxd_ipv6_linklocal_address_get

**Значок** ![Значок получения локального адреса ссылки на IPv6 типа Duo](./media/user-guide/netx-events/image69.png)

**Описание**

Это событие представляет собой получение локального адреса канала связи указанного экземпляра IP через nxd_ipv6_linklocal_address_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Четвертое слово (наименее значимое) локального адреса ссылки на IPv6
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-ipv6-link-local-address-set"></a>Установка локальных адресов для канала связи IPv6 типа Duo 

#### <a name="nxd_ipv6_linklocal_address_set"></a>nxd_ipv6_linklocal_address_set

**Значок** ![Значок набора локальных адресов для ссылки на IPv6 типа Duo](./media/user-guide/netx-events/image70.png)

**Описание**

Это событие представляет собой установку локального адреса канала связи указанного экземпляра IP через nxd_ipv6_linklocal_address_set.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Четвертое (наименее значимое) слово локального адреса канала связи IPv6
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-ipv6-raw-packet-send"></a>Отправка необработанных пакетов IPv6 типа Duo 

#### <a name="nxd_ipv6_raw_packet_send"></a>nxd_ipv6_raw_packet_send

**Значок** ![Значок отправки необработанного пакета IPv6 типа Duo](./media/user-guide/netx-events/image71.png)

**Описание**

Это событие представляет собой отправку необработанного пакета IP через основной IP-интерфейс в указанный пункт назначения с помощью nxd_ip_raw_packet_send.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет, который нужно отправить
- Поле сведений 3. IP-адрес пункта назначения
- Поле сведений 4. Не используется

### <a name="duo-tcp-socket-peer-info-get"></a>Получение сведений об узле сокета TCP Duo 

#### <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get

**Значок** ![Значок получения сведений об узле сокета TCP Duo](./media/user-guide/netx-events/image72.png)

**Описание**

Это событие извлекает данные отправителя из полученного пакета TCP в указанный сокет. Во время этого возвращается IP-адрес и порт отправителя.

**Поля сведений**

- Поле сведений 1. Указатель на сокет
- Поле сведений 2. IP-адрес однорангового узла
- Поле сведений 3. Порт однорангового узла
- Поле сведений 4. Наименее значимые 32-бита IP-адреса

### <a name="duo-tcp-socket-set-interface"></a>Интерфейс установки сокета TCP Duo 

#### <a name="nxd_tcp_socket_set_interface"></a>nxd_tcp_socket_set_interface

**Значок** ![Значок интерфейса установки сокетов TCP Duo](./media/user-guide/netx-events/image73.png)

**Описание**

Это событие представляет собой настройку исходящего интерфейса сокета после подключения клиента к серверу TCP по указанному IP-адресу сервера с помощью nxd_tcp_client_socket_connect.

**Поля сведений** 

- Поле сведений 1. Указатель на сокет TCP
- Поле сведений 2. Идентификатор интерфейса
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-udp-socket-send"></a>Отправка UDP-сокета Duo 

#### <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send

**Значок** ![Значок отправки UDP-сокета Duo](./media/user-guide/netx-events/image74.png)

**Описание**

Это событие представляет собой отправку пакета UDP через указанный сокет с IP-адресом входных данных и портом через nxd_udp_socket_send.

**Поля сведений** 

- Поле сведений 1. Указатель на сокет UDP
- Поле сведений 2. Указатель на пакет UDP
- Поле сведений 3. Длина пакета
- Поле сведений 4. Не используется


### <a name="duo-udp-socket-set-interface"></a>Интерфейс установки UDP-сокета Duo 

#### <a name="nxd_udp_socket_set_interface"></a>nxd_udp_socket_set_interface

**Значок** ![Значок интерфейса установки сокетов UDP Duo](./media/user-guide/netx-events/image75.png)

**Описание**

Это событие представляет собой установку указанного исходящего интерфейса UDP-сокета для интерфейса, соответствующего идентификатору интерфейса ввода, через nxd_udp_socket_set_interface.

**Поля сведений** 

- Поле сведений 1. Указатель на сокет UDP
- Поле сведений 2. Идентификатор интерфейса
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="duo-udp-source-extract"></a>Извлечение источника UDP Duo 

#### <a name="nxd_udp_socket_extract"></a>nxd_udp_socket_extract

**Значок** ![Значок извлечения источника UDP Duo](./media/user-guide/netx-events/image76.png)

**Описание**

Это событие представляет собой извлечение IP-адреса и исходного порта полученного пакета (IPv4 или IPv6). Если используется IPv6, четвертое слово (наименьшее значение) IP-адреса возвращается через nxd_udp_source_extract.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Версия IP
- Поле сведений 3. Исходный IP-адрес (IPv4 или IPv6)
- Поле сведений 4. Исходный порт

### <a name="icmp-enable"></a>Включение ICMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Значок** ![Значок включения протокола ICMP](./media/user-guide/netx-events/image77.png)

**Описание**

Это событие представляет собой включение протокола ICMP через nx_icmp_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP.
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="icmp-information-get"></a>Получение сведений о ICMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Значок** ![Значок получения сведений об ICMP](./media/user-guide/netx-events/image78.png)

**Описание**

Это событие представляет собой получение сведений с помощью nx_rarp_info_get.

**Поля сведений**
- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Количество отправленных запросов на проверку связи
- Поле сведений 3. Количество откликов на запросы на проверку связи
- Поле сведений 4. Количество полученных запросов на проверку связи

### <a name="icmp-ping"></a>Проверка связи ICMP 

#### <a name="nx_icmp_ping"></a>nx_icmp_ping

**Значок** ![Значок проверки связи ICМP](./media/user-guide/netx-events/image79.png)

**Описание**

Это событие представляет собой проверку связи для целевого IP-адреса через nx_icmp_ping.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Указатель на данные
- Поле сведений 4. Размер данных

### <a name="igmp-enable"></a>Включение IGMP 

#### <a name="nx_icmp_enable"></a>nx_icmp_enable

**Значок** ![Значок включения IGMP](./media/user-guide/netx-events/image80.png)

**Описание**

Это событие представляет собой включение протокола IGMP через nx_icmp_enable.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="igmp-information-get"></a>Получение сведений об IGMP 

#### <a name="nx_icmp_info_get"></a>nx_icmp_info_get

**Значок** ![Значок получения сведений об IGMP](./media/user-guide/netx-events/image81.png)

**Описание**

Это событие представляет собой получение сведений с помощью nx_igmp_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Количество отправленных отчетов
- Поле сведений 3. Количество полученных запросов
- Поле сведений 4. Количество присоединенных групп

### <a name="igmp-loopback-disable"></a>Отключение замыкания на себя для IGMP 

#### <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

**Значок** ![Значок отключения замыкания на себя для IGMP](./media/user-guide/netx-events/image82.png)

**Описание**

Это событие представляет собой отключение замыкания на себя для IGMP через nx_igmp_loopback_disable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="igmp-loopback-enable"></a>Включение замыкания на себя для IGMP 

#### <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

**Значок** ![Значок включения замыкания на себя для IGMP](./media/user-guide/netx-events/image83.png)

**Описание**

Это событие представляет собой включение замыкания на себя для IGMP через nx_igmp_loopback_enable.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="igmp-multicast-join"></a>Подключение IGMP к многоадресной рассылке 

#### <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

**Значок** ![Значок подключения IGMP к многоадресной рассылке](./media/user-guide/netx-events/image84.png)

**Описание**

Это событие представляет собой подключение группы к многоадресной рассылке через nx_igmp_multicast_join.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес группы
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="igmp-multicast-leave"></a>Отключение IGMP от многоадресной рассылки 

#### <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

**Значок** ![Значок отключения IGMP от многоадресной рассылки](./media/user-guide/netx-events/image85.png)

**Описание**

Это событие представляет собой отключение IGMP от многоадресной рассылки с помощью nx_igmp_multicast_leave.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес группы
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-address-change-notify"></a>Уведомление об изменении IP-адреса 

#### <a name="nx_ip_address_change_notify"></a>nx_ip_address_change_notify

**Значок** ![Значок уведомления об изменении IP-адреса](./media/user-guide/netx-events/image86.png)

**Описание**

Это событие представляет собой регистрацию для получения уведомлений об изменении IP-адреса с помощью nx_ip_address_change_notify.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на функцию обратного вызова
- Поле сведений 3. Указатель на дополнительную информацию
- Поле сведений 4. Не используется

### <a name="ip-address-get"></a>Получение IP-адреса 

#### <a name="nx_ip_address_get"></a>nx_ip_address_get

**Значок** ![Значок получения IP-адреса](./media/user-guide/netx-events/image87.png)

**Описание**

Это событие представляет собой получение IP-адреса через nx_ip_address_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Маска сети
- Поле сведений 4. Не используется

### <a name="ip-address-set"></a>Установка IP-адреса 

#### <a name="nx_ip_address_set"></a>nx_ip_address_set

**Значок** ![Значок установки IP-адреса](./media/user-guide/netx-events/image88.png)

**Описание**

Это событие представляет собой установку IP-адреса через nx_ip_address_set.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Маска сети
- Поле сведений 4. Не используется

### <a name="ip-create"></a>Создание IP-адреса 

#### <a name="nx_ip_create"></a>nx_ip_create

**Значок** ![Значок создания IP-адреса](./media/user-guide/netx-events/image89.png)

**Описание**

Это событие представляет собой создание экземпляра IP-адреса с помощью nx_ip_create.

**Поля сведений** 
- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес
- Поле сведений 3. Маска сети
- Поле сведений 4. Указатель на пул пакетов по умолчанию

### <a name="ip-delete"></a>Удаление IP-адреса 

#### <a name="nx_ip_delete"></a>nx_ip_delete

**Значок** ![Значок удаления IP-адреса](./media/user-guide/netx-events/image90.png)

**Описание**

Это событие представляет собой удаление экземпляра IP-адреса с помощью nx_ip_delete.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-driver-direct-command"></a>Команда прямого доступа к драйверу протокола IP 

#### <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

**Значок** ![Значок команды прямого доступа к драйверу протокола IP](./media/user-guide/netx-events/image91.png)

**Описание**

Это событие представляет собой команду прямого доступа к драйверу ввода-вывода с помощью nx_ip_driver_direct_command.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Команда драйвера
- Поле сведений 3. Возвращаемое значение
- Поле сведений 4. Не используется

### <a name="ip-forwarding-disable"></a>Отключение IP-пересылки 

#### <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

**Значок** ![Значок отключения IP-пересылки](./media/user-guide/netx-events/image92.png)

**Описание**

Это событие представляет собой отключение IP-пересылки через nx_ip_forwarding_disable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-forwarding-enable"></a>Включение IP-пересылки 

#### <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

**Значок** ![Значок включения IP-пересылки](./media/user-guide/netx-events/image93.png)

**Описание**

Это событие представляет собой включение IP-пересылки через nx_ip_forwarding_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-fragment-disable"></a>Отключение фрагмента IP-адреса 

#### <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

**Значок** ![Значок отключения фрагмента IP-адреса](./media/user-guide/netx-events/image94.png)

**Описание**

Это событие представляет собой отключение фрагментации IP-адресов с помощью nx_ip_fragment_disable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-fragment-enable"></a>Включение фрагмента IP-адреса 

#### <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

**Значок** ![Значок включения фрагмента IP-адреса](./media/user-guide/netx-events/image95.png)

**Описание**

Это событие представляет собой включение фрагментации IP-адресов с помощью nx_ip_fragment_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-gateway-address-set"></a>Установка адреса шлюза IP 

#### <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

**Значок** ![Значок установки адреса шлюза IP](./media/user-guide/netx-events/image96.png)

**Описание**

Это событие представляет собой установку IP-адреса шлюза с помощью nx_ip_gateway_address_set.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес шлюза
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-information-get"></a>Получение сведений об IP-адресе 

#### <a name="nx_ip_info_get"></a>nx_ip_info_get

**Значок** ![Значок получения сведений об IP](./media/user-guide/netx-events/image97.png)

**Описание**. Это событие представляет собой получение сведений об IP-адресе через nx_ip_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Байты, отправленные через IP
- Поле сведений 3. Байты, полученные через IP
- Поле сведений 4. Удаленные пакеты IP

### <a name="ip-interface-attach"></a>Подключение интерфейса IP 

#### <a name="nx_interface_attach"></a>nx_interface_attach

**Значок** ![Значок подключения интерфейса IP](./media/user-guide/netx-events/image98.png)

**Описание**

Это событие представляет собой дополнительный сетевой интерфейс, который присоединяется к экземпляру IP через nx_ip_interface_attach.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес интерфейса
- Поле сведений 3. Индекс в таблице IP-интерфейса
- Поле сведений 4. Не используется

### <a name="ip-interface-info-get"></a>Получение сведений об интерфейсе IP 

#### <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

**Значок** ![Значок получения сведений об интерфейсе IP](./media/user-guide/netx-events/image99.png)

**Описание**

Это событие представляет собой сведения, полученные из указанного сетевого интерфейса через nx_ip_interface_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. IP-адрес интерфейса
- Поле сведений 3. MAC-адрес msb интерфейса
- Поле сведений 4. MAC-адрес lsb интерфейса

### <a name="ip-raw-packet-disable"></a>Отключение необработанных пакетов IP 

#### <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

**Значок** ![Значок отключения необработанных пакетов IP](./media/user-guide/netx-events/image100.png)

**Описание**

Это событие представляет собой отключение необработанного пакета IP через nx_ip_raw_packet_disable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-raw-packet-enable"></a>Включение необработанных пакетов IP 

#### <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

**Значок** ![Значок включения необработанных пакетов IP](./media/user-guide/netx-events/image101.png)

**Описание**

Это событие представляет собой включение необработанного пакета IP с помощью nx_ip_raw_packet_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="ip-raw-packet-receive"></a>Получение необработанных пакетов IP 

#### <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

**Значок** ![Значок получения необработанных пакетов IP](./media/user-guide/netx-events/image102.png)

**Описание**

Это событие представляет собой получение необработанного пакета IP через nx_ip_raw_packet_receive.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Параметр Wait
- Поле сведений 4. Не используется

### <a name="ip-raw-packet-send"></a>Отправка необработанных пакетов IP 

#### <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

**Значок** ![Значок отправки необработанных пакетов IP](./media/user-guide/netx-events/image103.png)

**Описание**

Это событие представляет собой отправку необработанного пакета IP через nx_ip_raw_packet_send.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. IP-адрес пункта назначения
- Поле сведений 4. Тип службы.

### <a name="ip-static-route-add"></a>Добавление статического маршрута IP 

#### <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

**Значок** ![Значок добавления статического маршрута IP](./media/user-guide/netx-events/image104.png)

**Описание**

Это событие представляет собой добавление статического маршрута в таблицу маршрутизации экземпляра IP с помощью nx_ip_static_route_add.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Адрес сети
- Поле сведений 3. Маска сети
- Поле сведений 4. Следующий прыжок

### <a name="ip-static-route-delete"></a>Удаление статического маршрута IP 

#### <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

**Значок** ![Значок удаления статического маршрута IP](./media/user-guide/netx-events/image105.png)

**Описание**

Это событие представляет собой удаление статического маршрута из таблицы маршрутизации экземпляра IP с помощью nx_ip_static_route_add.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Адрес сети
- Поле сведений 3. Маска сети
- Поле сведений 4. Не используется

### <a name="ip-status-check"></a>Проверка состояния IP 

#### <a name="nx_ip_status_check"></a>nx_ip_status_check

**Значок** ![Значок проверки состояния IP](./media/user-guide/netx-events/image106.png)

**Описание**

Это событие представляет собой проверку состояния IP с помощью nx_ip_status_check.

Поля сведений 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Запрошенное состояние
- Поле сведений 3. Фактическое состояние
- Поле сведений 4. Параметр Wait

### <a name="ipsec-enable"></a>Включение IPSEC 

#### <a name="nx_ipsec_enable"></a>nx_ipsec_enable

**Значок** ![Значок включения IPSEC](./media/user-guide/netx-events/image107.png)

**Описание**

Это событие представляет собой включение служб IPSec в предоставленном экземпляре IP с помощью nx_ipsec_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="packet-allocate"></a>Выделение пакетов 

#### <a name="nx_packet_allocate"></a>nx_packet_allocate

**Значок** ![Значок выделения пакета](./media/user-guide/netx-events/image108.png)

**Описание**

Это событие представляет собой выделение пакета с помощью nx_packet_allocate.

**Поля сведений**

- Поле сведений 1. Указатель на пул пакетов
- Поле сведений 2. Указатель на выделенный пакет
- Поле сведений 3. Тип пакета
- Поле сведений 4. Доступные пакеты

### <a name="packet-copy"></a>Копирование пакетов 

#### <a name="nx_packet_copy"></a>nx_packet_copy

**Значок** ![Значок копирования пакета](./media/user-guide/netx-events/image109.png)

**Описание**

Это событие представляет собой копирование пакета с помощью nx_packet_copy.

**Поля сведений**

- Поле сведений 2. Указатель на новый пакет
- Поле сведений 3. Указатель на пул пакетов
- Поле сведений 4. Параметр Wait

### <a name="packet-data-append"></a>Добавление пакетных данных 

#### <a name="nx_packet_data_append"></a>nx_packet_data_append

**Значок** ![Значок добавления пакетных данных](./media/user-guide/netx-events/image110.png)

**Описание**

Это событие представляет собой добавление данных в пакет с помощью nx_packet_data_append.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Указатель на данные
- Поле сведений 3. Размер данных
- Поле сведений 4. Указатель на пул пакетов

### <a name="packet-data-extract-offset"></a>Смещение при извлечении данных пакета 

#### <a name="nx_udp_source_extract_offset"></a>nx_udp_source_extract_offset

**Значок** ![Значок смещения при извлечении данных пакета](./media/user-guide/netx-events/image111.png)

**Описание**

Это событие представляет собой извлечение данных из пакета в указанный буфер с помощью nx_udp_source_extract_offset.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Размер указанного буфера
- Поле сведений 3. Число скопированных байтов
- Поле сведений 4. Не используется

### <a name="packet-data-retrieve"></a>Получение пакетных данных 

#### <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

**Значок** ![Значок получения пакетных данных](./media/user-guide/netx-events/image112.png)

**Описание**

Это событие представляет собой получение данных из пакета с помощью nx_packet_data_retrieve.

**Поля сведений** 

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Указатель на запуск буфера
- Поле сведений 3. Скопированные байты
- Поле сведений 4. Не используется

### <a name="packet-length-get"></a>Получение длины пакета 

#### <a name="nx_packet_length_get"></a>nx_packet_length_get

**Значок** ![Значок получения длины пакета](./media/user-guide/netx-events/image113.png)

**Описание**

Это событие представляет собой получение длины пакета через nx_packet_length_get.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Длина пакета
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="packet-pool-create"></a>Создание пула пакетов 

#### <a name="nx_packet_pool_create"></a>nx_packet_pool_create

**Значок** ![Значок создания пула пакетов](./media/user-guide/netx-events/image114.png)

**Описание**

Это событие представляет собой создание пула пакетов с помощью nx_packet_pool_create.

**Поля сведений** 

- Поле сведений 1. Указатель на пул пакетов
- Поле сведений 2. Размер полезных данных пакета
- Поле сведений 3. Указатель на область памяти пула
- Поле сведений 4. Размер области памяти пула

### <a name="packet-pool-delete"></a>Удаление пула пакетов 

#### <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

**Значок** ![Значок удаления пула пакетов](./media/user-guide/netx-events/image115.png)

**Описание**

Это событие представляет собой удаление пула пакетов с помощью nx_packet_pool_delete.

**Поля сведений** 

- Поле сведений 1. Указатель на пул пакетов
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

#### <a name="packet-pool-information-get"></a>Получение сведений о пуле пакетов 

#### <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

**Значок** ![Значок получения сведений о пуле пакетов](./media/user-guide/netx-events/image116.png)

**Описание**

Это событие представляет собой получение сведений о пуле пакетов с помощью nx_packet_pool_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на пул пакетов
- Поле сведений 2. Общее количество пакетов
- Поле сведений 3. Доступные пакеты
- Поле сведений 4. Пустые запросы

### <a name="packet-release"></a>Выпуск пакета 

#### <a name="nx_packet_data_release"></a>nx_packet_data_release

**Значок** ![Значок выпуска пакета](./media/user-guide/netx-events/image117.png)

**Описание**

Это событие представляет собой выпуск пакета с помощью nx_packet_release.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Состояние пакета
- Поле сведений 3. Доступные пакеты
- Поле сведений 4. Не используется

### <a name="packet-transmit-release"></a>Выпуск передачи пакетов 

#### <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

**Значок** ![Значок выпуска передачи пакетов](./media/user-guide/netx-events/image118.png)

**Описание**

Это событие представляет собой выпуск передачи пакета с помощью nx_packet_transmit_release.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. Состояние пакета
- Поле сведений 3. Доступные пакеты
- Поле сведений 4. Не используется

### <a name="rarp-disable"></a>Отключение RARP 

#### <a name="nx_rarp_disable"></a>nx_rarp_disable

**Значок** ![Значок отключения RARP](./media/user-guide/netx-events/image119.png)

**Описание**

Это событие представляет собой отключение RARP через nx_rarp_disable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="rarp-enable"></a>Включение RARP 

#### <a name="nx_rarp_enable"></a>nx_rarp_enable

**Значок** ![Значок включения RARP](./media/user-guide/netx-events/image120.png)

**Описание**

Это событие представляет собой включение RARP через nx_arp_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="rarp-information-get"></a>Получение сведений о RARP 

#### <a name="nx_rarp_info_get"></a>nx_rarp_info_get

**Значок** ![Значок получения сведений о RARP](./media/user-guide/netx-events/image121.png)

**Описание**

Это событие представляет собой получение сведений о RARP с помощью nx_rarp_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Количество отправленных запросов
- Поле сведений 3. Количество полученных ответов
- Поле сведений 4. Недопустимые ответы

### <a name="system-initialize"></a>Инициализация системы 

#### <a name="nx_system_initialize"></a>nx_system_initialize

**Значок** ![Значок инициализации системы](./media/user-guide/netx-events/image122.png)

**Описание**

Это событие представляет собой инициализацию NetX через nx_system_initialize.

**Поля сведений**

- Поле сведений 1. Не используется
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="tcp-client-socket-bind"></a>Привязка сокета клиента TCP 

#### <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

**Значок** ![Значок привязки сокета клиента TCP](./media/user-guide/netx-events/image123.png)

**Описание**

Это событие представляет собой привязку сокета клиента к порту с помощью nx_tcp_client_socket_bind.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Запрошенный порт
- Поле сведений 4. Параметр Wait

### <a name="tcp-client-socket-connect"></a>Подключение сокета клиента TCP 

#### <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

**Значок** ![Значок подключения сокета клиента TCP](./media/user-guide/netx-events/image124.png)

**Описание**

Это событие представляет собой подключение сокета клиента через nx_tcp_client_socket_connect.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. IP-адрес сервера
- Поле сведений 4. Запрошенный порт сервера

### <a name="tcp-client-socket-port-get"></a>Получение порта сокета клиента TCP 

#### <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

**Значок** ![Значок получения порта сокета клиента TCP](./media/user-guide/netx-events/image125.png)

**Описание**

Это событие представляет собой получение номера порта сокета клиента помощью nx_tcp_client_socket_port_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Номер порта
- Поле сведений 4. Не используется

### <a name="tcp-client-socket-unbind"></a>Отмена привязки сокета клиента TCP 

#### <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

**Значок** ![Значок отмены привязки сокета клиента TCP](./media/user-guide/netx-events/image126.png)

**Описание**

Это событие представляет собой отмену привязки порта, связанного с сокетом, через nx_tcp_client_socket_unbind.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="tcp-enable"></a>Включение TCP 

#### <a name="nx_tcp_enable"></a>nx_tcp_enable

**Значок** ![Значок включения TCP](./media/user-guide/netx-events/image127.png)

**Описание**

Это событие представляет собой включение TCP через nx_tcp_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

###  <a name="tcp-free-port-find-tcp-free-port-find"></a>Поиск свободных TCP-портов 

#### <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

**Значок** ![Значок поиска свободных портов TCP](./media/user-guide/netx-events/image128.png)

**Описание**

Это событие представляет собой поиск свободного TCP-порта с помощью nx_tcp_free_port_find.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Запуск поиска номера порта
- Поле сведений 3. Номер свободного порта
- Поле сведений 4. Не используется

###  <a name="tcp-infomation-get"></a>Получение сведений о TCP 

#### <a name="nx_tcp_info_get"></a>nx_tcp_info_get

**Значок** ![Значок получения сведений о TCP](./media/user-guide/netx-events/image129.png)

**Описание**

Это событие представляет собой получение сведений о TCP для указанного экземпляра IP с помощью nx_tcp_info_get.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Число отправленных байтов
- Поле сведений 3. Число полученных байтов
- Поле сведений 4. Число недопустимых пакетов

###  <a name="tcp-server-socket-accept"></a>Принятие сокета сервера TCP 

#### <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

**Значок** ![Значок принятия сокета сервера TCP](./media/user-guide/netx-events/image130.png)

**Описание**

Это событие представляет собой настройку сокета сервера после получения активного запроса на подключение через nx_tcp_server_socket_accept.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Параметр Wait
- Поле сведений 4. Состояние сокета

###  <a name="tcp-server-socket-listen"></a>Прослушивание сокета сервера TCP 

#### <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

**Значок** ![Значок прослушивания сервера TCP](./media/user-guide/netx-events/image131.png)

**Описание**

Это событие представляет собой регистрацию запроса на прослушивание и сокета сервера для указанного TCP-порта с помощью nx_tcp_server_socket_listen.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Номер TCP-порта
- Поле сведений 3. Указатель на сокет
- Поле сведений 4. Максимальное число подключений, которые можно поставить в очередь

###  <a name="tcp-server-socket-relisten"></a>Повторное прослушивание сокета сервера TCP 

#### <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

**Значок** ![Значок повторного прослушивания сокета сервера TCP](./media/user-guide/netx-events/image132.png)

**Описание**

Это событие представляет собой регистрацию другого сокета сервера для существующего запроса на прослушивание по указанному TCP-порту с помощью nx_tcp_server_socket_relisten.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Номер TCP-порта
- Поле сведений 3. Указатель на сокет
- Поле сведений 4. Состояние сокета

###  <a name="tcp-server-socket-unaccept"></a>Отклонение сокета сервера TCP 

#### <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

**Значок** ![Значок отклонения сокета сервера TCP](./media/user-guide/netx-events/image133.png)

**Описание**

Это событие представляет собой удаление сокета сервера из связи с портом, получающим предыдущее пассивное подключение через nx_tcp_server_socket_unaccept.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Состояние сокета
- Поле сведений 4. Не используется

###  <a name="tcp-server-socket-unlisten-tcp-server-socket-unlisten"></a>Отмена прослушивания сокета сервера TCP 

#### <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

**Значок** ![Значок отмены прослушивания сервера TCP](./media/user-guide/netx-events/image134.png)

**Описание**

Это событие представляет собой удаление предыдущего запроса на прослушивание для указанного TCP-порта с помощью nx_tcp_server_socket_unlisten.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Номер TCP-порта
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="tcp-socket-bytes-available"></a>Доступные байты сокета TCP 

#### <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

**Значок** ![Значок доступных байтов сокета TCP](./media/user-guide/netx-events/image135.png)

**Описание**

Это событие представляет собой получение числа байтов, доступных в настоящее время в указанном сокете TCP, с помощью nx_tcp_socket_bytes_available.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет TCP
- Поле сведений 3. Количество байтов, полученных для сокета
- Поле сведений 4. Не используется

### <a name="tcp-socket-create"></a>Создание сокета TCP 

#### <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

**Значок** ![Значок создания сокета TCP](./media/user-guide/netx-events/image136.png)

**Описание**

Это событие представляет собой создание сокета TCP через nx_tcp_socket_create.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Тип службы
- Поле сведений 4. Размер окна приема

### <a name="tcp-socket-delete"></a>Удаление сокета TCP 

#### <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

**Значок** ![Значок удаления сокета TCP](./media/user-guide/netx-events/image137.png)

**Описание**

Это событие представляет собой удаление сокета с помощью nx_tcp_socket_delete.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Состояние сокета
- Поле сведений 4. Не используется

### <a name="tcp-socket-disconnect"></a>Отсоединение сокета TCP 

#### <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

**Значок** ![Значок отсоединения сокета TCP](./media/user-guide/netx-events/image138.png)

**Описание**

Это событие представляет собой отсоединение сокета через nx_tcp_socket_disconnect.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Параметр Wait
- Поле сведений 4. Состояние сокета

### <a name="tcp-socket-information-get"></a>Получение сведений о сокете TCP 

#### <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

**Значок** ![Значок получения сведений о сокете TCP](./media/user-guide/netx-events/image139.png)

**Описание**

Это событие представляет собой получение сведений о сокете через nx_tcp_socket_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Количество байтов, отправленных через этот сокет
- Поле сведений 4. Количество байтов, полученных через этот сокет

### <a name="tcp-socket-mss-get"></a>Получение MSS сокета TCP 

#### <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

**Значок** ![Значок получения MSS сокета TCP](./media/user-guide/netx-events/image140.png)

**Описание**

Это событие представляет собой получение MSS сокета через nx_tcp_socket_mss_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Максимальный размер сегмента (MSS)
- Поле сведений 4. Состояние сокета

### <a name="tcp-socket-mss-peer-get"></a>Получение значения MSS однорангового узла сокета 

#### <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

**Значок** ![Значок получения значения MSS однорангового узла сокета](./media/user-guide/netx-events/image141.png)

**Описание**

Это событие представляет собой получение значения MSS однорангового узла сокета через nx_tcp_socket_mss_peer_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. MSS однорангового узла
- Поле сведений 4. Состояние сокета

### <a name="tcp-socket-mss-set"></a>Задание значения MSS сокета TCP 

#### <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

**Значок** ![Значок задания значения MSS сокета TCP](./media/user-guide/netx-events/image142.png)

**Описание**

Это событие представляет собой задание значения MSS сокета через nx_tcp_socket_mss_set.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. MSS
- Поле сведений 4. Состояние сокета

### <a name="tcp-socket-peer-info-get"></a>Получение сведений об одноранговом узле сокета TCP 

#### <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

**Значок** ![Значок получения сведений об одноранговом узле сокета TCP](./media/user-guide/netx-events/image143.png)

**Описание**

Это событие представляет собой извлечение из сокета TCP сведений относительно узла (например, узел подключения), IP-адреса и порта через nx_tcp_socket_peer_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на сокет TCP
- Поле сведений 2. IP-адрес однорангового узла
- Поле сведений 3. Номер порта однорангового узла
- Поле сведений 4. Не используется

### <a name="tcp-socket-receive"></a>Получение сокета TCP 

#### <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

**Значок** ![Значок получения сокета TCP](./media/user-guide/netx-events/image144.png)

**Описание**

Это событие представляет собой получение данных от сокета через nx_tcp_socket_receive.

**Поля сведений**

- Поле сведений 1. Указатель на сокет
- Поле сведений 2. Указатель на полученный пакет
- Поле сведений 3. Длина полученного пакета
- Поле сведений 4. Получение порядкового номера

### <a name="tcp-socket-receive-notify"></a>Уведомление о получении сокета TCP 

#### <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

**Значок** ![Значок уведомления о получении сокета TCP](./media/user-guide/netx-events/image145.png)

**Описание**

Это событие представляет собой регистрацию обратного вызова уведомления о получении сокета через nx_tcp_socket_receive_notify.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель обратный вызов уведомления о получении. Поле сведений 4. Не используется

### <a name="tcp-socket-send"></a>Отправка сокета TCP 

#### <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

**Значок** ![Значок отправки сокета TCP](./media/user-guide/netx-events/image146.png)

**Описание**

Это событие представляет собой отправку данных через сокет с помощью nx_tcp_socket_send.

**Поля сведений**

- Поле сведений 1. Указатель на сокет
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Длина пакета
- Поле сведений 4. Порядковый номер передачи

### <a name="tcp-socket-state-wait"></a>Пребывание в состоянии ожидания для сокета TCP 

#### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

**Значок** ![Значок пребывания в состоянии ожидания для сокета TCP](./media/user-guide/netx-events/image147.png)

**Описание**

Это событие представляет собой ожидание сокетом на переход в определенное состояние через nx_tcp_socket_state_wait.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Требуемое состояние сокета
- Поле сведений 4. Предыдущее состояние сокета

### <a name="tcp-socket-transmit-configure"></a>Настройка передачи сокета TCP 

#### <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

**Значок** ![Значок настройки передачи сокета TCP](./media/user-guide/netx-events/image148.png)

**Описание**

Это событие представляет собой настройку параметров передачи сокета через nx_tcp_socket_transmit_configure.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Длина очереди передачи
- Поле сведений 4. Значение времени ожидания

### <a name="tcp-socket-window-update-notify-set"></a>Установка уведомления об обновлении окна сокета TCP 

#### <a name="nx_tcp_window_update_notify_set"></a>nx_tcp_window_update_notify_set

**Значок** ![Значок установки уведомления об обновлении окна сокета TCP](./media/user-guide/netx-events/image149.png)

**Описание**

Это событие представляет собой TCP-сокет, получающий уведомление об увеличении окна приема на удаленном узле через nx_tcp_window_update_notify_set.

**Поля сведений** 

- Поле сведений 1. Указатель на сокет TCP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="udp-enable"></a>Включение UDP 

#### <a name="nx_udp_enable"></a>nx_udp_enable

**Значок** ![Значок включения UDP](./media/user-guide/netx-events/image150.png)

**Описание**

Это событие представляет собой включение UDP через nx_udp_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Не используется
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="udp-free-port-find"></a>Поиск свободных портов UDP 

#### <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

**Значок** ![Значок поиска свободных портов UDP](./media/user-guide/netx-events/image151.png)

**Описание**

Это событие представляет собой поиск свободного UDP-порта с помощью nx_tcp_free_port_find.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Запуск порта для поиска
- Поле сведений 3. Свободный порт
- Поле сведений 4. Не используется

### <a name="udp-information-get"></a>Получение сведений о UDP 

#### <a name="nx_udp_info_get"></a>nx_udp_info_get

**Значок** ![Значок получения сведений о UDP](./media/user-guide/netx-events/image152.png)

**Описание**

Это событие представляет собой получение сведений о UDP с помощью nx_udp_info_get.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Количество отправленных байтов UDP
- Поле сведений 3. Количество полученных байтов UDP
- Поле сведений 4. Недопустимые пакеты

### <a name="udp-socket-bind"></a>Привязка UDP-сокета 

#### <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

**Значок** ![Значок привязки UDP-сокета](./media/user-guide/netx-events/image153.png)

**Описание**

Это событие представляет собой привязку UDP-сокета к порту с помощью nx_udp_socket_bind.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Номер порта
- Поле сведений 4. Параметр Wait

### <a name="udp-socket-bytes-available"></a>Доступные байты UDP-сокета 

#### <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

**Значок** ![Значок доступных байтов UDP-сокета](./media/user-guide/netx-events/image154.png)

**Описание**

Это событие представляет собой текущее число байтов, полученных через сокет UDP с помощью nx_udp_socket_bytes_available.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Количество байтов, полученных для сокета
- Поле сведений 4. Не используется

### <a name="udp-socket-checksum-disable"></a>Отключение контрольной суммы UDP-сокета 

#### <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

**Значок** ![Значок отключения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image155.png)

**Описание**

Это событие представляет собой отключение контрольной суммы для данных в сокете UDP через nx_udp_socket_checksum_disable.

**Поля сведений** 

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="udp-socket-checksum-enable"></a>Включение контрольной суммы UDP-сокета 

#### <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

**Значок** ![Значок включения контрольной суммы UDP-сокета](./media/user-guide/netx-events/image156.png)

**Описание**

Это событие представляет собой включение обработки контрольной суммы в сокете с помощью nx_udp_socket_checksum_enable.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="udp-socket-create"></a>Создание UDP-сокета 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Значок** ![Значок создания UDP-сокета](./media/user-guide/netx-events/image157.png)

**Описание**

Это событие представляет собой создание UDP-сокета с помощью nx_udp_socket_create.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Тип службы
- Поле сведений 4. Максимальная очередь получения

### <a name="udp-socket-delete-event"></a>Событие удаления UDP-сокета 

#### <a name="nx_udp_socket_delete-event"></a>Событие nx_udp_socket_delete

**Значок** ![Значок события удаления UDP-сокета](./media/user-guide/netx-events/image158.png)

**Описание**

Это событие представляет собой удаление UDP-сокета с помощью nx_tcp_socket_delete.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="udp-socket-information-get-event"></a>Событие получения сведений о сокете UDP 

#### <a name="nx_udp_socket_info_get-event"></a>Событие nx_udp_socket_info_get

**Значок** ![Значок события получения сведений о сокете UDP](./media/user-guide/netx-events/image159.png)

**Описание**

Это событие представляет собой получение сведений о сокете UDP через nx_tcp_socket_info_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Количество байтов, отправленных через сокет
- Поле сведений 4. Количество байтов, полученных через сокет

### <a name="udp-socket-interface-set"></a>Установка интерфейса сокетов UDP 

#### <a name="nx_udp_socket_interface_set-event"></a>Событие nx_udp_socket_interface_set

**Значок** ![Значок установки интерфейса сокетов UDP](./media/user-guide/netx-events/image160.png)

**Описание**

Это событие представляет собой установку исходящего интерфейса указанного UDP-сокета с указанным интерфейсом через nx_udp_socket_interface_set.

**Поля сведений**

- Поле сведений 1. Указатель на сокет UDP
- Поле сведений 2. Индекс, соответствующий интерфейсу для сокета
- Поле сведений 3. Не используется
- Поле сведений 4. Не используется

### <a name="udp-socket-port-get"></a>Получение порта UDP-сокета 

#### <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

**Значок** ![Значок получения порта UDP-сокета](./media/user-guide/netx-events/image161.png)

**Описание**

Это событие представляет собой получение UDP-порта, к которому привязан указанный сокет UDP, через nx_udp_socket_port_get.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет UDP
- Поле сведений 3. Номер порта
- Поле сведений 4. Не используется

### <a name="udp-socket-receive"></a>Получение UDP-сокета 

#### <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

**Значок** ![Значок получения UDP-сокета](./media/user-guide/netx-events/image162.png)

**Описание**

Это событие представляет собой получение данных по указанному сокету UDP через nx_udp_socket_receive.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет UDP
- Поле сведений 3. Указатель на полученный пакет
- Поле сведений 4. Размер полученного пакета

### <a name="udp-socket-receive-notify"></a>Уведомление о получении UDP-сокета 

#### <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

**Значок** ![Значок уведомления о получении UDP-сокета](./media/user-guide/netx-events/image163.png) **Описание**

Это событие представляет собой регистрацию обратного вызова уведомления о получении через nx_udp_socket_receive_notify.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Указатель на функцию получения уведомлений. Поле сведений 4. Не используется

### <a name="udp-socket-send"></a>Отправка UDP-сокета 

#### <a name="nx_udp_socket_send"></a>nx_udp_socket_send

**Значок** ![Значок отправки UDP-сокета](./media/user-guide/netx-events/image164.png)

**Описание**

Это событие представляет собой отправку данных через сокет UDP с помощью nx_udp_socket_send.

**Поля сведений**

- Поле сведений 1. Указатель на сокет
- Поле сведений 2. Указатель на пакет
- Поле сведений 3. Длина пакета
- Поле сведений 4. IP-адрес пункта назначения

### <a name="udp-socket-unbind"></a>Отмена привязки UDP-сокета 

#### <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

**Значок** ![Значок отмены привязки UDP-сокета](./media/user-guide/netx-events/image165.png)

**Описание**

Это событие представляет собой отмену привязки UDP-порта к сокету через nx_udp_socket_unbind.

**Поля сведений**

- Поле сведений 1. Указатель на экземпляр IP
- Поле сведений 2. Указатель на сокет
- Поле сведений 3. Номер порта
- Поле сведений 4. Не используется

### <a name="udp-source-extract"></a>Извлечение источника UDP 

#### <a name="nx_udp_socket_create"></a>nx_udp_socket_create

**Значок** ![Значок извлечения источника UDP](./media/user-guide/netx-events/image166.png)

**Описание**

Это событие представляет собой получение IP-адреса и номера порта полученного пакета UDP через nx_udp_source_extract.

**Поля сведений**

- Поле сведений 1. Указатель на пакет
- Поле сведений 2. IP-адрес отправителя
- Поле сведений 3. Номер порта отправителя
- Поле сведений 4. Не используется