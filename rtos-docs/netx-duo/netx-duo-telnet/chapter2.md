---
title: Глава 2. Установка и использование NetX Duo Telnet для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Duo Telnet для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5b24690db6ccbc582387dd9dba5b0471e6f278d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814536"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-telnet"></a><span data-ttu-id="740ad-103">Глава 2. Установка и использование NetX Duo Telnet для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="740ad-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Telnet</span></span>

<span data-ttu-id="740ad-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Duo Telnet для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="740ad-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Telnet component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="740ad-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="740ad-105">Product Distribution</span></span>

<span data-ttu-id="740ad-106">Пакет NetX Duo Telnet для ОСРВ Azure доступен по адресу <https://github.com/azure-rtos/netxduo>.</span><span class="sxs-lookup"><span data-stu-id="740ad-106">The Azure RTOS NetX Duo Telnet package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="740ad-107">В состав пакета входят следующие файлы.</span><span class="sxs-lookup"><span data-stu-id="740ad-107">The package includes the following files:</span></span>

- <span data-ttu-id="740ad-108">**nxd_telnet_client.h**: заголовочный файл клиента Telnet для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-108">**nxd_telnet_client.h**: Header file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="740ad-109">**nxd_telnet_client.c**: исходный файл C клиента Telnet для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-109">**nxd_telnet_client.c**: C Source file for Telnet Client for NetX Duo</span></span>
- <span data-ttu-id="740ad-110">**nxd_telnet_server.h**: заголовочный файл сервера Telnet для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-110">**nxd_telnet_server.h**: Header file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="740ad-111">**nxd_telnet_server.c**: исходный файл C сервера Telnet для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-111">**nxd_telnet_server.c**: C Source file for Telnet Server for NetX Duo</span></span>
- <span data-ttu-id="740ad-112">**nxd_telnet.pdf**: описание Telnet для NetX Duo в формате PDF.</span><span class="sxs-lookup"><span data-stu-id="740ad-112">**nxd_telnet.pdf**: PDF description of Telnet for NetX Duo</span></span>
- <span data-ttu-id="740ad-113">**demo_netxduo_telnet.c**: демонстрация работы Telnet для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-113">**demo_netxduo_telnet.c**: NetX Duo Telnet demonstration</span></span>

## <a name="telnet-installation"></a><span data-ttu-id="740ad-114">Установка Telnet</span><span class="sxs-lookup"><span data-stu-id="740ad-114">Telnet Installation</span></span>

<span data-ttu-id="740ad-115">Чтобы использовать Telnet для NetX Duo, упомянутый выше дистрибутив нужно целиком скопировать в тот же каталог, где установлен NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-115">In order to use Telnet for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="740ad-116">Например, если NetX Duo установлен в каталог " *\threadx\arm7\green*", то файлы *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c и nxd_telnet_server.h* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="740ad-116">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_telnet_client.h*, *nxd_telnet_client.c*, *nxd_telnet_server.c and nxd_telnet_server.h* files should be copied into this directory.</span></span>

## <a name="using-telnet"></a><span data-ttu-id="740ad-117">Использование Telnet</span><span class="sxs-lookup"><span data-stu-id="740ad-117">Using Telnet</span></span>

<span data-ttu-id="740ad-118">Использовать Telnet для NetX Duo просто.</span><span class="sxs-lookup"><span data-stu-id="740ad-118">Using Telnet for NetX Duo is easy.</span></span> <span data-ttu-id="740ad-119">Как правило, код приложения должен включать *nxd_telnet_server.h* для серверных приложений Telnet и *nxd_telnet_client.h* для клиентских приложений Telnet после включения *tx_api.h* и *nx_api.h* для использования ThreadX и NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-119">Basically, the application code must include *nxd_telnet_server.h* for Telnet Server applications and *nxd_telnet_client.h* for Telnet Client applications after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span> <span data-ttu-id="740ad-120">После включения *заголовка* код приложения сможет выполнять вызовы функций Telnet, указанные далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="740ad-120">Once *the header* is included, the application code is then able to make the Telnet function calls specified later in this guide.</span></span> <span data-ttu-id="740ad-121">Приложение должно также включать *nxd_telnet_client.c* и *nxd_telnet_server.c* в процессе сборки.</span><span class="sxs-lookup"><span data-stu-id="740ad-121">The application must also include *nxd_telnet_client.c* and *nxd_telnet_server.c* in the build process.</span></span> <span data-ttu-id="740ad-122">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="740ad-122">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="740ad-123">Это все, что необходимо для использования Telnet в NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-123">This is all that is required to use NetX Duo Telnet.</span></span>

