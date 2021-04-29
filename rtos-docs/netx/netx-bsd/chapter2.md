---
title: Глава 2. Установка и использование ОСРВ Azure NetX BSD
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815283"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a><span data-ttu-id="c5d4f-103">Глава 2. Установка и использование ОСРВ Azure NetX BSD</span><span class="sxs-lookup"><span data-stu-id="c5d4f-103">Chapter 2 - Installation and Use of Azure RTOS NetX BSD</span></span>

<span data-ttu-id="c5d4f-104">В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="c5d4f-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="c5d4f-105">Product Distribution</span></span>

<span data-ttu-id="c5d4f-106">ОСРВ Azure NetX BSD можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-106">Azure RTOS NetX BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="c5d4f-107">Этот пакет включает в себя два файла исходного кода и PDF-файл с этим документом:</span><span class="sxs-lookup"><span data-stu-id="c5d4f-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="c5d4f-108">**nx_bsd.h**: файл заголовка для NetX BSD;</span><span class="sxs-lookup"><span data-stu-id="c5d4f-108">**nx_bsd.h**: Header file for NetX BSD</span></span>
- <span data-ttu-id="c5d4f-109">**nx_bsd.c**: файл исходного кода C для NetX BSD;</span><span class="sxs-lookup"><span data-stu-id="c5d4f-109">**nx_bsd.c**: C Source file for NetX BSD</span></span>
- <span data-ttu-id="c5d4f-110">**nx_bsd.pdf**: руководство пользователя NetX BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-110">**nx_bsd.pdf**: User Guide for NetX BSD</span></span>

<span data-ttu-id="c5d4f-111">Демонстрационные файлы:</span><span class="sxs-lookup"><span data-stu-id="c5d4f-111">Demo files:</span></span>
- <span data-ttu-id="c5d4f-112">**bsd_demo_tcp.c**</span><span class="sxs-lookup"><span data-stu-id="c5d4f-112">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="c5d4f-113">**bsd_demo_udp.c**</span><span class="sxs-lookup"><span data-stu-id="c5d4f-113">**bsd_demo_udp.c**</span></span>

## <a name="netx-bsd-installation"></a><span data-ttu-id="c5d4f-114">Установка NetX BSD</span><span class="sxs-lookup"><span data-stu-id="c5d4f-114">NetX BSD Installation</span></span>

<span data-ttu-id="c5d4f-115">Чтобы использовать NetX BSD, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен экземпляр NetX.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-115">In order to use NetX BSD the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="c5d4f-116">Например, если экземпляр NetX установлен в каталоге *\threadx\arm7\green*, то файлы *nx_bsd.h* и *nx_bsd.c* необходимо скопировать в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-116">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_bsd.h* and *nx_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a><span data-ttu-id="c5d4f-117">Создание компонентов ThreadX и NetX приложения BSD</span><span class="sxs-lookup"><span data-stu-id="c5d4f-117">Building the ThreadX and NetX components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="c5d4f-118">ThreadX</span><span class="sxs-lookup"><span data-stu-id="c5d4f-118">ThreadX</span></span>

<span data-ttu-id="c5d4f-119">Библиотека ThreadX должна определять *bsd_errno* в локальном хранилище потоков.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-119">The ThreadX library must define *bsd_errno* in the thread local storage.</span></span> <span data-ttu-id="c5d4f-120">Рекомендуется следующая процедура.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-120">We recommend the following procedure:</span></span>

1. <span data-ttu-id="c5d4f-121">В файле *tx_port.h* задайте один из макросов TX_THREAD_EXTENSION следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c5d4f-121">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. <span data-ttu-id="c5d4f-122">Перестройте библиотеку ThreadX.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-122">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="c5d4f-123">Если TX_THREAD_EXTENSION_3 уже используется, пользователь может использовать один из других макросов TX_THREAD_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-123">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx"></a><span data-ttu-id="c5d4f-124">NetX</span><span class="sxs-lookup"><span data-stu-id="c5d4f-124">NetX</span></span>

