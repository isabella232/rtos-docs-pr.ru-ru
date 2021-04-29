---
title: Глава 2. Установка и использование сервера ОСРВ Azure NetX DHCP
description: В этой главе рассматриваются разные вопросы, связанные с установкой, настройкой и использованием компонента сервера ОСРВ Azure NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 034a4d74c566fbfe94981a42b7e06e7f2ee79d25
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815247"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-dhcp-server"></a><span data-ttu-id="81052-103">Глава 2. Установка и использование сервера ОСРВ Azure NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-103">Chapter 2 - Installation and use of the Azure RTOS NetX DHCP Server</span></span>

<span data-ttu-id="81052-104">В этой главе рассматриваются разные вопросы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="81052-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="81052-105">Product Distribution</span></span>

<span data-ttu-id="81052-106">Сервер ОСРВ Azure NetX DHCP можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="81052-106">Azure RTOS NetX DHCP Server can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="81052-107">Этот пакет включает в себя два файла исходного кода и PDF-файл с этим документом:</span><span class="sxs-lookup"><span data-stu-id="81052-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="81052-108">**nx_dhcp_server.h**: файл заголовка для сервера NetX DHCP;</span><span class="sxs-lookup"><span data-stu-id="81052-108">**nx_dhcp_server.h**: Header file for NetX DHCP Server</span></span>
- <span data-ttu-id="81052-109">**nx_dhcp_server.c**: файл исходного кода C для сервера NetX DHCP;</span><span class="sxs-lookup"><span data-stu-id="81052-109">**nx_dhcp_server.c**: C Source file for NetX DHCP Server</span></span>
- <span data-ttu-id="81052-110">**nx_dhcp_server.pdf**: PDF-файл с описанием сервера NetX DHCP;</span><span class="sxs-lookup"><span data-stu-id="81052-110">**nx_dhcp_server.pdf**: PDF description of NetX DHCP Server</span></span>
- <span data-ttu-id="81052-111">**demo_netx_dhcp_server.c**: демонстрационный файл для сервера NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-111">**demo_netx_dhcp_server.c**: NetX DHCP Server demonstration</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="81052-112">Установка экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-112">DHCP Installation</span></span>

<span data-ttu-id="81052-113">Чтобы использовать сервер NetX DHCP, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен экземпляр NetX.</span><span class="sxs-lookup"><span data-stu-id="81052-113">In order to use NetX DHCP Server, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="81052-114">Например, если экземпляр NetX установлен в каталог *\threadx\arm7\green*, то файлы *nx_dhcp_server.h* и *nx_dhpc_server.c* следует скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="81052-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_dhcp_server.h* and *nx_dhpc_server.c* files should be copied into this directory.</span></span>

## <a name="using-netx-dhcp-server"></a><span data-ttu-id="81052-115">Использование сервера NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-115">Using NetX DHCP Server</span></span>

<span data-ttu-id="81052-116">Использовать сервер NetX DHCP просто.</span><span class="sxs-lookup"><span data-stu-id="81052-116">Using NetX DHCP Server is easy.</span></span> <span data-ttu-id="81052-117">В код приложения достаточно добавить файл *nx_dhcp_server.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="81052-117">Basically, the application code must include *nx_dhcp_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="81052-118">После добавления файла *nx_dhcp_server.h* код приложения сможет выполнять вызовы функций DHCP, описанных далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="81052-118">Once *nx_dhcp_server.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="81052-119">В приложение также следует включить файл *nx_dhcp_server.c* в процессе сборки.</span><span class="sxs-lookup"><span data-stu-id="81052-119">The application must also include *nx_dhcp_server.c* in the build process.</span></span> <span data-ttu-id="81052-120">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="81052-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="81052-121">Дополнительные сведения об использовании сервера NetX DHCP см. в следующих разделах: [Требования для использования сервера NetX DHCP](#requirements-of-the-netx-dhcp-server) и [Ограничения сервера NetX DHCP](#constraints-of-the-netx-dhcp-server).</span><span class="sxs-lookup"><span data-stu-id="81052-121">For more details on using NetX DHCP Server, see the following sections [Requirements of the NetX DHCPServer](#requirements-of-the-netx-dhcp-server) and [Constraints of the NetX DHCP Server](#constraints-of-the-netx-dhcp-server).</span></span>

> [!NOTE]
> <span data-ttu-id="81052-122">Так как протокол DHCP использует службы NetX UDP, перед использованием DHCP следует включить протокол UDP с помощью вызова *nx_udp_enable*.</span><span class="sxs-lookup"><span data-stu-id="81052-122">Since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

## <a name="requirements-of-the-netx-dhcp-server"></a><span data-ttu-id="81052-123">Требования для использования сервера NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-123">Requirements of the NetX DHCP Server</span></span>

<span data-ttu-id="81052-124">Для сервера NetX DHCP требуется порт сокета UDP, назначенный известному порту DHCP 67.</span><span class="sxs-lookup"><span data-stu-id="81052-124">The NetX DHCP Server requires a UDP socket port assigned to the well known DHCP port 67.</span></span> <span data-ttu-id="81052-125">Для создания DHCP-сервера приложение должно создать пул пакетов с полезной нагрузкой пакета не менее 548 байт плюс заголовки IP, UDP и Ethernet (всего 44 байт с буферами по 4 байта).</span><span class="sxs-lookup"><span data-stu-id="81052-125">To create the DHCP Server, the application must create a packet pool with packet payload at least 548 bytes plus IP, UDP and Ethernet headers (which total 44 bytes with 4 byte alignment).</span></span>

