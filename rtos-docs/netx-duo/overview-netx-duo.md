---
title: Общие сведения о NetX Duo для ОСРВ Azure
description: NetX Duo в ОСРВ Azure — это расширенный сетевой стек TCP/IP промышленного класса, предназначенный специально для глубоко внедренных приложений, работающих в реальном времени, и приложений Интернета вещей.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 6112ab5cb711ca1a5c83fd5cd4b43abc0302c6c5
ms.sourcegitcommit: f9d8cf23becf96d5bd6d31dd54f89c48962fd09b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549342"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="3d063-103">Обзор NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="3d063-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="3d063-104">Сетевой стек NetX Duo для ОСРВ Azure с внедренным TCP/IP — это передовой двойной стек TCP/IP промышленного уровня с поддержкой IPv4 и IPv6 от Майкрософт, который предназначен специально для глубоко внедренных приложений, приложений Интернета вещей и приложений, работающих в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="3d063-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="3d063-105">NetX Duo предоставляет внедренным приложениям базовые сетевые протоколы, такие как IPv4, IPv6, TCP и UDP, и полный набор дополнительных подключаемых протоколов.</span><span class="sxs-lookup"><span data-stu-id="3d063-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="3d063-106">NetX Duo для ОСРВ Azure обеспечивает безопасность с помощью дополнительных подключаемых продуктов безопасности, в том числе Azure RTOS NetX Secure IPsec и Azure RTOS NetX Secure SSL, TLS, DTLS.</span><span class="sxs-lookup"><span data-stu-id="3d063-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="3d063-107">В сочетании с небольшими требованиями к ресурсам, высокой производительностью и непревзойденной простотой использования NetX Duo для ОСРВ Azure является идеальным выбором при использовании самых требовательных внедренных приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="3d063-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="3d063-108">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="3d063-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="3d063-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="3d063-109">MQTT</span></span>

* <span data-ttu-id="3d063-110">Транспортировка телеметрии очередью сообщений (MQTT).</span><span class="sxs-lookup"><span data-stu-id="3d063-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="3d063-111">Всего 2,7 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="3d063-111">Minimal 2.7 KB FLASH</span></span>

### <a name="auto-ip"></a><span data-ttu-id="3d063-112">Auto IP</span><span class="sxs-lookup"><span data-stu-id="3d063-112">Auto IP</span></span>

* <span data-ttu-id="3d063-113">Автоматическое назначение IPv4-адресов.</span><span class="sxs-lookup"><span data-stu-id="3d063-113">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="3d063-114">Всего 1,2 КБ занимаемой памяти и 300 байт в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-114">Minimal 1.2 KB, 300 bytes of RAM</span></span>

### <a name="http-https"></a><span data-ttu-id="3d063-115">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="3d063-115">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="3d063-116">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="3d063-116">HTTP 1.0</span></span>

* <span data-ttu-id="3d063-117">Протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d063-117">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="3d063-118">Всего 2,8–4,8 КБ занимаемой флэш-памяти, 0,4–1,0 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-118">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="3d063-119">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="3d063-119">Client and server support</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="3d063-120">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="3d063-120">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="3d063-121">Протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="3d063-121">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="3d063-122">Всего 3,0–9,5 КБ занимаемой флэш-памяти, 0,5–2 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-122">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="3d063-123">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="3d063-123">Client and server support</span></span>
* <span data-ttu-id="3d063-124">Поддержка нескольких входящих сеансов клиентов.</span><span class="sxs-lookup"><span data-stu-id="3d063-124">Multiple incoming client sessions</span></span>
* <span data-ttu-id="3d063-125">Поддержка передачи обычного текста и зашифрованных данных HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3d063-125">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="3d063-126">Поддержка постоянных подключений.</span><span class="sxs-lookup"><span data-stu-id="3d063-126">Persistent connection support</span></span>
* <span data-ttu-id="3d063-127">Передача составных файлов.</span><span class="sxs-lookup"><span data-stu-id="3d063-127">Multipart file upload</span></span>
* <span data-ttu-id="3d063-128">Полная интеграция с NetX Secure TLS для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-128">Fully integrated with Azure RTOS NetX Secure TLS</span></span>

### <a name="smtp"></a><span data-ttu-id="3d063-129">SMTP</span><span class="sxs-lookup"><span data-stu-id="3d063-129">SMTP</span></span>

* <span data-ttu-id="3d063-130">Протокол SMTP.</span><span class="sxs-lookup"><span data-stu-id="3d063-130">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="3d063-131">Всего 4,1 КБ занимаемой памяти и 0,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-131">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-132">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="3d063-132">Client support</span></span>

