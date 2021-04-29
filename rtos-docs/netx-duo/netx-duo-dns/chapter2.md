---
title: Глава 2. Установка и использование DNS-клиента для NetX Duo в ОСРВ Azure
description: В этой главе описываются разные вопросы, связанные с установкой, настройкой и использованием DNS-клиента для NetX Duo в ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b85829f80462015d66e1623b880d5139349ce0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815387"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dns-client"></a><span data-ttu-id="d46ee-103">Глава 2. Установка и использование DNS-клиента для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="d46ee-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo DNS Client</span></span>

<span data-ttu-id="d46ee-104">В этой главе описываются разные вопросы, связанные с установкой, настройкой и использованием DNS-клиента для NetX Duo в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="d46ee-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="d46ee-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="d46ee-105">Product Distribution</span></span>

<span data-ttu-id="d46ee-106">DNS-клиент NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="d46ee-106">NetX Duo DNS Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="d46ee-107">Этот пакет включает в себя два исходных файла и PDF-файл с этим документом:</span><span class="sxs-lookup"><span data-stu-id="d46ee-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="d46ee-108">**nxd_dns.h**: файл заголовка для DNS-клиента NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="d46ee-108">**nxd_dns.h** Header file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="d46ee-109">**nxd_dns.c**: файл исходного кода C для DNS-клиента NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="d46ee-109">**nxd_dns.c** C Source file for NetX Duo DNS Client</span></span>
- <span data-ttu-id="d46ee-110">**nxd_dns.pdf**: PDF-файл с описанием DNS-клиента NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d46ee-110">**nxd_dns.pdf** PDF description of NetX Duo DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="d46ee-111">Установка DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="d46ee-111">DNS Client Installation</span></span>

<span data-ttu-id="d46ee-112">Чтобы использовать DNS-клиент NetX Duo, скопируйте файлы исходного кода *nxd_dns.c* и *nxd_dns.h* в тот же каталог, где установлен NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d46ee-112">To use NetX Duo DNS Client, copy the source code files *nxd_dns.c* and *nxd_dns.h* to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="d46ee-113">Например, если NetX Duo установлен в каталог *\threadx\arm7\green*, то файлы *nxd_dns.h* и *nxd_dns.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="d46ee-113">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dns.h* and *nxd_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="d46ee-114">Использование DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="d46ee-114">Using the DNS Client</span></span>

<span data-ttu-id="d46ee-115">Использовать DNS-клиент NetX Duo просто.</span><span class="sxs-lookup"><span data-stu-id="d46ee-115">Using NetX Duo DNS Client is easy.</span></span> <span data-ttu-id="d46ee-116">В коде приложения нужно включить файл *nxd_dns.h* после включения *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX Duo соответственно.</span><span class="sxs-lookup"><span data-stu-id="d46ee-116">Basically, the application code must include *nxd_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="d46ee-117">После включения файла *nxd_dns.h* код приложения сможет выполнять вызовы функций DNS, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="d46ee-117">Once *nxd_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="d46ee-118">Приложение также должно включить файл *nxd_dns.c* в процесс сборки.</span><span class="sxs-lookup"><span data-stu-id="d46ee-118">The application must also add *nxd_dns.c* to the build process.</span></span> <span data-ttu-id="d46ee-119">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его объектная форма должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="d46ee-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="d46ee-120">Это все, что необходимо для использования DNS в NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d46ee-120">This is all that is required to use NetX Duo DNS.</span></span>

> [!NOTE]
> <span data-ttu-id="d46ee-121">Так как протокол DNS использует службы NetX Duo UDP, перед использованием DNS следует включить протокол UDP с помощью вызова *nx_udp_enable*.</span><span class="sxs-lookup"><span data-stu-id="d46ee-121">Since DNS utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-netx-duo-dns-client"></a><span data-ttu-id="d46ee-122">Пример небольшой системы для DNS-клиента NetX Duo</span><span class="sxs-lookup"><span data-stu-id="d46ee-122">Small Example System for NetX Duo DNS Client</span></span> 

<span data-ttu-id="d46ee-123">DNS-клиент NetX Duo совместим с существующими приложениями DNS в NetX.</span><span class="sxs-lookup"><span data-stu-id="d46ee-123">NetX Duo DNS Client is compatible with existing NetX DNS applications.</span></span> <span data-ttu-id="d46ee-124">Ниже приведен список устаревших служб и их эквивалентов в NetX Duo:</span><span class="sxs-lookup"><span data-stu-id="d46ee-124">The list of legacy services and their NetX Duo equivalent is shown below:</span></span>

