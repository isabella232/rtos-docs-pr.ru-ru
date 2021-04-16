---
title: Глава 2. Установка и использование PTP-клиента в NetX Duo для ОСРВ Azure
description: В этой главе описываются различные вопросы, связанные с установкой, настройкой и использованием PTP-клиента для NetX Duo.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cab2c31099bded953753fd530cef931cf0d7aaf7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814587"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-ptp-client"></a><span data-ttu-id="deeae-103">Глава 2. Установка и использование PTP-клиента в NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="deeae-103">Chapter 2 - Installation and Use of Azure RTOS NetX Duo PTP Client</span></span>

<span data-ttu-id="deeae-104">В этой главе описываются различные вопросы, связанные с установкой, настройкой и использованием PTP-клиента для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="deeae-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo PTP client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="deeae-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="deeae-105">Product Distribution</span></span>

<span data-ttu-id="deeae-106">NetX Duo для ОСРВ Azure можно получить из общедоступного репозитория исходного кода по адресу https://github.com/azure-rtos/netxduo/tree/master/addons/ptp.</span><span class="sxs-lookup"><span data-stu-id="deeae-106">Azure RTOS NetX Duo can be obtained from the public source code repository at https://github.com/azure-rtos/netxduo/tree/master/addons/ptp.</span></span>

<span data-ttu-id="deeae-107">***nxd_ptp_client.h*** — файл заголовка для PTP-клиента для NetX Duo. ***nxd_ptp_client.c*** — исходный файл C для PTP-клиента для NetX Duo. ***demo_netx_duo_ptp_client.c*** — демонстрационный пример PTP-клиента для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="deeae-107">***nxd_ptp_client.h*** Header file for PTP client for NetX Duo ***nxd_ptp_client.c*** C Source file for PTP client for NetX Duo ***demo_netx_duo_ptp_client.c*** NetX Duo PTP client demonstration</span></span>


