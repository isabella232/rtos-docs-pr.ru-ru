---
title: Общие сведения о NetX Duo для ОСРВ Azure
description: NetX Duo в ОСРВ Azure — это расширенный сетевой стек TCP/IP промышленного класса, предназначенный специально для глубоко внедренных приложений, работающих в реальном времени, и приложений Интернета вещей.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 2339da391e52b437a2111ae439cccf41e038bdcf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815336"
---
# <a name="overview-of-azure-rtos-netx-duo"></a><span data-ttu-id="fff1c-103">Обзор NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fff1c-103">Overview of Azure RTOS NetX Duo</span></span>

<span data-ttu-id="fff1c-104">Сетевой стек NetX Duo для ОСРВ Azure с внедренным TCP/IP — это передовой двойной стек TCP/IP промышленного уровня с поддержкой IPv4 и IPv6 от Майкрософт, который предназначен специально для глубоко внедренных приложений, приложений Интернета вещей и приложений, работающих в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="fff1c-104">Azure RTOS NetX Duo embedded TCP/IP network stack is Microsoft's advanced, industrial grade dual IPv4 and IPv6 TCP/IP network stack that is designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="fff1c-105">NetX Duo предоставляет внедренным приложениям базовые сетевые протоколы, такие как IPv4, IPv6, TCP и UDP, и полный набор дополнительных подключаемых протоколов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-105">NetX Duo provides embedded applications with core network protocols such as IPv4, IPv6, TCP, and UDP as well as a complete suite of additional, higher-level add-on protocols.</span></span> <span data-ttu-id="fff1c-106">NetX Duo для ОСРВ Azure обеспечивает безопасность с помощью дополнительных подключаемых продуктов безопасности, в том числе Azure RTOS NetX Secure IPsec и Azure RTOS NetX Secure SSL, TLS, DTLS.</span><span class="sxs-lookup"><span data-stu-id="fff1c-106">Azure RTOS NetX Duo offers security via additional add-on security products, including Azure RTOS NetX Secure IPsec and Azure RTOS NetX Secure SSL/TLS/DTLS.</span></span> <span data-ttu-id="fff1c-107">В сочетании с небольшими требованиями к ресурсам, высокой производительностью и непревзойденной простотой использования NetX Duo для ОСРВ Azure является идеальным выбором при использовании самых требовательных внедренных приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="fff1c-107">All of this combined with an small footprint, fast execution, and superior ease-of-use make Azure RTOS NetX Duo the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="fff1c-108">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="fff1c-108">API protocols</span></span>

### <a name="mqtt"></a><span data-ttu-id="fff1c-109">MQTT</span><span class="sxs-lookup"><span data-stu-id="fff1c-109">MQTT</span></span>

* <span data-ttu-id="fff1c-110">Транспортировка телеметрии очередью сообщений (MQTT).</span><span class="sxs-lookup"><span data-stu-id="fff1c-110">Messaging Queue Telemetry Transport (MQTT)</span></span>
* <span data-ttu-id="fff1c-111">Всего 2,7 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="fff1c-111">Minimal 2.7 KB FLASH</span></span>
* <span data-ttu-id="fff1c-112">Интуитивно простые API MQTT: *nx_mqtt_* \*.</span><span class="sxs-lookup"><span data-stu-id="fff1c-112">Intuitive MQTT APIs: *nx_mqtt_*\*</span></span>

### <a name="auto-ip"></a><span data-ttu-id="fff1c-113">Auto IP</span><span class="sxs-lookup"><span data-stu-id="fff1c-113">Auto IP</span></span>

* <span data-ttu-id="fff1c-114">Автоматическое назначение IPv4-адресов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-114">Automatic IPv4 address assignment</span></span>
* <span data-ttu-id="fff1c-115">Всего 1,2 КБ занимаемой памяти и 300 байт в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-115">Minimal 1.2 KB, 300 bytes of RAM</span></span>
* <span data-ttu-id="fff1c-116">Интуитивно простые API AutoIP: *nx_autoip_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-116">Intuitive AutoIP APIs: *nx_autoip_\**</span></span>

### <a name="http-https"></a><span data-ttu-id="fff1c-117">HTTP, HTTPS</span><span class="sxs-lookup"><span data-stu-id="fff1c-117">HTTP, HTTPS</span></span>

#### <a name="http-10"></a><span data-ttu-id="fff1c-118">HTTP 1.0</span><span class="sxs-lookup"><span data-stu-id="fff1c-118">HTTP 1.0</span></span>

* <span data-ttu-id="fff1c-119">Протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-119">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="fff1c-120">Всего 2,8–4,8 КБ занимаемой флэш-памяти, 0,4–1,0 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-120">Minimal 2.8 KB to 4.8 KB FLASH / 0.4 KB to 1.0 KB RAM</span></span>
* <span data-ttu-id="fff1c-121">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-121">Client and server support</span></span>
* <span data-ttu-id="fff1c-122">Интуитивно простые API: *nx_http_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-122">Intuitive APIs: *nx_http_\**</span></span>

#### <a name="httphttps-11"></a><span data-ttu-id="fff1c-123">HTTP/HTTPS 1.1</span><span class="sxs-lookup"><span data-stu-id="fff1c-123">HTTP/HTTPS 1.1</span></span>

* <span data-ttu-id="fff1c-124">Протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-124">Hypertext Transfer Protocol(HTTP)</span></span>
* <span data-ttu-id="fff1c-125">Всего 3,0–9,5 КБ занимаемой флэш-памяти, 0,5–2 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-125">Minimal 3.0 KB to 9.5 KB FLASH / 0.5 KB to 2 KB RAM</span></span>
* <span data-ttu-id="fff1c-126">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-126">Client and server support</span></span>
* <span data-ttu-id="fff1c-127">Поддержка нескольких входящих сеансов клиентов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-127">Multiple incoming client sessions</span></span>
* <span data-ttu-id="fff1c-128">Поддержка передачи обычного текста и зашифрованных данных HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fff1c-128">Plain text and encrypted HTTPS</span></span>
* <span data-ttu-id="fff1c-129">Поддержка постоянных подключений.</span><span class="sxs-lookup"><span data-stu-id="fff1c-129">Persistent connection support</span></span>
* <span data-ttu-id="fff1c-130">Передача составных файлов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-130">Multipart file upload</span></span>
* <span data-ttu-id="fff1c-131">Полная интеграция с NetX Secure TLS для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-131">Fully integrated with Azure RTOS NetX Secure TLS</span></span>
* <span data-ttu-id="fff1c-132">Интуитивно простые API: *nx_web_http\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-132">Intuitive APIs: *nx_web_http\**</span></span>

### <a name="smtp"></a><span data-ttu-id="fff1c-133">SMTP</span><span class="sxs-lookup"><span data-stu-id="fff1c-133">SMTP</span></span>

* <span data-ttu-id="fff1c-134">Протокол SMTP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-134">Simple Mall Transfer Protocol (SMTP)</span></span>
* <span data-ttu-id="fff1c-135">Всего 4,1 КБ занимаемой памяти и 0,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-135">Minimal 4.1 KB and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-136">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-136">Client support</span></span>
* <span data-ttu-id="fff1c-137">Интуитивно простые API SMTP: *nx_smtp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-137">Intuitive SMTP APIs: *nx_smtp_\**</span></span>

### <a name="dhcp"></a><span data-ttu-id="fff1c-138">DHCP</span><span class="sxs-lookup"><span data-stu-id="fff1c-138">DHCP</span></span>

* <span data-ttu-id="fff1c-139">Протокол DHCP</span><span class="sxs-lookup"><span data-stu-id="fff1c-139">Dynamic Host Configuration Protocol (DHCP)</span></span>
* <span data-ttu-id="fff1c-140">Всего 3,6–4,6 КБ занимаемой флэш-памяти, 2,7 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-140">Minimal 3.6 KB to 4.6 KB FLASH, 2.7 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-141">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-141">Client and server support</span></span>
* <span data-ttu-id="fff1c-142">Поддержка IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="fff1c-142">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="fff1c-143">Интуитивно простые API DHCP: *nx_dhcp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-143">Intuitive DHCP APIs: *nx_dhcp_\**</span></span>