<span data-ttu-id="81052-126">Предполагается, что и сервер, и клиент используют параметры аппаратного адреса Ethernet:</span><span class="sxs-lookup"><span data-stu-id="81052-126">It is assumed that the Server and Client are both using Ethernet hardware address settings:</span></span>

- <span data-ttu-id="81052-127">**тип оборудования**: 1;</span><span class="sxs-lookup"><span data-stu-id="81052-127">**Hardware type**: 1</span></span>
- <span data-ttu-id="81052-128">**аппаратная длина**: 6;</span><span class="sxs-lookup"><span data-stu-id="81052-128">**Hardware length**: 6</span></span>
- <span data-ttu-id="81052-129">**прыжки**: 0.</span><span class="sxs-lookup"><span data-stu-id="81052-129">**Hops**: 0</span></span>

### <a name="multiple-client-sessions"></a><span data-ttu-id="81052-130">Несколько сеансов клиентов</span><span class="sxs-lookup"><span data-stu-id="81052-130">Multiple Client Sessions</span></span>

<span data-ttu-id="81052-131">Сервер NetX DHCP может обрабатывать несколько сеансов клиентов, ведя таблицу активных DHCP-клиентов и их состояний, например состояний DHCP INIT, BOOT, SELECTING, REQUESTING, RENEWING и т. д. Если время ожидания сеанса истекает до получения следующего сообщения от клиента, не привязанного к аренде IP-адреса, сервер очищает данные сеанса клиента и возвращает назначенный IP-адрес в пул.</span><span class="sxs-lookup"><span data-stu-id="81052-131">The NetX DHCP Server can handles multiple Client sessions by keeping a table of active DHCP clients and what 'state' the Client is in e.g. DHCP states INIT, BOOT, SELECTING, REQUESTING, RENEWING etc. If the session time out expires before receiving the next Client message, unless that Client is bound to an IP lease, the Server will clear the Client session data and return the assigned IP address back to the available pool.</span></span> <span data-ttu-id="81052-132">Если сервер получает несколько сообщений DISCOVER от одного клиента, он сбрасывает время ожидания сеанса и оставляет IP-адрес зарезервированным для этого клиента, чтобы его можно было принять в последующем сообщении REQUEST.</span><span class="sxs-lookup"><span data-stu-id="81052-132">If the Server receives multiple DISCOVER messages from the same Client the Server resets the session time out and keeps the IP address reserved for the Client to accept in a subsequent REQUEST message.</span></span>

<span data-ttu-id="81052-133">Сервер NetX DHCP также принимает от DHCP-клиента запрос на одно состояние, например клиент отправляет только сообщение REQUEST.</span><span class="sxs-lookup"><span data-stu-id="81052-133">The NetX DHCP Server also accepts the single state Client DHCP request e.g. the Client only sends a REQUEST message.</span></span> <span data-ttu-id="81052-134">При этом предполагается, что клиенту ранее была назначена аренда IP-адреса DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="81052-134">This assumes the Client has been previously assigned an IP lease from the DHCP server.</span></span>

### <a name="setting-interface-specific-network-parameters-server-responses"></a><span data-ttu-id="81052-135">Задание ответов сервера для параметров сети, относящихся к конкретному интерфейсу</span><span class="sxs-lookup"><span data-stu-id="81052-135">Setting Interface Specific Network Parameters Server Responses</span></span>

<span data-ttu-id="81052-136">Приложение может задать параметры маршрутизатора, маски подсети и DNS-сервера для каждого интерфейса, обрабатывающего запросы DHCP-клиентов, с помощью службы *nx_dhcp_set_interface_network_parameters*.</span><span class="sxs-lookup"><span data-stu-id="81052-136">The application can set the router, subnet mask and DNS server parameters for each interface it handles DHCP Client requests, using the *nx_dhcp_set_interface_network_parameters* service.</span></span> <span data-ttu-id="81052-137">В противном случае по умолчанию применяются IP-шлюз из основного интерфейса сервера, его подсеть сети DHCP и IP-адрес DHCP-сервера соответственно.</span><span class="sxs-lookup"><span data-stu-id="81052-137">Otherwise these parameters are defaulted to the IP gateway on the Server's primary interface, its DHCP network subnet, and DHCP Server IP address, respectively.</span></span>

<span data-ttu-id="81052-138">DHCP-сервер включает эти параметры в данные сообщений DHCP, которые он отправляет DHCP-клиентам.</span><span class="sxs-lookup"><span data-stu-id="81052-138">The DHCP Server includes these parameters in the option data of DHCP messages it sends to DHCP clients.</span></span>

### <a name="assigning-ip-addresses-to-the-client"></a><span data-ttu-id="81052-139">Назначение IP-адресов клиенту</span><span class="sxs-lookup"><span data-stu-id="81052-139">Assigning IP addresses to the Client</span></span>

