---
title: Глава 2. Установка и использование клиента SNTP для NetX Duo (ОСРВ Azure)
description: В этой главе описываются разные вопросы, связанные с установкой, настройкой и использованием клиента SNTP для NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2058875c08d64e2c16f67b48323814ec77ec96882eec26aaf2c9454459511db3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799054"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-sntp-client"></a>Глава 2. Установка и использование клиента SNTP для NetX Duo (ОСРВ Azure)

В этой главе описываются разные вопросы, связанные с установкой, настройкой и использованием клиента SNTP для NetX Duo (ОСРВ Azure).

## <a name="product-distribution"></a>Распространение продукта

SNTP для NetX Duo предоставляется по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). Пакет включает в себя два исходных файла и PDF-файл с этим документом:

- **nxd_sntp_client.c** — исходный файл клиента SNTP на языке C;  
- **nxd_sntp_client.h** — файл заголовков для клиента SNTP;  
- **demo_netxduo_sntp_client.c** — пример приложения для клиента SNTP;  
- **nxd_sntp_client.pdf** — руководство пользователя клиента SNTP для NetX Duo.  

## <a name="netx-duo-sntp-client-installation"></a>Установка клиента SNTP для NetX Duo

Чтобы использовать SNTP для NetX Duo, упомянутый выше дистрибутив нужно целиком скопировать в тот же каталог с установленным экземпляром NetX Duo. Например, если экземпляр NetX Duo установлен в каталоге *\threadx\arm7\green*, файлы клиента SNTP NetX Duo *nxd_sntp_client.c* и *nxd_sntp_client.h* (*nx_sntp_client.c* и *nx_sntp_client.h* в среде NetX) нужно скопировать в тот же каталог.

## <a name="using-netx-duo-sntp-client"></a>Использование клиента SNTP для NetX Duo

Работа с клиентом SNTP для NetX Duo не представляет никаких сложностей. Чтобы использовать ThreadX и NetX Duo, в код приложения достаточно включить файл *nxd_ptp_client.h* после включения *tx_api.h, fx_api.h* и *nx_api.h* соответственно. После включения файла *nxd_sntp_client.h* код приложения может выполнять вызовы функций SNTP, описанные ниже в этом руководстве. В приложение также нужно включить файл *nxd_ptp_client.c* для процесса сборки. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования клиента SNTP для NetX Duo.

> [!NOTE]
> Так как клиент SNTP для NetX Duo использует службы UDP для NetX Duo, нужно включить протокол UDP с помощью вызова *nx_udp_enable* перед обращением к службам SNTP.

## <a name="small-example-system"></a>Пример небольшой системы

Ниже приведен пример использования SNTP для NetX Duo. Обратите внимание, что работоспособность этого примера в вашей системе **не гарантируется**. Возможно, в него придется внести изменения с учетом системы и оборудования. Например, заменить драйвер NetX RAM драйвером для вашей среды. Этот пример предоставляется исключительно для демонстрации.

В этом примере включается файл заголовка SNTP с именем *nxd_sntp_client.h*. Затем создается клиент SNTP в разделе *tx_application_define*. Обратите внимание, что функции для обработки пакета "поцелуй смерти" и корректировочной секунды не являются обязательными при создании клиента SNTP.

Эту демонстрацию можно использовать с IPv6 или IPv4. Чтобы запустить клиент SNTP с протоколом IPv6, определите параметр USE_IPV6. Также протокол IPv6 должен быть включен в NetX Duo. Узел клиента SNTP настроен на проверку IPv6-адреса и использование служб ICMPv6 и IPv6 для NetX Duo. Дополнительные сведения о поддержке IPv6 в NetX Duo см. в руководстве пользователя NetX Duo.

Затем вам нужно инициализировать клиент SNTP для работы в одноадресном или широковещательном режиме.

Клиент SNTP изначально записывает обновления времени, полученные от сервера, в собственную внутреннюю структуру данных. Эта структура отличается от местного времени устройства. Местное время устройства можно задать как базовое время для клиента SNTP перед запуском потока этого клиента SNTP. Это полезно, если для клиента SNTP параметр NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP имеет значение NX_FALSE, т. е. настроено сравнение первого обновления от сервера со значением NX_SNTP_CLIENT_MAX_ADJUSTMENT (по умолчанию оно составляет 180 миллисекунд). В противном случае клиент SNTP просто задаст начальное местное время при получении первого обновления от сервера.

