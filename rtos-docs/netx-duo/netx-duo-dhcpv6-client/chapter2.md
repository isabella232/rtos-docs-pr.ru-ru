---
title: Глава 2. Установка и использование клиента NetX Duo DHCPv6 для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиента NetX Duo DHCPv6 для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 481e29cc674edfa7e437e8e14253172b89aeae6856114192f4ca5b35717c91e0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791539"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcpv6-client"></a>Глава 2. Установка и использование клиента NetX Duo DHCPv6 для ОСРВ Azure

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиента NetX Duo DHCPv6 для ОСРВ Azure.

## <a name="product-distribution"></a>Распространение продукта

Клиент NetX Duo DHCPv6 доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). Этот пакет включает в себя два исходных файла и PDF-файл с этим документом.

- **nxd_dhcpv6_client.h** — файл заголовка для клиента NetX Duo DHCPv6

- **nxd_dhcpv6_client.c** — файл с исходным кодом для клиента NetX Duo DHCPv6

- **demo_netxduo_dhcpv6_client.c** — пример программы, демонстрирующей установку клиента NetX Duo DHCPv6

- **nxd_dhcpv6_client.pdf** — описание клиента NetX Duo DHCPv6 в формате PDF

## <a name="netx-duo-dhcpv6-client-installation"></a>Установка клиента NetX Duo DHCPv6

Чтобы использовать интерфейс API клиента NetX Duo DHCPv6, весь дистрибутив, упомянутый выше, можно скопировать в каталог, где установлен NetX Duo . Например, если NetX Duo установлен в каталоге *\threadx\arm7\green*, файлы *nxd_dhcpv6_client.h* и *nxd_dhpcv6_client.c* можно скопировать в этот каталог.

## <a name="using-the-netx-duo-dhcpv6-client"></a>Использование клиента NetX Duo DHCPv6

В код приложения необходимо включить файл *nxd_dhcpv6_client.h* после файлов *tx_api.h* и *nx_api.h* для использования клиента DHCPv6 и служб ThreadX и NetX Duo соответственно. Файл *nxd_dhcpv6_client.c* должен быть скомпилирован в проекте так же, как и другие файлы приложения, а его объектная форма должна быть связана с файлами приложения.

### <a name="span-classunderlineclient-dhcp-unique-identifier-duidspan"></a><span class="underline">Уникальный идентификатор DHCP клиента (DUID)</span>

DUID клиента уникально определяет каждый клиент в сети. Приложение должно создать DUID клиента перед запросом IPv6-адреса с сервера. DUID клиента автоматически включается во все сообщения серверу. Чтобы создать DUID, приложение вызывает службу *nx_dhcpv6_create_client_duid.*
```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT duid_type, 
                                  UINT hardware_type, ULONG time);
```

Приложение вызывает эту службу и указывает тип DUID (только канальный уровень или канальный уровень и время). Для идентификаторов DUID канального уровня и времени эта служба предоставляет поле времени, если входное значение времени не указано.

Если устройство перезагружается и ему необходимо использовать ранее назначенную аренду IPv6-адреса, приложение должно создать тот же DUID клиента, который использовался при назначении IPv6-адреса. Адрес канального уровня — это все, что необходимо для создания DUID клиента канального уровня. Если устройство имеет доступ к адресу канального уровня, ранее выделенная энергонезависимая память не требуется. Для идентификаторов DUID уровня времени приложение должно иметь доступ к тем же данным времени, которые использовались при создании предыдущего идентификатора DUID. Энергонезависимая память не требуется. Если у клиентов нет устойчивого хранилища, они не должны использовать идентификаторы DUID уровня времени.

### <a name="span-classunderlineclient-identity-association-for-non-temporary-addresses-ianaspan"></a><span class="underline">Сопоставление удостоверения клиента для постоянных адресов (IANA)</span>

