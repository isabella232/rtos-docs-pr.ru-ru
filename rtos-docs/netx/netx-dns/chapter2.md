---
title: Глава 2. Установка и использование клиента ОСРВ Azure NetX DNS
description: В этой главе описываются разные вопросы, связанные с установкой, настройкой и использованием клиента ОСРВ Azure NetX DNS.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 054b7366eb9a28bc0dc2fb8c4b2479c12532499b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815223"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a><span data-ttu-id="e2a0f-103">Глава 2. Установка и использование клиента ОСРВ Azure NetX DNS</span><span class="sxs-lookup"><span data-stu-id="e2a0f-103">Chapter 2 - Installation and Use of Azure RTOS NetX DNS Client</span></span>

<span data-ttu-id="e2a0f-104">В этой главе описываются разные вопросы, связанные с установкой, настройкой и использованием клиента ОСРВ Azure NetX DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DNS Client.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="e2a0f-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="e2a0f-105">Product Distribution</span></span>

<span data-ttu-id="e2a0f-106">Клиент NetX DNS доступен по адресу <https://github.com/azure-rtos/netx>.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-106">The NetX DNS Client is available at <https://github.com/azure-rtos/netx>.</span></span> <span data-ttu-id="e2a0f-107">В состав пакета входят следующие файлы:</span><span class="sxs-lookup"><span data-stu-id="e2a0f-107">The package includes the following files:</span></span>

- <span data-ttu-id="e2a0f-108">**nx_dns.h**: файл заголовка для клиента NetX DNS;</span><span class="sxs-lookup"><span data-stu-id="e2a0f-108">**nx_dns.h**: Header file for NetX DNS Client</span></span>
- <span data-ttu-id="e2a0f-109">**nx_dns.c**: файл исходного кода C для клиента NetX DNS;</span><span class="sxs-lookup"><span data-stu-id="e2a0f-109">**nx_dns.c**: C Source file for NetX DNS Client</span></span>
- <span data-ttu-id="e2a0f-110">**nx_dns.pdf**: PDF-файл с описанием клиента NetX DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-110">**nx_dns.pdf**: PDF description of NetX DNS Client</span></span>

## <a name="dns-client-installation"></a><span data-ttu-id="e2a0f-111">Установка DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="e2a0f-111">DNS Client Installation</span></span>

<span data-ttu-id="e2a0f-112">Чтобы использовать клиент NetX DNS, скопируйте файлы исходного кода *nx_dns.c* и *nx_dns.h* в тот же каталог, где установлен экземпляр NetX.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-112">To use NetX DNS Client, copy the source code files *nx_dns.c* and *nx_dns.h* to the same directory where NetX is installed.</span></span> <span data-ttu-id="e2a0f-113">Например, если экземпляр NetX установлен в каталог *\threadx\arm7\green*, то файлы *nx_dns.h* и *nx_dns.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-113">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dns.h* and *nx_dns.c* files should be copied into this directory.</span></span>

## <a name="using-the-dns-client"></a><span data-ttu-id="e2a0f-114">Использование DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="e2a0f-114">Using the DNS Client</span></span>

<span data-ttu-id="e2a0f-115">Использовать клиент NetX DNS просто.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-115">Using NetX DNS Client is easy.</span></span> <span data-ttu-id="e2a0f-116">В код приложения следует добавить *nx_dns.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-116">Basically, the application code must include *nx_dns.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="e2a0f-117">После включения файла *nx_dns.h* код приложения сможет выполнять вызовы функций DNS, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-117">Once *nx_dns.h* is included, the application code is then able to make the DNS function calls specified later in this guide.</span></span> <span data-ttu-id="e2a0f-118">Приложение также должно включить файл *nx_dns.c* для процесса сборки.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-118">The application must also add *nx_dns.c* to the build process.</span></span> <span data-ttu-id="e2a0f-119">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-119">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="e2a0f-120">Это все, что необходимо для использования NetX DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-120">This is all that is required to use NetX DNS.</span></span>

>[!NOTE]
> <span data-ttu-id="e2a0f-121">Так как протокол DNS использует службы NetX UDP, перед использованием DNS следует включить протокол UDP с помощью вызова *nx_udp_enable*.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-121">Since DNS utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DNS.</span></span>

