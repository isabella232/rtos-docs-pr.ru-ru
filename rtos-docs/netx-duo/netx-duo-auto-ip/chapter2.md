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
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="b76e7-103">Глава 2. Установка и использование ОСРВ Azure NetX Duo AutoIP</span><span class="sxs-lookup"><span data-stu-id="b76e7-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="b76e7-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="b76e7-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="b76e7-105">Product Distribution</span></span>

<span data-ttu-id="b76e7-106">ОСРВ Azure NetX AutoIP можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="b76e7-106">Azure RTOS NetX AutoIP can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="b76e7-107">Пакет содержит три файла исходного кода, один включаемый файл и PDF-файл, содержащий этот документ:</span><span class="sxs-lookup"><span data-stu-id="b76e7-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="b76e7-108">**nx_auto_ip.h**: файл заголовка NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="b76e7-109">**nx_auto_ip.c**: исходный файл C для NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="b76e7-110">**demo_netx_auto_ip.c**: демонстрационный исходный файл C для NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="b76e7-111">**nx_auto_ip.pdf**: PDF-файл с описанием NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="b76e7-112">Установка AutoIP</span><span class="sxs-lookup"><span data-stu-id="b76e7-112">AutoIP Installation</span></span>

<span data-ttu-id="b76e7-113">Чтобы использовать NetX AutoIP, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен экземпляр NetX.</span><span class="sxs-lookup"><span data-stu-id="b76e7-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="b76e7-114">Например, если экземпляр NetX установлен в каталог *\threadx\arm7\green*, то файлы *nx_auto_ip.h*, *nx_auto_ip.c* и *demo_netx_auto_ip.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="b76e7-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="b76e7-115">Использование AutoIP</span><span class="sxs-lookup"><span data-stu-id="b76e7-115">Using AutoIP</span></span>

<span data-ttu-id="b76e7-116">Использовать NetX AutoIP просто.</span><span class="sxs-lookup"><span data-stu-id="b76e7-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="b76e7-117">В код приложения следует включить файл *nx_auto_ip.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX.</span><span class="sxs-lookup"><span data-stu-id="b76e7-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="b76e7-118">После включения файла *nx_auto_ip.h* код приложения сможет выполнять вызовы функций AutoIP, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="b76e7-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="b76e7-119">В приложение также следует включить файл *nx_auto_ip.c* в процессе сборки.</span><span class="sxs-lookup"><span data-stu-id="b76e7-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="b76e7-120">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="b76e7-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="b76e7-121">Это все, что необходимо для использования NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="b76e7-122">Так как AutoIP использует службы NetX ARP, необходимо включить протокол ARP с помощью вызова *nx_arp_enable* перед использованием AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="b76e7-123">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="b76e7-123">Small Example System</span></span>

<span data-ttu-id="b76e7-124">Пример того, насколько просто использовать AutoIP NetX, приведен на рисунке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="b76e7-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="b76e7-125">В этом примере включаемый файл AutoIP *nx_auto_ip.h* добавлен в строке 002.</span><span class="sxs-lookup"><span data-stu-id="b76e7-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="b76e7-126">Затем создается экземпляр NetX AutoIP в функции *tx_application_define* в строке 090.</span><span class="sxs-lookup"><span data-stu-id="b76e7-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="b76e7-127">Обратите внимание на то, что блок управления NetX AutoIP, auto_ip_0, был ранее определен как глобальная переменная в строке 015.</span><span class="sxs-lookup"><span data-stu-id="b76e7-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="b76e7-128">После успешного создания NetX AutoIP запускается в строке 098.</span><span class="sxs-lookup"><span data-stu-id="b76e7-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="b76e7-129">В строке 105 начинается обработка функции обратного вызова при изменении IP-адреса, которая используется для обработки последующих конфликтов или возможного разрешения адресов DHCP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="b76e7-130">В приведенном ниже примере предполагается, что основное устройство имеет один сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b76e7-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="b76e7-131">Для многосетевого устройства ведущее приложение может использовать службу NetX AutoIP *nx_auto_ip_interface_* , чтобы указать дополнительный сетевой интерфейс для отправки пробы на IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="b76e7-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="b76e7-132">Дополнительные сведения о настройке многосетевых приложений см. в [руководстве пользователя NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide).</span><span class="sxs-lookup"><span data-stu-id="b76e7-132">See the [NetX User Guide](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) for more details on setting up multihomed applications.</span></span> <span data-ttu-id="b76e7-133">Обратите внимание на то, что ведущее приложение должно использовать API NetX *nx_status_ip_interface_check*, чтобы убедиться, что экземпляр AutoIP получил IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="b76e7-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

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

