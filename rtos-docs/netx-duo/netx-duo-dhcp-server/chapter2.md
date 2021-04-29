---
title: Глава 2. Установка и использование DHCP-сервера NetX Duo для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента DHCP NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 201e8b7e245539c1780ace4c3af4bc063a8485b3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814795"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-dhcp-server"></a>Глава 2. Установка и использование DHCP-сервера NetX Duo для ОСРВ Azure

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента DHCP NetX Duo.

## <a name="product-distribution"></a>Распространение продукта

DHCP-сервер NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). Этот пакет включает в себя два исходных файла и PDF-файл с этим документом.

- **nxd_dhcp_server.h** — файл заголовка для DHCP-сервера NetX Duo.
- **nxd_dhcp_server.c** — файл с исходным кодом для DHCP-сервера NetX Duo.
- **nxd_dhcp_server.pdf** — руководство пользователя DHCP-сервера NetX Duo.
- **demo_netxduo_dhcp.c** — демонстрация DHCP-сервера NetX Duo.

## <a name="dhcp-installation"></a>Установка DHCP

Чтобы использовать DHCP-сервер NetX Duo, весь дистрибутив, упомянутый ранее, необходимо скопировать на уровень каталога, где установлен NetX Duo. Например, если NetX Duo установлен в каталоге *\threadx\arm7\green*, файлы *nxd_dhcp_server.h* и *nxd_dhpc_server.c* следует скопировать в этот каталог.

## <a name="using-netx-duo-dhcp-server"></a>Использование DHCP-сервера NetX Duo

DHCP-сервер NetX Duo прост в использовании. В код приложения достаточно добавить файл *nx_dhcp_server.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX Duo соответственно. После добавления файла *nxd_dhcp_server.h* код приложения может выполнять вызовы функций DHCP, указанные далее в этом руководстве. В приложение также следует включить файл *nxd_dhcp_server.c* в процессе сборки. Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его объектная форма должна быть связана с файлами приложения. Дополнительные сведения об использовании DHCP-сервера NetX Duo см. в следующих разделах: **Требования для использования DHCP-сервера NetX** **Duo** и **Ограничения DHCP-сервера NetX Duo**.

Обратите внимание, что, поскольку протокол DHCP использует службы UDP NetX Duo, перед использованием DHCP следует включить протокол UDP с помощью вызова *nx_udp_enable*.

## <a name="requirements-of-the-netx-duo-dhcp-server"></a>Требования для использования DHCP-сервера NetX Duo

Для DHCP-сервера NetX Duo требуется порт сокета UDP, назначенный известному DHCP-порту 67. Для создания DHCP-сервера приложение должно создать пул пакетов с полезной нагрузкой пакета не менее 548 байт плюс заголовки IP, UDP и Ethernet (всего 44 байт с выравниванием по 4 байт).

Предполагается, что и сервер, и клиент используют аппаратные параметры адреса Ethernet

- Аппаратный тип: 1
- Аппаратная длина: 6
- Число переходов: 0

### <a name="multiple-client-sessions"></a>Несколько клиентских сеансов

DHCP-сервер NetX Duo может обрабатывать несколько клиентских сеансов, ведя таблицу активных клиентов DHCP и их состояний, например состояний DHCP INIT, BOOT, SELECTING, REQUESTING, RENEWING и т. д. Если время ожидания сеанса истекает до получения следующего сообщения от клиента, не привязанного к аренде IP-адреса, сервер очищает данные клиентского сеанса и возвращает назначенный IP-адрес в пул. Если сервер получает несколько сообщений DISCOVER от одного клиента, он сбрасывает время ожидания сеанса и оставляет IP-адрес зарезервированным для клиента, чтобы его можно было принять в последующем сообщении REQUEST.

DHCP-сервер NetX Duo также принимает запрос DHCP от клиента в одном состоянии, например клиент отправляет только сообщение REQUEST. При этом предполагается, что клиенту ранее была назначена аренда IP-адреса DHCP-сервером.

### <a name="setting-interface-specific-network-parameters-server-responses"></a>Задание ответов сервера для параметров сети, относящихся к конкретному интерфейсу

Приложение может задать параметры маршрутизатора, маски подсети и DNS-сервера для каждого интерфейса, обрабатывающего запросы клиентов DHCP, с помощью службы *nx_dhcp_set_interface_network_parameters*. В противном случае по умолчанию применяются IP-шлюз из основного интерфейса сервера, его подсеть сети DHCP и IP-адрес DHCP-сервера соответственно.

DHCP-сервер включает эти параметры в данные сообщений DHCP, которые он отправляет клиентам DHCP.

