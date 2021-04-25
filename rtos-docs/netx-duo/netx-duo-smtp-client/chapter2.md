---
title: Глава 2. Установка и использование клиента SMTP для NetX Duo
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиента SMTP для NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86f324935ba32aab010b81f825be0a6564983a2e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814576"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a><span data-ttu-id="3f580-103">Глава 2. Установка и использование клиента SMTP для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3f580-103">Chapter 2 - Installation and use of NetX Duo SMTP client</span></span>

<span data-ttu-id="3f580-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиента SMTP для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Duo SMTP Client component.</span></span>

## <a name="netx-duo-smtp-client-installation"></a><span data-ttu-id="3f580-105">Установка клиента SMTP для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3f580-105">NetX Duo SMTP Client Installation</span></span>

<span data-ttu-id="3f580-106">Клиент SMTP для NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="3f580-106">The NetX Duo SMTP Client is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="3f580-107">В состав пакета входят следующие файлы.</span><span class="sxs-lookup"><span data-stu-id="3f580-107">The package includes the following files:</span></span>

- <span data-ttu-id="3f580-108">**nxd_smtp_client.c** — файл исходного кода C API клиента SMTP для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-108">**nxd_smtp_client.c** C Source file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="3f580-109">**nxd_smtp_client.h** — файл заголовка C API клиента SMTP для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-109">**nxd_smtp_client.h** C Header file for NetX Duo SMTP Client API</span></span>
- <span data-ttu-id="3f580-110">**demo_netxduo_smtp_client.c** — демонстрация клиента SMTP для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-110">**demo_netxduo_smtp_client.c** Demo for NetX Duo SMTP Client</span></span>
- <span data-ttu-id="3f580-111">**nxd_smtp_client.pdf** — руководство пользователя по API клиента SMTP для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-111">**nxd_smtp_client.pdf User Guide for** NetX Duo SMTP Client API</span></span>

<span data-ttu-id="3f580-112">Для использования API клиента SMTP для NetX Duo необходимо скопировать все упомянутые выше файлы дистрибутива в каталог установки NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-112">To use the NetX Duo SMTP Client API, the entire distribution mentioned previously may be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="3f580-113">Например, если NetX Duo установлен в каталог "c: *\myproject*", то файлы *nxd_smtp_client.h и nxd_smtp_client.c* необходимо скопировать в этот же каталог.</span><span class="sxs-lookup"><span data-stu-id="3f580-113">For example, if NetX Duo is installed in the directory “c:*\myproject*” then the *nxd_smtp_client.h, and nxd_smtp_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-smtp-client"></a><span data-ttu-id="3f580-114">Использование клиента SMTP для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="3f580-114">Using NetX Duo SMTP Client</span></span>

<span data-ttu-id="3f580-115">Чтобы создать клиентское приложение SMTP для NetX Duo, сначала необходимо создать библиотеки ThreadX и NetX Duo и включить их в проект сборки.</span><span class="sxs-lookup"><span data-stu-id="3f580-115">To create the NetX Duo SMTP Client application, it must first build the ThreadX and NetX Duo libraries and include them in the build project.</span></span> <span data-ttu-id="3f580-116">Затем необходимо включить *tx_api.h* и *nx_api.h в исходный код приложения*.</span><span class="sxs-lookup"><span data-stu-id="3f580-116">The application must then include tx *_api.h* and *nx_api.h in its application source code*.</span></span> <span data-ttu-id="3f580-117">Это позволит использовать службы ThreadX и NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-117">This will enable ThreadX and NetX Duo services.</span></span> <span data-ttu-id="3f580-118">Для использования служб клиента SMTP необходимо после *tx_api.h* и *nx_api.h* также включить файлы *nxd_smtp_client.c* и *nxd_smtp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="3f580-118">It must also include *nxd_smtp_client.c* and *nxd_smtp_client.h* after *tx_api.h* and *nx_api.h to use SMTP Client services.*</span></span>

<span data-ttu-id="3f580-119">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их объектный код должен быть связан с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="3f580-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="3f580-120">Это все, что необходимо для создания клиентского приложения SMTP для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3f580-120">This is all that is required to create a NetX Duo SMTP Client application.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="3f580-121">Небольшой пример системы</span><span class="sxs-lookup"><span data-stu-id="3f580-121">Small Example System</span></span>