## <a name="using-ptp-client"></a><span data-ttu-id="deeae-108">Использование PTP-клиента</span><span class="sxs-lookup"><span data-stu-id="deeae-108">Using PTP Client</span></span>
<span data-ttu-id="deeae-109">Использование PTP-клиента для NetX Duo не представляет никаких трудностей.</span><span class="sxs-lookup"><span data-stu-id="deeae-109">Using PTP client for NetX Duo is easy.</span></span> <span data-ttu-id="deeae-110">В коде приложения следует включить файл ***nxd_ptp_client.h** _ после включения _*_tx_api.h_*_ и _*_nx_api.h_\*_, что использовать ThreadX и NetX Duo соответственно.</span><span class="sxs-lookup"><span data-stu-id="deeae-110">Basically, the application code must include ***nxd_ptp_client.h** _ after it includes _*_tx_api.h_*_ and _*_nx_api.h_\*_, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="deeae-111">После включения файла заголовка для PTP-клиента код приложения сможет выполнять вызовы функций PTP-клиента, которые описаны далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="deeae-111">Once the PTP client header file is included, the application code is then able to make the PTP client function calls specified later in this guide.</span></span> <span data-ttu-id="deeae-112">Приложение также должно включить файл _ *_nxd_ptp_client.c_*\* в ходе сборки.</span><span class="sxs-lookup"><span data-stu-id="deeae-112">The application must also include _ *_nxd_ptp_client.c_*\* in the build process.</span></span> <span data-ttu-id="deeae-113">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="deeae-113">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="deeae-114">Это все, что необходимо для использования PTP-клиента для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="deeae-114">This is all that is required to use NetX Duo PTP client.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="deeae-115">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="deeae-115">Small Example System</span></span>
<span data-ttu-id="deeae-116">Пример использования служб PTP-клиента для NetX Duo приведен на рис. 1 ниже.</span><span class="sxs-lookup"><span data-stu-id="deeae-116">An example of how to use NetX Duo PTP client services is described in Figure 1 that appears below.</span></span>
```C
/*
   This is a small demo of the NetX Duo PTP client on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo and NetX Duo PTP client API to execute the Precision Time
   Protocol.

 */

#include <stdio.h>
#include "nx_api.h"
#include "nxd_ptp_client.h"

#ifndef SAMPLE_DHCP_DISABLE
#include "nxd_dhcp_client.h"
#endif /* SAMPLE_DHCP_DISABLE */

#define PTP_THREAD_PRIORITY 2

/* Define the ThreadX and NetX object control blocks...  */
static TX_THREAD        thread_0;
static NX_PACKET_POOL   pool_0;
static NX_IP            ip_0;
#ifndef SAMPLE_DHCP_DISABLE
static NX_DHCP          dhcp_client;
#endif /* SAMPLE_DHCP_DISABLE */
static NX_PTP_CLIENT    ptp_client;

/* Define the IP thread's stack area.  */
static ULONG            ip_thread_stack[2048 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
static ULONG            packet_pool_area[((1536 + sizeof(NX_PACKET)) * 32) / sizeof(ULONG)];

/* Define the ARP cache area.  */
static ULONG            arp_space_area[512 / sizeof(ULONG)];

/* Define the main thread.  */
static ULONG            thread_0_stack[2048 / sizeof(ULONG)];
static ULONG            ptp_stack[2048 / sizeof(ULONG)];

/* Define an error counter.  */
static ULONG            error_counter;

/* Define ptp utc offset.  */
static SHORT            ptp_utc_offset = 0;

#ifndef SAMPLE_DHCP_DISABLE
#define IPV4_ADDRESS            IP_ADDRESS(0, 0, 0, 0)
#define IPV4_NETWORK_MASK       IP_ADDRESS(0, 0, 0, 0)
#else
#define IPV4_ADDRESS            IP_ADDRESS(10, 1, 0, 212)
#define IPV4_NETWORK_MASK       IP_ADDRESS(255, 255, 0, 0)
#define IPV4_GATEWAY_ADDR       IP_ADDRESS(10, 1, 0, 1)
#define DNS_SERVER_ADDRESS      IP_ADDRESS(10, 1, 0, 1)
#endif /* SAMPLE_DHCP_DISABLE */

/* Define the main thread entry point. */
static VOID thread_0_entry(ULONG thread_input);

/* PTP handler.  */
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data);

#ifndef SAMPLE_DHCP_DISABLE
static void dhcp_wait();
#endif /* SAMPLE_DHCP_DISABLE */

/***** Substitute your ethernet driver entry function here *********/
#ifndef NETWORK_DRIVER
#define NETWORK_DRIVER _nx_ram_network_driver
#endif
extern VOID NETWORK_DRIVER(NX_IP_DRIVER *driver_req_ptr);

#ifndef CLOCK_CALLBACK
#define CLOCK_CALLBACK nx_ptp_client_soft_clock_callback
#endif
extern UINT CLOCK_CALLBACK(NX_PTP_CLIENT *client_ptr, UINT operation,
                           NX_PTP_TIME *time_ptr, NX_PACKET *packet_ptr,
                           VOID *callback_data);

#ifdef HARDWARE_SETUP
extern VOID HARDWARE_SETUP();
#endif

int main()
{
#ifdef HARDWARE_SETUP
    HARDWARE_SETUP();
#endif

    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}


/* Define what the initial system looks like.  */

void    tx_application_define(void *first_unused_memory)
{

UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,  (ULONG*)(((int)packet_pool_area + 15) & ~15) , sizeof(packet_pool_area));

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance.  */
    status = nx_ip_create(&ip_0,
                          "NetX IP Instance 0",
                          IPV4_ADDRESS,
                          IPV4_NETWORK_MASK,
                          &pool_0,
                          NETWORK_DRIVER,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable TCP traffic.  */
    status =  nx_tcp_enable(&ip_0);

    /* Check for TCP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP traffic.  */
    status =  nx_udp_enable(&ip_0);

    /* Check for UDP enable errors.  */
    if (status)
        error_counter++;

    /* Enable ICMP.  */
    status =  nx_icmp_enable(&ip_0);

    /* Check for errors.  */
    if (status)
        error_counter++;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                     thread_0_stack, sizeof(thread_0_stack),
                     4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
}


/* Define the test threads.  */
void    thread_0_entry(ULONG thread_input)
{

NX_PTP_TIME tm;
NX_PTP_DATE_TIME date;

#ifndef SAMPLE_DHCP_DISABLE
    dhcp_wait();
#endif /* SAMPLE_DHCP_DISABLE */

    /* Create the PTP client instance */
    nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                         PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                         CLOCK_CALLBACK, NX_NULL);

    /* start the PTP client */
    nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

    while(1)
    {

        /* read the PTP clock */
        nx_ptp_client_time_get(&ptp_client, &tm);

        /* convert PTP time to UTC date and time */
        nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

        /* display the current time */
        printf("%2u/%02u/%u %02u:%02u:%02u.%09lu\r\n", date.day, date.month, date.year, date.hour, date.minute, date.second, date.nanosecond);

        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }
}

static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
    NX_PARAMETER_NOT_USED(callback_data);

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            printf("new MASTER clock!\r\n");
            break;
        }

        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &ptp_utc_offset);
            printf("SYNC event: utc offset=%d\r\n", ptp_utc_offset);
            break;
        }

        case NX_PTP_CLIENT_EVENT_TIMEOUT:
        {
            printf("Master clock TIMEOUT!\r\n");
            break;
        }
        default:
        {
            break;
        }
    }

    return 0;
}

/* DHCP */
#ifndef SAMPLE_DHCP_DISABLE
void dhcp_wait(void)
{

ULONG   actual_status;
ULONG   ip_address;
ULONG   network_mask;
ULONG   gw_address;

    printf("DHCP In Progress...\r\n");

    /* Create the DHCP instance.  */
    nx_dhcp_create(&dhcp_client, &ip_0, "dhcp_client");

    /* Start the DHCP Client.  */
    nx_dhcp_start(&dhcp_client);

    /* Wait util address is solved. */
    nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED, &actual_status, NX_WAIT_FOREVER);

    /* Get IP address. */
    nx_ip_address_get(&ip_0, &ip_address, &network_mask);
    nx_ip_gateway_address_get(&ip_0, &gw_address);

    /* Output IP address. */
    printf("IP address: %d.%d.%d.%d\r\nMask: %d.%d.%d.%d\r\nGateway: %d.%d.%d.%d\r\n",
           (INT)(ip_address >> 24),
           (INT)(ip_address >> 16 & 0xFF),
           (INT)(ip_address >> 8 & 0xFF),
           (INT)(ip_address & 0xFF),
           (INT)(network_mask >> 24),
           (INT)(network_mask >> 16 & 0xFF),
           (INT)(network_mask >> 8 & 0xFF),
           (INT)(network_mask & 0xFF),
           (INT)(gw_address >> 24),
           (INT)(gw_address >> 16 & 0xFF),
           (INT)(gw_address >> 8 & 0xFF),
           (INT)(gw_address & 0xFF));
}
#endif /* SAMPLE_DHCP_DISABLE  */
```