### <a name="assigning-ip-addresses-to-the-client"></a>Назначение IP-адресов клиенту

Если в сообщении DISCOVER клиента не указан запрашиваемый IP-адрес, DHCP-сервер может использовать адрес из собственного пула. Если у сервера нет доступных IP-адресов, он отправит клиенту сообщение NACK.

DHCP-сервер NetX Duo предоставит IP-адрес, запрошенный в сообщении REQUEST клиента, если этот адрес доступен и найден в базе данных IP-адресов сервера. Приложение создает список доступных IP-адресов сервера для назначения клиентам DHCP с помощью службы *nx_dhcp_create_server_ip_address_list*. Если у сервера нет запрошенного IP-адреса или он назначен другому узлу, клиенту отправляется сообщение NACK.

Когда DHCP-сервер получает запрос клиента, он однозначно идентифицирует клиент по его MAC-адресу в соответствующем поле в сообщении DHCP. Если MAC-адрес клиента меняется или клиент переносится в другую подсеть, он должен отправить на сервер сообщение RELEASE, чтобы вернуть IP-адрес в пул доступных адресов и запросить новый IP-адрес в состоянии INIT.

Дополнительные сведения см. на рис. 1.1 в разделе **Небольшой пример системы**. Количество IP-адресов, сохраняемых в экземпляре DHCP-сервера, ограничено размером массива адресов сервера в управляющем блоке DHCP-сервера и определяется настраиваемым параметром NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.

### <a name="ip-address-lease-times"></a>Сроки аренды IP-адресов

DHCP-сервер также принимает срок аренды в запросе клиента, если этот срок меньше срока аренды по умолчанию для сервера, определенного в настраиваемом параметре NX_DHCP_DEFAULT_LEASE_TIME. Сроки продления и повторной привязки, назначенные клиенту, составляют 50 % и 85 % от срока аренды соответственно, если только аренда не бессрочная (0xFFFFFFFF). В этом случае сроки продления и повторной привязки также бесконечны.

### <a name="dhcp-server-timeouts"></a>Время ожидания DHCP-сервера

У DHCP-сервера есть настраиваемое пользователем время ожидания сеанса NX_DHCP_CLIENT_SESSION_TIMEOUT. Оно определяет то, как долго следует ожидать следующего сообщения от клиента DHCP, пока сеанс не будет завершен. Время ожидания сбрасывается, когда сервер получает следующее сообщение от клиента, независимо от того, совпадает ли это сообщение с предыдущим.

### <a name="internal-error-handling"></a>Обработка внутренних ошибок

DHCP-сервер получает и обрабатывает пакеты клиента DHCP в функции *nx_dhcp_listen_for_messages*. Эта функция прекращает обработку текущего пакета клиента DHCP, если он является недопустимым или если DHCP-сервер обнаружил внутреннюю ошибку. Функция *nx_dhcp_listen_for_messages* возвращает состояние ошибки. Поток DHCP-сервера ненадолго отдает управление планировщиком ThreadX перед вызовом этой функции для получения следующего сообщения от клиента DHCP. В текущем выпуске ведение журнала ошибок, возвращаемых функцией *nx_dhcp_listen_for_messages*, не поддерживается.

### <a name="option-55-parameter-request-list"></a>Параметр 55: список запросов параметров

На DHCP-сервере NetX Duo необходимо настроить набор параметров для загрузки в список запросов параметров (55) в сообщениях OFFER и DHCPACK, которые он передает обратно клиенту. Эти параметры должны включать в себя критически важные данные по конфигурации сети клиента. По умолчанию в их число входят IP-адрес маршрутизатора, маска подсети и DNS-сервер. Список параметров разделяется пробелами и определяется в настраиваемом пользователем параметре NX_DHCP_DEFAULT_SERVER_OPTION_LIST. Обратите внимание, что число параметров в этом списке должно быть равно значению NX_DHCP_DEFAULT_OPTION_LIST_SIZE, которое также задается пользователем.

## <a name="constraints-of-the-netx-duo-dhcp-server"></a>Ограничения DHCP-сервера NetX Duo

### <a name="dhcp-messages"></a>Сообщения DHCP

DHCP-сервер NetX Duo не проверяет, назначен ли IP-адрес где-то еще в сети, прежде чем предоставлять его клиенту. Если DHCP-серверов несколько, такая ситуация возможна. *Согласно спецификации RFC 2131, за проверку уникальности IP-адреса в сети отвечает клиент* (например, посредством проверки связи). Если IP-адрес не уникален, сервер должен получить от клиента сообщение DECLINE с этим IP-адресом и обновить свою базу данных.

