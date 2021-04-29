---
title: Глава 2. Установка и использование ОСРВ Azure NetX Duo BSD
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814823"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="63156-103">Глава 2. Установка и использование ОСРВ Azure NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="63156-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="63156-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="63156-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="63156-105">Product Distribution</span></span>

<span data-ttu-id="63156-106">ОСРВ Azure NetX BSD можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="63156-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="63156-107">Этот пакет включает в себя два файла исходного кода и PDF-файл с этим документом:</span><span class="sxs-lookup"><span data-stu-id="63156-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="63156-108">**nxd_bsd.h**: файл заголовка для NetX Duo BSD;</span><span class="sxs-lookup"><span data-stu-id="63156-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="63156-109">**nxd_bsd.c**: файл исходного кода C для NetX Duo BSD;</span><span class="sxs-lookup"><span data-stu-id="63156-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="63156-110">**nxd_bsd.pdf**: PDF-файл с описанием NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="63156-111">Демонстрационные файлы:</span><span class="sxs-lookup"><span data-stu-id="63156-111">Demo files:</span></span>

- <span data-ttu-id="63156-112">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="63156-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="63156-113">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="63156-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="63156-114">**bsd_demo_raw.c**</span><span class="sxs-lookup"><span data-stu-id="63156-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="63156-115">Установка NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="63156-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="63156-116">Чтобы использовать NetX Duo BSD, весь дистрибутив, упомянутый ранее, необходимо скопировать в каталог, где установлен экземпляр NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="63156-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="63156-117">Например, если экземпляр NetX Duo установлен в каталог *\threadx\arm7\green*, то файлы *nxd_bsd.h* и *nxd_bsd.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="63156-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="63156-118">Создание компонентов ThreadX и NetX Duo приложения BSD</span><span class="sxs-lookup"><span data-stu-id="63156-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="63156-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="63156-119">ThreadX</span></span>

<span data-ttu-id="63156-120">Библиотека ThreadX должна определять `bsd_errno` в локальном по отношению к потоку хранилище.</span><span class="sxs-lookup"><span data-stu-id="63156-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="63156-121">Рекомендуется следующая процедура.</span><span class="sxs-lookup"><span data-stu-id="63156-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="63156-122">В файле *tx_port.h* задайте один из макросов TX_THREAD_EXTENSION следующим образом:</span><span class="sxs-lookup"><span data-stu-id="63156-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="63156-123">Перестройте библиотеку ThreadX.</span><span class="sxs-lookup"><span data-stu-id="63156-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="63156-124">Если TX_THREAD_EXTENSION_3 уже используется, пользователь может использовать один из других макросов TX_THREAD_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="63156-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="63156-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="63156-125">NetX Duo</span></span>

<span data-ttu-id="63156-126">Перед использованием служб NetX Duo BSD необходимо выполнить сборку библиотеки NetX с определенным параметром NX_ENABLE_EXTENDED_NOTIFY_SUPPORT.</span><span class="sxs-lookup"><span data-stu-id="63156-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="63156-127">По умолчанию он не определен.</span><span class="sxs-lookup"><span data-stu-id="63156-127">By default it is not defined.</span></span> <span data-ttu-id="63156-128">Если используются сокеты RAW для BSD, то при сборке библиотеки NetX Duo следует определить параметр NX_ENABLE_IP_RAW_PACKET_FILTER.</span><span class="sxs-lookup"><span data-stu-id="63156-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="63156-129">Использование NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="63156-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="63156-130">Проект приложения NetX Duo BSD должен включать в себя файл *nxd_bsd.h*, после которого нужно добавить файлы *tx_api.h* и *nx_api.h*, чтобы иметь возможность использовать службы BSD, описанные далее в этом руководством.</span><span class="sxs-lookup"><span data-stu-id="63156-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="63156-131">В приложение также нужно включить файл *nxd_bsd.c* для процесса сборки.</span><span class="sxs-lookup"><span data-stu-id="63156-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="63156-132">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="63156-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="63156-133">Это все, что необходимо для использования NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="63156-134">Чтобы использовать службы NetX Duo BSD, приложение должно создать экземпляр IP, создать пул пакетов для уровня BSD, чтобы выделять из него пакеты, выделить пространство памяти для внутреннего стека потоков BSD и задать приоритет внутреннего потока BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="63156-135">Уровень BSD инициализируется путем вызова *bsd_initialize* и передачи параметров.</span><span class="sxs-lookup"><span data-stu-id="63156-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="63156-136">Это будет показано в разделе "Пример небольшой системы" далее в этом документе, но прототип показан ниже.</span><span class="sxs-lookup"><span data-stu-id="63156-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="63156-137">Параметр default_ip задает экземпляр IP, с которым работает уровень BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="63156-138">Пул default_pool используется службами BSD для выделения пакетов.</span><span class="sxs-lookup"><span data-stu-id="63156-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="63156-139">Следующие два параметра, bsd_thread_stack_area и bsd_thread_stack_size определяют область стека, используемую внутренним потоком BSD, а последний параметр, bsd_thread_priority, задает приоритет этого потока.</span><span class="sxs-lookup"><span data-stu-id="63156-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="63156-140">Поддержка сокетов RAW в NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="63156-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="63156-141">NetX Duo BSD также поддерживает сокеты RAW.</span><span class="sxs-lookup"><span data-stu-id="63156-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="63156-142">Чтобы использовать сокеты RAW в NetX Duo BSD, необходимо скомпилировать библиотеку NetX Duo с определенным NX_ENABLE_IP_RAW_PACKET_FILTER.</span><span class="sxs-lookup"><span data-stu-id="63156-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="63156-143">По умолчанию он не определен.</span><span class="sxs-lookup"><span data-stu-id="63156-143">By default it is not defined.</span></span> <span data-ttu-id="63156-144">После этого приложение должно включить обработку сокетов RAW для созданного ранее экземпляра IP, вызвав *nx_ip_raw_packet_enable*.</span><span class="sxs-lookup"><span data-stu-id="63156-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="63156-145">Чтобы создать сокет RAW в NetX Duo BSD, приложение использует службу создания сокетов *socket* и указывает семейство протоколов, тип сокета и протокол.</span><span class="sxs-lookup"><span data-stu-id="63156-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="63156-146">Параметр protocolFamily имеет значение AF_INET для сокетов IPv4 или AF_INET6 для сокетов IPv6, при условии, что в экземпляре IP включен протокол IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="63156-147">Для socket_type необходимо задать значение SOCK_RAW.</span><span class="sxs-lookup"><span data-stu-id="63156-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="63156-148">Протокол зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="63156-148">protocol is application specific.</span></span>