Базовое время применяется к клиенту SNTP с помощью службы *nx_sntp_client_set_local_time*.

Клиент SNTP запускается в одноадресном и широковещательном режимах соответственно. В течение некоторого интервала (который немного меньше интервала опроса в одноадресном режиме) приложение обновляет местное время клиента SNTP с помощью службы *nx_sntp_client_set_local_time*, использующей нашу эмуляцию часов реального времени, в которой мы просто увеличиваем значения секунд и миллисекунд текущего времени. После каждого такого интервала приложение проверяет получение обновлений с сервера SNTP. Служба *nx_sntp_client_receiving_updates* проверяет, что клиент SNTP все еще получает допустимые обновления. Если это так, извлекается последнее полученное время обновления с помощью службы *nx_sntp_client_get_local_time_extended*.

Вы можете остановить клиент SNTP в любое время с помощью службы *nx_sntp_client_stop*, например, если клиент SNTP больше не получает допустимые обновления. Чтобы перезапустить клиент, приложению нужно вызвать службу инициализации в одноадресном или широковещательном режиме, а затем вызвать службу выполнения в одноадресном или широковещательном режиме. Пока задача в потоке клиента SNTP остановлена, клиент SNTP может изменять сервер и режим SNTP (одноадресный или широковещательный), например, если использовавшийся ранее сервер SNTP прекратил работу.

