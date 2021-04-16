---
title: Глава 2. Установка и использование NetX Duo HTTP для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Duo HTTP для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9a3ea37b180ab57a8dcd269092638fa74589836a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814696"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-http"></a>Глава 2. Установка и использование NetX Duo HTTP для ОСРВ Azure

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента NetX Duo HTTP для ОСРВ Azure.

## <a name="product-distribution"></a>Распространение продукта

NetX Duo для ОСРВ Azure можно получить из нашего общедоступного репозитория исходного кода по адресу [https://github.com/azure-rtos/netxduo/](https://github.com/azure-rtos/netxduo/).

 - **nxd_http_client.h** — файл заголовка HTTP-клиента для NetX Duo.
 - **nxd_http_server.h** — файл заголовка HTTP-сервера для NetX Duo.
 - **nxd_http_client.c** — исходный файл на C HTTP-клиента для NetX Duo.
 - **nxd_http_server.c** — исходный файл на C HTTP-сервера для NetX Duo.
 - **nx_md5.c** — алгоритмы хэширования MD5.
 - **filex_stub.h** — файл заглушки при отсутствии FileX.
 - **nxd_http.pdf** — описание HTTP для NetX Duo.
 - **demo_netxduo_http.c** — демонстрация HTTP в NetX Duo.

## <a name="http-installation"></a>Установка HTTP

Чтобы использовать HTTP для NetX Duo, весь дистрибутив, упомянутый ранее, должен быть скопирован в тот же каталог, где установлен NetX Duo. Например, если NetX Duo установлен в каталог *\threadx\arm7\green*, файлы *nxd_http_client.h* и *nxd_http_client.c* будут использоваться для приложений HTTP-клиента NetX Duo, а *nxd_http_server.h* и *nxd_http_server.c* — для приложений HTTP-сервера NetX Duo. *nx_md5.c* нужно скопировать в этот каталог. Для запуска демонстрационного приложения ram driver файлы клиента и сервера NetX Duo HTTP нужно скопировать в один каталог.

## <a name="using-http"></a>Использование HTTP

Использовать HTTP для NetX Duo очень просто. Код приложения должен только включать *nxd_http_client.h* и (или) *nxd_http_server.h* после включения *tx_api.h*, *fx_api.h* и *nx_api.h* для использования ThreadX, FileX и NetX Duo соответственно. После добавления файлов HTTP-заголовков код приложения сможет выполнять вызовы функций HTTP, указанные далее в этом руководстве. Приложение также должно включать *nxd_http_client.c*, *nxd_http_server.c* и *md5.c* в ходе сборки. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования NetX Duo HTTP.

> [!NOTE]
> Если NX_HTTP_DIGEST_ENABLE не указывается в ходе сборки, файл md5.c не нужно добавлять в приложение. Аналогично, если возможности HTTP-клиента не требуются, файл *nxd_http_client.c* можно не добавлять.

> [!NOTE]
> Так как HTTP использует TCP-службы NetX Duo, TCP нужно включить с помощью вызова *nx_tcp_enable* до использования HTTP.

## <a name="small-example-system"></a>Пример небольшой системы

Пример того, насколько просто использовать NetX Duo HTTP, показан на рисунке 1.1 ниже. Этот пример работает со службами duo, доступными в размещении #define USE_DUO в строке 23 в NetX Duo HTTP. В противном случае используется устаревший эквивалент NetX HTTP (только IPv4). Разработчикам рекомендуется перевести существующие приложения на использование HTTP-служб NetX Duo.

Чтобы указать обмен данными по протоколу IPv6, приложение определяет IPTYPE со значением IPv6 в строке 24.

В этом примере файлы HTTP *nxd_http_client.h* и *nxd_http_server.h* добавляются с помощью include в строках 8 и 9. Затем в строках 89–112 создаются вспомогательный поток HTTP-сервера, пул пакетов и экземпляр IP. Экземпляр IP HTTP-сервера должен поддерживать TCP, как можно видеть в строке 137. Собственно HTTP-сервер создается в строке 159.

Затем создается HTTP-клиент. Сначала создается поток клиента в строке 172, а после этого создается пул пакетов и экземпляр IP (аналогично HTTP-серверу) в строках 186–200. Опять же, экземпляр IP HTTP-клиента должен поддерживать TCP (строка 217).

После этого запускается поток HTTP-сервера, и его первой задачей является подтверждение собственного IP-адреса в NetX Duo (строки 423–450). Теперь HTTP-сервер может принимать запросы.

Первая задача потока HTTP-клиента — создать и отформатировать носитель FileX (строки 236 и 260). После инициализации носителя создается HTTP-клиент в строке 271. Это необходимо сделать до того, как HTTP-сервер сможет обслуживать HTTP-запросы. Затем он должен подтвердить собственный IP-адрес с помощью NetX Duo, что он делает в строках 282–316. HTTP-клиент затем создает и отправляет файл client_test.html HTTP-серверу, недолго ждет ответа и предпринимает попытку получить файл обратно от HTTP-сервера.

> [!NOTE]
> API HTTP-клиента использует другую службу, если протокол IPv6 не поддерживается (*nx_http_client_put_start* в строке 343 и *nx_http_client_get_start* в строке 399). Это позволяет NetX Duo поддерживать существующие приложения HTTP-клиента NetX.

> [!NOTE]
> Вызовы API HTTP-клиента выполняются с относительно небольшим временем ожидания. Возможно, потребуется увеличить время ожидания, если HTTP-клиент обменивается данными с загруженным сервером или удаленным сервером с медленным процессором.

```c
1    /* This is a small demo of the NetX Duo HTTP Client Server API running on a
2       high-performance NetX Duo TCP/IP stack. This demo is applicable for
3       either IPv4 or IPv6 enabled applications. */
4    
5    #include   "tx_api.h"
6    #include   "fx_api.h"
7    #include   "nx_api.h"
8    #include   "nxd_http_client.h"
9    #include   "nxd_http_server.h"
10   
11   #define     DEMO_STACK_SIZE         2048  
12   
13   /* Set up FileX and file memory resources. */
14   CHAR            *ram_disk_memory;
15   FX_MEDIA        ram_disk;
16   unsigned char   media_memory[512];
17      
18   /* Define device drivers. */
19   extern void _fx_ram_driver(FX_MEDIA *media_ptr);
20   VOID        _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
22   
23   #define USE_DUO        /* Use the duo service (not legacy netx) */
24   #define IPTYPE   6       /* Send packets over IPv6 */
25
26   /* Set up the HTTP client. */
27   TX_THREAD       client_thread;
28   NX_PACKET_POOL  client_pool;
29   NX_HTTP_CLIENT  my_client;
30   NX_IP           client_ip;
31   #define         CLIENT_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
32   void            thread_client_entry(ULONG thread_input);
33   
34   #define HTTP_SERVER_ADDRESS  IP_ADDRESS(1,2,3,4)
35   #define HTTP_CLIENT_ADDRESS  IP_ADDRESS(1,2,3,5)
36   
37   /* Set up the HTTP server */
38   
39   NX_HTTP_SERVER  my_server;
40   NX_PACKET_POOL  server_pool;
41   TX_THREAD       server_thread;
42   NX_IP           server_ip;
43   #define         SERVER_PACKET_SIZE  (NX_HTTP_SERVER_MIN_PACKET_SIZE * 2)
44   
45   void            thread_server_entry(ULONG thread_input);
46   #ifdef FEATURE_NX_IPV6
47   NXD_ADDRESS     server_ip_address;
48   #endif
49   
50   
51   /* Define the application's authentication check. This is called by
52      the HTTP server whenever a new request is received. */
53   UINT  authentication_check(NX_HTTP_SERVER *server_ptr, UINT request_type,
54               CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
55   {
56   
57       /* Just use a simple name, password, and realm for all
58          requests and resources. */
59       *name =     "name";
60       *password = "password";
61       *realm =    "NetX Duo HTTP demo";
62   
63       /* Request basic authentication. */
64       return(NX_HTTP_BASIC_AUTHENTICATE);
65   }
66   
67   /* Define main entry point. */
68   
69   int main()
70   {
71   
72       /* Enter the ThreadX kernel. */
73       tx_kernel_enter();
74   }
75   
76   
77   /* Define what the initial system looks like. */
78   void    tx_application_define(void *first_unused_memory)
79   {
80   
81   CHAR    *pointer;
82   UINT    status;
83   
84       
85       /* Setup the working pointer. */
86       pointer =  (CHAR *) first_unused_memory;
87   
88       /* Create a helper thread for the server. */
89       tx_thread_create(&server_thread, "HTTP Server thread", thread_server_entry, 0,  
90                        pointer, DEMO_STACK_SIZE,
91                        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
92   
93       pointer =  pointer + DEMO_STACK_SIZE;
94   
95       /* Initialize the NetX system. */
96       nx_system_initialize();
97   
98       /* Create the server packet pool. */
99       status =  nx_packet_pool_create(&server_pool, "HTTP Server Packet Pool",
        SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);
100
101  
102      pointer = pointer + SERVER_PACKET_SIZE * 4;
103  
104      /* Check for pool creation error. */
105      if (status)
106      {
107  
108          return;
109      }
110  
111      /* Create an IP instance. */
112      status = nx_ip_create(&server_ip, "HTTP Server IP", HTTP_SERVER_ADDRESS,
113                            0xFFFFFF00UL, &server_pool, _nx_ram_network_driver,
114                            pointer, 4096, 1);
115  
116      pointer =  pointer + 4096;
117  
118      /* Check for IP create errors. */
119      if (status)
120      {
121          printf("nx_ip_create failed. Status 0x%x\n", status);
122          return;
123      }
124  
125      /* Enable ARP and supply ARP cache memory for the server IP instance. */
126      status = nx_arp_enable(&server_ip, (void *) pointer, 1024);
127  
128      /* Check for ARP enable errors. */
129      if (status)
130      {
131          return;
132      }
133  
134      pointer = pointer + 1024;
135  
136       /* Enable TCP traffic. */
137      status = nx_tcp_enable(&server_ip);
138  
139      if (status)
140      {
141          return;
142      }
143  
144  #if (IP_TYPE==6)
145  
146      /* Set up HTTPv6 server, but we have to wait till its address has been
147         validated before we can start the thread_server_entry thread. */
148  
149      /* Set up the server's IPv6 address here. */
150      server_ip_address.nxd_ip_address.v6[3] = 0x105;
151      server_ip_address.nxd_ip_address.v6[2] = 0x0;
152      server_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
153      server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
154      server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
155  
156  #endif
157  
158      /* Create the NetX HTTP Server. */
159      status = nx_http_server_create(&my_server, "My HTTP Server", &server_ip,
            &ram_disk, pointer, 2048, &server_pool, authentication_check,
            NX_NULL);
160
161      if (status)
162      {
163          return;
164      }
165  
166      pointer =  pointer + 2048;
167  
168      /* Save the memory pointer for the RAM disk. */
169      ram_disk_memory =  pointer;
170  
171      /* Create the HTTP client thread. */
172      status = tx_thread_create(&client_thread, "HTTP Client", thread_client_entry, 0,  
173                       pointer, DEMO_STACK_SIZE,
174                       2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
175  
176      pointer =  pointer + DEMO_STACK_SIZE;
177  
178      /* Check for thread create error. */
179      if (status)
180      {
181  
182          return;
183      }
184  
185      /* Create the Client packet pool. */
186      status =  nx_packet_pool_create(&client_pool, "HTTP Client Packet Pool",
 SERVER_PACKET_SIZE, pointer, SERVER_PACKET_SIZE*4);

187
188  
189      pointer = pointer + SERVER_PACKET_SIZE * 4;
190  
191      /* Check for pool creation error. */
192      if (status)
193      {
194  
195          return;
196      }
197  
198  
199      /* Create an IP instance. */
200      status = nx_ip_create(&client_ip, "HTTP Client IP", HTTP_CLIENT_ADDRESS,
201                            0xFFFFFF00UL, &client_pool, _nx_ram_network_driver,
202                            pointer, 2048, 1);
203  
204      pointer =  pointer + 2048;
205  
206      /* Check for IP create errors. */
207      if (status)
208      {
209          return;
210      }
211  
212      nx_arp_enable(&client_ip, (void *) pointer, 1024);
213  
214      pointer =  pointer + 2048;
215  
216       /* Enable TCP traffic. */
217      nx_tcp_enable(&client_ip);
218  
219      return;
220  }
221  
222  
223  VOID thread_client_entry(ULONG thread_input)
224  {
225  
226  UINT            status;
227  NX_PACKET       *my_packet;
228  #ifdef FEATURE_NX_IPV6
229  NXD_ADDRESS     client_ip_address;
230  UINT            address_index;
230  #endif
231  
232  
233      /* Format the RAM disk - the memory for the RAM disk was setup in
234        tx_application_define above. This must be set up before the client(s) start
235        sending requests. */
236      status = fx_media_format(&ram_disk,
237                              _fx_ram_driver,         // Driver entry
238                              ram_disk_memory,        // RAM disk memory pointer
239                              media_memory,           // Media buffer pointer
240                              sizeof(media_memory),   // Media buffer size
241                              "MY_RAM_DISK",          // Volume Name
242                              1,                      // Number of FATs
243                              32,                     // Directory Entries
244                              0,                      // Hidden sectors
245                              256,                    // Total sectors
246                              128,                    // Sector size   
247                              1,                      // Sectors per cluster
248                              1,                      // Heads
249                              1);                     // Sectors per track
250  
251      /* Check the media format status. */
252      if (status != FX_SUCCESS)
253      {
254  
255          /* Error, bail out. */
256          return ;
257      }
258  
259      /* Open the RAM disk. */
260      status =  fx_media_open(&ram_disk, "RAM DISK", _fx_ram_driver, ram_disk_memory,
                media_memory, sizeof(media_memory));
261  
262      /* Check the media open status. */
263      if (status != FX_SUCCESS)
264      {
265  
266          /* Error, bail out. */
267          return ;
268      }
269  
270      /* Create an HTTP client instance. */
271      status = nx_http_client_create(&my_client, "HTTP Client", &client_ip,
                    &client_pool, 600);
272  
273      /* Check status. */
274      if (status != NX_SUCCESS)
275      {
276          return;
277      }
278  
279      /* Attempt to upload a file to the HTTP server. */
280  
281  
282  #if (IPTYPE== 6)
283  
284      /* Relinquish control so the HTTP server can get set up...*/
285      tx_thread_relinquish();
286  
287      /* Set up the client's IPv6 address here. */
288      client_ip_address.nxd_ip_address.v6[3] = 0x101;
289      client_ip_address.nxd_ip_address.v6[2] = 0x0;
290      client_ip_address.nxd_ip_address.v6[1] = 0x0000f101;
291      client_ip_address.nxd_ip_address.v6[0] = 0x20010db1;
292      client_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
293                 
294      /* Here's where we make the HTTP Client IPv6 enabled. */
295  
296      nxd_ipv6_enable(&client_ip);
298      nxd_icmp_enable(&client_ip);     
299      
300      /* Wait till the IP task thread has set the device MAC address. */
302      tx_thread_sleep(100);
303  
305      /* Now update NetX Duo the Client's link local and global IPv6 address. */
306      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
307      nxd_ipv6_ address_set(&server_ip, 0, &client_ip_address, 64, &address_index);
311
313      /* Then make sure NetX Duo has had time to validate the addresses. */
314      
316      tx_thread_sleep(400);
317  
321      /* Now upload an HTML file to the HTTPv6 server. */
322      status =  nxd_http_client_put_start(&my_client, &server_ip_address,
323         "/client_test.htm", "name", "password", 103, 500);
324
325
326      /* Check status. */
327      if (status != NX_SUCCESS)
328      {
329
330          return;
331      }
332      
333
334  #else
335  
336      /* Relinquish control so the HTTP server can get set up...*/
337      tx_thread_relinquish();
338  
339      do
340      {
341      
342          /* Attempt to upload to the HTTP IPv4 server. */
343          status =  nx_http_client_put_start(&my_client, HTTP_SERVER_ADDRESS,
            "/client_test.htm", "name", "password", 103, 500);
344
345  
346          /* Check status. */
347          if (status != NX_SUCCESS)
348          {
349              tx_thread_sleep(100);
350          }
351  
352      } while (status != NX_SUCCESS);
353  
354  
355  #endif  /* (IPTYPE== 6) */
356  
357  
358      /* Allocate a packet. */
359      status =  nx_packet_allocate(&client_pool, &my_packet, NX_TCP_PACKET,
                        NX_WAIT_FOREVER);
360  
361      /* Check status. */
362      if (status != NX_SUCCESS)
363      {
364          return;
365      }
366  
367      /* Build a simple 103-byte HTML page. */
368      nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
369                          &client_pool, NX_WAIT_FOREVER);
370      nx_packet_data_append(my_packet,
371                   "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
372                          &client_pool, NX_WAIT_FOREVER);
373      nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
374                          &client_pool, NX_WAIT_FOREVER);
375      nx_packet_data_append(my_packet, "<H1>Another NetX Test Page!</H1>\r\n", 25,
376                          &client_pool, NX_WAIT_FOREVER);
377      nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
378                          &client_pool, NX_WAIT_FOREVER);
379      nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
380                          &client_pool, NX_WAIT_FOREVER);
381  
382      /* Complete the PUT by writing the total length. */
383      status =  nx_http_client_put_packet(&my_client, my_packet, 50);
384  
385      /* Check status. */
386      if (status != NX_SUCCESS)
387      {
388          return;
389      }
390  
391      /* Now GET the test file  */
392  
393  #ifdef USE_DUO
394  
395      status =  nxd_http_client_get_start(&my_client, &server_ip_address,
396                     "/client_test.htm", NX_NULL, 0, "name", "password", 50);
397  #else
398  
399      status =  nx_http_client_get_start(&my_client, HTTP_SERVER_ADDRESS,
                 "/client_test.htm",  NX_NULL, 0, "name", "password", 50);
400
401  #endif
402  
403      /* Check status. */
404      if (status != NX_SUCCESS)
405      {
406          return;
407      }
408  
409      status = nx_http_client_delete(&my_client);
410  
411      return;
413  }
414  
416  /* Define the helper HTTP server thread. */
417  void    thread_server_entry(ULONG thread_input)
418  {
419  
420  UINT            status;
421  #if (IPTYPE == 6)
422  UINT            address_index
423  NXD_ADDRESS     ip_address
424  
425      /* Allow time for the IP task to initialize the driver. */
426      tx_thread_sleep(100);
427
428    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
429    ip_address.nxd_ip_address.v6[0] = 0x20010000;
430    ip_address.nxd_ip_address.v6[1] = 0;
431    ip_address.nxd_ip_address.v6[2] = 0;
432    ip_address.nxd_ip_address.v6[3] = 4;
433  
434      /* Here's where we make the HTTP server IPv6 enabled. */
435      nxd_ipv6_enable(&server_ip);
436      nxd_icmp_enable(&server_ip);
437  
438      /* Wait till the IP task thread has set the device MAC address. */
439      while (server_ip.nx_ip_arp_physical_address_msw == 0 ||
440             server_ip.nx_ip_arp_physical_address_lsw == 0)
441      {
442          tx_thread_sleep(30);
443      }
444  
445      nxd_ipv6_address_set(&server_ip, 0, NX_NULL, 10, &address_index)
446      nxd_ipv6_ address_set(&server_ip, 0, &ip_address, 64, &address_index);
447  
448      /* Wait for NetX Duo to validate server address. */
449      tx_thread_sleep(400);
450  
451  #endif  /* (IPTYPE == 6) */
452  
453      /* OK to start the HTTPv6 Server. */
454      status = nx_http_server_start(&my_server);
455  
456      if (status != NX_SUCCESS)
457      {
458          return;
459      }
460  
461      /* HTTP server ready to take requests! */
462  
463      /* Let the IP threads execute. */
464      tx_thread_relinquish();
465  
466      return;
467  }
```

**Рисунок 1.1. Пример использования HTTP с NetX Duo**

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для использования HTTP с NetX Duo. Ниже приведен список всех параметров с подробным описанием каждого из них. Приведены значения по умолчанию, но их можно переопределить до добавления файлов *nxd_http_client.h* и *nxd_http_server.h*:

 - **NX_DISABLE_ERROR_CHECKING** — если определен, этот параметр удаляет базовую проверку ошибок HTTP. Обычно он используется после отладки приложения.
 - **NX_HTTP_SERVER_PRIORITY** — приоритет потока HTTP-сервера. По умолчанию указано значение 16 для задания приоритета 16.
 - **NX_HTTP_NO_FILEX** — если определен, этот параметр предоставляет заглушку для зависимостей FileX. HTTP-клиент будет работать без каких-либо изменений, если этот параметр определен. Для надлежащей работы HTTP-сервер нужно будет изменить либо пользователю потребуется создать несколько служб FileX.
 - **NX_HTTP_TYPE_OF_SERVICE** — тип службы, необходимой для TCP-запросов HTTP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.
  - **NX_HTTP_SERVER_THREAD_TIME_SLICE** — число тактов таймера, которое может выполнить поток сервера, прежде чем уступить ресурсы потокам с таким же приоритетом. Значение по умолчанию — 2.
 - **NX_HTTP_FRAGMENT_OPTION** — поддержка фрагментов для TCP-запросов HTTP. По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментирование TCP в HTTP.
 - **NX_HTTP_SERVER_WINDOW_SIZE** — размер окна сокета для сервера. По умолчанию это значение равно 2048 байт.
 - **NX_HTTP_TIME_TO_LIVE** — указывает число маршрутов, которое может пройти этот пакет перед отменой. Значение по умолчанию — 0x80.
 - **NX_HTTP_SERVER_TIMEOUT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу. Значение по умолчанию — 10 секунд (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_ACCEPT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_server_socket_accept*. Значение по умолчанию — 10 * NX_IP_PERIODIC_RATE.
 - **NX_HTTP_SERVER_TIMEOUT_DISCONNECT** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_disconnect*. Значение по умолчанию — 10 секунд (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_RECEIVE** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_receive*. Значение по умолчанию — 10 секунд (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_SERVER_TIMEOUT_SEND** — указывает число тактов ThreadX, на которое внутренние службы приостановят работу для внутренних вызовов *nx_tcp_socket_send*. Значение по умолчанию — 10 секунд (10 * NX_IP_PERIODIC_RATE).
 - **NX_HTTP_MAX_HEADER_FIELD** — указывает максимальный размер поля HTTP-заголовка. Значение по умолчанию — 256.
 - **NX_HTTP_MULTIPART_ENABLE** — если определен, позволяет HTTP-серверу поддерживать составные HTTP-запросы.
 - **NX_HTTP_SERVER_MAX_PENDING** — указывает число подключений, которые можно поставить в очередь к HTTP-серверу. Значение по умолчанию — 5.
 - **NX_HTTP_MAX_RESOURCE** — указывает число байт, разрешенных в предоставляемом клиентом *имени ресурса*. Значение по умолчанию — 40.
 - **NX_HTTP_MAX_NAME** — указывает число байт, разрешенных в предоставляемом клиентом *имени пользователя*. Значение по умолчанию — 20.
 - **NX_HTTP_MAX_PASSWORD** — указывает число байт, разрешенных в предоставляемом клиентом *пароле*. Значение по умолчанию — 20.
 - **NX_HTTP_SERVER_MIN_PACKET_SIZE** — указывает минимальный размер пакетов в пуле, заданном при создании сервера. Минимальный размер нужно указать, чтобы обеспечить включение полного HTTP-заголовка в один пакет. Значение по умолчанию — 600.
 - **NX_HTTP_CLIENT_MIN_PACKET_SIZE** — указывает минимальный размер пакетов в пуле, заданном при создании клиента. Минимальный размер нужно указать, чтобы обеспечить включение полного HTTP-заголовка в один пакет. Значение по умолчанию — 300.
 - **NX_HTTP_SERVER_RETRY_SECONDS** — задает время ожидания повторной передачи на сокет сервера в секундах. Значение по умолчанию — 2.
 - **NX_HTTP_SERVER_RETRY_MAX** — задает максимальное число повторных передач на сокет сервера. Значение по умолчанию — 10.
 - **NX_HTTP_SERVER_RETRY_SHIFT** — это значение используется для указания времени ожидания следующей повторной передачи. Текущее время ожидания умножается на число повторных передач на текущий момент с добавлением значения для смещения времени ожидания сокета. Значение по умолчанию — 1 (для удвоения времени ожидания).
 - **NX_HTTP_SERVER_TRANSMIT_QUEUE_DEPTH** — указывает максимальное число пакетов, которых можно поставить в очередь для повторной передачи на сокет сервера. Если число пакетов в очереди достигает этого значения, пакеты не будут отправляться, пока один или несколько пакетов в очереди не будут освобождены. Значение по умолчанию — 20.