## <a name="small-example-system-for-dns-client"></a><span data-ttu-id="e2a0f-122">Пример небольшой системы для DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="e2a0f-122">Small Example System for DNS Client</span></span> 

<span data-ttu-id="e2a0f-123">В примере программы DNS, приведенном в этом разделе, файл *nx_dns.h* включен в строке 6.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-123">In the example DNS application program provided in this section, *nx_dns.h* is included at line 6.</span></span> <span data-ttu-id="e2a0f-124">Параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, который позволяет приложению DNS-клиента создать пул пакетов для DNS-клиента, объявлен в строках 21–23.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-124">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL, which allows the DNS Client application to create the packet pool for the DNS Client, is declared on lines 21-23.</span></span> <span data-ttu-id="e2a0f-125">Этот пул пакетов используется для выделения пакетов для отправки сообщений DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-125">This packet pool is used for allocating packets for sending DNS messages.</span></span> <span data-ttu-id="e2a0f-126">Если параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен, то пул пакетов создается в строках 71–91.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-126">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined, a packet pool is created in lines 71-91.</span></span> <span data-ttu-id="e2a0f-127">Если этот параметр не включен, то DNS-клиент создает собственный пул пакетов в соответствии с полезными данными пакета и размером пула, заданными параметрами конфигурации в *nx_dns.h*. Эти параметры описаны в другом разделе этой главы.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-127">If this option is not enabled, the DNS Client creates its own packet pool as per the packet payload and pool size set by configuration parameters in *nx_dns.h* and described elsewhere in this chapter.</span></span>

<span data-ttu-id="e2a0f-128">В строках 93–105 создается отдельный пул пакетов для экземпляра IP клиента, который используется для внутренних операций NetX.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-128">Another packet pool is created in lines 93-105 for the Client IP instance which is used for internal NetX operations.</span></span> <span data-ttu-id="e2a0f-129">Затем создается экземпляр IP с помощью вызова *nx_ip_create* в строках 107–119.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-129">Next the IP instance is created using the *nx_ip_create* call in line 107-119.</span></span> <span data-ttu-id="e2a0f-130">Задача IP и DNS-клиент могут использовать один и тот же пул пакетов, но так как DNS-клиент обычно отправляет сообщения большего размера, чем управляющие пакеты, отправляемые задачей IP, выделение отдельных пулов пакетов позволяет более эффективно использовать память.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-130">It is possible for the IP task and the DNS Client to share the same packet pool, but since the DNS Client typically sends out larger messages than the control packets sent by the IP task, using separate packet pools makes more efficient use of memory.</span></span>

<span data-ttu-id="e2a0f-131">Протоколы ARP и UDP (используемые сетями IPv4) включены в строках 122 и 134 соответственно.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-131">ARP and UDP (which is used by IPv4 networks) are enabled in lines 122 and 134 respectively.</span></span>

>[!NOTE]
> <span data-ttu-id="e2a0f-132">В этом демонстрационном файле указан драйвер ОЗУ, объявленный в строке 37 и используемый в вызове функции *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-132">This demo uses the ‘ram’ driver declared on line 37 and used in the *nx_ip_create* call.</span></span> <span data-ttu-id="e2a0f-133">Этот драйвер ОЗУ предоставляется с исходным кодом NetX.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-133">This ram driver is distributed with the NetX source code.</span></span> <span data-ttu-id="e2a0f-134">Чтобы фактически запустить DNS-клиент, приложение должно предоставить реальный физический сетевой драйвер для передачи и получения пакетов от DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-134">To actually run the DNS Client the application must supply an actual physical network driver to transmit and receive packets from the DNS server.</span></span>

<span data-ttu-id="e2a0f-135">Функция входа потока клиента *thread_client_entry* определена под функцией *tx_application_define*.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-135">The Client thread entry function *thread_client_entry* is defined below the *tx_application_define* function.</span></span> <span data-ttu-id="e2a0f-136">Изначально она передает управление системе, чтобы разрешить инициализацию потока задач IP сетевым драйвером.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-136">It initially relinquishes control to the system to allow the IP task thread to be initialized by the network driver.</span></span>