```c
/* 
   This is a small demo of the NetX SNTP Client on the high-performance NetX
   TCP/IP stack. This demo relies on Thread, NetX and NetX SNTP Client API to
   execute the Simple Network Time Protocol in unicast and broadcast modes.  
 */

#include <stdio.h>
#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_sntp_client.h"
                
/* Define SNTP packet size. */
#define NX_SNTP_CLIENT_PACKET_SIZE      (NX_UDP_PACKET + 100)

/* Define SNTP packet pool size. */
#define NX_SNTP_CLIENT_PACKET_POOL_SIZE      (4 * (NX_SNTP_CLIENT_PACKET_SIZE + 
                                                            sizeof(NX_PACKET)))

/* Define how often the demo checks for SNTP updates. */
#define DEMO_PERIODIC_CHECK_INTERVAL      (1 * NX_IP_PERIODIC_RATE) 

/* Define how often we check on SNTP server status. 
   We expect updates from the SNTP server about every hour using 
   the SNTP Client defaults. For testing
   make this (much) shorter. */
#define CHECK_SNTP_UPDATES_TIMEOUT       (180 * NX_IP_PERIODIC_RATE) 

/* Set up generic network driver for demo program. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Application defined services of the NetX SNTP Client. */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator);
UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, 
                                        UINT KOD_code);
VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time);


/* Set up client thread and network resources. */

NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;
TX_THREAD           demo_client_thread;
NX_SNTP_CLIENT      demo_sntp_client;
TX_EVENT_FLAGS_GROUP sntp_flags;

#define DEMO_SNTP_UPDATE_EVENT  1

/* Configure the SNTP Client to use IPv6. If not enabled, the 
   Client will use IPv4.  Note: IPv6 must be enabled in NetX Duo
   for the Client to communicate over IPv6.    */
#ifdef FEATURE_NX_IPV6
/* #define USE_IPV6 */
#endif /* FEATURE_NX_IPV6 */


/* Configure the SNTP Client to use unicast SNTP. */
#define USE_UNICAST


#define CLIENT_IP_ADDRESS       IP_ADDRESS(192,2,2,66)
#define SERVER_IP_ADDRESS       IP_ADDRESS(192,2,2,92)
#define SERVER_IP_ADDRESS_2     SERVER_IP_ADDRESS

/* Set up the SNTP network and address index; */
UINT     iface_index =0;
UINT     prefix = 64;   
UINT     address_index;

/* Set up client thread entry point. */
void    demo_client_thread_entry(ULONG info);

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
    return 0;
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UINT     status;
UCHAR    *free_memory_pointer;


    free_memory_pointer = (UCHAR *)first_unused_memory;

    /* Create client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool, 
                                "SNTP Client Packet Pool",
                                NX_SNTP_CLIENT_PACKET_SIZE, 
                                free_memory_pointer, 
                                NX_SNTP_CLIENT_PACKET_POOL_SIZE);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + NX_SNTP_CLIENT_PACKET_POOL_SIZE;

    /* Create Client IP instances */
    status = nx_ip_create(&client_ip, "SNTP IP Instance", 
                                        CLIENT_IP_ADDRESS, 
                                        0xFFFFFF00UL, 
                                        &client_packet_pool, 
                                       _nx_ram_network_driver, 
                                       free_memory_pointer, 2048, 1);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

    free_memory_pointer =  free_memory_pointer + 2048;

#ifndef NX_DISABLE_IPV4
    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 2048);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;
    
    /* Enable UDP for client. */
    status =  nx_udp_enable(&client_ip);
    
    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }

#ifndef NX_DISABLE_IPV4
    status = nx_icmp_enable(&client_ip);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        return;
    }
#endif /* NX_DISABLE_IPV4  */

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "SNTP Client Thread", 
                                                demo_client_thread_entry, 
                                              (ULONG)(&demo_sntp_client), 
                                                free_memory_pointer, 2048, 
                                                  4, 4, TX_NO_TIME_SLICE, 
                                                        TX_DONT_START);

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Create the event flags. */
    status = tx_event_flags_create(&sntp_flags, "SNTP event flags");

    /* Check for errors */
    if (status != TX_SUCCESS)
    {

        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* set the SNTP network interface to the primary interface. */
    iface_index = 0;

    /* Create the SNTP Client to run in broadcast mode.. */
status =  nx_sntp_client_create(&demo_sntp_client, &client_ip,
                           iface_index, &client_packet_pool,  
                               leap_second_handler, 
                               kiss_of_death_handler, 
                               NULL /* no random_number_generator callback */);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {

        /* Bail out!*/
        return;
    }

    tx_thread_resume(&demo_client_thread);

    return;
}

/* Define size of buffer to display client's local time. */
#define BUFSIZE 50

/* Define the client thread.  */
void    demo_client_thread_entry(ULONG info)
{

UINT   status;
UINT   spin;
UINT   server_status;
ULONG  base_seconds;
ULONG  base_fraction;
ULONG  seconds, milliseconds, microseconds, fraction;
UINT   wait = 0;
UINT   error_counter = 0;
ULONG  events = 0;
#ifdef USE_IPV6
NXD_ADDRESS sntp_server_address;
NXD_ADDRESS client_ip_address;
#endif

    NX_PARAMETER_NOT_USED(info);

    /* Give other threads (IP instance) initialize first. */
    tx_thread_sleep(NX_IP_PERIODIC_RATE); 

#ifdef USE_IPV6
    /* Set up IPv6 services. */
    status = nxd_ipv6_enable(&client_ip);

    status += nxd_icmp_enable(&client_ip);

    if (status  != NX_SUCCESS)
        return;

    client_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
    client_ip_address.nxd_ip_address.v6[2] = 0x0;
    client_ip_address.nxd_ip_address.v6[3] = 0x101;
    client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Set the IPv6 server address. */
    sntp_server_address.nxd_ip_address.v6[0] = 0x20010db8;  
    sntp_server_address.nxd_ip_address.v6[1] = 0x0000f101;
    sntp_server_address.nxd_ip_address.v6[2] = 0x0;
    sntp_server_address.nxd_ip_address.v6[3] = 0x00000106;
    sntp_server_address.nxd_ip_version = NX_IP_VERSION_V6;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address. */
    status = nxd_ipv6_address_set(&client_ip, iface_index, NX_NULL, 10, NULL);

    /* Check for link local address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

     /* Set the host global IP address. We are assuming a 64 
       bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&client_ip, iface_index, 
                                        &client_ip_address, 
                                    prefix, &address_index);

    /* Check for global address set error.  */
    if (status != NX_SUCCESS) 
    {
        return;
    }

    /* Wait while NetX Duo validates the global and link local addresses. */
    tx_thread_sleep(5 * NX_IP_PERIODIC_RATE);

#endif

    /* Setup time update callback function. */
    nx_sntp_client_set_time_update_notify(&demo_sntp_client, 
                                        time_update_callback);

    /* Set up client time updates depending on mode. */
#ifdef USE_UNICAST

    /* Initialize the Client for unicast mode to 
       poll the SNTP server once an hour. */
#ifdef USE_IPV6
/* Use the duo service to set up the Client and set the IPv6 SNTP server.
   Note: this can take either an IPv4 or IPv6 address. */
    status = nxd_sntp_client_initialize_unicast(&demo_sntp_client, 
                                            &sntp_server_address);
#else
    /* Use the IPv4 service to set up the Client and set the IPv4 SNTP server. */
    status = nx_sntp_client_initialize_unicast(&demo_sntp_client, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */


#else   /* Broadcast mode */

/* Initialize the Client for broadcast mode, no roundtrip calculation
   required and a broadcast SNTP service. */
#ifdef USE_IPV6
    /* Use the duo service to initialize the Client 
       and set IPv6 SNTP all hosts multicast address. 
       (Note: This can take either an IPv4 or IPv6 address.)*/
    status = nxd_sntp_client_initialize_broadcast(&demo_sntp_client, 
                                                &sntp_server_address, 
                                                            NX_NULL);
#else

    /* Use the IPv4 service to initialize the Client and set 
       IPv4 SNTP broadcast address. */
    status = nx_sntp_client_initialize_broadcast(&demo_sntp_client,  
                                                NX_NULL, 
                                                SERVER_IP_ADDRESS);
#endif  /* USE_IPV6 */
#endif  /* USE_UNICAST */

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Set the base time which is approximately the number of seconds since
       the turn of the last century. If this is not available in SNTP format,
       the nx_sntp_client_utility_add_msecs_to_ntp_time service can convert
       milliseconds to fraction.  For how to compute NTP seconds from real
   time, read the NetX SNTP User Guide. Otherwise set the base time to 
   zero and set NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP to NX_TRUE for
       the SNTP CLient to accept the first time update without applying a
       minimum or maximum adjustment parameters
      (NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT and
       NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT). */

    base_seconds =  0xd2c96b90;  /* Jan 24, 2012 UTC */
    base_fraction = 0xa132db1e;

    /* Apply to the SNTP Client local time.  */
status = nx_sntp_client_set_local_time(&demo_sntp_client, base_seconds,
                                base_fraction);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Run whichever service the client is configured for. */
#ifdef USE_UNICAST
    status = nx_sntp_client_run_unicast(&demo_sntp_client);
#else
    status = nx_sntp_client_run_broadcast(&demo_sntp_client);
#endif  /* USE_UNICAST */

    if (status != NX_SUCCESS)
    {
        return;
    }

    spin = NX_TRUE;

    /* Now check periodically for time changes. */
    while(spin)
    {
        /* Wait for a server update event. */
        tx_event_flags_get(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, 
                                          TX_OR_CLEAR, &events, 
                                 DEMO_PERIODIC_CHECK_INTERVAL);

        if (events == DEMO_SNTP_UPDATE_EVENT)
        {

            /* Check for valid SNTP server status. */
            status = nx_sntp_client_receiving_updates(&demo_sntp_client,
                                               &server_status);

            if ((status != NX_SUCCESS) || (server_status == NX_FALSE))
            {

                /* We do not have a valid update. Skip processing any time
                   data. If this happens repeatedly, consider stopping the
                   SNTP Client thread, picking another SNTP server and
                   resuming the SNTP Client thread task (more details about
                   that in the comments at the end of this function).
                 
                   If SNTP Client configurable parameters are too restrictive,
                   such as Max Adjustment, that may also cause valid server
                   updates to be rejected. Configurable parameters, however,
                   cannot be changed at run time.
                 */
                 
                continue;
            }

            /* We have a valid update.  Get the SNTP Client time.  */
            status = nx_sntp_client_get_local_time_extended(&demo_sntp_client, 
                                                    &seconds, &fraction,  
                                                    NX_NULL, 0); 

            /* Convert fraction to microseconds. */
            nx_sntp_client_utility_fraction_to_usecs(fraction, &microseconds);

            milliseconds = ((microseconds + 500) / 1000);

            if (status != NX_SUCCESS)
            {
                printf("Internal error with getting local time 0x%x\n", 
                       status);
                error_counter++;
            }
            else
            {
                printf("\nSNTP updated\n");
                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }

            /* Clear all events in our event flag. */
            events = 0;
        }
        else
        {

            /* No SNTP update event.             
               In the meantime, if we have an RTC we might want to check
               its notion of time. In this demo, we simulate the passage of 
               time on our 'RTC' really just the CPU counter, assuming that 
               seconds and milliseconds have previously been set to a base 
              (starting) time (as was the SNTP Client before running it) 
             */

            seconds += 1;
            milliseconds += 1;

            /* Update our timer. */
            wait += DEMO_PERIODIC_CHECK_INTERVAL;

            /* Check if it is time to display the local 'RTC' time. */
            if (wait >= CHECK_SNTP_UPDATES_TIMEOUT)
            {
                /* It is. Reset the timeout and print local time. */
                wait = 0;

                printf("Time: %lu.%03lu sec.\r\n", seconds, milliseconds);
            }           
        }
    }

/* We can stop the SNTP service if for example we think the SNTP server 
   has stopped sending updates.
     
       To restart the SNTP Client, simply call the
       nx_sntp_client_initialize_unicast or
       nx_sntp_client_initialize_broadcast using another SNTP server IP
       address as input, and resume the SNTP Client by calling
       nx_sntp_client_run_unicast or
       nx_sntp_client_run_braodcast. */
    status = nx_sntp_client_stop(&demo_sntp_client);

    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* When done with the SNTP Client, we delete it */
    status = nx_sntp_client_delete(&demo_sntp_client);

    return;
}


/* This application defined handler for handling an 
   impending leap second is not required by 
   the SNTP Client. The default handler below only logs the
   event for every time stamp received with the 
   leap indicator set.  */

UINT leap_second_handler(NX_SNTP_CLIENT *client_ptr, 
                                UINT leap_indicator)
{
    NX_PARAMETER_NOT_USED(client_ptr);
    NX_PARAMETER_NOT_USED(leap_indicator);

    /* Handle the leap second handler... */

    return NX_SUCCESS;
}

/* This application defined handler for handling 
   a Kiss of Death packet is not required by the SNTP Client. 
   A KOD handler should determine if the Client task should continue vs. 
   abort sending/receiving time data from its current time server, 
   and if aborting if it should remove
   the server from its active server list. 

   Note that the KOD list of codes is subject to change. The list
   below is current at the time of this software release. */

UINT kiss_of_death_handler(NX_SNTP_CLIENT *client_ptr, UINT KOD_code)
{

UINT    remove_server_from_list = NX_FALSE;
UINT    status = NX_SUCCESS;

    NX_PARAMETER_NOT_USED(client_ptr);

    /* Handle kiss of death by code group. */
    switch (KOD_code)
    {

        case NX_SNTP_KOD_RATE:
        case NX_SNTP_KOD_NOT_INIT:
        case NX_SNTP_KOD_STEP:

            /* Find another server while this one 
               is temporarily out of service.  */
            status =  NX_SNTP_KOD_SERVER_NOT_AVAILABLE;

        break;

        case NX_SNTP_KOD_AUTH_FAIL:
        case NX_SNTP_KOD_NO_KEY:
        case NX_SNTP_KOD_CRYP_FAIL:

            /* These indicate the server will not 
               service client with time updates
               without successful authentication. */


            remove_server_from_list =  NX_TRUE;

        break;


        default:

            /* All other codes. Remove server 
               before resuming time updates. */

            remove_server_from_list =  NX_TRUE;
        break;
    }

    /* Removing the server from the active server list? */
    if (remove_server_from_list)
    {

        /* Let the caller know it has to bail on 
           this server before resuming service. */
        status = NX_SNTP_KOD_REMOVE_SERVER;
    }

    return status;
}


/* This application defined handler for notifying SNTP time update event.  */

VOID time_update_callback(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                       NX_SNTP_TIME *local_time)
{
    tx_event_flags_set(&sntp_flags, DEMO_SNTP_UPDATE_EVENT, TX_OR);
}

```