<span data-ttu-id="63156-149">Чтобы отправлять и получать пакеты RAW, а также закрывать сокет RAW, приложение обычно использует те же самые службы BSD, что и для протокола UDP, например *sendto, recvfrom, select* и *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="63156-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="63156-150">Сокеты RAW не поддерживают службы BSD *accept* и *listen*.</span><span class="sxs-lookup"><span data-stu-id="63156-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="63156-151">По умолчанию полученные необработанные данные IPv4 содержат заголовок IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="63156-152">А полученные необработанные данные IPv6 не содержат заголовок IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="63156-153">По умолчанию при отправке пакетов RAW для IPv6 или IPv4 слой программы-оболочки BSD предварительно добавляет заголовок IPv6 или IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="63156-154">NetX Duo BSD поддерживает дополнительные параметры сокетов RAW, включая IP_RAW_RX_NO_HEADER, IP_HDRINCL и IP_RAW_IPV6_HDRINCL.</span><span class="sxs-lookup"><span data-stu-id="63156-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="63156-155">Если задан параметр IP_RAW_RX_NO_HEADER, заголовок IPv4 удаляется, чтобы полученные данные не содержали заголовок IPv4, а передаваемая длина сообщения не включает в себя заголовок IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="63156-156">Для сокетов IPv6 по умолчанию данные, получаемые через сокет RAW, не содержат заголовок IPv6, что эквивалентно заданию параметра IP_RAW_RX_NO_HEADER.</span><span class="sxs-lookup"><span data-stu-id="63156-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="63156-157">Приложение может использовать службу *setsockopt*, чтобы удалить параметр IP_RAW_RX_NO_HEADER. После удаления параметра IP_RAW_RX_NO_HEADER полученные необработанные данные IPv6 будут содержать заголовок IPv6, а передаваемая длина сообщения будет включать в себя заголовок IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="63156-158">Этот параметр не влияет на передачу данных по протоколам IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="63156-159">Если задан параметр IP_HDRINCL, приложение добавляет заголовок IPv4 при отправке данных.</span><span class="sxs-lookup"><span data-stu-id="63156-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="63156-160">Этот параметр не влияет на передачу данных по протоколу IPv6 и не определен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="63156-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="63156-161">Если задан параметр IP_RAW_IPV6_HDRINCL, приложение добавляет заголовок IPV6 при отправке данных.</span><span class="sxs-lookup"><span data-stu-id="63156-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="63156-162">Этот параметр не влияет на передачу данных по протоколу IPv4 и не определен по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="63156-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="63156-163">Параметры IP_HDRINCL и IP_RAW_IPV6_HDRINCL не влияют на получение данных по протоколу IPv4 или IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="63156-164">Спецификация сокета BSD 4.3 указывает, что ядро должно копировать пакет RAW в каждый буфер приема сокета.</span><span class="sxs-lookup"><span data-stu-id="63156-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="63156-165">Однако если в NetX Duo BSD создать несколько сокетов, использующих один протокол, то поведение будет не определено.</span><span class="sxs-lookup"><span data-stu-id="63156-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="63156-166">Поддержка пакетов RAW в NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="63156-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="63156-167">Чтобы включить поддержку пакетов RAW для PPPoE, необходимо выполнить сборку программы-оболочки NetX Duo BSD с включенным параметром NX_BSD_RAW_PPPOE_SUPPORT.</span><span class="sxs-lookup"><span data-stu-id="63156-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="63156-168">Следующая команда создает сокет BSD для обработки пакетов RAW для PPPoE:</span><span class="sxs-lookup"><span data-stu-id="63156-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="63156-169">Текущая реализация BSD поддерживает только два типа протоколов семейства AF_PACKET:</span><span class="sxs-lookup"><span data-stu-id="63156-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="63156-170">`ETHERTYPE_PPPOE_DISC`: пакеты Discovery PPPoE.</span><span class="sxs-lookup"><span data-stu-id="63156-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="63156-171">В кадре данных MAC пакеты Discovery имеют тип кадра Ethernet 0x8863.</span><span class="sxs-lookup"><span data-stu-id="63156-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="63156-172">`ETHERTYPE_PPPOE_SESS`: пакеты Session PPP.</span><span class="sxs-lookup"><span data-stu-id="63156-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="63156-173">В кадре данных MAC пакеты Session имеют тип кадра Ethernet 0x8864.</span><span class="sxs-lookup"><span data-stu-id="63156-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="63156-174">Структура `sockaddr_ll` используется для указания параметров при отправке или получении кадров PPPoE.</span><span class="sxs-lookup"><span data-stu-id="63156-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="63156-175">`struct sockaddr_ll` объявляется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="63156-175">`struct sockaddr_ll` is declared as:</span></span>

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> <span data-ttu-id="63156-176">Не все поля в структуре используются `sendto()` или `recvfrom()`.</span><span class="sxs-lookup"><span data-stu-id="63156-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="63156-177">Сведения о настройке `sockaddr_ll` для отправки и получения пакетов PPPoE приведены в описании ниже.</span><span class="sxs-lookup"><span data-stu-id="63156-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="63156-178">Сокет, созданный в семействе AF_PACKET, можно использовать для отправки пакетов Discovery PPPoE или пакетов Session PPP независимо от указанного протокола.</span><span class="sxs-lookup"><span data-stu-id="63156-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="63156-179">При передаче пакета PPPoE приложение должно подготовить буфер, который включает в себя правильно отформатированный кадр PPPoE, в том числе заголовки MAC (конечный MAC-адрес, исходный MAC-адрес и тип кадра). Размер буфера должен вмещать 14-байтовый заголовок Ethernet.</span><span class="sxs-lookup"><span data-stu-id="63156-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="63156-180">Структура `sockaddr_ll`, `sll_ifindex`, используется для указания физического интерфейса, который будет использоваться для отправки этого пакета.</span><span class="sxs-lookup"><span data-stu-id="63156-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="63156-181">Остальные поля в структуре не используются.</span><span class="sxs-lookup"><span data-stu-id="63156-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="63156-182">Значения, заданные для неиспользуемых полей, игнорируются внутренними операциями BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="63156-183">В следующем блоке кода показано, как передать пакет PPPoE.</span><span class="sxs-lookup"><span data-stu-id="63156-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="63156-184">Возвращаемое значение указывает количество переданных байтов.</span><span class="sxs-lookup"><span data-stu-id="63156-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="63156-185">Так как пакеты PPPoE на основаны на сообщениях, при успешной передаче число отправленных байтов соответствует размеру пакета, включая 14-байтовый заголовок Ethernet.</span><span class="sxs-lookup"><span data-stu-id="63156-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="63156-186">Пакеты PPPoE можно получить с помощью `recvfrom()`.</span><span class="sxs-lookup"><span data-stu-id="63156-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="63156-187">Буфер приема должен быть достаточно большим, чтобы вместить сообщения размера MTU для Ethernet.</span><span class="sxs-lookup"><span data-stu-id="63156-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="63156-188">Полученный пакет PPPoE включает в себя 14-байтовый заголовок Ethernet.</span><span class="sxs-lookup"><span data-stu-id="63156-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="63156-189">При получении пакетов PPPoE пакеты Discovery PPPoE могут быть получены только сокетом, созданным с использованием протокола `ETHERTYPE_PPPOE_DISC`.</span><span class="sxs-lookup"><span data-stu-id="63156-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="63156-190">Аналогично, пакеты Session PPP могут быть получены только сокетом, созданным с использованием протокола `ETHERTYPE_PPPOE_SESS`.</span><span class="sxs-lookup"><span data-stu-id="63156-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="63156-191">Если для одного типа протокола создано несколько сокетов, поступающие пакеты PPPoE перенаправляются в сокет, созданный первым.</span><span class="sxs-lookup"><span data-stu-id="63156-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="63156-192">Если первый сокет, созданный для протокола, закрыт, для получения этих пакетов используется следующий сокет в порядке создания.</span><span class="sxs-lookup"><span data-stu-id="63156-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="63156-193">После получения пакета PPPoE в `sockaddr_ll` структуре являются допустимыми следующие поля:</span><span class="sxs-lookup"><span data-stu-id="63156-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="63156-194">**sll_family**: задается внутренними процессами BSD и имеет значение AF_PACKET BSD;</span><span class="sxs-lookup"><span data-stu-id="63156-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="63156-195">**sll_ifindex**: указывает интерфейс, из которого получен пакет;</span><span class="sxs-lookup"><span data-stu-id="63156-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="63156-196">**sll_protocol**: задает тип полученного пакета: `ETHERTYPE_PPPOE_DISC` или `ETHERTYPE_PPPOE_SESS`.</span><span class="sxs-lookup"><span data-stu-id="63156-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="63156-197">Исключение внутреннего потока BSD</span><span class="sxs-lookup"><span data-stu-id="63156-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="63156-198">По умолчанию в BSD используется внутренний поток для части операций.</span><span class="sxs-lookup"><span data-stu-id="63156-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="63156-199">В системах с жесткими ограничениями памяти при сборке экземпляра BSD можно определить параметр NX_BSD_TIMEOUT_PROCESS_IN_TIMER. Он исключит внутренний поток BSD, а для выполнения той же обработки будет использоваться внутренний таймер.</span><span class="sxs-lookup"><span data-stu-id="63156-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="63156-200">Это освобождает объем памяти, необходимый для блока управления внутренним потоком BSD и стека внутреннего потока BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="63156-201">Однако общая интенсивность операций с таймером значительно увеличится, а обработка BSD может выполняться с более высоким приоритетом, чем требуется.</span><span class="sxs-lookup"><span data-stu-id="63156-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="63156-202">Чтобы настроить сокеты BSD для выполнения в контексте таймера ThreadX, определите NX_BSD_TIMEOUT_PROCESS_IN_TIMER в *nxd_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="63156-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="63156-203">Если уровень BSD настроен для выполнения задач BSD в контексте таймера, то в вызове *bsd_initialize* игнорируются приведенные ниже три параметра, и для них должно быть задано значение NULL:</span><span class="sxs-lookup"><span data-stu-id="63156-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="63156-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="63156-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="63156-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="63156-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="63156-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="63156-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="63156-207">NetX Duo BSD с поддержкой DNS</span><span class="sxs-lookup"><span data-stu-id="63156-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="63156-208">Если определен параметр NX_BSD_ENABLE_DNS, то NetX Duo BSD может отправлять запросы DNS для получения сведений об имени узла или IP-адресе узла.</span><span class="sxs-lookup"><span data-stu-id="63156-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="63156-209">Для применения этой функции требуется предварительно создать клиент NetX DNS с помощью службы *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="63156-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="63156-210">Один или несколько известных IP-адресов DNS-серверов должны быть зарегистрированы в экземпляре DNS с помощью службы *nx_dns_server_add* (для добавления адресов серверов IPv4) или службы *nxd_dns_server_add* (для добавления адресов серверов IPv4 или IPv6).</span><span class="sxs-lookup"><span data-stu-id="63156-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="63156-211">Службы DNS и выделение памяти используются службами *getaddrinfo* и *getnameinfo*.</span><span class="sxs-lookup"><span data-stu-id="63156-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="63156-212">Когда приложение BSD вызывает *getaddrinfo* с именем узла, NetX BSD вызывает следующие службы для получения IP-адреса:</span><span class="sxs-lookup"><span data-stu-id="63156-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="63156-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="63156-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="63156-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="63156-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="63156-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="63156-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="63156-216">Для *nx_dns_ipv4_address_by_name_get* и *nxd_dns_ipv6_address_by_name_get* NetX BSD использует области памяти ipv4_addr_buffer и ipv6_addr_buffer соответственно.</span><span class="sxs-lookup"><span data-stu-id="63156-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="63156-217">Размер этих буферов равен NX_BSD_IPV4_ADDR_PER_HOST \* 4 и NX_BSD_IPV6_ADDR_PER_HOST \* 16 соответственно.</span><span class="sxs-lookup"><span data-stu-id="63156-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="63156-218">Для возвращения сведений об адресе из функции *getaddrinfo* NetX BSD использует таблицу блоков памяти ThreadX, nx_bsd_addrinfo_pool_memory, область памяти которой определяется другим набором настраиваемых параметров, NX_BSD_IPV4_ADDR_MAX_NUM и NX_BSD_IPV6_ADDR_MAX_NUM.</span><span class="sxs-lookup"><span data-stu-id="63156-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="63156-219">Дополнительные сведения о перечисленных выше параметрах конфигурации см. в разделе **Общие параметры конфигурации**.</span><span class="sxs-lookup"><span data-stu-id="63156-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="63156-220">Кроме того, если определен параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES, а входные данные узла являются каноническим именем, то NetX Duo BSD выделит память динамически из созданного ранее пула блоков _nx_bsd_cname_block_pool.</span><span class="sxs-lookup"><span data-stu-id="63156-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="63156-221">После вызова службы *getaddrinfo* приложение BSD отвечает за освобождение памяти, на которую указывает аргумент res, и ее возвращение в таблицу блоков с помощью службы *freeaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="63156-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="63156-222">Ограничения NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="63156-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="63156-223">Из-за проблем с производительностью и архитектурой NetX Duo BSD не поддерживает все функции сокетов BSD 4.3:</span><span class="sxs-lookup"><span data-stu-id="63156-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="63156-224">Флаги INT не поддерживаются для вызовов *send, recv, sendto* и *recvfrom*.</span><span class="sxs-lookup"><span data-stu-id="63156-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="63156-225">Общие параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="63156-225">General Configuration Options</span></span>