### <a name="nat"></a><span data-ttu-id="fff1c-144">NAT</span><span class="sxs-lookup"><span data-stu-id="fff1c-144">NAT</span></span>

* <span data-ttu-id="fff1c-145">Преобразование сетевых адресов (NAT)</span><span class="sxs-lookup"><span data-stu-id="fff1c-145">Network Address Translation (NAT)</span></span>
* <span data-ttu-id="fff1c-146">Всего 3,5 КБ занимаемой памяти и 0,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-146">Minimal 3.5K6 and 0.6 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-147">Поддержка IPv4-адресов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-147">IPv4 address support</span></span>
* <span data-ttu-id="fff1c-148">Интуитивно простые API NAT: *nx_nat_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-148">Intuitive NAT APIs: *nx_nat_\**</span></span>
* <span data-ttu-id="fff1c-149">Преобразование сетевых адресов (NAT) доступно только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-149">NAT is only available with Azure RTOS NetX Duo</span></span>

### <a name="snmp"></a><span data-ttu-id="fff1c-150">SNMP</span><span class="sxs-lookup"><span data-stu-id="fff1c-150">SNMP</span></span>

* <span data-ttu-id="fff1c-151">Протокол SNMP</span><span class="sxs-lookup"><span data-stu-id="fff1c-151">Simple Network Management Protocol (SNMP)</span></span>
* <span data-ttu-id="fff1c-152">Всего 10,9 КБ занимаемой памяти и 2,6 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-152">Minimal 10.9 KB and 2.6 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-153">Поддержка версий 1, 2 и 3.</span><span class="sxs-lookup"><span data-stu-id="fff1c-153">Agent support for VI, V2, and V3</span></span>
* <span data-ttu-id="fff1c-154">Интуитивно простые API SNMP: *nx_snmp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-154">Intuitive SNMP APIs: *nx_snmp_\**</span></span>

### <a name="dns-mdns-dns-sd"></a><span data-ttu-id="fff1c-155">DNS, mDNS, DNS-SD</span><span class="sxs-lookup"><span data-stu-id="fff1c-155">DNS, mDNS, DNS-SD</span></span>

* <span data-ttu-id="fff1c-156">Служба доменных имен (DNS)</span><span class="sxs-lookup"><span data-stu-id="fff1c-156">Domain Name System (DNS)</span></span>
* <span data-ttu-id="fff1c-157">Многоадресная служба доменных имен (mDNS).</span><span class="sxs-lookup"><span data-stu-id="fff1c-157">Multicast Domain Name System (mDNS)</span></span>
* <span data-ttu-id="fff1c-158">Обнаружение служб на основе DNS (DNS-SD).</span><span class="sxs-lookup"><span data-stu-id="fff1c-158">DNS-based service discovery (DNS-SD)</span></span>
* <span data-ttu-id="fff1c-159">Всего 2,4–3 КБ занимаемой флэш-памяти и 1 КБ в ОЗУ для DNS.</span><span class="sxs-lookup"><span data-stu-id="fff1c-159">DNS Minimal 2.4 KB to 3 KB FLASH, 1 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-160">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-160">Client support</span></span>
* <span data-ttu-id="fff1c-161">Интуитивно простые API: *nx_dns_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-161">Intuitive APIs: *nx_dns_\**</span></span>
* <span data-ttu-id="fff1c-162">mDNS и DNS-SD доступны только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-162">mDNS and DNS-SD are only available with Azure RTOS NetX Duo</span></span>

### <a name="p0p3"></a><span data-ttu-id="fff1c-163">P0P3</span><span class="sxs-lookup"><span data-stu-id="fff1c-163">P0P3</span></span>

* <span data-ttu-id="fff1c-164">Протокол Post Office Protocol версии 3 (POP3).</span><span class="sxs-lookup"><span data-stu-id="fff1c-164">Post Office Protocol Version 3 (POP3)</span></span>
* <span data-ttu-id="fff1c-165">Всего 8,1 КБ занимаемой памяти и 1,4 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-165">Minimal 8.1 KB and 1.4 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-166">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-166">Client support</span></span>
* <span data-ttu-id="fff1c-167">Интуитивно простые API P0P3: *nx_pop3_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-167">Intuitive P0P3 APIs: *nx_pop3_\**</span></span>

### <a name="telnet"></a><span data-ttu-id="fff1c-168">TELNET</span><span class="sxs-lookup"><span data-stu-id="fff1c-168">TELNET</span></span>

* <span data-ttu-id="fff1c-169">Всего 0,5 КБ занимаемой памяти и 0,3 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-169">Minimal 0.5 KB and 0.3 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-170">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-170">Client and server support</span></span>
* <span data-ttu-id="fff1c-171">Интуитивно простые API Telnet: *nx_telnet_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-171">Intuitive Telnet APIs: *nx_telnet_\**</span></span>

### <a name="ftp-tftp"></a><span data-ttu-id="fff1c-172">FTP, TFTP</span><span class="sxs-lookup"><span data-stu-id="fff1c-172">FTP, TFTP</span></span>

* <span data-ttu-id="fff1c-173">Протокол FTP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-173">File Transfer Protocol (FTP)</span></span>
* <span data-ttu-id="fff1c-174">Протокол TFTP</span><span class="sxs-lookup"><span data-stu-id="fff1c-174">Trivial File Transfer Protocol (TFTP)</span></span>
* <span data-ttu-id="fff1c-175">Всего 1,8–7,2 КБ занимаемой флэш-памяти и 0,6–2,1 КБ в ОЗУ для FTP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-175">FTP Minimal 1.8 KB to 7.2 KB FLASH, 0.6 KB to 2.1 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-176">Всего 1,7–2,4 КБ занимаемой флэш-памяти и 0,3–1,8 КБ в ОЗУ для TFTP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-176">TFTP Minimal 1.7 KB to 2.4 KB FLASH, 0.3 KB to 1.8 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-177">Поддержка клиентов и серверов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-177">Client and server support</span></span>
* <span data-ttu-id="fff1c-178">Интуитивно простые API FTP и TFTP: *nx_ftp_\** или *nx_tftp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-178">Intuitive FTP and TFTP APIs: *nx_ftp_\** or *nx_tftp_\**</span></span>

### <a name="ppp-pppoe"></a><span data-ttu-id="fff1c-179">PPP, PPPoE</span><span class="sxs-lookup"><span data-stu-id="fff1c-179">PPP, PPPoE</span></span>

* <span data-ttu-id="fff1c-180">Протокол PPP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-180">Polnt-to-PoInt Protocol (PPP)</span></span>
* <span data-ttu-id="fff1c-181">Протокол PPPoE.</span><span class="sxs-lookup"><span data-stu-id="fff1c-181">Point-to-Point Protocol over Ethernet(PPPoE)</span></span>
* <span data-ttu-id="fff1c-182">Всего 7,1 КБ занимаемой памяти и 3,8 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-182">Minimal 7.1 KB and 3.8 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-183">Интуитивно простые API PPP: *nx_ppp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-183">Intuitive PPP APIs: *nx_ppp_\**</span></span>

* <span data-ttu-id="fff1c-184">PPPoE доступен только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-184">PPPoE is only available with Azure RTOS NetX Duo</span></span>

### <a name="sntp"></a><span data-ttu-id="fff1c-185">SNTP</span><span class="sxs-lookup"><span data-stu-id="fff1c-185">SNTP</span></span>

* <span data-ttu-id="fff1c-186">Простой протокол синхронизации времени по сети (SNTP).</span><span class="sxs-lookup"><span data-stu-id="fff1c-186">Simple Network Time Protocol (SNTP)</span></span>
* <span data-ttu-id="fff1c-187">Всего 4 КБ занимаемой памяти и 0,5 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-187">Minimal 4 KB and 0.5 KB RAM</span></span>
* <span data-ttu-id="fff1c-188">Поддержка клиентов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-188">Client support</span></span>
* <span data-ttu-id="fff1c-189">Интуитивно простые API SNTP: *nx_sntp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-189">Intuitive SNTP APIs: *nx_sntp_\**</span></span>

### <a name="azure-rtos-netx-duo-api"></a><span data-ttu-id="fff1c-190">API NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fff1c-190">Azure RTOS NetX Duo API</span></span>

