---
title: Глава 2. Установка и использование клиента POP3 для NetX Duo
description: Клиент POP3 для NetX Duo содержит один исходный файл, один файл заголовка и демонстрационный файл.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6ef4b6ba7aadf77ab95a4a12235eda847f32f3d5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814616"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-pop3-client"></a><span data-ttu-id="cb608-103">Глава 2. Установка и использование клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="cb608-103">Chapter 2 - Installation and Use of NetX Duo POP3 Client</span></span>

<span data-ttu-id="cb608-104">Клиент POP3 для NetX содержит один исходный файл, один файл заголовка и демонстрационный файл.</span><span class="sxs-lookup"><span data-stu-id="cb608-104">NetX POP3 Client includes one source file, one header file, and a demo file.</span></span> <span data-ttu-id="cb608-105">Для служб хэша MD5 прилагаются два дополнительных файла.</span><span class="sxs-lookup"><span data-stu-id="cb608-105">There are two additional files for MD5 digest services.</span></span> <span data-ttu-id="cb608-106">Также есть PDF-файл с руководством пользователя (этот документ).</span><span class="sxs-lookup"><span data-stu-id="cb608-106">There is also a User Guide PDF file (this document).</span></span>

- <span data-ttu-id="cb608-107">**nx_pop3_client.c**: исходный файл С для API клиента POP3 для NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="cb608-107">**nxd_pop3_client.c** C Source file for NetX Duo POP3 Client API</span></span>
- <span data-ttu-id="cb608-108">**nxd_pop3_client.h**: файл заголовка C для API клиента POP3 для NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="cb608-108">**nxd_pop3_client.h** C Header file for NetX Duo POP3 Client API</span></span>
- <span data-ttu-id="cb608-109">**demo_netxduo_pop3_client.c**: демонстрационный файл для создания клиента POP3 и инициации сеанса;</span><span class="sxs-lookup"><span data-stu-id="cb608-109">**demo_netxduo_pop3_client.c** Demo file for POP3 Client creation and session initiation</span></span>
- <span data-ttu-id="cb608-110">**nx_md5.c**: исходный файл C, определяющий службы хэша MD5;</span><span class="sxs-lookup"><span data-stu-id="cb608-110">**nx_md5.c** C Source file defining MD5 digest services</span></span>
- <span data-ttu-id="cb608-111">**nx_md5.h**: файл заголовка C, определяющий службы хэша MD5;</span><span class="sxs-lookup"><span data-stu-id="cb608-111">**nx_md5.h** C Header file defining MD5 digest services</span></span>
- <span data-ttu-id="cb608-112">**nx_pop3_client.pdf**: руководство пользователя клиента POP3 для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="cb608-112">**nxd_pop3_client.pdf** NetX Duo POP3 Client User Guide</span></span>

<span data-ttu-id="cb608-113">Чтобы использовать клиент POP3 для NetX Duo, нужно целиком скопировать упомянутый ранее дистрибутив в каталог, где установлено приложение NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="cb608-113">To use NetX Duo POP3 Client, the entire distribution mentioned previously can be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="cb608-114">Например, если приложение NetX Duo установлено в каталоге *\threadx\mcf5272\green*, то именно в него следует скопировать файлы *nx_md5.h*, *nx_md5.c*, *nxd_pop3_client.h и nxd_pop3_client.c*.</span><span class="sxs-lookup"><span data-stu-id="cb608-114">For example, if NetX Duo is installed in the directory “*\threadx\mcf5272\green*” then the *nx_md5.h*, *nx_md5.c,* *nxd_pop3_client.h, and nxd_pop3_client.c* files should be copied into this directory.</span></span>

## <a name="using-netx-duo-pop3-client"></a><span data-ttu-id="cb608-115">Использование клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="cb608-115">Using NetX Duo POP3 Client</span></span>