<span data-ttu-id="63156-226">Настраиваемые пользователем параметры в файле *nxd_bsd.h* позволяют приложению точно настроить сокеты NetX Duo BSD в соответствии с требованиями этого приложения.</span><span class="sxs-lookup"><span data-stu-id="63156-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="63156-227">Ниже приведен список настраиваемых параметров, задаваемых во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="63156-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="63156-228">**NX_BSD_TCP_WINDOW**: используется в вызовах create для сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="63156-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="63156-229">64 КБ — это стандартный размер окна для Ethernet 100 Мбит/с.</span><span class="sxs-lookup"><span data-stu-id="63156-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="63156-230">Значение по умолчанию — 65535.</span><span class="sxs-lookup"><span data-stu-id="63156-230">The default value is 65535.</span></span>

- <span data-ttu-id="63156-231">**NX_BSD_SOCKFD_START**: логический индекс для начального значения дескриптора файла сокета BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="63156-232">По умолчанию этот параметр имеет значение 32.</span><span class="sxs-lookup"><span data-stu-id="63156-232">By default this option is 32.</span></span>

- <span data-ttu-id="63156-233">**NX_BSD_MAX_SOCKETS**: указывает максимальное число доступных сокетов на уровне BSD. Это значение должно быть кратно 32.</span><span class="sxs-lookup"><span data-stu-id="63156-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="63156-234">Значение по умолчанию — 32.</span><span class="sxs-lookup"><span data-stu-id="63156-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="63156-235">**NX_BSD_SOCKET_QUEUE_MAX**: указывает максимальное число пакетов UDP, хранящихся в очереди приема сокета.</span><span class="sxs-lookup"><span data-stu-id="63156-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="63156-236">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="63156-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="63156-237">**NX_BSD_MAX_LISTEN_BACKLOG**: указывает размер очереди ожидания передачи данных ("невыполненной работы") для сокетов TCP протокола BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="63156-238">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="63156-238">The default value is 5.</span></span>

