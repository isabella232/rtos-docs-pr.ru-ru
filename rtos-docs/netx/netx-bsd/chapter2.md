---
title: Глава 2. Установка и использование ОСРВ Azure NetX BSD
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c04175ec18dff160faf853d675c9c85c9a0c6fbc5e834c410a7cb97a739c69f8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796707"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>Глава 2. Установка и использование ОСРВ Azure NetX BSD

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента ОСРВ Azure NetX BSD.

## <a name="product-distribution"></a>Распространение продукта

ОСРВ Azure NetX BSD можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/). Этот пакет включает в себя два файла исходного кода и PDF-файл с этим документом:

- **nx_bsd.h**: файл заголовка для NetX BSD;
- **nx_bsd.c**: файл исходного кода C для NetX BSD;
- **nx_bsd.pdf**: руководство пользователя NetX BSD.

Демонстрационные файлы:
- **bsd_demo_tcp.c**
- **bsd_demo_udp.c**

## <a name="netx-bsd-installation"></a>Установка NetX BSD

Чтобы использовать NetX BSD, следует скопировать упомянутый выше дистрибутив целиком в тот же каталог, где установлен экземпляр NetX. Например, если экземпляр NetX установлен в каталоге *\threadx\arm7\green*, то файлы *nx_bsd.h* и *nx_bsd.c* необходимо скопировать в этот каталог.

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>Создание компонентов ThreadX и NetX приложения BSD

### <a name="threadx"></a>ThreadX

Библиотека ThreadX должна определять *bsd_errno* в локальном хранилище потоков. Рекомендуется следующая процедура.

1. В файле *tx_port.h* задайте один из макросов TX_THREAD_EXTENSION следующим образом:

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. Перестройте библиотеку ThreadX.

> [!NOTE]
> Если TX_THREAD_EXTENSION_3 уже используется, пользователь может использовать один из других макросов TX_THREAD_EXTENSION.

### <a name="netx"></a>NetX

Перед использованием NetX BSD необходимо выполнить сборку библиотеки NetX с определенным параметром NX_ENABLE_EXTENDED_NOTIFY_SUPPORT (например, в файле *nx_user.h*). По умолчанию он не определен.

## <a name="using-netx-bsd"></a>Использование NetX BSD

Использовать NetX BSD просто. По сути, в код приложения следует добавить *nx_bsd.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно. После добавления *nx_bsd.h* код приложения сможет использовать службы BSD, описанные далее в этом разделе. В приложение также нужно включить файл *nx_bsd.c* в процессе сборки. Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX BSD.

Чтобы использовать службы NetX BSD, приложение должно создать экземпляр IP, пул пакетов и инициализировать службы BSD, вызвав *bsd_initialize*. Это показано в разделе "Пример небольшой системы" далее в этом руководстве. Ниже приведен прототип.

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

Последние три параметра используются для создания потока для выполнения периодических задач, таких как проверка событий TCP и определение пространства стека потоков.

> [!NOTE]
> В отличие от сокетов BSD, работающих в порядке байтов сети, NetX работает в порядке байтов узла, указанных для процессора узла. В целях обеспечения совместимости исходных файлов макросы htons(), ntohs(), htonl() и ntohl() определены, но без изменений передаваемых аргументов.

## <a name="netx-bsd-limitations"></a>Ограничения NetX BSD

Из-за проблем с производительностью и архитектурой NetX BSD не поддерживает все функции сокетов BSD 4.3.

Флаги INT не поддерживаются для вызовов *send, recv, sendto* и *recvfrom*.

## <a name="netx-bsd-with-dns-support"></a>NetX BSD с поддержкой DNS

Если определен параметр NX_BSD_ENABLE_DNS, то NetX BSD может отправлять запросы DNS для получения сведений об имени узла или IP-адресе узла. Для применения этой функции требуется предварительно создать клиент NetX DNS с помощью службы *nx_dns_create*. Один или несколько известных IP-адресов DNS-серверов должны быть зарегистрированы в экземпляре DNS с помощью службы *nx_dns_server_add* для добавления адресов серверов.

Службы DNS и выделение памяти используются службами *getaddrinfo* и *getnameinfo*.

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Когда приложение BSD вызывает *getaddrinfo* с именем узла, NetX BSD вызывает следующие службы для получения IP-адреса:

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

Для *nx_dns_ipv4_address_by_name_get* в NetX BSD используются области памяти ipv4_addr_buffer. Размер этих буферов определяет (`NX_BSD_IPV4_ADDR_PER_HOST * 4`).

Для сведений об адресе, возвращаемых службой *getaddrinfo*, NetX BSD использует таблицу блоков памяти ThreadX *nx_bsd_addrinfo_pool_memory*, область памяти которой определяется другим набором настраиваемых параметров — *NX_BSD_IPV4_ADDR_MAX_NUM*.

