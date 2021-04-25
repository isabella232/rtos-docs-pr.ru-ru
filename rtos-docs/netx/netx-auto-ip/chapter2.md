---
title: Глава 2. Установка и использование AutoIP NetX для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента AutoIP NetX для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 269a3b4e9754fdc19e2cf1482d483fad2b841de9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814460"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a><span data-ttu-id="f1177-103">Глава 2. Установка и использование AutoIP NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="f1177-103">Chapter 2 - Installation and use of Azure RTOS NetX AutoIP</span></span>

<span data-ttu-id="f1177-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента AutoIP NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="f1177-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="f1177-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="f1177-105">Product Distribution</span></span>

<span data-ttu-id="f1177-106">AutoIP для NetX доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span><span class="sxs-lookup"><span data-stu-id="f1177-106">AutoIP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="f1177-107">Пакет содержит три файла исходного кода, один файл заголовков и PDF-файл, содержащий этот документ:</span><span class="sxs-lookup"><span data-stu-id="f1177-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="f1177-108">**nx_auto_ip.h**: заголовочный файл AutoIP для NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="f1177-109">**nx_auto_ip.c**: исходный файл C AutoIP для NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="f1177-110">**demo_netx_auto_ip.c**: исходный файл C демонстрации работы AutoIP для NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="f1177-111">**nx_auto_ip.pdf**: описание AutoIP для NetX в формате PDF.</span><span class="sxs-lookup"><span data-stu-id="f1177-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="f1177-112">Установка AutoIP</span><span class="sxs-lookup"><span data-stu-id="f1177-112">AutoIP Installation</span></span>

<span data-ttu-id="f1177-113">Чтобы использовать AutoIP для NetX, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="f1177-114">Например, если NetX установлен в каталоге " *\threadx\arm7\green*", то файлы *nx_auto_ip.h*, *nx_auto_ip.c* и *demo_netx_auto_ip.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="f1177-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="f1177-115">Использование AutoIP</span><span class="sxs-lookup"><span data-stu-id="f1177-115">Using AutoIP</span></span>

<span data-ttu-id="f1177-116">Использовать AutoIP для NetX просто.</span><span class="sxs-lookup"><span data-stu-id="f1177-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="f1177-117">В коде приложения следует включить файл *nx_auto_ip.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="f1177-118">После включения файла *nx_auto_ip.h* код приложения сможет выполнять вызовы функций AutoIP, указанные далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="f1177-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="f1177-119">В приложение также следует включить файл *nx_auto_ip.c* для процесса сборки.</span><span class="sxs-lookup"><span data-stu-id="f1177-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="f1177-120">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="f1177-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="f1177-121">Это все, что необходимо для использования AutoIP для NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="f1177-122">Так как AutoIP использует службы ARP NetX, необходимо включить ARP с помощью вызова *nx_arp_enable* перед использованием AutoIP.</span><span class="sxs-lookup"><span data-stu-id="f1177-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="f1177-123">Небольшой пример системы</span><span class="sxs-lookup"><span data-stu-id="f1177-123">Small Example System</span></span>

<span data-ttu-id="f1177-124">Пример того, насколько просто использовать AutoIP NetX, приведен на рисунке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="f1177-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="f1177-125">В этом примере заголовочный файл AutoIP *nx_auto_ip.h* подключается в строке 002.</span><span class="sxs-lookup"><span data-stu-id="f1177-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="f1177-126">Затем создается экземпляр AutoIP NetX в "*tx_application_define*" в строке 090.</span><span class="sxs-lookup"><span data-stu-id="f1177-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="f1177-127">Обратите внимание, что блок управления AutoIP NetX "auto_ip_0" был ранее определен как глобальная переменная в строке 015.</span><span class="sxs-lookup"><span data-stu-id="f1177-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="f1177-128">После успешного создания AutoIP NetX запускается в строке 098.</span><span class="sxs-lookup"><span data-stu-id="f1177-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="f1177-129">Обработка функции обратного вызова изменения IP-адреса начинается со строки 105, которая используется для обработки последующих конфликтов или возможного разрешения адресов DHCP.</span><span class="sxs-lookup"><span data-stu-id="f1177-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="f1177-130">В приведенном ниже примере предполагается, что основное устройство является устройством с одной сетевой адресацией.</span><span class="sxs-lookup"><span data-stu-id="f1177-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="f1177-131">Для многосетевого устройства ведущее приложение может использовать службу AutoIP NetX *nx_auto_ip_interface_* , настроенную для указания дополнительного сетевого интерфейса для проверки IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="f1177-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="f1177-132">Дополнительные сведения о настройке многосетевых приложений см. в **Руководстве пользователя по NetX**.</span><span class="sxs-lookup"><span data-stu-id="f1177-132">See the **NetX User Guide** for more details on setting up multihomed applications.</span></span> <span data-ttu-id="f1177-133">Обратите внимание, что ведущее приложение должно использовать API NetX *nx_status_ip_interface_check*, чтобы убедиться, что AutoIP получил IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="f1177-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