<span data-ttu-id="c5d4f-125">Перед использованием NetX BSD необходимо выполнить сборку библиотеки NetX с определенным параметром NX_ENABLE_EXTENDED_NOTIFY_SUPPORT (например, в файле *nx_user.h*).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-125">Before using NetX BSD Services, the NetX library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined (e.g. in *nx_user.h*).</span></span> <span data-ttu-id="c5d4f-126">По умолчанию он не определен.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-126">By default it is not defined.</span></span>

## <a name="using-netx-bsd"></a><span data-ttu-id="c5d4f-127">Использование NetX BSD</span><span class="sxs-lookup"><span data-stu-id="c5d4f-127">Using NetX BSD</span></span>

<span data-ttu-id="c5d4f-128">Использовать NetX BSD просто.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-128">Using BSD for NetX is easy.</span></span> <span data-ttu-id="c5d4f-129">По сути, в код приложения следует добавить *nx_bsd.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-129">Basically, the application code must include *nx_bsd.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="c5d4f-130">После добавления *nx_bsd.h* код приложения сможет использовать службы BSD, описанные далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-130">Once *nx_bsd.h* is included, the application code is then able to use the BSD services specified later in this guide.</span></span> <span data-ttu-id="c5d4f-131">В приложение также нужно включить файл *nx_bsd.c* в процессе сборки.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-131">The application must also include *nx_bsd.c* in the build process.</span></span> <span data-ttu-id="c5d4f-132">Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="c5d4f-133">Это все, что необходимо для использования NetX BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-133">This is all that is required to use NetX BSD.</span></span>

<span data-ttu-id="c5d4f-134">Чтобы использовать службы NetX BSD, приложение должно создать экземпляр IP, пул пакетов и инициализировать службы BSD, вызвав *bsd_initialize*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-134">To utilize NetX BSD services, the application must create an IP instance, a packet pool, and initialize BSD services by calling *bsd_initialize.*</span></span> <span data-ttu-id="c5d4f-135">Это показано в разделе "Пример небольшой системы" далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-135">This is demonstrated in the "Small Example" section later in this guide.</span></span> <span data-ttu-id="c5d4f-136">Ниже приведен прототип.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-136">The prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

<span data-ttu-id="c5d4f-137">Последние три параметра используются для создания потока для выполнения периодических задач, таких как проверка событий TCP и определение пространства стека потоков.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-137">The last three parameters are used for creating a thread for performing periodic tasks such as checking for TCP events and define the thread stack space.</span></span>

> [!NOTE]
> <span data-ttu-id="c5d4f-138">В отличие от сокетов BSD, работающих в порядке байтов сети, NetX работает в порядке байтов узла, указанных для процессора узла.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-138">In contrast to BSD sockets, which work in network bye order, NetX works in the host byte order of the host processor.</span></span> <span data-ttu-id="c5d4f-139">В целях обеспечения совместимости исходных файлов макросы htons(), ntohs(), htonl() и ntohl() определены, но без изменений передаваемых аргументов.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-139">For source compatibility reasons, the macros htons(), ntohs(), htonl(), ntohl() have been defined, but do not modify the argument passed.</span></span>

## <a name="netx-bsd-limitations"></a><span data-ttu-id="c5d4f-140">Ограничения NetX BSD</span><span class="sxs-lookup"><span data-stu-id="c5d4f-140">NetX BSD Limitations</span></span>

<span data-ttu-id="c5d4f-141">Из-за проблем с производительностью и архитектурой NetX BSD не поддерживает все функции сокетов BSD 4.3.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-141">Due to performance and architecture issues, NetX BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="c5d4f-142">Флаги INT не поддерживаются для вызовов *send, recv, sendto* и *recvfrom*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-142">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="netx-bsd-with-dns-support"></a><span data-ttu-id="c5d4f-143">NetX BSD с поддержкой DNS</span><span class="sxs-lookup"><span data-stu-id="c5d4f-143">NetX BSD with DNS Support</span></span>

