---
title: Глава 2. Установка и использование ОСРВ Azure NetX Duo BSD
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 560621e528c8ce98013ce505ea1511f466317f4a087aa44cc0e70cb4d4b8ed1e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788513"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a>Глава 2. Установка и использование ОСРВ Azure NetX Duo BSD

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX Duo BSD.

## <a name="product-distribution"></a>Распространение продукта

ОСРВ Azure NetX BSD можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/). Этот пакет включает в себя два файла исходного кода и PDF-файл с этим документом:

- **nxd_bsd.h**: файл заголовка для NetX Duo BSD;
- **nxd_bsd.c**: файл исходного кода C для NetX Duo BSD;
- **nxd_bsd.pdf**: PDF-файл с описанием NetX Duo BSD.

Демонстрационные файлы:

- **bsd_demo_udp.c**
- **bsd_demo_tcp.c**
- **bsd_demo_raw.c**

## <a name="netx-duo-bsd-installation"></a>Установка NetX Duo BSD

Чтобы использовать NetX Duo BSD, весь дистрибутив, упомянутый ранее, необходимо скопировать в каталог, где установлен экземпляр NetX Duo. Например, если экземпляр NetX Duo установлен в каталог *\threadx\arm7\green*, то файлы *nxd_bsd.h* и *nxd_bsd.c* необходимо скопировать в этот каталог.

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a>Создание компонентов ThreadX и NetX Duo приложения BSD

### <a name="threadx"></a>ThreadX

Библиотека ThreadX должна определять `bsd_errno` в локальном по отношению к потоку хранилище. Рекомендуется следующая процедура.

1. В файле *tx_port.h* задайте один из макросов TX_THREAD_EXTENSION следующим образом:
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. Перестройте библиотеку ThreadX.

> [!NOTE]
> Если TX_THREAD_EXTENSION_3 уже используется, пользователь может использовать один из других макросов TX_THREAD_EXTENSION.

### <a name="netx-duo"></a>NetX Duo

Перед использованием служб NetX Duo BSD необходимо выполнить сборку библиотеки NetX с определенным параметром NX_ENABLE_EXTENDED_NOTIFY_SUPPORT. По умолчанию он не определен. Если используются сокеты RAW для BSD, то при сборке библиотеки NetX Duo следует определить параметр NX_ENABLE_IP_RAW_PACKET_FILTER.

## <a name="using-netx-duo-bsd"></a>Использование NetX Duo BSD

Проект приложения NetX Duo BSD должен включать в себя файл *nxd_bsd.h*, после которого нужно добавить файлы *tx_api.h* и *nx_api.h*, чтобы иметь возможность использовать службы BSD, описанные далее в этом руководством. В приложение также нужно включить файл *nxd_bsd.c* для процесса сборки. Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX Duo BSD.

Чтобы использовать службы NetX Duo BSD, приложение должно создать экземпляр IP, создать пул пакетов для уровня BSD, чтобы выделять из него пакеты, выделить пространство памяти для внутреннего стека потоков BSD и задать приоритет внутреннего потока BSD. Уровень BSD инициализируется путем вызова *bsd_initialize* и передачи параметров. Это будет показано в разделе "Пример небольшой системы" далее в этом документе, но прототип показан ниже.

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

Параметр default_ip задает экземпляр IP, с которым работает уровень BSD. Пул default_pool используется службами BSD для выделения пакетов. Следующие два параметра, bsd_thread_stack_area и bsd_thread_stack_size определяют область стека, используемую внутренним потоком BSD, а последний параметр, bsd_thread_priority, задает приоритет этого потока.

## <a name="netx-duo-bsd-raw-socket-support"></a>Поддержка сокетов RAW в NetX Duo BSD

NetX Duo BSD также поддерживает сокеты RAW. Чтобы использовать сокеты RAW в NetX Duo BSD, необходимо скомпилировать библиотеку NetX Duo с определенным NX_ENABLE_IP_RAW_PACKET_FILTER. По умолчанию он не определен. После этого приложение должно включить обработку сокетов RAW для созданного ранее экземпляра IP, вызвав *nx_ip_raw_packet_enable*.

Чтобы создать сокет RAW в NetX Duo BSD, приложение использует службу создания сокетов *socket* и указывает семейство протоколов, тип сокета и протокол.

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