### <a name="dhcp"></a><span data-ttu-id="3d063-133">DHCP</span><span class="sxs-lookup"><span data-stu-id="3d063-133">DHCP</span></span>

* <span data-ttu-id="3d063-134">Протокол DHCP</span><span class="sxs-lookup"><span data-stu-id="3d063-134">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="3d063-135">Всего 3,6–4,6 КБ занимаемой флэш-памяти, 2,7 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-135">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-136">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="3d063-136">Client and server support</span></span>
* <span data-ttu-id="3d063-137">Поддержка IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="3d063-137">IPv4 and IPv6 support</span></span>

### <a name="nat"></a><span data-ttu-id="3d063-138">NAT</span><span class="sxs-lookup"><span data-stu-id="3d063-138">NAT</span></span>

* <span data-ttu-id="3d063-139">Преобразование сетевых адресов (NAT)</span><span class="sxs-lookup"><span data-stu-id="3d063-139">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="3d063-140">Всего 3,5 КБ занимаемой памяти и 0,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-140">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-141">Поддержка IPv4-адресов.</span><span class="sxs-lookup"><span data-stu-id="3d063-141">IPv4 address support</span></span>
* <span data-ttu-id="3d063-142">Преобразование сетевых адресов (NAT) доступно только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-142">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="3d063-143">SNMP</span><span class="sxs-lookup"><span data-stu-id="3d063-143">SNMP</span></span>

* <span data-ttu-id="3d063-144">Протокол SNMP</span><span class="sxs-lookup"><span data-stu-id="3d063-144">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="3d063-145">Всего 10,9 КБ занимаемой памяти и 2,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-145">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-146">Поддержка версий 1, 2 и 3.</span><span class="sxs-lookup"><span data-stu-id="3d063-146">Agent support for VI, V2, and V3</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="3d063-147">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="3d063-147">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="3d063-148">Служба доменных имен (DNS)</span><span class="sxs-lookup"><span data-stu-id="3d063-148">Domain Name System (DNS)</span></span>
* <span data-ttu-id="3d063-149">Многоадресная служба доменных имен (mDNS).</span><span class="sxs-lookup"><span data-stu-id="3d063-149">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="3d063-150">Обнаружение служб на основе DNS (DNS-SD).</span><span class="sxs-lookup"><span data-stu-id="3d063-150">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="3d063-151">Всего 2,4–3 КБ занимаемой флэш-памяти и 1 КБ в ОЗУ для DNS.</span><span class="sxs-lookup"><span data-stu-id="3d063-151">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-152">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="3d063-152">Client support</span></span>
* <span data-ttu-id="3d063-153">mDNS и DNS-SD доступны только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-153">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="pop3"></a><span data-ttu-id="3d063-154">POP3</span><span class="sxs-lookup"><span data-stu-id="3d063-154">POP3</span></span>

* <span data-ttu-id="3d063-155">Протокол Post Office Protocol версии 3 (POP3).</span><span class="sxs-lookup"><span data-stu-id="3d063-155">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="3d063-156">Всего 8,1 КБ занимаемой памяти и 1,4 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-156">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-157">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="3d063-157">Client support</span></span>

### <a name="telnet"></a><span data-ttu-id="3d063-158">TELNET</span><span class="sxs-lookup"><span data-stu-id="3d063-158">TELNET</span></span>

* <span data-ttu-id="3d063-159">Всего 0,5 КБ занимаемой памяти и 0,3 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-159">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-160">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="3d063-160">Client and server support</span></span>
* <span data-ttu-id="3d063-161">Интуитивно простые API Telnet: *nx_telnet_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-161">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="3d063-162">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="3d063-162">FTP, TFTP</span></span>

* <span data-ttu-id="3d063-163">Протокол FTP.</span><span class="sxs-lookup"><span data-stu-id="3d063-163">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="3d063-164">Протокол TFTP</span><span class="sxs-lookup"><span data-stu-id="3d063-164">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="3d063-165">Всего 1,8–7,2 КБ занимаемой флэш-памяти и 0,6–2,1 КБ в ОЗУ для FTP.</span><span class="sxs-lookup"><span data-stu-id="3d063-165">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-166">Всего 1,7–2,4 КБ занимаемой флэш-памяти и 0,3–1,8 КБ в ОЗУ для TFTP.</span><span class="sxs-lookup"><span data-stu-id="3d063-166">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-167">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="3d063-167">Client and server support</span></span>
* <span data-ttu-id="3d063-168">Интуитивно простые API FTP и TFTP: *nx_ftp_\** или *nx_tftp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-168">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="3d063-169">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="3d063-169">PPP, PPPoE</span></span>