<span data-ttu-id="740ad-124">Если возможности клиента Telnet не требуются, файл *nxd_telnet_client.c* можно опустить.</span><span class="sxs-lookup"><span data-stu-id="740ad-124">If no Telnet Client capabilities are required, the *nxd_telnet_client.c* file may be omitted.</span></span>

<span data-ttu-id="740ad-125">Также обратите внимание на то, что поскольку Telnet использует TCP-службы NetX Duo, необходимо включить TCP с помощью вызова *nx_tcp_enable* до использования Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-125">Note also that because Telnet utilizes NetX Duo TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using Telnet.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="740ad-126">Небольшой пример системы</span><span class="sxs-lookup"><span data-stu-id="740ad-126">Small Example System</span></span>

<span data-ttu-id="740ad-127">Пример использования Telnet NetX Duo приведен на рисунке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="740ad-127">An example of how to use NetX Duo Telnet is shown in Figure 1.1 below.</span></span> <span data-ttu-id="740ad-128">В этом примере включение файлов Telnet *расположено* в строках 7 и 8.</span><span class="sxs-lookup"><span data-stu-id="740ad-128">In this example, the Telnet include files *are* brought in at line 7 and 8.</span></span> <span data-ttu-id="740ad-129">Затем создается сервер Telnet с помощью "*tx_application_define*" в строке 146.</span><span class="sxs-lookup"><span data-stu-id="740ad-129">Next, the Telnet Server is created in “*tx_application_define*” at line 146.</span></span> <span data-ttu-id="740ad-130">Обратите внимание, что управляющие блоки сервера и клиента Telnet определены ранее как глобальные переменные в строках 23–24.</span><span class="sxs-lookup"><span data-stu-id="740ad-130">Note that the Telnet Server and Client control blocks are defined as global variables at line 23-24 previously.</span></span>

<span data-ttu-id="740ad-131">Перед запуском сервера или клиента Telnet необходимо проверить их IP-адреса с помощью NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-131">Before the Telnet Server or Client can be started they must validate their IP address with NetX Duo.</span></span> <span data-ttu-id="740ad-132">Для подключений по протоколу IPv4 это достигается простым недолгим ожиданием, позволяя драйверу NetX инициализировать систему в строке 166.</span><span class="sxs-lookup"><span data-stu-id="740ad-132">For IPv4 connections this is accomplished by simply waiting briefly to let the NetX driver initialize the system on line 166.</span></span> <span data-ttu-id="740ad-133">Для IPv6-подключений требуется включить IPv6 и ICMPv6, что выполняется в строках 171–172.</span><span class="sxs-lookup"><span data-stu-id="740ad-133">For IPv6 connections, this requires enabling IPv6 and ICMPv6 which it does in lines 171-172.</span></span> <span data-ttu-id="740ad-134">Клиент устанавливает свои глобальные и связываемые локальные IPv6-адреса на основном интерфейсе в строках 181–186 и ожидает завершения проверки NetX Duo в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="740ad-134">The Client sets its global and link local IPv6 addresses on the primary interface on lines 181-186 and waits for NetX Duo validation to complete in the background.</span></span> <span data-ttu-id="740ad-135">Сервер также задает глобальные и связываемые локальные адреса на основном интерфейсе в строках 192–198.</span><span class="sxs-lookup"><span data-stu-id="740ad-135">The Server also sets its global and link local addresses on its primary interface in lines 192 – 198.</span></span> <span data-ttu-id="740ad-136">Обратите внимание, что две службы *nxd_ipv6_global_address_set* и *nxd_ipv6_linklocal_address_set* заменяются службой *nxd_ipv6_address_set*.</span><span class="sxs-lookup"><span data-stu-id="740ad-136">Note that the two services, *nxd_ipv6_global_address_set* and *nxd_ipv6_linklocal_address_set* are replaced with *nxd_ipv6_address_set service*.</span></span> <span data-ttu-id="740ad-137">Две предыдущие службы по-прежнему доступны для устаревших приложений NetX Duo, но в конечном итоге являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="740ad-137">The former two services are still available for legacy NetX Duo applications but are eventually deprecated.</span></span> <span data-ttu-id="740ad-138">Вместо этого разработчикам рекомендуется использовать *nxd_ipv6_address_set*.</span><span class="sxs-lookup"><span data-stu-id="740ad-138">Developers are encouraged to use *nxd_ipv6_address_set* instead.</span></span>

