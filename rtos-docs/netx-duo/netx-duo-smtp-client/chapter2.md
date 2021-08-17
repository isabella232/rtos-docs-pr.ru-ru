---
title: Глава 2. Установка и использование клиента SMTP для NetX Duo
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиента SMTP для NetX Duo.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ba4d50048adba4ac992f6bbe90d236445546a5929ace74899833c686a90dadd9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797846"
---
# <a name="chapter-2---installation-and-use-of-netx-duo-smtp-client"></a>Глава 2. Установка и использование клиента SMTP для NetX Duo

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиента SMTP для NetX Duo.

## <a name="netx-duo-smtp-client-installation"></a>Установка клиента SMTP для NetX Duo

Клиент SMTP для NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). В состав пакета входят следующие файлы.

- **nxd_smtp_client.c** — файл исходного кода C API клиента SMTP для NetX Duo.
- **nxd_smtp_client.h** — файл заголовка C API клиента SMTP для NetX Duo.
- **demo_netxduo_smtp_client.c** — демонстрация клиента SMTP для NetX Duo.
- **nxd_smtp_client.pdf** — руководство пользователя по API клиента SMTP для NetX Duo.

Для использования API клиента SMTP для NetX Duo необходимо скопировать все упомянутые выше файлы дистрибутива в каталог установки NetX Duo. Например, если NetX Duo установлен в каталог "c: *\myproject*", то файлы *nxd_smtp_client.h и nxd_smtp_client.c* необходимо скопировать в этот же каталог.

## <a name="using-netx-duo-smtp-client"></a>Использование клиента SMTP для NetX Duo

Чтобы создать клиентское приложение SMTP для NetX Duo, сначала необходимо создать библиотеки ThreadX и NetX Duo и включить их в проект сборки. Затем необходимо включить *tx_api.h* и *nx_api.h в исходный код приложения*. Это позволит использовать службы ThreadX и NetX Duo. Для использования служб клиента SMTP необходимо после *tx_api.h* и *nx_api.h* также включить файлы *nxd_smtp_client.c* и *nxd_smtp_client.h*.

Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их объектный код должен быть связан с файлами приложения. Это все, что необходимо для создания клиентского приложения SMTP для NetX Duo.

## <a name="small-example-system"></a>Небольшой пример системы

Пример использования клиента SMTP для NetX Duo приведен на рисунке 1 ниже. Пул пакетов для экземпляра IP создается с помощью службы nx_packet_pool_create в строке 68 и имеет очень небольшую полезную нагрузку пакета. Это происходит потому, что экземпляр IP отправляет только управляющие пакеты, которые не нуждаются в большой нагрузке. Пул пакетов клиента SMTP создается в строке 84 и используется для передачи сообщений клиента SMTP на сервер и данных сообщений. Его полезная нагрузка пакетов гораздо больше. Экземпляр IP создается в строке 118 с помощью того же пула пакетов. Протокол TCP, необходимый для протокола SMTP, включается в экземпляре IP в строке 130.

В потоке приложения клиент SMTP создается с помощью службы *nxd_smtp_client_create* в строке 170. Служба *nxd_smtp_client_create* поддерживает подключения SMTP-сервера по протоколам IPv4 и IPv6, хотя в данном примере используется только IPv4. Затем в строке 184 почтовое сообщение отправляется клиенту SMTP для передачи с помощью службы *nx_smtp_mail_send*. Обратите внимание, что строка темы с заголовком содержимого почты создается отдельно от текста сообщения. Также обратите внимание, что запрос на отправку почты принимает только один почтовый адрес получателя, который считается синтаксически правильным.

Затем приложение завершает работу клиента SMTP в строке 200. Служба *nx_smtp_client_delete* проверяет, что подключение к сокету закрыто и порт не привязан. Обратите внимание, что клиентское приложение SMTP удаляет пул пакетов, если он больше не используется.

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

**Рисунок 1. Пример использования клиента SMTP с NetX Duo**

## <a name="client-configuration-options"></a>Параметры конфигурации клиента

В API клиента SMTP для NetX Duo есть несколько параметров для настройки. Ниже приведен список всех параметров с подробным описанием.

- **NX_SMTP_CLIENT_TCP_WINDOW_SIZE** —этот параметр задает размер окна приема TCP клиента. Этот параметр должен иметь значение меньше размера MTU базового оборудования Ethernet и оставлять место для заголовков IP и TCP. По умолчанию размер окна TCP у клиента SMTP для NetX Duo равен 1460.
- **NX_SMTP_CLIENT_PACKET_TIMEOUT** —этот параметр задает время ожидания при выделении пакетов NetX. Время ожидания пакета клиента SMTP для NetX Duo по умолчанию равно 2 секунды.
- **NX_SMTP_CLIENT_CONNECTION_TIMEOUT** —этот параметр задает время ожидания подключения TCP-сокета клиента. Время ожидания подключения клиента SMTP для NetX Duo по умолчанию равно 10 секундам.
- **NX_SMTP_CLIENT_DISCONNECT_TIMEOUT** —этот параметр задает время ожидания отключения TCP-сокета клиента. Время ожидания отключения клиента SMTP для NetX Duo по умолчанию равно 5 секундам*. Обратите внимание, что если клиент SMTP обнаруживает внутреннюю ошибку, такую как нарушение соединения, он может разорвать подключение с нулевым временем ожидания.
- **NX_SMTP_GREETING_TIMEOUT** —этот параметр задает время ожидания, в течение которого клиент получает ответ сервера на приветствие. Значение по умолчанию для клиента SMTP для NetX Duo равно 10 секундам.
- **NX_SMTP_ENVELOPE_TIMEOUT** —этот параметр задает время ожидания, в течение которого клиент получает ответ сервера на команду клиента. Значение по умолчанию для клиента SMTP для NetX Duo равно 10 секундам.
- **NX_SMTP_MESSAGE_TIMEOUT** — этот параметр задает время ожидания, в течение которого клиент получает ответ сервера на получение данных почтового сообщения. Значение по умолчанию для клиента SMTP для NetX Duo равно 30 секундам.
- **NX_SMTP_CLIENT_SEND_TIMEOUT** — этот параметр определяет параметр ожидания буфера для сохранения пароля пользователя во время проверки подлинности SMTP на сервере. Значение по умолчанию — 20 байт.
- **NX_SMTP_SERVER_CHALLENGE_MAX_STRING** — этот параметр определяет размер буфера для извлечения запроса сервера во время проверки подлинности SMTP. Значение по умолчанию — 200 байт. Для проверки подлинности LOGIN и PLAIN клиент SMTP, вероятно, может использовать буфер меньшего размера.
- **NX_SMTP_CLIENT_MAX_PASSWORD** — этот параметр определяет размер буфера для хранения пароля пользователя во время проверки подлинности SMTP на сервере. Значение по умолчанию — 20 байт. 
- **NX_SMTP_CLIENT_MAX_USERNAME** — этот параметр определяет размер буфера для хранения имени узла пользователя во время проверки подлинности SMTP на сервере. Значение по умолчанию — 40 байт. 
