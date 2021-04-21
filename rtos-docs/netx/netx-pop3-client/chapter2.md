---
title: Глава 2. Установка и использование POP3-клиента NetX для ОСРВ Azure
description: POP3-клиент NetX содержит один исходный файл, один файл заголовка и демонстрационный файл. Для служб дайджеста MD5 доступно два дополнительных файла.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24de396c69d458866f9423fd995bcb8d905f29c8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815163"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a><span data-ttu-id="438d3-104">Глава 2. Установка и использование POP3-клиента NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="438d3-104">Chapter 2 - Installation and use of Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="438d3-105">POP3-клиент NetX содержит один исходный файл, один файл заголовка и демонстрационный файл.</span><span class="sxs-lookup"><span data-stu-id="438d3-105">NetX POP3 Client includes one source file, one header file, and a demo file.</span></span> <span data-ttu-id="438d3-106">Для служб дайджеста MD5 доступно два дополнительных файла.</span><span class="sxs-lookup"><span data-stu-id="438d3-106">There are two additional files for MD5 digest services.</span></span> <span data-ttu-id="438d3-107">Также есть PDF-файл с руководством пользователя (этот документ).</span><span class="sxs-lookup"><span data-stu-id="438d3-107">There is also a User Guide PDF file (this document).</span></span>

- <span data-ttu-id="438d3-108">**nx_pop3_client.c**: исходный файл C для API POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="438d3-108">**nx_pop3_client.c**: C Source file for NetX POP3 Client API</span></span>
- <span data-ttu-id="438d3-109">**nx_pop3_client.h**: файл заголовка C для API POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="438d3-109">**nx_pop3_client.h**: C Header file for NetX POP3 Client API</span></span>
- <span data-ttu-id="438d3-110">**demo_netxduo_pop3_client.c**: демонстрационный файл для создания POP3-клиента и инициации сеанса</span><span class="sxs-lookup"><span data-stu-id="438d3-110">**demo_netxduo_pop3_client.c**: Demo file for POP3 Client creation and session initiation</span></span>
- <span data-ttu-id="438d3-111">**nx_md5.c**: исходный файл C, определяющий службы дайджеста MD5</span><span class="sxs-lookup"><span data-stu-id="438d3-111">**nx_md5.c**: C Source file defining MD5 digest services</span></span>
- <span data-ttu-id="438d3-112">**nx_md5.h**: файл заголовка C, определяющий службы дайджеста MD5</span><span class="sxs-lookup"><span data-stu-id="438d3-112">**nx_md5.h**: C Header file defining MD5 digest services</span></span>
- <span data-ttu-id="438d3-113">**nx_pop3_client.pdf**: руководство пользователя POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="438d3-113">**nx_pop3_client.pdf**: NetX POP3 Client User Guide</span></span>

<span data-ttu-id="438d3-114">Чтобы использовать POP3-клиент для NetX, весь дистрибутив, упомянутый ранее, должен быть скопирован в тот же каталог, где установлен NetX.</span><span class="sxs-lookup"><span data-stu-id="438d3-114">To use NetX POP3 Client, the entire distribution mentioned previously can be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="438d3-115">Например, если NetX установлен в каталоге *\threadx\mcf5272\green*, то файлы *nx_md5.h*, *nx_md5.c*, *nx_pop3_client.h и nx_pop3_client.c* должны быть скопированы в этот же каталог.</span><span class="sxs-lookup"><span data-stu-id="438d3-115">For example, if NetX is installed in the directory "*\threadx\mcf5272\green*" then the *nx_md5.h*, *nx_md5.c,* *nx_pop3_client.h, and nx_pop3_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-pop3-client"></a><span data-ttu-id="438d3-116">Использование POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="438d3-116">Using NetX POP3 Client</span></span>