| <span data-ttu-id="d46ee-125">Служба API для DNS в NetX (только IPv4)</span><span class="sxs-lookup"><span data-stu-id="d46ee-125">NetX DNS API service (IPv4 only)</span></span> | <span data-ttu-id="d46ee-126">Служба API для DNS в NetX Duo (поддерживаются IPv4 и IPv6)</span><span class="sxs-lookup"><span data-stu-id="d46ee-126">NetX Duo DNS API service (IPv4 and IPv6 supported)</span></span> |
|----------------------------------|----------------------------------------------------|
| <span data-ttu-id="d46ee-127">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="d46ee-127">nx_dns_host_by_name_get</span></span>          | <span data-ttu-id="d46ee-128">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="d46ee-128">nxd_dns_host_by_name_get</span></span>                           |
| <span data-ttu-id="d46ee-129">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="d46ee-129">nx_dns_host_by_address_get</span></span>       | <span data-ttu-id="d46ee-130">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="d46ee-130">nxd_dns_host_by_address_get</span></span>                        |
| <span data-ttu-id="d46ee-131">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="d46ee-131">nx_dns_server_get</span></span>                | <span data-ttu-id="d46ee-132">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="d46ee-132">nxd_dns_server_get</span></span>                                 |
| <span data-ttu-id="d46ee-133">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="d46ee-133">nx_dns_server_add</span></span>                | <span data-ttu-id="d46ee-134">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="d46ee-134">nxd_dns_server_add</span></span>                                 |
| <span data-ttu-id="d46ee-135">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="d46ee-135">nx_dns_server_remove</span></span>             | <span data-ttu-id="d46ee-136">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="d46ee-136">nxd_dns_server_remove</span></span>                              |

<span data-ttu-id="d46ee-137">Дополнительные сведения см. в описании служб API DNS-клиента в NetX Duo в главе 3.</span><span class="sxs-lookup"><span data-stu-id="d46ee-137">See the description of NetX Duo DNS Client API services in Chapter 3 for more details.</span></span>

