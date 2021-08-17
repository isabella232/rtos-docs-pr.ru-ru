---
title: Глава 2. Установка и использование ОСРВ Azure NetX Secure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Secure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d11e50b2ab74ee147f682567d142768de6108fc18264e9d8bc69bbfc8a32cc0a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801875"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>Глава 2. Установка и использование ОСРВ Azure NetX Secure

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Secure.

## <a name="product-version-number"></a>Номер версии продукта

Пользователь может проверить номер версии продукта, выполнив поиск следующих символов в nx_secure_tls.h:

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

В выпусках пакетов обновления указан следующий символ, обозначающий номер пакета обновления:

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>Дистрибутивы продукта

Пакет NetX Secure доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). Он содержит файлы исходного кода, файлы включаемых компонентов и PDF-файл, содержащий этот документ:

- **nx_secure_tls_api.h**: файл заголовка общедоступного API для NetX Secure TLS;
- **nx_secure_tls_user.h**: здесь пользователь может определить файл заголовка для NetX Secure TLS;
- **nx_secure_tls_port.h**: относящиеся к различным платформам определения для NetX Secure;
- **nx_secure_tls.h**: файл заголовка для NetX Secure TLS;
- **nx_secure_tls&#42;.c/h**: файлы исходного кода C/H для NetX Secure TLS;
- **nx_crypto&#42;.c/h**: файлы исходного кода C/H для шифрования NetX Secure;
- **nx_secure_x509&#42;.c/h**: файлы исходного кода C/H для цифровых сертификатов X.509;
- **demo_netx_secure_tls.c**: демонстрационный файл исходного кода C для NetX Secure TLS;
- **NetX_Secure_User_Guide.pdf**: PDF-файл с описанием продукта NetX Secure.

> [!NOTE]
> Файлы nx_crypto* предоставляются для различных аппаратных платформ в подкаталоге родительского каталога NetX Secure.

## <a name="netx-secure-installation"></a>Установка NetX Secure

Чтобы использовать NetX Secure, весь дистрибутив, упомянутый ранее, нужно скопировать на тот же уровень каталога, на котором установлен NetX. Например, если компонент NetX установлен в каталоге " *\threadx\arm7\NetX*", то каталоги *nx_secure**.* нужно скопировать в " *\threadx\arm7\NetXSecure*".

## <a name="using-netx-secure"></a>Использование NetX Secure

Использовать NetX Secure TLS просто. В код приложения нужно включить файл *nx_secure_tls_api.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно. После добавления *nx_secure_tls_api.h* код приложения сможет выполнять вызовы функций NetX Secure, указанные далее в этом руководстве. Приложение также должно импортировать файлы *nx_secure**.* в библиотеку NetXSecure, а относящиеся к определенной платформе файлы *nx_crypto**.* — в библиотеку NetXCrypto.

## <a name="small-example-system-tls-client"></a>Пример небольшой системы (клиент TLS)

Пример того, как просто использовать NetX Secure, приведен на рисунке 1.1 ниже. Там продемонстрирован простой клиент TLS, использующий программные модули шифрования (не зависящие от оборудования) для шифрования. Он предназначен для работы с сервером обратного эхо-вывода (openssl s_server -rev).

Обратите внимание, что для запуска этого примера потребуется сертификат ЦС X.509 для проверки подлинности сертификата целевого сервера. Для примера OpenSSL достаточно иметь простой двухуровневую PKI (сертификат корневого ЦС-> >сертификат сервера). Нужно заполнить массив "trusted_ca_data" двоичной версией сертификата ЦС в кодировке DER и обновить переменную "trusted_ca_length", чтобы она отражала фактическую длину сертификата.

Вам также потребуется сетевой драйвер для используемого оборудования (замените параметр "nx_driver_xx" в вызове nx_ip_create).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

**Рисунок 1.1. Пример использования NetX Secure с NetX**

## <a name="small-example-system-tls-web-server"></a>Пример небольшой системы (веб-сервер TLS)

Пример того, как просто использовать NetX Secure, приведен на рисунке 1.1 ниже, где показан простой веб-сервер TLS (HTTPS).

Обратите внимание, что для запуска этого примера вам потребуется сертификат X.509, чтобы идентифицировать свой сервер для клиентов TLS. Для большинства веб-браузеров должно быть достаточно простого самозаверяющего сертификата. Ваш браузер сообщит о том, что не может проверить подлинность сервера, и в некоторых случаях может быть не в состоянии установить подключение TLS/HTTPS к вашему серверу<sup>3</sup>. Нужно заполнить массив "certificate_data" двоичной версией сертификата сервера в кодировке DER и обновить переменную "certificate_length", чтобы она отражала фактическую длину сертификата. Также необходимо заполнить массив "private_key" версией закрытого ключа сертификата в кодировке DER, отформатированную с использованием PKCS 1 для ключа RSA и с использованием RFC 5915 для ключей ECC. Укажите в переменной "private_key_length" фактическую длину данных ключа.

> [!IMPORTANT]
> Некоторые браузеры (в частности некоторые версии Chrome) могут отклонять самозаверяющие сертификаты. В этом случае можно создать двухуровневую PKI с сертификатом корневого ЦС, который используется для подписи сертификата сервера. В этом случае сертификат корневого ЦС устанавливается в браузере в качестве доверенного корневого сертификата. !!! Важно! Удалите сертификат корневого ЦС из браузера после завершения работы и не используйте его в рабочих приложениях.

