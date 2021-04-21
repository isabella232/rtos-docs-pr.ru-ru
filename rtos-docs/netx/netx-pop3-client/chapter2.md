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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pop3-client"></a>Глава 2. Установка и использование POP3-клиента NetX для ОСРВ Azure

POP3-клиент NetX содержит один исходный файл, один файл заголовка и демонстрационный файл. Для служб дайджеста MD5 доступно два дополнительных файла. Также есть PDF-файл с руководством пользователя (этот документ).

- **nx_pop3_client.c**: исходный файл C для API POP3-клиента NetX
- **nx_pop3_client.h**: файл заголовка C для API POP3-клиента NetX
- **demo_netxduo_pop3_client.c**: демонстрационный файл для создания POP3-клиента и инициации сеанса
- **nx_md5.c**: исходный файл C, определяющий службы дайджеста MD5
- **nx_md5.h**: файл заголовка C, определяющий службы дайджеста MD5
- **nx_pop3_client.pdf**: руководство пользователя POP3-клиента NetX

Чтобы использовать POP3-клиент для NetX, весь дистрибутив, упомянутый ранее, должен быть скопирован в тот же каталог, где установлен NetX. Например, если NetX установлен в каталоге *\threadx\mcf5272\green*, то файлы *nx_md5.h*, *nx_md5.c*, *nx_pop3_client.h и nx_pop3_client.c* должны быть скопированы в этот же каталог.

## <a name="using-netx-pop3-client"></a>Использование POP3-клиента NetX

Для использования службы POP3-клиента NetX приложение должно добавить файл *nx_pop3_client.c* в свой проект сборки. Для использования ThreadX и NetX в код приложения следует включить файлы *nx_md5.h, nx_pop3.h и nx_pop3_client.h* после файлов *tx_api.h* и *nx_api.h*.

Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их объектный код должен быть связан с файлами приложения. Это все, что необходимо для использования POP3-клиента NetX.

## <a name="small-example-of-the-netx-pop3-client"></a>Небольшой пример POP3-клиента NetX

Пример использования служб POP3-клиента NetX приведен на рис. 1 ниже. В нем настраиваются два обратных вызова для уведомления о скачивании почты и завершении сеанса в строках 37 и 38. Пул пакетов POP3-клиента создается в строке 76. Задача потока IP создается в строке 88. Обратите внимание, что этот пул пакетов также используется для пула пакетов POP3-клиента. Протокол TCP включен для задачи IP в строке 107.

POP3-клиент создается в строке 133 внутри функции входа в поток приложения *demo_thread_entry*. Это связано с тем, что служба *nx_pop3_client_create* также пытается установить TCP-подключение к POP3-серверу. В случае успеха приложение запрашивает у POP3-сервера количество элементов в его почтовом ящике в строке 149 с помощью службы *nx_pop3_client_mail_items_get*.

Если в ящике находится один элемент или несколько элементов, приложение выполняет итерацию цикла while для каждого почтового элемента, чтобы скачать почтовое сообщение. Запрос на RETR выполняется в строке 149 в вызове службы *nx_pop3_client_mail_item_get*. В случае успешного выполнения запроса приложение скачивает пакеты с помощью службы *nx_pop3_client_mail_item_message_get* в строке 177, пока не обнаружит, что получен последний пакет в сообщении в строке 196. Наконец, приложение удаляет почтовый элемент, предполагая успешное завершение скачивания в строке 199 в вызове службы *nx_pop3_client_mail_item_delete*. В соответствии со стандартом RFC 1939 рекомендуется, чтобы POP3-клиенты указывали серверу удалять скачанные почтовые элементы, чтобы избежать накопления почты в почтовом ящике клиента. В любом случае сервер может сделать это автоматически.

После скачивания всех почтовых элементов или в случае сбоя вызова службы POP3-клиента приложение выходит из цикла и удаляет POP3-клиент в строке 217 с помощью службы *nx_pop3_client_delete*.

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

Рис. 1. Пример приложения POP3-клиента NetX

## <a name="pop3-client-configuration-options"></a>Параметры конфигурации POP3-клиента

Существует несколько параметров конфигурации POP3-клиента NetX. Ниже приведен список всех параметров с подробным описанием.

- **NX_POP3_CLIENT_PACKET_TIMEOUT**: параметр ожидания в секундах для выделения пакета POP3-клиентом. Значение по умолчанию — 1 секунда.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: параметр ожидания в секундах для подключения POP3-клиента к POP3-серверу. Значение по умолчанию - 30 секунды.

- **NX_POP3_CLIENT_CONNECTION_TIMEOUT**: параметр ожидания в секундах для отключения POP3-клиента от POP3-сервера. Значение по умолчанию — 2 секунды.

- **NX_POP3_TCP_SOCKET_SEND_WAIT**: параметр ожидания в секундах в вызовах службы *nx_tcp_socket_send*. Значение по умолчанию — 2 секунды.

- **NX_POP3_SERVER_REPLY_TIMEOUT**: параметр ожидания в вызовах службы *nx_tcp_socket_receive* для ответа сервера на запрос клиента. Значение по умолчанию — 10 секунд.

- **NX_POP3_CLIENT_TCP_WINDOW_SIZE**: задает размер окна получения TCP-клиента. В качестве значения параметра следует задать размер MTU экземпляра IP минус размер IP и размер заголовка TCP. Значение по умолчанию — 1460.

- **NX_POP3_MAX_USERNAME**: задает размер буфера имени пользователя POP3-клиента. Значение по умолчанию — 40 байт.

- **NX_POP3_MAX_USERNAME**: задает размер буфера пароля POP3-клиента. Значение по умолчанию — 20 байт.