<span data-ttu-id="d46ee-138">В примере программы DNS, приведенном в этом разделе, файл *nxd_dns.h* включен в строке 6.</span><span class="sxs-lookup"><span data-stu-id="d46ee-138">In the example DNS application program provided in this section, *nxd_dns.h* is included at line 6.</span></span> <span data-ttu-id="d46ee-139">Параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, который позволяет приложению DNS-клиента создать пул пакетов для DNS-клиента, объявлен в строках 24–26.</span><span class="sxs-lookup"><span data-stu-id="d46ee-139">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 24-26.</span></span> <span data-ttu-id="d46ee-140">Этот пул пакетов используется для выделения пакетов для отправки сообщений DNS.</span><span class="sxs-lookup"><span data-stu-id="d46ee-140">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="d46ee-141">Если параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен, то пул пакетов создается в строках 78–98.</span><span class="sxs-lookup"><span data-stu-id="d46ee-141">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 78-98.</span></span> <span data-ttu-id="d46ee-142">Если этот параметр не включен, то DNS-клиент создает собственный пул пакетов в соответствии с полезными данными пакета и размером пула, заданными параметрами конфигурации в *nxd_dns.h*. Эти параметры описаны в другом разделе этой главы.</span><span class="sxs-lookup"><span data-stu-id="d46ee-142">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nxd_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="d46ee-143">В строках 100–112 создается отдельный пул пакетов для экземпляра IP-адреса клиента, который используется для внутренних операций NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d46ee-143">Another packet pool is created in lines 100-112 for the Client IP instance which is used for internal NetX Duo operations.</span></span> <span data-ttu-id="d46ee-144">Затем создается экземпляр IP-адреса с помощью вызова *nx_ip_create* в строке 115.</span><span class="sxs-lookup"><span data-stu-id="d46ee-144">Next the IP instance is created using the *nx_ip_create* call in line 115.</span></span> <span data-ttu-id="d46ee-145">Задача IP-адреса и DNS-клиент могут использовать один и тот же пул пакетов, но так как DNS-клиент обычно отправляет сообщения большего размера, чем управляющие пакеты, отправляемые задачей IP-адреса, выделение отдельных пулов пакетов позволяет более эффективно использовать память.</span><span class="sxs-lookup"><span data-stu-id="d46ee-145">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="d46ee-146">Протоколы ARP и UDP (используемые сетями IPv4) включены в строках 129 и 141 соответственно.</span><span class="sxs-lookup"><span data-stu-id="d46ee-146">ARP and UDP (which is used by IPv4 networks) are enabled in lines 129 and 141 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="d46ee-147">В этом демонстрационном файле указан драйвер ОЗУ ("ram"), объявленный в строке 44 и используемый в вызове функции *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="d46ee-147">This demo uses the ‘ram’ driver declared on line 44 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="d46ee-148">Этот драйвер ОЗУ предоставляется с исходным кодом NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d46ee-148">This ram driver is distributed with the NetX Duo source code.</span></span> <span data-ttu-id="d46ee-149">Чтобы фактически запустить DNS-клиент, приложение должно предоставить реальный физический сетевой драйвер для передачи и получения пакетов от DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="d46ee-149">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="d46ee-150">Функция входа потока клиента *thread_client_entry* определена под функцией *tx_application_define*.</span><span class="sxs-lookup"><span data-stu-id="d46ee-150">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="d46ee-151">Изначально она передает управление системе, чтобы разрешить инициализацию потока задач IP-адресов сетевым драйвером.</span><span class="sxs-lookup"><span data-stu-id="d46ee-151">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="d46ee-152">Затем она создает DNS-клиент в строке 257, инициализирует кэш DNS в строках 267–278 и задает созданный ранее пул пакетов для экземпляра DNS-клиента в строках 281–295.</span><span class="sxs-lookup"><span data-stu-id="d46ee-152">It then creates the DNS Client in line 257, initializes the DNS cache on lines 267- 278, and sets the packet pool previously created to the DNS Client instance on lines 281-295.</span></span> <span data-ttu-id="d46ee-153">После чего она добавляет DNS-сервер в строках 297–341.</span><span class="sxs-lookup"><span data-stu-id="d46ee-153">It then adds DNS server on lines 297-341.</span></span>

<span data-ttu-id="d46ee-154">Оставшаяся часть примера программы использует службы DNS-клиента для выполнения запросов DNS.</span><span class="sxs-lookup"><span data-stu-id="d46ee-154">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="d46ee-155">Поиск IP-адресов узлов выполняется в строках 193 и 207.</span><span class="sxs-lookup"><span data-stu-id="d46ee-155">Host IP address lookups are performed on lines 193 and 207.</span></span> <span data-ttu-id="d46ee-156">Различие между этими двумя службами *nxd_dns_host_by_name_get* и *nx_dns_host_by_name_get* заключается в том, что первая сохраняет данные об адресе с типом данных NXD_ADDRESS, а вторая — с типом данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="d46ee-156">The difference between these two services, *nxd_dns_host_by_name_get* and *nx_dns_host_by_name_get*, is that the former saves the address data in an NXD_ADDRESS data type, while the latter saves the data in a ULONG data type.</span></span> <span data-ttu-id="d46ee-157">Кроме того, вторая служба ограничена сетями IPv4, тогда как первую можно использовать с сетями IPv6 или IPv4.</span><span class="sxs-lookup"><span data-stu-id="d46ee-157">Further the latter is limited to IPv4 networks, while the former can be used with IPv6 or IPv4 networks.</span></span> <span data-ttu-id="d46ee-158">Это возможно только в том случае, если для экземпляра IP-адреса включен протокол IPv6.</span><span class="sxs-lookup"><span data-stu-id="d46ee-158">This is only possible if the IP instance is enabled for IPv6.</span></span> <span data-ttu-id="d46ee-159">Дополнительные сведения о включении для экземпляра IP-адреса поддержки сетей IPv6 см. в руководстве пользователя по NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="d46ee-159">See the NetX Duo User Guide for more details on enabling the IP instance for IPv6 networking.</span></span>

