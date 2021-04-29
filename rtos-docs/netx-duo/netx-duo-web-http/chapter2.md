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
# <a name="chapter-2---installation-and-use-of-http-and-https"></a><span data-ttu-id="26230-103">Глава 2. Установка и использование протоколов HTTP для HTTPS</span><span class="sxs-lookup"><span data-stu-id="26230-103">Chapter 2 - Installation and use of HTTP and HTTPS</span></span>

<span data-ttu-id="26230-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Web HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="26230-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="26230-105">Product Distribution</span></span>

<span data-ttu-id="26230-106">Пакет HTTP для NetX доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="26230-106">HTTP for NetX is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="26230-107">Этот пакет содержит три файла исходного кода, два включаемых файла и PDF-файл, содержащий этот документ:</span><span class="sxs-lookup"><span data-stu-id="26230-107">The package includes three source files, two include files, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="26230-108">**nx_web_http_common.h**: общий файл заголовка для NetX Web HTTP;</span><span class="sxs-lookup"><span data-stu-id="26230-108">**nx_web_http_common.h** Common header file for NetX Web HTTP</span></span>
- <span data-ttu-id="26230-109">**nx_web_http_client.h**: файл заголовка HTTP-клиента для NetX Web;</span><span class="sxs-lookup"><span data-stu-id="26230-109">**nx_web_http_client.h** Header file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="26230-110">**nx_web_http_server.h**: файл заголовка HTTP-сервера для NetX Web;</span><span class="sxs-lookup"><span data-stu-id="26230-110">**nx_web_http_server.h** Header file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="26230-111">**nx_web_http_client.c**: файл сходного кода C HTTP-клиента для NetX Web;</span><span class="sxs-lookup"><span data-stu-id="26230-111">**nx_web_http_client.c** C Source file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="26230-112">**nx_web_http_server.c**: файл исходного кода C HTTP-сервера для NetX Web;</span><span class="sxs-lookup"><span data-stu-id="26230-112">**nx_web_http_server.c** C Source file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="26230-113">**nx_tcpserver.c**: файл исходного кода C для нескольких сокетов TCP;</span><span class="sxs-lookup"><span data-stu-id="26230-113">**nx_tcpserver.c** C Source file for multiple TCP sockets</span></span>
- <span data-ttu-id="26230-114">**nx_tcpserver.h**: файл заголовка для определения символов HTTPS-сервера;</span><span class="sxs-lookup"><span data-stu-id="26230-114">**nx_tcpserver.h** Header file for defining HTTPS Server symbols</span></span>
- <span data-ttu-id="26230-115">**nx_md5.c**: дайджест-алгоритмы MD5;</span><span class="sxs-lookup"><span data-stu-id="26230-115">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="26230-116">**filex_stub.h**: файл заглушки при отсутствии FileX;</span><span class="sxs-lookup"><span data-stu-id="26230-116">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="26230-117">**nx_web_http.pdf**: описание протокола HTTP для NetX Web;</span><span class="sxs-lookup"><span data-stu-id="26230-117">**nx_web_http.pdf** Description of HTTP for NetX Web</span></span>
- <span data-ttu-id="26230-118">**demo_netx_web_http.c**: демонстрационный файл для NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-118">**demo_netx_web_http.c** NetX Web HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="26230-119">Установка протокола HTTP</span><span class="sxs-lookup"><span data-stu-id="26230-119">HTTP Installation</span></span>

<span data-ttu-id="26230-120">Чтобы использовать NetX Web HTTP, весь дистрибутив, упомянутый ранее, необходимо скопировать в каталог, где установлен экземпляр NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="26230-120">In order to use NetX Web HTTP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="26230-121">Например, если экземпляр NetX Duo установлен в каталог *\threadx\arm7\green*, то в него нужно скопировать файлы *nx_web_http_client.h*, *nx_web_http_client.c (для клиентских приложений NetX Web HTTP) и nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c и nx_tcpserver.h (для серверных приложений NetX Web HTTP). Для клиентских и серверных приложений файл nx_web_http_common.h также должен находиться в этом каталоге. Кроме того, в этот каталог нужно скопировать файл nx_md5.c*, если используется дайджест-проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="26230-121">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nx_web_http_client.h* and *nx_web_http_client.c for NetX Web HTTP Client applications, and nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c and nx_tcpserver.h for NetX Web HTTP Server applications. For both client and server applications, nx_web_http_common.h must be in this directory as well. nx_md5.c* should also be copied into this directory if digest authentication is being used.</span></span> <span data-ttu-id="26230-122">Для запуска демонстрационного приложения драйвера ОЗУ файлы HTTP-клиента и HTTP-сервера нужно скопировать в один каталог.</span><span class="sxs-lookup"><span data-stu-id="26230-122">For the demo ‘ram driver’ application HTTP Client and Server files should be copied into the same directory.</span></span>