Приложение должно создать IANA и при необходимости один адрес сопоставления удостоверений (IA) или несколько, прежде чем запрашивать IPv6-адрес. Для этого приложение вызывает службу *nx_dhcpv6_create_client_iana*. Чтобы создать адрес IA, приложение вызывает службу *nx_dhcpv6_add_client_ia* с запрошенным IPv6-адресом и значениями времени существования в качестве указания для сервера.

Адреса IANA и IA в совокупности определяют параметры назначения IPv6-адресов клиентам.

Перед запуском клиента DHCPv6 клиентское приложение DHCPv6 создает IANA с помощью службы *nx_dhcpv6_create_client_iana*.

```C
UINT    nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                     UINT IA_ident, ULONG T1, ULONG T2);
```

Кроме того, перед запуском клиента DHCPv6 оно также должно создать один IA или несколько с помощью службы *nx_dhcpv6_create_client_ia* и запрошенных IPv6-адресов.

```C
UINT    nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                                NXD_ADDRESS *ipv6_address, 
                                ULONG preferred_lifetime, 
                                ULONG valid_lifetime);
```

> [!NOTE]
> Число адресов IA, создаваемых приложением, не может превышать значение параметра NX_DHCPV6_MAX_IA_ADDRESS (значение по умолчанию — 1).

Клиент NetX Duo DHCPv6 поддерживает *nx_dhcpv6_create_client_ia* для клиентских приложений DHCPv6 прежних версий. Эта служба идентична службе *nx_dhcpv6_add_client_ia*, но разработчикам рекомендуется использовать службу *nx_dhcpv6_add_client_ia*.

Эти службы демонстрируются в разделе "Небольшой пример системы" далее в этой главе.

### <a name="span-classunderlinenon-volatile-memory-considerations-to-reuse-ianas-and-iasspan"></a><span class="underline">Рекомендации в отношении энергонезависимой памяти при повторном использовании IANA и IA</span>

Приложение должно сохранять параметры IANA T1 и T2, а также идентификатор IANA в энергонезависимой памяти, если те же адреса должны использоваться после перезагрузки. Приложение также должно сохранять IA, включая IPv6-адрес, в энергонезависимой памяти.

При завершении работы приложение должно сохранять время, в течение которого оно было привязано к назначенным арендам IPv6-адресов, в энергонезависимой памяти. Для этого оно вызывает службу *nx_dhcpv6_get_time_accrued* перед остановкой клиента DHCPv6.

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, 
                                ULONG *time_accrued);
```

Если у приложения имеются отдельные часы для отслеживания интервала времени, прошедшего с остановки до перезапуска клиента DHCPv6 после перезагрузки, к этому времени добавляется время, в течение которого продлилась аренда IPv6-адреса до остановки. В этом случае задача клиентского потока запускается с общим временем привязки к аренде IPv6-адреса в качестве входного значения nv_time.

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr, ULONG nv_time);
```

С этого момента задача клиентского потока DHCPv6 будет отслеживать время аренды IPv6-адреса, чтобы знать, когда необходимо продлить ее.

### <a name="span-classunderlinesetting-dhcpv6-option-dataspan"></a><span class="underline">Задание значений параметров DHCPv6</span>

Перед запросом аренды IPv6-адреса приложение может запросить значения других сетевых параметров, таких как DNS-сервер и сервер времени. Для некоторых из этих параметров есть специальные службы. Ниже показаны некоторые из них.

```C
UINT  nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT enable)

UINT  nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr, 
                                           UINT enable);
```

### <a name="span-classunderlineinitiating-the-ipv6-address-requestspan"></a><span class="underline">Инициация запроса IPv6-адреса</span>

Приложение запускает поток клиента DHCPv6, вызывая службу *nx_dhcpv6_start* с нулевым входным значением времени. Чтобы протокол DHCPv6 мог запросить IPv6-адрес, приложение вызывает службу *nx_dhcpv6_request_solicit*.