<span data-ttu-id="d46ee-160">В строке 464 показана другая служба для поиска IP-адресов узла — *nx_dns_ipv4_address_by_name_get*.</span><span class="sxs-lookup"><span data-stu-id="d46ee-160">Another service for host IP address lookups is shown on line 464, *nx_dns_ipv4_address_by_name_get*.</span></span> <span data-ttu-id="d46ee-161">Эта служба отличается от *nx_dns_host_by_name_get* тем, что она возвращает все (или столько, сколько помещается в заданном буфере) IPv4-адреса, обнаруженных для доменного имени, а не только первый адрес, полученный в ответе DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="d46ee-161">This service differs from *nx_dns_host_by_name_get* in that it returns all (or as many will fit in the supplied buffer) of the IPv4 addresses discovered for the domain name, not just the first address received in the DNS Server reply.</span></span>

<span data-ttu-id="d46ee-162">Аналогичным образом, служба *nxd_dns_ipv6_address_by_name_get*, вызываемая в строке 380, возвращает все IPv6-адреса, обнаруженные DNS-клиентом, а не только первый из них.</span><span class="sxs-lookup"><span data-stu-id="d46ee-162">Similarly, the *nxd_dns_ipv6_address_by_name_get* service, called on line 380, returns all the IPv6 addresses discovered by the DNS Client, not just the first one.</span></span>

<span data-ttu-id="d46ee-163">Обратные просмотры (имени узла по IP-адресу) выполняются в строке 606 (*nx_dns_host_by_address_get*) и еще раз в строках 564 и 588 (*nxd_dns_host_by_address_get*).</span><span class="sxs-lookup"><span data-stu-id="d46ee-163">Reverse lookups (host name from IP address) are performed on lines 606 (*nx_dns_host_by_address_get*) and again on line 564 and 588 (*nxd_dns_host_by_address_get*).</span></span> <span data-ttu-id="d46ee-164">Служба *nx_dns_host_by_address_get* будет работать только в сетях IPv4, тогда как *nxd_dns_host_by_address_get* — в сетях IPv4 или IPv6 (то есть для экземпляра IP-адреса включена поддержка как сетей IPv6, так и сетей IPv4).</span><span class="sxs-lookup"><span data-stu-id="d46ee-164">*nx_dns_host_by_address_get* will only work on IPv4 networks, while *nxd_dns_host_by_address_get* will work on either IPv4 or IPv6 networks (e.g. the IP instance is enabled for IPv6 as well as IPv4 networks).</span></span>

<span data-ttu-id="d46ee-165">Две дополнительные службы для поиска DNS, CNAME и TXT, показаны в строках 627 и 649 соответственно. Они используются, чтобы обнаруживать запись CNAME и данные о доменном имени для входного доменного имени.</span><span class="sxs-lookup"><span data-stu-id="d46ee-165">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 627 and 649 respectively, to discover CNAME and domain name data for the input domain name.</span></span> <span data-ttu-id="d46ee-166">DNS-клиент в NetX Duo использует аналогичные службы для других типов записей, например MX, NS, SRV и SOA.</span><span class="sxs-lookup"><span data-stu-id="d46ee-166">NetX Duo DNS Client as similar services for other record types, e.g. MX, NS, SRV and SOA.</span></span> <span data-ttu-id="d46ee-167">Подробное описание поиска всех типов записей, доступных в DNS-клиенте NetX Duo, приведено в главе 3.</span><span class="sxs-lookup"><span data-stu-id="d46ee-167">See Chapter 3 for detailed descriptions of all record type lookups available in NetX Duo DNS Client.</span></span>

