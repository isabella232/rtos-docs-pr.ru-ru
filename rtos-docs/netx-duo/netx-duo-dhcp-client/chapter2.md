---
title: Глава 2. Установка и использование клиента ОСРВ Azure NetX Duo DHCP
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиентского компонента ОСРВ Azure NetX Duo DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c3df64be337b557f492617c1ef20adc7c0f8d6e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814803"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-dhcp-client"></a><span data-ttu-id="3ba52-103">Глава 2. Установка и использование клиента ОСРВ Azure NetX Duo DHCP</span><span class="sxs-lookup"><span data-stu-id="3ba52-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo DHCP Client</span></span>

<span data-ttu-id="3ba52-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием клиентского компонента ОСРВ Azure NetX Duo DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo DHCP Client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="3ba52-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="3ba52-105">Product Distribution</span></span>

<span data-ttu-id="3ba52-106">ОСРВ Azure NetX Duo можно получить из нашего общедоступного репозитория исходного кода по адресу <https://github.com/azure-rtos/netxduo>.</span><span class="sxs-lookup"><span data-stu-id="3ba52-106">Azure RTOS NetX Duo can be obtained from our public source code repository at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="3ba52-107">В состав пакета входят следующие файлы:</span><span class="sxs-lookup"><span data-stu-id="3ba52-107">The package includes the following files:</span></span>

- <span data-ttu-id="3ba52-108">**nxd_dhcp_client.h**: файл заголовка для NetX Duo DHCP;</span><span class="sxs-lookup"><span data-stu-id="3ba52-108">**nxd_dhcp_client.h**: Header file for NetX Duo DHCP</span></span>
- <span data-ttu-id="3ba52-109">**nxd_dhcp_client.c**: файл исходного кода C для NetX Duo DHCP;</span><span class="sxs-lookup"><span data-stu-id="3ba52-109">**nxd_dhcp_client.c**: C Source file for DHCP NetX Duo</span></span>
- <span data-ttu-id="3ba52-110">**nxd_dhcp_client.pdf**: руководство пользователя NetX Duo DHCP;</span><span class="sxs-lookup"><span data-stu-id="3ba52-110">**nxd_dhcp_client.pdf**: User Guide for NetX Duo DHCP</span></span> 
    - <span data-ttu-id="3ba52-111">**demo_netxduo_dhcp.c**: демонстрационный файл для клиента NetX Duo DHCP;</span><span class="sxs-lookup"><span data-stu-id="3ba52-111">**demo_netxduo_dhcp.c**: NetX Duo DHCP Client demonstration</span></span>
    - <span data-ttu-id="3ba52-112">**demo_netxduo_multihome_dhcp_client.c**: демонстрационный файл клиента NetX Duo DHCP, котором протокол DHCP используется на нескольких интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="3ba52-112">**demo_netxduo_multihome_dhcp_client.c**: NetX Duo DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="3ba52-113">Установка экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="3ba52-113">DHCP Installation</span></span>

<span data-ttu-id="3ba52-114">Чтобы использовать клиент NetX Duo DHCP, весь дистрибутив, упомянутый выше, необходимо скопировать в каталог, где установлен экземпляр NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3ba52-114">To use NetX Duo DHCP Client, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="3ba52-115">Например, если экземпляр NetX Duo установлен в каталог *\threadx\arm7\green*, то файлы *nxd_dhcp_client.h* и *nxd_dhcp_client.c* следует скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="3ba52-115">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nxd_dhcp_client.h* and *nxd_dhcp_client.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="3ba52-116">Использование протокола DHCP</span><span class="sxs-lookup"><span data-stu-id="3ba52-116">Using DHCP</span></span>

<span data-ttu-id="3ba52-117">Использовать DHCP для NetX Duo просто.</span><span class="sxs-lookup"><span data-stu-id="3ba52-117">Using DHCP for NetX Duo is easy.</span></span> <span data-ttu-id="3ba52-118">В код приложения достаточно добавить файл *nxd_dhcp_client.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX Duo соответственно.</span><span class="sxs-lookup"><span data-stu-id="3ba52-118">Basically, the application code must include *nxd_dhcp_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX Duo, respectively.</span></span> <span data-ttu-id="3ba52-119">После добавления файла *nxd_dhcp_client.h* код приложения сможет выполнять вызовы функций DHCP, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="3ba52-119">Once *nxd_dhcp_client.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="3ba52-120">В приложение также нужно включить файл *nxd_dhcp_client.c* в процессе сборки.</span><span class="sxs-lookup"><span data-stu-id="3ba52-120">The application must also include *nxd_dhcp_client.c* in the build process.</span></span> <span data-ttu-id="3ba52-121">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="3ba52-122">Это все, что необходимо для использования NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="3ba52-123">Учтите, что так как протокол DHCP использует службы NetX Duo UDP, перед использованием DHCP следует включить протокол UDP с помощью вызова *nx_udp_enable*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-123">Note that since DHCP utilizes NetX Duo UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="3ba52-124">Чтобы получить назначенный ранее IP-адрес, DHCP-клиент может инициировать процесс DHCP с сообщением REQUEST и параметром 50 "Requested IP Address" (Запрошенный IP-адрес) на DHCP-сервере.</span><span class="sxs-lookup"><span data-stu-id="3ba52-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="3ba52-125">DHCP-сервер ответит сообщением ACK, если он предоставляет клиенту этот IP-адрес, или сообщением NACK, если он отклоняет запрос.</span><span class="sxs-lookup"><span data-stu-id="3ba52-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="3ba52-126">В последнем случае DHCP-клиент перезапустит процесс DHCP в состоянии INIT с сообщением DISCOVER и без запрошенного IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="3ba52-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="3ba52-127">Ведущее приложение сначала создает DHCP-клиент, а затем вызывает службу API *nx_dhcp_request_client_ip* для задания запрошенного IP-адреса перед запуском процесса DHCP вызовом *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="3ba52-128">В этом документе приведен пример приложения DHCP, ознакомившись с которым можно получить дополнительные сведения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="3ba52-129">В состоянии BOUND</span><span class="sxs-lookup"><span data-stu-id="3ba52-129">In the Bound State</span></span>

