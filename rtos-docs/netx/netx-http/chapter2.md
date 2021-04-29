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
# <a name="chapter-2---installation-and-use-of-netx-http"></a><span data-ttu-id="9c754-103">Глава 2. Установка и использование NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="9c754-103">Chapter 2 - Installation and use of NetX HTTP</span></span>

<span data-ttu-id="9c754-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="9c754-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="9c754-105">Product Distribution</span></span>

<span data-ttu-id="9c754-106">NetX для ОСРВ Azure можно получить из нашего репозитория общедоступного исходного кода по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="9c754-106">Azure RTOS NetX can be obtained from our public source code repository at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span>

- <span data-ttu-id="9c754-107">**nx_http_client.h** — файл заголовка HTTP-клиента для NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-107">**nx_http_client.h** Header file for HTTP Client for NetX</span></span>
- <span data-ttu-id="9c754-108">**nx_http_server.h** — файл заголовка HTTP-сервера для NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-108">**nx_http_server.h** Header file for HTTP Server for NetX</span></span>
- <span data-ttu-id="9c754-109">**nx_http_client.c** — исходный файл на C HTTP-клиента для NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-109">**nx_http_client.c** C Source file for HTTP Client for NetX</span></span>
- <span data-ttu-id="9c754-110">**nx_http_server.c** — исходный файл на C HTTP-сервера для NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-110">**nx_http_server.c** C Source file for HTTP Server for NetX</span></span>
- <span data-ttu-id="9c754-111">**nx_md5.c** — алгоритмы хэширования MD5.</span><span class="sxs-lookup"><span data-stu-id="9c754-111">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="9c754-112">**filex_stub.h** — файл заглушки при отсутствии FileX.</span><span class="sxs-lookup"><span data-stu-id="9c754-112">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="9c754-113">**nx_http.pdf** — описание HTTP для NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-113">**nx_http.pdf** Description of HTTP for NetX</span></span>
- <span data-ttu-id="9c754-114">**demo_netx_http.c** — демонстрация NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-114">**demo_netx_http.c** NetX HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="9c754-115">Установка HTTP</span><span class="sxs-lookup"><span data-stu-id="9c754-115">HTTP Installation</span></span>

<span data-ttu-id="9c754-116">Чтобы использовать HTTP для NetX, весь дистрибутив, упомянутый ранее, должен быть скопирован в тот же каталог, где установлен NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-116">In order to use HTTP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="9c754-117">Например, если NetX установлен в каталог *\threadx\arm7\green*, файлы *nx_http_client.h* и *nx_http_client.c* будут использоваться для приложений HTTP-клиента NetX, а *nx_http_server.h* и *nx_http_server.c* — для приложений сервера NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-117">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_http_client.h* and *nx_http_client.c* for NetX HTTP Client applications, and *nx_http_server.h* and *nx_http_server.c* for NetX HTTP Server applications.</span></span> <span data-ttu-id="9c754-118">*nx_md5.c* нужно скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="9c754-118">*nx_md5.c* should be copied into this directory.</span></span> <span data-ttu-id="9c754-119">Для запуска демонстрационного приложения ram driver файлы клиента и сервера NetX HTTP нужно скопировать в один каталог.</span><span class="sxs-lookup"><span data-stu-id="9c754-119">For the demo ‘ram driver’ application NetX HTTP Client and Server files should be copied into the same directory.</span></span>

## <a name="using-http"></a><span data-ttu-id="9c754-120">Использование HTTP</span><span class="sxs-lookup"><span data-stu-id="9c754-120">Using HTTP</span></span>

<span data-ttu-id="9c754-121">Использовать HTTP для NetX очень просто.</span><span class="sxs-lookup"><span data-stu-id="9c754-121">Using HTTP for NetX is easy.</span></span> <span data-ttu-id="9c754-122">Код приложения должен только включать *nx_http_client.h* и (или) *nx_http_server.h* после включения *tx_api.h, fx_api.h* и *nx_api.h* для использования ThreadX, FileX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="9c754-122">Basically, the application code must include *nx_http_client.h* and/or *nx_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h*, in order to use ThreadX, FileX, and NetX, respectively.</span></span> <span data-ttu-id="9c754-123">После добавления файлов HTTP-заголовков код приложения сможет выполнять вызовы функций HTTP, указанные далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="9c754-123">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="9c754-124">Приложение также должно включать *nx_http_client.c*, *nx_http_server.c* и *md5.c* в ходе сборки.</span><span class="sxs-lookup"><span data-stu-id="9c754-124">The application must also include *nx_http_client.c*, *nx_http_server.c*, and *md5.c* in the build process.</span></span> <span data-ttu-id="9c754-125">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="9c754-125">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="9c754-126">Это все, что необходимо для использования NetX HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-126">This is all that is required to use NetX HTTP.</span></span>