<span data-ttu-id="c5d4f-144">Если определен параметр NX_BSD_ENABLE_DNS, то NetX BSD может отправлять запросы DNS для получения сведений об имени узла или IP-адресе узла.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-144">If NX_BSD_ENABLE_DNS is defined, NetX BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="c5d4f-145">Для применения этой функции требуется предварительно создать клиент NetX DNS с помощью службы *nx_dns_create*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-145">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="c5d4f-146">Один или несколько известных IP-адресов DNS-серверов должны быть зарегистрированы в экземпляре DNS с помощью службы *nx_dns_server_add* для добавления адресов серверов.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-146">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* for adding server addresses.</span></span>

<span data-ttu-id="c5d4f-147">Службы DNS и выделение памяти используются службами *getaddrinfo* и *getnameinfo*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-147">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="c5d4f-148">Когда приложение BSD вызывает *getaddrinfo* с именем узла, NetX BSD вызывает следующие службы для получения IP-адреса:</span><span class="sxs-lookup"><span data-stu-id="c5d4f-148">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="c5d4f-149">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="c5d4f-149">nx_dns_ipv4_address_by_name_get</span></span>
- <span data-ttu-id="c5d4f-150">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="c5d4f-150">nx_dns_cname_get</span></span>

<span data-ttu-id="c5d4f-151">Для *nx_dns_ipv4_address_by_name_get* в NetX BSD используются области памяти ipv4_addr_buffer.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-151">For *nx_dns_ipv4_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer memory areas.</span></span> <span data-ttu-id="c5d4f-152">Размер этих буферов определяет (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-152">The size of these buffers are defined by (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).</span></span>

<span data-ttu-id="c5d4f-153">Для сведений об адресе, возвращаемых службой *getaddrinfo*, NetX BSD использует таблицу блоков памяти ThreadX *nx_bsd_addrinfo_pool_memory*, область памяти которой определяется другим набором настраиваемых параметров — *NX_BSD_IPV4_ADDR_MAX_NUM*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-153">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table *nx_bsd_addrinfo_pool_memory*, whose memory area is defined by another set of configurable options, *NX_BSD_IPV4_ADDR_MAX_NUM*.</span></span>

<span data-ttu-id="c5d4f-154">Дополнительные сведения о перечисленных выше параметрах конфигурации см. в разделе **Параметры конфигурации**.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-154">See **Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="c5d4f-155">Кроме того, если определен параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES, а для узла указано каноническое имя, то NetX BSD выделит память динамически из созданного ранее пула блоков *_nx_bsd_cname_block_pool*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-155">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX BSD will allocate memory dynamically from a previously created block pool *_nx_bsd_cname_block_pool*</span></span>

> [!NOTE]
> <span data-ttu-id="c5d4f-156">После вызова службы *getaddrinfo* приложение BSD отвечает за освобождение памяти, на которую указывает аргумент res, и ее возвращение в таблицу блоков с помощью службы *freeaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-156">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="c5d4f-157">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="c5d4f-157">Configuration Options</span></span>

<span data-ttu-id="c5d4f-158">Настраиваемые пользователем параметры в файле *nx_bsd.h* позволяют приложению точно настроить сокеты NetX BSD в соответствии с конкретными требованиями.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-158">User configurable options in *nx_bsd.h* allow the application to fine tune NetX BSD sockets for its particular requirements.</span></span> <span data-ttu-id="c5d4f-159">Ниже приведен список этих параметров:</span><span class="sxs-lookup"><span data-stu-id="c5d4f-159">The following is a list of these parameters:</span></span>