<span data-ttu-id="3ba52-130">Пока DHCP-клиент находится в состоянии BOUND, поток DHCP-клиента обрабатывает состояние клиента один раз в период (указанный в NX_DHCP_TIME_INTERVAL) и уменьшает оставшееся время аренды IP-адреса, назначенной этому клиенту.</span><span class="sxs-lookup"><span data-stu-id="3ba52-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="3ba52-131">Когда наступает время продления, состояние DHCP-клиента меняется на RENEW. На этом этапе клиент запрашивает продление у DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="3ba52-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>

## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="3ba52-132">Отправка сообщений DHCP на сервер</span><span class="sxs-lookup"><span data-stu-id="3ba52-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="3ba52-133">У DHCP-клиента имеются службы API, позволяющие ведущему приложению отправить сообщение на DHCP-сервер.</span><span class="sxs-lookup"><span data-stu-id="3ba52-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="3ba52-134">Обратите внимание на то, что эти службы не предназначены для того, чтобы ведущее приложение вручную запускало протокол DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol.</span></span>

  - <span data-ttu-id="3ba52-135">*nx_dhcp_release*: отправляет сообщение RELEASE на сервер, когда ведущее приложение либо выходит из сети, либо должно освободить свой IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="3ba52-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>
  - <span data-ttu-id="3ba52-136">*nx_dhcp_decline*: отправляет сообщение DECLINE на сервер, если ведущее приложение определило независимо от DHCP-клиента, что его IP-адрес уже используется.</span><span class="sxs-lookup"><span data-stu-id="3ba52-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>
  - <span data-ttu-id="3ba52-137">*nx_dhcp_forcerenew*: отправляет сообщение FORCERENEW на сервер.</span><span class="sxs-lookup"><span data-stu-id="3ba52-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>
  - <span data-ttu-id="3ba52-138">*nx_dhcp_send_request*: этот параметр принимает в качестве аргумента тип сообщения DHCP, указанный в файле *nxd_dhcp_client.h*, и отправляет сообщение на сервер.</span><span class="sxs-lookup"><span data-stu-id="3ba52-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nxd_dhcp_client.h*, and sends the message to the Server.</span></span> <span data-ttu-id="3ba52-139">Он предназначен в первую очередь для отправки сообщения INFORM протокола DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="3ba52-140">Дополнительные сведения об этих службах см. в [описании служб DHCP](chapter3.md).</span><span class="sxs-lookup"><span data-stu-id="3ba52-140">See [Description of DHCP Services](chapter3.md) for more information about these services</span></span> 

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="3ba52-141">Запуск и остановка DHCP-клиента</span><span class="sxs-lookup"><span data-stu-id="3ba52-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="3ba52-142">Чтобы остановить DHCP-клиент независимо от того, перешел ли он в состояние BOUND, ведущее приложение вызывает службу *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="3ba52-143">Чтобы перезапустить DHCP-клиент, ведущее приложение должно сначала остановить его с помощью службы *nx_dhcp_stop*, описанной выше.</span><span class="sxs-lookup"><span data-stu-id="3ba52-143">To restart a DHCP Client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="3ba52-144">Затем узел может вызвать службу *nx_dhcp_start*, чтобы возобновить работу DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="3ba52-145">Если ведущее приложение хочет очистить предыдущий профиль DHCP-клиента, например, полученный от предыдущего DHCP-сервера в другой сети, то перед вызовом службы *nx_dhcp_start* оно должно вызвать службу *nx_dhcp_reinitialize* для внутреннего выполнения этой задачи.</span><span class="sxs-lookup"><span data-stu-id="3ba52-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="3ba52-146">Типичная последовательность может быть следующей.</span><span class="sxs-lookup"><span data-stu-id="3ba52-146">A typical sequence might be:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="3ba52-147">Для приложений DHCP, выполняющихся только на одном интерфейсе DHCP, остановка DHCP-клиента также приводит к отключению таймера DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="3ba52-148">Поэтому оставшееся время аренды IP-адреса больше не отслеживается.</span><span class="sxs-lookup"><span data-stu-id="3ba52-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="3ba52-149">Остановка DHCP-клиента на определенном интерфейсе не приведет к отключению таймера DHCP-клиента, но прекратит обновление таймера с учетом оставшегося времени аренды IP-адреса на этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="3ba52-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface</span></span>