DHCP-сервер NetX Duo не выдает сообщений FORCE_RENEW. Продлевать аренду IP-адреса должен сам клиент DHCP. Однако DHCP-сервер отслеживает оставшийся срок действия всех назначенных IP-адресов в своей базе данных. Когда срок аренды IP-адреса истекает, он возвращается в пул доступных IP-адресов. Поэтому клиент должен самостоятельно продлевать или повторно привязывать аренду IP-адреса.

Данные сеанса очищаются, как только клиенту предоставляется ("привязывается") аренда IP-адреса (или продлевается существующая аренда). Они также очищаются, если клиентский пакет оказывается поддельным или истекает время ожидания ответа клиентом.

### <a name="saving-data-between-reboots"></a>Сохранение данных между перезагрузками

DHCP-сервер NetX Duo сохраняет данные клиента, включая параметры DHCP-запроса, в таблице записей клиента. Она не сохраняется в энергонезависимой памяти, поэтому, если узел DHCP-сервера должен перезагрузиться, эта информация утрачивается.

DHCP-сервер NetX Duo сохраняет данные по аренде IP-адресов в таблице IP-адресов. Она не сохраняется в энергонезависимой памяти, поэтому, если узел DHCP-сервера должен перезагрузиться, эта информация утрачивается.

### <a name="relay-agents"></a>Агенты ретрансляции

В поле "Агент ретрансляции" DHCP-сервера NetX Duo содержится нулевой IP-адрес, так как DHCP-сервер не поддерживает внесетевые DHCP-запросы.

## <a name="small-example-system"></a>Пример небольшой системы

Пример того, насколько просто использовать DHCP-сервер NetX Duo, приведен на рис. 1.1 ниже. В этом примере файл DHCP *nxd_dhcp_server. h* включается в строке 5. Размер стека потока DHCP-сервера, размер стека потока IP и размер стека тестового потока определяются в строках 7–13.

Сначала создается необязательная задача тестового потока для остановки, перезапуска и окончательного удаления DHCP-сервера с помощью функции *test_thread_entry* в строке 57. Управляющий блок DHCP-сервера *dhcp_server* определяется как глобальная переменная в строке 20. Обратите внимание, что размер полезных данных пакета в пуле пакетов сервера не меньше размера стандартного сообщения DHCP (548 байт плюс байты заголовков IP и UDP). После успешного создания экземпляра IP для DHCP-сервера приложение создает DHCP-сервер в строке 96. Затем приложение включает поддержку протокола UDP для экземпляра IP сервера. Перед запуском DHCP-сервера создается список доступных IP-адресов в строке 137 с помощью службы **nx_dhcp_create_server_ip_address_list**. Параметры конфигурации сети задаются в строке 138 с помощью службы **nx_dhcp_set_interface_network_parameters**. Службы DHCP-сервера становятся доступными, когда приложение вызывает *nx_dhcp_server_start* в строке 141. Задача тестового потока демонстрирует остановку и перезапуск DHCP-сервера.

```C
/* This is a small demo of NetX Duo DHCP Server for the high-performance NetX Duo TCP/IP stack.  */

#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE         2048
#define     DEMO_SERVER_STACK_SIZE  2048
#define     SERVER_IP_ADDRESS_LIST  "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD          1000
#define     PACKET_POOL_SIZE        (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK    2048


/* Define the ThreadX and NetX Duo Duo object control blocks...  */

TX_THREAD test_thread;
NX_PACKET_POOL server_pool;
NX_IP server_ip;
NX_DHCP_SERVER dhcp_server;


/* Define the counters used in the demo application...  */

ULONG state_changes;


/* Define thread prototypes.  */

void test_thread_entry(ULONG thread_input);
void nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);


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
    UINT    status;


    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the test thread.  */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
            pointer, TEST_STACK_SIZE,  1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duosystem.  */
    nx_system_initialize();

    /* Create the DHCP Server packet pool.  */
    status =  nx_packet_pool_create(&server_pool, "NetX Main Packet Pool", PACKET_PAYLOAD,
        pointer, PACKET_POOL_SIZE);
    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error.  */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance.  */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
        0xFFFFFF00UL,  &server_pool, nx_etherDriver_mcf5485, pointer,
        R_IP_THREAD_STACK, 1);

    pointer =  pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors.  */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance.  */
    status =  nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                                     DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    status =  nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic.  */
    status =  nx_udp_enable(&server_ip);

    /* Check for UDP enable errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility.  */
    status =  nx_icmp_enable(&server_ip);

    /* Check for errors.  */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

   status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                                 START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

   status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                               NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                               IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server.  */
   status =  nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread.  */
void    test_thread_entry(ULONG thread_input)
{
    UINT status;
    UINT keep_spinning;


    /* Just let the test thread be idle till we're ready to shut things down. */
    keep_spinning = 1;
    while(keep_spinning)
    {
        tx_thread_sleep(300);
    }

    printf("Stopping the server...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(500);

    printf("Starting the server...\n");
    status = nx_dhcp_server_start(&dhcp_server);
    if (status)
    {
        printf("Error with DHPC server start. Status 0x%x\r\n", status);
        return;
    }


    tx_thread_sleep(600);

    printf("Stopping the server for good...\n");
    status = nx_dhcp_server_stop(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server stop. Status 0x%x\r\n", status);
        return;
    }

    tx_thread_sleep(200);


    printf("Deleting the server...\n");
    status = nx_dhcp_server_delete(&dhcp_server);
    if (status)
    {
        printf("Error with DHCP server delete. Status 0x%x\r\n", status);
        return;
    }
}

```

