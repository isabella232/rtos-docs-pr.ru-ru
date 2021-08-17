---
title: Глава 2. Установка и использование AutoIP NetX для ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента AutoIP NetX для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9bc5ce189980dbceaf12a2f2e8429d9267e7d37f559c88d10c54e399d01ec259
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796894"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a>Глава 2. Установка и использование AutoIP NetX для ОСРВ Azure

В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента AutoIP NetX для ОСРВ Azure.

## <a name="product-distribution"></a>Распространение продукта

AutoIP для NetX доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). Пакет содержит три файла исходного кода, один файл заголовков и PDF-файл, содержащий этот документ:

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
> В приведенном ниже примере предполагается, что основное устройство имеет один сетевой интерфейс. Для многосетевого устройства ведущее приложение может использовать службу NetX AutoIP *nx_auto_ip_interface_* , чтобы указать дополнительный сетевой интерфейс для отправки пробы на IP-адрес. Дополнительные сведения о настройке многосетевых приложений см. в **руководстве пользователя NetX**. Обратите внимание, что ведущее приложение должно использовать API NetX *nx_status_ip_interface_check*, чтобы убедиться, что AutoIP получил IP-адрес.

## <a name="example-of-autoip-use-with-netx"></a>Пример использования AutoIP с NetX

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