<span data-ttu-id="81052-140">Если в сообщении DISCOVER клиента не указан запрашиваемый IP-адрес, DHCP-сервер может использовать адрес из собственного пула.</span><span class="sxs-lookup"><span data-stu-id="81052-140">If the Client DISCOVER message does not specify a requested IP address, the DHCP Server can use one from its own pool.</span></span> <span data-ttu-id="81052-141">Если у сервера нет доступных IP-адресов, он отправит клиенту сообщение NACK.</span><span class="sxs-lookup"><span data-stu-id="81052-141">If the Server has no available IP addresses it will send the Client a NACK message.</span></span>

<span data-ttu-id="81052-142">Сервер NetX DHCP предоставит IP-адрес, запрошенный в сообщении REQUEST клиента, если этот адрес доступен и найден в базе данных IP-адресов сервера.</span><span class="sxs-lookup"><span data-stu-id="81052-142">The NetX DHCP Server will grant the requested IP address in the Client REQUEST message as long as the IP address is available and can be found in the Server IP address database.</span></span> <span data-ttu-id="81052-143">Приложение создает список доступных IP-адресов сервера для назначения DHCP-клиентам с помощью службы *nx_dhcp_create_server_ip_address_list*.</span><span class="sxs-lookup"><span data-stu-id="81052-143">The application creates the Server's list of available IP addresses for assigning to DHCP Clients using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="81052-144">Если у сервера нет запрошенного IP-адреса или он назначен другому узлу, клиенту отправляется сообщение NACK.</span><span class="sxs-lookup"><span data-stu-id="81052-144">If the Server does not have the requested IP addresses or it is assigned to another host it will send the Client a NACK message.</span></span>

<span data-ttu-id="81052-145">Когда DHCP-сервер получает запрос клиента, он однозначно идентифицирует клиент по его MAC-адресу в соответствующем поле в сообщении DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-145">When the DHCP Server receives a Client request, it identifies that Client uniquely using the Client MAC address in the Client MAC address field in the DHCP message.</span></span> <span data-ttu-id="81052-146">Если MAC-адрес клиента изменяется или клиент перемещается в другую подсеть, он должен отправить на сервер сообщение RELEASE, чтобы вернуть IP-адрес в пул доступных адресов и запросить новый IP-адрес в состоянии INIT.</span><span class="sxs-lookup"><span data-stu-id="81052-146">If the Client changes it's MAC address or is moved elsewhere onto another subnet it should send a RELEASE message to the Server to return the IP address back to the available pool, and request a new IP address in the INIT state.</span></span>

<span data-ttu-id="81052-147">Дополнительные сведения приведены на рисунке 1.1 в разделе **Пример небольшой системы**.</span><span class="sxs-lookup"><span data-stu-id="81052-147">See Figure 1.1 of the **Small Example System** section for details.</span></span> <span data-ttu-id="81052-148">Количество IP-адресов, сохраняемых в экземпляре DHCP-сервера, ограничено размером массива адресов сервера в блоке управления DHCP-сервером и определяется настраиваемым параметром NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span><span class="sxs-lookup"><span data-stu-id="81052-148">The number of IP addresses saved to the DHCP Server instance is limited to the size of the server address array in the DHCP Server control block, and defined by the configurable option NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE.</span></span>

### <a name="ip-address-lease-times"></a><span data-ttu-id="81052-149">Сроки аренды IP-адресов</span><span class="sxs-lookup"><span data-stu-id="81052-149">IP Address Lease Times</span></span>

<span data-ttu-id="81052-150">DHCP-сервер также принимает срок аренды в запросе клиента, если этот срок меньше срока аренды по умолчанию для сервера, определенного в настраиваемом параметре NX_DHCP_DEFAULT_LEASE_TIME.</span><span class="sxs-lookup"><span data-stu-id="81052-150">The DHCP Server will also accept the request Client lease time if that lease time is less than the Server default lease time which is defined in configurable option NX_DHCP_DEFAULT_LEASE_TIME.</span></span> <span data-ttu-id="81052-151">Сроки продления и повторной привязки, назначенные клиенту, составляют 50 % и 85 % от срока аренды соответственно, если только аренда не бессрочная (0xFFFFFFFF). В этом случае сроки продления и повторной привязки также бесконечны.</span><span class="sxs-lookup"><span data-stu-id="81052-151">Renewal and rebind times assigned to the Client are 50% and 85% of the lease time, respectively, unless the lease time is infinity (0xFFFFFFFF), in which case renewal and rebind times are also set to infinity.</span></span>

### <a name="dhcp-server-timeouts"></a><span data-ttu-id="81052-152">Время ожидания DHCP-сервера</span><span class="sxs-lookup"><span data-stu-id="81052-152">DHCP Server Timeouts</span></span>

<span data-ttu-id="81052-153">У DHCP-сервера есть настраиваемое пользователем время ожидания сеанса NX_DHCP_CLIENT_SESSION_TIMEOUT. Оно определяет то, как долго следует ожидать следующего сообщения от DHCP-клиента, пока сеанс не будет завершен.</span><span class="sxs-lookup"><span data-stu-id="81052-153">The DHCP Server has a user configurable session timeout, NX_DHCP_CLIENT_SESSION_TIMEOUT, for waiting for the next DHCP Client message unless the session is completed.</span></span> <span data-ttu-id="81052-154">Время ожидания сбрасывается, когда сервер получает следующее сообщение от клиента, независимо от того, совпадает ли это сообщение с предыдущим.</span><span class="sxs-lookup"><span data-stu-id="81052-154">The time out is reset when the Server receives the next message from the Client regardless if is the same message previously sent.</span></span>