<span data-ttu-id="26230-123">При использовании протокола TLS необходим отдельный каталог NetX Secure, содержащий файлы исходного кода TLS.</span><span class="sxs-lookup"><span data-stu-id="26230-123">If using TLS, you should have a separate NetX Secure directory containing the TLS source files.</span></span>

## <a name="using-http"></a><span data-ttu-id="26230-124">Использование HTTP</span><span class="sxs-lookup"><span data-stu-id="26230-124">Using HTTP</span></span>

<span data-ttu-id="26230-125">Использовать NetX Web HTTP просто.</span><span class="sxs-lookup"><span data-stu-id="26230-125">Using NetX Web HTTP is easy.</span></span> <span data-ttu-id="26230-126">Как правило, код приложения должен включать в себя файлы *nx_web_http_client.h* и (или) *nx_web_http_server.h* после добавления файлов *tx_api.h, fx_api.h* и *nx_api.h* (файл *nx_web_http_common.h* включается автоматически).</span><span class="sxs-lookup"><span data-stu-id="26230-126">Basically, the application code must include *nx_web_http_client.h* and/or *nx_web_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h* (*nx_web_http_common.h* is automatically included).</span></span> <span data-ttu-id="26230-127">Эти файлы заголовка позволяют приложению использовать ThreadX, FileX и NetX Duo соответственно.</span><span class="sxs-lookup"><span data-stu-id="26230-127">Those headers enable the application to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="26230-128">Для поддержки протокола HTTPS файлы заголовка должны быть добавлены после включения файла *nx_secure_tls.h*, чтобы обеспечить поддержку протокола TLS.</span><span class="sxs-lookup"><span data-stu-id="26230-128">For HTTPS support, the headers must be included after the *nx_secure_tls.h* file is included to bring in TLS support.</span></span>

<span data-ttu-id="26230-129">После добавления файлов заголовка HTTP код приложения сможет выполнять вызовы функций HTTP, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="26230-129">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="26230-130">В процессе сборки приложение также нужно связать с файлами *nx_web_http_client.c* (для HTTP(s)-клиентов), *nx_web_http_server.c и nx_tcpserver.c* (для HTTP(s)-серверов) и *nx_md5.c* (для дайджест-проверки подлинности).</span><span class="sxs-lookup"><span data-stu-id="26230-130">The application must also link with *nx_web_http_client.c for HTTP(S) clients*, *nx_web_http_server.c and nx_tcpserver.c for HTTP(S) servers*, and *nx_md5.c (for digest authentication)* in the build process.</span></span> <span data-ttu-id="26230-131">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="26230-131">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="26230-132">Это все, что необходимо для использования NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-132">This is all that is required to use NetX Web HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="26230-133">Если NX_WEB_HTTP_DIGEST_ENABLE не указывается в процессе сборки, файл *md5.c* не нужно добавлять в приложение.</span><span class="sxs-lookup"><span data-stu-id="26230-133">If NX_WEB_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="26230-134">Аналогично, если не требуются возможности HTTP-клиента, файл *nx_web_http_client.c* может быть опущен. Если не требуются возможности HTTP-сервера, то можно опустить файл *nx_web_http_server.c*.</span><span class="sxs-lookup"><span data-stu-id="26230-134">Similarly, if no HTTP Client capabilities are required, the *nx_web_http_client.c* file may be omitted and if no HTTP Server capabilities are required, *nx_web_http_server.c* may be omitted.</span></span>
>
> <span data-ttu-id="26230-135">Если не определен параметр NX_WEB_HTTPS_ENABLE для включения протокола HTTPS (вместо использования только HTTP без шифрования), то наличие NetX Secure TLS в сборке не обязательно.</span><span class="sxs-lookup"><span data-stu-id="26230-135">Unless NX_WEB_HTTPS_ENABLE is defined in order to enable HTTPS (instead of using only plaintext HTTP) then NetX Secure TLS does not need to be in the build.</span></span>
>
> <span data-ttu-id="26230-136">Так как протокол HTTP использует службы NetX TCP, то перед его использованием нужно включить протокол TCP с помощью вызова *nx_tcp_enable*.</span><span class="sxs-lookup"><span data-stu-id="26230-136">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable()* call prior to using HTTP.</span></span>
>
> <span data-ttu-id="26230-137">При использовании протокола HTTPS с NetX Secure TLS необходимо инициализировать TLS с помощью *nx_secure_tls_initialize()* перед вызовом подпрограмм HTTPS.</span><span class="sxs-lookup"><span data-stu-id="26230-137">When using HTTPS with NetX Secure TLS, TLS must be initialized with *nx_secure_tls_initialize()* prior to calling HTTPS routines.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="26230-138">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="26230-138">Small Example System</span></span>

