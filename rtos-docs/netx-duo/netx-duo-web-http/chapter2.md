---
title: Глава 2. Установка и использование протоколов HTTP для HTTPS
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Web HTTP.
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814523"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a>Глава 2. Установка и использование протоколов HTTP для HTTPS

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Web HTTP.

## <a name="product-distribution"></a>Распространение продукта

Пакет HTTP для NetX доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). Этот пакет содержит три файла исходного кода, два включаемых файла и PDF-файл, содержащий этот документ:

- **nx_web_http_common.h**: общий файл заголовка для NetX Web HTTP;
- **nx_web_http_client.h**: файл заголовка HTTP-клиента для NetX Web;
- **nx_web_http_server.h**: файл заголовка HTTP-сервера для NetX Web;
- **nx_web_http_client.c**: файл сходного кода C HTTP-клиента для NetX Web;
- **nx_web_http_server.c**: файл исходного кода C HTTP-сервера для NetX Web;
- **nx_tcpserver.c**: файл исходного кода C для нескольких сокетов TCP;
- **nx_tcpserver.h**: файл заголовка для определения символов HTTPS-сервера;
- **nx_md5.c**: дайджест-алгоритмы MD5;
- **filex_stub.h**: файл заглушки при отсутствии FileX;
- **nx_web_http.pdf**: описание протокола HTTP для NetX Web;
- **demo_netx_web_http.c**: демонстрационный файл для NetX Web HTTP.

## <a name="http-installation"></a>Установка протокола HTTP

Чтобы использовать NetX Web HTTP, весь дистрибутив, упомянутый ранее, необходимо скопировать в каталог, где установлен экземпляр NetX Duo. Например, если экземпляр NetX Duo установлен в каталог *\threadx\arm7\green*, то в него нужно скопировать файлы *nx_web_http_client.h*, *nx_web_http_client.c (для клиентских приложений NetX Web HTTP) и nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c и nx_tcpserver.h (для серверных приложений NetX Web HTTP). Для клиентских и серверных приложений файл nx_web_http_common.h также должен находиться в этом каталоге. Кроме того, в этот каталог нужно скопировать файл nx_md5.c*, если используется дайджест-проверка подлинности. Для запуска демонстрационного приложения драйвера ОЗУ файлы HTTP-клиента и HTTP-сервера нужно скопировать в один каталог.

При использовании протокола TLS необходим отдельный каталог NetX Secure, содержащий файлы исходного кода TLS.

## <a name="using-http"></a>Использование HTTP

Использовать NetX Web HTTP просто. Как правило, код приложения должен включать в себя файлы *nx_web_http_client.h* и (или) *nx_web_http_server.h* после добавления файлов *tx_api.h, fx_api.h* и *nx_api.h* (файл *nx_web_http_common.h* включается автоматически). Эти файлы заголовка позволяют приложению использовать ThreadX, FileX и NetX Duo соответственно. Для поддержки протокола HTTPS файлы заголовка должны быть добавлены после включения файла *nx_secure_tls.h*, чтобы обеспечить поддержку протокола TLS.

После добавления файлов заголовка HTTP код приложения сможет выполнять вызовы функций HTTP, описанных далее в этом руководстве. В процессе сборки приложение также нужно связать с файлами *nx_web_http_client.c* (для HTTP(s)-клиентов), *nx_web_http_server.c и nx_tcpserver.c* (для HTTP(s)-серверов) и *nx_md5.c* (для дайджест-проверки подлинности). Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX Web HTTP.

> [!NOTE]
> Если NX_WEB_HTTP_DIGEST_ENABLE не указывается в процессе сборки, файл *md5.c* не нужно добавлять в приложение. Аналогично, если не требуются возможности HTTP-клиента, файл *nx_web_http_client.c* может быть опущен. Если не требуются возможности HTTP-сервера, то можно опустить файл *nx_web_http_server.c*.
>
> Если не определен параметр NX_WEB_HTTPS_ENABLE для включения протокола HTTPS (вместо использования только HTTP без шифрования), то наличие NetX Secure TLS в сборке не обязательно.
>
> Так как протокол HTTP использует службы NetX TCP, то перед его использованием нужно включить протокол TCP с помощью вызова *nx_tcp_enable*.
>
> При использовании протокола HTTPS с NetX Secure TLS необходимо инициализировать TLS с помощью *nx_secure_tls_initialize()* перед вызовом подпрограмм HTTPS.

## <a name="small-example-system"></a>Пример небольшой системы

Пример использования NetX Web HTTP описан на рисунке 1.1 ниже.

> [!CAUTION]
> Он предоставлен только в демонстрационных целях, и не гарантируется, что его можно будет скомпилировать и запустить "как есть".
>
> Демонстрационные файлы исходного кода, сборка которых будет правильно выполнена в среде Logic Express, доступны в дистрибутиве выпуска NetX Duo HTTPS.  Также имейте в виду, что эти демонстрационные файлы намеренно созданы очень простыми, так как они предназначены для создания приложений HTTPS и (или) NetX Duo HTTPS новыми пользователями.

В этом примере указаны включаемые файлы HTTP *nx_web_http_client.h и nx_web_http_server.h* (*netx_web_http_common.h* включается автоматически). Затем создается HTTP-сервер с помощью *tx_application_define*. Обратите внимание на то, что блок управления HTTP-сервером *Server* был задан в качестве глобальной переменной ранее. После успешного создания HTTPS-сервер запускается. Затем создается HTTPS-клиент. Он записывает файл и считывает его файл.

> [!NOTE]
> В этой системе определен параметр NX_WEB_HTTPS_ENABLE.

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
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

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