- <span data-ttu-id="c5d4f-160">**NX_BSD_TCP_WINDOW**: используется в вызовах create для сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-160">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="c5d4f-161">65535 — это стандартный размер окна для Ethernet 100 Мбит/с.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-161">65535 is a typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="c5d4f-162">Значение по умолчанию — 65535.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-162">The default value is 65535.</span></span>
- <span data-ttu-id="c5d4f-163">**NX_BSD_SOCKFD_START**: логический индекс для начального значения дескриптора файла сокета BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-163">**NX_BSD_SOCKFD_START** This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="c5d4f-164">По умолчанию этот параметр имеет значение 32.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-164">By default this option is 32.</span></span>
- <span data-ttu-id="c5d4f-165">**NX_BSD_MAX_SOCKETS**: указывает максимальное число доступных сокетов на уровне BSD. Это значение должно быть кратно 32. Значение по умолчанию — 32.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-165">**NX_BSD_MAX_SOCKETS** Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.The value is defaulted to 32.</span></span>
- <span data-ttu-id="c5d4f-166">**NX_BSD_SOCKET_QUEUE_MAX**: указывает максимальное число пакетов UDP, хранящихся в очереди приема сокета.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-166">**NX_BSD_SOCKET_QUEUE_MAX** Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="c5d4f-167">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-167">The value is defaulted to 5.</span></span>
- <span data-ttu-id="c5d4f-168">**NX_BSD_MAX_LISTEN_BACKLOG**: указывает размер очереди ожидания передачи данных ("невыполненной работы") для сокетов TCP протокола BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-168">**NX_BSD_MAX_LISTEN_BACKLOG** This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="c5d4f-169">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-169">The default value is 5.</span></span>
- <span data-ttu-id="c5d4f-170">**NX_MICROSECOND_PER_CPU_TICK**: указывает число микросекунд на прерывание таймера.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-170">**NX_MICROSECOND_PER_CPU_TICK** Specifies the number of microseconds per timer interrupt</span></span>
- <span data-ttu-id="c5d4f-171">**NX_BSD_TIMEOUT**: указывает время ожидания в тактах таймера для внутренних вызовов NetX, необходимых для BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-171">**NX_BSD_TIMEOUT** Specifies the timeout in timer ticks on NetX internal calls required by BSD.</span></span> <span data-ttu-id="c5d4f-172">Значение по умолчанию равно 20 \* NX_IP_PERIODIC_RATE.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-172">The default value is 20\*NX_IP_PERIODIC_RATE.</span></span>
- <span data-ttu-id="c5d4f-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: указывает время ожидания в тактах таймера при вызове отключения NetX.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-173">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX disconnect call.</span></span> <span data-ttu-id="c5d4f-174">Значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-174">The default value is 1.</span></span>
- <span data-ttu-id="c5d4f-175">**NX_BSD_PRINT_ERRORS**: если этот параметр задан, то при возвращении состояния ошибки функция BSD возвращает номер строки, где возникла ошибка, и тип ошибки, например NX_SOC_ERROR.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-175">**NX_BSD_PRINT_ERRORS** If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="c5d4f-176">Для использования этой функции разработчику приложения нужно определить выходные данные отладки.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-176">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="c5d4f-177">По умолчанию этот параметр отключен, а выходные данные отладки в файле *nx_bsd.h* не указаны.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-177">The default setting is disabled and no debug output is specified in *nx_bsd.h*</span></span>
- <span data-ttu-id="c5d4f-178">**NX_BSD_TIMER_RATE**: интервал, по истечении которого выполняется периодическая задача таймера BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-178">**NX_BSD_TIMER_RATE** Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="c5d4f-179">Значение по умолчанию — 1 секунда (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-179">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>
- <span data-ttu-id="c5d4f-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: если этот параметр задан, он позволяет выполнять процесс времени ожидания BSD в контексте системного таймера.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-180">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER** If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="c5d4f-181">По умолчанию этот режим отключен.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-181">The default behavior is disabled.</span></span> <span data-ttu-id="c5d4f-182">Эта функция более подробно описана в главе 2, "Установка и использование NetX BSD".</span><span class="sxs-lookup"><span data-stu-id="c5d4f-182">This feature is described in more detail in Chapter 2 "Installation and Use of NetX BSD".</span></span>
- <span data-ttu-id="c5d4f-183">**NX_BSD_ENABLE_DNS**: если этот параметр включен, то NetX BSD будет отправлять запрос DNS по имени узла или IP-адресу узла.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-183">**NX_BSD_ENABLE_DNS** If enabled, NetX BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="c5d4f-184">Требуется, чтобы предварительно был создан и запущен экземпляр DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-184">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="c5d4f-185">По умолчанию эта функция отключена.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-185">By default it is not enabled.</span></span>
- <span data-ttu-id="c5d4f-186">**NX_BSD_IPV4_ADDR_MAX_NUM**: максимальное число IPv4-адресов, возвращаемых службой *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-186">**NX_BSD_IPV4_ADDR_MAX_NUM** Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="c5d4f-187">Вместе с NX_BSD_IPV4_ADDR_MAX_NUM определяет размер пула блоков NetX BSD, nx_bsd_addrinfo_block_pool, используемого для динамического выделения памяти для хранения информации об адресах, возвращаемой *getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-187">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="c5d4f-188">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-188">The default value is 5.</span></span>
- <span data-ttu-id="c5d4f-189">**NX_BSD_IPV4_ADDR_PER_HOST**: определяет максимальное количество IPv4-адресов, сохраняемых для каждого запроса DNS.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-189">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="c5d4f-190">Значение по умолчанию — 5.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-190">The default value is 5.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="c5d4f-191">Параметры сокета BSD</span><span class="sxs-lookup"><span data-stu-id="c5d4f-191">BSD Socket Options</span></span>