* <span data-ttu-id="fff1c-191">Интуитивно простой и согласованный API.</span><span class="sxs-lookup"><span data-stu-id="fff1c-191">Intuitive and consistent API</span></span>
* <span data-ttu-id="fff1c-192">Соглашение об именовании с использованием конструкций "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="fff1c-192">Noun-verb naming convention</span></span>
* <span data-ttu-id="fff1c-193">Быстрая реализация API без копирования.</span><span class="sxs-lookup"><span data-stu-id="fff1c-193">Fast, zero-copy API implementation</span></span>
* <span data-ttu-id="fff1c-194">Все API имеют префикс <i>nx_\*</i> для простой идентификации принадлежности к NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-194">All APIs have leading <i>nx_\*</i> to easily identify as Azure RTOS NetX</span></span>
* <span data-ttu-id="fff1c-195">Блокирующие API поддерживают опциональное время ожидания потоков.</span><span class="sxs-lookup"><span data-stu-id="fff1c-195">Blocking APIs have optional thread timeout</span></span>
* <span data-ttu-id="fff1c-196">Дополнительные сведения см. в статье [Руководство пользователя по NetX Duo в ОСРВ Azure](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="fff1c-196">See [Azure RTOS NetX Duo User Guide](about-this-guide.md) for more details</span></span>
* <span data-ttu-id="fff1c-197">Опциональный уровень BSD для портирования старого кода сокетов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-197">Optional BSD layer for porting legacy socket code</span></span>

### <a name="igmp"></a><span data-ttu-id="fff1c-198">IGMP</span><span class="sxs-lookup"><span data-stu-id="fff1c-198">IGMP</span></span>

* <span data-ttu-id="fff1c-199">протокол управления группами Интернета (IGMP)</span><span class="sxs-lookup"><span data-stu-id="fff1c-199">Internet Group Management Protocol (IGMP)</span></span>
* <span data-ttu-id="fff1c-200">Всего 2,5 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="fff1c-200">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fff1c-201">Поддержка групп многоадресной рассылки IPv4.</span><span class="sxs-lookup"><span data-stu-id="fff1c-201">IPv4 multicast group support</span></span>
* <span data-ttu-id="fff1c-202">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fff1c-202">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fff1c-203">Опциональная статистика IGMP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-203">Optional IGMP statistics</span></span>
* <span data-ttu-id="fff1c-204">Трассировка на уровне системы через ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="fff1c-204">System-level trace via Azure RTOS ThreadX</span></span>
* <span data-ttu-id="fff1c-205">Интуитивно простые API IGMP: *nx_igmp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-205">Intuitive IGMP APIs: *nx_igmp_\**</span></span>

### <a name="azure-rtos-netx-secure-dtls"></a><span data-ttu-id="fff1c-206">NetX Secure DTLS для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fff1c-206">Azure RTOS NetX Secure DTLS</span></span>

* <span data-ttu-id="fff1c-207">Протокол датаграмм безопасности транспортного уровня (DTLS) версий 1.0 и 1.2.</span><span class="sxs-lookup"><span data-stu-id="fff1c-207">Datagram Transport Layer Security (DTLS) 1.0 and 1.2</span></span>
* <span data-ttu-id="fff1c-208">Всего 11 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="fff1c-208">Minimal 11 KB FLASH</span></span>
* <span data-ttu-id="fff1c-209">Быстрое программное шифрование RSA с 2048-битным ключом занимает около 1 секунды при частоте @120MHz.</span><span class="sxs-lookup"><span data-stu-id="fff1c-209">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="fff1c-210">Оптимизированная реализация X.509.</span><span class="sxs-lookup"><span data-stu-id="fff1c-210">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="fff1c-211">Полная интеграция с сокетами UDP в NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-211">Fully integrated with Azure RTOS NetX Duo UDP sockets</span></span>
* <span data-ttu-id="fff1c-212">Поддержка аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="fff1c-212">Hardware Crypto Support</span></span>
* <span data-ttu-id="fff1c-213">Поддержка программного шифрования: RSA (с ключами любого размера), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512).</span><span class="sxs-lookup"><span data-stu-id="fff1c-213">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="fff1c-214">Шифрование на основе эллиптических кривых (ECC) с ECDSA (подписывание) и ECDH (шифрование), в том числе с P-кривыми с разрядностью в 192, 224, 256, 384 и 521 бит.</span><span class="sxs-lookup"><span data-stu-id="fff1c-214">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="fff1c-215">Поддержка зашифрованных ключей (зависит от оборудования).</span><span class="sxs-lookup"><span data-stu-id="fff1c-215">Encrypted Key Support (hardware dependent)</span></span>

### <a name="azure-rtos-netx-secure-tls"></a><span data-ttu-id="fff1c-216">NetX Secure TLS для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fff1c-216">Azure RTOS NetX Secure TLS</span></span>

* <span data-ttu-id="fff1c-217">Протокол TLS версий 1.0, 1.1 и 1.2.</span><span class="sxs-lookup"><span data-stu-id="fff1c-217">Transport Layer Security (TLS) 1.0, 1.1, and 1.2</span></span>
* <span data-ttu-id="fff1c-218">Всего 8,8 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="fff1c-218">Minimal 8.8 KB FLASH</span></span>
* <span data-ttu-id="fff1c-219">Быстрое программное шифрование RSA с 2048-битным ключом занимает около 1 секунды при частоте @120MHz.</span><span class="sxs-lookup"><span data-stu-id="fff1c-219">Fast, software RSA 2048-bit key size ~1-second @120MHz</span></span>
* <span data-ttu-id="fff1c-220">Оптимизированная реализация X.509.</span><span class="sxs-lookup"><span data-stu-id="fff1c-220">Streamlined X.509 Implementation</span></span>
* <span data-ttu-id="fff1c-221">Полная интеграция с сокетами TCP в NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-221">Fully integrated with Azure RTOS NetX Duo TCP sockets</span></span>
* <span data-ttu-id="fff1c-222">Поддержка аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="fff1c-222">Hardware Crypto Support</span></span>
* <span data-ttu-id="fff1c-223">Поддержка программного шифрования: RSA (с ключами любого размера), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512).</span><span class="sxs-lookup"><span data-stu-id="fff1c-223">Software Crypto Support: RSA (all key sizes), AES, DES/3DES, ECC, HMAC, MD5, SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512)</span></span>
* <span data-ttu-id="fff1c-224">Шифрование на основе эллиптических кривых (ECC) с ECDSA (подписывание) и ECDH (шифрование), в том числе с P-кривыми с разрядностью в 192, 224, 256, 384 и 521 бит.</span><span class="sxs-lookup"><span data-stu-id="fff1c-224">Elliptic Curve Cryptography (ECC) with ECDSA (signing) and ECDH (encryption), including P-curves 192/224/256/384/521</span></span>
* <span data-ttu-id="fff1c-225">Поддержка зашифрованных ключей (зависит от оборудования).</span><span class="sxs-lookup"><span data-stu-id="fff1c-225">Encrypted Key Support (hardware dependent)</span></span>

### <a name="icmp"></a><span data-ttu-id="fff1c-226">ICMP</span><span class="sxs-lookup"><span data-stu-id="fff1c-226">ICMP</span></span>

* <span data-ttu-id="fff1c-227">Протокол межсетевых управляющих сообщений (ICMP).</span><span class="sxs-lookup"><span data-stu-id="fff1c-227">Internet Control Message Protocol (ICMP)</span></span>
* <span data-ttu-id="fff1c-228">Всего 2,5 КБ занимаемой флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="fff1c-228">Minimal 2.5 KB FLASH</span></span>
* <span data-ttu-id="fff1c-229">Поддержка IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="fff1c-229">IPv4 and IPv6 support</span></span>
* <span data-ttu-id="fff1c-230">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fff1c-230">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fff1c-231">Запрос проверки связи и ответ на нее.</span><span class="sxs-lookup"><span data-stu-id="fff1c-231">Ping request and ping response</span></span>
* <span data-ttu-id="fff1c-232">Опциональная приостановка потока при запросах проверки связи.</span><span class="sxs-lookup"><span data-stu-id="fff1c-232">Optional thread suspension on ping requests</span></span>
* <span data-ttu-id="fff1c-233">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="fff1c-233">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fff1c-234">Опциональная статистика ICMP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-234">Optional ICMP statistics</span></span>
* <span data-ttu-id="fff1c-235">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-235">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fff1c-236">Интуитивно простые API ICMP: *nx_icmp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-236">Intuitive ICMP APIs: *nx_icmp_\**</span></span>