<span data-ttu-id="740ad-139">После успешного выполнения проверки IP-адреса с помощью NetX Duo сервер Telnet запускается в строке 215 с помощью службы *nxd_telnet_server_start*.</span><span class="sxs-lookup"><span data-stu-id="740ad-139">After successful IP address validation with NetX Duo, the Telnet Server is started at line 215 using the *nxd_telnet_server_start* service.</span></span> <span data-ttu-id="740ad-140">В строке 226 клиент Telnet создается с помощью службы *nx_telnet_client_create*.</span><span class="sxs-lookup"><span data-stu-id="740ad-140">At line 226 the Telnet Client is created using the *nx_telnet_client_create* service.</span></span> <span data-ttu-id="740ad-141">Затем он соединяется с сервером Telnet в строке 242 для приложений IPv4 и строке 238 для приложений IPv6, используя службы *nxd_telnet_client_connect* и *nx_telnet_client_connect* соответственно.</span><span class="sxs-lookup"><span data-stu-id="740ad-141">It then connects with the Telnet Server on line 242 for IPv4 applications and line 238 for IPv6 applications using the *nxd_telnet_client_connect* and *nx_telnet_client_connect* services respectively.</span></span> <span data-ttu-id="740ad-142">После успешной проверки и подключения к серверу выполняется несколько обменов данными перед отключением.</span><span class="sxs-lookup"><span data-stu-id="740ad-142">After successful validation and connection with the server, it makes a few exchanges before disconnecting.</span></span>