<span data-ttu-id="cb608-116">Для использования службы клиента POP3 для NetX Duo приложение должно добавить файл *nx_pop3_client.c* в проект сборки.</span><span class="sxs-lookup"><span data-stu-id="cb608-116">To use the NetX Duo POP3 Client service, the application must add *nxd_pop3_client.c* to its build project.</span></span> <span data-ttu-id="cb608-117">Для использования ThreadX и NetX Duo в код приложения следует включить файлы *nx_md5.h и nx_pop3_client.h* после файлов *tx_api.h* и *nx_api.h*.</span><span class="sxs-lookup"><span data-stu-id="cb608-117">The application code must include *nx_md5.h, and nxd_pop3_client.h* after *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo.</span></span>

<span data-ttu-id="cb608-118">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их объектный код должен быть связан с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="cb608-118">These files must be compiled in the same manner as other application files and the object code must be linked along with the files of the application.</span></span> <span data-ttu-id="cb608-119">Это все, что необходимо для использования клиента POP3 для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="cb608-119">This is all that is required to use the NetX Duo POP3 Client.</span></span>

## <a name="small-example-of-the-netx-duo-pop3-client"></a><span data-ttu-id="cb608-120">Небольшой пример клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="cb608-120">Small Example of the NetX Duo POP3 Client</span></span>

<span data-ttu-id="cb608-121">Пример использования служб клиента POP3 для NetX Duo описан ниже на рис. 1.</span><span class="sxs-lookup"><span data-stu-id="cb608-121">An example of how to use NetX Duo POP3 Client services is described in Figure 1 that appears below.</span></span> <span data-ttu-id="cb608-122">В нем настраиваются два обратных вызова для уведомления о скачивании почты и завершении сеанса (строки 37 и 38).</span><span class="sxs-lookup"><span data-stu-id="cb608-122">This demo sets up the two callbacks for notification of mail download and session completion on lines 37 and 38.</span></span> <span data-ttu-id="cb608-123">Создается пул пакетов для клиента POP3 (строка 76).</span><span class="sxs-lookup"><span data-stu-id="cb608-123">The POP3 Client packet pool is created on line 76.</span></span> <span data-ttu-id="cb608-124">Создается задача потока IP (строка 88).</span><span class="sxs-lookup"><span data-stu-id="cb608-124">The IP thread task is created on line 88.</span></span> <span data-ttu-id="cb608-125">Обратите внимание, что этот же пул пакетов используется для пула пакетов клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-125">Note that this packet pool is also used for the POP3 Client packet pool.</span></span> <span data-ttu-id="cb608-126">Для задачи IP включается протокол TCP (строка 107).</span><span class="sxs-lookup"><span data-stu-id="cb608-126">TCP is enabled on the IP task in line 107.</span></span>

<span data-ttu-id="cb608-127">Клиент POP3 создается внутри функции входа в поток приложения *demo_thread_entry* (строка 133).</span><span class="sxs-lookup"><span data-stu-id="cb608-127">The POP3 Client is created on line 133 inside the application thread entry function, *demo_thread_entry*.</span></span> <span data-ttu-id="cb608-128">Это связано с тем, что служба *nx_pop3_client_create* также пытается установить TCP-подключение с сервером POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-128">This is because the *nx_pop3_client_create* service also attempts to make a TCP connection with the POP3 server.</span></span> <span data-ttu-id="cb608-129">В случае успеха приложение запрашивает у POP3-сервера количество элементов в его почтовом ящике с помощью службы *nx_pop3_client_mail_items_get* (строка 149).</span><span class="sxs-lookup"><span data-stu-id="cb608-129">If successful, the application queries the POP3 server for the number of items in its maildrop on line 149 using the *nx_pop3_client_mail_items_get* service.</span></span>