<span data-ttu-id="438d3-117">Для использования службы POP3-клиента NetX приложение должно добавить файл *nx_pop3_client.c* в свой проект сборки.</span><span class="sxs-lookup"><span data-stu-id="438d3-117">To use the NetX POP3 Client service, the application must add *nx_pop3_client.c* to its build project.</span></span> <span data-ttu-id="438d3-118">Для использования ThreadX и NetX в код приложения следует включить файлы *nx_md5.h, nx_pop3.h и nx_pop3_client.h* после файлов *tx_api.h* и *nx_api.h*.</span><span class="sxs-lookup"><span data-stu-id="438d3-118">The application code must include *nx_md5.h, nx_pop3.h and nx_pop3_client.h* after *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span>

<span data-ttu-id="438d3-119">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их объектный код должен быть связан с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="438d3-119">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="438d3-120">Это все, что необходимо для использования POP3-клиента NetX.</span><span class="sxs-lookup"><span data-stu-id="438d3-120">This is all that is required to use the NetX POP3 Client.</span></span>

## <a name="small-example-of-the-netx-pop3-client"></a><span data-ttu-id="438d3-121">Небольшой пример POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="438d3-121">Small Example of the NetX POP3 Client</span></span>

<span data-ttu-id="438d3-122">Пример использования служб POP3-клиента NetX приведен на рис. 1 ниже.</span><span class="sxs-lookup"><span data-stu-id="438d3-122">An example of how to use NetX POP3 Client services is described in Figure 1 that appears below.</span></span> <span data-ttu-id="438d3-123">В нем настраиваются два обратных вызова для уведомления о скачивании почты и завершении сеанса в строках 37 и 38.</span><span class="sxs-lookup"><span data-stu-id="438d3-123">This demo sets up the two callbacks for notification of mail download and session completion on lines 37 and 38.</span></span> <span data-ttu-id="438d3-124">Пул пакетов POP3-клиента создается в строке 76.</span><span class="sxs-lookup"><span data-stu-id="438d3-124">The POP3 Client packet pool is created on line 76.</span></span> <span data-ttu-id="438d3-125">Задача потока IP создается в строке 88.</span><span class="sxs-lookup"><span data-stu-id="438d3-125">The IP thread task is created on line 88.</span></span> <span data-ttu-id="438d3-126">Обратите внимание, что этот пул пакетов также используется для пула пакетов POP3-клиента.</span><span class="sxs-lookup"><span data-stu-id="438d3-126">Note that this packet pool is also used for the POP3 Client packet pool.</span></span> <span data-ttu-id="438d3-127">Протокол TCP включен для задачи IP в строке 107.</span><span class="sxs-lookup"><span data-stu-id="438d3-127">TCP is enabled on the IP task in line 107.</span></span>

<span data-ttu-id="438d3-128">POP3-клиент создается в строке 133 внутри функции входа в поток приложения *demo_thread_entry*.</span><span class="sxs-lookup"><span data-stu-id="438d3-128">The POP3 Client is created on line 133 inside the application thread entry function, *demo_thread_entry*.</span></span> <span data-ttu-id="438d3-129">Это связано с тем, что служба *nx_pop3_client_create* также пытается установить TCP-подключение к POP3-серверу.</span><span class="sxs-lookup"><span data-stu-id="438d3-129">This is because the *nx_pop3_client_create* service also attempts to make a TCP connection with the POP3 server.</span></span> <span data-ttu-id="438d3-130">В случае успеха приложение запрашивает у POP3-сервера количество элементов в его почтовом ящике в строке 149 с помощью службы *nx_pop3_client_mail_items_get*.</span><span class="sxs-lookup"><span data-stu-id="438d3-130">If successful, the application queries the POP3 server for the number of items in its maildrop on line 149 using the *nx_pop3_client_mail_items_get* service.</span></span>