Если приложению нужно использовать назначенную ранее аренду IPv6-адреса, оно вызывает *nx_dhcpv6_start* с ненулевым входным значением времени. Вызывать *nx_dhcpv6_request_solicit* не следует.

После этого приложению делать ничего больше не нужно. Клиент DHCPv6 будет автоматически следить за тем, когда пора продлить или повторно привязать IPv6-адрес.

## <a name="small-example-system"></a>Пример небольшой системы

Приведенный ниже пример демонстрирует, как просто пользоваться клиентом NetX Duo DHCPv6. В нем применяется клиент DHCPv6 и виртуальный драйвер ОЗУ. Предполагается, что у устройства всего один физический сетевой интерфейс.

Функция *tx_application_define* создает пул пакетов для клиента DHCPv6 с целью отправки сообщений DHCPv6. Она также создает поток приложения и экземпляр IP-адреса. Затем она включает протоколы UDP и ICMP для IP-адреса в строках 130–148. Далее создается клиент DHCPv6 с помощью функций обратного вызова для уведомления об изменении состояния (*dhcpv6_state_change_notify*) и обработки ошибки сервера (*dhcpv6_server_error_handler*) в строке 151.

В функции входа в клиентский поток (*thread_client_entry*) IP-адрес клиента настраивается с использованием локального адреса канала и для него включаются службы IPv6 и ICMPv6 в строках 202–217. Перед запуском клиента DHCPv6 приложение создает идентификатор DUID клиента, параметр IANA и параметр адреса IA в строках 219–303. Параметр адреса IA необязателен, если клиент будет запрашивать IPv6-адрес, а также допустимое и предпочтительное время существования с сервера. Сервер может предоставить либо не предоставлять запрошенный IPv6-адрес или время аренды. Приложение может добавить дополнительные параметры IA (до NX_DHCPV6_MAX_IA_ADDRESS) для назначения нескольких глобальных адресов.

Наконец, приложение задает различные параметры для запроса сетевых параметров в сообщениях серверу DHCPv6. Задача клиента DHCPv6 запускается путем вызова *nx_dhcpv6_start* в строке 306, а сам протокол DHCPv6 запускается в состоянии SOLICIT путем вызова *nx_dhcpv6_request_solicit* в строке 317. Затем клиент DHCPv6 автоматически обрабатывает изменение состояния клиента в рамках протокола DHCPv6, пока он не будет привязан к адресу или не возникает ошибка. В течение этого времени приложение ожидает завершения работы протокола, а также завершения обнаружения повторяющихся адресов (DAD), если оно настроено для экземпляра IP-адреса (конфигурация по умолчанию).

После вызова tx_thread_sleep приложение проверяет глобальные параметры, заданные в обратном вызове изменения состояния, чтобы определить успешность назначения аренды IPv6-задаче клиента DHCPv6, а также, если аренда назначена, успешность проверки уникальности DAD. Это делается с помощью счетчиков, настроенных в функциях обратного вызова для уведомления об изменении состояния и обработки ошибки сервера. Приложение проверяет наличие ненулевых значений у счетчиков address_not_assigned, address_expired и server_errors, чтобы определить, завершилось ли назначение адреса сбоем. Если значение bound_addresses не равно нулю (по крайней мере один адрес успешно назначен), проверяется наличие ненулевого значения у счетчика address_failed_dad с целью определить, была ли проверка DAD неудачной. Ниже приводятся пояснения к обратным вызовам изменения состояния и ошибки сервера.

Обратный вызов изменения состояния *dhcpv6_state_change_notify* проверяет предыдущее и текущее состояния клиента DHCPv6, чтобы определить, получал ли клиент допустимые ответы от сервера.

  - *dhcpv6_state_change_notify* проверяет наличие переходов из состояния SOLICIT непосредственно в состояние INIT. Если они есть, для клиента DHCPv6, не получавшего ответов от сервера, значение счетчика увеличивается.