<span data-ttu-id="cb608-130">Если в ящике находится один или несколько элементов, приложение выполняет цикл while для каждого элемента почты, чтобы скачать почтовое сообщение.</span><span class="sxs-lookup"><span data-stu-id="cb608-130">If there are one or more items, the application iterates through the while loop for each mail item to download the mail message.</span></span> <span data-ttu-id="cb608-131">Выполняется запрос RETR в вызове службы *nx_pop3_client_mail_item_get* (строка 149).</span><span class="sxs-lookup"><span data-stu-id="cb608-131">The RETR request is made on line 149 in the *nx_pop3_client_mail_item_get* call.</span></span> <span data-ttu-id="cb608-132">В случае успешного выполнения запроса приложение скачивает пакеты с помощью службы *nx_pop3_client_mail_item_message_get* (строка 177), пока не обнаружит, что получен последний пакет в сообщении (строка 196).</span><span class="sxs-lookup"><span data-stu-id="cb608-132">If successful, the application downloads packets using the *nx_pop3_client_mail_item_message_get* service on line 177 till it detects the last packet in the message has been received on line 196.</span></span> <span data-ttu-id="cb608-133">Наконец, если скачивание прошло успешно, приложение удаляет почтовый элемент путем вызова службы *nx_pop3_client_mail_item_delete* (строка 199).</span><span class="sxs-lookup"><span data-stu-id="cb608-133">Lastly, the application deletes the mail item, assuming a successful download has occurred on line 199 in *the nx_pop3_client_mail_item_delete* call.</span></span> <span data-ttu-id="cb608-134">Стандарт RFC 1939 рекомендует, чтобы клиенты POP3 передавали серверу команды на удаление скачанных элементов почты, чтобы избежать накопления почты в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="cb608-134">The RFC 1939 recommends that POP3 Clients instruct the Server to delete downloaded mail items to prevent mail accumulating in the Client’s maildrop.</span></span> <span data-ttu-id="cb608-135">Но сервер может выполнять это автоматически.</span><span class="sxs-lookup"><span data-stu-id="cb608-135">The Server may automatically do so anyway.</span></span>

<span data-ttu-id="cb608-136">После скачивания всех почтовых элементов или в случае сбоя вызова службы POP3-клиента приложение выходит из цикла и удаляет POP3-клиент с помощью службы *nx_pop3_client_delete* (строка 217).</span><span class="sxs-lookup"><span data-stu-id="cb608-136">Once all the mail items are downloaded, or if a POP3 Client service call fails, the application exits of the loop and deletes the POP3 Client on line 217 using the *nx_pop3_client_delete* service.</span></span>

