---
title: Глава 2. Установка и использование ОСРВ Azure NetX FTP
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX FTP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9da2761ed9483a920ab6f735b8a3a6bd82936c867ece8047b622788d5fb99804
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799495"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-ftp"></a>Глава 2. Установка и использование ОСРВ Azure NetX FTP

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX FTP.

## <a name="product-distribution"></a>Распространение продукта

ОСРВ Azure NetX можно получить из нашего репозитория общедоступного исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/]). Этот пакет включает в себя два файла исходного кода и PDF-файл с этим документом:

- **nx_ftp.h**: файл заголовка для FTP для NetX;
- **nxd_ftp_client.c**: файл исходного кода C для FTP-клиента для NetX;
- **nxd_ftp_server.c**: файл исходного кода C FTP-сервера NetX;
- **filex_stub.h**: файл заглушки при отсутствии FileX;
- **nx_ftp.pdf**: PDF-файл с описанием FTP для NetX.
- **demo_netx_ftp.c**: демонстрационная система FTP.

## <a name="ftp-installation"></a>Установка экземпляра FTP

Чтобы использовать FTP для NetX, следует скопировать упомянутый выше дистрибутив целиком в каталог с установленным экземпляром NetX. Например, если экземпляр NetX установлен в каталог *\threadx\arm7\green*, то файлы *nx_ftp.h*, *nx_ftp_client.c* и *nx_ftp_server.c* следует скопировать в этот каталог.

## <a name="using-ftp"></a>С помощью FTP

Использовать FTP для NetX просто. В код приложения следует добавить *nx_ftp.h* после *tx_api.h, fx_api.h* и *nx_api.h*, чтобы использовать ThreadX, FileX и NetX соответственно. После включения файла *nx_ftp.h* код приложения сможет выполнять вызовы функций FTP, описанные далее в этом руководстве. В приложение также нужно включить файлы *nx_ftp_client.c* и *nx_ftp_server.c* в процессе сборки. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX FTP.

> [!NOTE]
> Так как протокол FTP использует службы NetX TCP, нужно включить протокол TCP с помощью вызова *nx_tcp_enable*, прежде чем использовать FTP.

## <a name="small-example-system"></a>Пример небольшой системы

Пример того, насколько просто использовать NetX FTP, приведен на рисунке 1.1 ниже.

> [!NOTE]
> Это устройство узла с одним сетевым интерфейсом.

В этом примере в строках 10 и 11 указаны включаемые файлы FTP *nx_ftp_client.h* и *nx_ftp_server.h*. Затем создается FTP-сервер с помощью службы *tx_application_define* в строке 134. Блок управления FTP-сервером *server* был задан в качестве глобальной переменной в строке 31 ранее. После успешного создания FTP-сервер запускается в строке 363. Затем в строке 183 создается FTP-клиент. И, наконец, клиент записывает файл в строке 229 и считывает файл в строке 318.