## <a name="example-of-autoip-use-with-netx"></a><span data-ttu-id="f1177-134">Пример использования AutoIP с NetX</span><span class="sxs-lookup"><span data-stu-id="f1177-134">Example of AutoIP use with NetX</span></span>

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a><span data-ttu-id="f1177-135">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="f1177-135">Configuration Options</span></span>

<span data-ttu-id="f1177-136">Существует ряд параметров конфигурации для создания AutoIP NetX.</span><span class="sxs-lookup"><span data-stu-id="f1177-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="f1177-137">Ниже приведен список всех параметров с описанием.</span><span class="sxs-lookup"><span data-stu-id="f1177-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="f1177-138">**NX_DISABLE_ERROR_CHECKING**: определен, этот параметр удаляет базовую проверку ошибок AutoIP.</span><span class="sxs-lookup"><span data-stu-id="f1177-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="f1177-139">Обычно он включается после завершения отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="f1177-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="f1177-140">**NX_AUTO_IP_PROBE_WAIT**: время ожидания в секундах перед отправкой первой пробы.</span><span class="sxs-lookup"><span data-stu-id="f1177-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="f1177-141">По умолчанию значение равно 1.</span><span class="sxs-lookup"><span data-stu-id="f1177-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="f1177-142">**NX_AUTO_IP_PROBE_NUM**: количество проб ARP для отправки.</span><span class="sxs-lookup"><span data-stu-id="f1177-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="f1177-143">По умолчанию значение равно 3.</span><span class="sxs-lookup"><span data-stu-id="f1177-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="f1177-144">**NX_AUTO_IP_PROBE_MIN**: минимальное время ожидания в секундах между отправкой проб.</span><span class="sxs-lookup"><span data-stu-id="f1177-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="f1177-145">По умолчанию значение равно 1.</span><span class="sxs-lookup"><span data-stu-id="f1177-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="f1177-146">**NX_AUTO_IP_PROBE_MAX**: максимальное время ожидания в секундах между отправкой проб.</span><span class="sxs-lookup"><span data-stu-id="f1177-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="f1177-147">По умолчанию значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="f1177-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="f1177-148">**NX_AUTO_IP_MAX_CONFLICTS**: количество конфликтов AutoIP перед увеличением задержки обработки.</span><span class="sxs-lookup"><span data-stu-id="f1177-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="f1177-149">По умолчанию значение равно 10.</span><span class="sxs-lookup"><span data-stu-id="f1177-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="f1177-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: время в секундах, в течение которого будет продлен период ожидания при превышении общего числа конфликтов.</span><span class="sxs-lookup"><span data-stu-id="f1177-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="f1177-151">По умолчанию значение равно 60.</span><span class="sxs-lookup"><span data-stu-id="f1177-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="f1177-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: время ожидания в секундах перед отправкой объявления.</span><span class="sxs-lookup"><span data-stu-id="f1177-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="f1177-153">По умолчанию значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="f1177-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="f1177-154">**NX_AUTO_IP_ANNOUNCE_NUM**: количество отправляемых объявлений ARP.</span><span class="sxs-lookup"><span data-stu-id="f1177-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="f1177-155">По умолчанию значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="f1177-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="f1177-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: время ожидания в секундах между отправками объявлений.</span><span class="sxs-lookup"><span data-stu-id="f1177-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="f1177-157">По умолчанию значение равно 2.</span><span class="sxs-lookup"><span data-stu-id="f1177-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="f1177-158">**NX_AUTO_IP_DEFEND_INTERVAL**: время ожидания в секундах между объявлениями защиты.</span><span class="sxs-lookup"><span data-stu-id="f1177-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="f1177-159">По умолчанию значение равно 10.</span><span class="sxs-lookup"><span data-stu-id="f1177-159">By default, this value is defined as 10.</span></span>