**Рис. 1.1. Пример приложения DHCP-сервера NetX Duo**

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для создания DHCP-сервера NetX Duo. Их подробное описание приводится ниже.

- **NX_DISABLE_ERROR_CHECKING** — этот параметр отключает базовую проверку ошибок DHCP. Обычно используется после отладки приложения.
- **NX_DHCP_SERVER_THREAD_PRIORITY** — этот параметр задает приоритет для потока DHCP-сервера. По умолчанию поток DHCP выполняется с приоритетом 2.
- **NX_DHCP_TYPE_OF_SERVICE** — этот параметр определяет тип службы, необходимой для UDP-запросов DHCP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.
- **NX_DHCP_FRAGMENT_OPTION** — включение фрагментации для UDP-запросов DHCP. По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментацию UDP.
- **NX_DHCP_TIME_TO_LIVE** — указывает число маршрутизаторов, через которые может пройти пакет перед отменой. Значение по умолчанию — 0x80.
- **NX_DHCP_QUEUE_DEPTH** — указывает число пакетов, которые сохраняет сокет DHCP-сервера перед освобождением очереди. Значение по умолчанию — 5.
- **NX_DHCP_PACKET_ALLOCATE_TIMEOUT** — указывает время ожидания выделения пакета из пула пакетов DHCP-сервера NetX в тактах таймера. Значение по умолчанию — NX_IP_PERIODIC_RATE.
- **NX_DHCP_SUBNET_MASK** — маска подсети, которая должна быть настроена для клиента DHCP. Значение по умолчанию — 0xFFFFFF00.
- **NX_DHCP_FAST_PERIODIC_TIME_INTERVAL** — время ожидания в тактах таймера, используемое быстрым таймером DHCP-сервера при проверке оставшегося времени сеанса и обработки истекших сеансов.
- **NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL** — время ожидания в тактах таймера, используемое медленным таймером DHCP-сервера при проверке оставшегося срока аренды IP-адреса и обработки истекшей аренды.
- **NX_DHCP_CLIENT_SESSION_TIMEOUT** — время ожидания получения DHCP-сервером следующего сообщения от клиента DHCP в тактах таймера.
- **NX_DHCP_DEFAULT_LEASE_TIME** — срок аренды IP-адреса, назначенной клиенту DHCP, в секундах. Служит основой для вычисления сроков продления и повторной привязки для клиента. Значение по умолчанию — 0xFFFFFFFF (бесконечность).
- **NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE** — размер массива DHCP-сервера для хранения доступных IP-адресов, которые можно назначить клиенту. Значение по умолчанию — 20.
- **NX_DHCP_CLIENT_RECORD_TABLE_SIZE** — размер массива DHCP-сервера для хранения записей клиентов. Значение по умолчанию — 50.
- **NX_DHCP_CLIENT_OPTIONS_MAX** — размер массива в экземпляре клиента DHCP для хранения всех запрошенных в рамках текущего сеанса параметров в списке запросов параметров. Значение по умолчанию — 12.
- **NX_DHCP_OPTIONAL_SERVER_OPTION_LIST** — буфер, который содержит список параметров DHCP-сервера по умолчанию, предоставляемых текущему клиенту DHCP в списке запросов параметров. Значение по умолчанию — "1 3 6".
- **NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE** — размер массива, в котором хранится список параметров DHCP-сервера по умолчанию. Значение по умолчанию равно 3.
- **NX_DHCP_SERVER_HOSTNAME_MAX** — размер буфера для хранения имени узла сервера. Значение по умолчанию: 32.
- **NX_DHCP_CLIENT_HOSTNAME_MAX** — размер буфера для хранения имени узла клиента в течение текущего сеанса клиента DHCP-сервера. Значение по умолчанию: 32.