```c
/* This is a small demo of NetX FTP on the high-performance NetX TCP/IP stack. This demo
relies on ThreadX, NetX, and FileX to show a simple file transfer from the client
and then back to the server. */

#include     "tx_api.h"
#include     "fx_api.h"
#include     "nx_api.h"
#include     "nx_ftp_client.h"
#include     "nx_ftp_server.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX, NetX, and FileX object control blocks... */

TX_THREAD          server_thread;
TX_THREAD          client_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_PACKET_POOL     client_pool;
NX_IP              client_ip;
FX_MEDIA           ram_disk;

/* Define the NetX FTP object control blocks. */

NX_FTP_CLIENT     ftp_client;
NX_FTP_SERVER     ftp_server;

/* Define the counters used in the demo application... */

ULONG     error_counter = 0;

/* Define the memory area for the FileX RAM disk. */

UCHAR     ram_disk_memory[32000];
UCHAR     ram_disk_sector_cache[512];

#define FTP_SERVER_ADDRESS IP_ADDRESS(1,2,3,4)
#define FTP_CLIENT_ADDRESS IP_ADDRESS(1,2,3,5)

extern UINT _fx_media_format(FX_MEDIA *media_ptr, VOID (*driver)(FX_MEDIA *media),
                    VOID *driver_info_ptr, UCHAR *memory_ptr, UINT memory_size,
                    CHAR *volume_name, UINT number_of_fats, UINT directory_entries,
                    UINT hidden_sectors, ULONG total_sectors, UINT bytes_per_sector,
                    UINT sectors_per_cluster, UINT heads, UINT sectors_per_track);

/* Define the FileX and NetX driver entry functions. */
VOID     _fx_ram_driver(FX_MEDIA *media_ptr);

/* Replace the 'ram' driver with your own Ethernet driver. */
VOID     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

void     client_thread_entry(ULONG thread_input);
void     thread_server_entry(ULONG thread_input);

/* Define server login/logout functions. These are stubs for functions that would
validate a client login request. */

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port, CHAR *name,
                CHAR *password, CHAR *extra_info);

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port, CHAR *name,
                    CHAR *password, CHAR *extra_info);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

UINT      status;
UCHAR     *pointer;

    /* Setup the working pointer. */
    pointer = (UCHAR *) first_unused_memory;

    /* Create a helper thread for the server. */
    tx_thread_create(&server_thread, "FTP Server thread", thread_server_entry,
                    0, pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize NetX. */
    nx_system_initialize();

    /* Create the packet pool for the FTP Server. */
    status = nx_packet_pool_create(&server_pool, "NetX Server Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Check for errors. */
    if (status)
        error_counter++;

    /* Create the IP instance for the FTP Server. */
    status = nx_ip_create(&server_ip, "NetX Server IP Instance",
                        FTP_SERVER_ADDRESS, 0xFFFFFF00UL, &server_pool,
                        _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Enable ARP and supply ARP cache memory for server IP instance. */
    nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP. */
    nx_tcp_enable(&server_ip);

    /* Create the FTP server. */
    status = nx_ftp_server_create(&ftp_server, "FTP Server Instance",
                    &server_ip, &ram_disk, pointer, DEMO_STACK_SIZE,
                    &server_pool, server_login, server_logout);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Now set up the FTP Client. */

    /* Create the main FTP client thread. */
    status = tx_thread_create(&client_thread, "FTP Client thread ",
                            client_thread_entry, 0,
                            pointer, DEMO_STACK_SIZE,
                            6, 6, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create a packet pool for the FTP client. */
    status = nx_packet_pool_create(&client_pool, "NetX Client Packet Pool",
                                    256, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance for the FTP client. */
    status = nx_ip_create(&client_ip, "NetX Client IP Instance", FTP_CLIENT_ADDRESS,
            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver, pointer, 2048, 1);
    pointer = pointer + 2048;

    /* Enable ARP and supply ARP cache memory for the FTP Client IP. */
    nx_arp_enable(&client_ip, (void *) pointer, 1024);

    pointer = pointer + 1024;

    /* Enable TCP for client IP instance. */
    nx_tcp_enable(&client_ip);

    return;
}

/* Define the FTP client thread. */
void     client_thread_entry(ULONG thread_input)
{

NX_PACKET     *my_packet;
UINT          status;

    /* Format the RAM disk - the memory for the RAM disk was defined above. */
    status = _fx_media_format(&ram_disk,
            _fx_ram_driver, /* Driver entry */
            ram_disk_memory, /* RAM disk memory pointer */
            ram_disk_sector_cache, /* Media buffer pointer */
            sizeof(ram_disk_sector_cache), /* Media buffer size */
            "MY_RAM_DISK", /* Volume Name */
            1, /* Number of FATs */
            32, /* Directory Entries */
            0, /* Hidden sectors */
            256, /* Total sectors */
            128, /* Sector size */
            1, /* Sectors per cluster */
            1, /* Heads */
            1); /* Sectors per track */

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Open the RAM disk. */
    status = fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                            ram_disk_sector_cache, sizeof(ram_disk_sector_cache));

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

     /* Let the IP threads and driver initialize the system. */
    tx_thread_sleep(100);

    /* Create an FTP client. */
    status = nx_ftp_client_create(&ftp_client, "FTP Client", &client_ip, 2000, &client_pool);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Created the FTP Client\n");

    /* Now connect with the NetX FTP (IPv4) server. */
    status = nx_ftp_client_connect(&ftp_client, FTP_SERVER_ADDRESS,
                                    "name", "password", 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Connected to the FTP Server\n");

    /* Open a FTP file for writing. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_WRITE, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    printf("Opened the FTP client test.txt file\n");

    /* Allocate a FTP packet. */
    status = nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Write ABCs into the packet payload! */
    memcpy(my_packet -> nx_packet_prepend_ptr, "ABCDEFGHIJKLMNOPQRSTUVWXYZ ", 28);

    /* Adjust the write pointer. */
    my_packet -> nx_packet_length = 28;
    my_packet -> nx_packet_append_ptr = my_packet -> nx_packet_prepend_ptr + 28;

    /* Write the packet to the file test.txt. */
    status = nx_ftp_client_file_write(&ftp_client, my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
        printf("Wrote to the FTP client test.txt file\n");

    /* Close the file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
        printf("Closed the FTP client test.txt file\n");

    /* Now open the same file for reading. */
    status = nx_ftp_client_file_open(&ftp_client, "test.txt", NX_FTP_OPEN_FOR_READ, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    else
        printf("Reopened the FTP client test.txt file\n");

    /* Read the file. */
    status = nx_ftp_client_file_read(&ftp_client, &my_packet, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
    else
    {
        printf("Reread the FTP client test.txt file\n");
        nx_packet_release(my_packet);
    }

    /* Close this file. */
    status = nx_ftp_client_file_close(&ftp_client, 100);

    if (status != NX_SUCCESS)
        error_counter++;

    /* Disconnect from the server. */
    status = nx_ftp_client_disconnect(&ftp_client, 100);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;

    /* Delete the FTP client. */
    status = nx_ftp_client_delete(&ftp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
        error_counter++;
}

/* Define the helper FTP server thread. */
void     thread_server_entry(ULONG thread_input)
{

UINT     status;

    /* Wait till the IP thread and driver have initialized the system. */
    tx_thread_sleep(100);

    /* OK to start the FTP Server. */
    status = nx_ftp_server_start(&ftp_server);

    if (status != NX_SUCCESS)
        error_counter++;

    printf("Server started!\n");

    /* FTP server ready to take requests! */

    /* Let the IP threads execute. */
    tx_thread_relinquish();

    return;
}

UINT     server_login(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                ULONG client_ip_address, UINT client_port,
                CHAR *name, CHAR *password, CHAR *extra_info)
{

    printf("Logged in!\n");
    /* Always return success. */
    return(NX_SUCCESS);
}

UINT     server_logout(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
                    ULONG client_ip_address, UINT client_port,
                    CHAR *name, CHAR *password, CHAR *extra_info)
{
    printf("Logged out!\n");

    /* Always return success. */
    return(NX_SUCCESS);
}
```