Дополнительные сведения о перечисленных выше параметрах конфигурации см. в разделе **Параметры конфигурации**.

Кроме того, если определен параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES, а для узла указано каноническое имя, то NetX BSD выделит память динамически из созданного ранее пула блоков *_nx_bsd_cname_block_pool*.

> [!NOTE]
> После вызова службы *getaddrinfo* приложение BSD отвечает за освобождение памяти, на которую указывает аргумент res, и ее возвращение в таблицу блоков с помощью службы *freeaddrinfo*.

## <a name="configuration-options"></a>Параметры конфигурации

Настраиваемые пользователем параметры в файле *nx_bsd.h* позволяют приложению точно настроить сокеты NetX BSD в соответствии с конкретными требованиями. Ниже приведен список этих параметров:

- **NX_BSD_TCP_WINDOW**: используется в вызовах create для сокета TCP. 65535 — это стандартный размер окна для Ethernet 100 Мбит/с. Значение по умолчанию — 65535.
- **NX_BSD_SOCKFD_START**: логический индекс для начального значения дескриптора файла сокета BSD. По умолчанию этот параметр имеет значение 32.
- **NX_BSD_MAX_SOCKETS**: указывает максимальное число доступных сокетов на уровне BSD. Это значение должно быть кратно 32. Значение по умолчанию — 32.
- **NX_BSD_SOCKET_QUEUE_MAX**: указывает максимальное число пакетов UDP, хранящихся в очереди приема сокета. Значение по умолчанию — 5.
- **NX_BSD_MAX_LISTEN_BACKLOG**: указывает размер очереди ожидания передачи данных ("невыполненной работы") для сокетов TCP протокола BSD. Значение по умолчанию — 5.
- **NX_MICROSECOND_PER_CPU_TICK**: указывает число микросекунд на прерывание таймера.
- **NX_BSD_TIMEOUT**: указывает время ожидания в тактах таймера для внутренних вызовов NetX, необходимых для BSD. Значение по умолчанию равно 20 * NX_IP_PERIODIC_RATE.
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: указывает время ожидания в тактах таймера при вызове отключения NetX. Значение по умолчанию — 1.
- **NX_BSD_PRINT_ERRORS**: если этот параметр задан, то при возвращении состояния ошибки функция BSD возвращает номер строки, где возникла ошибка, и тип ошибки, например NX_SOC_ERROR. Для использования этой функции разработчику приложения нужно определить выходные данные отладки. По умолчанию этот параметр отключен, а выходные данные отладки в файле *nx_bsd.h* не указаны.
- **NX_BSD_TIMER_RATE**: интервал, по истечении которого выполняется периодическая задача таймера BSD. Значение по умолчанию — 1 секунда (1 * NX_IP_PERIODIC_RATE).
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: если этот параметр задан, он позволяет выполнять процесс времени ожидания BSD в контексте системного таймера. По умолчанию этот режим отключен. Эта функция более подробно описана в главе 2, "Установка и использование NetX BSD".
- **NX_BSD_ENABLE_DNS**: если этот параметр включен, то NetX BSD будет отправлять запрос DNS по имени узла или IP-адресу узла. Требуется, чтобы предварительно был создан и запущен экземпляр DNS-клиента. По умолчанию эта функция отключена.
- **NX_BSD_IPV4_ADDR_MAX_NUM**: максимальное число IPv4-адресов, возвращаемых службой *getaddrinfo*. Вместе с NX_BSD_IPV4_ADDR_MAX_NUM определяет размер пула блоков NetX BSD, nx_bsd_addrinfo_block_pool, используемого для динамического выделения памяти для хранения информации об адресах, возвращаемой *getaddrinfo*. Значение по умолчанию — 5.
- **NX_BSD_IPV4_ADDR_PER_HOST**: определяет максимальное количество IPv4-адресов, сохраняемых для каждого запроса DNS. Значение по умолчанию — 5.

## <a name="bsd-socket-options"></a>Параметры сокета BSD

Ниже приведен список параметров сокета NetX BSD, которые можно включать (или отключать) во время выполнения для каждого сокета с помощью службы *setsockopt*.

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

Существуют два разных параметра для *option_level*.

Первый тип параметров сокета времени выполнения — SOL_SOCKET для параметров уровня сокета. Чтобы включить параметр уровня сокета, вызовите *setsockopt*, присвоив параметру option_level значение SOL_SOCKET и указав для параметра option_name конкретный параметр, например SO_BROADCAST. Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение SOL_SOCKET.

Ниже приведен список параметров уровня сокета времени выполнения.

