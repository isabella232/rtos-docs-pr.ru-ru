---
title: Основные сведения о NetX в ОСРВ Azure
description: NetX в ОСРВ Azure — это высокопроизводительная реализация стандартов протокола TCP/IP, полностью интегрированная с ThreadX в ОСРВ Azure и доступная для всех поддерживаемых процессоров.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 7c864c23f019e4841ddb3096fde663c8039baf44
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171324"
---
# <a name="overview-of-azure-rtos-netx"></a><span data-ttu-id="33575-103">Общие сведения о NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="33575-103">Overview of Azure RTOS NetX</span></span>

<span data-ttu-id="33575-104">NetX в ОСРВ Azure — это сетевой стек TCP/IP промышленного класса с внедренным протоколом IPv4, предназначенный специально для глубоко встраиваемых приложений, работающих в реальном времени, и приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="33575-104">Azure RTOS NetX is an industrial grade TCP/IP IPv4 embedded network stack, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="33575-105">NetX в ОСРВ Azure — это оригинальный сетевой стек IPv4 от Майкрософт. Он фактически является подмножеством ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-105">Azure RTOS NetX is Microsoft's original IPv4 network stack, and is essentially a subset of Azure RTOS.</span></span> <span data-ttu-id="33575-106">NetX предоставляет встраиваемым приложениям базовые сетевые протоколы, такие как IPv4, TCP и UDP, а также полный набор дополнительных подключаемых протоколов.</span><span class="sxs-lookup"><span data-stu-id="33575-106">NetX provides embedded applications with core network protocols such as IPv4, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="33575-107">Небольшой объем занимаемой памяти, высокая производительность и непревзойденная простота использования делают NetX в ОСРВ Azure идеальным вариантом при использовании самых требовательных встраиваемых приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="33575-107">A small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX an ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="33575-108">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="33575-108">API protocols</span></span>

### <a name="telnet"></a><span data-ttu-id="33575-109">TELNET</span><span class="sxs-lookup"><span data-stu-id="33575-109">TELNET</span></span>

* <span data-ttu-id="33575-110">Минимум занимаемой памяти — 0,5 КБ и 0,3 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-110">Minimal 0.5 KB and 0.3 KB RAM footprint.</span></span>
* <span data-ttu-id="33575-111">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="33575-111">Client and server support.</span></span>

### <a name="auto-ip"></a><span data-ttu-id="33575-112">Auto IP</span><span class="sxs-lookup"><span data-stu-id="33575-112">Auto IP</span></span>

* <span data-ttu-id="33575-113">Автоматическое назначение IPv4-адресов.</span><span class="sxs-lookup"><span data-stu-id="33575-113">Automatic IPv4 address assignment.</span></span>
* <span data-ttu-id="33575-114">Минимум занимаемой памяти — 1,2 КБ и 300 байт в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-114">Minimal 1.2 KB, 300 bytes of RAM.</span></span>

### <a name="http---hypertext-transfer-protocolhttp"></a><span data-ttu-id="33575-115">HTTP</span><span class="sxs-lookup"><span data-stu-id="33575-115">HTTP - Hypertext Transfer Protocol(HTTP)</span></span>

* <span data-ttu-id="33575-116">Минимум занимаемой памяти — флэш-память: 2,8–4,8 КБ; ОЗУ: 0,4 –1,0 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-116">Minimal 2.8 KB to 4.8KBFLASH, 0.4 KB to 1.0 KB RAM footprint.</span></span>
* <span data-ttu-id="33575-117">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="33575-117">Client and server support.</span></span>

### <a name="smtp---simple-mail-transfer-protocol-smtp"></a><span data-ttu-id="33575-118">SMTP</span><span class="sxs-lookup"><span data-stu-id="33575-118">SMTP - Simple Mail Transfer Protocol (SMTP)</span></span>

* <span data-ttu-id="33575-119">Минимум занимаемой памяти — 4,1 КБ и 0,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-119">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="33575-120">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="33575-120">Client support</span></span>