<span data-ttu-id="3f580-122">Пример использования клиента SMTP для NetX Duo приведен на рисунке 1 ниже.</span><span class="sxs-lookup"><span data-stu-id="3f580-122">An example of using the NetX Duo SMTP Client is described in Figure 1 that appears below.</span></span> <span data-ttu-id="3f580-123">Пул пакетов для экземпляра IP создается с помощью службы nx_packet_pool_create в строке 68 и имеет очень небольшую полезную нагрузку пакета.</span><span class="sxs-lookup"><span data-stu-id="3f580-123">The packet pool for the IP instance is created using the nx_packet_pool_create service, on line 68 and has a very small packet payload.</span></span> <span data-ttu-id="3f580-124">Это происходит потому, что экземпляр IP отправляет только управляющие пакеты, которые не нуждаются в большой нагрузке.</span><span class="sxs-lookup"><span data-stu-id="3f580-124">This is because the IP instance only sends control packets which don’t require much payload.</span></span> <span data-ttu-id="3f580-125">Пул пакетов клиента SMTP создается в строке 84 и используется для передачи сообщений клиента SMTP на сервер и данных сообщений.</span><span class="sxs-lookup"><span data-stu-id="3f580-125">The SMTP Client packet pool created on line 84 and is used for transmitting SMTP Client messages to the server and message data.</span></span> <span data-ttu-id="3f580-126">Его полезная нагрузка пакетов гораздо больше.</span><span class="sxs-lookup"><span data-stu-id="3f580-126">Its packet payload is much larger.</span></span> <span data-ttu-id="3f580-127">Экземпляр IP создается в строке 118 с помощью того же пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="3f580-127">The IP instance is created in line 118 using the same packet pool.</span></span> <span data-ttu-id="3f580-128">Протокол TCP, необходимый для протокола SMTP, включается в экземпляре IP в строке 130.</span><span class="sxs-lookup"><span data-stu-id="3f580-128">TCP, required for the SMTP protocol, is enabled on the IP instance in line 130.</span></span>

<span data-ttu-id="3f580-129">В потоке приложения клиент SMTP создается с помощью службы *nxd_smtp_client_create* в строке 170.</span><span class="sxs-lookup"><span data-stu-id="3f580-129">In the application thread, the SMTP Client is created using the *nxd_smtp_client_create* service, in line 170.</span></span> <span data-ttu-id="3f580-130">Служба *nxd_smtp_client_create* поддерживает подключения SMTP-сервера по протоколам IPv4 и IPv6, хотя в данном примере используется только IPv4.</span><span class="sxs-lookup"><span data-stu-id="3f580-130">The *nxd_smtp_client_create* service supports both IPv4 and IPv6 SMTP server connections although this example is limited to IPv4.</span></span> <span data-ttu-id="3f580-131">Затем в строке 184 почтовое сообщение отправляется клиенту SMTP для передачи с помощью службы *nx_smtp_mail_send*.</span><span class="sxs-lookup"><span data-stu-id="3f580-131">Then the mail message is submitted to the SMTP Client for transmission on line 184 using the *nx_smtp_mail_send* service.</span></span> <span data-ttu-id="3f580-132">Обратите внимание, что строка темы с заголовком содержимого почты создается отдельно от текста сообщения.</span><span class="sxs-lookup"><span data-stu-id="3f580-132">Note that the subject line with the mail content header is created separately from the message body.</span></span> <span data-ttu-id="3f580-133">Также обратите внимание, что запрос на отправку почты принимает только один почтовый адрес получателя, который считается синтаксически правильным.</span><span class="sxs-lookup"><span data-stu-id="3f580-133">Also note that the send mail request accepts only one recipient mail address which is assumed to be syntactically correct.</span></span>

<span data-ttu-id="3f580-134">Затем приложение завершает работу клиента SMTP в строке 200.</span><span class="sxs-lookup"><span data-stu-id="3f580-134">Then the application terminates the SMTP Client on line 200.</span></span> <span data-ttu-id="3f580-135">Служба *nx_smtp_client_delete* проверяет, что подключение к сокету закрыто и порт не привязан.</span><span class="sxs-lookup"><span data-stu-id="3f580-135">The *nx_smtp_client_delete* service checks that the socket connection is closed and the port is unbound.</span></span> <span data-ttu-id="3f580-136">Обратите внимание, что клиентское приложение SMTP удаляет пул пакетов, если он больше не используется.</span><span class="sxs-lookup"><span data-stu-id="3f580-136">Note that it is up to the SMTP Client application to delete the packet pool if it no longer has use for it.</span></span>