### <a name="internal-error-handling"></a><span data-ttu-id="81052-155">Обработка внутренних ошибок</span><span class="sxs-lookup"><span data-stu-id="81052-155">Internal error handling</span></span>

<span data-ttu-id="81052-156">DHCP-сервер получает и обрабатывает пакеты DHCP-клиента в функции *nx_dhcp_listen_for_messages*.</span><span class="sxs-lookup"><span data-stu-id="81052-156">The DHCP Server receives and processes DHCP Client packets in the *nx_dhcp_listen_for_messages* function.</span></span> <span data-ttu-id="81052-157">Эта функция прекращает обработку текущего пакета DHCP-клиента, если он является недопустимым или DHCP-сервер обнаружил внутреннюю ошибку. Функция *nx_dhcp_listen_for_messages* возвращает состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="81052-157">This function will discontinue processing the current DHCP Client packet if the packet is invalid, or the DHCP Server encounters an internal error.n *x_dhcp_listen_for_messages* returns an error status.</span></span> <span data-ttu-id="81052-158">Поток DHCP-сервера ненадолго отдает управление планировщиком ThreadX перед вызовом этой функции для получения следующего сообщения от DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="81052-158">The DHCP Server thread relinquishes control briefly of the ThreadX scheduler before calling this function to receive the next DHCP Client message.</span></span> <span data-ttu-id="81052-159">В текущем выпуске ведение журнала ошибок, возвращаемых функцией *nx_dhcp_listen_for_messages*, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="81052-159">In the current release there is no logging support for error status returns from *nx_dhcp_listen_for_messages.*</span></span>

### <a name="option-55-parameter-request-list"></a><span data-ttu-id="81052-160">Параметр 55: список запросов параметров</span><span class="sxs-lookup"><span data-stu-id="81052-160">Option 55: Parameter Request List</span></span>

<span data-ttu-id="81052-161">На сервере NetX DHCP необходимо настроить набор параметров для загрузки в список запросов параметров (55) в сообщениях OFFER и DHCPACK, которые он передает обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="81052-161">The NetX DHCP Server must be configured with a set of options to load to Parameter Request Option (55) list in the OFFER and DHCPACK messages it transmits back to the Client.</span></span> <span data-ttu-id="81052-162">Эти параметры должны включать в себя критически важные данные о конфигурации сети клиента. По умолчанию в их число входят IP-адрес маршрутизатора, маска подсети и DNS-сервер.</span><span class="sxs-lookup"><span data-stu-id="81052-162">These options should include network critical configuration data for the Client network and by default is defined to be router IP address, subnet mask, and DNS server.</span></span> <span data-ttu-id="81052-163">Список параметров разделяется пробелами и определяется в настраиваемом пользователем параметре NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span><span class="sxs-lookup"><span data-stu-id="81052-163">The option list is a space delimited list and defined in the user configurable NX_DHCP_DEFAULT_SERVER_OPTION_LIST.</span></span> <span data-ttu-id="81052-164">Обратите внимание на то, что число параметров в этом списке должно быть равно значению NX_DHCP_DEFAULT_OPTION_LIST_SIZE, которое также задается пользователем.</span><span class="sxs-lookup"><span data-stu-id="81052-164">Note the number of options specified in this list must equal NX_DHCP_DEFAULT_OPTION_LIST_SIZE which is also user defined.</span></span>

## <a name="constraints-of-the-netx-dhcp-server"></a><span data-ttu-id="81052-165">Ограничения сервера NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-165">Constraints of the NetX DHCP Server</span></span>

### <a name="dhcp-messages"></a><span data-ttu-id="81052-166">Сообщения DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-166">DHCP Messages</span></span>

<span data-ttu-id="81052-167">Сервер NetX DHCP не проверяет, назначен ли IP-адрес где-то еще в сети, прежде чем предоставлять его клиенту.</span><span class="sxs-lookup"><span data-stu-id="81052-167">The NetX DHCP Server does not verify that an IP address has not been assigned elsewhere on the network before granting the IP address to the Client.</span></span> <span data-ttu-id="81052-168">Если DHCP-серверов несколько, такая ситуация возможна.</span><span class="sxs-lookup"><span data-stu-id="81052-168">If there are multiple DHCP servers, this can indeed be the case.</span></span> <span data-ttu-id="81052-169">*Согласно спецификации RFC 2131, за проверку уникальности IP-адреса в сети отвечает клиент* (например, посредством проверки связи).</span><span class="sxs-lookup"><span data-stu-id="81052-169">*As per RFC 2131, it is the Client's responsibility to verify the IP address is unique on its network* (e.g. pinging the address).</span></span> <span data-ttu-id="81052-170">Если IP-адрес не уникален, сервер должен получить от клиента сообщение DECLINE с этим IP-адресом и обновить свою базу данных.</span><span class="sxs-lookup"><span data-stu-id="81052-170">If it is not, the Server should receive a DECLINE message with the IP address to update its database from the Client.</span></span>