<span data-ttu-id="d46ee-168">При удалении DNS-клиента в строке 846 с помощью службы *nx_dns_delete* его пул пакетов не удаляется, если только DNS-клиент не создал собственный пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="d46ee-168">When the DNS Client is deleted on line 846, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="d46ee-169">В противном случае приложение удаляет этот пул пакетов, если он больше не используется.</span><span class="sxs-lookup"><span data-stu-id="d46ee-169">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```C
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack. */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nx_udp.h"
#include   "nxd_dns.h"

#ifdef FEATURE_NX_IPV6
#include   "nx_ipv6.h"
#endif

#define     DEMO_STACK_SIZE         4096

#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS                  client_dns;
TX_THREAD               client_thread;
NX_IP                   client_ip;
NX_PACKET_POOL          main_pool;
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
NX_PACKET_POOL          client_pool;
#endif
UCHAR                   local_cache[LOCAL_CACHE_SIZE];

UINT                    error_counter = 0;

#ifdef FEATURE_NX_IPV6
/* If IPv6 is enabled in NetX Duo, allow DNS Client to try using IPv6 */
//#define USE_IPV6
#endif

#define CLIENT_ADDRESS      IP_ADDRESS(192,168,0,11)
#define DNS_SERVER_ADDRESS  IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */

void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern  VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", thread_client_entry, 0,
            pointer, DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Create the packet pool for the DNS Client to send packets.

        If the DNS Client is configured for letting the host application create
        the DNS packet pool, (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see
       nx_dns_create() for guidelines on packet payload size and pool size.
       packet traffic for NetX processes.
    */
    status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", NX_DNS_PACKET_PAYLOAD, pointer, NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
     /* Create the packet pool which the IP task will use to send packets. Also available to the host
       application to send packet. */
    status =  nx_packet_pool_create(&main_pool, "Main Packet Pool", NX_PACKET_PAYLOAD, pointer, NX_PACKET_POOL_SIZE);

    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", CLIENT_ADDRESS, 0xFFFFFF00UL,
                          &main_pool, _nx_ram_network_driver, pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status =  nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Enable UDP traffic because DNS is a UDP based protocol. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
}

#define BUFFER_SIZE     200
#define RECORD_COUNT    10

/* Define the Client thread. */

void    thread_client_entry(ULONG thread_input)
{

UCHAR           record_buffer[200];
UINT            record_count;
UINT            status;
ULONG           host_ip_address;
#ifdef FEATURE_NX_IPV6
NXD_ADDRESS     host_ipduo_address;
NXD_ADDRESS     test_ipduo_server_address;
#ifdef USE_IPV6
NXD_ADDRESS     client_ipv6_address;
NXD_ADDRESS     dns_ipv6_server_address;
UINT            iface_index, address_index;
#endif
#endif
UINT            i;
ULONG           *ipv4_address_ptr[RECORD_COUNT];
NX_DNS_IPV6_ADDRESS
                *ipv6_address_ptr[RECORD_COUNT];
#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
NX_DNS_NS_ENTRY
                *nx_dns_ns_entry_ptr[RECORD_COUNT];
NX_DNS_MX_ENTRY
                *nx_dns_mx_entry_ptr[RECORD_COUNT];
NX_DNS_SRV_ENTRY
                *nx_dns_srv_entry_ptr[RECORD_COUNT];
NX_DNS_SOA_ENTRY
                *nx_dns_soa_entry_ptr;
ULONG           host_address;
USHORT          host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Make the DNS Client IPv6 enabled. */
    status = nxd_ipv6_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
     }
    status = nxd_icmp_enable(&client_ip);

    /* Check for enable errors. */
    if (status)
    {

        error_counter++;
        return;
    }

    client_ipv6_address.nxd_ip_address.v6[3] = 0x101;
    client_ipv6_address.nxd_ip_address.v6[2] = 0x0;
    client_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;


     /* Set the link local address with the host MAC address. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, &address_index);

    /* Check for link local address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Set the host global IP address. We are assuming a 64
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, &client_ipv6_address, 64, &address_index);

    /* Check for global address set error. */
    if (status)
    {

        error_counter++;
        return;
     }

    /* Wait while NetX Duo validates the link local and global address. */
    tx_thread_sleep(500);
#endif
#endif

    /* Create a DNS instance for the Client. Note this function will create
       the DNS Client packet pool for creating DNS message packets intended
       for querying its DNS server. */
    status =  nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

    /* Check for DNS create error. */
    if (status)
    {

        error_counter++;
        return;
     }

#ifdef NX_DNS_CACHE_ENABLE
    /* Initialize the cache. */
    status = nx_dns_cache_initialize(&client_dns, local_cache, LOCAL_CACHE_SIZE);

    /* Check for DNS cache error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif

    /* Is the DNS client configured for the host application to create the pecket pool? */
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Yes, use the packet pool created above which has appropriate payload size
       for DNS messages. */
     status = nx_dns_packet_pool_set(&client_dns, &client_pool);

     /* Check for set DNS packet pool error. */
     if (status)
     {

         error_counter++;
         return;
      }

#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

#ifdef FEATURE_NX_IPV6
#ifdef USE_IPV6

    /* Add an IPv6 DNS server to the DNS client. */
    dns_ipv6_server_address.nxd_ip_address.v6[3] = 0x106;
    dns_ipv6_server_address.nxd_ip_address.v6[2] = 0x0;
    dns_ipv6_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    dns_ipv6_server_address.nxd_ip_address.v6[0] = 0x20010db8;
    dns_ipv6_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    status = nxd_dns_server_add(&client_dns, &dns_ipv6_server_address);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif
#else

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);

    /* Check for DNS add server error. */
    if (status)
    {

        error_counter++;
        return;
     }
#endif


/********************************************************************************/
/*                                  Type AAAA                                   */
/*     Send AAAA type DNS Query to its DNS server and get the IPv6 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6

    /* Send a DNS Client name query. Indicate the Client expects an IPv6 address (containing an AAAA record). The DNS
       Client will send AAAA type query to its DNS server. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V6);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: \n");

        printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n",
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
            (UINT)host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
    }

#endif

    /* Look up IPv6 addresses(AAAA TYPE) to record multiple IPv6 addresses in record_buffer and return the IPv6 address count. */
    status = nxd_dns_ipv6_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test AAAA: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv6_address_ptr[i] = (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS));

        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i,
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF),
                (UINT)(ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF));
    }


/********************************************************************************/
/*                                  Type A                                      */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
#ifdef FEATURE_NX_IPV6
    /* Send a DNS Client name query. Indicate the Client expects an IPv4 address (containing an A record). If the DNS client
       is using an IPv6 DNS server it will send this query over IPv6; otherwise it will be sent over IPv4. */
    status = nxd_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ipduo_address, 400, NX_IP_VERSION_V4);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
              host_ipduo_address.nxd_ip_address.v4 >> 24,
              host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
              host_ipduo_address.nxd_ip_address.v4 & 0xFF);
    }

#endif

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }


/********************************************************************************/
/*                                  Type A + CNAME response                     */
/*       Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }


    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test Test A + CNAME response: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }


/********************************************************************************/
/*                                  Type PTR                                    */
/*       Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

#ifdef FEATURE_NX_IPV6

    /* Look up a host name from an IPv6 address (reverse lookup). */

    /* Create an IPv6 address for a reverse lookup. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V6;
    test_ipduo_server_address.nxd_ip_address.v6[0] = 0x24046800;
    test_ipduo_server_address.nxd_ip_address.v6[1] = 0x40050c00;
    test_ipduo_server_address.nxd_ip_address.v6[2] = 0x00000000;
    test_ipduo_server_address.nxd_ip_address.v6[3] = 0x00000065;

    /* This will be sent over IPv6 to the DNS server who should return a PTR record if it can find the information. */
    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }
#endif

#ifdef FEATURE_NX_IPV6

    /* Create an IPv4 address for the reverse lookup. If the DNS client is IPv6 enabled, it will send this over
       IPv6 to the DNS server; otherwise it will send it over IPv4. In either case the respective server will
       return a PTR record if it has the information. */
    test_ipduo_server_address.nxd_ip_version = NX_IP_VERSION_V4;
    test_ipduo_server_address.nxd_ip_address.v4 = IP_ADDRESS(74, 125, 71, 106);

    status = nxd_dns_host_by_address_get(&client_dns, &test_ipduo_server_address, &record_buffer[0], BUFFER_SIZE, 450);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }
#endif

     /* Look up host name over IPv4. */
     host_ip_address = IP_ADDRESS(74, 125, 71, 106);
     status = nx_dns_host_by_address_get(&client_dns, host_ip_address, &record_buffer[0], BUFFER_SIZE, 450);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {
        printf("------------------------------------------------------\n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/*                                  Type CNAME                                  */
/*   Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

     /* Send CNAME type to record the canonical name of host in record_buffer. */
     status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test CNAME: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type TXT                                    */
/*      Send TXT type DNS Query to its DNS server and get descriptive text. */
/********************************************************************************/

     /* Send TXT type to record the descriptive test of host in record_buffer. */
     status = nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test TXT: %s\n", record_buffer);
    }


/********************************************************************************/
/*                                  Type NS                                     */
/*   Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

     /* Send NS type to record multiple name servers in record_buffer and return the name server count.
        If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */
     status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type MX                                     */
/*   Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

     /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count.
        If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */
     status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test MX: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);
        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);
        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/*                                  Type SRV                                    */
/*  Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

     /* Send SRV DNS query type to record the location of services in record_buffer and return count.
        If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */
     status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, &record_count, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);
    }

    /* Get the location of services. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY));

        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);
        printf("port number = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
        printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
        printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );
        if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
            printf("hostname = %s\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

    /* Get the service info, NetX old API.*/
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_address, &host_port, 200);

    /* Check for DNS add server error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

    else
    {

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }

/********************************************************************************/
/*                                  Type SOA                                    */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

     /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */
     status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);

     /* Check for DNS query error. */
     if (status != NX_SUCCESS)
     {
         error_counter++;
     }

     /* Get the loc*/
     nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
     printf("------------------------------------------------------\n");
     printf("Test SOA: \n");
     printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
     printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
     printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
     printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
     printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
     if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
         printf("host mname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
     else
         printf("host mame is not set\n");
     if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
         printf("host rname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
     else
         printf("host rname is not set\n");


#endif

    /* Shutting down...*/

    /* Terminate the DNS Client thread. */
    status = nx_dns_delete(&client_dns);

    return;
}
```
## <a name="configuration-options"></a><span data-ttu-id="d46ee-170">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="d46ee-170">Configuration Options</span></span>

