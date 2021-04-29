---
title: Глава 2. Установка и использование ОСРВ Azure NetX Duo AutoIP
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814832"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a>Глава 2. Установка и использование ОСРВ Azure NetX Duo AutoIP

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo AutoIP.

## <a name="product-distribution"></a>Распространение продукта

ОСРВ Azure NetX AutoIP можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/). Пакет содержит три файла исходного кода, один включаемый файл и PDF-файл, содержащий этот документ:

- **nx_auto_ip.h**: файл заголовка NetX AutoIP.
- **nx_auto_ip.c**: исходный файл C для NetX AutoIP.
- **demo_netx_auto_ip.c**: демонстрационный исходный файл C для NetX AutoIP.
- **nx_auto_ip.pdf**: PDF-файл с описанием NetX AutoIP.

## <a name="autoip-installation"></a>Установка AutoIP

Чтобы использовать NetX AutoIP, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен экземпляр NetX. Например, если экземпляр NetX установлен в каталог *\threadx\arm7\green*, то файлы *nx_auto_ip.h*, *nx_auto_ip.c* и *demo_netx_auto_ip.c* необходимо скопировать в этот каталог.

## <a name="using-autoip"></a>Использование AutoIP

Использовать NetX AutoIP просто. В код приложения следует включить файл *nx_auto_ip.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX. После включения файла *nx_auto_ip.h* код приложения сможет выполнять вызовы функций AutoIP, описанных далее в этом руководстве. В приложение также следует включить файл *nx_auto_ip.c* в процессе сборки. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX AutoIP.

> [!NOTE]
> Так как AutoIP использует службы NetX ARP, необходимо включить протокол ARP с помощью вызова *nx_arp_enable* перед использованием AutoIP.

## <a name="small-example-system"></a>Пример небольшой системы

Пример того, насколько просто использовать AutoIP NetX, приведен на рисунке 1.1 ниже. В этом примере включаемый файл AutoIP *nx_auto_ip.h* добавлен в строке 002. Затем создается экземпляр NetX AutoIP в функции *tx_application_define* в строке 090. Обратите внимание на то, что блок управления NetX AutoIP, auto_ip_0, был ранее определен как глобальная переменная в строке 015. После успешного создания NetX AutoIP запускается в строке 098. В строке 105 начинается обработка функции обратного вызова при изменении IP-адреса, которая используется для обработки последующих конфликтов или возможного разрешения адресов DHCP.

> [!NOTE]
> В приведенном ниже примере предполагается, что основное устройство имеет один сетевой интерфейс. Для многосетевого устройства ведущее приложение может использовать службу NetX AutoIP *nx_auto_ip_interface_* , чтобы указать дополнительный сетевой интерфейс для отправки пробы на IP-адрес. Дополнительные сведения о настройке многосетевых приложений см. в [руководстве пользователя NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide). Обратите внимание на то, что ведущее приложение должно использовать API NetX *nx_status_ip_interface_check*, чтобы убедиться, что экземпляр AutoIP получил IP-адрес.

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

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
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

Рисунок 1.1. Пример использования AutoIP с NetX

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для сборки NetX AutoIP. Ниже приведен список всех параметров с подробным описанием каждого из них.

- **NX_DISABLE_ERROR_CHECKING**: если этот параметр определен, он отключает базовую проверку на ошибки AutoIP. Обычно он используется после отладки приложения.
- **NX_AUTO_IP_PROBE_WAIT**: время ожидания в секундах перед отправкой первой пробы. По умолчанию это значение равно 1.
- **NX_AUTO_IP_PROBE_NUM**: количество отправляемых проб ARP. По умолчанию это значение равно 3.
- **NX_AUTO_IP_PROBE_MIN**: минимальное время ожидания в секундах между отправками проб. По умолчанию это значение равно 1.
- **NX_AUTO_IP_PROBE_MAX**: максимальное время ожидания в секундах между отправками проб. По умолчанию это значение равно 2.
- **NX_AUTO_IP_MAX_CONFLICTS**: количество конфликтов AutoIP, предшествующих увеличению задержки обработки. По умолчанию это значение равно 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL**: время в секундах, на которое будет продлен период ожидания при превышении общего числа конфликтов. По умолчанию это значение равно 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT**: время ожидания в секундах перед отправкой объявления. По умолчанию это значение равно 2.
- **NX_AUTO_IP_ANNOUNCE_NUM**: количество отправляемых объявлений ARP. По умолчанию это значение равно 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL**: время ожидания в секундах между отправками объявлений. По умолчанию это значение равно 2.
- **NX_AUTO_IP_DEFEND_INTERVAL**: время ожидания в секундах между объявлениями защиты. По умолчанию это значение равно 10.