<span data-ttu-id="81052-171">Сервер NetX DHCP не выдает сообщения FORCE_RENEW.</span><span class="sxs-lookup"><span data-stu-id="81052-171">The NetX DHCP Server does not issue FORCE_RENEW messages.</span></span> <span data-ttu-id="81052-172">Продлевать аренду IP-адреса должен сам DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="81052-172">It is up to the DHCP Client to renew its IP address lease.</span></span> <span data-ttu-id="81052-173">Однако DHCP-сервер отслеживает оставшийся срок действия всех назначенных IP-адресов в своей базе данных.</span><span class="sxs-lookup"><span data-stu-id="81052-173">However, the DHCP Server monitors the time remaining on all the assigned IP addresses in its database.</span></span> <span data-ttu-id="81052-174">Когда срок аренды IP-адреса истекает, он возвращается в пул доступных IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="81052-174">When an IP address lease expires, that IP address is returned to the pool of available IP addresses.</span></span> <span data-ttu-id="81052-175">Поэтому клиент должен самостоятельно продлевать или повторно привязывать аренду IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="81052-175">Hence it is up to the Client to actively renew/rebind its IP address lease.</span></span>

<span data-ttu-id="81052-176">Данные сеанса очищаются, как только клиенту предоставляется ("привязывается") аренда IP-адреса (или продлевается существующая аренда).</span><span class="sxs-lookup"><span data-stu-id="81052-176">Session data is cleared as soon as the Client either is granted ("bound") to an IP lease (or an existing one is renewed).</span></span> <span data-ttu-id="81052-177">Они также очищаются, если клиентский пакет оказывается поддельным или истекает время ожидания ответа клиентом.</span><span class="sxs-lookup"><span data-stu-id="81052-177">If a Client packet proves bogus, or the Client times out between responses, session data is cleared.</span></span>

### <a name="saving-data-between-reboots"></a><span data-ttu-id="81052-178">Сохранение данных после перезагрузки</span><span class="sxs-lookup"><span data-stu-id="81052-178">Saving Data Between Reboots</span></span>

<span data-ttu-id="81052-179">Сервер NetX DHCP сохраняет данные клиента, включая параметры запроса DHCP, в таблице записей клиента.</span><span class="sxs-lookup"><span data-stu-id="81052-179">The NetX DHCP Server saves Client data including DHCP request parameters in a Client record table.</span></span> <span data-ttu-id="81052-180">Она не сохраняется в энергонезависимой памяти, поэтому, если узел DHCP-сервера должен перезагрузиться, эта информация утрачивается.</span><span class="sxs-lookup"><span data-stu-id="81052-180">This table is not stored in non volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

<span data-ttu-id="81052-181">Сервер NetX DHCP сохраняет данные по аренде IP-адресов в таблице IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="81052-181">The NetX DHCP Server saves IP address lease data in a IP address table.</span></span> <span data-ttu-id="81052-182">Она не сохраняется в энергонезависимой памяти, поэтому, если узел DHCP-сервера должен перезагрузиться, эта информация утрачивается.</span><span class="sxs-lookup"><span data-stu-id="81052-182">This table is not stored in non volatile memory, so if the DHCP Server host must reboot that information is not saved between reboots.</span></span>

### <a name="relay-agents"></a><span data-ttu-id="81052-183">Агенты ретрансляции</span><span class="sxs-lookup"><span data-stu-id="81052-183">Relay Agents</span></span>

<span data-ttu-id="81052-184">В поле "Relay agent" (Агент ретрансляции) сервера NetX DHCP содержится нулевой IP-адрес, так как DHCP-сервер не поддерживает запросы DHCP вне сети.</span><span class="sxs-lookup"><span data-stu-id="81052-184">The NetX DHCP Server is configured with a zero IP address for the 'Relay agent' field because it does not support out of network DHCP requests.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="81052-185">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="81052-185">Small Example System</span></span>

<span data-ttu-id="81052-186">Пример того, насколько просто использовать сервер NetX DHCP, приведен на рисунке 1.1 ниже.</span><span class="sxs-lookup"><span data-stu-id="81052-186">An example of how easy it is to use the NetX DHCP Server is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="81052-187">В этом примере файл DHCP *nx_dhcp_server.h* включается в строке 5.</span><span class="sxs-lookup"><span data-stu-id="81052-187">In this example, the DHCP include file *nx_dhcp_server.h* is brought in at line 5.</span></span> <span data-ttu-id="81052-188">Размер стека потоков DHCP-сервера, размер стека потоков IP и размер стека тестового потока определяются в строках 7–13.</span><span class="sxs-lookup"><span data-stu-id="81052-188">DHCP Server thread stack size, IP thread stack size and test thread stack size are all defined in lines 7-13.</span></span>