Параметр protocolFamily имеет значение AF_INET для сокетов IPv4 или AF_INET6 для сокетов IPv6, при условии, что в экземпляре IP включен протокол IPv6. Для socket_type необходимо задать значение SOCK_RAW. Протокол зависит от приложения.

Чтобы отправлять и получать пакеты RAW, а также закрывать сокет RAW, приложение обычно использует те же самые службы BSD, что и для протокола UDP, например *sendto, recvfrom, select* и *soc_close*. Сокеты RAW не поддерживают службы BSD *accept* и *listen*.

- По умолчанию полученные необработанные данные IPv4 содержат заголовок IPv4.  А полученные необработанные данные IPv6 не содержат заголовок IPv6.

- По умолчанию при отправке пакетов RAW для IPv6 или IPv4 слой программы-оболочки BSD предварительно добавляет заголовок IPv6 или IPv4.

NetX Duo BSD поддерживает дополнительные параметры сокетов RAW, включая IP_RAW_RX_NO_HEADER, IP_HDRINCL и IP_RAW_IPV6_HDRINCL.

Если задан параметр IP_RAW_RX_NO_HEADER, заголовок IPv4 удаляется, чтобы полученные данные не содержали заголовок IPv4, а передаваемая длина сообщения не включает в себя заголовок IPv4.  Для сокетов IPv6 по умолчанию данные, получаемые через сокет RAW, не содержат заголовок IPv6, что эквивалентно заданию параметра IP_RAW_RX_NO_HEADER. Приложение может использовать службу *setsockopt*, чтобы удалить параметр IP_RAW_RX_NO_HEADER. После удаления параметра IP_RAW_RX_NO_HEADER полученные необработанные данные IPv6 будут содержать заголовок IPv6, а передаваемая длина сообщения будет включать в себя заголовок IPv6.

Этот параметр не влияет на передачу данных по протоколам IPv4 и IPv6.

Если задан параметр IP_HDRINCL, приложение добавляет заголовок IPv4 при отправке данных.  Этот параметр не влияет на передачу данных по протоколу IPv6 и не определен по умолчанию. Если задан параметр IP_RAW_IPV6_HDRINCL, приложение добавляет заголовок IPV6 при отправке данных.  Этот параметр не влияет на передачу данных по протоколу IPv4 и не определен по умолчанию.

Параметры IP_HDRINCL и IP_RAW_IPV6_HDRINCL не влияют на получение данных по протоколу IPv4 или IPv6.

> [!NOTE]
> Спецификация сокета BSD 4.3 указывает, что ядро должно копировать пакет RAW в каждый буфер приема сокета. Однако если в NetX Duo BSD создать несколько сокетов, использующих один протокол, то поведение будет не определено.

## <a name="netx-duo-bsd-raw-packet-support"></a>Поддержка пакетов RAW в NetX Duo BSD

Чтобы включить поддержку пакетов RAW для PPPoE, необходимо выполнить сборку программы-оболочки NetX Duo BSD с включенным параметром NX_BSD_RAW_PPPOE_SUPPORT.

Следующая команда создает сокет BSD для обработки пакетов RAW для PPPoE:

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

Текущая реализация BSD поддерживает только два типа протоколов семейства AF_PACKET:

- `ETHERTYPE_PPPOE_DISC`: пакеты Discovery PPPoE. В кадре данных MAC пакеты Discovery имеют тип кадра Ethernet 0x8863.

- `ETHERTYPE_PPPOE_SESS`: пакеты Session PPP. В кадре данных MAC пакеты Session имеют тип кадра Ethernet 0x8864.

Структура `sockaddr_ll` используется для указания параметров при отправке или получении кадров PPPoE.

`struct sockaddr_ll` объявляется следующим образом:

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
> Не все поля в структуре используются `sendto()` или `recvfrom()`. Сведения о настройке `sockaddr_ll` для отправки и получения пакетов PPPoE приведены в описании ниже.

Сокет, созданный в семействе AF_PACKET, можно использовать для отправки пакетов Discovery PPPoE или пакетов Session PPP независимо от указанного протокола. При передаче пакета PPPoE приложение должно подготовить буфер, который включает в себя правильно отформатированный кадр PPPoE, в том числе заголовки MAC (конечный MAC-адрес, исходный MAC-адрес и тип кадра). Размер буфера должен вмещать 14-байтовый заголовок Ethernet.