* <span data-ttu-id="3d063-170">Протокол PPP.</span><span class="sxs-lookup"><span data-stu-id="3d063-170">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="3d063-171">Протокол PPPoE.</span><span class="sxs-lookup"><span data-stu-id="3d063-171">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="3d063-172">Всего 7,1 КБ занимаемой памяти и 3,8 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-172">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-173">Интуитивно простые API PPP: *nx_ppp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-173">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="3d063-174">PPPoE доступен только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-174">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="3d063-175">SNTP</span><span class="sxs-lookup"><span data-stu-id="3d063-175">SNTP</span></span>

* <span data-ttu-id="3d063-176">Простой протокол синхронизации времени по сети (SNTP).</span><span class="sxs-lookup"><span data-stu-id="3d063-176">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="3d063-177">Всего 4 КБ занимаемой памяти и 0,5 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-177">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="3d063-178">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="3d063-178">Client support</span></span>
* <span data-ttu-id="3d063-179">Интуитивно простые API SNTP: *nx_sntp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-179">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="3d063-180">API NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="3d063-180">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="3d063-181">Интуитивно простой и согласованный API.</span><span class="sxs-lookup"><span data-stu-id="3d063-181">Intuitive and consistent API</span></span>
* <span data-ttu-id="3d063-182">Соглашение об именовании с использованием конструкций "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="3d063-182">Noun-verb naming convention</span></span>
* <span data-ttu-id="3d063-183">Быстрая реализация API без копирования.</span><span class="sxs-lookup"><span data-stu-id="3d063-183">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="3d063-184">Все API имеют префикс <i>nx_\*</i> для простой идентификации принадлежности к NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-184">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="3d063-185">Блокирующие API поддерживают опциональное время ожидания потоков.</span><span class="sxs-lookup"><span data-stu-id="3d063-185">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="3d063-186">Дополнительные сведения см. в статье [Руководство пользователя по NetX Duo в ОСРВ Azure](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="3d063-186">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="3d063-187">Опциональный уровень BSD для портирования старого кода сокетов.</span><span class="sxs-lookup"><span data-stu-id="3d063-187">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="3d063-188">IGMP</span><span class="sxs-lookup"><span data-stu-id="3d063-188">IGMP</span></span>

* <span data-ttu-id="3d063-189">протокол управления группами Интернета (IGMP)</span><span class="sxs-lookup"><span data-stu-id="3d063-189">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="3d063-190">Всего 2,5 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="3d063-190">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3d063-191">Поддержка групп многоадресной рассылки IPv4.</span><span class="sxs-lookup"><span data-stu-id="3d063-191">IPv4 multicast group support</span></span>
* <span data-ttu-id="3d063-192">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="3d063-192">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3d063-193">Опциональная статистика IGMP.</span><span class="sxs-lookup"><span data-stu-id="3d063-193">Optional IGMP statistics</span></span>
* <span data-ttu-id="3d063-194">Трассировка на уровне системы через ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="3d063-194">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="3d063-195">Интуитивно простые API IGMP: *nx_igmp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-195">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="3d063-196">NetX Secure DTLS для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="3d063-196">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="3d063-197">Протокол датаграмм безопасности транспортного уровня (DTLS) версий 1.0 и 1.2.</span><span class="sxs-lookup"><span data-stu-id="3d063-197">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="3d063-198">Всего 11 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="3d063-198">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="3d063-199">Быстрое программное шифрование RSA с 2048-битным ключом занимает около 1 секунды при частоте @120MHz.</span><span class="sxs-lookup"><span data-stu-id="3d063-199">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="3d063-200">Оптимизированная реализация X.509.</span><span class="sxs-lookup"><span data-stu-id="3d063-200">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="3d063-201">Полная интеграция с сокетами UDP в NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-201">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="3d063-202">Поддержка аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d063-202">Hardware Crypto Support</span></span>
* <span data-ttu-id="3d063-203">Поддержка программного шифрования: RSA (с ключами любого размера), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512).</span><span class="sxs-lookup"><span data-stu-id="3d063-203">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="3d063-204">Шифрование на основе эллиптических кривых (ECC) с ECDSA (подписывание) и ECDH (шифрование), в том числе с P-кривыми с разрядностью в 192, 224, 256, 384 и 521 бит.</span><span class="sxs-lookup"><span data-stu-id="3d063-204">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="3d063-205">Поддержка зашифрованных ключей (зависит от оборудования).</span><span class="sxs-lookup"><span data-stu-id="3d063-205">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="3d063-206">NetX Secure TLS для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="3d063-206">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="3d063-207">Протокол TLS версий 1.0, 1.1 и 1.2.</span><span class="sxs-lookup"><span data-stu-id="3d063-207">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="3d063-208">Всего 8,8 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="3d063-208">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="3d063-209">Быстрое программное шифрование RSA с 2048-битным ключом занимает около 1 секунды при частоте @120MHz.</span><span class="sxs-lookup"><span data-stu-id="3d063-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="3d063-210">Оптимизированная реализация X.509.</span><span class="sxs-lookup"><span data-stu-id="3d063-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="3d063-211">Полная интеграция с сокетами TCP в NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-211">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="3d063-212">Поддержка аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d063-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="3d063-213">Поддержка программного шифрования: RSA (с ключами любого размера), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512).</span><span class="sxs-lookup"><span data-stu-id="3d063-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="3d063-214">Шифрование на основе эллиптических кривых (ECC) с ECDSA (подписывание) и ECDH (шифрование), в том числе с P-кривыми с разрядностью в 192, 224, 256, 384 и 521 бит.</span><span class="sxs-lookup"><span data-stu-id="3d063-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="3d063-215">Поддержка зашифрованных ключей (зависит от оборудования).</span><span class="sxs-lookup"><span data-stu-id="3d063-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="3d063-216">ICMP</span><span class="sxs-lookup"><span data-stu-id="3d063-216">ICMP</span></span>