<span data-ttu-id="b76e7-134">Рисунок 1.1. Пример использования AutoIP с NetX</span><span class="sxs-lookup"><span data-stu-id="b76e7-134">Figure 1.1 Example of AutoIP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="b76e7-135">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="b76e7-135">Configuration Options</span></span>

<span data-ttu-id="b76e7-136">Существует ряд параметров конфигурации для сборки NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="b76e7-137">Ниже приведен список всех параметров с подробным описанием каждого из них.</span><span class="sxs-lookup"><span data-stu-id="b76e7-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="b76e7-138">**NX_DISABLE_ERROR_CHECKING**: если этот параметр определен, он отключает базовую проверку на ошибки AutoIP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="b76e7-139">Обычно он используется после отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="b76e7-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="b76e7-140">**NX_AUTO_IP_PROBE_WAIT**: время ожидания в секундах перед отправкой первой пробы.</span><span class="sxs-lookup"><span data-stu-id="b76e7-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="b76e7-141">По умолчанию это значение равно 1.</span><span class="sxs-lookup"><span data-stu-id="b76e7-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="b76e7-142">**NX_AUTO_IP_PROBE_NUM**: количество отправляемых проб ARP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="b76e7-143">По умолчанию это значение равно 3.</span><span class="sxs-lookup"><span data-stu-id="b76e7-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="b76e7-144">**NX_AUTO_IP_PROBE_MIN**: минимальное время ожидания в секундах между отправками проб.</span><span class="sxs-lookup"><span data-stu-id="b76e7-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="b76e7-145">По умолчанию это значение равно 1.</span><span class="sxs-lookup"><span data-stu-id="b76e7-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="b76e7-146">**NX_AUTO_IP_PROBE_MAX**: максимальное время ожидания в секундах между отправками проб.</span><span class="sxs-lookup"><span data-stu-id="b76e7-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="b76e7-147">По умолчанию это значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="b76e7-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b76e7-148">**NX_AUTO_IP_MAX_CONFLICTS**: количество конфликтов AutoIP, предшествующих увеличению задержки обработки.</span><span class="sxs-lookup"><span data-stu-id="b76e7-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="b76e7-149">По умолчанию это значение равно 10.</span><span class="sxs-lookup"><span data-stu-id="b76e7-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="b76e7-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: время в секундах, на которое будет продлен период ожидания при превышении общего числа конфликтов.</span><span class="sxs-lookup"><span data-stu-id="b76e7-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="b76e7-151">По умолчанию это значение равно 60.</span><span class="sxs-lookup"><span data-stu-id="b76e7-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="b76e7-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: время ожидания в секундах перед отправкой объявления.</span><span class="sxs-lookup"><span data-stu-id="b76e7-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="b76e7-153">По умолчанию это значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="b76e7-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b76e7-154">**NX_AUTO_IP_ANNOUNCE_NUM**: количество отправляемых объявлений ARP.</span><span class="sxs-lookup"><span data-stu-id="b76e7-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="b76e7-155">По умолчанию это значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="b76e7-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b76e7-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: время ожидания в секундах между отправками объявлений.</span><span class="sxs-lookup"><span data-stu-id="b76e7-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="b76e7-157">По умолчанию это значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="b76e7-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="b76e7-158">**NX_AUTO_IP_DEFEND_INTERVAL**: время ожидания в секундах между объявлениями защиты.</span><span class="sxs-lookup"><span data-stu-id="b76e7-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="b76e7-159">По умолчанию это значение равно 10.</span><span class="sxs-lookup"><span data-stu-id="b76e7-159">By default, this value is defined as 10.</span></span>
