---
title: Основные сведения о NetX в ОСРВ Azure
description: NetX в ОСРВ Azure — это высокопроизводительная реализация стандартов протокола TCP/IP, полностью интегрированная с ThreadX в ОСРВ Azure и доступная для всех поддерживаемых процессоров.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 029f73b755d5c40279125fb010ec35baaaf7f38d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814443"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="fb411-103">Общие сведения о NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fb411-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="fb411-104">NetX в ОСРВ Azure — это сетевой стек TCP/IP промышленного класса с внедренным протоколом IPv4, предназначенный специально для глубоко встраиваемых приложений, работающих в реальном времени, и приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="fb411-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="fb411-105">NetX в ОСРВ Azure — это оригинальный сетевой стек IPv4 от Майкрософт. Он фактически является подмножеством ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="fb411-106">NetX предоставляет встраиваемым приложениям базовые сетевые протоколы, такие как IPv4, TCP и UDP, а также полный набор дополнительных подключаемых протоколов.</span><span class="sxs-lookup"><span data-stu-id="fb411-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="fb411-107">Небольшой объем занимаемой памяти, высокая производительность и непревзойденная простота использования делают NetX в ОСРВ Azure идеальным вариантом при использовании самых требовательных встраиваемых приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="fb411-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="fb411-108">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="fb411-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="fb411-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="fb411-109">TELNET</span></span>

* <span data-ttu-id="fb411-110">Минимум занимаемой памяти — 0,5 КБ и 0,3 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-110">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-111">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fb411-111">Client and server support</span></span>
* <span data-ttu-id="fb411-112">Интуитивно простые API-интерфейсы Telnet: *nx_telnet_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-112">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="auto-ip"></a><span data-ttu-id="fb411-113">Auto IP</span><span class="sxs-lookup"><span data-stu-id="fb411-113">Auto IP</span></span>