Рис. 1. Пример использования клиента SNTP для NetX Duo

## <a name="configuration-options"></a>Параметры конфигурации

Существует несколько параметров конфигурации для определения клиента SNTP для NetX Duo. Их подробное описание приводится ниже.  
  

**NX_SNTP_CLIENT_THREAD_STACK_SIZE**  
Этот параметр задает размер стека для потока клиента. По умолчанию для клиента SNTP для NetX Duo задается значение 2048.

**NX_SNTP_CLIENT_THREAD_TIME_SLICE**  
Этот параметр задает для планировщика интервал времени, допустимый для выполнения клиентского потока. По умолчанию для клиента SNTP для NetX Duo SNTP задается значение TX_NO_TIME_SLICE.

**NX_SNTP_CLIENT_THREAD_PRIORITY**  
Этот параметр задает приоритет потока клиента. По умолчанию для клиента SNTP для NetX Duo задается значение 2.

**NX_SNTP_CLIENT_PREEMPTION_THRESHOLD**  
Этот параметр задает уровень приоритета, при котором поток клиента допускает вытеснение. По умолчанию для клиента SNTP для NetX Duo задается значение `NX_SNTP_CLIENT_ THREAD_PRIORITY`.

**NX_SNTP_CLIENT_UDP_SOCKET_NAME**  
Этот параметр задает имя сокета UDP. По умолчанию для клиента SNTP для NetX Duo задается имя сокета SNTP Client socket.

