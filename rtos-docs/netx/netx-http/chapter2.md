---
title: Глава 2. Установка и использование NetX HTTP
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX HTTP.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db621e38e9d2324ca3ce2398aee9f729b05886ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815196"
---
# <a name="chapter-2---installation-and-use-of-netx-http"></a>Глава 2. Установка и использование NetX HTTP

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX HTTP.

## <a name="product-distribution"></a>Распространение продукта

NetX для ОСРВ Azure можно получить из нашего репозитория общедоступного исходного кода по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).

- **nx_http_client.h** — файл заголовка HTTP-клиента для NetX.
- **nx_http_server.h** — файл заголовка HTTP-сервера для NetX.
- **nx_http_client.c** — исходный файл на C HTTP-клиента для NetX.
- **nx_http_server.c** — исходный файл на C HTTP-сервера для NetX.
- **nx_md5.c** — алгоритмы хэширования MD5.
- **filex_stub.h** — файл заглушки при отсутствии FileX.
- **nx_http.pdf** — описание HTTP для NetX.
- **demo_netx_http.c** — демонстрация NetX HTTP.

## <a name="http-installation"></a>Установка HTTP

Чтобы использовать HTTP для NetX, весь дистрибутив, упомянутый ранее, должен быть скопирован в тот же каталог, где установлен NetX. Например, если NetX установлен в каталог *\threadx\arm7\green*, файлы *nx_http_client.h* и *nx_http_client.c* будут использоваться для приложений HTTP-клиента NetX, а *nx_http_server.h* и *nx_http_server.c* — для приложений сервера NetX HTTP. *nx_md5.c* нужно скопировать в этот каталог. Для запуска демонстрационного приложения ram driver файлы клиента и сервера NetX HTTP нужно скопировать в один каталог.

## <a name="using-http"></a>Использование HTTP

Использовать HTTP для NetX очень просто. Код приложения должен только включать *nx_http_client.h* и (или) *nx_http_server.h* после включения *tx_api.h, fx_api.h* и *nx_api.h* для использования ThreadX, FileX и NetX соответственно. После добавления файлов HTTP-заголовков код приложения сможет выполнять вызовы функций HTTP, указанные далее в этом руководстве. Приложение также должно включать *nx_http_client.c*, *nx_http_server.c* и *md5.c* в ходе сборки. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX HTTP.

>[!NOTE] 
> Если NX_HTTP_DIGEST_ENABLE не указывается в ходе сборки, файл *md5.c* не нужно добавлять в приложение. Аналогично, если возможности HTTP-клиента не требуются, файл *nx_http_client.c* можно опустить.

>[!NOTE] 
> Так как HTTP использует TCP-службы NetX, TCP нужно включить с помощью вызова *nx_tcp_enable* до использования HTTP.

## <a name="small-example-system"></a>Пример небольшой системы

Пример того, насколько просто использовать NetX HTTP, приведен на рис. 1.1 ниже. В этом примере файлы HTTP *nx_http_client.h и nx_http_server.h* включаются с помощью include в строке 8. Затем создается HTTP-сервер с помощью *tx_application_define* в строке 131.

>[!NOTE] 
> Блок управления HTTP-сервером *Server* задается в качестве глобальной переменной в строке 25 ранее.

После успешного создания HTTP-сервер запускается в строке 136. Затем в строке 149 создается HTTP-клиент. И наконец, клиент записывает файл в строке 157 и считывает файл обратно в строке 195.

```c
/* This is a small demo of HTTP on the high-performance NetX TCP/IP stack.
This demo relies on ThreadX, NetX, and FileX to show a simple HTML
transfer from the client and then back from the server. */

#include "tx_api.h"
#include "fx_api.h"
#include "nx_api.h"
#include "nx_http_client.h"
#include "nx_http_server.h"
#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_0;
TX_THREAD         thread_1;
NX_PACKET_POOL    pool_0;
NX_PACKET_POOL    pool_1;
NX_IP             ip_0;
NX_IP             ip_1;
FX_MEDIA          ram_disk;

/* Define HTTP objects. */

NX_HTTP_SERVER    my_server;
NX_HTTP_CLIENT    my_client;

/* Define the counters used in the demo application... */

ULONG             error_counter;

/* Define the RAM disk memory. */

UCHAR             ram_disk_memory[32000];

/* Define function prototypes. */

void     thread_0_entry(ULONG thread_input);
VOID     _fx_ram_driver(FX_MEDIA *media_ptr) ;
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT     authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, CHAR **name, CHAR **password, 
                              CHAR **realm);

/* Define the application's authentication check. This is called by
the HTTP server whenever a new request is received. */
UINT authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, CHAR **name, CHAR **password, 
                         CHAR **realm);
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */
    *name = "name";
    *password = "password";
    *realm = "NetX HTTP demo";

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create packet pool. */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
                         600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create an IP instance. */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
                0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
                         pointer = pointer + 8192;

    /* Create another IP instance. */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
                0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
                pointer, 4096, 1);
                pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1. */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
                 pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances. */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk. */
                 _fx_ram_driver, ram_disk_memory, pointer, 4096) ;
                 pointer += 4096;

    /* Create the NetX HTTP Server. */
    nx_http_server_create(&my_server, "My HTTP Server", &ip_1, &ram_disk,
                         pointer, 4096, &pool_1, authentication_check, NX_NULL);
                         pointer = pointer + 4096;

    /* Start the HTTP Server. */
    nx_http_server_start(&my_server);
}

/* Define the test thread. */
void     thread_0_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Create an HTTP client instance. */
    status = nx_http_client_create(&my_client, "My Client", &ip_0,
                                  &pool_0, 600);

    /* Check status. */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server. */
    status = nx_http_client_put_start(&my_client, IP_ADDRESS(1,2,3,5),
                                      "/test.htm", "name", "password", 103, 50);
    /* Check status. */
    if (status)
        error_counter++;

    /* Allocate a packet. */
    status = nx_packet_allocate(&pool_0, &my_packet, NX_TCP_PACKET,
                               NX_WAIT_FOREVER);
    /* Check status. */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page. */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
                         "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
                         &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length. */
    status = **nx_http_client_put_packet**(&my_client, my_packet, 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Now GET the file back! */
    status = nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
                                     "/test.htm", NX_NULL, 0, "name", 
                                     "password", 50);

    /* Check status. */
    if (status)
        error_counter++;

    /* Get a packet. */
    status = nx_http_client_get_packet(&my_client, &my_packet, 20);

    /* Check for an error. */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet. */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it! */
        nx_packet_release(my_packet);
    }

    /* Flush the media. */
     fx_media_flush(&ram_disk);
 }
```