### <a name="dhcp---dynamic-host-configuration-protocol-dhcp"></a><span data-ttu-id="33575-121">DHCP (протокол динамической конфигурации узла)</span><span class="sxs-lookup"><span data-stu-id="33575-121">DHCP - Dynamic Host Configuration Protocol (DHCP)</span></span>

* <span data-ttu-id="33575-122">Минимум занимаемой памяти — флэш-память: 3,6–4,6 КБ; ОЗУ: 2,7 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-122">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="33575-123">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="33575-123">Client and server support</span></span>
* <span data-ttu-id="33575-124">Поддержка IPv4.</span><span class="sxs-lookup"><span data-stu-id="33575-124">IPv4 support</span></span>

### <a name="p0p3---post-office-protocol-version-3-pop3"></a><span data-ttu-id="33575-125">POP3</span><span class="sxs-lookup"><span data-stu-id="33575-125">P0P3 - Post Office Protocol Version 3 (POP3)</span></span>

* <span data-ttu-id="33575-126">Минимум занимаемой памяти — 8,1 КБ и 1,4 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-126">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="33575-127">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="33575-127">Client support</span></span>

### <a name="snmp---simple-network-management-protocol-snmp"></a><span data-ttu-id="33575-128">SNMP</span><span class="sxs-lookup"><span data-stu-id="33575-128">SNMP - Simple Network Management Protocol (SNMP)</span></span>

* <span data-ttu-id="33575-129">Минимум занимаемой памяти — 10,9 КБ и 2,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-129">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="33575-130">Поддержка версий 1, 2 и 3.</span><span class="sxs-lookup"><span data-stu-id="33575-130">Agent support for VI, V2, and V3</span></span>

### <a name="ftp-tftp---file-transfer-protocol-ftp-trivial-file-transfer-protocol-tftp"></a><span data-ttu-id="33575-131">FTP и TFTP</span><span class="sxs-lookup"><span data-stu-id="33575-131">FTP, TFTP - File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP)</span></span>

* <span data-ttu-id="33575-132">Минимум занимаемой памяти FTP — флэш-память: 1,8–7,2 КБ; ОЗУ: 0,6–2,1 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-132">FTP Minimal 1.8 KB to 7.2KBFLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="33575-133">Минимум занимаемой памяти TFTP — флэш-память: 1,7–2,4 КБ; ОЗУ: 0,3–1,8 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-133">TFTP Minimal 1.7 KB to 2.4KBFLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="33575-134">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="33575-134">Client and server support</span></span>

### <a name="ppp---polnt-to-point-protocol-ppp"></a><span data-ttu-id="33575-135">PPP</span><span class="sxs-lookup"><span data-stu-id="33575-135">PPP - Polnt-to-PoInt Protocol (PPP)</span></span>

* <span data-ttu-id="33575-136">Минимум занимаемой памяти — 7,1 КБ и 3,8 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-136">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="33575-137">Отказоустойчивость и надежность.</span><span class="sxs-lookup"><span data-stu-id="33575-137">Dependable and reliable.</span></span>

### <a name="sntp---simple-network-time-protocol-sntp"></a><span data-ttu-id="33575-138">SNTP</span><span class="sxs-lookup"><span data-stu-id="33575-138">SNTP - Simple Network Time Protocol (SNTP)</span></span>

* <span data-ttu-id="33575-139">Минимум занимаемой памяти — 4 КБ и 0,5 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="33575-139">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="33575-140">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="33575-140">Client support</span></span>

### <a name="azure-rtos-netx-api"></a><span data-ttu-id="33575-141">API NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="33575-141">Azure RTOS NetX API</span></span>

* <span data-ttu-id="33575-142">Быстрая реализация API без копирования.</span><span class="sxs-lookup"><span data-stu-id="33575-142">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="33575-143">Дополнительный уровень BSD для переноса старого кода сокетов.</span><span class="sxs-lookup"><span data-stu-id="33575-143">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp---internet-group-management-protocol-igmp"></a><span data-ttu-id="33575-144">IGMP</span><span class="sxs-lookup"><span data-stu-id="33575-144">IGMP - Internet Group Management Protocol (IGMP)</span></span>