**NX_SNTP_CLIENT_UDP_PORT**  
Этот параметр задает порт, к которому привязан сокет клиента. По умолчанию для клиента SNTP для NetX Duo задается порт 123.

**NX_SNTP_SERVER_UDP_PORT**  
Порт на сервере SNTP, на который клиент отправляет сообщения SNTP. По умолчанию для NetX задается порт сервера SNTP 123.

**NX_SNTP_CLIENT_TIME_TO_LIVE**  
Указывает число маршрутизаторов, которые может пройти пакет клиента, прежде чем будет отброшен. По умолчанию для клиента SNTP для NetX Duo задается значение 0x80 *.*

**NX_SNTP_CLIENT_MAX_QUEUE_DEPTH**  
Максимальное количество UDP-пакетов (датаграмм), которые могут находиться в очереди для сокета клиента SNTP для NetX Duo. При получении большего числа пакетов самые старые пакеты будут отбрасываться. По умолчанию для клиента SNTP для NetX Duo задается значение 5.

**NX_SNTP_CLIENT_PACKET_TIMEOUT**  
Время ожидания для распределения пакетов NetX Duo. По умолчанию для клиента SNTP для NetX Duo задается время ожидания пакетов, равное 1 секунде.

**NX_SNTP_CLIENT_NTP_VERSION**  
Версия SNTP, используемая в API клиента SNTP для NetX Duo, была основана на версии 4. Значение по умолчанию равно 3.