Далее *dhcpv6_state_change_notify* проверяет, был ли клиент назначен (привязан) одному IPv6-адресу или нескольким.

  - Если новое состояние — BOUND, увеличивается счетчик адресов, привязанных к клиенту.
    
*dhcpv6_state_change_notify* также проверяет наличие неудачной проверки DAD.

  - Если состояние меняется с DECLINE на INIT, значит, клиент DHCPv6 не прошел проверку DAD для одного из назначенных адресов и счетчик неудачных назначений адресов увеличивается.
    
Последняя проверка, выполняемая обратным вызовом *dhcpv6_state_change_notify* в этом примере, служит для определения успешно назначенного адреса, который прошел проверку DAD, но при продлении или повторной привязке произошел сбой.

  - Если состояние меняется с REBIND на INIT, клиент не получил ответа на запросы RENEW или REBIND и *dhcpv6_state_change_notify* увеличивает число адресов с истекшим сроком действия.

Если *dhcpv6_server_error_handler* получает уведомление от задачи клиента DHCPv6 о состоянии ошибки, полученном с сервера, счетчик ошибок сервера увеличивается.

Если все работает правильно, приложение запрашивает у клиента DHCPv6 данные адреса, включая время аренды. Оно получает число допустимых (успешно назначенных) адресов путем вызова службы *nx_dhcpv6_get_valid_ip_address_count*, а время продления в IANA (относится ко всем назначенным адресам IA) — путем вызова *nx_dhcpv6_get_iana_lease_time* в строках 372–392. Затем оно запрашивает у клиента DHCPv6 каждый из его параметров IA для IPv6-адреса и времени аренды по индексу адреса.

Некоторые службы клиента DHCPv6 (*nx_dhcpv6_get_lease_time_data, nx_dhcpv6_get_IP_address*) не требуют индекса адреса в качестве входных данных и возвращают параметры DHCPv6 для основного глобального адреса клиента. Это подходит для клиентов с одним глобальным IPv6-адресом при вызове *nx_dhcpv6_get_valid_ip_address_lease_time* в строке 384.

Конфигурация клиента DHCPv6 NX_DHCPV6_CLIENT_RESTORE_STATE позволяет системе восстанавливать ранее созданный клиент DHCPv6 в состоянии привязки между перезагрузками системы. В строке 434 вызывается *nx_dhcpv6_client_get_record* для получения записи клиента DHCPv6 между перезагрузками системы, а в строке 525 вызывается *nx_dhcpv6_client_restore_record* для сохранения этой записи после включения питания системы.

Затем приложение освобождает назначенные адреса с помощью службы *nx_dhcpv6_request_release* в строке 552. Для перезапуска приложение останавливает клиент DHCPv6 с помощью службы *nx_dhcpv6_client_stop* в строке 567 и очищает все IPv6-адреса, зарегистрированные в экземпляре IP и настроенные посредством клиента DHCPv6. Для этого вызывается *nx_dhcpv6_reinitialize* в строке 578. После этого задача клиента DHCPv6 перезапускается с помощью служб *nx_dhcpv6_start* и *nx_dhcpv6_request_solicit*, как и ранее.

Клиент DHCPv6 удаляется путем вызова *nx_dhcpv6_delete* в строке 626. Обратите внимание, что при этом не удаляется *пул пакетов*, созданный для клиента DHCPv6, так как этот пул также используется экземпляром IP. Если пул пакетов больше не нужен, его следует удалить с помощью службы NetX Duo *nx_packet_pool_delete*.