Вам также потребуется сетевой драйвер для используемого оборудования (замените параметр "nx_driver_xx" в вызове nx_ip_create).

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

**Рисунок 1.2. Пример использования NetX Secure с NetX**

## <a name="a-note-on-tls-session-error-recovery"></a>Примечание о восстановлении после ошибки сеанса TLS

В примерах систем выше описаны общие черты клиента и сервера TLS соответственно, однако обработка ошибок пропущена для большей ясности. Тем не менее, обеспечиваемая протоколом TLS безопасность частично зависит от правильной обработки условий ошибки. Как правило, наиболее серьезные потенциальные проблемы будут обрабатываться в самом стеке TLS, однако важно, чтобы приложение TLS реагировало на ошибки TLS, которые не обрабатываются в реализации TLS, и производило последующее восстановление должным образом.

Чтобы продемонстрировать необходимую логику для правильной обработки ошибок, в следующей функции показана типичная коллекция служб API, которую можно использовать для надлежащей обработки ошибок TLS и правильного сброса состояния TLS после возникновения условия ошибки. Кроме того раздела, в котором это указано, данная логика применяется как к экземплярам как клиента TLS, так и сервера TLS.

Обратите внимание, что наиболее важными вызовами API в функции являются вызовы служб *nx_secure_tls_session_end*, которая правильно закрывает подтверждение или сеанс TLS, и *nx_secure_tls_session_reset*, которая очищает состояние сеанса TLS, чтобы экземпляр управляющей структуры tls_session можно было повторно использовать для нового сеанса TLS. Обратите внимание и на то, что *nx_secure_tls_session_reset* не очищает настроенное пользователем состояние, например сертификаты или назначенные буферы, что позволяет еще раз использовать сеанс без повторного вызова *nx_secure_tls_session_create*. Чтобы полностью очистить все состояние сеанса TLS, вместо нее можно использовать службу *nx_secure_tls_session_delete*.

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для создания NetX Secure. Ниже приведен список всех параметров, каждый из которых подробно описан ниже.

| Определение | Значение |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | Этот параметр позволяет отключить базовую проверку ошибок NetX Secure. Обычно он используется после отладки приложения. |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | Этот параметр позволяет задать максимальный ожидаемый модуль RSA в битах. Значение по умолчанию — 4096 для 4096-разрядного модуля. Другие возможные значения: 3072, 2048 или 1024 (не рекомендуется). |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | Этот параметр позволяет протоколу TLS принимать самозаверяющие сертификаты с удаленного узла. По умолчанию протокол TLS отклоняет самозаверяющие сертификаты сервера в целях обеспечения безопасности. Если этот макрос определен, для принятия самозаверяющих сертификатов их по-прежнему нужно добавить в доверенное хранилище. |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | Этот параметр позволяет включить необязательную проверку сертификата клиента X.509 для серверов TLS<sup>4</sup>.  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | Этот параметр позволяет включить функции общего ключа (PSK). Цифровые сертификаты при этом не отключаются. |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | Этот параметр позволяет удалить весь код стека TLS, связанный с режимом клиента TLS, уменьшая объем кода и использование данных. |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | Этот параметр позволяет удалить весь код стека TLS, связанный с режимом сервера TLS, уменьшая объем кода и использование данных.  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | Этот параметр позволяет удалить всю логику TLS для комплектов шифров шифрования на основе эллиптических кривых (ECC). Эти комплекты шифров являются необязательными в TLS 1.2 и более ранних версиях, и их отключение может обеспечить значительное уменьшение размера кода и данных.|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | Этот параметр позволяет включить режим TLS 1.3. TLS 1.3 является последней версией протокола TLS и по умолчанию отключен. |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | Этот параметр позволяет включить устаревший режим TLS 1.0. TLS 1.0 считается устаревшим, поэтому его следует включать только для обратной совместимости с более старыми приложениями. |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | Этот параметр позволяет включить устаревший режим TLS 1.1. TLS 1.1 считается устаревшим, поэтому его следует включать только для обратной совместимости с более старыми приложениями. |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | Этот параметр позволяет отключить режим TLS 1.1. Он задан по умолчанию. TLS 1.1 отключен для использования только более надежной версии TLS 1.2<sup>5</sup>.  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | Этот параметр позволяет включить сравнение строгих различающихся имен для поиска и проверки сертификатов X.509. По умолчанию сравниваются только поля общих имен различающихся имен.|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | Этот параметр позволяет включить необязательные поля различающихся имен X.509 за счет дополнительного использования памяти для сертификатов X.509. |

4. Обратите внимание, что этот параметр позволяет только связать код с приложением. Для использования проверки сертификата клиента потребуется включить эту функцию с помощью службы API nx_secure_tls_session_client_verify_enable или настроить ее с помощью службы nx_secure_tls_session_x509_client_verify_configure.

5. Обратите внимание, что также можно отключить TLS 1.2 при использовании только TLS 1.0 или только TLS 1.1. Однако это не рекомендуется и не поддерживается напрямую.