>[!NOTE] 
> <span data-ttu-id="9c754-127">Если NX_HTTP_DIGEST_ENABLE не указывается в ходе сборки, файл *md5.c* не нужно добавлять в приложение.</span><span class="sxs-lookup"><span data-stu-id="9c754-127">If NX_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="9c754-128">Аналогично, если возможности HTTP-клиента не требуются, файл *nx_http_client.c* можно опустить.</span><span class="sxs-lookup"><span data-stu-id="9c754-128">Similarly, if no HTTP Client capabilities are required, the *nx_http_client.c* file may be omitted.</span></span>

>[!NOTE] 
> <span data-ttu-id="9c754-129">Так как HTTP использует TCP-службы NetX, TCP нужно включить с помощью вызова *nx_tcp_enable* до использования HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-129">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using HTTP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="9c754-130">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="9c754-130">Small Example System</span></span>

<span data-ttu-id="9c754-131">Пример того, насколько просто использовать NetX HTTP, приведен на рис. 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="9c754-131">An example of how easy it is to use NetX HTTP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="9c754-132">В этом примере файлы HTTP *nx_http_client.h и nx_http_server.h* включаются с помощью include в строке 8.</span><span class="sxs-lookup"><span data-stu-id="9c754-132">In this example, the HTTP include file *nx_http_client.h and nx_http_server.h are* brought in at line 8.</span></span> <span data-ttu-id="9c754-133">Затем создается HTTP-сервер с помощью *tx_application_define* в строке 131.</span><span class="sxs-lookup"><span data-stu-id="9c754-133">Next, the HTTP Server is created in “*tx_application_define*” at line 131.</span></span>

>[!NOTE] 
> <span data-ttu-id="9c754-134">Блок управления HTTP-сервером *Server* задается в качестве глобальной переменной в строке 25 ранее.</span><span class="sxs-lookup"><span data-stu-id="9c754-134">The HTTP Server control block “*Server*” was defined as a global variable at line 25 previously.</span></span>

<span data-ttu-id="9c754-135">После успешного создания HTTP-сервер запускается в строке 136.</span><span class="sxs-lookup"><span data-stu-id="9c754-135">After successful creation, an HTTP Server is started at line 136.</span></span> <span data-ttu-id="9c754-136">Затем в строке 149 создается HTTP-клиент.</span><span class="sxs-lookup"><span data-stu-id="9c754-136">At line 149 the HTTP Client is created.</span></span> <span data-ttu-id="9c754-137">И наконец, клиент записывает файл в строке 157 и считывает файл обратно в строке 195.</span><span class="sxs-lookup"><span data-stu-id="9c754-137">And finally, the Client writes the file at line 157 and reads the file back at line 195.</span></span>

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

<span data-ttu-id="9c754-138">Рис. 1.1. Пример использования HTTP с NetX</span><span class="sxs-lookup"><span data-stu-id="9c754-138">Figure 1.1 Example of HTTP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="9c754-139">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="9c754-139">Configuration Options</span></span>

<span data-ttu-id="9c754-140">Существует ряд параметров конфигурации для использования HTTP с NetX.</span><span class="sxs-lookup"><span data-stu-id="9c754-140">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="9c754-141">Ниже приведен список всех параметров, каждый из которых подробно описан ниже.</span><span class="sxs-lookup"><span data-stu-id="9c754-141">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="9c754-142">Приведены значения по умолчанию, но их можно переопределить перед включением файлов *nx_http_client.h и nx_http_server.h*.</span><span class="sxs-lookup"><span data-stu-id="9c754-142">The default values are listed, but can be redefined prior to inclusion of *nx_http_client.h and nx_http_server.h*:</span></span>