- **SO_BROADCAST**: если этот параметр задан, он позволяет отправлять и получать широковещательные пакеты через сокеты Netx. Это режим по умолчанию для NetX. Эта возможность поддерживается всеми сокетами.
- **SO_ERROR**: используется для получения состояния сокета в предыдущей операции указанного сокета с помощью службы *getsockopt*. Эта возможность поддерживается всеми сокетами.
- **SO_KEEPALIVE**: если этот параметр задан, то он включает функцию проверки активности TCP. Для этого необходимо, чтобы библиотека NetX была создана с параметром NX_TCP_ENABLE_KEEPALIVE, определенным в файле *nx_user.h*. По умолчанию эта функция отключена.
- **SO_RCVTIMEO**: задает время ожидания в секундах для получения пакетов через сокеты NetX BSD. Значение по умолчанию — NX_WAIT_FOREVER (0xFFFFFFFF) или, если включена защита от блокировки, NX_NO_WAIT (0x0).
- **SO_RCVBUF**: задает размер окна сокета TCP. Значение по умолчанию, NX_BSD_TCP_WINDOW, равно 64 КБ для сокетов TCP протокола BSD. Чтобы установить размер больше 65535, необходимо создать библиотеку NetX с определенным параметром NX_TCP_ENABLE_WINDOW_SCALING.
- **SO_REUSEADDR**: если этот параметр задан, то он позволяет сопоставить несколько сокетов с одним портом. Как правило, это используется для сокета TCP-сервера. Это режим по умолчанию для сокетов NetX.

Вторым типом параметров сокета времени выполнения являются параметры уровня IP-адреса. Чтобы включить параметр уровня IP-адреса, вызовите *setsockopt*, задав для параметра option_level значение IP_PROTO, а для option_name — имя параметра, например IP_MULTICAST_TTL. Чтобы получить параметр, вызовите *getsockopt* для option_name, присвоив параметру option_level значение IP_PROTO

Ниже приведен список параметров уровня IP-адреса времени выполнения.

- **IP_MULTICAST_TTL**: задает срок жизни сокетов UDP. Значение по умолчанию — NX_IP_TIME_TO_LIVE (0x80). Оно задается при создании сокета. Это значение можно переопределить, вызвав *setsockopt* с этим параметром сокета.
- **IP_ADD_MEMBERSHIP**: если этот параметр задан, то он позволяет включить сокет BSD (применяется только к сокетам UDP) в указанную группу IGMP.
- **IP_DROP_MEMBERSHIP**: если этот параметр задан, то он позволяет удалить сокет BSD (применяется только к сокетам UDP) из указанной группы IGMP.

## <a name="small-example-system"></a>Пример небольшой системы

Пример использования NetX BSD показан на рисунке 1.0 ниже. В этом примере показан включаемый файл *nx_bsd.h* (строка 7). Далее, в строках 20 и 21 как глобальные переменные создаются экземпляр IP *bsd_ip* и пул пакетов *bsd_pool*. Обратите внимание на то, что в этом демонстрационном файле используется драйвер сетевой ОЗУ (виртуальный) (строка 41). В этом примере клиент и сервер будут использовать один и тот же IP-адрес экземпляра IP.

Потоки клиента и сервера создаются в строках 303 и 309 вызовом *tx_application_define*, который настраивает приложение и определяется в строках 293–361. После успешного создания экземпляра IP в строке 327 он включается для служб TCP в строке 350. Последнее требование для использования служб BSD — вызов *bsd_initialize* в строке 360 для настройки всех структур данных и ресурсов NetX и ThreadX, необходимых для BSD.

В функции входа потока сервера *thread_1_entry*, которая определена в строках 381—397, приложение ожидает, пока драйвер инициализирует NetX с применением параметров сети. После этого оно вызывает экземпляр *tcpServer*, определенный в строках 146—253, для обработки сведений о конфигурации сокета TCP-сервера.

Экземпляр *tcpServer* создает главный сокет, вызывая службу *socket* в строке 159, и привязывает его к сокету ожидания передачи данных, используя вызов *bind* в строке 176. Затем он настраивается для ожидания передачи запросов соединения в строке 191. Обратите внимание на то, что главный сокет не принимает запрос соединения. Он выполняется в непрерывном цикле, который каждый раз вызывает метод *select* для обнаружения запросов соединения. После вызова службы *accept* в строке 218 запрос соединения назначается дополнительному сокету BSD, выбранному из массива сокетов BSD.

На стороне клиента функция входа потока клиента, *thread_0_entry*, определенная в строках 366—377, должна также ожидать инициализации драйвером NetX. На этом этапе нужно просто ожидать, пока это не выполнит сервер. Затем вызывается экземпляр *tcpClient*, определенный в строках 54–142, для обработки сведений о конфигурации сокета TCP-клиента и запроса TCP-соединения.

Сокет TCP-клиента создается в строке 68. Этот сокет привязан к указанному IP-адресу. Он пытается подключиться к TCP-серверу путем вызова *connect* в строке 84. Теперь он готов к отправке и получению пакетов.

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