<span data-ttu-id="3ba52-150">Следовательно, остановка DHCP-клиента не рекомендуется, если только ведущему приложению не требуется выполнить перезагрузку или переключение сетей.</span><span class="sxs-lookup"><span data-stu-id="3ba52-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="3ba52-151">Использование DHCP-клиента с протоколом AutoIP</span><span class="sxs-lookup"><span data-stu-id="3ba52-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="3ba52-152">Клиент NetX Duo DHCP работает вместе с протоколом AutoIP в приложениях, в которых протоколы DHCP и AutoIP обеспечивают адрес, а наличие доступного и отвечающего на запросы DHCP-сервера не гарантируется.</span><span class="sxs-lookup"><span data-stu-id="3ba52-152">The NetX Duo DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="3ba52-153">Однако если узлу не удается обнаружить сервер или получить назначенный IP-адрес, он может переключиться на протокол AutoIP для локального IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="3ba52-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="3ba52-154">Перед этим рекомендуется временно остановить DHCP-клиент, пока протокол AutoIP выполняет этапы отправки проб и защиты.</span><span class="sxs-lookup"><span data-stu-id="3ba52-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="3ba52-155">После назначения адреса AutoIP узлу можно будет перезапустить DHCP-клиент и, если DHCP-сервер станет доступным, IP-адрес узла сможет принять IP-адрес, предлагаемый DHCP-сервером во время работы приложения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="3ba52-156">В протокол NetX Duo AutoIP имеется уведомление об изменении адреса, которое позволяет узлу отслеживать свои действия в случае изменения IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="3ba52-156">The NetX Duo Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="packet-chaining"></a><span data-ttu-id="3ba52-157">Связывание пакетов</span><span class="sxs-lookup"><span data-stu-id="3ba52-157">Packet Chaining</span></span>

<span data-ttu-id="3ba52-158">Для более эффективного использования ресурсов пула пакетов и памяти DHCP-клиент может обрабатывать входящие связанные пакеты (датаграммы, размер которых превышает MTU драйвера) от драйвера Ethernet.</span><span class="sxs-lookup"><span data-stu-id="3ba52-158">For more efficient use of packet pool and memory resources, the DHCP Client can handle incoming chained packets (datagrams exceeding the driver MTU) from the Ethernet driver.</span></span> <span data-ttu-id="3ba52-159">Если драйвер поддерживает такую возможность, приложение может настроить пул пакетов для получения пакетов, размер которых не превышает обязательное значение NX_DHCP_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="3ba52-159">If the driver has this capability, the application can set the packet pool for receiving packets to below the mandatory NX_DHCP_PACKET_PAYLOAD bytes.</span></span> <span data-ttu-id="3ba52-160">Значение NX_DHCP_PACKET_PAYLOAD должно быть достаточным, чтобы вместить кадр физической сети (обычно Ethernet), 548 байт данных сообщения DHCP, а также служебные данные IP и UDP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-160">NX_DHCP_PACKET_PAYLOAD should accommodate the physical network (typically Ethernet) frame, plus 548 bytes of DHCP message data, and IP and UDP.</span></span>

<span data-ttu-id="3ba52-161">Обратите внимание на то, что приложение может оптимизировать полезные данные пакета и количество пакетов в пуле пакетов, который является частью DHCP-клиента и используется для отправки сообщений DHCP. Оно может оптимизировать размер в зависимости от ожидаемого использования и размера сообщений DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-161">Note that the application can optimize the packet payload and number of packets in the packet pool that is part of the DHCP Client, and which is used for sending DHCP messages out. It can optimize the size based on expected usage and size of the DHCP Client messages.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="3ba52-162">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="3ba52-162">Small Example System</span></span>

<span data-ttu-id="3ba52-163">Пример использования NetX Duo показан на рисунке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="3ba52-163">An example of how to use NetX Duo is shown in Figure 1.1 below.</span></span> <span data-ttu-id="3ba52-164">Функция входа потока приложения *my_thread_entry* создается в строке 101.</span><span class="sxs-lookup"><span data-stu-id="3ba52-164">The application thread entry function “*my_thread_entry*” is created at line 101.</span></span> <span data-ttu-id="3ba52-165">После успешного создания в строке 108 инициируется обработка DHCP с помощью вызова *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-165">After successful creation, DHCP processing is initiated with the *nx_dhcp_start* call at line 108.</span></span> <span data-ttu-id="3ba52-166">На этом этапе задача потока DHCP-клиента пытается отдельно связаться с DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="3ba52-166">At this point, the DHCP Client thread task separately attempts to contact a DHCP server.</span></span> <span data-ttu-id="3ba52-167">Во время этого процесса код приложения ожидает регистрации допустимого IP-адреса в экземпляре IP с помощью службы *nx_ip_status_check* (или *nx_ip_interface_status_check* для дополнительного интерфейса) в строке 95.</span><span class="sxs-lookup"><span data-stu-id="3ba52-167">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) on line 95.</span></span> <span data-ttu-id="3ba52-168">Чаще всего для этого используется цикл с более коротким параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="3ba52-168">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="3ba52-169">После строки 127 DHCP-сервер получил допустимый IP-адрес, и приложение может продолжать работу, используя службы NetX Duo TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-169">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX Duo TCP/IP services as desired.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */
intmain()
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

    /* Create “my_thread”.  */
      tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                        pointer, DEMO_STACK_SIZE, 2, 2, 
                        TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

    /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                          0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
                          DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
 }


 /* Define my thread.  */

 void    my_thread_entry(ULONG thread_input)
 {

 UINT        status;
 ULONG       actual_status;
 NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
    /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                                     &actual_status, 100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
      error_counter++;
      return;
    }
    else
    {

  /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.
    }
 }