```C
/*
   demo_netxduo_pop3.c

   This is a small demo of POP3 Client on the NetX Duo TCP/IP stack.
   This demo relies on Thread, NetX Duo and POP3 Client API to conduct
   a POP3 mail session.
 */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_pop3_client.h"

#define DEMO_STACK_SIZE             4096
#define CLIENT_ADDRESS              IP_ADDRESS(192,2,2,61)
#define SERVER_ADDRESS              IP_ADDRESS(192,2,2,89)
#define SERVER_PORT                 110

/* Replace the 'ram' driver with your own Ethernet driver. */
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Set up the POP3 Client.  */

TX_THREAD           demo_client_thread;
NX_POP3_CLIENT      demo_client;
NX_PACKET_POOL      client_packet_pool;
NX_IP               client_ip;

#define PAYLOAD_SIZE 500

/* Set up Client thread entry point. */
void    demo_thread_entry(ULONG info);


  /* Shared secret is the same as password. */

#define LOCALHOST                               "recipient@domain.com"
#define LOCALHOST_PASSWORD                      "testpwd"

/* Define main entry point.  */
int main()
{
    /* Enter the ThreadX kernel.  */
    tx_kernel_enter();
}

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    UINT     status;
    UCHAR    *free_memory_pointer;


    /* Setup the working pointer.  */
    free_memory_pointer =  first_unused_memory;

    /* Create a client thread.  */
    tx_thread_create(&demo_client_thread, "Client", demo_thread_entry, 0,
                     free_memory_pointer, DEMO_STACK_SIZE, 1, 1,
                     TX_NO_TIME_SLICE, TX_AUTO_START);

    free_memory_pointer =  free_memory_pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* The demo client username and password is the authentication
       data used when the server attempts to authentication the client. */

    /* Create Client packet pool. */
    status =  nx_packet_pool_create(&client_packet_pool,"POP3 Client Packet Pool",
                                    PAYLOAD_SIZE, free_memory_pointer,
                                    (PAYLOAD_SIZE * 10));
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
    free_memory_pointer =  free_memory_pointer + 2048;

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

void    demo_thread_entry(ULONG info)
{

    UINT        status;
    UINT        mail_item, number_mail_items;
    UINT        bytes_downloaded = 0;
    UINT        final_packet = NX_FALSE;
    ULONG       total_size, mail_item_size, bytes_retrieved;
    NX_PACKET   *packet_ptr;

    /* Let the IP instance get initialized with driver parameters. */
    tx_thread_sleep(40);


    /* Create a NetX POP3 Client instance with no byte or block memory pools.
       Note that it uses its password for its APOP shared secret. */
    status =  nx_pop3_client_create(&demo_client,
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

    /* Find out how many items are in our mailbox.  */
    status = nx_pop3_client_mail_items_get(&demo_client, &number_mail_items,
                                            &total_size);

    printf("Got %d mail items, total size%d \n", number_mail_items, total_size);

    /* If nothing in the mailbox, disconnect. */
    if (number_mail_items == 0)
    {

        nx_pop3_client_delete(&demo_client);

        return;
    }

    /* Download all mail items.  */
    mail_item = 1;

    while (mail_item <= number_mail_items)
    {


        /* This submits a RETR request and gets the mail message size. */
        status = nx_pop3_client_mail_item_get(&demo_client, mail_item,
                                               &mail_item_size);

        /* Loop to get all mail message packets until the mail item is completely
           downloaded. */
        while((final_packet ==  NX_FALSE) && (status == NX_SUCCESS))
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

    /* Delete the POP3 Client.  This will not delete the Client packet pool. */
    status = nx_pop3_client_delete(&demo_client);

}
```

<span data-ttu-id="cb608-137">**Рис. 1.Пример приложения клиента POP3 для NetX Duo**</span><span class="sxs-lookup"><span data-stu-id="cb608-137">**Figure 1. Example of a NetX Duo POP3 Client application**</span></span>

## <a name="pop3-client-configuration-options"></a><span data-ttu-id="cb608-138">Параметры конфигурации POP3-клиента</span><span class="sxs-lookup"><span data-stu-id="cb608-138">POP3 Client Configuration Options</span></span>

<span data-ttu-id="cb608-139">Существует несколько параметров конфигурации клиента POP3 для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="cb608-139">There are several configuration options with the NetX Duo POP3 Client.</span></span> <span data-ttu-id="cb608-140">Ниже приведен список всех параметров с подробным описанием.</span><span class="sxs-lookup"><span data-stu-id="cb608-140">Following is a list of all options described in detail:</span></span>