Рисунок 1.1. Пример FTP-клиента и FTP-сервера в NetX (узел с одним сетевым интерфейсом)

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для сборки FTP для NetX. Их подробное описание приведено ниже.  

- **NX_FTP_SERVER_PRIORITY**: приоритет потока FTP-сервера. По умолчанию указано значение 16 для задания приоритета 16.

- **NX_FTP_MAX_CLIENTS**: максимальное число клиентов, с которыми сервер может работать одновременно. Значение по умолчание — 4 (одновременно поддерживаются 4 клиента).

- **NX_FTP_SERVER_MIN_PACKET_PAYLOAD**: минимальный размер полезных данных в пуле пакетов сервера в байтах, включая заголовки TCP, IP и сетевых кадров, а также данные HTTP. Значение по умолчанию — 256 (максимальная длина имени файла в FileX) плюс 12 байт для данных о файле и NX_PHYSICAL_TRAILER.

- **NX_FTP_NO_FILEX**: если этот параметр определен, он предоставляет заглушку для зависимостей FileX. FTP-клиент будет работать без каких-либо изменений, если этот параметр определен. Чтобы FTP-сервер работал правильно, его нужно будет изменить или пользователю потребуется создать несколько служб FileX.

- **NX_FTP_CONTROL_TOS**: тип службы, необходимый для управляющих запросов TCP для FTP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов. Это определение можно задать в приложении перед включением файла *nx_ftp.h*.

- **NX_FTP_DATA_TOS**: тип службы, необходимый для выполнения запросов данных TCP для FTP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов. Это определение можно задать в приложении перед включением файла *nx_ftp.h*.

- **NX_FTP_FRAGMENT_OPTION**: позволяет включить фрагментирование для запросов TCP для FTP. По умолчанию имеет значение NX_DONT_FRAGMENT, при котором фрагментирование TCP для FTP отключено. Это определение можно задать в приложении перед включением файла *nx_ftp.h*.

- **NX_FTP_CONTROL_WINDOW_SIZE**: размер окна управляющего сокета. Значение по умолчанию — 400 байт. Это определение можно задать в приложении перед включением файла *nx_ftp.h*.

- **NX_FTP_DATA_WINDOW_SIZE**: размер окна сокета данных. Значение по умолчанию — 2048 байт. Это определение можно задать в приложении перед включением файла *nx_ftp.h*.

- **NX_FTP_TIME_TO_LIVE**: указывает число маршрутизаторов, которые может пройти этот пакет, прежде чем он будет удален. Значение по умолчанию — 0x80, но оно может быть переопределено перед включением *nx_ftp.h*.

- **NX_FTP_SERVER_TIMEOUT**: указывает число тактов ThreadX, на которое внутренние службы приостановят работу. Значение по умолчанию — 100, но оно может быть переопределено перед включением *nx_ftp.h*.

- **NX_FTP_USERNAME_SIZE**: задает допустимое число байтов в предоставляемом клиентом *имени пользователя*. Значение по умолчанию — 20, но оно может быть переопределено перед включением *nx_ftp.h*.

- **NX_FTP_PASSWORD_SIZE**: задает допустимое число байтов в предоставляемом клиентом *пароле*. Значение по умолчанию — 20, но оно может быть переопределено перед включением *nx_ftp.h*.

- **NX_FTP_ACTIVITY_TIMEOUT**: указывает число секунд, в течение которых поддерживается подключение клиента, если отсутствуют действия. Значение по умолчанию — 240, но оно может быть переопределено перед включением *nx_ftp.h*.

- **NX_FTP_TIMEOUT_PERIOD**: указывает количество секунд между проверками неактивности клиентов, выполняемыми сервером. Значение по умолчанию — 60, но оно может быть переопределено перед включением *nx_ftp.h*.