**NX_SNTP_CLIENT_MIN_NTP_VERSION**  
Самая старая версия SNTP, с которой клиент сможет работать. По умолчанию для клиента SNTP для NetX Duo задается версия 3.

**NX_SNTP_CLIENT_MIN_SERVER_STRATUM**  
Самый низкий уровень (наибольшее числовое значение) сервера SNTP (страта), который принимает клиент. По умолчанию для клиента SNTP для NetX Duo задается уровень 2.

**NX_SNTP_CLIENT_MIN_TIME_ADJUSTMENT**  
Минимальная корректировка времени в миллисекундах, начиная с которой клиент будет обновлять часы местного времени. Любые корректировки меньше этого значения будут игнорироваться. По умолчанию для клиента SNTP для NetX Duo задается значение 10.

**NX_SNTP_CLIENT_MAX_TIME_ADJUSTMENT**  
Максимальная корректировка времени в миллисекундах, до которой клиент будет обновлять часы местного времени. Если потребуется корректировка больше этого значения, часы местного времени будут скорректированы только на это максимальное значение. По умолчанию для клиента SNTP для NetX Duo задается значение 180 000 (3 минуты).

**NX_SNTP_CLIENT_IGNORE_MAX_ADJUST_STARTUP**  
Этот параметр позволяет пропустить проверку максимального времени корректировки при получении первого обновления от сервера времени. После этого всегда проверяется максимальное время корректировки. Это нужно, чтобы синхронизация клиента с часами сервера произошла как можно скорее. По умолчанию для клиента SNTP для NetX Duo задается значение NX_TRUE.