```C
/* This is a small demo of the NetX Duo DHCPv6 Client for the high-performance NetX Duo stack. */

#include    <stdio.h>
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcpv6_client.h"

#ifdef FEATURE_NX_IPV6
#define     DEMO_STACK_SIZE         2048

/* Set the client address, and request these address from DHCPv6 Server. */
/*
#define     NX_DHCPV6_REQUEST_IA_ADDRESS
*/

/* Set the list of DHCPv6 option data (timezone, DNS server, timer server, domain name)to get from the DHCPv6 server. */

#define     NX_DHCPV6_REQUEST_OPTION


/* Add the fully qualified domain name to request whether the DHCPv6 server SHOULD or SHOULD NOT perform the AAAA RR or DNS updates. */

#define     NX_DHCPV6_REQUEST_FQDN_OPTION


/* Define the ThreadX and NetX object control blocks... */

NX_PACKET_POOL          pool_0;
TX_THREAD               thread_client;
NX_IP                   client_ip;

/* Define the Client and Server instances. */

NX_DHCPV6               dhcp_client;

/* Define the error counter used in the demo application... */
ULONG                   error_counter;
CHAR                    *pointer;

/* Define thread prototypes. */
void    thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Declare DHCPv6 Client callbacks */
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state);
VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type);

/* Set up globals for tracking changes to DHCPv6 Client from callback services. */
UINT state_changes = 0;
UINT address_expired = 0;
UINT address_failed_dad = 0;
UINT bound_addresses = 0;
UINT address_not_assigned = 0;
UINT server_errors = 0;

/* Define some DHCPv6 parameters. */

#define DHCPV6_IANA_ID      0xC0DEDBAD
#define DHCPV6_T1           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_T2           NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_RENEW_TIME   NX_DHCPV6_INFINITE_LEASE
#define DHCPV6_REBIND_TIME  NX_DHCPV6_INFINITE_LEASE
#define PACKET_PAYLOAD      500
#define PACKET_POOL_SIZE    (5*PACKET_PAYLOAD)

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

UINT    status;

    /* Setup the working pointer. */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the Client thread. */
    status = tx_thread_create(&thread_client, "Client thread", thread_client_entry, 0,
                              pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1024,  pointer, PACKET_POOL_SIZE);

    pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create a Client IP instance. */
    status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                          0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                          pointer, 2048, 1);

    pointer =  pointer + 2048;

    /* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable UDP traffic for sending DHCPv6 messages. */
    status =  nx_udp_enable(&client_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Enable ICMP. */
    status =  nx_icmp_enable(&client_ip);

    /* Check for ICMP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 Client. */
    status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                      &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                      dhcpv6_server_error_handler);

    /* Check for errors. */
    if (status)
    {
        error_counter++;
        return;
    }

    /* Update the stack pointer because we need it again. */
    pointer = pointer + 2048;

    /* Yield control to DHCPv6 threads and ThreadX. */
    return;
}


/* Define the Client host application thread. */

void    thread_client_entry(ULONG thread_input)
{

UINT        status;
ULONG       T1, T2;
UINT        address_count;
UINT        address_index = 0;
NXD_ADDRESS valid_ipv6_address;
ULONG       preferred_lifetime;
ULONG       valid_lifetime;
UINT        ia_count = 1;

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
NXD_ADDRESS ipv6_address;
#endif

#ifdef NX_DHCPV6_REQUEST_OPTION
UCHAR       buffer[200];
NXD_ADDRESS dns_server;
#endif

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE
ULONG       current_time;
ULONG       elapsed_time;
NX_DHCPV6_CLIENT_RECORD dhcpv6_client_record;
#endif


    state_changes = 0;

    /* Establish the link local address for the host. The RAM driver creates
       a virtual MAC address of 0x1122334456. */
    status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

    if (status)
    {
        error_counter++;
        return;
    }

    /* Let NetX Duo get initialized. */
    tx_thread_sleep(50);

    /* Enable the Client IP for IPv6 and ICMPv6 services. */
    nxd_ipv6_enable(&client_ip);
    nxd_icmp_enable(&client_ip);

    /* Create a Link Layer Plus Time DUID for the DHCPv6 Client. Set time ID field
       to NULL; the DHCPv6 Client API will supply one. */
    status = nx_dhcpv6_create_client_duid(&dhcp_client, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                          NX_DHCPV6_HW_TYPE_IEEE_802, 0);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* Create the DHCPv6 client's Identity Association (IA-NA) now.

       Note that if this host had already been assigned in IPv6 lease, it
       would have to use the assigned T1 and T2 values in loading the DHCPv6
       client with an IANA block.
    */
    status = nx_dhcpv6_create_client_iana(&dhcp_client, DHCPV6_IANA_ID, DHCPV6_T1,  DHCPV6_T2);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

#ifdef NX_DHCPV6_REQUEST_IA_ADDRESS
    memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
    ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
    ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
    ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
    ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
    ipv6_address.nxd_ip_address.v6[3] = 0x0000abcd;

    /* Create an IA address option.
        Note that if this host had already been assigned in IPv6 lease, it
        would have to use the assigned IPv6 address, preferred and valid lifetime
        values in loading the DHCPv6 Client with an IA block.
    */
    status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address,DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

    if (status != NX_SUCCESS)
    {
        error_counter++;
        return;
    }

    /* If the DHCPv6 Client is configured for a maximum number of IA addresses
       greater than 1, we can add another IA address if the device requires
       multiple global IPv6 addresses. */
    if(NX_DHCPV6_MAX_IA_ADDRESS >= 2)
    {
        memset(&ipv6_address,0x0, sizeof(NXD_ADDRESS));
        ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
        ipv6_address.nxd_ip_address.v6[0] = 0x3ffe0501;
        ipv6_address.nxd_ip_address.v6[1] = 0xffff0100;
        ipv6_address.nxd_ip_address.v6[2] = 0x00000000;
        ipv6_address.nxd_ip_address.v6[3] = 0x00001234;

        /* Add another  IA address option. */
        status = nx_dhcpv6_add_client_ia(&dhcp_client, &ipv6_address, DHCPV6_RENEW_TIME, DHCPV6_REBIND_TIME);

        if (status != NX_SUCCESS)
        {
            error_counter++;
            return;
        }
    }
#endif /* NX_DHCPV6_REQUEST_IA_ADDRESS  */

#ifdef NX_DHCPV6_REQUEST_OPTION
    /* Set the list of DHCPv6 option data to get from the DHCPv6 server if needed. */
    nx_dhcpv6_request_option_timezone(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_DNS_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_time_server(&dhcp_client, NX_TRUE);
    nx_dhcpv6_request_option_domain_name(&dhcp_client, NX_TRUE);
#endif /* NX_DHCPV6_REQUEST_OPTION */


#ifdef NX_DHCPV6_REQUEST_FQDN_OPTION
    /* Set the DHCPv6 Client FQDN option.
       operation: NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR         DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client.
                  NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE   DHCPv6 Client choose to updating the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the client to the server.
                  NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE   DHCPv6 Client choose to request that the server perform no DNS updatest on its behalf. */
    nx_dhcpv6_request_option_FQDN(&dhcp_client, "DHCPv6-Client", NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR);
#endif /* NX_DHCPV6_REQUEST_FQDN_OPTION */

    /* Start up the NetX DHCPv6 Client thread task. */
    status =  nx_dhcpv6_start(&dhcp_client);

    /* Check for errors. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start the DHCPv6 by sending a Solicit message out on the network. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Is the DHCPv6 Client request for address assignment successfully started? */
    if (status == NX_SUCCESS)
    {

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Check the bound address. */
        if (bound_addresses != ia_count)
        {

            /* Attempt to find out why DHCPv6 failed, where...*/

            if (server_errors > 0)
            {
                /* Actually you would compare server_error count with number of IA's added
                   to determine if any addresses were assigned. */
                printf("Server error, not all address assigned\n");
            }

            if (address_not_assigned > 0)
            {
                /* Actually you would compare address not assigned count with number of IA's added
                   to determine if any addresses were assigned. */

                printf("No servers responded to some or all of our IAs\n");
            }

        }

        /* Regardless if the DHCPv6 Client achieved a bound state, check for DAD
           failures. */
        if (address_failed_dad > 0)
        {
            /* Actually you would compare failed dad count with number of IA's added
               to determine if any addresses were assigned. */

            printf("Some or all of our IAs failed DAD\n");

        }

        /* Successfully assigned IPv6 addresses! */

        /* Get the count of valid IPv6 address obtained by DHCPv6. */
        status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_client, &address_count);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IPv6 address and related lifetimes by address index. This index is the
           index into the DHCPv6 Client address table. Not to be confused with the IP
           instance address table! */
        status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_client, address_index,
                                                           &valid_ipv6_address, 
                                                               &preferred_lifetime,
                                                           &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IANA options for when to start renew/rebind requests. These time
           parameters are the same for all IPv6 addresses assigned in the Client
           e.g. IANA returned from Server. */
        status = nx_dhcpv6_get_iana_lease_time(&dhcp_client, &T1, &T2);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /*****************************************************************************/
        /* These are 'legacy' DHCPv6 services and are for the most part identical to the services
           above except they default to the primary global IPv6 address regardless if the
           Client was assigned more than one global IPv6 address. */

        /* Now check the assigned lease times. */
        status = nx_dhcpv6_get_lease_time_data(&dhcp_client, &T1, &T2,
                                               &preferred_lifetime, &valid_lifetime);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Get the IP address. */
        status = nx_dhcpv6_get_IP_address(&dhcp_client, &valid_ipv6_address);

        /* Check status. */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }

        /* Bound state. */

#ifdef NX_DHCPV6_CLIENT_RESTORE_STATE

        /* Get the DHCPv6 Client record. */
        nx_dhcpv6_client_get_record(&dhcp_client, &dhcpv6_client_record);

        /* Delete DHCPv6 instance. */
        nx_dhcpv6_client_delete(&dhcp_client);

        /* Delete IP instance. */
        status = nx_ip_delete(&client_ip);

        /* Check for error. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Create a Client IP instance. */
        status = nx_ip_create(&client_ip, "Client IP", IP_ADDRESS(0, 0, 0, 0),
                              0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                              pointer, 2048, 1);

        pointer =  pointer + 2048;

        /* Check for IP create errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable UDP traffic for sending DHCPv6 messages. */
        status =  nx_udp_enable(&client_ip);

        /* Check for UDP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable ICMP. */
        status =  nx_icmp_enable(&client_ip);

        /* Check for ICMP enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Enable the Client IP for IPv6 and ICMPv6 services. */
        status = nxd_ipv6_enable(&client_ip);
        status += nxd_icmp_enable(&client_ip);

        /* Check for IPv6 and ICMPv6 enable errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Establish the link local address for the host. The RAM driver creates
           a virtual MAC address of 0x1122334456. */
        status = nxd_ipv6_address_set(&client_ip, 0, NX_NULL, 10, NULL);

        if (status)
        {
            error_counter++;
            return;
        }

        /* If Duplicate Address Detection (DAD) is enabled in NetX Duo, e.g. #NXDUO_DISABLE_DAD
           not defined, allow time for NetX Duo to verify the address is unique on our network.
         */
        tx_thread_sleep(500);

        /* Create the DHCPv6 Client. */
        status =  nx_dhcpv6_client_create(&dhcp_client, &client_ip, "DHCPv6 Client",
                                          &pool_0, pointer, 2048, dhcpv6_state_change_notify,
                                          dhcpv6_server_error_handler);

        /* Check for errors. */
        if (status)
        {
            error_counter++;
            return;
        }

        /* Update the stack pointer because we need it again. */
        pointer = pointer + 2048;

        /* Restore the DHCPv6 record. */
        nx_dhcpv6_client_restore_record(&dhcp_client, &dhcpv6_client_record, 5);

        /* Resume the DHCPv6 service. */
        nx_dhcpv6_resume(&dhcp_client);
#endif


#ifdef NX_DHCPV6_REQUEST_OPTION

        /* Get the DNS Server address. */
        nx_dhcpv6_get_DNS_server_address(&dhcp_client, 0, &dns_server);

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_DOMAIN_NAME_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server

        /* Get the domain name. */
        memset(buffer, 0, sizeof(buffer));

        /* Get the time zone. */
        nx_dhcpv6_get_other_option_data(&dhcp_client, NX_DHCPV6_NEW_POSIX_TIMEZONE_OPTION, buffer, 200); // Try to get DNS info got from DHCPv6 Server
#endif

        /* At some point, we may wish to release the IPv6 address lease e.g. the device
           is leaving the network or powering down. In that case we inform the
           DHCPv6 Server that we are releasing the address lease. */
        status = nx_dhcpv6_request_release(&dhcp_client);

        /* Check status. */
        if (status != NX_SUCCESS)
        {

            error_counter++;
            return;
        }

        /* Send the release message. */
        tx_thread_sleep(100);
    }

    /* Stopping the Client task. */
    status = nx_dhcpv6_stop(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Clear the previously assigned IPv6 addresses from the Client and IP address table. */
    status = nx_dhcpv6_reinitialize(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Start up the Client task again. */
    status = nx_dhcpv6_start(&dhcp_client);

    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Begin the request process by sending a Solicit message with the IA created above
       with our preferred IPv6 address. */
    status = nx_dhcpv6_request_solicit(&dhcp_client);
    /* Check status. */
    if (status != NX_SUCCESS)
    {

        error_counter++;
        return;
    }

    /* Wait a bit before releasing the IP address and terminating the client. */
    tx_thread_sleep(500);

    /* Ok, lets stop the application. Again we DO NOT plan
       to keep the IPv6 address we were assigned and need to release it
       back to the DHCPv6 server. */
    status = nx_dhcpv6_request_release(&dhcp_client);

    /* Check for error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    /* Now delete the DHCPv6 client and release ThreadX and
       NetX Duo resources back to the system. */
    nx_dhcpv6_client_delete(&dhcp_client);


    return;

}


/* This is the notification from the DHCPv6 Client task that it has changed
   state in the DHCPv6 protocol, for example getting assigned an IPv6 lease and
   achieving the bound state or an IPv6 lease expires and being reset to
   the init state.
*/
VOID dhcpv6_state_change_notify(NX_DHCPV6 *dhcpv6_ptr, UINT old_state, UINT new_state)
{


    /* Increment state change counter. */
    state_changes++;

    /* Check if the Client attempted to request an IPv6 lease but no servers
       responded. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_SOLICIT) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that either DAD failed or IP lease expired. */
        address_not_assigned++;
    }

    /* Check if the Client has been assigned an IPv6 lease. */
    if (new_state == NX_DHCPV6_STATE_BOUND_TO_ADDRESS)
    {
        bound_addresses++;
    }

   /* Check if the Client was bound, but failed the uniqueness check
       (Duplicate Address Detection) and was reset to the INIT state. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_DECLINE) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that DAD failed on Client IA. */
        address_failed_dad++;
    }

    /* Check if the Client was bound, attempted renew the lease but the
       IPv6 address renewal/rebinding failed. */
    if ((old_state == NX_DHCPV6_STATE_SENDING_REBIND) && (new_state == NX_DHCPV6_STATE_INIT))
    {

        /* Indication that the IP lease expired. */
        address_expired++;
    }



    /* Other checks are possible. */

}

/* This is the notification from the DHCPv6 Client task that it received an error
   from the server (status code) in response to the Client's last DHCPv6 message.
*/

VOID dhcpv6_server_error_handler(NX_DHCPV6 *dhcpv6_ptr, UINT op_code, UINT status_code, UINT message_type)
{

    /* Increment the server error count. */
    server_errors++;

    /* This should distinguish between receiving a server error and no server
       available to assign the Client an IPv6 address if the Client fails
       to get assigned an address. */
}

#endif /* FEATURE_NX_IPV6 */
```