```c
/* This is a small demo of TELNET on the high-performance NetX Duo TCP/IP stack.  
       This demo relies on ThreadX and NetX Duo to show a simple TELNET connection,
       send, server echo, and then disconnection from the TELNET server.  */
    
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_telnet_client.h"
#include  "nxd_telnet_server.h"
#define     DEMO_STACK_SIZE         4096    
   
/* Define the ThreadX and NetX object control blocks...  */
TX_THREAD               test_thread;
NX_PACKET_POOL          pool_server;
NX_PACKET_POOL          pool_client;
NX_IP                   ip_server;
NX_IP                   ip_client;
   
/* Define TELNET objects.  */

NX_TELNET_SERVER        my_server;
NX_TELNET_CLIENT        my_client;


#ifdef FEATURE_NX_IPV6

/* Define NetX Duo IP address for the NetX Duo Telnet Server and Client. */

NXD_ADDRESS     server_ip_address;
NXD_ADDRESS     client_ip_address;

#endif

#define         SERVER_ADDRESS          IP_ADDRESS(1,2,3,4)
#define         CLIENT_ADDRESS          IP_ADDRESS(1,2,3,5)

/* Define the counters used in the demo application...  */
ULONG                   error_counter;

/* Define timeout in ticks for connecting and sending/receiving data. */

#define                 TELNET_TIMEOUT  200

/* Define function prototypes.  */

void    thread_test_entry(ULONG thread_input);
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);


/* Define the application's TELNET Server callback routines.  */

void    telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection); 
void    telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection, 
                            NX_PACKET *packet_ptr);
void    telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT 
                              logical_connection);

/* Define main entry point.  */

int main()
{

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT    status;
CHAR    *pointer;
UINT    iface_index, address_index;
    
    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;
    
    /* Create the main thread.  */
    tx_thread_create(&test_thread, "test thread", thread_test_entry, 0,  
                     pointer, DEMO_STACK_SIZE, 
                     2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;
    
    /* Initialize the NetX system.  */
    nx_system_initialize();
    
    /* Create packet pool.  */
    nx_packet_pool_create(&pool_server, "Server NetX Packet Pool", 600, pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create an IP instance.  */
    nx_ip_create(&ip_server, "Server NetX IP Instance", SERVER_ADDRESS, 
                 0xFFFFFF00UL, &pool_server, _nx_ram_network_driver,
                 pointer, 4096, 1);
    
    pointer =  pointer + 4096;
    
    /* Create another packet pool. */
    nx_packet_pool_create(&pool_client, "Client NetX Packet Pool", 600, 
                          pointer, 8192);
    pointer = pointer + 8192;
    
    /* Create another IP instance.  */
    nx_ip_create(&ip_client, "Client NetX IP Instance", CLIENT_ADDRESS, 
                 0xFFFFFF00UL, &pool_client, _nx_ram_network_driver, 
                 pointer, 4096, 1);
    
    pointer = pointer + 4096;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_server, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_client, (void *) pointer, 1024);
    pointer = pointer + 1024;
    
    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_server);
    nx_tcp_enable(&ip_client);

#ifdef FEATURE_NX_IPV6

    /* Next set the NetX Duo Telnet Server and Client addresses. */
    server_ip_address.nxd_ip_address.v6[3] = 0x105;
    server_ip_address.nxd_ip_address.v6[2] = 0x0;
    server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

#endif

    /* Create the NetX Duo TELNET Server.  */
    status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_server, 
                                      pointer, 2048, telnet_new_connection, telnet_receive_data, 
                                      telnet_connection_end);
    
    /* Check for errors.  */
    if (status)
        error_counter++;
    
    return;
}

/* Define the test thread.  */
void    thread_test_entry(ULONG thread_input)
{

NX_PACKET   *my_packet;
UINT        status;
    
    /* Allow other threads (e.g. IP thread task) to run first. */
    tx_thread_sleep(100);
    
    #ifdef FEATURE_NX_IPV6
    /* Here's where we make the Telnet Client IPv6 enabled. */
    nxd_ipv6_enable(&ip_client);
    nxd_icmp_enable(&ip_client);     
    
    /* Wait till the IP task thread initializes the system. */
    tx_thread_sleep(100);
        
    /* Set up the Client addresses on the Client IP for the primary interface. */
    if_index = 0;
    
    status = nxd_ipv6_address_set(&ip_ client, iface_index, NX_NULL, 10, 
                                  &address_index);
    status = nxd_ipv6_address_set(&ip_ client, iface_index, & client _ip_address, 
                                   64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */
    tx_thread_sleep(400);
    
    /* Set up the Server addresses on the Client IP. */
    iface_index = 0;
    status = nxd_ipv6_address_set (&ip_server, iface_index, NX_NULL, 10, 
                                   &address_index);
    
    status = nxd_ ipv6_address _set(&ip_server, iface_index, & server _ip_address, 
                                     64, &address_index);
        
    /* Allow NetX Duo time to validate addresses. */     
    tx_thread_sleep(400);
    
    #endif
    
    /* Start the TELNET Server.  */
    status =  nx_telnet_server_start(&my_server);
    
    /* Check for errors.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Create a TELENT client instance.  */
    status =  nx_telnet_client_create(&my_client, "My TELNET Client", 
                                      &ip_client, 600);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    #ifdef FEATURE_NX_IPV6
    
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 
                                             TELNET_TIMEOUT);
    
    #else
        /* Connect the TELNET client to the TELNET Server at port 23.  */
        status =  nx_telnet_client_connect(&my_client, SERVER_ADDRESS, 23,
                                            TELNET_TIMEOUT);
    #endif
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Allocate a packet.  */
    status =  nx_packet_allocate(&pool_client, &my_packet, NX_TCP_PACKET, 
                                  NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Build a simple 1-byte message.  */
    nx_packet_data_append(my_packet, "a", 1, &pool_client, NX_WAIT_FOREVER);
    
    /* Send the packet to the TELNET Server.  */
    status =  nx_telnet_client_packet_send(&my_client, my_packet, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* Pickup the Server header.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);

    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the Server's banner
        message sent by the Server callback function below.  Just
        release it for this demo.  */
    nx_packet_release(my_packet);
    
    /* Pickup the Server echo of the character.  */
    status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 
                                               TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
    
    /* At this point the packet should contain the character 'a' that
        we sent earlier.  Just release the packet for now.  */
    nx_packet_release(my_packet);
    
    /* Now disconnect form the TELNET Server.  */
    status =  nx_telnet_client_disconnect(&my_client, TELNET_TIMEOUT);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Delete the TELNET Client.  */
    status =  nx_telnet_client_delete(&my_client);
    
    /* Check status.  */
    if (status != NX_SUCCESS)
    {
        return;
    }
}

/* This routine is called by the NetX Telnet Server whenever a new Telnet client 
    connection is established.  */
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{

UINT        status;
NX_PACKET   *packet_ptr;

    /* Allocate a packet for client greeting. */
    status =  nx_packet_allocate(&pool_server, &packet_ptr, NX_TCP_PACKET, 
                                  NX_NO_WAIT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Build a banner message and a prompt.  */
    nx_packet_data_append(packet_ptr,"**** Welcome to NetX TELNET Server ****\r\n\r\n\r\n", 45,                            
                         &pool_server, NX_NO_WAIT);

    nx_packet_data_append(packet_ptr, "NETX> ", 6, &pool_server, NX_NO_WAIT);
    
    /* Send the packet to the client.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }
    return;
}

/* This routine is called by the NetX Telnet Server whenever data is present on a 
    Telnet client connection.  */          
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, UINT logical_connection,
                          NX_PACKET *packet_ptr)
{

UINT    status;
UCHAR   alpha;

    /* This demo echoes the character back; on <cr,lf> sends a new prompt back to 
        the client.  A real system would likely buffer the character(s) received in a 
        buffer associated with the supplied logical connection and process it.  */

    /* Just throw away carriage returns.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\r') && (packet_ptr -> nx_packet_length == 1))
    {
        printf("telnet server received just a CRLF\n");

        nx_packet_release(packet_ptr);
        return;
    }

    /* Setup new line on line feed.  */
    if ((packet_ptr -> nx_packet_prepend_ptr[0] == '\n') || (packet_ptr -> nx_packet_prepend_ptr[1] == '\n'))
    {
        /* Clean up the packet.  */
        packet_ptr -> nx_packet_length =  0;
        packet_ptr -> nx_packet_prepend_ptr =  packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;
        packet_ptr -> nx_packet_append_ptr =   packet_ptr -> nx_packet_data_start + NX_TCP_PACKET;

        /* Build the next prompt.  */
        nx_packet_data_append(packet_ptr, "\r\nNETX> ", 8, &pool_server, 
                              NX_NO_WAIT);

        /* Send the packet to the client.  */
        status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                               packet_ptr, TELNET_TIMEOUT);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            nx_packet_release(packet_ptr);
        }
        return;
    }

    /* Pickup first character (usually only one from client).  */
    alpha =  packet_ptr -> nx_packet_prepend_ptr[0];

    /* Echo character.  */
    status =  nx_telnet_server_packet_send(server_ptr, logical_connection, 
                                           packet_ptr, TELNET_TIMEOUT);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        nx_packet_release(packet_ptr);
    }

    /* Check for a disconnection.  */
    if (alpha == 'q')
    {
        /* Initiate server disconnection.  */
        nx_telnet_server_disconnect(server_ptr, logical_connection);
    }
}


/* This routine is called by the NetX Telnet Server when the client disconnects.  */
void  telnet_connection_end(NX_TELNET_SERVER *server_ptr, UINT logical_connection)
{
    /* Cleanup any application specific connection or buffer information.  */
    return;
}
```