Структура `sockaddr_ll`, `sll_ifindex`, используется для указания физического интерфейса, который будет использоваться для отправки этого пакета. Остальные поля в структуре не используются. Значения, заданные для неиспользуемых полей, игнорируются внутренними операциями BSD.

В следующем блоке кода показано, как передать пакет PPPoE.

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

Возвращаемое значение указывает количество переданных байтов. Так как пакеты PPPoE на основаны на сообщениях, при успешной передаче число отправленных байтов соответствует размеру пакета, включая 14-байтовый заголовок Ethernet.

Пакеты PPPoE можно получить с помощью `recvfrom()`. Буфер приема должен быть достаточно большим, чтобы вместить сообщения размера MTU для Ethernet. Полученный пакет PPPoE включает в себя 14-байтовый заголовок Ethernet. При получении пакетов PPPoE пакеты Discovery PPPoE могут быть получены только сокетом, созданным с использованием протокола `ETHERTYPE_PPPOE_DISC`. Аналогично, пакеты Session PPP могут быть получены только сокетом, созданным с использованием протокола `ETHERTYPE_PPPOE_SESS`. Если для одного типа протокола создано несколько сокетов, поступающие пакеты PPPoE перенаправляются в сокет, созданный первым. Если первый сокет, созданный для протокола, закрыт, для получения этих пакетов используется следующий сокет в порядке создания.

После получения пакета PPPoE в `sockaddr_ll` структуре являются допустимыми следующие поля:
- **sll_family**: задается внутренними процессами BSD и имеет значение AF_PACKET BSD;
- **sll_ifindex**: указывает интерфейс, из которого получен пакет;
- **sll_protocol**: задает тип полученного пакета: `ETHERTYPE_PPPOE_DISC` или `ETHERTYPE_PPPOE_SESS`.

## <a name="eliminating-internal-bsd-thread"></a>Исключение внутреннего потока BSD

По умолчанию в BSD используется внутренний поток для части операций. В системах с жесткими ограничениями памяти при сборке экземпляра BSD можно определить параметр NX_BSD_TIMEOUT_PROCESS_IN_TIMER. Он исключит внутренний поток BSD, а для выполнения той же обработки будет использоваться внутренний таймер. Это освобождает объем памяти, необходимый для блока управления внутренним потоком BSD и стека внутреннего потока BSD. Однако общая интенсивность операций с таймером значительно увеличится, а обработка BSD может выполняться с более высоким приоритетом, чем требуется.

Чтобы настроить сокеты BSD для выполнения в контексте таймера ThreadX, определите NX_BSD_TIMEOUT_PROCESS_IN_TIMER в *nxd_bsd.h*. Если уровень BSD настроен для выполнения задач BSD в контексте таймера, то в вызове *bsd_initialize* игнорируются приведенные ниже три параметра, и для них должно быть задано значение NULL:

- **bsd_thread_stack_area**
- **bsd_thread_stack_size**
- **bsd_thread_priority**

## <a name="netx-duo-bsd-with-dns-support"></a>NetX Duo BSD с поддержкой DNS

Если определен параметр NX_BSD_ENABLE_DNS, то NetX Duo BSD может отправлять запросы DNS для получения сведений об имени узла или IP-адресе узла. Для применения этой функции требуется предварительно создать клиент NetX DNS с помощью службы *nx_dns_create*. Один или несколько известных IP-адресов DNS-серверов должны быть зарегистрированы в экземпляре DNS с помощью службы *nx_dns_server_add* (для добавления адресов серверов IPv4) или службы *nxd_dns_server_add* (для добавления адресов серверов IPv4 или IPv6).

Службы DNS и выделение памяти используются службами *getaddrinfo* и *getnameinfo*.

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Когда приложение BSD вызывает *getaddrinfo* с именем узла, NetX BSD вызывает следующие службы для получения IP-адреса:

- **nx_dns_ipv4_address_by_name_get**
- **nxd_dns_ipv6_address_by_name_get**
- **nx_dns_cname_get**

Для *nx_dns_ipv4_address_by_name_get* и *nxd_dns_ipv6_address_by_name_get* NetX BSD использует области памяти ipv4_addr_buffer и ipv6_addr_buffer соответственно. Размер этих буферов равен NX_BSD_IPV4_ADDR_PER_HOST * 4 и NX_BSD_IPV6_ADDR_PER_HOST * 16 соответственно.