```
## <a name="multi-server-environments"></a><span data-ttu-id="3ba52-170">Многосерверные среды</span><span class="sxs-lookup"><span data-stu-id="3ba52-170">Multi-Server Environments</span></span>

<span data-ttu-id="3ba52-171">В сетях, в которых имеется более одного DHCP-сервера, DHCP-клиент принимает первое полученное от DHCP-сервера сообщение OFFER, переходит в состояние REQUEST и игнорирует все прочие полученные предложения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-171">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="3ba52-172">Пробы ARP</span><span class="sxs-lookup"><span data-stu-id="3ba52-172">ARP Probes</span></span>

<span data-ttu-id="3ba52-173">DHCP-клиент можно настроить для отправки одной или нескольких проб ARP после назначения IP-адреса DHCP-сервером, чтобы проверить, не используется ли этот IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="3ba52-173">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="3ba52-174">Этап отправки проб ARP рекомендуется спецификацией RFC 2131 и особенно важен в средах с несколькими DHCP-серверами.</span><span class="sxs-lookup"><span data-stu-id="3ba52-174">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="3ba52-175">Если ведущее приложение включит параметр NX_DHCP_CLIENT_SEND_ARP_PROBE (см. раздел **Параметры конфигурации** в главе 2, чтобы ознакомиться с дополнительными параметрами проверки ARP), то DHCP-клиент отправит пробу ARP на свой адрес и будет ждать ответ в течение указанного времени.</span><span class="sxs-lookup"><span data-stu-id="3ba52-175">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="3ba52-176">Если DHCP-клиент не получит ответа, то он перейдет в состояние BOUND.</span><span class="sxs-lookup"><span data-stu-id="3ba52-176">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="3ba52-177">В случае получения ответа DHCP-клиент предполагает, что этот адрес уже используется.</span><span class="sxs-lookup"><span data-stu-id="3ba52-177">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="3ba52-178">Он автоматически отправляет на сервер сообщение DECLINE и повторно инициализирует клиент для отправки проб DHCP в состоянии INIT.</span><span class="sxs-lookup"><span data-stu-id="3ba52-178">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="3ba52-179">Это приводит к перезапуску конечного автомата DHCP, и клиент отправляет на сервер еще одно сообщение DISCOVER.</span><span class="sxs-lookup"><span data-stu-id="3ba52-179">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="3ba52-180">Протокол BOOTP</span><span class="sxs-lookup"><span data-stu-id="3ba52-180">BOOTP Protocol</span></span>

<span data-ttu-id="3ba52-181">Помимо протокола DHCP DHCP-клиент также поддерживает протокол BOOTP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-181">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="3ba52-182">Чтобы включить эту возможность и использовать протокол BOOTP вместо DHCP, ведущее приложение должно задать параметр конфигурации NX_DHCP_BOOTP_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="3ba52-182">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="3ba52-183">Ведущее приложение по-прежнему может запрашивать определенные IP-адреса в протоколе BOOTP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-183">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="3ba52-184">DHCP-клиент не поддерживает загрузку операционной системы узла, в отличие от протокола BOOTP, который иногда используется для этого.</span><span class="sxs-lookup"><span data-stu-id="3ba52-184">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="3ba52-185">DHCP на дополнительном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="3ba52-185">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="3ba52-186">Клиент NetX Duo DHCP может работать на дополнительных интерфейсах, а не на основном интерфейсе по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3ba52-186">The NetX Duo DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="3ba52-187">Для запуска клиента NetX Duo DHCP на дополнительном сетевом интерфейсе ведущее приложение должно задать индекс дополнительного интерфейса для DHCP-клиента с помощью службы API *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-187">To run NetX Duo DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="3ba52-188">Интерфейс должен быть подключен к основному сетевому интерфейсу с помощью службы *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-188">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="3ba52-189">Сведения о подключении дополнительных интерфейсов приведены в руководстве пользователя NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3ba52-189">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="3ba52-190">Ниже приведен пример системы (рисунок 1.2), в которой ведущее приложение подключается к DHCP-серверу с помощью дополнительного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="3ba52-190">Below is an example system (Figure 1.2) in which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="3ba52-191">В строке 65 дополнительный интерфейс подключается к задаче IP с нулевым IP-адресом.</span><span class="sxs-lookup"><span data-stu-id="3ba52-191">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="3ba52-192">В строке 104 после создания экземпляра DHCP-клиента индексу интерфейса этого DHCP-клиента присваивается значение 1 (т. е. смещение относительно основного интерфейса, которому соответствует индекс 0) путем вызова *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-192">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="3ba52-193">После этого DHCP-клиент готов к запуску в строке 108.</span><span class="sxs-lookup"><span data-stu-id="3ba52-193">Then the DHCP Client is ready to be started in line 108.</span></span>

```c
#include   "tx_api.h"
#include   "nx_api.h"
#include   "nxd_dhcp_client.h"