<span data-ttu-id="81052-189">Сначала создается необязательная задача тестового потока для остановки, перезапуска и окончательного удаления DHCP-сервера с помощью функции *test_thread_entry* в строке 57.</span><span class="sxs-lookup"><span data-stu-id="81052-189">First, an optional test thread task for stopping, restarting and eventually deleting the DHCP server is created with the "*test_thread_entry*" function at line 57.</span></span> <span data-ttu-id="81052-190">Блок управления DHCP-сервером *dhcp_server* определяется как глобальная переменная в строке 20.</span><span class="sxs-lookup"><span data-stu-id="81052-190">A DHCP Server control block "*dhcp_server*" is defined as a global variable at line 20.</span></span> <span data-ttu-id="81052-191">Обратите внимание на то, что размер полезных данных пакета в пуле пакетов сервера не меньше размера стандартного сообщения DHCP (548 байт плюс байты заголовков IP и UDP).</span><span class="sxs-lookup"><span data-stu-id="81052-191">Note that the server packet pool is created with packets having a payload at least as large as the standard DHCP message (548 bytes plus IP and UDP header bytes).</span></span> <span data-ttu-id="81052-192">После успешного создания экземпляра IP для DHCP-сервера приложение создает DHCP-сервер в строке 96.</span><span class="sxs-lookup"><span data-stu-id="81052-192">After successfully creating an IP instance for the DHCP Server, the application creates the DHCP Server in line 96.</span></span> <span data-ttu-id="81052-193">Затем приложение включает поддержку протокола UDP для экземпляра IP сервера.</span><span class="sxs-lookup"><span data-stu-id="81052-193">Next, the application enables the Server IP instance to be UDP enabled.</span></span> <span data-ttu-id="81052-194">Перед запуском DHCP-сервера создается список доступных IP-адресов в строке 137 с помощью службы *nx_dhcp_create_server_ip_address_list*.</span><span class="sxs-lookup"><span data-stu-id="81052-194">Before starting the DHCP Server, the available IP address list is created in line 137 using the *nx_dhcp_create_server_ip_address_list* service.</span></span> <span data-ttu-id="81052-195">Параметры конфигурации сети задаются в строке 138 с помощью службы *nx_dhcp_set_interface_network_parameters*. Службы DHCP-сервера становятся доступными, когда приложение вызывает *nx_dhcp_server_start* в строке 141.</span><span class="sxs-lookup"><span data-stu-id="81052-195">The network configuration parameters are set in the following line 138 using the *nx_dhcp_set_interface_network_parameters* service, DHCP Server services become available when the application calls the *nx_dhcp_server_start* at line 141.</span></span> <span data-ttu-id="81052-196">Задача тестового потока демонстрирует остановку и перезапуск DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="81052-196">The test thread task demonstrates the use of stopping and restarting the DHCP server.</span></span>