<span data-ttu-id="438d3-131">Если в ящике находится один элемент или несколько элементов, приложение выполняет итерацию цикла while для каждого почтового элемента, чтобы скачать почтовое сообщение.</span><span class="sxs-lookup"><span data-stu-id="438d3-131">If there are one or more items, the application iterates through the while loop for each mail item to download the mail message.</span></span> <span data-ttu-id="438d3-132">Запрос на RETR выполняется в строке 149 в вызове службы *nx_pop3_client_mail_item_get*.</span><span class="sxs-lookup"><span data-stu-id="438d3-132">The RETR request is made on line 149 in the *nx_pop3_client_mail_item_get* call.</span></span> <span data-ttu-id="438d3-133">В случае успешного выполнения запроса приложение скачивает пакеты с помощью службы *nx_pop3_client_mail_item_message_get* в строке 177, пока не обнаружит, что получен последний пакет в сообщении в строке 196.</span><span class="sxs-lookup"><span data-stu-id="438d3-133">If successful, the application downloads packets using the *nx_pop3_client_mail_item_message_get* service on line 177 till it detects the last packet in the message has been received on line 196.</span></span> <span data-ttu-id="438d3-134">Наконец, приложение удаляет почтовый элемент, предполагая успешное завершение скачивания в строке 199 в вызове службы *nx_pop3_client_mail_item_delete*.</span><span class="sxs-lookup"><span data-stu-id="438d3-134">Lastly, the application deletes the mail item, assuming a successful download has occurred on line 199 in *the nx_pop3_client_mail_item_delete* call.</span></span> <span data-ttu-id="438d3-135">В соответствии со стандартом RFC 1939 рекомендуется, чтобы POP3-клиенты указывали серверу удалять скачанные почтовые элементы, чтобы избежать накопления почты в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="438d3-135">The RFC 1939 recommends that POP3 Clients instruct the Server to delete downloaded mail items to prevent mail accumulating in the Client's maildrop.</span></span> <span data-ttu-id="438d3-136">В любом случае сервер может сделать это автоматически.</span><span class="sxs-lookup"><span data-stu-id="438d3-136">The Server may automatically do so anyway.</span></span>

<span data-ttu-id="438d3-137">После скачивания всех почтовых элементов или в случае сбоя вызова службы POP3-клиента приложение выходит из цикла и удаляет POP3-клиент в строке 217 с помощью службы *nx_pop3_client_delete*.</span><span class="sxs-lookup"><span data-stu-id="438d3-137">Once all the mail items are downloaded, or if a POP3 Client service call fails, the application exits of the loop and deletes the POP3 Client on line 217 using the *nx_pop3_client_delete* service.</span></span>