- <span data-ttu-id="cb608-141">**NX_POP3_CLIENT_PACKET_TIMEOUT**: параметр ожидания в секундах для выделения пакета клиентом POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-141">**NX_POP3_CLIENT_PACKET_TIMEOUT** This defines the wait option in seconds for the POP3 Client to allocate a packet.</span></span> <span data-ttu-id="cb608-142">Значение по умолчанию — 1 секунда.</span><span class="sxs-lookup"><span data-stu-id="cb608-142">The default value is 1 second.</span></span>
- <span data-ttu-id="cb608-143">**NX_POP3_CLIENT_CONNECTION_TIMEOUT**: параметр ожидания в секундах для подключения клиента POP3 к серверу POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-143">**NX_POP3_CLIENT_CONNECTION_TIMEOUT** This defines the wait option in seconds for the POP3 Client to connect with the POP3 Server.</span></span> <span data-ttu-id="cb608-144">Значение по умолчанию - 30 секунды.</span><span class="sxs-lookup"><span data-stu-id="cb608-144">The default value is 30 seconds.</span></span>
- <span data-ttu-id="cb608-145">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT**: параметр ожидания в секундах для отключения клиента POP3 от сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-145">**NX_POP3_CLIENT_DISCONNECT_TIMEOUT** This defines the wait option in seconds for the POP3 Client to disconnect from the POP3 Server.</span></span> <span data-ttu-id="cb608-146">Значение по умолчанию — 2 секунды.</span><span class="sxs-lookup"><span data-stu-id="cb608-146">The default value is 2 seconds.</span></span>
- <span data-ttu-id="cb608-147">**NX_POP3_TCP_SOCKET_SEND_WAIT**: параметр ожидания в секундах в вызовах службы *nx_tcp_socket_send*.</span><span class="sxs-lookup"><span data-stu-id="cb608-147">**NX_POP3_TCP_SOCKET_SEND_WAIT** This option sets the wait option in seconds in *nx_tcp_socket_send* service calls.</span></span> <span data-ttu-id="cb608-148">Значение по умолчанию — 2 секунды.</span><span class="sxs-lookup"><span data-stu-id="cb608-148">The default value is 2 seconds.</span></span>
- <span data-ttu-id="cb608-149">**NX_POP3_SERVER_REPLY_TIMEOUT**: параметр ожидания в вызовах службы *nx_tcp_socket_receive* для ответа сервера на запрос клиента.</span><span class="sxs-lookup"><span data-stu-id="cb608-149">**NX_POP3_SERVER_REPLY_TIMEOUT** This option sets the wait option in *nx_tcp_socket_receive* service calls for the Server reply to a Client request.</span></span> <span data-ttu-id="cb608-150">Значение по умолчанию — 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="cb608-150">The default value is 10 seconds.</span></span>
- <span data-ttu-id="cb608-151">**NX_POP3_CLIENT_TCP_WINDOW_SIZE**: задает допустимый размер получаемого TCP-пакета в клиенте.</span><span class="sxs-lookup"><span data-stu-id="cb608-151">**NX_POP3_CLIENT_TCP_WINDOW_SIZE** This option sets the size of the Client TCP receive window.</span></span> <span data-ttu-id="cb608-152">В качестве значения этого параметра следует задать размер MTU экземпляра IP за вычетом размеров заголовков IP и TCP.</span><span class="sxs-lookup"><span data-stu-id="cb608-152">This should be set to the IP instance MTU size minus the IP and TCP header.</span></span> <span data-ttu-id="cb608-153">Значение по умолчанию — 1460.</span><span class="sxs-lookup"><span data-stu-id="cb608-153">The default value is 1460.</span></span> <span data-ttu-id="cb608-154">Это значение следует уменьшить до 1440 байт, если приложение передает пакеты POP3 через сеть IPv6, поскольку заголовок IPv6 имеет больший размер.</span><span class="sxs-lookup"><span data-stu-id="cb608-154">This should be less if the application is sending POP3 packets over IPv6 (1440 bytes) to account for the larger IPv6 header.</span></span>
- <span data-ttu-id="cb608-155">**NX_POP3_MAX_USERNAME**: задает размер буфера для имени пользователя в клиенте POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-155">**NX_POP3_MAX_USERNAME** This option sets the size of the buffer of the POP3 Client user name.</span></span> <span data-ttu-id="cb608-156">Значение по умолчанию — 40 байт.</span><span class="sxs-lookup"><span data-stu-id="cb608-156">The default value is 40 bytes.</span></span>
- <span data-ttu-id="cb608-157">**NX_POP3_MAX_PASSWORD**: задает размер буфера для пароля в клиенте POP3.</span><span class="sxs-lookup"><span data-stu-id="cb608-157">**NX_POP3_MAX_PASSWORD** This option sets the size of the buffer of the POP3 Client password.</span></span> <span data-ttu-id="cb608-158">Значение по умолчанию — 20 байт.</span><span class="sxs-lookup"><span data-stu-id="cb608-158">The default value is 20 bytes.</span></span>