<span data-ttu-id="e2a0f-137">Затем она создает DNS-клиент в строках 176–187, инициализирует кэш в строках 189–200 и задает созданный ранее пул пакетов для экземпляра DNS-клиента в строках 202–217.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-137">It then creates the DNS Client on lines 176-187, initializes the cache on lines 189-200, and sets the packet pool previously created to the DNS Client instance on lines 202-217.</span></span> <span data-ttu-id="e2a0f-138">После чего она добавляет DNS-сервер IPv4 в строках 220–229.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-138">It then adds an IPv4 DNS server on lines 220-229.</span></span>

<span data-ttu-id="e2a0f-139">Оставшаяся часть примера программы использует службы DNS-клиента для выполнения запросов DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-139">The remainder of the example program uses the DNS Client services to make DNS queries.</span></span> <span data-ttu-id="e2a0f-140">Поиск IP-адресов узлов выполняется в строках 240 и 262.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-140">Host IP address lookups are performed on lines 240 and 262.</span></span> <span data-ttu-id="e2a0f-141">Различие между службами *nx_dns_host_by_name_get* и *nx_dns_ipv4_address_by_name_get* заключается в том, что первая сохраняет только один IP-адрес, тогда как вторая сохраняет несколько адресов, если DNS-сервер ответил.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-141">The difference between these two services, *nx_dns_host_by_name_get* and *nx_dns_ipv4_address_by_name_get*, is that the former only saves one IP address, while the latter saves multiple addresses if DNS Server replied.</span></span>

<span data-ttu-id="e2a0f-142">Обратный поиск (имени узла по IP-адресу) выполняется в строке 354 (*nx_dns_host_by_address_get*).</span><span class="sxs-lookup"><span data-stu-id="e2a0f-142">Reverse lookups (host name from IP address) are performed on lines 354 (*nx_dns_host_by_address_get*).</span></span>

<span data-ttu-id="e2a0f-143">Две дополнительные службы для поиска DNS, CNAME и TXT, показаны в строках 375 и 420 соответственно. Они используются, чтобы обнаруживать записи CNAME и TXT для входного доменного имени.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-143">Two more services for DNS lookups, CNAME and TXT, are demonstrated on lines 375 and 420 respectively, to discover CNAME and TXT for the input domain name.</span></span> <span data-ttu-id="e2a0f-144">Клиент NetX DNS использует аналогичные службы для других типов записей, например NS, MX, SRV и SOA.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-144">NetX DNS Client as similar services for other record types, e.g. NS, MX, SRV and SOA.</span></span> <span data-ttu-id="e2a0f-145">Подробное описание поиска всех типов записей, доступных в клиенте NetX DNS, приведено в главе 3.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-145">See Chapter 3 for detailed descriptions of all record type lookups available in NetX DNS Client.</span></span>

<span data-ttu-id="e2a0f-146">При удалении DNS-клиента в строке 594 с помощью службы *nx_dns_delete* пул пакетов этого DNS-клиента не удаляется, если только он не создал собственный пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-146">When the DNS Client is deleted on line 594, using the *nx_dns_delete* service, the packet pool for the DNS Client is not deleted unless the DNS Client created its own packet pool.</span></span> <span data-ttu-id="e2a0f-147">В противном случае приложение удаляет этот пул пакетов, если он больше не используется.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-147">Otherwise, it is up to the application to delete the packet pool if it has no further use for it.</span></span>