* <span data-ttu-id="3d063-217">Протокол межсетевых управляющих сообщений (ICMP).</span><span class="sxs-lookup"><span data-stu-id="3d063-217">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="3d063-218">Всего 2,5 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="3d063-218">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="3d063-219">Поддержка IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="3d063-219">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="3d063-220">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="3d063-220">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3d063-221">Запрос проверки связи и ответ на нее.</span><span class="sxs-lookup"><span data-stu-id="3d063-221">Ping request and ping response</span></span>
* <span data-ttu-id="3d063-222">Опциональная приостановка потока при запросах проверки связи.</span><span class="sxs-lookup"><span data-stu-id="3d063-222">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="3d063-223">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="3d063-223">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3d063-224">Опциональная статистика ICMP.</span><span class="sxs-lookup"><span data-stu-id="3d063-224">Optional ICMP statistics</span></span>
* <span data-ttu-id="3d063-225">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-225">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3d063-226">Интуитивно простые API ICMP: *nx_icmp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-226">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="3d063-227">UDP</span><span class="sxs-lookup"><span data-stu-id="3d063-227">UDP</span></span>

* <span data-ttu-id="3d063-228">Протокол UDP.</span><span class="sxs-lookup"><span data-stu-id="3d063-228">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="3d063-229">Всего 2,5 КБ занимаемой флэш-памяти, 124 байт в ОЗУ на сокет.</span><span class="sxs-lookup"><span data-stu-id="3d063-229">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="3d063-230">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="3d063-230">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="3d063-231">RX на уровне 95 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 14 %.</span><span class="sxs-lookup"><span data-stu-id="3d063-231">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="3d063-232">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 10 %.</span><span class="sxs-lookup"><span data-stu-id="3d063-232">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="3d063-233">Технология UDP Fast Path™.</span><span class="sxs-lookup"><span data-stu-id="3d063-233">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="3d063-234">Отсутствие ограничений на число UDP.</span><span class="sxs-lookup"><span data-stu-id="3d063-234">No limits on the number of UDP</span></span>
* <span data-ttu-id="3d063-235">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="3d063-235">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3d063-236">Опциональная приостановка при получении на сокет.</span><span class="sxs-lookup"><span data-stu-id="3d063-236">Optional suspension on socket receive</span></span>
* <span data-ttu-id="3d063-237">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="3d063-237">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3d063-238">Опциональная статистика UDP.</span><span class="sxs-lookup"><span data-stu-id="3d063-238">Optional UDP statistics</span></span>
* <span data-ttu-id="3d063-239">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-239">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3d063-240">Интуитивно простые API UDP: *nx_udp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-240">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="3d063-241">TCP</span><span class="sxs-lookup"><span data-stu-id="3d063-241">TCP</span></span>