### <a name="udp"></a><span data-ttu-id="fff1c-237">UDP</span><span class="sxs-lookup"><span data-stu-id="fff1c-237">UDP</span></span>

* <span data-ttu-id="fff1c-238">Протокол UDP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-238">User Datagram Protocol (UDP)</span></span>
* <span data-ttu-id="fff1c-239">Всего 2,5 КБ занимаемой флэш-памяти, 124 байт в ОЗУ на сокет.</span><span class="sxs-lookup"><span data-stu-id="fff1c-239">Minimal 2.5 KB FLASH, 124 sockets bytes of RAM per socket</span></span>
* <span data-ttu-id="fff1c-240">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="fff1c-240">Fast, near wirespeed TCP packet processing:</span></span>
    * <span data-ttu-id="fff1c-241">RX на уровне 95 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 14 %.</span><span class="sxs-lookup"><span data-stu-id="fff1c-241">RX 95 Mbps on 100 Mbps Ethernet, MCU @100MHz, 14% MCU utilization</span></span>
    * <span data-ttu-id="fff1c-242">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 10 %.</span><span class="sxs-lookup"><span data-stu-id="fff1c-242">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 10% MCU utilization</span></span>
* <span data-ttu-id="fff1c-243">Технология UDP Fast Path™.</span><span class="sxs-lookup"><span data-stu-id="fff1c-243">UDP Fast Path™ technology</span></span>
* <span data-ttu-id="fff1c-244">Отсутствие ограничений на число UDP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-244">No limits on the number of UDP</span></span>
* <span data-ttu-id="fff1c-245">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fff1c-245">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fff1c-246">Опциональная приостановка при получении на сокет.</span><span class="sxs-lookup"><span data-stu-id="fff1c-246">Optional suspension on socket receive</span></span>
* <span data-ttu-id="fff1c-247">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="fff1c-247">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fff1c-248">Опциональная статистика UDP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-248">Optional UDP statistics</span></span>
* <span data-ttu-id="fff1c-249">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-249">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fff1c-250">Интуитивно простые API UDP: *nx_udp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-250">Intuitive UDP APIs: *nx_udp_\**</span></span>

### <a name="tcp"></a><span data-ttu-id="fff1c-251">TCP</span><span class="sxs-lookup"><span data-stu-id="fff1c-251">TCP</span></span>

* <span data-ttu-id="fff1c-252">Протокол TCP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-252">Transmission Control Protocol (TCP)</span></span>
* <span data-ttu-id="fff1c-253">Всего 10,5–12,5 КБ занимаемой флэш-памяти, 280 байт в ОЗУ на сокет.</span><span class="sxs-lookup"><span data-stu-id="fff1c-253">Minimal 10.5K8 to 12.5 KB FLASH, 280 bytes of RAM per socket</span></span>
* <span data-ttu-id="fff1c-254">Быстрая обработка пакетов TCP на уровне проводной сети:</span><span class="sxs-lookup"><span data-stu-id="fff1c-254">Fast, near wlrespeed TCP packet processing:</span></span>
    * <span data-ttu-id="fff1c-255">RX на уровне 93 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 20 %.</span><span class="sxs-lookup"><span data-stu-id="fff1c-255">RX 93 Mbps on 100 Mbps Ethernet, MCU @100MHz, 20% MCU utilization</span></span>
    * <span data-ttu-id="fff1c-256">TX на уровне 94 Мбит/с в сети Ethernet со скоростью 100 Мбит/с при частоте MCU @100MHz и использовании MCU на уровне 27 %.</span><span class="sxs-lookup"><span data-stu-id="fff1c-256">TX 94 Mbps on 100 Mbps Ethernet, MCU @100MHz, 27% MCU utilization</span></span>
* <span data-ttu-id="fff1c-257">Надежное подключение.</span><span class="sxs-lookup"><span data-stu-id="fff1c-257">Reliable connection</span></span>
* <span data-ttu-id="fff1c-258">Отсутствие ограничений на число TCP-сокетов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-258">No limits on the number of TCP sockets</span></span>
* <span data-ttu-id="fff1c-259">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fff1c-259">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fff1c-260">Опциональная приостановка при получении или отправке на сокете.</span><span class="sxs-lookup"><span data-stu-id="fff1c-260">Optional suspension on socket receive/transmit</span></span>
* <span data-ttu-id="fff1c-261">Опциональное время ожидания при всех приостановках.</span><span class="sxs-lookup"><span data-stu-id="fff1c-261">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fff1c-262">Опциональная статистика TCP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-262">Optional TCP statistics</span></span>
* <span data-ttu-id="fff1c-263">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-263">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fff1c-264">Интуитивно простые API TCP: *nx_tcp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-264">Intuitive TCP APIs: *nx_tcp_\**</span></span>

### <a name="arprarp"></a><span data-ttu-id="fff1c-265">ARP и RARP</span><span class="sxs-lookup"><span data-stu-id="fff1c-265">ARP/RARP</span></span>

* <span data-ttu-id="fff1c-266">Протокол разрешения адресов (ARP).</span><span class="sxs-lookup"><span data-stu-id="fff1c-266">Address Resolution Protocol (ARP)</span></span>
* <span data-ttu-id="fff1c-267">Обратный протокол разрешения адресов (RARP)</span><span class="sxs-lookup"><span data-stu-id="fff1c-267">Reverse Address Resolution Protocol (RARP)</span></span>
* <span data-ttu-id="fff1c-268">Всего 1,7 КБ занимаемой флэш-памяти и ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-268">Minimal 1.7 KB FLASH, RAM size</span></span>
* <span data-ttu-id="fff1c-269">Динамическое разрешение 32-разрядных IPv4-адресов и 48-разрядных MAC-адресов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-269">Dynamic resolution of 32-blt IPv4 and 48-blt MAC addresses</span></span>
* <span data-ttu-id="fff1c-270">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fff1c-270">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fff1c-271">Гибкий кэш ARP, определяемый пользователем.</span><span class="sxs-lookup"><span data-stu-id="fff1c-271">Flexible, user-defined ARP cache</span></span>
* <span data-ttu-id="fff1c-272">Поддержка самообращенных запросов ARP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-272">Gratuitous ARP support</span></span>
* <span data-ttu-id="fff1c-273">Опциональная статистика ARP и RARP, определяемая приложением.</span><span class="sxs-lookup"><span data-stu-id="fff1c-273">Optional ARP/RARP statistics determined by application</span></span>
* <span data-ttu-id="fff1c-274">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-274">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fff1c-275">Интуитивно простые API ARP и RARP: *nx_arp_\** , *nx_rarp_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-275">Intuitive ARP/RARP APIs: *nx_arp_\**, *nx_rarp_\**</span></span>

### <a name="ipv4-amp-ipv6"></a><span data-ttu-id="fff1c-276">IPv4 и IPv6</span><span class="sxs-lookup"><span data-stu-id="fff1c-276">IPv4 &amp; IPv6</span></span>