<span data-ttu-id="c5d4f-192">Ниже приведен список параметров сокета NetX BSD, которые можно включать (или отключать) во время выполнения для каждого сокета с помощью службы *setsockopt*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-192">The following list of NetX BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

<span data-ttu-id="c5d4f-193">Существуют два разных параметра для *option_level*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-193">There are two different settings for *option_level*.</span></span>

<span data-ttu-id="c5d4f-194">Первый тип параметров сокета времени выполнения — SOL_SOCKET для параметров уровня сокета.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-194">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="c5d4f-195">Чтобы включить параметр уровня сокета, вызовите *setsockopt*, присвоив параметру option_level значение SOL_SOCKET и указав для параметра option_name конкретный параметр, например SO_BROADCAST.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-195">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST.</span></span> <span data-ttu-id="c5d4f-196">Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-196">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="c5d4f-197">Ниже приведен список параметров уровня сокета времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-197">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="c5d4f-198">**SO_BROADCAST**: если этот параметр задан, он позволяет отправлять и получать широковещательные пакеты через сокеты Netx.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-198">**SO_BROADCAST**: If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="c5d4f-199">Это режим по умолчанию для NetX.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-199">This is the default behavior for NetX.</span></span> <span data-ttu-id="c5d4f-200">Эта возможность поддерживается всеми сокетами.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-200">All sockets have this capability.</span></span>
- <span data-ttu-id="c5d4f-201">**SO_ERROR**: используется для получения состояния сокета в предыдущей операции указанного сокета с помощью службы *getsockopt*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-201">**SO_ERROR**: Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="c5d4f-202">Эта возможность поддерживается всеми сокетами.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-202">All sockets have this capability.</span></span>
- <span data-ttu-id="c5d4f-203">**SO_KEEPALIVE**: если этот параметр задан, то он включает функцию проверки активности TCP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-203">**SO_KEEPALIVE**: If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="c5d4f-204">Для этого необходимо, чтобы библиотека NetX была создана с параметром NX_TCP_ENABLE_KEEPALIVE, определенным в файле *nx_user.h*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-204">This requires the NetX library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="c5d4f-205">По умолчанию эта функция отключена.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-205">By default this feature is disabled.</span></span>
- <span data-ttu-id="c5d4f-206">**SO_RCVTIMEO**: задает время ожидания в секундах для получения пакетов через сокеты NetX BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-206">**SO_RCVTIMEO**: This sets the wait option in seconds for receiving packets on NetX BSD sockets.</span></span> <span data-ttu-id="c5d4f-207">Значение по умолчанию — NX_WAIT_FOREVER (0xFFFFFFFF) или, если включена защита от блокировки, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-207">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>
- <span data-ttu-id="c5d4f-208">**SO_RCVBUF**: задает размер окна сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-208">**SO_RCVBUF**: This sets the window size of the TCP socket.</span></span> <span data-ttu-id="c5d4f-209">Значение по умолчанию, NX_BSD_TCP_WINDOW, равно 64 КБ для сокетов TCP протокола BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-209">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="c5d4f-210">Чтобы установить размер больше 65535, необходимо создать библиотеку NetX с определенным параметром NX_TCP_ENABLE_WINDOW_SCALING.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-210">To set the size over 65535 requires the NetX library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>
- <span data-ttu-id="c5d4f-211">**SO_REUSEADDR**: если этот параметр задан, то он позволяет сопоставить несколько сокетов с одним портом.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-211">**SO_REUSEADDR**: If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="c5d4f-212">Как правило, это используется для сокета TCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-212">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="c5d4f-213">Это режим по умолчанию для сокетов NetX.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-213">This is the default behavior of NetX sockets.</span></span>