* <span data-ttu-id="3d063-242">Протокол TCP.</span><span class="sxs-lookup"><span data-stu-id="3d063-242">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="3d063-243">Всего 10,5–12,5 КБ занимаемой флэш-памяти, 280 байт в ОЗУ на сокет.</span><span class="sxs-lookup"><span data-stu-id="3d063-243">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="3d063-244">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="3d063-244">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="3d063-245">RX на уровне 93 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 20 %.</span><span class="sxs-lookup"><span data-stu-id="3d063-245">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="3d063-246">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 27 %.</span><span class="sxs-lookup"><span data-stu-id="3d063-246">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="3d063-247">Надежное подключение.</span><span class="sxs-lookup"><span data-stu-id="3d063-247">Reliable connection</span></span>
* <span data-ttu-id="3d063-248">Отсутствие ограничений на число TCP-сокетов.</span><span class="sxs-lookup"><span data-stu-id="3d063-248">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="3d063-249">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="3d063-249">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3d063-250">Опциональная приостановка при получении или отправке на сокете.</span><span class="sxs-lookup"><span data-stu-id="3d063-250">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="3d063-251">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="3d063-251">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3d063-252">Опциональная статистика TCP.</span><span class="sxs-lookup"><span data-stu-id="3d063-252">Optional TCP statistics</span></span>
* <span data-ttu-id="3d063-253">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-253">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3d063-254">Интуитивно простые API TCP: *nx_tcp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-254">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="3d063-255">ARP и RARP</span><span class="sxs-lookup"><span data-stu-id="3d063-255">ARP/RARP</span></span>

* <span data-ttu-id="3d063-256">Протокол разрешения адресов (ARP).</span><span class="sxs-lookup"><span data-stu-id="3d063-256">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="3d063-257">Обратный протокол разрешения адресов (RARP)</span><span class="sxs-lookup"><span data-stu-id="3d063-257">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="3d063-258">Всего 1,7 КБ занимаемой флэш-памяти и ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-258">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="3d063-259">Динамическое разрешение 32-разрядных IPv4-адресов и 48-разрядных MAC-адресов.</span><span class="sxs-lookup"><span data-stu-id="3d063-259">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="3d063-260">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="3d063-260">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3d063-261">Гибкий кэш ARP, определяемый пользователем.</span><span class="sxs-lookup"><span data-stu-id="3d063-261">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="3d063-262">Поддержка самообращенных запросов ARP.</span><span class="sxs-lookup"><span data-stu-id="3d063-262">Gratuitous ARP support</span></span>
* <span data-ttu-id="3d063-263">Опциональная статистика ARP и RARP, определяемая приложением.</span><span class="sxs-lookup"><span data-stu-id="3d063-263">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="3d063-264">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-264">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3d063-265">Интуитивно простые API ARP и RARP: *nx_arp_\** , *nx_rarp_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-265">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="3d063-266">IPv4 и IPv6</span><span class="sxs-lookup"><span data-stu-id="3d063-266">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="3d063-267">Протокол IP.</span><span class="sxs-lookup"><span data-stu-id="3d063-267">Internet Protocol (IP)</span></span>
* <span data-ttu-id="3d063-268">Всего 3,5–8,5 КБ занимаемой флэш-памяти, 2–3 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="3d063-268">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="3d063-269">Архитектура Piconet™.</span><span class="sxs-lookup"><span data-stu-id="3d063-269">Piconet™ architecture</span></span>
* <span data-ttu-id="3d063-270">Высокая производительность на уровне проводной сети.</span><span class="sxs-lookup"><span data-stu-id="3d063-270">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="3d063-271">Поддержка нескольких интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="3d063-271">Multiple interface support</span></span>
* <span data-ttu-id="3d063-272">Поддержка многосетевых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="3d063-272">Multihomed support</span></span>
* <span data-ttu-id="3d063-273">Поддержка статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="3d063-273">Static routing support</span></span>
* <span data-ttu-id="3d063-274">Поддержка фрагментирования и повторной сборки пакетов IP.</span><span class="sxs-lookup"><span data-stu-id="3d063-274">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="3d063-275">Поддержка IPv4- и IPv6-адресов.</span><span class="sxs-lookup"><span data-stu-id="3d063-275">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="3d063-276">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="3d063-276">IXIA IxANVL validated</span></span>
* <span data-ttu-id="3d063-277">Сертификация по программе IPv6 Ready Logo Phase-2</span><span class="sxs-lookup"><span data-stu-id="3d063-277">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="3d063-278">Опциональная статистика IP.</span><span class="sxs-lookup"><span data-stu-id="3d063-278">Optional IP statistics</span></span>
* <span data-ttu-id="3d063-279">Хорошо определенный, интуитивно простой интерфейс драйвера физического уровня.</span><span class="sxs-lookup"><span data-stu-id="3d063-279">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="3d063-280">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-280">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="3d063-281">Интуитивно простые API уровня IP: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-281">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="3d063-282">Предварительная сертификация TUV и UL на соответствие стандартам IEC 61508 SIL 4, IEC 62304 (класс C), ISO 26262 ASIL D и EN 50128 SW-SIL4.</span><span class="sxs-lookup"><span data-stu-id="3d063-282">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="3d063-283">Надежный протокол IPsec в NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="3d063-283">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="3d063-284">IPsec.</span><span class="sxs-lookup"><span data-stu-id="3d063-284">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="3d063-285">Уровень IP.</span><span class="sxs-lookup"><span data-stu-id="3d063-285">IP layer</span></span>
* <span data-ttu-id="3d063-286">Поддержка аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d063-286">Hardware crypto support</span></span>
* <span data-ttu-id="3d063-287">Поддержка программного шифрования, в том числе следующего:</span><span class="sxs-lookup"><span data-stu-id="3d063-287">Software crypto support, including:</span></span>
    * <span data-ttu-id="3d063-288">DES, 3DES;</span><span class="sxs-lookup"><span data-stu-id="3d063-288">DES, 3DES</span></span>
    * <span data-ttu-id="3d063-289">AES</span><span class="sxs-lookup"><span data-stu-id="3d063-289">AES</span></span>
    * <span data-ttu-id="3d063-290">HMAC-MD5;</span><span class="sxs-lookup"><span data-stu-id="3d063-290">HMAC-MD5</span></span>
    * <span data-ttu-id="3d063-291">HMAC-SHA1.</span><span class="sxs-lookup"><span data-stu-id="3d063-291">HMAC-SHA1</span></span>