- <span data-ttu-id="63156-239">**NX_MICROSECOND_PER_CPU_TICK**: указывает число микросекунд на такт таймера планировщика.</span><span class="sxs-lookup"><span data-stu-id="63156-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="63156-240">**NX_BSD_TIMEOUT**: указывает время ожидания в тактах таймера для внутренних вызовов NetX Duo, необходимых для BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="63156-241">Значение по умолчанию равно 20 \* NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="63156-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="63156-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: указывает время ожидания в тактах таймера при вызове отключения NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="63156-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="63156-243">Значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="63156-243">The default value is 1.</span></span>

- <span data-ttu-id="63156-244">**NX_BSD_PRINT_ERRORS**: если этот параметр задан, то при возвращении состояния ошибки функция BSD возвращает номер строки, где возникла ошибка, и тип ошибки, например NX_SOC_ERROR.</span><span class="sxs-lookup"><span data-stu-id="63156-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="63156-245">Для использования этой функции разработчику приложения нужно определить выходные данные отладки.</span><span class="sxs-lookup"><span data-stu-id="63156-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="63156-246">По умолчанию этот параметр отключен, а выходные данные отладки в файле *nxd_bsd.h* не указаны.</span><span class="sxs-lookup"><span data-stu-id="63156-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="63156-247">**NX_BSD_TIMER_RATE**: интервал, по истечении которого выполняется периодическая задача таймера BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="63156-248">Значение по умолчанию — 1 секунда (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="63156-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="63156-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: если этот параметр задан, он позволяет выполнять процесс времени ожидания BSD в контексте системного таймера.</span><span class="sxs-lookup"><span data-stu-id="63156-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="63156-250">По умолчанию этот режим отключен.</span><span class="sxs-lookup"><span data-stu-id="63156-250">The default behavior is disabled.</span></span> <span data-ttu-id="63156-251">Эта функция более подробно описана в главе 2, "Установка и использование NetX Duo BSD".</span><span class="sxs-lookup"><span data-stu-id="63156-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="63156-252">**NX_BSD_RAW_PPPOE_SUPPORT**: включение поддержки пакетов RAW для PPPoE.</span><span class="sxs-lookup"><span data-stu-id="63156-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="63156-253">По умолчанию этот параметр отключен.</span><span class="sxs-lookup"><span data-stu-id="63156-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="63156-254">**NX_BSD_ENABLE_DNS**: если этот параметр включен, то NetX Duo BSD будет отправлять запрос DNS по имени узла или IP-адресу узла.</span><span class="sxs-lookup"><span data-stu-id="63156-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="63156-255">Требуется, чтобы предварительно был создан и запущен экземпляр DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="63156-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="63156-256">По умолчанию эта функция отключена.</span><span class="sxs-lookup"><span data-stu-id="63156-256">By default it is not enabled.</span></span>