<span data-ttu-id="c5d4f-214">Вторым типом параметров сокета времени выполнения являются параметры уровня IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-214">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="c5d4f-215">Чтобы включить параметр уровня IP-адреса, вызовите *setsockopt*, задав для параметра option_level значение IP_PROTO, а для option_name — имя параметра, например IP_MULTICAST_TTL.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-215">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL.</span></span> <span data-ttu-id="c5d4f-216">Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение IP_PROTO</span><span class="sxs-lookup"><span data-stu-id="c5d4f-216">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="c5d4f-217">Ниже приведен список параметров уровня IP-адреса времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-217">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="c5d4f-218">**IP_MULTICAST_TTL**: задает срок жизни сокетов UDP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-218">**IP_MULTICAST_TTL**: This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="c5d4f-219">Значение по умолчанию — NX_IP_TIME_TO_LIVE (0x80). Оно задается при создании сокета.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-219">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="c5d4f-220">Это значение можно переопределить, вызвав *setsockopt* с этим параметром сокета.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-220">This value can be overridden by calling *setsockopt* with this socket option.</span></span>
- <span data-ttu-id="c5d4f-221">**IP_ADD_MEMBERSHIP**: если этот параметр задан, то он позволяет включить сокет BSD (применяется только к сокетам UDP) в указанную группу IGMP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-221">**IP_ADD_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>
- <span data-ttu-id="c5d4f-222">**IP_DROP_MEMBERSHIP**: если этот параметр задан, то он позволяет удалить сокет BSD (применяется только к сокетам UDP) из указанной группы IGMP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-222">**IP_DROP_MEMBERSHIP**: If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="c5d4f-223">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="c5d4f-223">Small Example System</span></span>

<span data-ttu-id="c5d4f-224">Пример использования NetX BSD показан на рисунке 1.0 ниже.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-224">An example of how to use NetX BSD is shown in Figure 1.0 below.</span></span> <span data-ttu-id="c5d4f-225">В этом примере показан включаемый файл *nx_bsd.h* (строка 7).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-225">In this example, the include file *nx_bsd.h* is brought in at line 7.</span></span> <span data-ttu-id="c5d4f-226">Далее, в строках 20 и 21 как глобальные переменные создаются экземпляр IP *bsd_ip* и пул пакетов *bsd_pool*.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-226">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="c5d4f-227">Обратите внимание на то, что в этом демонстрационном файле используется драйвер сетевой ОЗУ (виртуальный) (строка 41).</span><span class="sxs-lookup"><span data-stu-id="c5d4f-227">Note that this demo uses a ram (virtual) network driver (line 41).</span></span> <span data-ttu-id="c5d4f-228">В этом примере клиент и сервер будут использовать один и тот же IP-адрес экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-228">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="c5d4f-229">Потоки клиента и сервера создаются в строках 303 и 309 вызовом *tx_application_define*, который настраивает приложение и определяется в строках 293–361.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-229">The client and server threads are created on line 303 and 309 in *tx_application_define* which sets up the application and is defined on lines 293-361.</span></span> <span data-ttu-id="c5d4f-230">После успешного создания экземпляра IP в строке 327 он включается для служб TCP в строке 350.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-230">After IP instance successful creation on line 327, the IP instance is enabled for TCP services on line 350.</span></span> <span data-ttu-id="c5d4f-231">Последнее требование для использования служб BSD — вызов *bsd_initialize* в строке 360 для настройки всех структур данных и ресурсов NetX и ThreadX, необходимых для BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-231">The last requirement before BSD services can be used is to call *bsd_initialize* on line 360 to set up all data structures and NetX, and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="c5d4f-232">В функции входа потока сервера *thread_1_entry*, которая определена в строках 381—397, приложение ожидает, пока драйвер инициализирует NetX с применением параметров сети.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-232">In the server thread entry function, *thread_1_entry,* which is defined on lines 381-397, the application waits for the driver to initialize NetX with network parameters.</span></span> <span data-ttu-id="c5d4f-233">После этого оно вызывает экземпляр *tcpServer*, определенный в строках 146—253, для обработки сведений о конфигурации сокета TCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-233">Once this is done, it calls *tcpServer,* defined on lines 146-253, to handle the details of setting up the TCP server socket.</span></span>