Для возвращения сведений об адресе из функции *getaddrinfo* NetX BSD использует таблицу блоков памяти ThreadX, nx_bsd_addrinfo_pool_memory, область памяти которой определяется другим набором настраиваемых параметров, NX_BSD_IPV4_ADDR_MAX_NUM и NX_BSD_IPV6_ADDR_MAX_NUM.

Дополнительные сведения о перечисленных выше параметрах конфигурации см. в разделе **Общие параметры конфигурации**.

Кроме того, если определен параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES, а входные данные узла являются каноническим именем, то NetX Duo BSD выделит память динамически из созданного ранее пула блоков _nx_bsd_cname_block_pool.

> [!NOTE]
> После вызова службы *getaddrinfo* приложение BSD отвечает за освобождение памяти, на которую указывает аргумент res, и ее возвращение в таблицу блоков с помощью службы *freeaddrinfo*.

## <a name="netx-duo-bsd-limitations"></a>Ограничения NetX Duo BSD

Из-за проблем с производительностью и архитектурой NetX Duo BSD не поддерживает все функции сокетов BSD 4.3:

Флаги INT не поддерживаются для вызовов *send, recv, sendto* и *recvfrom*.

## <a name="general-configuration-options"></a>Общие параметры конфигурации

Настраиваемые пользователем параметры в файле *nxd_bsd.h* позволяют приложению точно настроить сокеты NetX Duo BSD в соответствии с требованиями этого приложения.

Ниже приведен список настраиваемых параметров, задаваемых во время компиляции.

- **NX_BSD_TCP_WINDOW**: используется в вызовах create для сокета TCP. 64 КБ — это стандартный размер окна для Ethernet 100 Мбит/с. Значение по умолчанию — 65535.

- **NX_BSD_SOCKFD_START**: логический индекс для начального значения дескриптора файла сокета BSD. По умолчанию этот параметр имеет значение 32.

- **NX_BSD_MAX_SOCKETS**: указывает максимальное число доступных сокетов на уровне BSD. Это значение должно быть кратно 32. Значение по умолчанию — 32.

- **NX_BSD_SOCKET_QUEUE_MAX**: указывает максимальное число пакетов UDP, хранящихся в очереди приема сокета. Значение по умолчанию — 5.

- **NX_BSD_MAX_LISTEN_BACKLOG**: указывает размер очереди ожидания передачи данных ("невыполненной работы") для сокетов TCP протокола BSD. Значение по умолчанию — 5.

- **NX_MICROSECOND_PER_CPU_TICK**: указывает число микросекунд на такт таймера планировщика.

- **NX_BSD_TIMEOUT**: указывает время ожидания в тактах таймера для внутренних вызовов NetX Duo, необходимых для BSD. Значение по умолчанию равно 20 * NX_IP_PERIODIC_RATE.

- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: указывает время ожидания в тактах таймера при вызове отключения NetX Duo. Значение по умолчанию — 1.

- **NX_BSD_PRINT_ERRORS**: если этот параметр задан, то при возвращении состояния ошибки функция BSD возвращает номер строки, где возникла ошибка, и тип ошибки, например NX_SOC_ERROR. Для использования этой функции разработчику приложения нужно определить выходные данные отладки. По умолчанию этот параметр отключен, а выходные данные отладки в файле *nxd_bsd.h* не указаны.

- **NX_BSD_TIMER_RATE**: интервал, по истечении которого выполняется периодическая задача таймера BSD. Значение по умолчанию — 1 секунда (1 * NX_IP_PERIODIC_RATE).

- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: если этот параметр задан, он позволяет выполнять процесс времени ожидания BSD в контексте системного таймера. По умолчанию этот режим отключен. Эта функция более подробно описана в главе 2, "Установка и использование NetX Duo BSD".

- **NX_BSD_RAW_PPPOE_SUPPORT**: включение поддержки пакетов RAW для PPPoE. По умолчанию этот параметр отключен.

- **NX_BSD_ENABLE_DNS**: если этот параметр включен, то NetX Duo BSD будет отправлять запрос DNS по имени узла или IP-адресу узла. Требуется, чтобы предварительно был создан и запущен экземпляр DNS-клиента. По умолчанию эта функция отключена.