- <span data-ttu-id="9c754-143">**NX_DISABLE_ERROR_CHECKING** — если определен, этот параметр удаляет базовую проверку ошибок HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-143">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="9c754-144">Обычно он используется после отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="9c754-144">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="9c754-145">**NX_HTTP_SERVER_PRIORITY** — приоритет потока HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="9c754-145">**NX_HTTP_SERVER_PRIORITY** The priority of the HTTP Server thread.</span></span> <span data-ttu-id="9c754-146">По умолчанию указано значение 16 для задания приоритета 16.</span><span class="sxs-lookup"><span data-stu-id="9c754-146">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="9c754-147">**NX_HTTP_NO_FILEX** — если определен, этот параметр предоставляет заглушку для зависимостей FileX.</span><span class="sxs-lookup"><span data-stu-id="9c754-147">**NX_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="9c754-148">HTTP-клиент будет работать без каких-либо изменений, если этот параметр определен.</span><span class="sxs-lookup"><span data-stu-id="9c754-148">The HTTP Client will function without any change if this option is defined.</span></span> <span data-ttu-id="9c754-149">Для надлежащей работы HTTP-сервер нужно будет изменить, либо пользователю потребуется создать несколько служб FileX.</span><span class="sxs-lookup"><span data-stu-id="9c754-149">The HTTP Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="9c754-150">**NX_HTTP_TYPE_OF_SERVICE** — тип службы, необходимой для TCP-запросов HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-150">**NX_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTP TCP requests.</span></span> <span data-ttu-id="9c754-151">По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="9c754-151">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="9c754-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** — число тактов таймера, которое может выполнить поток сервера, прежде чем уступить ресурсы потокам с таким же приоритетом.</span><span class="sxs-lookup"><span data-stu-id="9c754-152">**NX_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="9c754-153">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="9c754-153">The default value is 2.</span></span>
- <span data-ttu-id="9c754-154">**NX_HTTP_FRAGMENT_OPTION** — поддержка фрагментов для TCP-запросов HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-154">**NX_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="9c754-155">По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование TCP в HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c754-155">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="9c754-156">**NX_HTTP_SERVER_WINDOW_SIZE** — размер окна сокета для сервера.</span><span class="sxs-lookup"><span data-stu-id="9c754-156">**NX_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="9c754-157">Значение по умолчанию: 2048 байт.</span><span class="sxs-lookup"><span data-stu-id="9c754-157">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="9c754-158">**NX_HTTP_TIME_TO_LIVE** — указывает число маршрутов, которое может пройти этот пакет перед отменой.</span><span class="sxs-lookup"><span data-stu-id="9c754-158">**NX_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="9c754-159">Значение по умолчанию: 0x80.</span><span class="sxs-lookup"><span data-stu-id="9c754-159">The default value is set to 0x80.</span></span>
- <span data-ttu-id="9c754-160">**NX_HTTP_SERVER_TIMEOUT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу.</span><span class="sxs-lookup"><span data-stu-id="9c754-160">**NX_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="9c754-161">Значение по умолчанию: 10 секунд (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="9c754-161">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="9c754-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_server_socket_accept*.</span><span class="sxs-lookup"><span data-stu-id="9c754-162">**NX_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept* calls.</span></span> <span data-ttu-id="9c754-163">Значение по умолчанию: (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="9c754-163">The default value is set to (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="9c754-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_disconnect*.</span><span class="sxs-lookup"><span data-stu-id="9c754-164">**NX_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect* calls.</span></span> <span data-ttu-id="9c754-165">Значение по умолчанию: 10 секунд (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="9c754-165">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="9c754-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_receive*.</span><span class="sxs-lookup"><span data-stu-id="9c754-166">**NX_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive* calls.</span></span> <span data-ttu-id="9c754-167">Значение по умолчанию: 10 секунд (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="9c754-167">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="9c754-168">**NX_HTTP_SERVER_TIMEOUT_SEND** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_send*.</span><span class="sxs-lookup"><span data-stu-id="9c754-168">**NX_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send* calls.</span></span> <span data-ttu-id="9c754-169">Значение по умолчанию: 10 секунд (10 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="9c754-169">The default value is set to 10 seconds (10 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="9c754-170">**NX_HTTP_MAX_HEADER_FIELD** — указывает максимальный размер поля HTTP-заголовка.</span><span class="sxs-lookup"><span data-stu-id="9c754-170">**NX_HTTP_MAX_HEADER_FIELD** Specifies the maximum size of the HTTP header field.</span></span> <span data-ttu-id="9c754-171">Значение по умолчанию — 256.</span><span class="sxs-lookup"><span data-stu-id="9c754-171">The default value is 256.</span></span>
- <span data-ttu-id="9c754-172">**NX_HTTP_MULTIPART_ENABLE** — если определен, позволяет HTTP-серверу поддерживать составные HTTP-запросы.</span><span class="sxs-lookup"><span data-stu-id="9c754-172">**NX_HTTP_MULTIPART_ENABLE** If defined, enables HTTP Server to support multipart HTTP requests.</span></span>
- <span data-ttu-id="9c754-173">**NX_HTTP_SERVER_MAX_PENDING** — указывает число подключений, которые можно поставить в очередь к HTTP-серверу.</span><span class="sxs-lookup"><span data-stu-id="9c754-173">**NX_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTP Server.</span></span> <span data-ttu-id="9c754-174">Значение по умолчанию: 5.</span><span class="sxs-lookup"><span data-stu-id="9c754-174">The default value is set to 5.</span></span>
- <span data-ttu-id="9c754-175">**NX_HTTP_MAX_RESOURCE** — указывает число байтов, разрешенных в предоставляемом клиентом *имени ресурса*.</span><span class="sxs-lookup"><span data-stu-id="9c754-175">**NX_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="9c754-176">Значение по умолчанию: 40.</span><span class="sxs-lookup"><span data-stu-id="9c754-176">The default value is set to 40.</span></span>
- <span data-ttu-id="9c754-177">**NX_HTTP_MAX_NAME** — указывает число байтов, разрешенных в предоставляемом клиентом *имени пользователя*.</span><span class="sxs-lookup"><span data-stu-id="9c754-177">**NX_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="9c754-178">Значение по умолчанию: 20.</span><span class="sxs-lookup"><span data-stu-id="9c754-178">The default value is set to 20.</span></span>
- <span data-ttu-id="9c754-179">**NX_HTTP_MAX_PASSWORD** — указывает число байтов, разрешенных в предоставляемом клиентом *пароле*.</span><span class="sxs-lookup"><span data-stu-id="9c754-179">**NX_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="9c754-180">Значение по умолчанию: 20.</span><span class="sxs-lookup"><span data-stu-id="9c754-180">The default value is set to 20.</span></span>
- <span data-ttu-id="9c754-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** — указывает минимальный размер пакетов в пуле, заданном при создании сервера.</span><span class="sxs-lookup"><span data-stu-id="9c754-181">**NX_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Server creation.</span></span> <span data-ttu-id="9c754-182">Минимальный размер нужно указать, чтобы обеспечить включение полного HTTP-заголовка в один пакет.</span><span class="sxs-lookup"><span data-stu-id="9c754-182">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="9c754-183">Значение по умолчанию: 600.</span><span class="sxs-lookup"><span data-stu-id="9c754-183">The default value is set to 600.</span></span>
- <span data-ttu-id="9c754-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** — указывает минимальный размер пакетов в пуле, заданном при создании клиента.</span><span class="sxs-lookup"><span data-stu-id="9c754-184">**NX_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="9c754-185">Минимальный размер нужно указать, чтобы обеспечить включение полного HTTP-заголовка в один пакет.</span><span class="sxs-lookup"><span data-stu-id="9c754-185">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="9c754-186">Значение по умолчанию: 300.</span><span class="sxs-lookup"><span data-stu-id="9c754-186">The default value is set to 300.</span></span>
- <span data-ttu-id="9c754-187">**NX_HTTP_SERVER_RETRY_SECONDS** — *задает время ожидания повторной передачи на сокет сервера в секундах.* Значение по умолчанию: 2.</span><span class="sxs-lookup"><span data-stu-id="9c754-187">**NX_HTTP_SERVER_RETRY_SECONDS** *Set the Server socket retransmission timeout in seconds. The* default value is set to 2.</span></span>
- <span data-ttu-id="9c754-188">**NX_HTTP_SERVER_RETRY_MAX** — задает максимальное число повторных передач на сокете сервера.</span><span class="sxs-lookup"><span data-stu-id="9c754-188">**NX_HTTP_SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="9c754-189">Значение по умолчанию: 10.</span><span class="sxs-lookup"><span data-stu-id="9c754-189">The default value is set to 10.</span></span>
- <span data-ttu-id="9c754-190">**NX_HTTP_SERVER_ RETRY_SHIFT** — это значение используется для указания времени ожидания следующей повторной передачи.</span><span class="sxs-lookup"><span data-stu-id="9c754-190">**NX_HTTP_SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="9c754-191">Текущее время ожидания умножается на число повторных передач на текущий момент с добавлением значения для смещения времени ожидания сокета.</span><span class="sxs-lookup"><span data-stu-id="9c754-191">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="9c754-192">Значение по умолчанию: 1 (для удвоения времени ожидания).</span><span class="sxs-lookup"><span data-stu-id="9c754-192">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="9c754-193">**NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** — указывает максимальное число пакетов, которое можно поставить в очередь для повторной передачи на сокет сервера.</span><span class="sxs-lookup"><span data-stu-id="9c754-193">**NX_HTTP_ SERVER_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="9c754-194">Если число пакетов в очереди достигает этого значения, пакеты не будут отправляться, пока один пакет в очереди или более не будут освобождены.</span><span class="sxs-lookup"><span data-stu-id="9c754-194">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="9c754-195">Значение по умолчанию: 20.</span><span class="sxs-lookup"><span data-stu-id="9c754-195">The default value is set to 20.</span></span>