- <span data-ttu-id="63156-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: определяет размер таблицы сокетов RAW.</span><span class="sxs-lookup"><span data-stu-id="63156-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="63156-258">Значение должно быть степенью числа 2.</span><span class="sxs-lookup"><span data-stu-id="63156-258">The value must be a power of two.</span></span> <span data-ttu-id="63156-259">NetX BSD создает массив сокетов типа NX_BSD_SOCKETS для отправки и получения пакетов RAW.</span><span class="sxs-lookup"><span data-stu-id="63156-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="63156-260">Параметр NX_ENABLE_IP_RAW_PACKET_FILTER должен быть включен.</span><span class="sxs-lookup"><span data-stu-id="63156-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="63156-261">Значение по умолчанию — 32.</span><span class="sxs-lookup"><span data-stu-id="63156-261">By default it is 32.</span></span>

- <span data-ttu-id="63156-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: максимальное число IPv4-адресов, возвращаемых службой *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="63156-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="63156-263">Вместе с NX_BSD_IPV6_ADDR_MAX_NUM определяет размер пула блоков NetX BSD, nx_bsd_addrinfo_block_pool, используемого для динамического выделения памяти для хранения информации об адресах, возвращаемой *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="63156-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="63156-264">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="63156-264">The default value is 5.</span></span>

- <span data-ttu-id="63156-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: максимальное число IPv6-адресов, возвращаемых службой *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="63156-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="63156-266">Вместе с NX_BSD_IPV4_ADDR_MAX_NUM определяет размер пула блоков NetX BSD, nx_bsd_addrinfo_block_pool, используемого для динамического выделения памяти для хранения информации об адресах, возвращаемой *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="63156-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="63156-267">**NX_BSD_IPV4_ADDR_PER_HOST**: определяет максимальное количество IPv4-адресов, сохраняемых для каждого запроса DNS.</span><span class="sxs-lookup"><span data-stu-id="63156-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="63156-268">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="63156-268">The default value is 5.</span></span>

- <span data-ttu-id="63156-269">**NX_BSD_IPV6_ADDR_PER_HOST**: определяет максимальное количество IPv6-адресов, сохраняемых для каждого запроса DNS.</span><span class="sxs-lookup"><span data-stu-id="63156-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="63156-270">Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="63156-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="63156-271">Параметры сокета BSD</span><span class="sxs-lookup"><span data-stu-id="63156-271">BSD Socket Options</span></span>