<span data-ttu-id="c5d4f-234">Экземпляр *tcpServer* создает главный сокет, вызывая службу *socket* в строке 159, и привязывает его к сокету ожидания передачи данных, используя вызов *bind* в строке 176.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-234">*tcpServer* creates the master socket by calling the *socket* service on line 159 and binds it to the listening socket using the *bind* call on line 176.</span></span> <span data-ttu-id="c5d4f-235">Затем он настраивается для ожидания передачи запросов соединения в строке 191.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-235">It is then configured for listening for connection requests on line 191.</span></span> <span data-ttu-id="c5d4f-236">Обратите внимание на то, что главный сокет не принимает запрос соединения.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-236">Note that the master socket does not accept a connection request.</span></span> <span data-ttu-id="c5d4f-237">Он выполняется в непрерывном цикле, который каждый раз вызывает метод *select* для обнаружения запросов соединения.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-237">It runs in a continuous loop which calls *select* each time to detect connection requests.</span></span> <span data-ttu-id="c5d4f-238">После вызова службы *accept* в строке 218 запрос соединения назначается дополнительному сокету BSD, выбранному из массива сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-238">A secondary BSD socket chosen from an array of BSD sockets is assigned the connection request after calling the *accept* service on line 218.</span></span>

<span data-ttu-id="c5d4f-239">На стороне клиента функция входа потока клиента, *thread_0_entry*, определенная в строках 366—377, должна также ожидать инициализации драйвером NetX.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-239">On the Client side, the client thread entry function, *thread_0_entry*, defined on lines 366-377, should also wait for NetX to be initialized by the driver.</span></span> <span data-ttu-id="c5d4f-240">На этом этапе нужно просто ожидать, пока это не выполнит сервер.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-240">Here we just wait for the server side to do so.</span></span> <span data-ttu-id="c5d4f-241">Затем вызывается экземпляр *tcpClient*, определенный в строках 54–142, для обработки сведений о конфигурации сокета TCP-клиента и запроса TCP-соединения.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-241">It then calls *tcpClient* defined on line 54-142, to handle the details of setting up the TCP client socket and requesting a TCP connection.</span></span>

<span data-ttu-id="c5d4f-242">Сокет TCP-клиента создается в строке 68.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-242">The TCP client socket is created on line 68.</span></span> <span data-ttu-id="c5d4f-243">Этот сокет привязан к указанному IP-адресу. Он пытается подключиться к TCP-серверу путем вызова *connect* в строке 84.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-243">The socket is bound to the specified IP address and attempts to connect to the TCP server by calling *connect* on line 84.</span></span> <span data-ttu-id="c5d4f-244">Теперь он готов к отправке и получению пакетов.</span><span class="sxs-lookup"><span data-stu-id="c5d4f-244">It is now ready to begin sending and receiving packets.</span></span>

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