<span data-ttu-id="26230-139">Пример использования NetX Web HTTP описан на рисунке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="26230-139">An example of how to use NetX Web HTTP is described in Figure 1.1 below.</span></span>

> [!CAUTION]
> <span data-ttu-id="26230-140">Он предоставлен только в демонстрационных целях, и не гарантируется, что его можно будет скомпилировать и запустить "как есть".</span><span class="sxs-lookup"><span data-stu-id="26230-140">This is provided for demonstration purposes only and is not guaranteed to compile and run as is.</span></span>
>
> <span data-ttu-id="26230-141">Демонстрационные файлы исходного кода, сборка которых будет правильно выполнена в среде Logic Express, доступны в дистрибутиве выпуска NetX Duo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="26230-141">Please refer to the NetX Duo HTTPS release code distribution for  demo source code file(s) that will properly build in the native Express Logic environment.</span></span>  <span data-ttu-id="26230-142">Также имейте в виду, что эти демонстрационные файлы намеренно созданы очень простыми, так как они предназначены для создания приложений HTTPS и (или) NetX Duo HTTPS новыми пользователями.</span><span class="sxs-lookup"><span data-stu-id="26230-142">Also be aware that these demos are intentionally kept very simple as they are intended to introduce HTTPS and/or NetX Duo HTTPS application to new users.</span></span>

<span data-ttu-id="26230-143">В этом примере указаны включаемые файлы HTTP *nx_web_http_client.h и nx_web_http_server.h* (*netx_web_http_common.h* включается автоматически).</span><span class="sxs-lookup"><span data-stu-id="26230-143">In this example, the HTTP include file *nx_web_http_client.h and nx_web_http_server.h are* brought in (*netx_web_http_common.h* is included automatically).</span></span> <span data-ttu-id="26230-144">Затем создается HTTP-сервер с помощью *tx_application_define*.</span><span class="sxs-lookup"><span data-stu-id="26230-144">Next, the HTTP Server is created in “*tx_application_define*”.</span></span> <span data-ttu-id="26230-145">Обратите внимание на то, что блок управления HTTP-сервером *Server* был задан в качестве глобальной переменной ранее.</span><span class="sxs-lookup"><span data-stu-id="26230-145">Note that the HTTP Server control block “*Server*” was defined as a global variable previously.</span></span> <span data-ttu-id="26230-146">После успешного создания HTTPS-сервер запускается.</span><span class="sxs-lookup"><span data-stu-id="26230-146">After successful creation, the HTTPS Server is started.</span></span> <span data-ttu-id="26230-147">Затем создается HTTPS-клиент.</span><span class="sxs-lookup"><span data-stu-id="26230-147">The HTTPS Client is then created.</span></span> <span data-ttu-id="26230-148">Он записывает файл и считывает его файл.</span><span class="sxs-lookup"><span data-stu-id="26230-148">It writes the file and reads the file back.</span></span>

> [!NOTE]
> <span data-ttu-id="26230-149">В этой системе определен параметр NX_WEB_HTTPS_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="26230-149">NX_WEB_HTTPS_ENABLE is defined on this system.</span></span>

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