* <span data-ttu-id="3d063-292">Поддержка протокола IKE версии 2.</span><span class="sxs-lookup"><span data-stu-id="3d063-292">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="3d063-293">Интуитивно простые API IPsec: *nx_ipsec_\** .</span><span class="sxs-lookup"><span data-stu-id="3d063-293">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="3d063-294">IPsec доступен только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-294">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="3d063-295">Безопасность и защищенность</span><span class="sxs-lookup"><span data-stu-id="3d063-295">Safe and secure</span></span>

<span data-ttu-id="3d063-296">Стек NetX Duo для ОСРВ Azure защищен.</span><span class="sxs-lookup"><span data-stu-id="3d063-296">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="3d063-297">Его безопасность обеспечивается с помощью подключаемых продуктов безопасности, в числе которых IPsec, SSL, TLS и DTLS.</span><span class="sxs-lookup"><span data-stu-id="3d063-297">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="3d063-298">Кроме того, приложение полностью управляет всем внешним доступом к NetX Duo для ОСРВ Azure, что значительно упрощает определение рисков безопасности.</span><span class="sxs-lookup"><span data-stu-id="3d063-298">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="3d063-299">ОСРВ Azure от Майкрософт предоставляет изготовителям оборудования компоненты для безопасного обмена данными, а также создания кода и изоляции данных с помощью базовых аппаратных механизмов защиты, встроенных в микроконтроллеры и микропроцессоры.</span><span class="sxs-lookup"><span data-stu-id="3d063-299">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="3d063-300">Ответственность за полное соответствие устройства меняющимся требованиям к безопасности в отношении отдельных вариантов использования в конечном итоге лежит на производителе устройства.</span><span class="sxs-lookup"><span data-stu-id="3d063-300">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>


## <a name="interoperability-verification"></a><span data-ttu-id="3d063-301">Подтвержденная совместимость</span><span class="sxs-lookup"><span data-stu-id="3d063-301">Interoperability verification</span></span>