- **NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: определяет размер таблицы сокетов RAW. Значение должно быть степенью числа 2. NetX BSD создает массив сокетов типа NX_BSD_SOCKETS для отправки и получения пакетов RAW. Параметр NX_ENABLE_IP_RAW_PACKET_FILTER должен быть включен. Значение по умолчанию — 32.

- **NX_BSD_IPV4_ADDR_MAX_NUM**: максимальное число IPv4-адресов, возвращаемых службой *getaddrinfo*. Вместе с NX_BSD_IPV6_ADDR_MAX_NUM определяет размер пула блоков NetX BSD, nx_bsd_addrinfo_block_pool, используемого для динамического выделения памяти для хранения информации об адресах, возвращаемой *getaddrinfo*. Значение по умолчанию — 5.

- **NX_BSD_IPV6_ADDR_MAX_NUM**: максимальное число IPv6-адресов, возвращаемых службой *getaddrinfo*. Вместе с NX_BSD_IPV4_ADDR_MAX_NUM определяет размер пула блоков NetX BSD, nx_bsd_addrinfo_block_pool, используемого для динамического выделения памяти для хранения информации об адресах, возвращаемой *getaddrinfo*.

- **NX_BSD_IPV4_ADDR_PER_HOST**: определяет максимальное количество IPv4-адресов, сохраняемых для каждого запроса DNS. Значение по умолчанию — 5.

- **NX_BSD_IPV6_ADDR_PER_HOST**: определяет максимальное количество IPv6-адресов, сохраняемых для каждого запроса DNS. Значение по умолчанию — 2.

## <a name="bsd-socket-options"></a>Параметры сокета BSD

Ниже приведен список параметров сокета NetX Duo BSD, которые можно включать (или отключать) во время выполнения для каждого сокета с помощью службы *setsockopt*.

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

Существуют два разных параметра для option_level.

Первый тип параметров сокета времени выполнения — SOL_SOCKET для параметров уровня сокета. Чтобы включить параметр уровня сокета, вызовите *setsockopt*, присвоив параметру option_level значение SOL_SOCKET и указав для параметра option_name конкретный параметр, например SO_BROADCAST *.* Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение SOL_SOCKET.

Ниже приведен список параметров уровня сокета времени выполнения.

- **SO_BROADCAST**: если этот параметр задан, он позволяет отправлять и получать широковещательные пакеты через сокеты Netx. Это режим по умолчанию для NetX Duo. Эта возможность поддерживается всеми сокетами.

- **SO_ERROR**: используется для получения состояния сокета в предыдущей операции указанного сокета с помощью службы *getsockopt*. Эта возможность поддерживается всеми сокетами.

- **SO_KEEPALIVE**: если этот параметр задан, то он включает функцию проверки активности TCP. Для этого необходимо, чтобы библиотека NetX Duo была создана с параметром NX_TCP_ENABLE_KEEPALIVE, определенным в файле *nx_user.h*. По умолчанию эта функция отключена.

- **SO_RCVTIMEO**: задает время ожидания в секундах для получения пакетов через сокеты NetX Duo BSD. Значение по умолчанию — NX_WAIT_FOREVER (0xFFFFFFFF) или, если включена защита от блокировки, NX_NO_WAIT (0x0).

- **SO_RCVBUF**: задает размер окна сокета TCP. Значение по умолчанию, NX_BSD_TCP_WINDOW, равно 64 КБ для сокетов TCP протокола BSD. Чтобы установить размер больше 65535, необходимо создать библиотеку NetX Duo с определенным параметром NX_TCP_ENABLE_WINDOW_SCALING.

- **SO_REUSEADDR**: если этот параметр задан, то он позволяет сопоставить несколько сокетов с одним портом. Как правило, это используется для сокета TCP-сервера. Это режим по умолчанию для сокетов NetX Duo.

Вторым типом параметров сокета времени выполнения являются параметры уровня IP-адреса. Чтобы включить параметр уровня IP-адреса, вызовите *setsockopt*, задав для параметра option_level значение IP_PROTO, а для option_name — имя параметра, например IP_MULTICAST_TTL *.* Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение IP_PROTO

Ниже приведен список параметров уровня IP-адреса времени выполнения.