* <span data-ttu-id="fff1c-277">Протокол IP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-277">Internet Protocol (IP)</span></span>
* <span data-ttu-id="fff1c-278">Всего 3,5–8,5 КБ занимаемой флэш-памяти, 2–3 КБ в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="fff1c-278">Minimal 3.5 KB to 8.5 KB FLASH, 2 KB to 3 KB RAM footprint</span></span>
* <span data-ttu-id="fff1c-279">Архитектура Piconet™.</span><span class="sxs-lookup"><span data-stu-id="fff1c-279">Piconet™ architecture</span></span>
* <span data-ttu-id="fff1c-280">Высокая производительность на уровне проводной сети.</span><span class="sxs-lookup"><span data-stu-id="fff1c-280">Fast, near wirespeed performance</span></span>
* <span data-ttu-id="fff1c-281">Поддержка нескольких интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-281">Multiple interface support</span></span>
* <span data-ttu-id="fff1c-282">Поддержка многосетевых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-282">Multihomed support</span></span>
* <span data-ttu-id="fff1c-283">Поддержка статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="fff1c-283">Static routing support</span></span>
* <span data-ttu-id="fff1c-284">Поддержка фрагментирования и повторной сборки пакетов IP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-284">IP fragmentation/reassembly support</span></span>
* <span data-ttu-id="fff1c-285">Поддержка IPv4- и IPv6-адресов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-285">IPv4 and IPv6 address support</span></span>
* <span data-ttu-id="fff1c-286">Проверено IXIA IxANVL.</span><span class="sxs-lookup"><span data-stu-id="fff1c-286">IXIA IxANVL validated</span></span>
* <span data-ttu-id="fff1c-287">Сертификация по программе IPv6 Ready Logo Phase-2</span><span class="sxs-lookup"><span data-stu-id="fff1c-287">Phase II IPv6 Ready Logo Certification</span></span>
* <span data-ttu-id="fff1c-288">Опциональная статистика IP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-288">Optional IP statistics</span></span>
* <span data-ttu-id="fff1c-289">Хорошо определенный, интуитивно простой интерфейс драйвера физического уровня.</span><span class="sxs-lookup"><span data-stu-id="fff1c-289">Well defined, intuitive physical layer driver interface</span></span>
* <span data-ttu-id="fff1c-290">Трассировка на уровне системы через TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-290">System-level trace via Azure RTOS TraceX</span></span>
* <span data-ttu-id="fff1c-291">Интуитивно простые API уровня IP: *nx_ip_\** , *nxd_ip_\** , *nxd_ipv6_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-291">Intuitive IP layer APIs: *nx_ip_\**, *nxd_ip_\**, *nxd_ipv6_\**</span></span>
* <span data-ttu-id="fff1c-292">Предварительная сертификация TUV и UL на соответствие стандартам IEC 61508 SIL 4, IEC 62304 (класс C), ISO 26262 ASIL D и EN 50128 SW-SIL4.</span><span class="sxs-lookup"><span data-stu-id="fff1c-292">Pre-certified by TUV and UL to IEC 61508 SIL 4, IEC 62304 Class C, ISO 26262 ASIL D, and EN 50128 SW-SIL4</span></span>

### <a name="azure-rtos-netx-secure-ipsec"></a><span data-ttu-id="fff1c-293">Надежный протокол IPsec в NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fff1c-293">Azure RTOS NetX Secure IPSEC</span></span>

* <span data-ttu-id="fff1c-294">IPsec.</span><span class="sxs-lookup"><span data-stu-id="fff1c-294">Internet Protocol Security (IPSEC)</span></span>
* <span data-ttu-id="fff1c-295">Уровень IP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-295">IP layer</span></span>
* <span data-ttu-id="fff1c-296">Поддержка аппаратного шифрования.</span><span class="sxs-lookup"><span data-stu-id="fff1c-296">Hardware crypto support</span></span>
* <span data-ttu-id="fff1c-297">Поддержка программного шифрования, в том числе следующего:</span><span class="sxs-lookup"><span data-stu-id="fff1c-297">Software crypto support, including:</span></span>
    * <span data-ttu-id="fff1c-298">DES, 3DES;</span><span class="sxs-lookup"><span data-stu-id="fff1c-298">DES, 3DES</span></span>
    * <span data-ttu-id="fff1c-299">AES</span><span class="sxs-lookup"><span data-stu-id="fff1c-299">AES</span></span>
    * <span data-ttu-id="fff1c-300">HMAC-MD5;</span><span class="sxs-lookup"><span data-stu-id="fff1c-300">HMAC-MD5</span></span>
    * <span data-ttu-id="fff1c-301">HMAC-SHA1.</span><span class="sxs-lookup"><span data-stu-id="fff1c-301">HMAC-SHA1</span></span>
* <span data-ttu-id="fff1c-302">Поддержка протокола IKE версии 2.</span><span class="sxs-lookup"><span data-stu-id="fff1c-302">Internet Key Exchange (IKE) Version 2 support</span></span>
* <span data-ttu-id="fff1c-303">Интуитивно простые API IPsec: *nx_ipsec_\** .</span><span class="sxs-lookup"><span data-stu-id="fff1c-303">Intuitive IPsec APIs: *nx_ipsec_\**</span></span>
* <span data-ttu-id="fff1c-304">IPsec доступен только с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-304">IPsec is only available with Azure RTOS NetX Duo</span></span>

## <a name="small-footprint"></a><span data-ttu-id="fff1c-305">Нетребовательность к ресурсам</span><span class="sxs-lookup"><span data-stu-id="fff1c-305">Small-footprint</span></span>

<span data-ttu-id="fff1c-306">NetX Duo для ОСРВ Azure занимает всего 9–15 КБ памяти при базовой поддержке IP и UDP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-306">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="fff1c-307">Для функций TCP требуются дополнительно 10–13 КБ памяти области инструкций.</span><span class="sxs-lookup"><span data-stu-id="fff1c-307">An additional 10 KB to 13 KB of instruction area memory is needed for TCP functionality.</span></span> <span data-ttu-id="fff1c-308">NetX Duo для ОСРВ Azure обычно занимает в ОЗУ от 2,6 до 3,6 КБ, а также некоторый объем памяти пула пакетов, который определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="fff1c-308">Azure RTOS NetX Duo RAM usage typically ranges from 2.6 KB to 3.6 KB plus the packet pool memory, which is defined by the application.</span></span> <span data-ttu-id="fff1c-309">Как и со ThreadX для ОСРВ Azure, размер NetX Duo для ОСРВ Azure масштабируется автоматически в зависимости от служб, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="fff1c-309">Like Azure RTOS ThreadX, the size of Azure RTOS NetX Duo automatically scales based on the services used by the application.</span></span> <span data-ttu-id="fff1c-310">Это практически устраняет потребность в сложной настройке и параметрах сборки, что упрощает работу разработчика.</span><span class="sxs-lookup"><span data-stu-id="fff1c-310">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="fff1c-311">Быстрое выполнение</span><span class="sxs-lookup"><span data-stu-id="fff1c-311">Fast execution</span></span>

<span data-ttu-id="fff1c-312">NetX Duo для ОСРВ Azure предоставляет реализацию отправки и получения пакетов без копирования, а также тесно интегрирован со ThreadX для ОСРВ Azure для достижения максимальной производительности.</span><span class="sxs-lookup"><span data-stu-id="fff1c-312">Azure RTOS NetX Duo provides a zero-copy packet send/receive implementation, highly integrated with Azure RTOS ThreadX, to achieve the fastest possible performance.</span></span> <span data-ttu-id="fff1c-313">Например, NetX Duo для ОСРВ Azure может достигать скоростей передачи данных, сравнимых с проводной сетью, на процессоре с частотой 80 МГц (или менее), используя лишь незначительную часть его ресурсов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-313">For example, Azure RTOS NetX Duo can typically achieve near wirespeed data transfers on an 80 MHz (or less) processor, while using only a small percentage of the processor cycles.</span></span>

## <a name="simple-easy-to-use"></a><span data-ttu-id="fff1c-314">Простота использования</span><span class="sxs-lookup"><span data-stu-id="fff1c-314">Simple, easy-to-use</span></span>

<span data-ttu-id="fff1c-315">API NetX Duo для ОСРВ Azure отличается простотой, понятностью и функциональностью.</span><span class="sxs-lookup"><span data-stu-id="fff1c-315">The Azure RTOS NetX Duo API is intuitive, straightforward,  and highly functional.</span></span>

<span data-ttu-id="fff1c-316">Названия API состоят из реальных слов, а не из набора букв или сокращенных имен, которые так часто используются для других сетевых продуктов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-316">The API names are made of real words and not the “alphabet soup” or highly abbreviated names that are so common in other networking products.</span></span> <span data-ttu-id="fff1c-317">Все API NetX Duo для ОСРВ Azure имеют префикс *nx_* и соответствуют соглашению об именовании с использованием конструкций "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="fff1c-317">All Azure RTOS NetX Duo APIs have a leading *nx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="fff1c-318">Более того, для API обеспечивается функциональная согласованность.</span><span class="sxs-lookup"><span data-stu-id="fff1c-318">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="fff1c-319">Например, для всех функций API, которые поддерживают приостановку работы, реализовано опциональное время ожидания, работающее аналогичным образом.</span><span class="sxs-lookup"><span data-stu-id="fff1c-319">For example, all API functions that suspend have an optional timeout that operates in an identical manner.</span></span>