```c
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack.*/
#include "tx_api.h"
#include "nx_api.h"
#include "nx_udp.h"
#include "nx_dns.h"

#define     DEMO_STACK_SIZE         4096
#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS             client_dns;
TX_THREAD          client_thread;
NX_IP              client_ip;
NX_PACKET_POOL     main_pool;

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
    NX_PACKET_POOL client_pool;
#endif

UCHAR       local_cache[LOCAL_CACHE_SIZE];
UINT        error_counter = 0;
#define     CLIENT_ADDRESS IP_ADDRESS(192,168,0,11)
#define     DNS_SERVER_ADDRESS IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */
void        thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern     VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */
int main()
{
/* Enter the ThreadX kernel. */
    tx_kernel_enter();
}
/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    CHAR     *pointer;
    UINT     status;
    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;
    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", 
                     thread_client_entry, 0, pointer, 
                     DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, 
                     TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /*Create the packet pool for the DNS Client to send packets. If the DNS Client is configured for letting the host application create the DNS packet pool, 
        (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see 77 nx_dns_create() for guidelines on packet payload size and pool size. 
        packet traffic for NetX processes.
    */

    status = nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                   NX_DNS_PACKET_PAYLOAD, pointer, 
                                   NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;
    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

#endif
/* Create the packet pool which the IP task will use to send packets. Also available to the host 94 application to send packet. */

    status = nx_packet_pool_create(&main_pool, "Main Packet Pool", 
                                   NX_PACKET_PAYLOAD, pointer, 
                                   NX_PACKET_POOL_SIZE);
    pointer = pointer + NX_PACKET_POOL_SIZE;

/* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

/* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", 
                          CLIENT_ADDRESS, 0xFFFFFF00UL, 
                          &main_pool, _nx_ram_network_driver, 
                          pointer, 2048, 1);
    pointer = pointer + 2048;

/* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status = nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

/* Check for ARP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable UDP traffic because DNS is a UDP based protocol. */

    status = nx_udp_enable(&client_ip);
/* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

}

#define BUFFER_SIZE 200
#define RECORD_COUNT 10

/* Define the Client thread. */
void thread_client_entry(ULONG thread_input)
{
    UCHAR         record_buffer[200];
    UINT          record_count;
    UINT          status;
    ULONG         host_ip_address;
    UINT          i;
    ULONG         *ipv4_address_ptr[RECORD_COUNT];

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
    NX_DNS_NS_ENTRY    *nx_dns_ns_entry_ptr[RECORD_COUNT];
    NX_DNS_MX_ENTRY    *nx_dns_mx_entry_ptr[RECORD_COUNT];
    NX_DNS_SRV_ENTRY    *nx_dns_srv_entry_ptr[RECORD_COUNT];
    NX_DNS_SOA_ENTRY    *nx_dns_soa_entry_ptr;
    ULONG                host_address;
    USHORT               host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);
    /* Create a DNS instance for the Client. Note this function will create the DNS Client packet pool for creating DNS message packets intended for querying its DNS server. */
    status = nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

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

    /* Yes, use the packet pool created above which has appropriate payload size for DNS messages. */
    status = nx_dns_packet_pool_set(&client_dns, &client_pool);
    /* Check for set DNS packet pool error. */
        
    if (status)
    {
        error_counter++;
        return;
    }
#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);
    /* Check for DNS add server error. */
    if (status)
    {
        error_counter++;
        return;
    }
/********************************************************************************/
/* Type A */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
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
        printf("------------------------------------------------------> n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }
    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
/* Type A + CNAME response */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
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
        printf("------------------------------------------------------> n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }

    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 
                                             &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
/* Type PTR */
/* Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

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
        printf("------------------------------------------------------> n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/* Type CNAME */
/* Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

    /* Send CNAME type to record the canonical name of host in record_buffer. */

    status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", 
                              &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test CNAME: %s\n", record_buffer);
    }
/********************************************************************************/
/* Type TXT */
/* Send TXT type DNS Query to its DNS server and get descriptive text. */
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
        printf("------------------------------------------------------> n");
        printf("Test TXT: %s\n", record_buffer);
    }

/********************************************************************************/
/* Type NS */
/* Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

    /* Send NS type to record multiple name servers in record_buffer and return the name server count. If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */

    status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                           &record_buffer[0], BUFFER_SIZE, 
                                           &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/* Type MX */
/* Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

    /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count. If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */

    status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
/* Type SRV */
/* Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

    /* Send SRV DNS query type to record the location of services in record_buffer and return count. If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */

    status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                       &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
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
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                     &host_address, &host_port, 200);
    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }
    
/********************************************************************************/
/* Type SOA */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

    /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */

    status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    
    /* Get the loc*/
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    printf("------------------------------------------------------> n");
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

## <a name="configuration-options"></a><span data-ttu-id="e2a0f-148">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="e2a0f-148">Configuration Options</span></span>

<span data-ttu-id="e2a0f-149">Существует ряд параметров конфигурации для сборки DNS для NetX.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-149">There are several configuration options for building DNS for NetX.</span></span> <span data-ttu-id="e2a0f-150">Эти параметры можно переопределить в файле *nx_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-150">These options can be redefined in *nx_dns.h.*</span></span> <span data-ttu-id="e2a0f-151">Их подробное описание приведено ниже.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-151">The following list describes each in detail:</span></span>  

- <span data-ttu-id="e2a0f-152">**NX_DNS_TYPE_OF_SERVICE**: тип службы, необходимый для UDP-запросов DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-152">**NX_DNS_TYPE_OF_SERVICE**: Type of service required for the DNS UDP requests.</span></span> <span data-ttu-id="e2a0f-153">По умолчанию для этого параметра определено значение NX_IP_NORMAL, указывающее обычную службу IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-153">By default, this value is defined as NX_IP_NORMAL for normal IP packet service.</span></span>

- <span data-ttu-id="e2a0f-154">**NX_DNS_TIME_TO_LIVE**: указывает максимальное число маршрутизаторов, через которые может пройти пакет, прежде чем он будет удален.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-154">**NX_DNS_TIME_TO_LIVE**: Specifies the maximum number of routers a packet can pass before it is discarded.</span></span> <span data-ttu-id="e2a0f-155">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-155">The default value is 0x80</span></span>

- <span data-ttu-id="e2a0f-156">**NX_DNS_FRAGMENT_OPTION**: устанавливает свойство сокета, чтобы разрешить или запретить фрагментирование исходящих пакетов.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-156">**NX_DNS_FRAGMENT_OPTION**: Sets the socket property to allow or disallow fragmentation of outgoing packets.</span></span> <span data-ttu-id="e2a0f-157">По умолчанию имеет значение NX_DONT_FRAGMENT.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-157">The default value is NX_DONT_FRAGMENT.</span></span>

- <span data-ttu-id="e2a0f-158">**NX_DNS_QUEUE_DEPTH**: задает максимальное число пакетов, сохраняемых в очереди получения сокета.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-158">**NX_DNS_QUEUE_DEPTH**: Sets the maximum number of packets to store on the socket receive queue.</span></span> <span data-ttu-id="e2a0f-159">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-159">The default value is 5.</span></span>

- <span data-ttu-id="e2a0f-160">**NX_DNS_MAX_SERVERS**: указывает максимальное число DNS-серверов в списке серверов клиента.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-160">**NX_DNS_MAX_SERVERS**: Specifies the maximum number of DNS Servers in the Client server list.</span></span>

- <span data-ttu-id="e2a0f-161">**NX_DNS_MESSAGE_MAX**: максимальный размер сообщения DNS для отправки запросов DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-161">**NX_DNS_MESSAGE_MAX**: The maximum DNS message size for sending DNS queries.</span></span> <span data-ttu-id="e2a0f-162">Значение по умолчанию — 512, которое также является максимальным размером, указанным в разделе 2.3.4 RFC 1035.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-162">The default value is 512, which is also the maximum size specified in RFC 1035 Section 2.3.4.</span></span>

- <span data-ttu-id="e2a0f-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: если этот параметр не определен, то размер полезных данных пакета клиента (включая заголовки Ethernet, IP (или IPv6) и UDP), а также максимальный размер сообщения DNS задает параметр NX_DNS_MESSAGE_MAX.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-163">**NX_DNS_PACKET_PAYLOAD_UNALIGNED**: If not defined, the size of the Client packet payload which includes the Ethernet, IP (or IPv6), and UDP headers plus the maximum DNS message size specified by NX_DNS_MESSAGE_MAX.</span></span> <span data-ttu-id="e2a0f-164">Независимо от того, определен ли этот параметр, для полезных данных пакета выделяется буфер в 4 байта и они определяются параметром NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-164">Regardless if defined, the packet payload is the 4-byte aligned and stored in NX_DNS_PACKET_PAYLOAD.</span></span>

- <span data-ttu-id="e2a0f-165">**NX_DNS_PACKET_POOL_SIZE**: размер пула пакетов клиента для отправки запросов DNS, если параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL не определен.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-165">**NX_DNS_PACKET_POOL_SIZE**: Size of the Client packet pool for sending DNS queries if NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is not defined.</span></span> <span data-ttu-id="e2a0f-166">Значение по умолчанию достаточно велико для 16 пакетов размера полезных данных (который определяет параметр NX_DNS_PACKET_PAYLOAD) с учетом буфера в 4 байта.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-166">The default value is large enough for 16 packets of payload size defined by NX_DNS_PACKET_PAYLOAD, and is 4-byte aligned.</span></span>

- <span data-ttu-id="e2a0f-167">**NX_DNS_MAX_RETRIES**: максимальное число запросов DNS-клиента, отправляемых на текущий DNS-сервер, перед попыткой подключиться к другому серверу или прерыванием запроса DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-167">**NX_DNS_MAX_RETRIES**: The maximum number of times the DNS Client will query the current DNS server before trying another server or aborting the DNS query.</span></span>

- <span data-ttu-id="e2a0f-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: максимальное время ожидания повторной отправки запроса DNS на конкретный DNS-сервер.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-168">**NX_DNS_MAX_RETRANS_TIMEOUT**: The maximum retransmission timeout on a DNS query to a specific DNS server.</span></span> <span data-ttu-id="e2a0f-169">Значение по умолчанию — 64 секунды (64 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="e2a0f-169">The default value is 64 seconds (64 \*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="e2a0f-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: если этот параметр определен и адрес шлюза IPv4 клиента не равен нулю, DNS-клиент устанавливает шлюз IPv4 в качестве своего основного DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-170">**NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: If defined and the Client IPv4 gateway address is non zero, the DNS Client sets the IPv4 gateway as the Client’s primary DNS server.</span></span> <span data-ttu-id="e2a0f-171">По умолчанию эта политика отключена.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-171">The default value is disabled.</span></span>

- <span data-ttu-id="e2a0f-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: задает параметр времени ожидания для выделения пакета из пула пакетов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-172">**NX_DNS_PACKET_ALLOCATE_TIMEOUT**: This sets the timeout option for allocating a packet from the DNS client packet pool.</span></span> <span data-ttu-id="e2a0f-173">Значение по умолчанию — 1 секунда (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="e2a0f-173">The default value is 1 second (1\*NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="e2a0f-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: этот параметр позволяет DNS-клиенту разрешить приложению создать и настроить пул пакетов DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-174">**NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: This enables the DNS Client to let the application create and set the DNS Client packet pool.</span></span> <span data-ttu-id="e2a0f-175">По умолчанию этот параметр отключен и DNS-клиент создает собственный пул пакетов с помощью *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-175">By default this option is disabled, and the DNS Client creates its own packet pool in *nx_dns_create*.</span></span>

- <span data-ttu-id="e2a0f-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: этот параметр позволяет DNS-клиенту удалить старые сообщения DNS из очереди получения перед отправкой нового запроса.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-176">**NX_DNS_CLIENT_CLEAR_QUEUE**: This enables the DNS Client to clear old DNS messages off the receive queue before sending a new query.</span></span> <span data-ttu-id="e2a0f-177">Удаление пакетов от предыдущих запросов DNS предотвращает переполнение очереди сокета DNS-клиента и удаление допустимых пакетов.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-177">Removing these packets from previous DNS queries prevents the DNS Client socket queue from overflowing and dropping valid packets.</span></span>

- <span data-ttu-id="e2a0f-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: этот параметр позволяет DNS-клиенту запрашивать дополнительные типы записей DNS (например, CNAME, NS, MX, SOA, SRV и TXT).</span><span class="sxs-lookup"><span data-stu-id="e2a0f-178">**NX_DNS_ENABLE_EXTENDED_RR_TYPES**: This enables the DNS Client to query on additional DNS record types in (e.g. CNAME, NS, MX, SOA, SRV and TXT).</span></span>

- <span data-ttu-id="e2a0f-179">**NX_DNS_CACHE_ENABLE**: этот параметр позволяет DNS-клиенту хранить записи ответов в кэше DNS.</span><span class="sxs-lookup"><span data-stu-id="e2a0f-179">**NX_DNS_CACHE_ENABLE**: This enables the DNS Client to store the answer records into DNS cache.</span></span>