* <span data-ttu-id="fb411-114">Автоматическое назначение IPv4-адресов.</span><span class="sxs-lookup"><span data-stu-id="fb411-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="fb411-115">Минимум занимаемой памяти — 1,2 КБ и 300 байт в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="fb411-116">Интуитивно простые API-интерфейсы AutoIP: *nx_autoip_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="fb411-117">HTTP</span><span class="sxs-lookup"><span data-stu-id="fb411-117">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="fb411-118">Минимум занимаемой памяти — флэш-память: 2,8–4,8 КБ; ОЗУ: 0,4 –1,0 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-118">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-119">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fb411-119">Client and server support</span></span>
* <span data-ttu-id="fb411-120">Интуитивно простые API-интерфейсы HTTP: *nx_http_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-120">Intuitive HTTP APIs: *nx_http_\**</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="fb411-121">SMTP</span><span class="sxs-lookup"><span data-stu-id="fb411-121">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="fb411-122">Минимум занимаемой памяти — 4,1 КБ и 0,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-122">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-123">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fb411-123">Client support</span></span>
* <span data-ttu-id="fb411-124">Интуитивно простые API-интерфейсы SMTP: *nx_smtp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-124">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="fb411-125">DHCP (протокол динамической конфигурации узла)</span><span class="sxs-lookup"><span data-stu-id="fb411-125">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="fb411-126">Минимум занимаемой памяти — флэш-память: 3,6–4,6 КБ; ОЗУ: 2,7 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-126">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-127">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fb411-127">Client and server support</span></span>
* <span data-ttu-id="fb411-128">Поддержка IPv4.</span><span class="sxs-lookup"><span data-stu-id="fb411-128">IPv4 support</span></span>
* <span data-ttu-id="fb411-129">Интуитивно простые API-интерфейсы DHCP: *nx_dhcp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-129">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="fb411-130">POP3</span><span class="sxs-lookup"><span data-stu-id="fb411-130">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="fb411-131">Минимум занимаемой памяти — 8,1 КБ и 1,4 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-131">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-132">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fb411-132">Client support</span></span>
* <span data-ttu-id="fb411-133">Интуитивно простые API-интерфейсы P0P3: *nx_pop3_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-133">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="fb411-134">SNMP</span><span class="sxs-lookup"><span data-stu-id="fb411-134">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="fb411-135">Минимум занимаемой памяти — 10,9 КБ и 2,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-135">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-136">Поддержка агентов для VI, V2 и V3.</span><span class="sxs-lookup"><span data-stu-id="fb411-136">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="fb411-137">Интуитивно простые API-интерфейсы SNMP: *nx_snmp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-137">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="fb411-138">FTP и TFTP</span><span class="sxs-lookup"><span data-stu-id="fb411-138">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="fb411-139">Минимум занимаемой памяти FTP — флэш-память: 1,8–7,2 КБ; ОЗУ: 0,6–2,1 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-139">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-140">Минимум занимаемой памяти TFTP — флэш-память: 1,7–2,4 КБ; ОЗУ: 0,3–1,8 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-140">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-141">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fb411-141">Client and server support</span></span>
* <span data-ttu-id="fb411-142">Интуитивно простые API-интерфейсы FTP и TFTP: <i>nx_ftp_ *</i> или <i>nx_tftp_* </i>.</span><span class="sxs-lookup"><span data-stu-id="fb411-142">Intuitive FTP and TFTP APIs: <i>nx_ftp_ *</i> or <i>nx_tftp_*</i></span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="fb411-143">PPP</span><span class="sxs-lookup"><span data-stu-id="fb411-143">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="fb411-144">Минимум занимаемой памяти — 7,1 КБ и 3,8 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-144">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-145">Интуитивно простые API-интерфейсы PPP: *nx_ppp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-145">Intuitive PPP APIs: *nx_ppp_\**</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="fb411-146">SNTP</span><span class="sxs-lookup"><span data-stu-id="fb411-146">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="fb411-147">Минимум занимаемой памяти — 4 КБ и 0,5 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fb411-147">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="fb411-148">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fb411-148">Client support</span></span>
* <span data-ttu-id="fb411-149">Интуитивно простые API-интерфейсы SNTP: *nx_sntp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-149">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="fb411-150">API NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fb411-150">Azure RTOS NetX API</span></span>