#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_DHCP                 my_dhcp;

/* Define function prototypes.  */

void    my_thread_entry(ULONG thread_input);
void    my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point.  */

intmain()
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

    /* Create “my_thread”.  */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                      pointer, DEMO_STACK_SIZE, 
                      2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX Duo system.  */
    nx_system_initialize();

  /* Create a packet pool.  */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                     1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error.  */
    if (status)
        error_counter++;

    /* Create an IP instance without an IP address. */
    status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
                           0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors.  */
    if (status)
        error_counter++;

    status =  _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                                       0xFFFFFF00UL, my_netx_driver);

    /* Enable ARP and supply ARP cache memory for my IP Instance.  */
    status =  nx_arp_enable(&my_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors.  */
    if (status)
        error_counter++;

    /* Enable UDP.  */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}


void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       status;
NX_PACKET   *my_packet;

    /* Wait for the link to come up.  */
    do
    {
      /* Get the link status.  */
        status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
    } while (status != NX_SUCCESS);

    /* Create a DHCP instance.  */
    status =  nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

    /* Check for DHCP create error.  */
    if (status)
        error_counter++;

    /* Set the DHCP client interface to the secondary interface. */
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


    /* Start DHCP.  */
    nx_dhcp_start(&my_dhcp);

    /* Check for DHCP start error.  */
    if (status)
        error_counter++;

    /* Wait for IP address to be resolved through DHCP.  */
    nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                       (ULONG *) &status, 100000);

    /* Check to see if we have a valid IP address.  */
    if (status)
    {
        error_counter++;
        return;
    }
    else
    {
    /* Yes, a valid IP address is now on lease…  All NetX Duo
        services are available.*/
    }
}
```

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="3ba52-194">Одновременный запуск DHCP-клиента на нескольких интерфейсах</span><span class="sxs-lookup"><span data-stu-id="3ba52-194">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="3ba52-195">Чтобы запускать DHCP-клиент на нескольких интерфейсах, для параметра NX_MAX_PHYSICAL_INTERFACES в *nx_api.h* должно быть задано число физических интерфейсов, подключенных к устройству.</span><span class="sxs-lookup"><span data-stu-id="3ba52-195">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="3ba52-196">По умолчанию это значение равно 1 (т. е. это основной интерфейс).</span><span class="sxs-lookup"><span data-stu-id="3ba52-196">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="3ba52-197">Чтобы зарегистрировать дополнительный интерфейс для экземпляра IP, используйте службу *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-197">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="3ba52-198">Сведения о подключении дополнительных интерфейсов приведены в руководстве пользователя NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="3ba52-198">See the NetX Duo User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="3ba52-199">Следующим шагом является задание для параметра NX_DHCP_CLIENT_MAX_RECORDS в файле *nxd_dhcp_client.h* ожидаемого максимального числа интерфейсов, на которых будет одновременно выполняться протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-199">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nxd_dhcp_client.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="3ba52-200">Обратите внимание на то, что значение NX_DHCP_CLIENT_MAX_RECORDS не равно значению NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="3ba52-200">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="3ba52-201">Например, параметр NX_MAX_PHYSICAL_INTERFACES может иметь значение 3, а NX_DHCP_CLIENT_MAX_RECORDS — 2.</span><span class="sxs-lookup"><span data-stu-id="3ba52-201">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="3ba52-202">В такой конфигурации только два (и это могут быть любые два из трех физических интерфейсов в любой момент) из трех физических интерфейсов могут запускать протокол DHCP одновременно.</span><span class="sxs-lookup"><span data-stu-id="3ba52-202">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="3ba52-203">Записи DHCP-клиентов не сопоставляются однозначно с сетевыми интерфейсами. Например, запись клиента 1 не будет автоматически сопоставлена с индексом физического интерфейса 1.</span><span class="sxs-lookup"><span data-stu-id="3ba52-203">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="3ba52-204">Кроме того, для параметра NX_DHCP_CLIENT_MAX_RECORDS можно задать значение больше значения NX_MAX_PHYSICAL_INTERFACES, но это приведет к созданию неиспользуемых записей клиентов и неэффективному использованию памяти.</span><span class="sxs-lookup"><span data-stu-id="3ba52-204">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="3ba52-205">Прежде чем запустить протокол DHCP на каком-либо интерфейсе, приложение должно включить эти интерфейсы, вызвав *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-205">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="3ba52-206">Обратите внимание на то, что исключением является основной интерфейс, который автоматически включается в вызове *nx_dhcp_create* (его можно отключить с помощью службы *nx_dhcp_interface_disable*, описанной ниже).</span><span class="sxs-lookup"><span data-stu-id="3ba52-206">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="3ba52-207">В любое время на интерфейсе можно отключить протокол DHCP, кроме того, протокол DHCP на этом интерфейсе может быть остановлен независимо от других интерфейсов, использующих DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-207">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="3ba52-208">Как упоминалось выше, чтобы включить протокол DHCP для конкретного интерфейса, используйте службу *nx_dhcp_interface_enable* и укажите индекс физического интерфейса в качестве входного аргумента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-208">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="3ba52-209">Включить протокол можно для числа интерфейсов, не превышающего значение NX_DHCP_CLIENT_MAX_RECORDS. Единственное ограничение состоит в том, что входной аргумент индекса интерфейса должен быть меньше значения NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="3ba52-209">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="3ba52-210">Чтобы запустить протокол DHCP на определенном интерфейсе, используйте службу *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-210">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="3ba52-211">Чтобы запустить протокол DHCP на всех интерфейсах, используйте службу *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-211">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="3ba52-212">(Интерфейсы, для которых протокол DHCP уже запущен, не будут затронуты вызовом *nx_dhcp_start*.)</span><span class="sxs-lookup"><span data-stu-id="3ba52-212">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="3ba52-213">Чтобы остановить протокол DHCP на интерфейсе, используйте службу *nx_dhcp_interface_stop*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-213">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="3ba52-214">Протокол DHCP уже запущен на этом интерфейсе или возвращено состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="3ba52-214">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="3ba52-215">Чтобы остановить протокол DHCP на всех интерфейсах, используйте службу *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-215">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="3ba52-216">Протокол DHCP можно в любое время остановить независимо от других интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="3ba52-216">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="3ba52-217">Большинство существующих служб DHCP-клиента имеют эквивалент для интерфейсов. Например, служба *nx_dhcp_interface_release* является предназначенным для интерфейсов службы *nx_dhcp_release*.</span><span class="sxs-lookup"><span data-stu-id="3ba52-217">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="3ba52-218">Если для DHCP-клиента настроен один интерфейс, он выполняет то же действие.</span><span class="sxs-lookup"><span data-stu-id="3ba52-218">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="3ba52-219">Обратите внимание на то, что службы DHCP-клиента, не относящиеся к интерфейсам, обычно применяются ко всем интерфейсам, но все из них.</span><span class="sxs-lookup"><span data-stu-id="3ba52-219">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="3ba52-220">В последнем случае служба, не относящаяся к интерфейсам, применяется к первому интерфейсу с поддержкой DHCP, найденному в списке записей интерфейсов DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-220">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="3ba52-221">Сведения о том, как работает служба, не относящаяся к интерфейсам, в случае включения протокола DHCP на нескольких интерфейсах, приведены в **описании служб** в главе 3.</span><span class="sxs-lookup"><span data-stu-id="3ba52-221">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="3ba52-222">В приведенном ниже примере для экземпляра IP заданы два сетевых интерфейса, и сначала протокол DHCP выполняется на дополнительном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="3ba52-222">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="3ba52-223">Через некоторое время протокол DHCP запускается на основном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="3ba52-223">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="3ba52-224">Затем освобождается IP-адрес основного интерфейса и протокол DHCP перезапускается на основном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="3ba52-224">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```c
nx_dhcp_create(&my_dhcp_client); /* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); /* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); /* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); /* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); /* DHCP is restarted on primary interface. */
```

<span data-ttu-id="3ba52-225">Полный список служб, связанных с интерфейсами, приведен в **описании служб** в главе 3.</span><span class="sxs-lookup"><span data-stu-id="3ba52-225">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="3ba52-226">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="3ba52-226">Configuration Options</span></span>

<span data-ttu-id="3ba52-227">Настраиваемые пользователем параметры DHCP в файле *nxd_dhcp_client.h* позволяют ведущему приложению настроить DHCP-клиент в соответствии с конкретными требованиями.</span><span class="sxs-lookup"><span data-stu-id="3ba52-227">User configurable DHCP options in *nxd_dhcp_client.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="3ba52-228">Ниже приведен список этих параметров:</span><span class="sxs-lookup"><span data-stu-id="3ba52-228">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="3ba52-229">**NX_DHCP_ENABLE_BOOTP**: если этот параметр определен, то он включает протокол BOOTP вместо DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-229">**NX_DHCP_ENABLE_BOOTP**: Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="3ba52-230">Этот параметр по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="3ba52-230">By default this option is disabled.</span></span>
- <span data-ttu-id="3ba52-231">**NX_DHCP_CLIENT_RESTORE_STATE**: если этот параметр определен, DHCP-клиент сохраняет свое текущее состояние аренды, включая оставшееся время аренды, и восстанавливает это состояние после перезагрузки клиентского приложения DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-231">**NX_DHCP_CLIENT_RESTORE_STATE**: If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="3ba52-232">По умолчанию эта политика отключена.</span><span class="sxs-lookup"><span data-stu-id="3ba52-232">The default value is disabled.</span></span>
- <span data-ttu-id="3ba52-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: если этот параметр задан, DHCP-клиент не будет создавать собственный пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="3ba52-233">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="3ba52-234">Ведущее приложение должно использовать службу *nx_dhcp_packet_pool_set*, чтобы задать пул пакетов DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-234">The host application must use the *nx_dhcp_packet_pool_set* service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="3ba52-235">По умолчанию эта политика отключена.</span><span class="sxs-lookup"><span data-stu-id="3ba52-235">The default value is disabled.</span></span>
- <span data-ttu-id="3ba52-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: если этот параметр определен, он позволяет DHCP-клиенту отправить пробу ARP после назначения IP-адреса, чтобы убедиться, что назначенный адрес DHCP не принадлежит другому узлу.</span><span class="sxs-lookup"><span data-stu-id="3ba52-236">**NX_DHCP_CLIENT_SEND_ARP_PROBE**: Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="3ba52-237">Этот параметр по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="3ba52-237">By default, this option is disabled.</span></span>
- <span data-ttu-id="3ba52-238">**NX_DHCP_ARP_PROBE_WAIT**: определяет период времени, в течение которого DHCP-клиент ожидает ответ после отправки пробы ARP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-238">**NX_DHCP_ARP_PROBE_WAIT**: Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="3ba52-239">Значение по умолчанию — 1 секунда (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="3ba52-239">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>
- <span data-ttu-id="3ba52-240">**NX_DHCP_ARP_PROBE_MIN**: определяет минимальное изменение интервала между отправками проб ARP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-240">**NX_DHCP_ARP_PROBE_MIN**: Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="3ba52-241">Значение по умолчанию — 1 секунда.</span><span class="sxs-lookup"><span data-stu-id="3ba52-241">The value is defaulted to 1 second.</span></span>
- <span data-ttu-id="3ba52-242">**NX_DHCP_ARP_PROBE_MAX**: определяет максимальное изменение интервала между отправками проб ARP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-242">**NX_DHCP_ARP_PROBE_MAX**: Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="3ba52-243">Значение по умолчанию — 2 секунды.</span><span class="sxs-lookup"><span data-stu-id="3ba52-243">The value is defaulted to 2 seconds.</span></span>
- <span data-ttu-id="3ba52-244">**NX_DHCP_ARP_PROBE_NUM**: определяет количество отправленных проб ARP, позволяющее определить, используется ли другим узлом IP-адрес, назначенный DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="3ba52-244">**NX_DHCP_ARP_PROBE_NUM**: Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="3ba52-245">Значение по умолчанию — 3 пробы.</span><span class="sxs-lookup"><span data-stu-id="3ba52-245">The value is defaulted to 3 probes.</span></span>
- <span data-ttu-id="3ba52-246">**NX_DHCP_RESTART_WAIT**: определяет период времени, в течение которого DHCP-клиент ожидает перезапуска протокола DHCP, если IP-адрес, назначенный этому DHCP-клиенту, уже используется.</span><span class="sxs-lookup"><span data-stu-id="3ba52-246">**NX_DHCP_RESTART_WAIT**: Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="3ba52-247">Значение по умолчанию — 10 секунд.</span><span class="sxs-lookup"><span data-stu-id="3ba52-247">The value is defaulted to 10 seconds.</span></span>
- <span data-ttu-id="3ba52-248">**NX_DHCP_CLIENT_MAX_RECORDS**: указывает максимальное число записей интерфейсов, сохраняемых в экземпляре DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-248">**NX_DHCP_CLIENT_MAX_RECORDS**: Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="3ba52-249">Запись интерфейса DHCP-клиента — это запись о DHCP-клиенте, запущенном на определенном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="3ba52-249">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="3ba52-250">Значение по умолчанию равно количеству физических интерфейсов (NX_MAX_PHYSICAL_INTERFACES).</span><span class="sxs-lookup"><span data-stu-id="3ba52-250">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>
- <span data-ttu-id="3ba52-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: если этот параметр определен, он позволяет DHCP-клиенту передавать максимальный размер сообщения DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-251">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="3ba52-252">Этот параметр по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="3ba52-252">By default, this option is disabled.</span></span>
- <span data-ttu-id="3ba52-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: если этот параметр определен, он позволяет DHCP-клиенту проверять входное имя узла в вызове nx_dhcp_create на допустимость символов и длины.</span><span class="sxs-lookup"><span data-stu-id="3ba52-253">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="3ba52-254">Этот параметр по умолчанию отключен.</span><span class="sxs-lookup"><span data-stu-id="3ba52-254">By default, this option is disabled.</span></span>
- <span data-ttu-id="3ba52-255">**NX_DHCP_THREAD_PRIORITY**: приоритет потока DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-255">**NX_DHCP_THREAD_PRIORITY**: Priority of the DHCP thread.</span></span> <span data-ttu-id="3ba52-256">По умолчанию поток DHCP выполняется с приоритетом 3.</span><span class="sxs-lookup"><span data-stu-id="3ba52-256">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>
- <span data-ttu-id="3ba52-257">**NX_DHCP_THREAD_STACK_SIZE**: размер стека потоков DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-257">**NX_DHCP_THREAD_STACK_SIZE**: Size of the DHCP thread stack.</span></span> <span data-ttu-id="3ba52-258">По умолчанию размер составляет 2048 байт.</span><span class="sxs-lookup"><span data-stu-id="3ba52-258">By default, the size is 2048 bytes.</span></span>
- <span data-ttu-id="3ba52-259">**NX_DHCP_TIME_INTERVAL**: интервал в секундах, по истечении которого выполняется функция истечения срока действия таймера DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-259">**NX_DHCP_TIME_INTERVAL**: Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="3ba52-260">Эта функция обновляет все значения времени ожидания в операциях DHCP (например, если сообщения должны быть перенаправлены или изменилось состояние DHCP-клиента).</span><span class="sxs-lookup"><span data-stu-id="3ba52-260">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="3ba52-261">По умолчанию это значение равно 1 секунде.</span><span class="sxs-lookup"><span data-stu-id="3ba52-261">By default, this value is 1 second.</span></span>
- <span data-ttu-id="3ba52-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: размер буфера параметров DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-262">**NX_DHCP_OPTIONS_BUFFER_SIZE**: Size of DHCP options buffer.</span></span> <span data-ttu-id="3ba52-263">Значение по умолчанию — 312 байт.</span><span class="sxs-lookup"><span data-stu-id="3ba52-263">By default, this value is 312 bytes.</span></span>
- <span data-ttu-id="3ba52-264">**NX_DHCP_PACKET_PAYLOAD**: задает размер полезных данных пакета DHCP-клиента в байтах.</span><span class="sxs-lookup"><span data-stu-id="3ba52-264">**NX_DHCP_PACKET_PAYLOAD**: Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="3ba52-265">Значение по умолчанию — NX_DHCP_MINIMUM_IP_DATAGRAM + размер физического заголовка.</span><span class="sxs-lookup"><span data-stu-id="3ba52-265">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="3ba52-266">Размером физического заголовка в проводных сетях обычно является размер кадра Ethernet.</span><span class="sxs-lookup"><span data-stu-id="3ba52-266">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>
- <span data-ttu-id="3ba52-267">**NX_DHCP_PACKET_POOL_SIZE**: задает размер пула пакетов DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="3ba52-267">**NX_DHCP_PACKET_POOL_SIZE**: Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="3ba52-268">Значение по умолчанию — 5 \* NX_DHCP_PACKET_PAYLOAD, которое обеспечит четыре пакета, а также место для внутренних служебных данных пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="3ba52-268">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>
- <span data-ttu-id="3ba52-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: задает минимальное время ожидания для получения ответа DHCP-сервера на сообщение клиента перед повторной передачей сообщения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-269">**NX_DHCP_MIN_RETRANS_TIMEOUT**: Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="3ba52-270">Значение по умолчанию — 4 секунды (рекомендация RFC 2131).</span><span class="sxs-lookup"><span data-stu-id="3ba52-270">The default value is the RFC 2131 recommended 4 seconds.</span></span>
- <span data-ttu-id="3ba52-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: задает максимальное время ожидания для получения ответа DHCP-сервера на сообщение клиента перед повторной передачей сообщения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-271">**NX_DHCP_MAX_RETRANS_TIMEOUT**: Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="3ba52-272">Значение по умолчанию — 64 секунды.</span><span class="sxs-lookup"><span data-stu-id="3ba52-272">The default value is 64 seconds.</span></span>
- <span data-ttu-id="3ba52-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: задает минимальное время ожидания для получения сообщения DHCP-сервера и отправки запроса на обновление после привязки DHCP-клиента к IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="3ba52-273">**NX_DHCP_MIN_RENEW_TIMEOUT**: Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="3ba52-274">Значение по умолчанию — 60 секунд.</span><span class="sxs-lookup"><span data-stu-id="3ba52-274">The default value is 60 seconds.</span></span> <span data-ttu-id="3ba52-275">Однако DHCP-клиент применяет значения срока действия продления и повторной привязки из сообщения DHCP-сервера, прежде чем использовать минимальное время ожидания продления, заданное по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3ba52-275">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>
- <span data-ttu-id="3ba52-276">**NX_DHCP_TYPE_OF_SERVICE**: тип службы, необходимый для UDP-запросов DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-276">**NX_DHCP_TYPE_OF_SERVICE**: Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="3ba52-277">По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="3ba52-277">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="3ba52-278">**NX_DHCP_FRAGMENT_OPTION**: включение фрагментирования для UDP-запросов DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-278">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="3ba52-279">По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование UDP в DHCP.</span><span class="sxs-lookup"><span data-stu-id="3ba52-279">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>
- <span data-ttu-id="3ba52-280">**NX_DHCP_TIME_TO_LIVE**: указывает число маршрутизаторов, которые может пройти этот пакет, прежде чем он будет удален.</span><span class="sxs-lookup"><span data-stu-id="3ba52-280">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="3ba52-281">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="3ba52-281">The default value is set to 0x80.</span></span>
- <span data-ttu-id="3ba52-282">**NX_DHCP_QUEUE_DEPTH**: указывает максимальное значение глубины очереди получения.</span><span class="sxs-lookup"><span data-stu-id="3ba52-282">**NX_DHCP_QUEUE_DEPTH**: Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="3ba52-283">Значение по умолчанию — 4.</span><span class="sxs-lookup"><span data-stu-id="3ba52-283">The default value is set to 4.</span></span>