```c
/*
   demo_netxduo_smtp_client.c

   This is a small demo of the NetX Duo SMTP Client on the high-performance NetX
   Duo TCP/IP stack.  This demo relies on Thread, NetX Duo and SMTP Client API to
   perform simple SMTP mail transfers in an SMTP client application to an SMTP mail
   server.   */

#include "nx_api.h"
#include "nx_ip.h"
#include "nxd_smtp_client.h"


/* Define the host user name and mail box parameters */
#define USERNAME               "myusername"
#define PASSWORD               "mypassword"
#define FROM_ADDRESS           "my@mycompany.com"
#define RECIPIENT_ADDRESS      "your@yourcompany.com"
#define LOCAL_DOMAIN           "mycompany.com"

#define SUBJECT_LINE           "NetX Duo SMTP Client Demo"
#define MAIL_BODY              "NetX Duo SMTP client is an SMTP client \r\n" \
                               “implementation for embedded devices to send  \r\n" \
                               "email to SMTP servers. This feature is \r\n" \
                               "intended to allow a device to send simple \r\n " \
                               "status reports using the most universal \r\n " \
                               “Internet application, email.\r\n"

/* See the NetX Duo SMTP Client User Guide for how to set the authentication type.
   The most common authentication type is PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE 3


#define CLIENT_IP_ADDRESS  IP_ADDRESS(1,2,3,5)
#define SERVER_IP_ADDRESS  IP_ADDRESS(1,2,3,4)
#define SERVER_PORT        25


/* Define the NetX Duo and ThreadX structures for the SMTP client appliciation. */
NX_PACKET_POOL                  ip_packet_pool;
NX_PACKET_POOL                  client_packet_pool;
NX_IP                           client_ip;
TX_THREAD                       demo_client_thread;
static NX_SMTP_CLIENT           demo_client;


void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
void    demo_client_thread_entry(ULONG info);

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
    CHAR    *free_memory_pointer;


    /* Setup the pointer to unallocated memory.  */
    free_memory_pointer =  (CHAR *) first_unused_memory;

    /* Create IP default packet pool. */
    status =  nx_packet_pool_create(&ip_packet_pool, "Default IP Packet Pool",
                                    128, free_memory_pointer, 2048);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Create SMTP Client packet pool. This is only for transmitting packets to the
       server. It need not be a separate packet pool than the IP default packet pool
       but for more efficient resource use, we use two different packet pools
       because the CLient SMTP messages generally require more payload than IP
       control packets.

       Packet payload depends on the SMTP Client application requirements.  Size of
       packet payload must include IP and TCP headers. For IPv6 connections, IP and
       TCP header data is 60 bytes. For IPv4 IP and TCP header data is 40 bytes (not
       including TCP options). */
    status |=  nx_packet_pool_create(&client_packet_pool, "SMTP Client Packet Pool",
                                     800, free_memory_pointer, (10*800));

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (10*800);

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the client thread */
    status = tx_thread_create(&demo_client_thread, "client_thread",
                              demo_client_thread_entry, 0, free_memory_pointer,
                              2048, 16, 16,
                              TX_NO_TIME_SLICE, TX_DONT_START);

    if (status != NX_SUCCESS)
    {

        printf("Error creating Client thread. Status 0x%x\r\n", status);
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer =  free_memory_pointer + 4096;


    /* Create Client IP instance. Remember to replace the generic driver
       with a real ethernet driver to actually run this demo! */

    status = nx_ip_create(&client_ip, "SMTP Client IP Instance", CLIENT_IP_ADDRESS,
                          0xFFFFFF00UL, &ip_packet_pool, _nx_ram_network_driver,
                          free_memory_pointer, 2048, 1);


    free_memory_pointer =  free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    status =  nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1040);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1040;

    /* Enable TCP for client. */
    status =  nx_tcp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable ICMP for client. */
    status =  nx_icmp_enable(&client_ip);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Start the client thread. */
    tx_thread_resume(&demo_client_thread);

    return;
}


/* Define the smtp application thread task.   */
void    demo_client_thread_entry(ULONG info)
{

    UINT        status;
    UINT        error_counter = 0;
    NXD_ADDRESS server_ip_address;


    tx_thread_sleep(100);

    /* Set up the server IP address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    status =  nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
                                     USERNAME,
                                     PASSWORD,
                                     FROM_ADDRESS,
                                     LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
                                     &server_ip_address, SERVER_PORT);

    if (status != NX_SUCCESS)
    {
        printf("Error creating the client. Status: 0x%x.\n\r", status);
        return;
    }

    /* Create a mail instance with the above text message and recipient info. */
    status =  nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
                                TP_MAIL_PRIORITY_NORMAL,
                                SUBJECT_LINE, MAIL_BODY, sizeof(MAIL_BODY) - 1);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        /* Mail item was not sent. Note that we need not delete the client. The
           error status may be a failed authentication check or a broken connection.
           We can simply call nx_smtp_mail_send again.  */
        error_counter++;
    }

    /* Release resources used by client. Note that the transmit packet
       pool must be deleted by the application if it no longer has use for it.*/
    status = nx_smtp_client_delete(&demo_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    return;
}
```