<span data-ttu-id="fff1c-320">Для устаревших приложений NetX Duo для ОСРВ Azure предлагает дополнительный уровень, совместимый с сокетами BSD.</span><span class="sxs-lookup"><span data-stu-id="fff1c-320">For legacy applications, Azure RTOS NetX Duo offers an additional BSD socket compatible layer.</span></span> <span data-ttu-id="fff1c-321">Этот уровень помогает разработчикам переносить крупные сетевые приложения.</span><span class="sxs-lookup"><span data-stu-id="fff1c-321">This layer helps developers migrate large networking applications with ease.</span></span>

## <a name="safe-and-secure"></a><span data-ttu-id="fff1c-322">Безопасность и защищенность</span><span class="sxs-lookup"><span data-stu-id="fff1c-322">Safe and secure</span></span>

<span data-ttu-id="fff1c-323">Стек NetX Duo для ОСРВ Azure защищен.</span><span class="sxs-lookup"><span data-stu-id="fff1c-323">Azure RTOS NetX Duo is secure.</span></span> <span data-ttu-id="fff1c-324">Его безопасность обеспечивается с помощью подключаемых продуктов безопасности, в числе которых IPsec, SSL, TLS и DTLS.</span><span class="sxs-lookup"><span data-stu-id="fff1c-324">This security is provided through add-on security products, including IPsec, SSL, TLS, and DTLS.</span></span> <span data-ttu-id="fff1c-325">Кроме того, приложение полностью управляет всем внешним доступом к NetX Duo для ОСРВ Azure, что значительно упрощает определение рисков безопасности.</span><span class="sxs-lookup"><span data-stu-id="fff1c-325">Also, the application has complete control over all external access to Azure RTOS NetX Duo, making security risk determination much easier.</span></span>

<span data-ttu-id="fff1c-326">ОСРВ Azure от Майкрософт предоставляет изготовителям оборудования компоненты для безопасного обмена данными, а также создания кода и изоляции данных с помощью базовых аппаратных механизмов защиты, встроенных в микроконтроллеры и микропроцессоры.</span><span class="sxs-lookup"><span data-stu-id="fff1c-326">Microsoft Azure RTOS provides OEMs with components to secure communication and to create code and data isolation using underlying MCU/MPU hardware protection mechanisms.</span></span> <span data-ttu-id="fff1c-327">Ответственность за полное соответствие устройства меняющимся требованиям к безопасности в отношении отдельных вариантов использования в конечном итоге лежит на производителе устройства.</span><span class="sxs-lookup"><span data-stu-id="fff1c-327">It is ultimately the responsibility of the device builder to ensure the device fully meets the evolving security requirements associated with its specific use case.</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="fff1c-328">Предварительная сертификация TUV и UL на соответствие множеству стандартов безопасности</span><span class="sxs-lookup"><span data-stu-id="fff1c-328">Pre-certified  by TUV and UL to many safety standards</span></span>

<span data-ttu-id="fff1c-329">NetX Duo для ОСРВ Azure сертифицирован SGS-TUV Saar для использования в системах со строгими требованиями к безопасности, определенными стандартами IEC-61508 SIL 4, IEC-62304 SW (класс безопасности C), ISO 26262 ASIL D и EN 50128.</span><span class="sxs-lookup"><span data-stu-id="fff1c-329">Azure RTOS NetX Duo has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="fff1c-330">Такая сертификация гарантирует, что NetX Duo для ОСРВ Azure можно использовать при разработке ПО с особыми требованиями к функциональной безопасности, соответствующего высочайшим уровням полноты безопасности по стандартам IEC-61508, IEC-62304, ISO 26262 и EN 50128 для "функциональной безопасности электрических, электронных и программируемых электронных систем, связанных с безопасностью".</span><span class="sxs-lookup"><span data-stu-id="fff1c-330">The certification confirms that Azure RTOS NetX Duo can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="fff1c-331">Компания SGS-TUV Saar, основанная совместно немецкими компаниями SGS-Group и TUV Saarland, стала ведущей аккредитованной и независимой компанией, выполняющей тестирование, аудит, проверку и сертификацию внедренного ПО для связанных с безопасностью систем.</span><span class="sxs-lookup"><span data-stu-id="fff1c-331">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="fff1c-332">Соответствие промышленному стандарту безопасности IEC 61508 и всем его производным стандартам, в том числе IEC-62304, ISO 26262 и EN 50128, гарантирует функциональную безопасность электрических, электронных и программируемых электронных медицинских изделий, систем управления процессами, промышленного оборудования, автомобилей и систем управления железнодорожными перевозками с высоким уровнем безопасности.</span><span class="sxs-lookup"><span data-stu-id="fff1c-332">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

:::image type="content" source="media/overview-netx-duo/partener-logo-sgs-tuv-saar.png" alt-text="Сертификация SGS-TUV":::

<span data-ttu-id="fff1c-334">NetX Duo для ОСРВ Azure отмечен UL как соответствующий стандартам безопасности UL 60730-1 (приложение H), CSA E60730-1 (приложение H), IEC 60730-1 (приложение H), UL 60335-1 (приложение R), IEC 60335-1 (приложение R) и UL 1998 для ПО в программируемых компонентах.</span><span class="sxs-lookup"><span data-stu-id="fff1c-334">Azure RTOS NetX Duo has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="fff1c-335">UL — это глобальная независимая компания, работающая в сфере науки безопасности. Уже более ста лет она создает инновационные решения безопасности в разных областях — от повсеместного внедрения электричества до прорывов в сферах экологической устойчивости, возобновляемых источников энергии и нанотехнологий.</span><span class="sxs-lookup"><span data-stu-id="fff1c-335">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

:::image type="content" source="media/overview-netx-duo/cru-logo-certification.png" alt-text="Сертификация CRU UL":::

<span data-ttu-id="fff1c-337">Информационные продукты (сертификат, руководство по безопасности, отчет о тестировании и т. д.) для сертификаций TUV и UL доступны для продажи.</span><span class="sxs-lookup"><span data-stu-id="fff1c-337">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="fff1c-338">В тех случаях, когда для приложения требуется дополнительная сертификация, Майкрософт предлагает услугу по сертификации, которая позволяет получить готовую сертификацию по различным стандартам с учетом реальной аппаратной платформы, распространяющуюся даже на код приложения.</span><span class="sxs-lookup"><span data-stu-id="fff1c-338">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span> <span data-ttu-id="fff1c-339">Чтобы узнать больше об услуге сертификации, свяжитесь с нами.</span><span class="sxs-lookup"><span data-stu-id="fff1c-339">Contact us for more details on our certification service.</span></span>

## <a name="eal4-common-criteria-security-certification"></a><span data-ttu-id="fff1c-340">Сертификат безопасности по общим критериям EAL4+</span><span class="sxs-lookup"><span data-stu-id="fff1c-340">EAL4+ Common Criteria security certification</span></span>

<span data-ttu-id="fff1c-341">Служба ОСРВ Azure имеет сертификацию безопасности по общим критериям EAL4+.</span><span class="sxs-lookup"><span data-stu-id="fff1c-341">Azure RTOS has achieved EAL4+ Common Criteria security certification.</span></span> <span data-ttu-id="fff1c-342">Цели оценки (TOE): ThreadX для ОСРВ Azure, NetX Duo для ОСРВ Azure, NetX Secure TLS для ОСРВ Azure и MQTT в NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-342">The Target of Evalution (TOE) covers Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS, and Azure RTOS NetX MQTT.</span></span> <span data-ttu-id="fff1c-343">Это самые распространенные протоколы Интернета вещей, которые требуются для работы внедренных датчиков, устройств, пограничных маршрутизаторов и шлюзов.</span><span class="sxs-lookup"><span data-stu-id="fff1c-343">This represents the most typical IoT protocols required by deeply embedded sensors, devices, edge routers, and gateways.</span></span>

:::image type="content" source="media/overview-netx-duo/eal-logo-certification.png" alt-text="Сертификация EAL":::