<span data-ttu-id="d46ee-171">Существует ряд параметров конфигурации для создания DNS для NetX.</span><span class="sxs-lookup"><span data-stu-id="d46ee-171">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="d46ee-172">Эти параметры можно переопределить в файле *nxd_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="d46ee-172">These options can be redefined in *nxd_dns.h.*</span></span> <span data-ttu-id="d46ee-173">Их подробное описание приводится ниже:</span><span class="sxs-lookup"><span data-stu-id="d46ee-173">The following list describes each in detail:</span></span>  

- <span data-ttu-id="d46ee-174">**NX_DNS_TYPE_OF_SERVICE**: тип службы, необходимый для UDP-запросов DNS.</span><span class="sxs-lookup"><span data-stu-id="d46ee-174">**NX_DNS_TYPE_OF_SERVICE** Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="d46ee-175">По умолчанию для этого параметра определено значение NX_IP_NORMAL, указывающее обычную службу IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d46ee-175">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="d46ee-176">**NX_DNS_TIME_TO_LIVE**: указывает максимальное число маршрутизаторов, через которые может пройти пакет, прежде чем он будет удален.</span><span class="sxs-lookup"><span data-stu-id="d46ee-176">**NX_DNS_TIME_TO_LIVE** Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="d46ee-177">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="d46ee-177">The default value is 0x80.</span></span>