<span data-ttu-id="63156-272">Ниже приведен список параметров сокета NetX Duo BSD, которые можно включать (или отключать) во время выполнения для каждого сокета с помощью службы *setsockopt*.</span><span class="sxs-lookup"><span data-stu-id="63156-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="63156-273">Существуют два разных параметра для option_level.</span><span class="sxs-lookup"><span data-stu-id="63156-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="63156-274">Первый тип параметров сокета времени выполнения — SOL_SOCKET для параметров уровня сокета.</span><span class="sxs-lookup"><span data-stu-id="63156-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="63156-275">Чтобы включить параметр уровня сокета, вызовите *setsockopt*, присвоив параметру option_level значение SOL_SOCKET и указав для параметра option_name конкретный параметр, например SO_BROADCAST *.*</span><span class="sxs-lookup"><span data-stu-id="63156-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="63156-276">Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="63156-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="63156-277">Ниже приведен список параметров уровня сокета времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="63156-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="63156-278">**SO_BROADCAST**: если этот параметр задан, он позволяет отправлять и получать широковещательные пакеты через сокеты Netx.</span><span class="sxs-lookup"><span data-stu-id="63156-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="63156-279">Это режим по умолчанию для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="63156-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="63156-280">Эта возможность поддерживается всеми сокетами.</span><span class="sxs-lookup"><span data-stu-id="63156-280">All sockets have this capability.</span></span>

- <span data-ttu-id="63156-281">**SO_ERROR**: используется для получения состояния сокета в предыдущей операции указанного сокета с помощью службы *getsockopt*.</span><span class="sxs-lookup"><span data-stu-id="63156-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="63156-282">Эта возможность поддерживается всеми сокетами.</span><span class="sxs-lookup"><span data-stu-id="63156-282">All sockets have this capability.</span></span>

- <span data-ttu-id="63156-283">**SO_KEEPALIVE**: если этот параметр задан, то он включает функцию проверки активности TCP.</span><span class="sxs-lookup"><span data-stu-id="63156-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="63156-284">Для этого необходимо, чтобы библиотека NetX Duo была создана с параметром NX_TCP_ENABLE_KEEPALIVE, определенным в файле *nx_user.h*.</span><span class="sxs-lookup"><span data-stu-id="63156-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="63156-285">По умолчанию эта функция отключена.</span><span class="sxs-lookup"><span data-stu-id="63156-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="63156-286">**SO_RCVTIMEO**: задает время ожидания в секундах для получения пакетов через сокеты NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="63156-287">Значение по умолчанию — NX_WAIT_FOREVER (0xFFFFFFFF) или, если включена защита от блокировки, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="63156-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="63156-288">**SO_RCVBUF**: задает размер окна сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="63156-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="63156-289">Значение по умолчанию, NX_BSD_TCP_WINDOW, равно 64 КБ для сокетов TCP протокола BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="63156-290">Чтобы установить размер больше 65535, необходимо создать библиотеку NetX Duo с определенным параметром NX_TCP_ENABLE_WINDOW_SCALING.</span><span class="sxs-lookup"><span data-stu-id="63156-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="63156-291">**SO_REUSEADDR**: если этот параметр задан, то он позволяет сопоставить несколько сокетов с одним портом.</span><span class="sxs-lookup"><span data-stu-id="63156-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="63156-292">Как правило, это используется для сокета TCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="63156-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="63156-293">Это режим по умолчанию для сокетов NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="63156-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="63156-294">Вторым типом параметров сокета времени выполнения являются параметры уровня IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="63156-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="63156-295">Чтобы включить параметр уровня IP-адреса, вызовите *setsockopt*, задав для параметра option_level значение IP_PROTO, а для option_name — имя параметра, например IP_MULTICAST_TTL *.*</span><span class="sxs-lookup"><span data-stu-id="63156-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="63156-296">Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение IP_PROTO</span><span class="sxs-lookup"><span data-stu-id="63156-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="63156-297">Ниже приведен список параметров уровня IP-адреса времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="63156-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="63156-298">**IP_MULTICAST_TTL**: задает срок жизни сокетов UDP.</span><span class="sxs-lookup"><span data-stu-id="63156-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="63156-299">Значение по умолчанию — NX_IP_TIME_TO_LIVE (0x80). Оно задается при создании сокета.</span><span class="sxs-lookup"><span data-stu-id="63156-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="63156-300">Это значение можно переопределить, вызвав *setsockopt* с этим параметром сокета.</span><span class="sxs-lookup"><span data-stu-id="63156-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="63156-301">**IP_RAW_IPV6_HDRINCL**: если этот параметр задан, то вызывающее приложение должно добавить заголовок IPv6 и необязательные заголовки приложения в данные, передаваемые в сокеты RAW для IPv6, созданные экземпляром BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="63156-302">Чтобы использовать этот параметр, необходимо включить обработку сокетов RAW в задаче IP.</span><span class="sxs-lookup"><span data-stu-id="63156-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="63156-303">**IP_ADD_MEMBERSHIP**: если этот параметр задан, то он позволяет включить сокет BSD (применяется только к сокетам UDP) в указанную группу IGMP.</span><span class="sxs-lookup"><span data-stu-id="63156-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="63156-304">**IP_DROP_MEMBERSHIP**: если этот параметр задан, то он позволяет удалить сокет BSD (применяется только к сокетам UDP) из указанной группы IGMP.</span><span class="sxs-lookup"><span data-stu-id="63156-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="63156-305">**IP_HDRINCL**: если этот параметр задан, то вызывающее приложение должно добавить заголовок IP и необязательные заголовки приложения в данные, передаваемые в сокеты RAW для IPv4, созданные в BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="63156-306">Чтобы использовать этот параметр, необходимо включить обработку сокетов RAW в задаче IP.</span><span class="sxs-lookup"><span data-stu-id="63156-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="63156-307">**IP_RAW_RX_NO_HEADER**: если этот параметр не задан, заголовок IPv6 добавляется в полученные данные для сокетов RAW для IPv6, созданных в BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="63156-308">В протоколе BSD заголовки IPv6 по умолчанию удаляются в сокетах RAW для IPv6, а длина пакета не включает в себя заголовок IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="63156-309">Если этот параметр задан, то заголовок IPv4 удаляется из полученных данных в сокетах RAW для BSD типа IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="63156-310">В протоколе BSD заголовки IPv4 по умолчанию добавляются в сокеты RAW для IPv4, а длина пакета включает в себя заголовок IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="63156-311">Этот параметр не влияет на данные, передаваемые по протоколам IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="63156-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="63156-312">Пример небольшой системы IPv4</span><span class="sxs-lookup"><span data-stu-id="63156-312">Small IPv4 Example</span></span>