<span data-ttu-id="fff1c-345">В качестве оценщика ИТ-безопасности (ITSEF), выполнившего сертификацию ОСРВ Azure по безопасности, выступила компания Brightsight BV, а в качестве центра сертификации — SERTIT.</span><span class="sxs-lookup"><span data-stu-id="fff1c-345">The IT Security Evaluation Facility used for the Microsoft Azure RTOS SC security certification is Brightsight BV and the Certification Authority is SERTIT.</span></span>

## <a name="fips-140-2-validated"></a><span data-ttu-id="fff1c-346">Соответствие стандарту FIPS 140-2</span><span class="sxs-lookup"><span data-stu-id="fff1c-346">FIPS 140-2 Validated</span></span>

<span data-ttu-id="fff1c-347">Библиотеки шифрования NetX для ОСРВ Azure сертифицированы на соответствие стандарту FIPS 140-2 для программного обеспечения, который включает требования для криптографических модулей.</span><span class="sxs-lookup"><span data-stu-id="fff1c-347">Azure RTOS NetX Crypto libraries have achieved Federal Information Processing Standardization 140-2 (FIPS 140-2) Certification for software, which specifies requirements for cryptography modules.</span></span> <span data-ttu-id="fff1c-348">FIPS 140-2 требует, чтобы все федеральные правительственные организации и министерства, использующие средства безопасности на основе шифрования, обеспечили соответствие определенным стандартам, касающимся стойкости и возможностей шифрования.</span><span class="sxs-lookup"><span data-stu-id="fff1c-348">FIPS 140-2 requires all federal government agencies and departments that use cryptographic-based security to meet specific standards related to encryption strength and capabilities.</span></span> <span data-ttu-id="fff1c-349">Такие стандарты безопасности на основе шифрования также признаются в Канаде и Европейском союзе.</span><span class="sxs-lookup"><span data-stu-id="fff1c-349">These cryptographic-based security standards are also recognized in Canada and the European Union.</span></span>

<span data-ttu-id="fff1c-350">В качестве лаборатории оценки ИТ-безопасности, выполнившей проверку библиотек шифрования NetX для ОСРВ Azure, выступила компания atsec, а в качестве центра сертификации — Национальный институт стандартов и технологии (NIST).</span><span class="sxs-lookup"><span data-stu-id="fff1c-350">The Information Security evaluation lab used for Azure RTOS NetX Crypto libraries was atsec and the certification authority is The National Institute of Standards and Technology (NIST).</span></span> <span data-ttu-id="fff1c-351">Дополнительные сведения см. на [веб-сайте NIST](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394).</span><span class="sxs-lookup"><span data-stu-id="fff1c-351">Review the [NIST website](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394) for additional details.</span></span>

## <a name="interoperability-verification"></a><span data-ttu-id="fff1c-352">Подтвержденная совместимость</span><span class="sxs-lookup"><span data-stu-id="fff1c-352">Interoperability verification</span></span>

<span data-ttu-id="fff1c-353">NetX Duo соответствует стандартам RFC и обеспечивает полную совместимость с устройствами большинства поставщиков.</span><span class="sxs-lookup"><span data-stu-id="fff1c-353">NetX Duo conforms to RFC standards and offers complete interoperability with devices for most vendors.</span></span>

![Логотип IPv6 Ready](./media/overview-netx-duo/ipv6-ready-logo.png)

<span data-ttu-id="fff1c-355">NetX Duo для ОСРВ Azure — это единственный стек с внедренными протоколами TCP/IP, соответствующий строгим требованиям сертификации IPv6-Ready Logo. То есть он прошел все проверки на согласованность и совместимость, принятые и утвержденные организацией IPv6 Forum.</span><span class="sxs-lookup"><span data-stu-id="fff1c-355">Azure RTOS NetX Duo is one of the only embedded TCP/IP stacks to achieve the rigorous IPv6-Ready Logo certification, evidence that it has passed conformance and interoperability tests, administered and validated by the IPv6 Forum.</span></span> <span data-ttu-id="fff1c-356">NetX Duo также использует стандартную отраслевую библиотеку IxANVL для базовой реализации протокола TCP/IP в NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fff1c-356">NetX Duo also utilizes the industry standard IxANVL (Automated Network Validation Library) for the NetX Duo core TCP/IP protocol implementation.</span></span>

## <a name="comprehensive-iot-solution"></a><span data-ttu-id="fff1c-357">Комплексное решение Интернета вещей</span><span class="sxs-lookup"><span data-stu-id="fff1c-357">Comprehensive IoT solution</span></span>

<span data-ttu-id="fff1c-358">NetX Duo для ОСРВ Azure занимает всего 9–15 КБ памяти при базовой поддержке IP и UDP.</span><span class="sxs-lookup"><span data-stu-id="fff1c-358">Azure RTOS NetX Duo has a remarkably small footprint of 9 KB to 15 KB for basic IP and UDP support.</span></span> <span data-ttu-id="fff1c-359">NetX Duo предоставляет один из самых комплексных наборов сетевых функций с поддержкой TCP/IP для глубоко внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="fff1c-359">NetX Duo has one of the most comprehensive TCP/IP networking for deeply embedded IoT applications.</span></span> <span data-ttu-id="fff1c-360">Такая поддержка включает следующие подключаемые протоколы:</span><span class="sxs-lookup"><span data-stu-id="fff1c-360">This support includes the following add-on protocol products:</span></span>

<span data-ttu-id="fff1c-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP версии 1, 2 и 3, Telnet, TFTP</span><span class="sxs-lookup"><span data-stu-id="fff1c-361">MQTT, CoAP, LWM2M, 6LoWPAN, SSL/TLS/DTLS, IPsec, AutoIP, DHCP, DNS, mDNS, DNS-SD, FTP, HTTP, IPsec, NAT, POP3, PPP, PPPoE, SMTP, SNMP v1/2/3, Telnet, TFTP</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="fff1c-362">Передовая технология</span><span class="sxs-lookup"><span data-stu-id="fff1c-362">Advanced technology</span></span>

<span data-ttu-id="fff1c-363">NetX Duo для ОСРВ Azure — эта передовая технология, включающая следующее:</span><span class="sxs-lookup"><span data-stu-id="fff1c-363">Azure RTOS NetX Duo is advanced technology that includes:</span></span>

* <span data-ttu-id="fff1c-364">архитектура Piconet™;</span><span class="sxs-lookup"><span data-stu-id="fff1c-364">Piconet™ architecture</span></span>
* <span data-ttu-id="fff1c-365">Автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="fff1c-365">Automatic scaling</span></span>
* <span data-ttu-id="fff1c-366">технология UDP Fast-Path™;</span><span class="sxs-lookup"><span data-stu-id="fff1c-366">UDP Fast-Path Technology™</span></span>
* <span data-ttu-id="fff1c-367">гибкое управление пакетами;</span><span class="sxs-lookup"><span data-stu-id="fff1c-367">Flexible packet management</span></span>
* <span data-ttu-id="fff1c-368">API и реализация без копирования;</span><span class="sxs-lookup"><span data-stu-id="fff1c-368">Zero-copy API and implementation</span></span>
* <span data-ttu-id="fff1c-369">поддержка многосетевых интерфейсов;</span><span class="sxs-lookup"><span data-stu-id="fff1c-369">Multihomed support</span></span>
* <span data-ttu-id="fff1c-370">опциональное время ожидания при всех приостановках;</span><span class="sxs-lookup"><span data-stu-id="fff1c-370">Optional timeout on all suspension</span></span>
* <span data-ttu-id="fff1c-371">поддержка статической маршрутизации;</span><span class="sxs-lookup"><span data-stu-id="fff1c-371">Static routing support</span></span>
* <span data-ttu-id="fff1c-372">IPsec</span><span class="sxs-lookup"><span data-stu-id="fff1c-372">IPsec</span></span>
* <span data-ttu-id="fff1c-373">SSL, TLS и DTLS;</span><span class="sxs-lookup"><span data-stu-id="fff1c-373">SSL/TLS/DTLS</span></span>
* <span data-ttu-id="fff1c-374">поддержка системного анализа TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-374">Azure RTOS TraceX system analysis support</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="fff1c-375">Минимальное время выхода на рынок</span><span class="sxs-lookup"><span data-stu-id="fff1c-375">Fastest time-to-market</span></span>