Рис. 1.1. Пример использования HTTP с NetX

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для использования HTTP с NetX. Ниже приведен список всех параметров, каждый из которых подробно описан ниже. Приведены значения по умолчанию, но их можно переопределить перед включением файлов *nx_http_client.h и nx_http_server.h*.

- **NX_DISABLE_ERROR_CHECKING** — если определен, этот параметр удаляет базовую проверку ошибок HTTP. Обычно он используется после отладки приложения.
- **NX_HTTP_SERVER_PRIORITY** — приоритет потока HTTP-сервера. По умолчанию указано значение 16 для задания приоритета 16.
- **NX_HTTP_NO_FILEX** — если определен, этот параметр предоставляет заглушку для зависимостей FileX. HTTP-клиент будет работать без каких-либо изменений, если этот параметр определен. Для надлежащей работы HTTP-сервер нужно будет изменить, либо пользователю потребуется создать несколько служб FileX.
- **NX_HTTP_TYPE_OF_SERVICE** — тип службы, необходимой для TCP-запросов HTTP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.
- **NX_HTTP_SERVER_THREAD_TIME_SLICE** — число тактов таймера, которое может выполнить поток сервера, прежде чем уступить ресурсы потокам с таким же приоритетом. Значение по умолчанию — 2.
- **NX_HTTP_FRAGMENT_OPTION** — поддержка фрагментов для TCP-запросов HTTP. По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование TCP в HTTP.
- **NX_HTTP_SERVER_WINDOW_SIZE** — размер окна сокета для сервера. Значение по умолчанию: 2048 байт.
- **NX_HTTP_TIME_TO_LIVE** — указывает число маршрутов, которое может пройти этот пакет перед отменой. Значение по умолчанию: 0x80.
- **NX_HTTP_SERVER_TIMEOUT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу. Значение по умолчанию: 10 секунд (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_ACCEPT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_server_socket_accept*. Значение по умолчанию: (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_disconnect*. Значение по умолчанию: 10 секунд (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_RECEIVE** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_receive*. Значение по умолчанию: 10 секунд (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_SERVER_TIMEOUT_SEND** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_send*. Значение по умолчанию: 10 секунд (10 * NX_IP_PERIODIC_RATE).
- **NX_HTTP_MAX_HEADER_FIELD** — указывает максимальный размер поля HTTP-заголовка. Значение по умолчанию — 256.
- **NX_HTTP_MULTIPART_ENABLE** — если определен, позволяет HTTP-серверу поддерживать составные HTTP-запросы.
- **NX_HTTP_SERVER_MAX_PENDING** — указывает число подключений, которые можно поставить в очередь к HTTP-серверу. Значение по умолчанию: 5.
- **NX_HTTP_MAX_RESOURCE** — указывает число байтов, разрешенных в предоставляемом клиентом *имени ресурса*. Значение по умолчанию: 40.
- **NX_HTTP_MAX_NAME** — указывает число байтов, разрешенных в предоставляемом клиентом *имени пользователя*. Значение по умолчанию: 20.
- **NX_HTTP_MAX_PASSWORD** — указывает число байтов, разрешенных в предоставляемом клиентом *пароле*. Значение по умолчанию: 20.
- **NX_HTTP_SERVER_MIN_PACKET_SIZE** — указывает минимальный размер пакетов в пуле, заданном при создании сервера. Минимальный размер нужно указать, чтобы обеспечить включение полного HTTP-заголовка в один пакет. Значение по умолчанию: 600.
- **NX_HTTP_CLIENT_MIN_PACKET_SIZE** — указывает минимальный размер пакетов в пуле, заданном при создании клиента. Минимальный размер нужно указать, чтобы обеспечить включение полного HTTP-заголовка в один пакет. Значение по умолчанию: 300.
- **NX_HTTP_SERVER_RETRY_SECONDS** — *задает время ожидания повторной передачи на сокет сервера в секундах.* Значение по умолчанию: 2.
- **NX_HTTP_SERVER_RETRY_MAX** — задает максимальное число повторных передач на сокете сервера. Значение по умолчанию: 10.
- **NX_HTTP_SERVER_ RETRY_SHIFT** — это значение используется для указания времени ожидания следующей повторной передачи. Текущее время ожидания умножается на число повторных передач на текущий момент с добавлением значения для смещения времени ожидания сокета. Значение по умолчанию: 1 (для удвоения времени ожидания).
- **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** — указывает максимальное число пакетов, которое можно поставить в очередь для повторной передачи на сокет сервера. Если число пакетов в очереди достигает этого значения, пакеты не будут отправляться, пока один пакет в очереди или более не будут освобождены. Значение по умолчанию: 20.