```c
/*
    demo_netxduo_pop3.c

    This is a small demo of POP3 Client on the NetX TCP/IP stack.
    This demo relies on Thread, NetX and POP3 Client API to conduct
    a POP3 mail session.
*/

#include "tx_api.h"
#include "nx_api.h"
#include "nx_pop3_client.h"

#define DEMO_STACK_SIZE        4096
#define CLIENT_ADDRESS         IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS         IP_ADDRESS(192,2,2,89)
#define SERVER_PORT            110

/* Replace the 'ram' driver with your own Ethernet driver. */
void _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client. */

TX_THREAD          demo_client_thread;
NX_POP3_CLIENT     demo_client;
NX_PACKET_POOL     client_packet_pool;
NX_IP              client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void     demo_thread_entry(ULONG info);

/* Shared secret is the same as password. */

#define LOCALHOST              "recipient@domain.com"
#define LOCALHOST_PASSWORD     "testpwd"

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *free_memory_pointer;

    /* Setup the working pointer. */
    free_memory_pointer = first_unused_memory;

    /* Create a client thread. */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                    free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer = free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* The demo client username and password is the authentication
    data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status = nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                        PAYLOAD_SIZE, free_memory_pointer, (PAYLOAD_SIZE * 10));
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + (PAYLOAD_SIZE * 10);

    /* Create IP instance for demo Client */
    status = nx_ip_create(&client_ip, "POP3 Client IP Instance",
                            CLIENT_ADDRESS, 0xFFFFFF00UL, &client_packet_pool,
                            _nx_ram_network_driver, free_memory_pointer,
                            2048, 1);

    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 2048;

    /* Enable ARP and supply ARP cache memory. */
    nx_arp_enable(&client_ip, (void **) free_memory_pointer, 1024);

    /* Update pointer to unallocated (free) memory. */
    free_memory_pointer = free_memory_pointer + 1024;

    /* Enable TCP and ICMP for Client IP. */
    nx_tcp_enable(&client_ip);
    nx_icmp_enable(&client_ip);

    return;
}

/* Define the application thread entry function. */

void demo_thread_entry(ULONG info)
{

UINT          status;
UINT          mail_item, number_mail_items;
UINT          bytes_downloaded = 0;
UINT          final_packet = NX_FALSE;
ULONG         total_size, mail_item_size, bytes_retrieved;
NX_PACKET     *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);

    /* Create a NetX POP3 Client instance with no byte or block memory pools.
    Note that it uses its password for its APOP shared secret. */
    status = nx_pop3_client_create(&demo_client,
                        NX_TRUE,
                        &client_ip, &client_packet_pool, SERVER_ADDRESS,
                        SERVER_PORT, LOCALHOST, LOCALHOST_PASSWORD);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        status = nx_pop3_client_delete(&demo_client);

        /* Abort. */
        return;
    }

    /* Find out how many items are in our mailbox. */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items, &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {
        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items. */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {

        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item, &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely downloaded. */

        while((final_packet == NX_FALSE) && (status == NX_SUCCESS))
        {
            status = nx_pop3_client_mail_item_message_get(&demo_client, &packet_ptr,
                                                        &bytes_retrieved,
                                                        &final_packet);

            if (status != NX_SUCCESS)
            {
                break;
            }

            if (bytes_retrieved != 0)
            {

            printf("Received %d bytes of data for item %d: %s\n",
                    packet_ptr -> nx_packet_length,
                    mail_item, packet_ptr -> nx_packet_prepend_ptr);
            }

            nx_packet_release(packet_ptr);

            /* Determine if this is the last data packet. */
            if (final_packet)
            {
                /* It is. Let the server know it can delete this mail item. */
                status = nx_pop3_client_mail_item_delete(&demo_client, mail_item);
            }

            /* Keep track of how much mail message data is left. */
            bytes_downloaded += bytes_retrieved;
        }

        /* Get the next mail item. */
        mail_item++;

        tx_thread_sleep(100);
    }

    /* Disconnect from the POP3 server. */
    status = nx_pop3_client_quit(&demo_client);

    /* Delete the POP3 Client. This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

<span data-ttu-id="438d3-138">Рис. 1.</span><span class="sxs-lookup"><span data-stu-id="438d3-138">Figure 1.</span></span> <span data-ttu-id="438d3-139">Пример приложения POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="438d3-139">Example of a NetX POP3 Client application</span></span>

## <a name="pop3-client-configuration-options"></a><span data-ttu-id="438d3-140">Параметры конфигурации POP3-клиента</span><span class="sxs-lookup"><span data-stu-id="438d3-140">POP3 Client Configuration Options</span></span>

<span data-ttu-id="438d3-141">Существует несколько параметров конфигурации POP3-клиента NetX.</span><span class="sxs-lookup"><span data-stu-id="438d3-141">There are several configuration options with the NetX POP3 Client.</span></span> <span data-ttu-id="438d3-142">Ниже приведен список всех параметров с подробным описанием.</span><span class="sxs-lookup"><span data-stu-id="438d3-142">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="438d3-143">**NX_POP3_CLIENT_PACKET_TIMEOUT**: параметр ожидания в секундах для выделения пакета POP3-клиентом.</span><span class="sxs-lookup"><span data-stu-id="438d3-143">**NX_POP3_CLIENT_PACKET_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to allocate a packet.</span></span> <span data-ttu-id="438d3-144">Значение по умолчанию — 1 секунда.</span><span class="sxs-lookup"><span data-stu-id="438d3-144">The default value is 1 second.</span></span>

- <span data-ttu-id="438d3-145">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: параметр ожидания в секундах для подключения POP3-клиента к POP3-серверу.</span><span class="sxs-lookup"><span data-stu-id="438d3-145">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to connect with the POP3 Server.</span></span> <span data-ttu-id="438d3-146">Значение по умолчанию - 30 секунды.</span><span class="sxs-lookup"><span data-stu-id="438d3-146">The default value is 30 seconds.</span></span>

- <span data-ttu-id="438d3-147">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: параметр ожидания в секундах для отключения POP3-клиента от POP3-сервера.</span><span class="sxs-lookup"><span data-stu-id="438d3-147">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: This defines the wait option in seconds for the POP3 Client to disconnect from the POP3 Server.</span></span> <span data-ttu-id="438d3-148">Значение по умолчанию — 2 секунды.</span><span class="sxs-lookup"><span data-stu-id="438d3-148">The default value is 2 seconds.</span></span>

- <span data-ttu-id="438d3-149">**NX_POP3_TCP_SOCKET_SEND_WAIT**: параметр ожидания в секундах в вызовах службы *nx_tcp_socket_send*.</span><span class="sxs-lookup"><span data-stu-id="438d3-149">**NX_POP3_TCP_SOCKET_SEND_WAIT**: This option sets the wait option in seconds in *nx_tcp_socket_send* service calls.</span></span> <span data-ttu-id="438d3-150">Значение по умолчанию — 2 секунды.</span><span class="sxs-lookup"><span data-stu-id="438d3-150">The default value is 2 seconds.</span></span>

- <span data-ttu-id="438d3-151">**NX_POP3_SERVER_REPLY_TIMEOUT**: параметр ожидания в вызовах службы *nx_tcp_socket_receive* для ответа сервера на запрос клиента.</span><span class="sxs-lookup"><span data-stu-id="438d3-151">**NX_POP3_SERVER_REPLY_TIMEOUT**: This option sets the wait option in *nx_tcp_socket_receive* service calls for the Server reply to a Client request.</span></span> <span data-ttu-id="438d3-152">Значение по умолчанию — 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="438d3-152">The default value is 10 seconds.</span></span>

- <span data-ttu-id="438d3-153">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: задает размер окна получения TCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="438d3-153">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="438d3-154">В качестве значения параметра следует задать размер MTU экземпляра IP минус размер IP и размер заголовка TCP.</span><span class="sxs-lookup"><span data-stu-id="438d3-154">This should be set to the IP instance MTU size minus the IP and TCP header.</span></span> <span data-ttu-id="438d3-155">Значение по умолчанию — 1460.</span><span class="sxs-lookup"><span data-stu-id="438d3-155">The default value is 1460.</span></span>

- <span data-ttu-id="438d3-156">**NX_POP3_MAX_USERNAME**: задает размер буфера имени пользователя POP3-клиента.</span><span class="sxs-lookup"><span data-stu-id="438d3-156">**NX_POP3_MAX_USERNAME**: This option sets the size of the buffer of the POP3 Client user name.</span></span> <span data-ttu-id="438d3-157">Значение по умолчанию — 40 байт.</span><span class="sxs-lookup"><span data-stu-id="438d3-157">The default value is 40 bytes.</span></span>

- <span data-ttu-id="438d3-158">**NX_POP3_MAX_USERNAME**: задает размер буфера пароля POP3-клиента.</span><span class="sxs-lookup"><span data-stu-id="438d3-158">**NX_POP3_MAX_PASSWORD**: This option sets the size of the buffer of the POP3 Client password.</span></span> <span data-ttu-id="438d3-159">Значение по умолчанию — 20 байт.</span><span class="sxs-lookup"><span data-stu-id="438d3-159">The default value is 20 bytes.</span></span>