<span data-ttu-id="fff1c-376">NetX Duo для ОСРВ Azure легко устанавливать, изучать, использовать, отлаживать, проверять, сертифицировать и обслуживать.</span><span class="sxs-lookup"><span data-stu-id="fff1c-376">Azure RTOS NetX Duo is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="fff1c-377">В результате NetX для ОСРВ Azure является одним из самых популярных стеков TCP/IP для внедренных устройств Интернета вещей, в том числе для множества интегральных систем от Broadcom, Gainspan и др. Наше преимущество по стабильно малому времени выхода на рынок обусловлено следующим:</span><span class="sxs-lookup"><span data-stu-id="fff1c-377">As a result, NetX Duo is one of the most popular TCP/IP stacks for embedded IoT devices, including many SoCs from Broadcom, Gainspan, etc. Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="fff1c-378">документация высокого качества — ознакомьтесь с нашим [руководством пользователя по NetX Duo для ОСРВ Azure](about-this-guide.md) и убедитесь в этом сами;</span><span class="sxs-lookup"><span data-stu-id="fff1c-378">Quality documentation – please review our [Azure RTOS NetX Duo User Guide](about-this-guide.md) and see for yourself!</span></span>
* <span data-ttu-id="fff1c-379">полная доступность исходного кода;</span><span class="sxs-lookup"><span data-stu-id="fff1c-379">Complete source code availability</span></span>
* <span data-ttu-id="fff1c-380">простые в использовании API;</span><span class="sxs-lookup"><span data-stu-id="fff1c-380">Easy-to-use API</span></span>
* <span data-ttu-id="fff1c-381">комплексный и широкий набор функций.</span><span class="sxs-lookup"><span data-stu-id="fff1c-381">Comprehensive and advanced feature set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="fff1c-382">Одна простая лицензия</span><span class="sxs-lookup"><span data-stu-id="fff1c-382">One Simple License</span></span>

<span data-ttu-id="fff1c-383">Использование и тестирование исходного кода не требуют каких-либо затрат, как и лицензии для рабочей среды при развертывании на предварительно лицензированных устройствах. Для всех других устройств требуется лишь простая лицензия сроком на один год.</span><span class="sxs-lookup"><span data-stu-id="fff1c-383">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="fff1c-384">Полный и высококачественный исходный код</span><span class="sxs-lookup"><span data-stu-id="fff1c-384">Full, highest-quality source code</span></span>

<span data-ttu-id="fff1c-385">Уже несколько лет NetX Duo для ОСРВ Azure задает стандарт качества и простоты понимания.</span><span class="sxs-lookup"><span data-stu-id="fff1c-385">Throughout the years, Azure RTOS NetX Duo source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="fff1c-386">Кроме того, соглашение по назначению каждой функции отдельного файла упрощает навигацию по исходному коду.</span><span class="sxs-lookup"><span data-stu-id="fff1c-386">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="fff1c-387">Поддержка большинства популярных архитектур</span><span class="sxs-lookup"><span data-stu-id="fff1c-387">Supports most popular architectures</span></span>

<span data-ttu-id="fff1c-388">NetX Duo для ОСРВ Azure работает на большинстве популярных 32-и 64-разрядных микропроцессоров. Этот стек не требует дополнительной настройки, полностью протестирован и поддерживается в том числе на следующих передовых архитектурах:</span><span class="sxs-lookup"><span data-stu-id="fff1c-388">Azure RTOS NetX Duo runs on most popular 32/64-bit microprocessors out-of-the-box, fully tested and fully supported, including the following advanced architectures:</span></span>

<span data-ttu-id="fff1c-389">**Analog Devices**: SHARC, Blackfin, CM4xx.</span><span class="sxs-lookup"><span data-stu-id="fff1c-389">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="fff1c-390">**Andes Core**: RISC-V.</span><span class="sxs-lookup"><span data-stu-id="fff1c-390">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="fff1c-391">**Ambiqmicro**: микроконтроллеры Apollo.</span><span class="sxs-lookup"><span data-stu-id="fff1c-391">**Ambiqmicro**: pollo MCUs</span></span>

<span data-ttu-id="fff1c-392">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="fff1c-392">**ARM**: RM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="fff1c-393">**Cadence**: Xtensa, Diamond.</span><span class="sxs-lookup"><span data-stu-id="fff1c-393">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="fff1c-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi.</span><span class="sxs-lookup"><span data-stu-id="fff1c-394">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="fff1c-395">**Cypress**: RISC-V.</span><span class="sxs-lookup"><span data-stu-id="fff1c-395">**Cypress**: RISC-V</span></span>

<span data-ttu-id="fff1c-396">**EnSilica**: eSi-RISC.</span><span class="sxs-lookup"><span data-stu-id="fff1c-396">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="fff1c-397">**Infineon**: XMC1000, XMC4000, TriCore.</span><span class="sxs-lookup"><span data-stu-id="fff1c-397">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="fff1c-398">**Intel и Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10.</span><span class="sxs-lookup"><span data-stu-id="fff1c-398">**Intel & Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="fff1c-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32.</span><span class="sxs-lookup"><span data-stu-id="fff1c-399">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="fff1c-400">**Microsemi**: RISC-V.</span><span class="sxs-lookup"><span data-stu-id="fff1c-400">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="fff1c-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4.</span><span class="sxs-lookup"><span data-stu-id="fff1c-401">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="fff1c-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy.</span><span class="sxs-lookup"><span data-stu-id="fff1c-402">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="fff1c-403">**Silicon Labs**: EFM32.</span><span class="sxs-lookup"><span data-stu-id="fff1c-403">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="fff1c-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS.</span><span class="sxs-lookup"><span data-stu-id="fff1c-404">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="fff1c-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7.</span><span class="sxs-lookup"><span data-stu-id="fff1c-405">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="fff1c-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C.</span><span class="sxs-lookup"><span data-stu-id="fff1c-406">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="fff1c-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class.</span><span class="sxs-lookup"><span data-stu-id="fff1c-407">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="fff1c-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE.</span><span class="sxs-lookup"><span data-stu-id="fff1c-408">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="fff1c-409">*Все приведенные сведения о времени ожидания и размере могут отличаться в зависимости от платформы разработки.*</span><span class="sxs-lookup"><span data-stu-id="fff1c-409">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>

## <a name="related-services"></a><span data-ttu-id="fff1c-410">Связанные службы</span><span class="sxs-lookup"><span data-stu-id="fff1c-410">Related services</span></span>

<span data-ttu-id="fff1c-411">Модуль безопасности "Центр безопасности Azure для ОСРВ Интернета вещей" предоставляет комплексное решение безопасности для устройств ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="fff1c-411">The Azure Security Center for IoT RTOS security module provides a comprehensive security solution for Azure RTOS devices.</span></span> <span data-ttu-id="fff1c-412">Модуль безопасности для ОСРВ Azure позволяет обнаруживать вредоносные действия в сети, настраивать базовое поведение устройств с учетом оповещений и помогает повысить уровень безопасности устройства.</span><span class="sxs-lookup"><span data-stu-id="fff1c-412">The Security Module for Azure RTOS offers malicious network activity detection, custom alert based device behavior baselining, and helps improve device security hygiene.</span></span> <span data-ttu-id="fff1c-413">Узнайте больше о [модуле безопасности для ОСРВ Azure](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) или изучите краткое руководство по [настройке модуля безопасности для ОСРВ Azure](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module).</span><span class="sxs-lookup"><span data-stu-id="fff1c-413">Learn more about the [Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/iot-security-azure-rtos) or get started with the [Configure Security Module for Azure RTOS](https://docs.microsoft.com/azure/asc-for-iot/quickstart-azure-rtos-security-module) quickstart.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fff1c-414">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="fff1c-414">Next steps</span></span>

<span data-ttu-id="fff1c-415">Чтобы узнать больше о NetX Duo, ознакомьтесь со статьей [Руководство пользователя по NetX Duo для ОСРВ Azure](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="fff1c-415">To learn more about NetX Duo, start with the [Azure RTOS NetX Duo User Guide](about-this-guide.md).</span></span>