- <span data-ttu-id="d46ee-178">**NX_DNS_FRAGMENT_OPTION**: устанавливает свойство сокета, чтобы разрешить или запретить фрагментацию исходящих пакетов.</span><span class="sxs-lookup"><span data-stu-id="d46ee-178">**NX_DNS_FRAGMENT_OPTION** Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="d46ee-179">По умолчанию имеет значение NX_DONT_FRAGMENT.</span><span class="sxs-lookup"><span data-stu-id="d46ee-179">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="d46ee-180">**NX_DNS_QUEUE_DEPTH**: задает максимальное число пакетов, сохраняемых в очереди получения сокета.</span><span class="sxs-lookup"><span data-stu-id="d46ee-180">**NX_DNS_QUEUE_DEPTH** Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="d46ee-181">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="d46ee-181">The default value is 5.</span></span>

- <span data-ttu-id="d46ee-182">**NX_DNS_MAX_SERVERS**: указывает максимальное число DNS-серверов в списке серверов клиента.</span><span class="sxs-lookup"><span data-stu-id="d46ee-182">**NX_DNS_MAX_SERVERS** Specifies the maximum number of DNS Servers in the Client server list.</span></span> <span data-ttu-id="d46ee-183">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="d46ee-183">The default value is 5.</span></span>

- <span data-ttu-id="d46ee-184">**NX_DNS_MESSAGE_MAX**: максимальный размер сообщения DNS для отправки запросов DNS.</span><span class="sxs-lookup"><span data-stu-id="d46ee-184">**NX_DNS_MESSAGE_MAX** The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="d46ee-185">Значение по умолчанию — 512, которое также является максимальным размером, указанным в разделе 2.3.4 документа RFC 1035.</span><span class="sxs-lookup"><span data-stu-id="d46ee-185">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="d46ee-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: если этот параметр не определен, то размер полезных данных пакета клиента (включая заголовки Ethernet, IP (или IPv6) и UDP), а также максимальный размер сообщения DNS задает параметр NX_DNS_MESSAGE_MAX.</span><span class="sxs-lookup"><span data-stu-id="d46ee-186">**NX_DNS_PACKET_PAYLOAD_UNALIGNED** If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="d46ee-187">Независимо от того, определен ли этот параметр, для полезных данных пакета выделяется буфер в 4 байта и они определяются параметром NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="d46ee-187">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="d46ee-188">**NX_DNS_PACKET_POOL_SIZE**: размер пула пакетов клиента для отправки запросов DNS, если параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL не определен.</span><span class="sxs-lookup"><span data-stu-id="d46ee-188">**NX_DNS_PACKET_POOL_SIZE** Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="d46ee-189">Значение по умолчанию достаточно велико для 16 пакетов размера полезных данных (который определяет параметр NX_DNS_PACKET_PAYLOAD) с учетом буфера в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="d46ee-189">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="d46ee-190">**NX_DNS_MAX_RETRIES**: максимальное число запросов DNS-клиента, отправляемых на текущий DNS-сервер, перед попыткой подключиться к другому серверу или прерыванием запроса DNS.</span><span class="sxs-lookup"><span data-stu-id="d46ee-190">**NX_DNS_MAX_RETRIES** The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span> <span data-ttu-id="d46ee-191">Значение по умолчанию равно 3.</span><span class="sxs-lookup"><span data-stu-id="d46ee-191">The default value is 3.</span></span>