<span data-ttu-id="63156-313">Ниже приведен пример использования служб NetX Duo BSD для сетей IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="63156-314">В этом примере в строке 8 добавлен включаемый файл *nxd_bsd.h*.</span><span class="sxs-lookup"><span data-stu-id="63156-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="63156-315">Далее, в строках 20 и 21 как глобальные переменные создаются экземпляр IP *bsd_ip* и пул пакетов *bsd_pool*.</span><span class="sxs-lookup"><span data-stu-id="63156-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="63156-316">Обратите внимание на то, что в этом демонстрационном файле используется драйвер сетевой ОЗУ, *_nx_ram_network_driver*.</span><span class="sxs-lookup"><span data-stu-id="63156-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="63156-317">В этом примере клиент и сервер будут использовать один и тот же IP-адрес экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="63156-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="63156-318">Потоки клиента и сервера создаются в строках 62 и 68.</span><span class="sxs-lookup"><span data-stu-id="63156-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="63156-319">Пул пакетов BSD для передачи пакетов создается в строке 78 и используется при создании экземпляра IP в строке 87.</span><span class="sxs-lookup"><span data-stu-id="63156-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="63156-320">Обратите внимание на то, что задаче потока IP назначается приоритет 1 в вызове *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="63156-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="63156-321">Этот поток должен быть задачей с наивысшим приоритетом, определенной в программе, чтобы обеспечить оптимальную производительность NetX.</span><span class="sxs-lookup"><span data-stu-id="63156-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="63156-322">В строках 88 и 110 для экземпляра IP включаются службы ARP и TCP соответственно.</span><span class="sxs-lookup"><span data-stu-id="63156-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="63156-323">Последнее требование, которое необходимо выполнить, чтобы использовать службы BSD, — вызвать функцию *bsd_initialize* в строке 120. Это требуется, чтобы настроить все структуры данных, а также ресурсы NetX и ThreadX, необходимые для протокола BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="63156-324">Функция входа потока сервера определена далее.</span><span class="sxs-lookup"><span data-stu-id="63156-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="63156-325">Сокет TCP для BSD создается в строке 149.</span><span class="sxs-lookup"><span data-stu-id="63156-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="63156-326">IP-адрес и порт сервера задаются в строках 160–163.</span><span class="sxs-lookup"><span data-stu-id="63156-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="63156-327">Обратите внимание на использование макросов обработки порядка байтов узла и сети *htonl* и *htons*, применяемых к IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="63156-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="63156-328">Многобайтовые данные передаются в службы BSD в порядке байтов сети, что соответствует спецификации сокета BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="63156-329">Затем в строке 166 главный сокет сервера привязывается к порту с помощью службы *bind*.</span><span class="sxs-lookup"><span data-stu-id="63156-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="63156-330">В строке 180 с помощью службы *listen* определяется сокет ожидания передачи запросов TCP-соединения.</span><span class="sxs-lookup"><span data-stu-id="63156-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="63156-331">После этого функция потока сервера, *thread_server_entry*, выполняет циклические проверки событий получения с помощью вызова *select* в строке 202.</span><span class="sxs-lookup"><span data-stu-id="63156-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="63156-332">Если событие получения представляет собой запрос соединения, который определяется путем сравнения списка готовности к чтению, вызывается метод *accept* в строке 213.</span><span class="sxs-lookup"><span data-stu-id="63156-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="63156-333">В строке 223 назначается дочерний сокет сервера для выполнения запроса соединения, который добавляется в главный список сокетов TCP-сервера, подключенных к клиенту.</span><span class="sxs-lookup"><span data-stu-id="63156-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="63156-334">Если новые запросы соединения отсутствуют, поток сервера проверяет все подключенные в данный момент сокеты на наличие событий получения в цикле for, который начинается в строке 236.</span><span class="sxs-lookup"><span data-stu-id="63156-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="63156-335">При обнаружении ожидающего события получения он будет вызывать службы *send* и *recv* для этого сокета, пока получение данных не завершится (подключение закроется на другой стороне), а сокет не будет закрыт с помощью службы *soc_close* в строке 277.</span><span class="sxs-lookup"><span data-stu-id="63156-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="63156-336">После настройки потока сервера функция входа потока клиента *thread_client_entry* создает сокет в строке 326 и подключается к сокету TCP-сервера с помощью вызова *connect* в строке 337.</span><span class="sxs-lookup"><span data-stu-id="63156-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="63156-337">Затем она выполняет циклы отправки и получения пакетов, используя службы *send* и *recv* соответственно.</span><span class="sxs-lookup"><span data-stu-id="63156-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="63156-338">Когда получение данных завершается, она закрывает сокет в строке 398 с помощью службы *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="63156-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="63156-339">После отключения функция входа потока клиента создает новый сокет TCP и отправляет еще один запрос соединения в цикле while, который начинается в строке 321.</span><span class="sxs-lookup"><span data-stu-id="63156-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
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

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a><span data-ttu-id="63156-340">Пример небольшой системы IPv6</span><span class="sxs-lookup"><span data-stu-id="63156-340">Small IPv6 Example System</span></span>