* <span data-ttu-id="33575-145">Минимум занимаемой флэш-памяти — 2,5 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-145">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="33575-146">Поддержка групп многоадресной рассылки IPv4.</span><span class="sxs-lookup"><span data-stu-id="33575-146">IPv4 multicast group support</span></span>
* <span data-ttu-id="33575-147">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="33575-147">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="33575-148">Статистика IGMP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-148">Optional IGMP statistics</span></span>
* <span data-ttu-id="33575-149">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-149">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="udp---user-datagram-protocol-udp"></a><span data-ttu-id="33575-150">UDP</span><span class="sxs-lookup"><span data-stu-id="33575-150">UDP - User Datagram Protocol (UDP)</span></span>

* <span data-ttu-id="33575-151">Минимум занимаемой памяти — флэш-память: 2,5 КБ; ОЗУ: 124 байт на сокет.</span><span class="sxs-lookup"><span data-stu-id="33575-151">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="33575-152">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="33575-152">Fast, near wirespeed TCP packet processing:</span></span>
* <span data-ttu-id="33575-153">RX на уровне 95 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 14 %.</span><span class="sxs-lookup"><span data-stu-id="33575-153">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU Utilization</span></span>
* <span data-ttu-id="33575-154">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 10 %.</span><span class="sxs-lookup"><span data-stu-id="33575-154">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU Utilization</span></span>
* <span data-ttu-id="33575-155">Технология UDP Fast Path™.</span><span class="sxs-lookup"><span data-stu-id="33575-155">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="33575-156">Отсутствие ограничений на число UDP.</span><span class="sxs-lookup"><span data-stu-id="33575-156">No limits on the number of UDP</span></span>
* <span data-ttu-id="33575-157">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="33575-157">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="33575-158">Приостановка при получении в сокет (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-158">Optional suspension on socket receive</span></span>
* <span data-ttu-id="33575-159">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="33575-159">Optional timeout on all suspension</span></span>
* <span data-ttu-id="33575-160">Статистика UDP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-160">Optional UDP statistics</span></span>
* <span data-ttu-id="33575-161">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-161">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="tcp---transmission-control-protocol-tcp"></a><span data-ttu-id="33575-162">TCP</span><span class="sxs-lookup"><span data-stu-id="33575-162">TCP - Transmission Control Protocol (TCP)</span></span>

* <span data-ttu-id="33575-163">Минимум занимаемой памяти — флэш-память: 10,5–12,5 КБ; ОЗУ: 280 байт на сокет.</span><span class="sxs-lookup"><span data-stu-id="33575-163">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="33575-164">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="33575-164">Fast, near wlrespeed TCP packet processing:</span></span>
* <span data-ttu-id="33575-165">RX на уровне 93 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 20 %.</span><span class="sxs-lookup"><span data-stu-id="33575-165">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU Utilization</span></span>
* <span data-ttu-id="33575-166">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 27 %.</span><span class="sxs-lookup"><span data-stu-id="33575-166">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU Utilization</span></span>
* <span data-ttu-id="33575-167">Надежное подключение.</span><span class="sxs-lookup"><span data-stu-id="33575-167">Reliable connection</span></span>
* <span data-ttu-id="33575-168">Отсутствие ограничений на число TCP-сокетов.</span><span class="sxs-lookup"><span data-stu-id="33575-168">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="33575-169">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="33575-169">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="33575-170">Приостановка при получении или отправке в сокете (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-170">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="33575-171">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="33575-171">Optional timeout on all suspension</span></span>
* <span data-ttu-id="33575-172">Статистика TCP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-172">Optional TCP statistics</span></span>
* <span data-ttu-id="33575-173">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-173">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="icmp---internet-control-message-protocol-icmp"></a><span data-ttu-id="33575-174">ICMP</span><span class="sxs-lookup"><span data-stu-id="33575-174">ICMP - Internet Control Message Protocol (ICMP)</span></span>

* <span data-ttu-id="33575-175">Минимум занимаемой флэш-памяти — 2,5 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-175">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="33575-176">Поддержка IPv4.</span><span class="sxs-lookup"><span data-stu-id="33575-176">IPv4 support</span></span>
* <span data-ttu-id="33575-177">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="33575-177">IXIA IxANVL Validated</span></span>
* <span data-ttu-id="33575-178">Запрос проверки связи и ответ на нее.</span><span class="sxs-lookup"><span data-stu-id="33575-178">Ping request and ping response</span></span>
* <span data-ttu-id="33575-179">Опциональная приостановка потока при запросах проверки связи.</span><span class="sxs-lookup"><span data-stu-id="33575-179">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="33575-180">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="33575-180">Optional timeout on all suspension</span></span>
* <span data-ttu-id="33575-181">Статистика ICMP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-181">Optional ICMP statistics</span></span>
* <span data-ttu-id="33575-182">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-182">System-level Trace via Azure RTOS TraceX</span></span>

### <a name="ipv4---internet-protocol-ip"></a><span data-ttu-id="33575-183">IPv4 (IP)</span><span class="sxs-lookup"><span data-stu-id="33575-183">IPv4 - Internet Protocol (IP)</span></span>

* <span data-ttu-id="33575-184">Минимум занимаемой памяти — флэш-память: 3,5–8,5 КБ; ОЗУ: 2–3 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-184">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint.</span></span>
* <span data-ttu-id="33575-185">Архитектура Piconet™.</span><span class="sxs-lookup"><span data-stu-id="33575-185">Piconet™ Architecture.</span></span>
* <span data-ttu-id="33575-186">Высокая производительность на уровне проводной сети.</span><span class="sxs-lookup"><span data-stu-id="33575-186">Fast, near wirespeed performance.</span></span>
* <span data-ttu-id="33575-187">Поддержка нескольких интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="33575-187">Multiple interface support.</span></span>
* <span data-ttu-id="33575-188">Поддержка множественной адресации.</span><span class="sxs-lookup"><span data-stu-id="33575-188">Multi-homed support.</span></span>
* <span data-ttu-id="33575-189">Поддержка статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="33575-189">Static routing support.</span></span>
* <span data-ttu-id="33575-190">Поддержка фрагментирования и пересборки IP.</span><span class="sxs-lookup"><span data-stu-id="33575-190">IP fragmentation/reassembly support.</span></span>
* <span data-ttu-id="33575-191">Поддержка IPv4.</span><span class="sxs-lookup"><span data-stu-id="33575-191">IPv4 Support.</span></span>
* <span data-ttu-id="33575-192">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="33575-192">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="33575-193">Сертификация по программе Ready Logo Phase-2.</span><span class="sxs-lookup"><span data-stu-id="33575-193">Phase II Ready Logo Certification.</span></span>
* <span data-ttu-id="33575-194">Статистика IP (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-194">Optional IP statistics.</span></span>
* <span data-ttu-id="33575-195">Хорошо определенный, интуитивно простой интерфейс драйвера физического уровня.</span><span class="sxs-lookup"><span data-stu-id="33575-195">Well defined, intuitive physical layer driver interface.</span></span>
* <span data-ttu-id="33575-196">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-196">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="arprarp---address-resolution-protocol-arp-reverse-address-resolution-protocol-rarp"></a><span data-ttu-id="33575-197">ARP и RARP</span><span class="sxs-lookup"><span data-stu-id="33575-197">ARP/RARP - Address Resolution Protocol (ARP), Reverse Address Resolution Protocol (RARP)</span></span>

* <span data-ttu-id="33575-198">Минимум занимаемой памяти — флэш-память и ОЗУ: 1,7 КБ.</span><span class="sxs-lookup"><span data-stu-id="33575-198">Minimal 1.7 KB FLASH, RAM size.</span></span>
* <span data-ttu-id="33575-199">Динамическое разрешение 32-разрядных IPv4-адресов и 48-разрядных MAC-адресов.</span><span class="sxs-lookup"><span data-stu-id="33575-199">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses.</span></span>
* <span data-ttu-id="33575-200">Пройдена проверка IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="33575-200">IXIA IxANVL Validated.</span></span>
* <span data-ttu-id="33575-201">Гибкий кэш ARP, определяемый пользователем.</span><span class="sxs-lookup"><span data-stu-id="33575-201">Flexible, user-defined ARP cache.</span></span>
* <span data-ttu-id="33575-202">Поддержка самообращенных запросов ARP.</span><span class="sxs-lookup"><span data-stu-id="33575-202">Gratuitous ARP support.</span></span>
* <span data-ttu-id="33575-203">Статистика ARP и RARP, определяемая приложением (необязательно).</span><span class="sxs-lookup"><span data-stu-id="33575-203">Optional ARP/RARP statistics determined by application.</span></span>
* <span data-ttu-id="33575-204">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-204">System-level Trace via Azure RTOS TraceX.</span></span>

### <a name="ethernet-wifi-bluetooth-le-154-etc"></a><span data-ttu-id="33575-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4 и т. д.</span><span class="sxs-lookup"><span data-stu-id="33575-205">ETHERNET, WiFi, BLUETOOTH LE, 15.4, etc.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="33575-206">Подтвержденная совместимость</span><span class="sxs-lookup"><span data-stu-id="33575-206">Interoperability verification</span></span>

<span data-ttu-id="33575-207">NetX в ОСРВ Azure соответствует стандартам RFC и обеспечивает полную совместимость с устройствами большинства поставщиков.</span><span class="sxs-lookup"><span data-stu-id="33575-207">Azure RTOS NetX conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span> <span data-ttu-id="33575-208">Кроме того, NetX в ОСРВ Azure использует стандартную отраслевую библиотеку IxANVL для базовой реализации протокола TCP/IP в NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-208">Azure RTOS NetX also utilizes the industry standard IxANVL (Automated Network Validation Library) for the Azure RTOS NetX core TCP/IP protocol implementation.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="33575-209">Передовая технология</span><span class="sxs-lookup"><span data-stu-id="33575-209">Advanced technology</span></span>

<span data-ttu-id="33575-210">NetX в ОСРВ Azure — эта передовая технология, включающая следующее:</span><span class="sxs-lookup"><span data-stu-id="33575-210">Azure RTOS NetX is advanced technology that includes the following.</span></span>
* <span data-ttu-id="33575-211">архитектуру Piconet™;</span><span class="sxs-lookup"><span data-stu-id="33575-211">Piconet™ architecture.</span></span>
* <span data-ttu-id="33575-212">автоматическое масштабирование;</span><span class="sxs-lookup"><span data-stu-id="33575-212">Automatic scaling.</span></span>
* <span data-ttu-id="33575-213">технологию UDP Fast-Path™;</span><span class="sxs-lookup"><span data-stu-id="33575-213">UDP Fast-Path Technology™.</span></span>
* <span data-ttu-id="33575-214">гибкое управление пакетами;</span><span class="sxs-lookup"><span data-stu-id="33575-214">Flexible packet management.</span></span>
* <span data-ttu-id="33575-215">API и реализацию без копирования;</span><span class="sxs-lookup"><span data-stu-id="33575-215">Zero-copy API and implementation.</span></span>
* <span data-ttu-id="33575-216">поддержку множественной адресации;</span><span class="sxs-lookup"><span data-stu-id="33575-216">Multi-homed support.</span></span>
* <span data-ttu-id="33575-217">время ожидания при всех приостановках (необязательно);</span><span class="sxs-lookup"><span data-stu-id="33575-217">Optional timeout on all suspension.</span></span>
* <span data-ttu-id="33575-218">поддержку статической маршрутизации;</span><span class="sxs-lookup"><span data-stu-id="33575-218">Static routing support.</span></span>
* <span data-ttu-id="33575-219">поддержку системного анализа TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="33575-219">Azure RTOS TraceX system analysis support.</span></span>