<span data-ttu-id="3d063-302">NetX Duo соответствует стандартам RFC и обеспечивает полную совместимость с устройствами большинства поставщиков.</span><span class="sxs-lookup"><span data-stu-id="3d063-302">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Логотип IPv6 Ready](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="3d063-304">NetX Duo для ОСРВ Azure — это единственный стек с внедренными протоколами TCP/IP, соответствующий строгим требованиям сертификации IPv6-Ready Logo. То есть он прошел все проверки на согласованность и совместимость, принятые и утвержденные организацией IPv6 Forum.</span><span class="sxs-lookup"><span data-stu-id="3d063-304">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="3d063-305">NetX Duo также использует стандартную отраслевую библиотеку IxANVL для базовой реализации протокола TCP/IP в NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3d063-305">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="3d063-306">Комплексное решение Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="3d063-306">Comprehensive IoT solution</span></span>

<span data-ttu-id="3d063-307">NetX Duo предоставляет один из самых комплексных наборов сетевых функций с поддержкой TCP/IP для глубоко внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="3d063-307">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="3d063-308">Такая поддержка включает следующие подключаемые протоколы:</span><span class="sxs-lookup"><span data-stu-id="3d063-308">This support includes the following add-on protocol products.</span></span>

<span data-ttu-id="3d063-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP версии 1, 2 и 3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="3d063-309">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="3d063-310">Передовая технология</span><span class="sxs-lookup"><span data-stu-id="3d063-310">Advanced technology</span></span>

<span data-ttu-id="3d063-311">NetX Duo для ОСРВ Azure — эта передовая технология, включающая следующее:</span><span class="sxs-lookup"><span data-stu-id="3d063-311">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="3d063-312">архитектура Piconet™;</span><span class="sxs-lookup"><span data-stu-id="3d063-312">Piconet™ architecture</span></span>
* <span data-ttu-id="3d063-313">Автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="3d063-313">Automatic scaling</span></span>
* <span data-ttu-id="3d063-314">технология UDP Fast-Path™;</span><span class="sxs-lookup"><span data-stu-id="3d063-314">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="3d063-315">гибкое управление пакетами;</span><span class="sxs-lookup"><span data-stu-id="3d063-315">Flexible packet management</span></span>
* <span data-ttu-id="3d063-316">API и реализация без копирования;</span><span class="sxs-lookup"><span data-stu-id="3d063-316">Zero-copy API and implementation</span></span>
* <span data-ttu-id="3d063-317">поддержка многосетевых интерфейсов;</span><span class="sxs-lookup"><span data-stu-id="3d063-317">Multihomed support</span></span>
* <span data-ttu-id="3d063-318">опциональное время ожидания при всех приостановках;</span><span class="sxs-lookup"><span data-stu-id="3d063-318">Optional timeout on all suspension</span></span>
* <span data-ttu-id="3d063-319">поддержка статической маршрутизации;</span><span class="sxs-lookup"><span data-stu-id="3d063-319">Static routing support</span></span>
* <span data-ttu-id="3d063-320">IPsec</span><span class="sxs-lookup"><span data-stu-id="3d063-320">IPsec</span></span>
* <span data-ttu-id="3d063-321">SSL, TLS и DTLS;</span><span class="sxs-lookup"><span data-stu-id="3d063-321">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="3d063-322">поддержка системного анализа TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-322">Azure RTOS TraceX system analysis support</span></span>

## <a name="related-services"></a><span data-ttu-id="3d063-323">Связанные службы</span><span class="sxs-lookup"><span data-stu-id="3d063-323">Related services</span></span>

### <a name="azure-iot"></a><span data-ttu-id="3d063-324">Azure IoT</span><span class="sxs-lookup"><span data-stu-id="3d063-324">Azure IoT</span></span>

<span data-ttu-id="3d063-325">NetX Duo включает [ПО промежуточного слоя Интернета вещей Azure для ОСРВ Azure](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), библиотеку для конкретной платформы, которая выступает в качестве уровня привязки между ОСРВ Azure и пакетом SDK Azure для Embedded C для упрощения подключения к службам Интернета вещей Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-325">NetX Duo includes [Azure IoT Middleware for Azure RTOS](https://github.com/azure-rtos/netxduo/blob/master/addons/azure_iot/docs/README.md), a platform-specific library that acts as a binding layer between the Azure RTOS and the Azure SDK for Embedded C to facilitate connectivity to Azure IoT services.</span></span> <span data-ttu-id="3d063-326">Ниже указаны задачи ПО промежуточного слоя Интернета вещей Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-326">The goals of Azure IoT Middleware are the following.</span></span>
* <span data-ttu-id="3d063-327">Предоставьте интерфейсы интеллектуальных клиентов (IoTHub_Client, DeviceProvisioning_Client), требуемые разработчикам для приложений.</span><span class="sxs-lookup"><span data-stu-id="3d063-327">Provide the smart client interfaces (IoTHub_Client, DeviceProvisioning_Client) that developers need for their applications.</span></span>
* <span data-ttu-id="3d063-328">Управляйте взаимодействием между пакетом SDK для Embedded C и платформой.</span><span class="sxs-lookup"><span data-stu-id="3d063-328">Orchestrate the interaction between the Embedded C SDK and the platform.</span></span>
* <span data-ttu-id="3d063-329">Настройте инициализацию платформы ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-329">Provide Azure RTOS platform initialization.</span></span>
* <span data-ttu-id="3d063-330">Поддержка IoT Plug and Play.</span><span class="sxs-lookup"><span data-stu-id="3d063-330">IoT Plug and Play support.</span></span>
* <span data-ttu-id="3d063-331">Возможности системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="3d063-331">Security capabilities.</span></span>
* <span data-ttu-id="3d063-332">Учитывается ограничение ресурсов.</span><span class="sxs-lookup"><span data-stu-id="3d063-332">Resource limitation aware.</span></span>
* <span data-ttu-id="3d063-333">Поддержка протоколов.</span><span class="sxs-lookup"><span data-stu-id="3d063-333">Protocol support.</span></span>

![Связанные службы NetX Duo ОСРВ Azure](./media/overview-netx-duo/related-services.png)

### <a name="azure-defender"></a><span data-ttu-id="3d063-335">Azure Defender</span><span class="sxs-lookup"><span data-stu-id="3d063-335">Azure Defender</span></span>

<span data-ttu-id="3d063-336">Модуль безопасности Azure Defender для Интернета вещей предоставляет комплексное решение для защиты устройств ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-336">The Azure Defender for IoT security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="3d063-337">Модуль безопасности для ОСРВ Azure позволяет обнаруживать вредоносные действия в сети, настраивать базовое поведение устройств с учетом оповещений и помогает повысить уровень безопасности устройства.</span><span class="sxs-lookup"><span data-stu-id="3d063-337">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="3d063-338">Узнайте больше о [модуле безопасности для ОСРВ Azure](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) или изучите краткое руководство по [настройке модуля безопасности для ОСРВ Azure](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module).</span><span class="sxs-lookup"><span data-stu-id="3d063-338">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

### <a name="device-update-for-iot-hub"></a><span data-ttu-id="3d063-339">Обновление устройств для Центра Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="3d063-339">Device Update for IoT Hub</span></span>

<span data-ttu-id="3d063-340">[Обновление устройств для Центра Интернета вещей Azure](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) — это служба, которая позволяет развертывать обновления на устройствах Интернета вещей по беспроводной сети.</span><span class="sxs-lookup"><span data-stu-id="3d063-340">The [Azure Device Update for IoT Hub](https://docs.microsoft.com/azure/iot-hub-device-update/understand-device-update) is a service that enables you to deploy over-the-air updates (OTA) for your IoT devices.</span></span> <span data-ttu-id="3d063-341">Модуль Обновления устройств для Центра Интернета вещей — это реализация обновления устройства для агента Центра Интернета вещей в NetX Duo ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="3d063-341">The Device Update for IoT Hub module is the implementation of Device Update for IoT Hub Agent in Azure RTOS NetX Duo.</span></span> <span data-ttu-id="3d063-342">Здесь представлены простые API для разработчиков устройств, позволяющие интегрировать возможности Обновления устройств в приложения.</span><span class="sxs-lookup"><span data-stu-id="3d063-342">It provides simple APIs for device builders to integrate the Device Update capability in their application.</span></span>

<span data-ttu-id="3d063-343">Просмотрите примеры основных макетов полупроводниковых плат, которые включают руководства по началу работы с инструкциями по настройке, созданию и развертыванию обновлений для устройств по беспроводной сети.</span><span class="sxs-lookup"><span data-stu-id="3d063-343">See the samples of key semiconductors evaluation boards that include the get started guides to learn configure, build and deploy the over-the-air (OTA) updates to the devices.</span></span>

<span data-ttu-id="3d063-344">Вы также можете получить дополнительные сведения о работе с [Обновлением устройств для Центра Интернета вещей с использованием ОСРВ Azure](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span><span class="sxs-lookup"><span data-stu-id="3d063-344">And you can learn more details about use [Device Update for IoT Hub with Azure RTOS](https://docs.microsoft.com/azure/iot-hub-device-update/device-update-azure-real-time-operating-system).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3d063-345">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="3d063-345">Next steps</span></span>

<span data-ttu-id="3d063-346">Чтобы узнать больше о NetX Duo, ознакомьтесь со статьей [Руководство пользователя по NetX Duo для ОСРВ Azure](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="3d063-346">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