- <span data-ttu-id="d46ee-192">**NX_DNS_MAX_RETRANS_TIMEOUT**: максимальное время ожидания повторной отправки запроса DNS на конкретный DNS-сервер.</span><span class="sxs-lookup"><span data-stu-id="d46ee-192">**NX_DNS_MAX_RETRANS_TIMEOUT** The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="d46ee-193">Значение по умолчанию — 64 секунды (64 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="d46ee-193">The default value is 64 seconds (64 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="d46ee-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: если этот параметр определен и адрес шлюза IPv4 клиента не равен нулю, DNS-клиент устанавливает шлюз IPv4 в качестве своего основного DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="d46ee-194">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER** If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="d46ee-195">По умолчанию эта политика отключена.</span><span class="sxs-lookup"><span data-stu-id="d46ee-195">The default value is disabled.</span></span>

- <span data-ttu-id="d46ee-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: задает параметр времени ожидания для выделения пакета из пула пакетов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="d46ee-196">**NX_DNS_PACKET_ALLOCATE_TIMEOUT** This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="d46ee-197">Значение по умолчанию — 1 секунда (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="d46ee-197">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="d46ee-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: этот параметр позволяет DNS-клиенту разрешить приложению создать и настроить пул пакетов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="d46ee-198">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="d46ee-199">По умолчанию этот параметр отключен, и DNS-клиент создает собственный пул пакетов с помощью *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="d46ee-199">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="d46ee-200">**NX_DNS_CLIENT_CLEAR_QUEUE**: этот параметр позволяет DNS-клиенту удалить старые сообщения DNS из очереди получения перед отправкой нового запроса.</span><span class="sxs-lookup"><span data-stu-id="d46ee-200">**NX_DNS_CLIENT_CLEAR_QUEUE** This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="d46ee-201">Удаление пакетов от предыдущих запросов DNS предотвращает переполнение очереди сокета DNS-клиента и удаление допустимых пакетов.</span><span class="sxs-lookup"><span data-stu-id="d46ee-201">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="d46ee-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: этот параметр позволяет DNS-клиенту запрашивать дополнительные типы записей DNS (например, CNAME, NS, MX, SOA, SRV и TXT).</span><span class="sxs-lookup"><span data-stu-id="d46ee-202">**NX_DNS_ENABLE_EXTENDED_RR_TYPES** This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="d46ee-203">**NX_DNS_CACHE_ENABLE**: этот параметр позволяет DNS-клиенту хранить записи ответов в кэше DNS.</span><span class="sxs-lookup"><span data-stu-id="d46ee-203">**NX_DNS_CACHE_ENABLE** This enables the DNS Client to store the answer records into DNS cache.</span></span>