<span data-ttu-id="3f580-137">**Рисунок 1. Пример использования клиента SMTP с NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="3f580-137">**Figure 1. Example of SMTP Client use with NetX Duo**</span></span>

## <a name="client-configuration-options"></a><span data-ttu-id="3f580-138">Параметры конфигурации клиента</span><span class="sxs-lookup"><span data-stu-id="3f580-138">Client Configuration Options</span></span>

<span data-ttu-id="3f580-139">В API клиента SMTP для NetX Duo есть несколько параметров для настройки.</span><span class="sxs-lookup"><span data-stu-id="3f580-139">There are several configuration options with the NetX Duo SMTP Client API.</span></span> <span data-ttu-id="3f580-140">Ниже приведен список всех параметров с подробным описанием.</span><span class="sxs-lookup"><span data-stu-id="3f580-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="3f580-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** —этот параметр задает размер окна приема TCP клиента.</span><span class="sxs-lookup"><span data-stu-id="3f580-141">**NX_SMTP_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="3f580-142">Этот параметр должен иметь значение меньше размера MTU базового оборудования Ethernet и оставлять место для заголовков IP и TCP.</span><span class="sxs-lookup"><span data-stu-id="3f580-142">This should be set to below the MTU size of the underlying Ethernet hardware and allow room for IP and TCP headers.</span></span> <span data-ttu-id="3f580-143">По умолчанию размер окна TCP у клиента SMTP для NetX Duo равен 1460.</span><span class="sxs-lookup"><span data-stu-id="3f580-143">The default NetX Duo SMTP Client TCP window size is 1460.</span></span>
- <span data-ttu-id="3f580-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** —этот параметр задает время ожидания при выделении пакетов NetX.</span><span class="sxs-lookup"><span data-stu-id="3f580-144">**NX_SMTP_CLIENT_PACKET_TIMEOUT** This option sets the timeout on NetX packet allocation.</span></span> <span data-ttu-id="3f580-145">Время ожидания пакета клиента SMTP для NetX Duo по умолчанию равно 2 секунды.</span><span class="sxs-lookup"><span data-stu-id="3f580-145">The default NetX Duo SMTP Client packet timeout is 2 seconds.</span></span>
- <span data-ttu-id="3f580-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** —этот параметр задает время ожидания подключения TCP-сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="3f580-146">**NX_SMTP_CLIENT_CONNECTION_TIMEOUT** This option sets the Client TCP socket connect timeout.</span></span> <span data-ttu-id="3f580-147">Время ожидания подключения клиента SMTP для NetX Duo по умолчанию равно 10 секундам.</span><span class="sxs-lookup"><span data-stu-id="3f580-147">The default NetX Duo SMTP Client connect timeout is 10 seconds.</span></span>
- <span data-ttu-id="3f580-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** —этот параметр задает время ожидания отключения TCP-сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="3f580-148">**NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** This option sets the Client TCP socket disconnect timeout.</span></span> <span data-ttu-id="3f580-149">Время ожидания отключения клиента SMTP для NetX Duo по умолчанию равно 5 секундам\*.</span><span class="sxs-lookup"><span data-stu-id="3f580-149">The default NetX Duo SMTP Client disconnect timeout is 5 seconds\*.</span></span> <span data-ttu-id="3f580-150">Обратите внимание, что если клиент SMTP обнаруживает внутреннюю ошибку, такую как нарушение соединения, он может разорвать подключение с нулевым временем ожидания.</span><span class="sxs-lookup"><span data-stu-id="3f580-150">Note that if the SMTP Client encounters an internal error such as a broken connection it may terminate the connection with a zero wait timeout.</span></span>
- <span data-ttu-id="3f580-151">**NX_SMTP_GREETING_TIMEOUT** —этот параметр задает время ожидания, в течение которого клиент получает ответ сервера на приветствие.</span><span class="sxs-lookup"><span data-stu-id="3f580-151">**NX_SMTP_GREETING_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to its greeting.</span></span> <span data-ttu-id="3f580-152">Значение по умолчанию для клиента SMTP для NetX Duo равно 10 секундам.</span><span class="sxs-lookup"><span data-stu-id="3f580-152">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="3f580-153">**NX_SMTP_ENVELOPE_TIMEOUT** —этот параметр задает время ожидания, в течение которого клиент получает ответ сервера на команду клиента.</span><span class="sxs-lookup"><span data-stu-id="3f580-153">**NX_SMTP_ENVELOPE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to a Client command.</span></span> <span data-ttu-id="3f580-154">Значение по умолчанию для клиента SMTP для NetX Duo равно 10 секундам.</span><span class="sxs-lookup"><span data-stu-id="3f580-154">The default NetX Duo SMTP Client value is 10 seconds.</span></span>
- <span data-ttu-id="3f580-155">**NX_SMTP_MESSAGE_TIMEOUT** — этот параметр задает время ожидания, в течение которого клиент получает ответ сервера на получение данных почтового сообщения.</span><span class="sxs-lookup"><span data-stu-id="3f580-155">**NX_SMTP_MESSAGE_TIMEOUT** This option sets the timeout for the Client to receive the Server reply to receiving the mail message data.</span></span> <span data-ttu-id="3f580-156">Значение по умолчанию для клиента SMTP для NetX Duo равно 30 секундам.</span><span class="sxs-lookup"><span data-stu-id="3f580-156">The default NetX Duo SMTP Client value is 30 seconds.</span></span>
- <span data-ttu-id="3f580-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** — этот параметр определяет параметр ожидания буфера для сохранения пароля пользователя во время проверки подлинности SMTP на сервере.</span><span class="sxs-lookup"><span data-stu-id="3f580-157">**NX_SMTP_CLIENT_SEND_TIMEOUT** This option defines the wait option of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="3f580-158">Значение по умолчанию — 20 байт.</span><span class="sxs-lookup"><span data-stu-id="3f580-158">The default value is 20 bytes.</span></span>
- <span data-ttu-id="3f580-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** — этот параметр определяет размер буфера для извлечения запроса сервера во время проверки подлинности SMTP.</span><span class="sxs-lookup"><span data-stu-id="3f580-159">**NX_SMTP_SERVER_CHALLENGE_MAX_STRING** This option defines the size of the buffer for extracting the Server challenge during SMTP authentication.</span></span> <span data-ttu-id="3f580-160">Значение по умолчанию — 200 байт.</span><span class="sxs-lookup"><span data-stu-id="3f580-160">The default value is 200 bytes.</span></span> <span data-ttu-id="3f580-161">Для проверки подлинности LOGIN и PLAIN клиент SMTP, вероятно, может использовать буфер меньшего размера.</span><span class="sxs-lookup"><span data-stu-id="3f580-161">For LOGIN and PLAIN authentication, the SMTP Client can probably use a smaller buffer.</span></span>
- <span data-ttu-id="3f580-162">**NX_SMTP_CLIENT_MAX_PASSWORD** — этот параметр определяет размер буфера для хранения пароля пользователя во время проверки подлинности SMTP на сервере.</span><span class="sxs-lookup"><span data-stu-id="3f580-162">**NX_SMTP_CLIENT_MAX_PASSWORD** This option defines the size of the buffer to store the user password during SMTP authentication with the Server.</span></span> <span data-ttu-id="3f580-163">Значение по умолчанию — 20 байт.</span><span class="sxs-lookup"><span data-stu-id="3f580-163">The default value is 20 bytes.</span></span> 
- <span data-ttu-id="3f580-164">**NX_SMTP_CLIENT_MAX_USERNAME** — этот параметр определяет размер буфера для хранения имени узла пользователя во время проверки подлинности SMTP на сервере.</span><span class="sxs-lookup"><span data-stu-id="3f580-164">**NX_SMTP_CLIENT_MAX_USERNAME** This option defines the size of the buffer to store the host username during SMTP authentication with the Server.</span></span> <span data-ttu-id="3f580-165">Значение по умолчанию — 40 байт.</span><span class="sxs-lookup"><span data-stu-id="3f580-165">The default value is 40 bytes.</span></span> 