## <a name="configuration-options"></a><span data-ttu-id="740ad-143">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="740ad-143">Configuration Options</span></span>

<span data-ttu-id="740ad-144">Существует ряд параметров конфигурации для использования Telnet с NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="740ad-144">There are several configuration options for building Telnet for NetX Duo.</span></span> <span data-ttu-id="740ad-145">Эти директивы #define можно задать в приложении перед включением *nxd_telnet_server.h* и *nxd_telnet_client. h.*</span><span class="sxs-lookup"><span data-stu-id="740ad-145">These #defines can be set by the application prior to inclusion of *nxd_telnet_server.h*.and *nxd_telnet_client.h.*</span></span>

<span data-ttu-id="740ad-146">Ниже приведен список всех параметров с описанием.</span><span class="sxs-lookup"><span data-stu-id="740ad-146">Following is a list of all options, where each is described in detail:</span></span>  
  
- <span data-ttu-id="740ad-147">**NX_DISABLE_ERROR_CHECKING**: если определен, этот параметр удаляет базовую проверку ошибок Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-147">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic Telnet error checking.</span></span> <span data-ttu-id="740ad-148">Обычно он включается после завершения отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="740ad-148">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="740ad-149">**NX_TELNET_MAX_CLIENTS**: максимальное число клиентов Telnet, поддерживаемое потоком сервера.</span><span class="sxs-lookup"><span data-stu-id="740ad-149">**NX_TELNET_MAX_CLIENTS**: The maximum number of Telnet Clients supported by the Server thread.</span></span> <span data-ttu-id="740ad-150">По умолчанию это значение равно 4, чтобы задать одновременное подключение не более 4 клиентов.</span><span class="sxs-lookup"><span data-stu-id="740ad-150">By default, this value is defined as 4 to specify a maximum of 4 clients at a time.</span></span>
- <span data-ttu-id="740ad-151">**NX_TELNET_SERVER_PRIORITY**: приоритет потока сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-151">**NX_TELNET_SERVER_PRIORITY**: The priority of the Telnet Server thread.</span></span> <span data-ttu-id="740ad-152">По умолчанию указано значение 16 для задания приоритета 16.</span><span class="sxs-lookup"><span data-stu-id="740ad-152">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="740ad-153">**NX_TELNET_TOS**: тип службы, необходимый для TCP-запросов Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-153">**NX_TELNET_TOS**: Type of service required for the Telnet TCP requests.</span></span> <span data-ttu-id="740ad-154">По умолчанию это значение определяется как NX_IP_NORMAL для указания</span><span class="sxs-lookup"><span data-stu-id="740ad-154">By default, this value is defined as NX_IP_NORMAL to indicate</span></span>  
<span data-ttu-id="740ad-155">обычной службы IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="740ad-155">normal IP packet service.</span></span>
- <span data-ttu-id="740ad-156">**NX_TELNET_FRAGMENT_OPTION**: включить фрагментирование для TCP-запросов Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-156">**NX_TELNET_FRAGMENT_OPTION**: Fragment enable for Telnet TCP requests.</span></span> <span data-ttu-id="740ad-157">По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование TCP в Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-157">By default, this value is NX_DONT_FRAGMENT to disable Telnet TCP fragmenting.</span></span>
- <span data-ttu-id="740ad-158">**NX_TELNET_SERVER_WINDOW_SIZE**: размер окна сокета для сервера.</span><span class="sxs-lookup"><span data-stu-id="740ad-158">**NX_TELNET_SERVER_WINDOW_SIZE**: Server socket window size.</span></span> <span data-ttu-id="740ad-159">Значение по умолчанию — 2048 байт.</span><span class="sxs-lookup"><span data-stu-id="740ad-159">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="740ad-160">**NX_TELNET_TIME_TO_LIVE**: указывает число маршрутов, которое может пройти этот пакет перед его отбрасыванием.</span><span class="sxs-lookup"><span data-stu-id="740ad-160">**NX_TELNET_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="740ad-161">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="740ad-161">The default value is set to 0x80.</span></span>
- <span data-ttu-id="740ad-162">**NX_TELNET_SERVER_TIMEOUT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу.</span><span class="sxs-lookup"><span data-stu-id="740ad-162">**NX_TELNET_SERVER_TIMEOUT**: Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="740ad-163">По умолчанию значение равно 10 секундам.</span><span class="sxs-lookup"><span data-stu-id="740ad-163">The default value is set to 10 seconds.</span></span>
- <span data-ttu-id="740ad-164">**NX_TELNET_ACTIVITY_TIMEOUT**: указывает количество секунд, которое может пройти без каких бы то ни было действий, прежде чем сервер отключит клиентское подключение.</span><span class="sxs-lookup"><span data-stu-id="740ad-164">**NX_TELNET_ACTIVITY_TIMEOUT**: Specifies the number of seconds that can elapse without any activity before the Server disconnects the Client connection.</span></span> <span data-ttu-id="740ad-165">По умолчанию значение равно 600 секундам.</span><span class="sxs-lookup"><span data-stu-id="740ad-165">The default value is set to 600 seconds.</span></span>
- <span data-ttu-id="740ad-166">**NX_TELNET_TIMEOUT_PERIOD**: указывает количество секунд между проверками времени ожидания активности клиентов.</span><span class="sxs-lookup"><span data-stu-id="740ad-166">**NX_TELNET_TIMEOUT_PERIOD**: Specifies the number of seconds between checking for Client activity timeouts.</span></span> <span data-ttu-id="740ad-167">По умолчанию значение равно 60 секундам.</span><span class="sxs-lookup"><span data-stu-id="740ad-167">The default value is set to 60 seconds.</span></span>
- <span data-ttu-id="740ad-168">**NX_TELNET_SERVER_OPTION_DISABLE**: если параметр определен, то согласование параметров Telnet отключено.</span><span class="sxs-lookup"><span data-stu-id="740ad-168">**NX_TELNET_SERVER_OPTION_DISABLE**: Defined, Telnet option negotiation is disabled.</span></span> <span data-ttu-id="740ad-169">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="740ad-169">By default this option is not defined.</span></span>
- <span data-ttu-id="740ad-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: если этот параметр определен, пул пакетов сервера Telnet должен быть создан извне.</span><span class="sxs-lookup"><span data-stu-id="740ad-170">**NX_TELNET_SERVER_USER_CREATE_PACKET_POOL**: If defined, the Telnet Server packet pool must be created externally.</span></span> <span data-ttu-id="740ad-171">Этот параметр имеет смысл только в том случае, если NX_TELNET_SERVER_OPTION_DISABLE не определен.</span><span class="sxs-lookup"><span data-stu-id="740ad-171">This is only meaningful if NX_TELNET_SERVER_OPTION_DISABLE is not defined.</span></span> <span data-ttu-id="740ad-172">По умолчанию этот параметр не определен, и поток сервера Telnet создает собственный пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="740ad-172">By default this option is not defined and the Telnet Server thread creates its own packet pool.</span></span>
- <span data-ttu-id="740ad-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: определяет размер полезных данных пакета, созданных сервером Telnet для согласования параметров.</span><span class="sxs-lookup"><span data-stu-id="740ad-173">**NX_TELNET_SERVER_PACKET_PAYLOAD**: Defines the size of the packet payload created by the Telnet Server for option negotiation.</span></span> <span data-ttu-id="740ad-174">Обратите внимание, что сервер Telnet создает этот пул пакетов, только если NX_TELNET_SERVER_OPTION_DISABLE не определен (параметры Telnet включены).</span><span class="sxs-lookup"><span data-stu-id="740ad-174">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="740ad-175">Значение этого параметра по умолчанию — 300.</span><span class="sxs-lookup"><span data-stu-id="740ad-175">The default value of this option is 300.</span></span>
- <span data-ttu-id="740ad-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: определяет размер пула пакетов сервера Telnet, используемого для согласований Telnet.</span><span class="sxs-lookup"><span data-stu-id="740ad-176">**NX_TELNET_SERVER_PACKET_POOL_SIZE**: Defines the size of the Telnet Server packet pool used for Telnet negotiations.</span></span> <span data-ttu-id="740ad-177">Обратите внимание, что сервер Telnet создает этот пул пакетов, только если NX_TELNET_SERVER_OPTION_DISABLE не определен (параметры Telnet включены).</span><span class="sxs-lookup"><span data-stu-id="740ad-177">Note that the Telnet Server only creates this packet pool if NX_TELNET_SERVER _OPTION_DISABLE is not defined (Telnet options are enabled).</span></span> <span data-ttu-id="740ad-178">Значение этого параметра по умолчанию равно 2048 (\~5–6 пакетов).</span><span class="sxs-lookup"><span data-stu-id="740ad-178">The default value of this option is 2048 (\~5-6 packets).</span></span>