- **IP_MULTICAST_TTL**: задает срок жизни сокетов UDP. Значение по умолчанию — NX_IP_TIME_TO_LIVE (0x80). Оно задается при создании сокета. Это значение можно переопределить, вызвав *setsockopt* с этим параметром сокета.

- **IP_RAW_IPV6_HDRINCL**: если этот параметр задан, то вызывающее приложение должно добавить заголовок IPv6 и необязательные заголовки приложения в данные, передаваемые в сокеты RAW для IPv6, созданные экземпляром BSD. Чтобы использовать этот параметр, необходимо включить обработку сокетов RAW в задаче IP.

- **IP_ADD_MEMBERSHIP**: если этот параметр задан, то он позволяет включить сокет BSD (применяется только к сокетам UDP) в указанную группу IGMP.

- **IP_DROP_MEMBERSHIP**: если этот параметр задан, то он позволяет удалить сокет BSD (применяется только к сокетам UDP) из указанной группы IGMP.

- **IP_HDRINCL**: если этот параметр задан, то вызывающее приложение должно добавить заголовок IP и необязательные заголовки приложения в данные, передаваемые в сокеты RAW для IPv4, созданные в BSD. Чтобы использовать этот параметр, необходимо включить обработку сокетов RAW в задаче IP.

- **IP_RAW_RX_NO_HEADER**: если этот параметр не задан, заголовок IPv6 добавляется в полученные данные для сокетов RAW для IPv6, созданных в BSD. В протоколе BSD заголовки IPv6 по умолчанию удаляются в сокетах RAW для IPv6, а длина пакета не включает в себя заголовок IPv6.

Если этот параметр задан, то заголовок IPv4 удаляется из полученных данных в сокетах RAW для BSD типа IPv4. В протоколе BSD заголовки IPv4 по умолчанию добавляются в сокеты RAW для IPv4, а длина пакета включает в себя заголовок IPv4.

Этот параметр не влияет на данные, передаваемые по протоколам IPv4 и IPv6.

## <a name="small-ipv4-example"></a>Пример небольшой системы IPv4

Ниже приведен пример использования служб NetX Duo BSD для сетей IPv4. В этом примере в строке 8 добавлен включаемый файл *nxd_bsd.h*. Далее, в строках 20 и 21 как глобальные переменные создаются экземпляр IP *bsd_ip* и пул пакетов *bsd_pool*. Обратите внимание на то, что в этом демонстрационном файле используется драйвер сетевой ОЗУ, *_nx_ram_network_driver*. В этом примере клиент и сервер будут использовать один и тот же IP-адрес экземпляра IP.

Потоки клиента и сервера создаются в строках 62 и 68. Пул пакетов BSD для передачи пакетов создается в строке 78 и используется при создании экземпляра IP в строке 87. Обратите внимание на то, что задаче потока IP назначается приоритет 1 в вызове *nx_ip_create*. Этот поток должен быть задачей с наивысшим приоритетом, определенной в программе, чтобы обеспечить оптимальную производительность NetX.

В строках 88 и 110 для экземпляра IP включаются службы ARP и TCP соответственно. Последнее требование, которое необходимо выполнить, чтобы использовать службы BSD, — вызвать функцию *bsd_initialize* в строке 120. Это требуется, чтобы настроить все структуры данных, а также ресурсы NetX и ThreadX, необходимые для протокола BSD.

Функция входа потока сервера определена далее. Сокет TCP для BSD создается в строке 149. IP-адрес и порт сервера задаются в строках 160–163. Обратите внимание на использование макросов обработки порядка байтов узла и сети *htonl* и *htons*, применяемых к IP-адресу и порту. Многобайтовые данные передаются в службы BSD в порядке байтов сети, что соответствует спецификации сокета BSD.

Затем в строке 166 главный сокет сервера привязывается к порту с помощью службы *bind*. В строке 180 с помощью службы *listen* определяется сокет ожидания передачи запросов TCP-соединения. После этого функция потока сервера, *thread_server_entry*, выполняет циклические проверки событий получения с помощью вызова *select* в строке 202. Если событие получения представляет собой запрос соединения, который определяется путем сравнения списка готовности к чтению, вызывается метод *accept* в строке 213. В строке 223 назначается дочерний сокет сервера для выполнения запроса соединения, который добавляется в главный список сокетов TCP-сервера, подключенных к клиенту. Если новые запросы соединения отсутствуют, поток сервера проверяет все подключенные в данный момент сокеты на наличие событий получения в цикле for, который начинается в строке 236. При обнаружении ожидающего события получения он будет вызывать службы *send* и *recv* для этого сокета, пока получение данных не завершится (подключение закроется на другой стороне), а сокет не будет закрыт с помощью службы *soc_close* в строке 277.