```c
/* This is a small demo of NetX DHCP Server for the high-performance NetX TCP/IP stack. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_dhcp_server.h"

#define     DEMO_TEST_STACK_SIZE       2048
#define     DEMO_SERVER_STACK_SIZE     2048
#define     SERVER_IP_ADDRESS_LIST     "192.168.2.10 192.168.2.11 192.168.2.12"
#define     PACKET_PAYLOAD             1000
#define     PACKET_POOL_SIZE           (PACKET_PAYLOAD * 10)
#define     SERVER_IP_THREAD_STACK     2048

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD          test_thread;
NX_PACKET_POOL     server_pool;
NX_IP              server_ip;
NX_DHCP_SERVER     dhcp_server;

/* Define the counters used in the demo application... */

ULONG             state_changes;

/* Define thread prototypes. */

void     test_thread_entry(ULONG thread_input);
void     nx_etherDriver_mcf5485(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
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

    /* Create the test thread. */
    status = tx_thread_create(&test_thread, "test thread", test_thread_entry, 0,
                pointer, TEST_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_DONT_START);

    if (status)
    {
        printf("Error with DHCP test thread create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create the DHCP Server packet pool. */
    status = nx_packet_pool_create(&server_pool, "NetX Main Packet Pool",
                                PACKET_PAYLOAD, pointer, PACKET_POOL_SIZE);
                                pointer = pointer + PACKET_POOL_SIZE;

    /* Check for pool creation error. */
    if (status)
    {
        printf("Error with DHCP server packet pool create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server IP instance. */
    status = nx_ip_create(&server_ip, "NetX DHCP Server IP", NX_DHCP_SERVER_IP_ADDRESS,
                        0xFFFFFF00UL, &server_pool, nx_etherDriver_mcf5485, pointer,
                        SERVER_IP_THREAD_STACK, 1);

    pointer = pointer + DEMO_IP_THREAD_STACK;

    /* Check for IP create errors. */
    if (status)
    {
        printf("Error with DHCP server IP task create. Status 0x%x\r\n", status);
        return;
    }

    /* Create the DHCP Server instance. */
    status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE,"DHCP Server", &server_pool);

    if (status)
    {
        printf("Error with DHCP server create. Status 0x%x\r\n", status);
        return;
    }

    pointer = pointer + DEMO_SERVER_STACK_SIZE;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
    {
        printf("Error with ARP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable UDP traffic. */
    status = nx_udp_enable(&server_ip);

    /* Check for UDP enable errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
        return;
    }

    /* Enable ICMP to enable the ping utility. */
    status = nx_icmp_enable(&server_ip);

    /* Check for errors. */
    if (status)
    {
        printf("Error with ICMP enable. Status 0x%x\r\n", status);
    }

    status = nx_dhcp_create_server_ip_address_list(&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);
    status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                        NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                        IP_ADDRESS(10,0,0,1));

    /* Start the DHCP Server. */
    status = nx_dhcp_server_start(&dhcp_server);

    tx_thread_resume(&test_thread);
}

/* Define the test thread. */
void     test_thread_entry(ULONG thread_input)
{

UINT     status;
UINT     keep_spinning;

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
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
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
        printf("Error with DHPC server stop. Status 0x%x\r\n", status);
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

<span data-ttu-id="81052-197">Рисунок 1.1. Пример серверного приложения NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="81052-197">Figure 1.1 Example NetX DHCP Server application</span></span>

## <a name="configuration-options"></a><span data-ttu-id="81052-198">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="81052-198">Configuration Options</span></span>

<span data-ttu-id="81052-199">Существует ряд параметров конфигурации для сборки сервера NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-199">There are several configuration options for building NetX DHCP Server.</span></span> <span data-ttu-id="81052-200">Их подробное описание приведено ниже.</span><span class="sxs-lookup"><span data-stu-id="81052-200">The following list describes each in detail:</span></span>  
  
- <span data-ttu-id="81052-201">**NX_DISABLE_ERROR_CHECKING**: этот параметр отключает базовую проверку на ошибки DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-201">**NX_DISABLE_ERROR_CHECKING**: This option removes the basic DHCP error checking.</span></span> <span data-ttu-id="81052-202">Обычно он используется после отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="81052-202">It is typically used after the application is debugged.</span></span>  
- <span data-ttu-id="81052-203">**NX_DHCP_SERVER_THREAD_PRIORITY**: этот параметр задает приоритет для потока DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="81052-203">**NX_DHCP_SERVER_THREAD_PRIORITY**: This option specifies the priority of the DHCP Server thread.</span></span> <span data-ttu-id="81052-204">По умолчанию поток DHCP выполняется с приоритетом 2.</span><span class="sxs-lookup"><span data-stu-id="81052-204">By default, this value specifies that the DHCP thread runs at priority 2.</span></span>
- <span data-ttu-id="81052-205">**NX_DHCP_TYPE_OF_SERVICE**: этот параметр определяет тип службы, необходимой для UDP-запросов DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-205">**NX_DHCP_TYPE_OF_SERVICE**: This option specifies the type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="81052-206">По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="81052-206">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="81052-207">**NX_DHCP_FRAGMENT_OPTION**: включение фрагментирования для UDP-запросов DHCP.</span><span class="sxs-lookup"><span data-stu-id="81052-207">**NX_DHCP_FRAGMENT_OPTION**: Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="81052-208">По умолчанию этот параметр имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование UDP.</span><span class="sxs-lookup"><span data-stu-id="81052-208">By default, this value is set to NX_DONT_FRAGMENT to disable UDP fragmenting.</span></span>
- <span data-ttu-id="81052-209">**NX_DHCP_TIME_TO_LIVE**: указывает число маршрутизаторов, через которые может пройти пакет, прежде чем он будет удален.</span><span class="sxs-lookup"><span data-stu-id="81052-209">**NX_DHCP_TIME_TO_LIVE**: Specifies the number of routers the packet can pass before it is discarded.</span></span> <span data-ttu-id="81052-210">Значение по умолчанию — 0x80.</span><span class="sxs-lookup"><span data-stu-id="81052-210">The default value is 0x80.</span></span>
- <span data-ttu-id="81052-211">**NX_DHCP_QUEUE_DEPTH**: указывает число пакетов, которые сохраняет сокет DHCP-сервера перед освобождением очереди.</span><span class="sxs-lookup"><span data-stu-id="81052-211">**NX_DHCP_QUEUE_DEPTH** Specifies the number of packets that the DHCP Server socket keeps before flushing the queue.</span></span> <span data-ttu-id="81052-212">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="81052-212">The default value is 5.</span></span>
- <span data-ttu-id="81052-213">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: указывает время ожидания выделения пакета из пула пакетов сервера NetX DHCP в тактах таймера.</span><span class="sxs-lookup"><span data-stu-id="81052-213">**NX_DHCP_PACKET_ALLOCATE_TIMEOUT**: Specifies the timeout in timer ticks for the NetX DHCP Server to wait for allocate a packet from its packet pool.</span></span> <span data-ttu-id="81052-214">Значение по умолчанию — NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="81052-214">The default value is set to NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="81052-215">**NX_DHCP_SUBNET_MASK**: маска подсети, которая должна быть настроена для DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="81052-215">**NX_DHCP_SUBNET_MASK**: This is the subnet mask the DHCP Client should be configured with.</span></span> <span data-ttu-id="81052-216">Значение по умолчанию — 0xFFFFFF00.</span><span class="sxs-lookup"><span data-stu-id="81052-216">The default value is set to 0xFFFFFF00.</span></span>
- <span data-ttu-id="81052-217">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: время ожидания в тактах таймера, используемое быстрым таймером DHCP-сервера при проверке оставшегося времени сеанса и обработки истекших сеансов.</span><span class="sxs-lookup"><span data-stu-id="81052-217">**NX_DHCP_FAST_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server fast timer to check on session time remaining and handle sessions that have timed out.</span></span>
- <span data-ttu-id="81052-218">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: время ожидания в тактах таймера, используемое медленным таймером DHCP-сервера при проверке оставшегося срока аренды IP-адреса и обработки истекшей аренды.</span><span class="sxs-lookup"><span data-stu-id="81052-218">**NX_DHCP_SLOW_PERIODIC_TIME_INTERVAL**: This is timeout period in timer ticks for the DHCP Server slow timer to check on IP address lease time remaining and handle lease that have timed out.</span></span>
- <span data-ttu-id="81052-219">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: время ожидания получения DHCP-сервером следующего сообщения от DHCP-клиента в тактах таймера.</span><span class="sxs-lookup"><span data-stu-id="81052-219">**NX_DHCP_CLIENT_SESSION_TIMEOUT**: This is timeout period in timer ticks the DHCP Server will wait to receive the next DHCP Client message.</span></span>
- <span data-ttu-id="81052-220">**NX_DHCP_DEFAULT_LEASE_TIME**: срок аренды IP-адреса, назначенной DHCP-клиенту, в секундах. Служит основой для вычисления сроков продления и повторной привязки для клиента.</span><span class="sxs-lookup"><span data-stu-id="81052-220">**NX_DHCP_DEFAULT_LEASE_TIME**: This is IP Address lease time in seconds assigned to the DHCP Client, and the basis for computing the renewal and rebind times also assigned to the Client.</span></span> <span data-ttu-id="81052-221">Значение по умолчанию — 0xFFFFFFFF (бесконечность).</span><span class="sxs-lookup"><span data-stu-id="81052-221">The default value is set to 0xFFFFFFFF (infinity).</span></span>
- <span data-ttu-id="81052-222">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: размер массива DHCP-сервера для хранения доступных IP-адресов, которые можно назначить клиенту.</span><span class="sxs-lookup"><span data-stu-id="81052-222">**NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE**: This is size of the DHCP Server array for holding available IP addresses for assigning to the Client.</span></span> <span data-ttu-id="81052-223">Значение по умолчанию — 20.</span><span class="sxs-lookup"><span data-stu-id="81052-223">The default value is 20.</span></span>
- <span data-ttu-id="81052-224">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: размер массива DHCP-сервера для хранения записей клиентов.</span><span class="sxs-lookup"><span data-stu-id="81052-224">**NX_DHCP_CLIENT_RECORD_TABLE_SIZE**: This is size of the DHCP Server array for holding Client records.</span></span> <span data-ttu-id="81052-225">Значение по умолчанию — 50.</span><span class="sxs-lookup"><span data-stu-id="81052-225">The default value is 50.</span></span>
- <span data-ttu-id="81052-226">**NX_DHCP_CLIENT_OPTIONS_MAX**: размер массива в экземпляре DHCP-клиента для сохранения всех параметров, запрошенных в текущем сеансе, в списке запросов параметров.</span><span class="sxs-lookup"><span data-stu-id="81052-226">**NX_DHCP_CLIENT_OPTIONS_MAX**: This is size of the array in the DHCP Client instance for holding the all the requested options in the parameter request list in the current session.</span></span> <span data-ttu-id="81052-227">Значение по умолчанию — 12.</span><span class="sxs-lookup"><span data-stu-id="81052-227">The default value is 12.</span></span>
- <span data-ttu-id="81052-228">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: буфер, который содержит список параметров DHCP-сервера по умолчанию, предоставляемых текущему DHCP-клиенту в списке запросов параметров.</span><span class="sxs-lookup"><span data-stu-id="81052-228">**NX_DHCP_OPTIONAL_SERVER_OPTION_LIST**: This is the buffer holding the DHCP Server's default list of options to supply to the current DHCP Client in the parameter request list.</span></span> <span data-ttu-id="81052-229">Значение по умолчанию — 1 3 6.</span><span class="sxs-lookup"><span data-stu-id="81052-229">The default is "1 3 6."</span></span>
- <span data-ttu-id="81052-230">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: размер массива, в котором хранится список параметров DHCP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="81052-230">**NX_DHCP_OPTIONAL_SERVER_OPTION_SIZE**: This is the size of the array to hold the DHCP Server's default list of options.</span></span> <span data-ttu-id="81052-231">Значение по умолчанию равно 3.</span><span class="sxs-lookup"><span data-stu-id="81052-231">The default value is 3.</span></span>
- <span data-ttu-id="81052-232">**NX_DHCP_SERVER_HOSTNAME_MAX**: размер буфера для хранения имени узла сервера.</span><span class="sxs-lookup"><span data-stu-id="81052-232">**NX_DHCP_SERVER_HOSTNAME_MAX**: This is size of the buffer for holding the Server host name.</span></span> <span data-ttu-id="81052-233">Значение по умолчанию: 32.</span><span class="sxs-lookup"><span data-stu-id="81052-233">The default value is 32.</span></span>
- <span data-ttu-id="81052-234">**NX_DHCP_CLIENT_HOSTNAME_MAX**: размер буфера для хранения имени узла клиента в течение текущего сеанса клиента DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="81052-234">**NX_DHCP_CLIENT_HOSTNAME_MAX**: This is size of the buffer for holding the Client host name in the current DHCP Server Client session.</span></span> <span data-ttu-id="81052-235">Значение по умолчанию: 32.</span><span class="sxs-lookup"><span data-stu-id="81052-235">The default value is 32.</span></span>