<span data-ttu-id="63156-341">Пример использования служб NetX Duo BSD для сетей IPv6 описан в приведенной ниже программе.</span><span class="sxs-lookup"><span data-stu-id="63156-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="63156-342">Этот пример очень похож на демонстрационную программу IPv4, описанную выше, за исключением нескольких важных отличий.</span><span class="sxs-lookup"><span data-stu-id="63156-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="63156-343">Обработка потоков клиента и сервера, пула пакетов BSD, экземпляра IP и инициализация BSD выполняются так же, как и для сокетов IPv4 для BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="63156-344">В функции входа потока сервера *thread_server_entry* в строках 145–148 определяется пара переменных IPv6 с типом данных *sockaddr_in6* и *NXD_ADDRESS*.</span><span class="sxs-lookup"><span data-stu-id="63156-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="63156-345">Тип данных NXD_ADDRESS фактически позволяет хранить как IPv4-адреса, так и IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="63156-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="63156-346">Затем в строках 161 и 169 поток сервера включает протоколы IPv6 и ICMPv6 для экземпляра IP, используя службы *nxd_ipv6_enable* и *nxd_icmpv6_enable* соответственно.</span><span class="sxs-lookup"><span data-stu-id="63156-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="63156-347">Затем в экземпляре регистрируются локальный и глобальный IP-адреса канала.</span><span class="sxs-lookup"><span data-stu-id="63156-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="63156-348">Это делается с помощью службы *nxd_ipv6_address_set* в строках 180 и 195.</span><span class="sxs-lookup"><span data-stu-id="63156-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="63156-349">Затем он ожидает достаточно долго, чтобы задача потока IP выполнила протокол обнаружения повторяющихся адресов, и регистрирует эти адреса в качестве допустимых адресов в вызове *tx_thread_sleep* в строке 201.</span><span class="sxs-lookup"><span data-stu-id="63156-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="63156-350">Затем в строке 204 создается сокет TCP-сервера с входным аргументом типа сокета, равным AF_INET6.</span><span class="sxs-lookup"><span data-stu-id="63156-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="63156-351">IPv6-адрес и порт сокета задаются в строках 216–221. Еще раз обратите внимание на использование макросов *htonl* и *htons* для передачи данных в порядке байтов сети для служб сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="63156-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="63156-352">С этого места функция входа потока сервера практически такая же, как в примере для IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="63156-353">Далее определяется функция входа потока клиента, *thread_client_entry*.</span><span class="sxs-lookup"><span data-stu-id="63156-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="63156-354">Обратите внимание на то, что так как TCP-клиент в этом примере использует те же экземпляр IP и IPv6-адрес, что и TCP-сервер, нам не нужно снова включать службы IPv6 или ICMPv6 для экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="63156-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="63156-355">Кроме того, этот IPv6-адрес уже зарегистрирован в экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="63156-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="63156-356">Вместо этого функция входа потока клиента в строке 368 просто ожидает, пока сервер не будет настроен.</span><span class="sxs-lookup"><span data-stu-id="63156-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="63156-357">Адрес и порт сервера задаются с помощью макросов обработки порядка байтов сети в строках 387–392, после чего клиент может подключиться к TCP-серверу в строке 412.</span><span class="sxs-lookup"><span data-stu-id="63156-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="63156-358">Обратите внимание на то, что типы данных локальных IP-адресов в строках 378–383 используются только для демонстрации служб *getsockname* и *getpeername* в строках 425 и 434 соответственно.</span><span class="sxs-lookup"><span data-stu-id="63156-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="63156-359">Так как данные поступают из сети, в строках 378–383 используются макросы обработки порядка байтов узла и сети.</span><span class="sxs-lookup"><span data-stu-id="63156-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="63156-360">Затем функция входа потока клиента входит в цикл, в котором она создает сокет TCP, устанавливает TCP-подключение и отправляет и получает данные с помощью TCP-сервера до тех пор, пока не будут получены все данные, практически как в примере для IPv4.</span><span class="sxs-lookup"><span data-stu-id="63156-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="63156-361">Затем она закрывает сокет в строке 483, недолго ожидает, после чего создает другой сокет TCP и запрашивает соединение с TCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="63156-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="63156-362">Одно важное отличие от примера для IPv4 заключается в том, что в вызовах *socket* сокет IPv6 указывается с входным аргументом AF_INET6.</span><span class="sxs-lookup"><span data-stu-id="63156-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="63156-363">Другое важное отличие состоит в том, что вызов *connect* TCP-клиента принимает тип данных *sockaddr_in6*, а аргумент length имеет значение размера типа данных *sockaddr_in6*.</span><span class="sxs-lookup"><span data-stu-id="63156-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