**NX_SNTP_CLIENT_MAX_TIME_LAPSE**  
Максимальное допустимое время (в секундах), которое может пройти без получения клиентом SNTP допустимого обновления времени. Клиент SNTP будет продолжать работу, но для сервера SNTP устанавливается состояние NX_FALSE. По умолчанию используется значение 7200.


**NX_SNTP_UPDATE_TIMEOUT_INTERVAL**  
Интервал (в секундах), через который таймер клиента SNTP обновляет оставшееся время с момента получения клиентом SNTP последнего допустимого обновления, а клиент в одноадресном режиме обновляет оставшееся время опроса перед отправкой следующего запроса на обновление SNTP. Значение по умолчанию — 1.

**NX_SNTP_CLIENT_UNICAST_POLL_INTERVAL**  
Начальный интервал опроса (в секундах), по прошествии которого клиент отправляет запрос на сервер SNTP в одноадресном режиме. По умолчанию для клиента SNTP для NetX Duo задается значение 3600.

**NX_SNTP_CLIENT_EXP_BACKOFF_RATE**  
Коэффициент, на который умножается текущий интервал опроса на клиенте в одноадресном режиме. Если клиенту не удается получить обновление времени с сервера или сервер сообщает о временной недоступности службы обновления времени (например, он еще не синхронизирован), текущий интервал опроса увеличится в указанное здесь количество раз, но не более значения NX_SNTP_CLIENT_MAX_TIME_LAPSE. Значение по умолчанию — 2

**NX_SNTP_CLIENT_RTT_REQUIRED**  
Если включен этот параметр, клиент SNTP должен вычислять время кругового пути для сообщений SNTP при применении обновлений сервера к часам местного времени. По умолчанию используется значение NX_FALSE (отключено).

**NX_SNTP_CLIENT_MAX_ROOT_DISPERSION**  
Максимальная допустимая для клиента дисперсия серверных часов (в микросекундах), которая является мерой точности серверных часов. Чтобы отключить это требование, задайте для параметра максимальной дисперсии значение 0x0. По умолчанию для клиента SNTP для NetX Duo задается значение 50 000.

**NX_SNTP_CLIENT_INVALID_UPDATE_LIMIT**  
Ограничение на количество последовательных недопустимых обновлений, полученных от сервера в режиме широковещательной или одноадресной трансляции. При достижении этого предела клиент устанавливает для текущего сервера SNTP состояние "недопустимо" (NX_FALSE), но при этом будет продолжать попытки получения обновлений от этого сервера. По умолчанию для клиента SNTP для NetX Duo задается значение 3.

**NX_SNTP_CLIENT_RANDOMIZE_ON_STARTUP**  
Этот параметр определяет, должен ли клиент SNTP в одноадресном режиме отправлять первый запрос SNTP к текущему сервера SNTP через случайный интервал ожидания. Он используется, когда одновременно запускается значительное количество клиентов SNTP, чтобы не допустить перегрузки сервера SNTP. По умолчанию используется значение NX_FALSE (отключено).

**NX_SNTP_CLIENT_SLEEP_INTERVAL**  
Интервал времени, в течение которого задача SNTP находится в спящем режиме. Это позволяет клиенту SNTP выполнять вызовы API приложения. По умолчанию задается 1 такт таймера.

**NX_SNTP_CURRENT_YEAR**  
Чтобы отобразить дату в формате "год/месяц/дата", присвойте этому параметру значение не выше текущего года (не обязательно тот же год, который указан в вычисляемом времени NTP). По умолчанию используется значение 2015.

**NTP_SECONDS_AT_01011999**  
Время в секундах с начала первой эпохи NTP на главных часах NTP. Оно определяется как 0xBA368E80. Чтобы отключить отображение секунд NTP в виде даты и времени, установите здесь нулевое значение.