## <a name="configuration-options"></a><span data-ttu-id="deeae-117">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="deeae-117">Configuration Options</span></span>
<span data-ttu-id="deeae-118">Существует несколько параметров для настройки PTP-клиента для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="deeae-118">There are several configuration options with the NetX Duo PTP client.</span></span> <span data-ttu-id="deeae-119">Ниже приведен список всех параметров с подробным описанием:</span><span class="sxs-lookup"><span data-stu-id="deeae-119">Following is a list of all options described in detail:</span></span>
* <span data-ttu-id="deeae-120">**NX_PTP_CLIENT_THREAD_TIME_SLICE** определяет интервал времени для потока PTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="deeae-120">**NX_PTP_CLIENT_THREAD_TIME_SLICE** This defines the PTP client thread time slice.</span></span> <span data-ttu-id="deeae-121">По умолчанию интервал времени не используется.</span><span class="sxs-lookup"><span data-stu-id="deeae-121">The default value is no time slice.</span></span>
* <span data-ttu-id="deeae-122">**NX_PTP_CLIENT_TIMER_TICKS_PER_SECOND** определяет частоту внутреннего таймера PTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="deeae-122">**NX_PTP_CLIENT_TIMER_TICKS_PER_SECOND** This defines the PTP client internal timer frequency.</span></span> <span data-ttu-id="deeae-123">По умолчанию используется значение 10, что означает длительность такта в 100 мс.</span><span class="sxs-lookup"><span data-stu-id="deeae-123">The default value is 10, indicating a 100ms timer.</span></span>
* <span data-ttu-id="deeae-124">**NX_PTP_CLIENT_ANNOUNCE_RECEIPT_TIMEOUT** определяет максимальное количество отсутствующих пакетов Announce, после которого завершается время ожидания.</span><span class="sxs-lookup"><span data-stu-id="deeae-124">**NX_PTP_CLIENT_ANNOUNCE_RECEIPT_TIMEOUT** This defines the maximum number of missing Announce packets before timeout.</span></span> <span data-ttu-id="deeae-125">Значение по умолчанию равно 3.</span><span class="sxs-lookup"><span data-stu-id="deeae-125">The default value is 3.</span></span>
* <span data-ttu-id="deeae-126">**NX_PTP_CLIENT_LOG_ANNOUNCE_INTERVAL** определяет интервал времени между двумя последовательными пакетами Announce, выраженный в формате логарифма по основанию 2.</span><span class="sxs-lookup"><span data-stu-id="deeae-126">**NX_PTP_CLIENT_LOG_ANNOUNCE_INTERVAL** This defines the time interval between successive Announce packet, expressed as log 2.</span></span> <span data-ttu-id="deeae-127">Это значение должно быть одинаковым в пределах домена.</span><span class="sxs-lookup"><span data-stu-id="deeae-127">This value should be uniform throughout a domain.</span></span> <span data-ttu-id="deeae-128">По умолчанию используется значение 1, что обозначает интервал в 2 с.</span><span class="sxs-lookup"><span data-stu-id="deeae-128">The default value is 1, which is 2s.</span></span>
* <span data-ttu-id="deeae-129">**NX_PTP_CLIENT_DELAY_REQ_INTERVAL** определяет интервал отправки для пакетов запроса задержки (Delay).</span><span class="sxs-lookup"><span data-stu-id="deeae-129">**NX_PTP_CLIENT_DELAY_REQ_INTERVAL** This defines the interval for sending Delay request packets.</span></span> <span data-ttu-id="deeae-130">По умолчанию используется значение в 2 с.</span><span class="sxs-lookup"><span data-stu-id="deeae-130">The default value is 2 seconds.</span></span>
* <span data-ttu-id="deeae-131">**NX_PTP_CLIENT_MAX_QUEUE_DEPTH** определяет максимальную глубину очереди для сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="deeae-131">**NX_PTP_CLIENT_MAX_QUEUE_DEPTH** This defines the maximum queue depth for client socket.</span></span> <span data-ttu-id="deeae-132">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="deeae-132">The default value is 5.</span></span>