После настройки потока сервера функция входа потока клиента *thread_client_entry* создает сокет в строке 326 и подключается к сокету TCP-сервера с помощью вызова *connect* в строке 337. Затем она выполняет циклы отправки и получения пакетов, используя службы *send* и *recv* соответственно. Когда получение данных завершается, она закрывает сокет в строке 398 с помощью службы *soc_close*. После отключения функция входа потока клиента создает новый сокет TCP и отправляет еще один запрос соединения в цикле while, который начинается в строке 321.

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

## <a name="small-ipv6-example-system"></a>Пример небольшой системы IPv6

Пример использования служб NetX Duo BSD для сетей IPv6 описан в приведенной ниже программе. Этот пример очень похож на демонстрационную программу IPv4, описанную выше, за исключением нескольких важных отличий.

Обработка потоков клиента и сервера, пула пакетов BSD, экземпляра IP и инициализация BSD выполняются так же, как и для сокетов IPv4 для BSD.

В функции входа потока сервера *thread_server_entry* в строках 145–148 определяется пара переменных IPv6 с типом данных *sockaddr_in6* и *NXD_ADDRESS*. Тип данных NXD_ADDRESS фактически позволяет хранить как IPv4-адреса, так и IPv6-адреса.

Затем в строках 161 и 169 поток сервера включает протоколы IPv6 и ICMPv6 для экземпляра IP, используя службы *nxd_ipv6_enable* и *nxd_icmpv6_enable* соответственно. Затем в экземпляре регистрируются локальный и глобальный IP-адреса канала. Это делается с помощью службы *nxd_ipv6_address_set* в строках 180 и 195. Затем он ожидает достаточно долго, чтобы задача потока IP выполнила протокол обнаружения повторяющихся адресов, и регистрирует эти адреса в качестве допустимых адресов в вызове *tx_thread_sleep* в строке 201.

Затем в строке 204 создается сокет TCP-сервера с входным аргументом типа сокета, равным AF_INET6. IPv6-адрес и порт сокета задаются в строках 216–221. Еще раз обратите внимание на использование макросов *htonl* и *htons* для передачи данных в порядке байтов сети для служб сокетов BSD. С этого места функция входа потока сервера практически такая же, как в примере для IPv4.

Далее определяется функция входа потока клиента, *thread_client_entry*. Обратите внимание на то, что так как TCP-клиент в этом примере использует те же экземпляр IP и IPv6-адрес, что и TCP-сервер, нам не нужно снова включать службы IPv6 или ICMPv6 для экземпляра IP. Кроме того, этот IPv6-адрес уже зарегистрирован в экземпляре IP. Вместо этого функция входа потока клиента в строке 368 просто ожидает, пока сервер не будет настроен. Адрес и порт сервера задаются с помощью макросов обработки порядка байтов сети в строках 387–392, после чего клиент может подключиться к TCP-серверу в строке 412. Обратите внимание на то, что типы данных локальных IP-адресов в строках 378–383 используются только для демонстрации служб *getsockname* и *getpeername* в строках 425 и 434 соответственно. Так как данные поступают из сети, в строках 378–383 используются макросы обработки порядка байтов узла и сети.

Затем функция входа потока клиента входит в цикл, в котором она создает сокет TCP, устанавливает TCP-подключение и отправляет и получает данные с помощью TCP-сервера до тех пор, пока не будут получены все данные, практически как в примере для IPv4. Затем она закрывает сокет в строке 483, недолго ожидает, после чего создает другой сокет TCP и запрашивает соединение с TCP-сервером.

Одно важное отличие от примера для IPv4 заключается в том, что в вызовах *socket* сокет IPv6 указывается с входным аргументом AF_INET6. Другое важное отличие состоит в том, что вызов *connect* TCP-клиента принимает тип данных *sockaddr_in6*, а аргумент length имеет значение размера типа данных *sockaddr_in6*.

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