<span data-ttu-id="26230-150">**Рисунок 1.1. Пример использования протокола HTTPS с NetX и NetX Secure TLS**</span><span class="sxs-lookup"><span data-stu-id="26230-150">**Figure 1.1 Example of HTTPS use with NetX and NetX Secure TLS**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="26230-151">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="26230-151">Configuration Options</span></span>

<span data-ttu-id="26230-152">Существует ряд параметров конфигурации для сборки HTTP для NetX.</span><span class="sxs-lookup"><span data-stu-id="26230-152">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="26230-153">Ниже приведен список всех параметров с подробным описанием каждого из них.</span><span class="sxs-lookup"><span data-stu-id="26230-153">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="26230-154">Приведены значения по умолчанию, но их можно переопределить перед включением файлов *nx_web_http_server.h и nx_http_server.h*.</span><span class="sxs-lookup"><span data-stu-id="26230-154">The default values are listed but can be redefined prior to inclusion of *nx_web_http_client.h and nx_web_http_server.h*:</span></span>

- <span data-ttu-id="26230-155">**NX_DISABLE_ERROR_CHECKING**: если этот параметр определен, он удаляет базовую проверку на ошибки HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-155">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="26230-156">Обычно он используется после отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="26230-156">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="26230-157">**NX_WEB_HTTP_DIGEST_ENABLE**: если этот параметр определен, на HTTPS-сервере включается дайджест-проверка подлинности MD5.</span><span class="sxs-lookup"><span data-stu-id="26230-157">**NX_WEB_HTTP_DIGEST_ENABLE** If defined, authentication using the MD5 digest is enabled on the HTTPS Server.</span></span> <span data-ttu-id="26230-158">По умолчанию он не определен.</span><span class="sxs-lookup"><span data-stu-id="26230-158">By default it is not defined.</span></span>
- <span data-ttu-id="26230-159">**NX_WEB_HTTP_SERVER_PRIORITY**: задает приоритет потока HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-159">**NX_WEB_HTTP_SERVER_PRIORITY** The priority of the HTTPS Server thread.</span></span> <span data-ttu-id="26230-160">По умолчанию указано значение 16 для задания приоритета 16.</span><span class="sxs-lookup"><span data-stu-id="26230-160">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="26230-161">**NX_WEB_HTTP_NO_FILEX**: если этот параметр определен, он предоставляет заглушку для зависимостей FileX.</span><span class="sxs-lookup"><span data-stu-id="26230-161">**NX_WEB_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="26230-162">HTTPS-клиент будет работать без каких-либо изменений, если этот параметр определен.</span><span class="sxs-lookup"><span data-stu-id="26230-162">The HTTPS Client will function without any change if this option is defined.</span></span> <span data-ttu-id="26230-163">Для надлежащей работы HTTPS-сервер нужно будет изменить либо пользователю потребуется создать несколько служб FileX.</span><span class="sxs-lookup"><span data-stu-id="26230-163">The HTTPS Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="26230-164">**NX_WEB_HTTP_TYPE_OF_SERVICE**: задает тип службы, необходимый для TCP-запросов HTTPS.</span><span class="sxs-lookup"><span data-stu-id="26230-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTPS TCP requests.</span></span> <span data-ttu-id="26230-165">По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="26230-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="26230-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE**: задает число тактов таймера, в течение которых может выполняться поток сервера, прежде чем уступить ресурсы потокам с таким же приоритетом.</span><span class="sxs-lookup"><span data-stu-id="26230-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="26230-167">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="26230-167">The default value is 2.</span></span> <span data-ttu-id="26230-168">Этот параметр не рекомендуется использовать.</span><span class="sxs-lookup"><span data-stu-id="26230-168">Note this option is deprecated.</span></span>
- <span data-ttu-id="26230-169">**NX_WEB_HTTP_FRAGMENT_OPTION**: поддержка фрагментирования для TCP-запросов HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="26230-170">По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование TCP в HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-170">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="26230-171">**NX_HTTP_SERVER_WINDOW_SIZE**: размер окна сокета для сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="26230-172">Значение по умолчанию — 2048 байт.</span><span class="sxs-lookup"><span data-stu-id="26230-172">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="26230-173">**NX_WEB_HTTP_TIME_TO_LIVE**: указывает число маршрутизаторов, которые может пройти этот пакет, прежде чем он будет удален.</span><span class="sxs-lookup"><span data-stu-id="26230-173">**NX_WEB_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="26230-174">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="26230-174">The default value is set to 0x80.</span></span>
- <span data-ttu-id="26230-175">**NX_WEB_HTTP_SERVER_TIMEOUT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу.</span><span class="sxs-lookup"><span data-stu-id="26230-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="26230-176">Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="26230-176">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="26230-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_server_socket_accept*.</span><span class="sxs-lookup"><span data-stu-id="26230-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept()* calls.</span></span> <span data-ttu-id="26230-178">Значение по умолчанию — 10 \* *NX_IP_PERIODIC_RATE*.</span><span class="sxs-lookup"><span data-stu-id="26230-178">The default value is set to (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="26230-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_disconnect*.</span><span class="sxs-lookup"><span data-stu-id="26230-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect()* calls.</span></span> <span data-ttu-id="26230-180">Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="26230-180">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="26230-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_receive*.</span><span class="sxs-lookup"><span data-stu-id="26230-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive()* calls.</span></span> <span data-ttu-id="26230-182">Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="26230-182">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="26230-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_send*.</span><span class="sxs-lookup"><span data-stu-id="26230-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send()* calls.</span></span> <span data-ttu-id="26230-184">Значение по умолчанию — 10 секунд (10 \* *NX_IP_PERIODIC_RATE*).</span><span class="sxs-lookup"><span data-stu-id="26230-184">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="26230-185">**NX_WEB_HTTP_MAX_HEADER_FIELD**: **указывает максимальный размер поля заголовка HTTP. Значение по умолчанию — 256.**</span><span class="sxs-lookup"><span data-stu-id="26230-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Specifies the maximum size of the HTTP header field. The default value is 256.**</span></span>
- <span data-ttu-id="26230-186">**NX_WEB_HTTP_MULTIPART_ENABLE** — если этот параметр определен, он позволяет HTTP-серверу поддерживать составные HTTP-запросы.</span><span class="sxs-lookup"><span data-stu-id="26230-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*If defined, enables HTTPS Server to support multipart HTTP requests.</span></span> **
- <span data-ttu-id="26230-187">**NX_WEB_HTTP_SERVER_MAX_PENDING**: указывает число подключений к HTTPS-серверу, которые можно поставить в очередь.</span><span class="sxs-lookup"><span data-stu-id="26230-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTPS Server.</span></span> <span data-ttu-id="26230-188">Значение по умолчанию равно удвоенному максимальному количеству сеансов сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-188">The default value is set to twice the maximum number of server sessions.</span></span>
- <span data-ttu-id="26230-189">**NX_WEB_HTTP_MAX_RESOURCE**: указывает допустимое число байтов в предоставляемом клиентом *имени ресурса*.</span><span class="sxs-lookup"><span data-stu-id="26230-189">**NX_WEB_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="26230-190">Значение по умолчанию — 40.</span><span class="sxs-lookup"><span data-stu-id="26230-190">The default value is set to 40.</span></span>
- <span data-ttu-id="26230-191">**NX_WEB_HTTP_MAX_NAME**: указывает допустимое число байтов в предоставляемом клиентом *имени пользователя*.</span><span class="sxs-lookup"><span data-stu-id="26230-191">**NX_WEB_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="26230-192">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="26230-192">The default value is set to 20.</span></span>
- <span data-ttu-id="26230-193">**NX_WEB_HTTP_MAX_PASSWORD**: указывает допустимое число байтов в предоставляемом клиентом *пароле*.</span><span class="sxs-lookup"><span data-stu-id="26230-193">**NX_WEB_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="26230-194">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="26230-194">The default value is set to 20.</span></span>
- <span data-ttu-id="26230-195">**NX_WEB_HTTP_SERVER_SESSION_MAX**: указывает количество одновременных сеансов для HTTP- или HTTPS-сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Specifies the number of simultaneous sessions for an HTTP or HTTPS Server.</span></span> <span data-ttu-id="26230-196">Для каждого сеанса выделяются сокет TCP и сеанс TLS (если включен протокол HTTPS).</span><span class="sxs-lookup"><span data-stu-id="26230-196">A TCP socket and a TLS session (if HTTPS is enabled) are allocated for each session.</span></span> <span data-ttu-id="26230-197">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="26230-197">The default value is set to 2.</span></span>
- <span data-ttu-id="26230-198">**NX_WEB_HTTPS_ENABLE**: если этот макрос определен, он включает протоколы TLS и HTTPS.</span><span class="sxs-lookup"><span data-stu-id="26230-198">**NX_WEB_HTTPS_ENABLE** If defined, this macro enables TLS and HTTPS.</span></span> <span data-ttu-id="26230-199">Оставьте значение без определения, чтобы освободить ресурсы, если требуется только протокол HTTP без шифрования.</span><span class="sxs-lookup"><span data-stu-id="26230-199">Leave undefined to free up resources if only plaintext HTTP is desired.</span></span> <span data-ttu-id="26230-200">По умолчанию этот макрос отключен.</span><span class="sxs-lookup"><span data-stu-id="26230-200">By default, this macro is not defined.</span></span>
- <span data-ttu-id="26230-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE**: если этот макрос определен, он отключает функцию проверки активности HTTP.</span><span class="sxs-lookup"><span data-stu-id="26230-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** If defined, this macro disables HTTP keep-alive feature.</span></span> <span data-ttu-id="26230-202">По умолчанию этот макрос отключен.</span><span class="sxs-lookup"><span data-stu-id="26230-202">By default, this macro is not defined.</span></span>
- <span data-ttu-id="26230-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE**: указывает минимальный размер пакетов в пуле, заданном при создании сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at server creation.</span></span> <span data-ttu-id="26230-204">Минимальный размер нужно указать, чтобы обеспечить включение полного заголовка HTTP в один пакет.</span><span class="sxs-lookup"><span data-stu-id="26230-204">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="26230-205">Значение по умолчанию — 600.</span><span class="sxs-lookup"><span data-stu-id="26230-205">The default value is set to 600.</span></span>
- <span data-ttu-id="26230-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE**: указывает минимальный размер пакетов в пуле, заданном при создании клиента.</span><span class="sxs-lookup"><span data-stu-id="26230-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="26230-207">Минимальный размер нужно указать, чтобы обеспечить включение полного заголовка HTTP в один пакет.</span><span class="sxs-lookup"><span data-stu-id="26230-207">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="26230-208">Значение по умолчанию — 600.</span><span class="sxs-lookup"><span data-stu-id="26230-208">The default value is set to 600.</span></span>
- <span data-ttu-id="26230-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS**: задает время ожидания повторной передачи в сокет сервера в секундах.</span><span class="sxs-lookup"><span data-stu-id="26230-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="26230-210">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="26230-210">The default value is set to 2.</span></span>
- <span data-ttu-id="26230-211">**NX_WEB_HTTP_SERVER_RETRY_MAX**: задает максимальное число повторных передач в сокет сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="26230-212">Значение по умолчанию — 10.</span><span class="sxs-lookup"><span data-stu-id="26230-212">The default value is set to 10.</span></span>
- <span data-ttu-id="26230-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT**: это значение используется для указания времени ожидания следующей повторной передачи.</span><span class="sxs-lookup"><span data-stu-id="26230-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="26230-214">Текущее время ожидания умножается на число повторных передач на текущий момент с добавлением значения для смещения времени ожидания сокета.</span><span class="sxs-lookup"><span data-stu-id="26230-214">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="26230-215">Значение по умолчанию — 1 (для удвоения времени ожидания).</span><span class="sxs-lookup"><span data-stu-id="26230-215">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="26230-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH**: указывает максимальное число пакетов, которых можно поставить в очередь для повторной передачи в сокет сервера.</span><span class="sxs-lookup"><span data-stu-id="26230-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="26230-217">Если число пакетов в очереди достигает этого значения, пакеты не будут отправляться, пока один или несколько пакетов в очереди не будут освобождены.</span><span class="sxs-lookup"><span data-stu-id="26230-217">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="26230-218">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="26230-218">The default value is set to 20.</span></span>