* <span data-ttu-id="fb411-151">Интуитивно простой и согласованный API.</span><span class="sxs-lookup"><span data-stu-id="fb411-151">Intuitive and consistent API</span></span>
* <span data-ttu-id="fb411-152">Соглашение об именовании с использованием конструкции "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="fb411-152">Noun-verb naming convention</span></span>
* <span data-ttu-id="fb411-153">Быстрая реализация API без копирования.</span><span class="sxs-lookup"><span data-stu-id="fb411-153">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="fb411-154">Все функции API имеют префикс <i>nx_\*</i> для простой идентификации принадлежности к NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-154">All API functions have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="fb411-155">Блокирующие функции API дополнительно поддерживают ожидание потока в определенном интервале времени.</span><span class="sxs-lookup"><span data-stu-id="fb411-155">Blocking API functions have an optional thread timeout</span></span>
* <span data-ttu-id="fb411-156">Дополнительный уровень BSD для переноса старого кода сокетов.</span><span class="sxs-lookup"><span data-stu-id="fb411-156">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="fb411-157">IGMP</span><span class="sxs-lookup"><span data-stu-id="fb411-157">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="fb411-158">Минимум занимаемой флэш-памяти — 2,5 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-158">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fb411-159">Поддержка групп многоадресной рассылки IPv4.</span><span class="sxs-lookup"><span data-stu-id="fb411-159">IPv4 multicast group support</span></span>
* <span data-ttu-id="fb411-160">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fb411-160">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="fb411-161">Статистика IGMP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-161">Optional IGMP statistics</span></span>
* <span data-ttu-id="fb411-162">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-162">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb411-163">Интуитивно простые API-интерфейсы IGMP: *nx_igmp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-163">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="fb411-164">UDP</span><span class="sxs-lookup"><span data-stu-id="fb411-164">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="fb411-165">Минимум занимаемой памяти — флэш-память: 2,5 КБ; ОЗУ: 124 байт на сокет.</span><span class="sxs-lookup"><span data-stu-id="fb411-165">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="fb411-166">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="fb411-166">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="fb411-167">RX на уровне 95 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 14 %.</span><span class="sxs-lookup"><span data-stu-id="fb411-167">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="fb411-168">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 10 %.</span><span class="sxs-lookup"><span data-stu-id="fb411-168">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="fb411-169">Технология UDP Fast Path™.</span><span class="sxs-lookup"><span data-stu-id="fb411-169">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="fb411-170">Отсутствие ограничений на число UDP.</span><span class="sxs-lookup"><span data-stu-id="fb411-170">No limits on the number of UDP</span></span>
* <span data-ttu-id="fb411-171">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fb411-171">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="fb411-172">Приостановка при получении в сокет (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-172">Optional suspension on socket receive</span></span>
* <span data-ttu-id="fb411-173">Время ожидания при всех приостановках (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-173">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb411-174">Статистика UDP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-174">Optional UDP statistics</span></span>
* <span data-ttu-id="fb411-175">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-175">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb411-176">Интуитивно простые API-интерфейсы UDP: *nx_udp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-176">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="fb411-177">TCP</span><span class="sxs-lookup"><span data-stu-id="fb411-177">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="fb411-178">Минимум занимаемой памяти — флэш-память: 10,5–12,5 КБ; ОЗУ: 280 байт на сокет.</span><span class="sxs-lookup"><span data-stu-id="fb411-178">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="fb411-179">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="fb411-179">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="fb411-180">RX на уровне 93 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 20 %.</span><span class="sxs-lookup"><span data-stu-id="fb411-180">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="fb411-181">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 27 %.</span><span class="sxs-lookup"><span data-stu-id="fb411-181">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="fb411-182">Надежное подключение.</span><span class="sxs-lookup"><span data-stu-id="fb411-182">Reliable connection</span></span>
* <span data-ttu-id="fb411-183">Отсутствие ограничений на число TCP-сокетов.</span><span class="sxs-lookup"><span data-stu-id="fb411-183">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="fb411-184">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fb411-184">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="fb411-185">Приостановка при получении или отправке в сокете (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-185">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="fb411-186">Время ожидания при всех приостановках (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-186">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb411-187">Статистика TCP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-187">Optional TCP statistics</span></span>
* <span data-ttu-id="fb411-188">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-188">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb411-189">Интуитивно простые API-интерфейсы TCP: *nx_tcp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-189">Intuitive TCP APIs:  *nx_tcp_\**</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="fb411-190">ICMP</span><span class="sxs-lookup"><span data-stu-id="fb411-190">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="fb411-191">Минимум занимаемой флэш-памяти — 2,5 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-191">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fb411-192">Поддержка IPv4.</span><span class="sxs-lookup"><span data-stu-id="fb411-192">IPv4 support</span></span>
* <span data-ttu-id="fb411-193">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fb411-193">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="fb411-194">Запрос проверки связи и ответ на нее.</span><span class="sxs-lookup"><span data-stu-id="fb411-194">Ping request and ping response</span></span>
* <span data-ttu-id="fb411-195">Приостановка потока при запросах проверки связи (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-195">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="fb411-196">Время ожидания при всех приостановках (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-196">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fb411-197">Статистика ICMP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-197">Optional ICMP statistics</span></span>
* <span data-ttu-id="fb411-198">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-198">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb411-199">Интуитивно простые API-интерфейсы ICMP: *nx_icmp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-199">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="fb411-200">IPv4 (IP)</span><span class="sxs-lookup"><span data-stu-id="fb411-200">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="fb411-201">Минимум занимаемой памяти — флэш-память: 3,5–8,5 КБ; ОЗУ: 2–3 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-201">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="fb411-202">Архитектура Piconet™.</span><span class="sxs-lookup"><span data-stu-id="fb411-202">Piconet™ Architecture</span></span>
* <span data-ttu-id="fb411-203">Высокая производительность на уровне проводной сети.</span><span class="sxs-lookup"><span data-stu-id="fb411-203">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="fb411-204">Поддержка нескольких интерфейсов</span><span class="sxs-lookup"><span data-stu-id="fb411-204">Multiple interface support</span></span>
* <span data-ttu-id="fb411-205">Поддержка многосетевых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="fb411-205">Multihomed support</span></span>
* <span data-ttu-id="fb411-206">Поддержка статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="fb411-206">Static routing support</span></span>
* <span data-ttu-id="fb411-207">Поддержка фрагментирования и пересборки IP.</span><span class="sxs-lookup"><span data-stu-id="fb411-207">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="fb411-208">Поддержка IPv4.</span><span class="sxs-lookup"><span data-stu-id="fb411-208">IPv4 Support</span></span>
* <span data-ttu-id="fb411-209">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fb411-209">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="fb411-210">Сертификация с логотипом Phase II Ready.</span><span class="sxs-lookup"><span data-stu-id="fb411-210">Phase II Ready Logo Certification</span></span>
* <span data-ttu-id="fb411-211">Статистика IP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-211">Optional IP statistics</span></span>
* <span data-ttu-id="fb411-212">Хорошо определенный, интуитивно простой интерфейс драйвера физического уровня.</span><span class="sxs-lookup"><span data-stu-id="fb411-212">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="fb411-213">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-213">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb411-214">Интуитивно простые API-интерфейсы уровня IP: *nx_ip_\** , *nxd_ip_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-214">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**</span></span>
* <span data-ttu-id="fb411-215">Предварительная сертификация TUV и UL на соответствие стандартам IEC 61508 SIL 4, IEC 62304 (класс C), ISO 26262 ASIL D и EN 50128 SW-SIL4.</span><span class="sxs-lookup"><span data-stu-id="fb411-215">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="fb411-216">ARP и RARP</span><span class="sxs-lookup"><span data-stu-id="fb411-216">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="fb411-217">Минимум занимаемой памяти — флэш-память и ОЗУ: 1,7 КБ.</span><span class="sxs-lookup"><span data-stu-id="fb411-217">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="fb411-218">Динамическое разрешение 32-разрядных IPv4-адресов и 48-разрядных MAC-адресов.</span><span class="sxs-lookup"><span data-stu-id="fb411-218">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="fb411-219">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fb411-219">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="fb411-220">Гибкий, определяемый пользователем кэш ARP.</span><span class="sxs-lookup"><span data-stu-id="fb411-220">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="fb411-221">Поддержка самообращенных запросов ARP.</span><span class="sxs-lookup"><span data-stu-id="fb411-221">Gratuitous ARP support</span></span>
* <span data-ttu-id="fb411-222">Статистика ARP/RARP, определяемая приложением (необязательно).</span><span class="sxs-lookup"><span data-stu-id="fb411-222">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="fb411-223">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-223">System-level Trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fb411-224">Интуитивно простые API-интерфейсы ARP/RARP: *nx_arp_\** , *nx_rarp_\** .</span><span class="sxs-lookup"><span data-stu-id="fb411-224">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="fb411-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4 и т. д.</span><span class="sxs-lookup"><span data-stu-id="fb411-225">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="small-footprint"></a><span data-ttu-id="fb411-226">Небольшой объем занимаемой памяти</span><span class="sxs-lookup"><span data-stu-id="fb411-226">Small-footprint</span></span>

<span data-ttu-id="fb411-227">NetX в ОСРВ Azure занимает всего 9–15 КБ при базовой поддержке IP и UDP.</span><span class="sxs-lookup"><span data-stu-id="fb411-227">Azure RTOS NetX has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="fb411-228">Для функций TCP требуются дополнительно 10–13 КБ памяти области инструкций.</span><span class="sxs-lookup"><span data-stu-id="fb411-228">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="fb411-229">NetX в ОСРВ Azure обычно занимает в ОЗУ от 2,6 до 3,6 КБ, а также некоторый объем памяти пула пакетов, который определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="fb411-229">Azure RTOS NetX RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="fb411-230">Как и с ThreadX в ОСРВ Azure, размер NetX в ОСРВ Azure масштабируется автоматически в зависимости от служб, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="fb411-230">Like Azure RTOS ThreadX, the size of Azure RTOS NetX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="fb411-231">Это практически устраняет потребность в сложной настройке и параметрах сборки, что упрощает работу разработчика.</span><span class="sxs-lookup"><span data-stu-id="fb411-231">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="fb411-232">Быстрое выполнение</span><span class="sxs-lookup"><span data-stu-id="fb411-232">Fast execution</span></span>

<span data-ttu-id="fb411-233">NetX в ОСРВ Azure предоставляет реализацию отправки и получения пакетов без копирования. Решение тесно интегрировано со ThreadX в ОСРВ Azure для достижения максимальной возможной производительности.</span><span class="sxs-lookup"><span data-stu-id="fb411-233">Azure RTOS NetX provides a zero-copy packet send/receive implementation and is highly integrated with Azure RTOS ThreadX to achieve the fastest possible performance.</span></span> <span data-ttu-id="fb411-234">Например, NetX в ОСРВ Azure может достигать скоростей передачи данных, сравнимых с проводной сетью, с процессором с частотой 80 МГц (или менее), используя лишь незначительную часть его ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fb411-234">For example, Azure RTOS NetX can typically achieve near wirespeed data transfers on an 80-MHz processor (or less), while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="fb411-235">Простота использования</span><span class="sxs-lookup"><span data-stu-id="fb411-235">Simple, easy-to-use</span></span>

<span data-ttu-id="fb411-236">NetX в ОСРВ Azure очень легко использовать.</span><span class="sxs-lookup"><span data-stu-id="fb411-236">Azure RTOS NetX is simple to use.</span></span> <span data-ttu-id="fb411-237">API NetX в ОСРВ Azure предоставляет интуитивно простые, но широкие функции.</span><span class="sxs-lookup"><span data-stu-id="fb411-237">The Azure RTOS NetX API is both intuitive and highly functional.</span></span> <span data-ttu-id="fb411-238">Имена API состоят из реальных слов, а не из набора букв или сокращенных имен, которые часто используются для других сетевых продуктов.</span><span class="sxs-lookup"><span data-stu-id="fb411-238">The API names are made of real words and not “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="fb411-239">Все API-интерфейсы NetX в ОСРВ Azure имеют префикс *nx_* и соответствуют соглашению об именовании с использованием конструкций "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="fb411-239">All Azure RTOS NetX APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="fb411-240">Более того, для API обеспечивается функциональная согласованность.</span><span class="sxs-lookup"><span data-stu-id="fb411-240">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="fb411-241">Например, для всех функций API, которые поддерживают приостановку работы, реализована необязательная возможность использовать время ожидания. Возможность функционирует одинаково для всех функций.</span><span class="sxs-lookup"><span data-stu-id="fb411-241">For example, all API functions that suspend have an optional timeout that functions in an identical manner.</span></span> <span data-ttu-id="fb411-242">Для устаревших приложений NetX в ОСРВ Azure предлагает дополнительный уровень, совместимый с сокетами BSD.</span><span class="sxs-lookup"><span data-stu-id="fb411-242">For legacy applications, Azure RTOS NetX offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="fb411-243">Этот уровень помогает разработчикам переносить крупные сетевые приложения.</span><span class="sxs-lookup"><span data-stu-id="fb411-243">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="fb411-244">Подтвержденная совместимость</span><span class="sxs-lookup"><span data-stu-id="fb411-244">Interoperability verification</span></span>

<span data-ttu-id="fb411-245">NetX в ОСРВ Azure соответствует стандартам RFC и обеспечивает полную совместимость с устройствами большинства поставщиков.</span><span class="sxs-lookup"><span data-stu-id="fb411-245">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="fb411-246">Кроме того, NetX в ОСРВ Azure использует стандартную отраслевую библиотеку IxANVL для базовой реализации протокола TCP/IP в NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-246">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="fb411-247">Передовая технология</span><span class="sxs-lookup"><span data-stu-id="fb411-247">Advanced technology</span></span>

<span data-ttu-id="fb411-248">NetX в ОСРВ Azure — эта передовая технология, включающая следующее:</span><span class="sxs-lookup"><span data-stu-id="fb411-248">Azure RTOS NetX is advanced technology that includes:</span></span>

* <span data-ttu-id="fb411-249">архитектуру Piconet™;</span><span class="sxs-lookup"><span data-stu-id="fb411-249">Piconet™ architecture</span></span>
* <span data-ttu-id="fb411-250">автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="fb411-250">automatic scaling</span></span>
* <span data-ttu-id="fb411-251">технологию UDP Fast-Path™;</span><span class="sxs-lookup"><span data-stu-id="fb411-251">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="fb411-252">гибкое управление пакетами;</span><span class="sxs-lookup"><span data-stu-id="fb411-252">flexible packet management</span></span>
* <span data-ttu-id="fb411-253">API и реализациб без копирования;</span><span class="sxs-lookup"><span data-stu-id="fb411-253">zero-copy API and implementation</span></span>
* <span data-ttu-id="fb411-254">поддержку многосетевых интерфейсов;</span><span class="sxs-lookup"><span data-stu-id="fb411-254">multihomed support</span></span>
* <span data-ttu-id="fb411-255">время ожидания при всех приостановках (необязательно);</span><span class="sxs-lookup"><span data-stu-id="fb411-255">optional timeout on all suspension</span></span>
* <span data-ttu-id="fb411-256">поддержку статической маршрутизации;</span><span class="sxs-lookup"><span data-stu-id="fb411-256">static routing support</span></span>
* <span data-ttu-id="fb411-257">поддержку системного анализа TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fb411-257">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="fb411-258">Минимальное время выхода на рынок</span><span class="sxs-lookup"><span data-stu-id="fb411-258">Fastest time-to-market</span></span>

<span data-ttu-id="fb411-259">NetX в ОСРВ Azure легко устанавливать, изучать, использовать, отлаживать, проверять, сертифицировать и обслуживать.</span><span class="sxs-lookup"><span data-stu-id="fb411-259">Azure RTOS NetX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="fb411-260">Поэтому NetX в ОСРВ Azure является одним из самых популярных стеков TCP/IP для встраиваемых устройств Интернета вещей, в том числе для множества интегральных систем от Broadcom, Gainspan и т. д.</span><span class="sxs-lookup"><span data-stu-id="fb411-260">As a result, Azure RTOS NetX is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, and so forth.</span></span> <span data-ttu-id="fb411-261">Наше преимущество по стабильно малому времени выхода на рынок обусловлено следующим:</span><span class="sxs-lookup"><span data-stu-id="fb411-261">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="fb411-262">документация высокого качества — ознакомьтесь с нашим [руководством пользователя по NetX в ОСРВ Azure](about-this-guide.md) и убедитесь в этом сами;</span><span class="sxs-lookup"><span data-stu-id="fb411-262">quality documentation – please review our [Azure RTOS NetX User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="fb411-263">полная доступность исходного кода;</span><span class="sxs-lookup"><span data-stu-id="fb411-263">complete source code availability</span></span>
* <span data-ttu-id="fb411-264">простые в использовании API-интерфейсы;</span><span class="sxs-lookup"><span data-stu-id="fb411-264">easy-to-use API</span></span>
* <span data-ttu-id="fb411-265">комплексный и широкий набор функций.</span><span class="sxs-lookup"><span data-stu-id="fb411-265">comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="fb411-266">Одна простая лицензия</span><span class="sxs-lookup"><span data-stu-id="fb411-266">One Simple License</span></span>

<span data-ttu-id="fb411-267">Использование и тестирование исходного кода не требуют каких-либо затрат, как и лицензии для рабочей среды при развертывании на предварительно лицензированных устройствах. Для всех других устройств требуется лишь простая лицензия сроком на один год.</span><span class="sxs-lookup"><span data-stu-id="fb411-267">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="fb411-268">Полный и высококачественный исходный код</span><span class="sxs-lookup"><span data-stu-id="fb411-268">Full, highest-quality source code</span></span>

<span data-ttu-id="fb411-269">Уже несколько лет NetX в ОСРВ Azure задает стандарт качества и простоты понимания.</span><span class="sxs-lookup"><span data-stu-id="fb411-269">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="fb411-270">Кроме того, соглашение по назначению каждой функции отдельного файла упрощает навигацию по исходному коду.</span><span class="sxs-lookup"><span data-stu-id="fb411-270">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="fb411-271">Поддержка большинства популярных архитектур</span><span class="sxs-lookup"><span data-stu-id="fb411-271">Supports most popular architectures</span></span>

<span data-ttu-id="fb411-272">NetX в ОСРВ Azure работает с большинством популярных 32/64-разрядных микропроцессоров. Этот стек не требует дополнительной настройки, полностью протестирован и поддерживается в том числе в следующих передовых архитектурах:</span><span class="sxs-lookup"><span data-stu-id="fb411-272">Azure RTOS NetX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="fb411-273">**Analog Devices**: SHARC, Blackfin, CM4xx;</span><span class="sxs-lookup"><span data-stu-id="fb411-273">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="fb411-274">**Andes Core**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="fb411-274">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="fb411-275">**Ambiqmicro**: микроконтроллеры Apollo;</span><span class="sxs-lookup"><span data-stu-id="fb411-275">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="fb411-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M;</span><span class="sxs-lookup"><span data-stu-id="fb411-276">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="fb411-277">**Cadence**: Xtensa, Diamond;</span><span class="sxs-lookup"><span data-stu-id="fb411-277">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="fb411-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi;</span><span class="sxs-lookup"><span data-stu-id="fb411-278">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="fb411-279">**Cypress**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="fb411-279">**Cypress**: RISC-V</span></span>

<span data-ttu-id="fb411-280">**EnSilica**: eSi-RISC;</span><span class="sxs-lookup"><span data-stu-id="fb411-280">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="fb411-281">**Infineon**: XMC1000, XMC4000, TriCore;</span><span class="sxs-lookup"><span data-stu-id="fb411-281">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="fb411-282">**Intel; ППВМ Intel**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10;</span><span class="sxs-lookup"><span data-stu-id="fb411-282">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="fb411-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32;</span><span class="sxs-lookup"><span data-stu-id="fb411-283">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="fb411-284">**Microsemi**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="fb411-284">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="fb411-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4;</span><span class="sxs-lookup"><span data-stu-id="fb411-285">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="fb411-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy;</span><span class="sxs-lookup"><span data-stu-id="fb411-286">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="fb411-287">**Silicon Labs**: EFM32;</span><span class="sxs-lookup"><span data-stu-id="fb411-287">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="fb411-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS;</span><span class="sxs-lookup"><span data-stu-id="fb411-288">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="fb411-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7;</span><span class="sxs-lookup"><span data-stu-id="fb411-289">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="fb411-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C;</span><span class="sxs-lookup"><span data-stu-id="fb411-290">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="fb411-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class;</span><span class="sxs-lookup"><span data-stu-id="fb411-291">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="fb411-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE.</span><span class="sxs-lookup"><span data-stu-id="fb411-292">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="fb411-293">*Все приведенные сведения о времени ожидания и размере могут отличаться от фактических. Это зависит от платформы разработки.*</span><span class="sxs-lookup"><span data-stu-id="fb411-293">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