**Рисунок 1.1. Пример использования протокола HTTPS с NetX и NetX Secure TLS**

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для сборки HTTP для NetX. Ниже приведен список всех параметров с подробным описанием каждого из них. Приведены значения по умолчанию, но их можно переопределить перед включением файлов *nx_web_http_server.h и nx_http_server.h*.

- **NX_DISABLE_ERROR_CHECKING**: если этот параметр определен, он удаляет базовую проверку на ошибки HTTP. Обычно он используется после отладки приложения.
- **NX_WEB_HTTP_DIGEST_ENABLE**: если этот параметр определен, на HTTPS-сервере включается дайджест-проверка подлинности MD5. По умолчанию он не определен.
- **NX_WEB_HTTP_SERVER_PRIORITY**: задает приоритет потока HTTP-сервера. По умолчанию указано значение 16 для задания приоритета 16.
- **NX_WEB_HTTP_NO_FILEX**: если этот параметр определен, он предоставляет заглушку для зависимостей FileX. HTTPS-клиент будет работать без каких-либо изменений, если этот параметр определен. Для надлежащей работы HTTPS-сервер нужно будет изменить либо пользователю потребуется создать несколько служб FileX.
- **NX_WEB_HTTP_TYPE_OF_SERVICE**: задает тип службы, необходимый для TCP-запросов HTTPS. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.
- **NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE**: задает число тактов таймера, в течение которых может выполняться поток сервера, прежде чем уступить ресурсы потокам с таким же приоритетом. Значение по умолчанию — 2. Этот параметр не рекомендуется использовать.
- **NX_WEB_HTTP_FRAGMENT_OPTION**: поддержка фрагментирования для TCP-запросов HTTP. По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование TCP в HTTP.
- **NX_HTTP_SERVER_WINDOW_SIZE**: размер окна сокета для сервера. Значение по умолчанию — 2048 байт.
- **NX_WEB_HTTP_TIME_TO_LIVE**: указывает число маршрутизаторов, которые может пройти этот пакет, прежде чем он будет удален. Значение по умолчанию — 0x80.
- **NX_WEB_HTTP_SERVER_TIMEOUT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу. Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_server_socket_accept*. Значение по умолчанию — 10 \* *NX_IP_PERIODIC_RATE*.
- **NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_disconnect*. Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_receive*. Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_SERVER_TIMEOUT_SEND**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_send*. Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).
- **NX_WEB_HTTP_MAX_HEADER_FIELD**: **указывает максимальный размер поля заголовка HTTP. Значение по умолчанию — 256.**
- **NX_WEB_HTTP_MULTIPART_ENABLE** — если этот параметр определен, он позволяет HTTP-серверу поддерживать составные HTTP-запросы. **
- **NX_WEB_HTTP_SERVER_MAX_PENDING**: указывает число подключений к HTTPS-серверу, которые можно поставить в очередь. Значение по умолчанию равно удвоенному максимальному количеству сеансов сервера.
- **NX_WEB_HTTP_MAX_RESOURCE**: указывает допустимое число байтов в предоставляемом клиентом *имени ресурса*. Значение по умолчанию — 40.
- **NX_WEB_HTTP_MAX_NAME**: указывает допустимое число байтов в предоставляемом клиентом *имени пользователя*. Значение по умолчанию — 20.
- **NX_WEB_HTTP_MAX_PASSWORD**: указывает допустимое число байтов в предоставляемом клиентом *пароле*. Значение по умолчанию — 20.
- **NX_WEB_HTTP_SERVER_SESSION_MAX**: указывает количество одновременных сеансов для HTTP- или HTTPS-сервера. Для каждого сеанса выделяются сокет TCP и сеанс TLS (если включен протокол HTTPS). Значение по умолчанию — 2.
- **NX_WEB_HTTPS_ENABLE**: если этот макрос определен, он включает протоколы TLS и HTTPS. Оставьте значение без определения, чтобы освободить ресурсы, если требуется только протокол HTTP без шифрования. По умолчанию этот макрос отключен.
- **NX_WEB_HTTPS_KEEPALIVE_DISABLE**: если этот макрос определен, он отключает функцию проверки активности HTTP. По умолчанию этот макрос отключен.
- **NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE**: указывает минимальный размер пакетов в пуле, заданном при создании сервера. Минимальный размер нужно указать, чтобы обеспечить включение полного заголовка HTTP в один пакет. Значение по умолчанию — 600.
- **NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE**: указывает минимальный размер пакетов в пуле, заданном при создании клиента. Минимальный размер нужно указать, чтобы обеспечить включение полного заголовка HTTP в один пакет. Значение по умолчанию — 600.
- **NX_WEB_HTTP_SERVER_RETRY_SECONDS**: задает время ожидания повторной передачи в сокет сервера в секундах. Значение по умолчанию — 2.
- **NX_WEB_HTTP_SERVER_RETRY_MAX**: задает максимальное число повторных передач в сокет сервера. Значение по умолчанию — 10.
- **NX_WEB_HTTP_ SERVER_RETRY_SHIFT**: это значение используется для указания времени ожидания следующей повторной передачи. Текущее время ожидания умножается на число повторных передач на текущий момент с добавлением значения для смещения времени ожидания сокета. Значение по умолчанию — 1 (для удвоения времени ожидания).
- **NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH**: указывает максимальное число пакетов, которых можно поставить в очередь для повторной передачи в сокет сервера. Если число пакетов в очереди достигает этого значения, пакеты не будут отправляться, пока один или несколько пакетов в очереди не будут освобождены. Значение по умолчанию — 20.
