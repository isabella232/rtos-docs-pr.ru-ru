---
title: Глава 2. Установка и использование DHCP-клиента для NetX в ОСРВ Azure
description: В этой главе описываются различные проблемы, связанные с установкой, настройкой и использованием компонента DHCP-клиента для NetX в ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: da27039694c90f74a8b13dc556a367802f66c0ba7dd337f3e31ebab05641a9b1
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788785"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a>Глава 2. Установка и использование DHCP-клиента для NetX в ОСРВ Azure

В этой главе рассматриваются разные вопросы, связанные с установкой, настройкой и использованием компонента DHCP для NetX в ОСРВ Azure.

## <a name="product-distribution"></a>Распространение продукта

Пакет DHCP для NetX доступен по адресу [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx). Этот пакет включает в себя два исходных файла и PDF-файл с этим документом:

- **nx_dhcp.h** — файл заголовка для DHCP для NetX.

- **nx_dhcp.c** — исходный файл C для DHCP для NetX.

- **nx_dhcp.pdf** — описание DHCP для NetX в формате PDF.

- **demo_netx_dhcp.c** — демонстрационный пример DHCP для NetX.

- **demo_netx_multihome_dhcp_client.c**: демонстрационный файл DHCP-клиента для NetX, котором протокол DHCP используется на нескольких интерфейсах.

## <a name="dhcp-installation"></a>Установка DHCP

Чтобы использовать DHCP для NetX, следует скопировать упомянутый выше дистрибутив целиком в каталог с установленным экземпляром NetX. Например, если экземпляр NetX установлен в каталоге *\threadx\arm7\green*, файлы *nx_dhcp.h* и *nx_dhcp.c* необходимо скопировать в этот каталог.

## <a name="using-dhcp"></a>Использование DHCP

Использовать DHCP для NetX просто. В код приложения следует добавить *nx_dhcp.h* после *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX соответственно. После добавления файла *nx_dhcp.h* код приложения сможет выполнять вызовы функций DHCP, описанных далее в этом руководстве. В приложение также нужно включить файл *nx_dhcp.c* для процесса сборки. Этот файл должен быть скомпилирован так же, как и другие файлы приложения, а его объектная форма должна быть связана с файлами приложения. Это все, что необходимо для использования DHCP для NetX.

Обратите внимание, что, поскольку протокол DHCP использует службы UDP NetX, перед использованием DHCP следует включить протокол UDP с помощью вызова *nx_udp_enable*.

Чтобы получить назначенный ранее IP-адрес, DHCP-клиент может инициировать процесс DHCP с сообщением REQUEST и параметром 50 "Requested IP Address" (Запрошенный IP-адрес) на DHCP-сервере. DHCP-сервер ответит сообщением ACK, если он предоставляет клиенту этот IP-адрес, или сообщением NACK, если он отклоняет запрос. В последнем случае DHCP-клиент перезапустит процесс DHCP в состоянии INIT с сообщением DISCOVER и без запрошенного IP-адреса. Ведущее приложение сначала создает DHCP-клиент, а затем вызывает службу API *nx_dhcp_request_client_ip* для задания запрошенного IP-адреса перед запуском процесса DHCP вызовом *nx_dhcp_start*. В этом документе приведен пример приложения DHCP, ознакомившись с которым можно получить дополнительные сведения.

## <a name="in-the-bound-state"></a>В состоянии BOUND

Пока DHCP-клиент находится в состоянии BOUND, поток DHCP-клиента обрабатывает состояние клиента один раз в период (указанный в NX_DHCP_TIME_INTERVAL) и уменьшает оставшееся время аренды IP-адреса, назначенной этому клиенту. Когда наступает время продления, состояние DHCP-клиента меняется на RENEW. На этом этапе клиент запрашивает продление у DHCP-сервера.


## <a name="sending-dhcp-messages-to-the-server"></a>Отправка сообщений DHCP на сервер

У DHCP-клиента имеются службы API, позволяющие ведущему приложению отправить сообщение на DHCP-сервер. Обратите внимание на то, что эти службы не предназначены для того, чтобы ведущее приложение вручную запускало протокол DHCP-клиента, так как они в основном отправляют сообщение без необходимости обновления внутреннего состояния клиента DHCP.

  - *nx_dhcp_release*: отправляет сообщение RELEASE на сервер, когда ведущее приложение либо выходит из сети, либо должно освободить свой IP-адрес.

  - *nx_dhcp_decline*: отправляет сообщение DECLINE на сервер, если ведущее приложение определило независимо от DHCP-клиента, что его IP-адрес уже используется.

  - *nx_dhcp_forcerenew*: отправляет сообщение FORCERENEW на сервер.

  - *nx_dhcp_send_request*: этот параметр принимает в качестве аргумента тип сообщения DHCP, указанный в файле *nx_dhcp.h*, и отправляет сообщение на сервер. Он предназначен в первую очередь для отправки сообщения INFORM протокола DHCP.

Дополнительные сведения об этих службах см. в *описании служб DHCP*.

## <a name="starting-and-stopping-the-dhcp-client"></a>Запуск и остановка DHCP-клиента

Чтобы остановить DHCP-клиент независимо от того, перешел ли он в состояние BOUND, ведущее приложение вызывает службу *nx_dhcp_stop*.

Чтобы перезапустить DHCP-клиент, ведущее приложение должно сначала остановить его с помощью службы *nx_dhcp_stop*, описанной выше. Затем узел может вызвать службу *nx_dhcp_start*, чтобы возобновить работу DHCP-клиента. Если ведущее приложение хочет очистить предыдущий профиль DHCP-клиента, например полученный от предыдущего DHCP-сервера в другой сети, то перед вызовом службы nx_dhcp_start оно должно вызвать службу *nx_dhcp_reinitialize* для внутреннего выполнения этой задачи.

Типичная последовательность может быть следующей:

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

Для приложений DHCP, выполняющихся только на одном интерфейсе DHCP, остановка DHCP-клиента также приводит к отключению таймера DHCP-клиента. Поэтому оставшееся время аренды IP-адреса больше не отслеживается. Остановка DHCP-клиента на определенном интерфейсе не приведет к отключению таймера DHCP-клиента, но прекратит обновление таймера с учетом оставшегося времени аренды IP-адреса на этом интерфейсе.

Следовательно, остановка DHCP-клиента не рекомендуется, если только ведущему приложению не требуется выполнить перезагрузку или переключение сетей.

## <a name="using-the-dhcp-client-with-auto-ip"></a>Использование DHCP-клиента с протоколом AutoIP

DHCP-клиент для NetX работает вместе с протоколом AutoIP в приложениях, в которых протоколы DHCP и AutoIP обеспечивают адрес, а наличие доступного и отвечающего на запросы DHCP-сервера не гарантируется. Однако если узлу не удается обнаружить сервер или получить назначенный IP-адрес, он может переключиться на протокол AutoIP для локального IP-адреса. Перед этим рекомендуется временно остановить DHCP-клиент, пока протокол AutoIP выполняет этапы отправки проб и защиты. После назначения адреса AutoIP узлу можно будет перезапустить DHCP-клиент и, если DHCP-сервер станет доступным, IP-адрес узла сможет принять IP-адрес, предлагаемый DHCP-сервером во время работы приложения.

В протоколе AutoIP для NetX имеется уведомление об изменении адреса, которое позволяет узлу отслеживать свои действия в случае изменения IP-адреса.

## <a name="small-example-system"></a>Пример небольшой системы

Пример использования NetX описан на рисунке 1.1 ниже. DHCP-клиент создается (*my_thread_entry*) в строке 101. После успешного создания в строке 108 инициируется процесс DHCP с помощью вызова *nx_dhcp_start*. На этом этапе предпринимаются попытки DHCP-клиента связаться с DHCP-сервером. Во время этого процесса код приложения ожидает регистрации допустимого IP-адреса в экземпляре IP с помощью службы *nx_ip_status_check* (или *nx_ip_interface_status_check* для дополнительного интерфейса), начиная со строки 95. Чаще всего для этого используется цикл с более коротким параметром ожидания.

После строки 127 DHCP-сервер получил допустимый IP-адрес, и приложение может продолжать работу, используя службы TCP/IP для NetX.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Рис. 1.1. Пример использования DHCP с NetX

## <a name="multi-server-environments"></a>Многосерверные среды

В сетях, в которых имеется более одного DHCP-сервера, DHCP-клиент принимает первое полученное от DHCP-сервера сообщение OFFER, переходит в состояние REQUEST и игнорирует все прочие полученные предложения.

## <a name="arp-probes"></a>Пробы ARP

DHCP-клиент можно настроить для отправки одной или нескольких проб ARP после назначения IP-адреса DHCP-сервером, чтобы проверить, не используется ли этот IP-адрес. Этап отправки проб ARP рекомендуется спецификацией RFC 2131 и особенно важен в средах с несколькими DHCP-серверами. Если ведущее приложение включит параметр NX_DHCP_CLIENT_SEND_ARP_PROBE (см. раздел **Параметры конфигурации** в главе 2, чтобы ознакомиться с дополнительными параметрами проверки ARP), то DHCP-клиент отправит пробу ARP на свой адрес и будет ждать ответ в течение указанного времени. Если DHCP-клиент не получит ответа, то он перейдет в состояние BOUND. В случае получения ответа DHCP-клиент предполагает, что этот адрес уже используется. Он автоматически отправляет на сервер сообщение DECLINE и повторно инициализирует клиент для отправки проб DHCP в состоянии INIT. Это приводит к перезапуску конечного автомата DHCP, и клиент отправляет на сервер еще одно сообщение DISCOVER.

## <a name="bootp-protocol"></a>Протокол BOOTP

Помимо протокола DHCP DHCP-клиент также поддерживает протокол BOOTP. Чтобы включить эту возможность и использовать протокол BOOTP вместо DHCP, ведущее приложение должно задать параметр конфигурации NX_DHCP_BOOTP_ENABLE. Ведущее приложение по-прежнему может запрашивать определенные IP-адреса в протоколе BOOTP. DHCP-клиент не поддерживает загрузку операционной системы узла, в отличие от протокола BOOTP, который иногда используется для этого.

## <a name="dhcp-on-a-secondary-interface"></a>DHCP на дополнительном интерфейсе

DHCP-клиент для NetX может работать на дополнительных интерфейсах, а не на основном интерфейсе по умолчанию.

Для запуска DHCP-клиента для NetX на дополнительном сетевом интерфейсе ведущее приложение должно задать индекс дополнительного интерфейса для DHCP-клиента с помощью службы API *nx_dhcp_set_interface_index*. Интерфейс должен быть подключен к основному сетевому интерфейсу с помощью службы *nx_ip_interface_attach*. Сведения о подключении дополнительных интерфейсов приведены в руководстве пользователя NetX.

На рис. 1.2 ниже приведен пример системы, в которой ведущее приложение подключается к DHCP-серверу с помощью дополнительного интерфейса. В строке 65 дополнительный интерфейс подключается к задаче IP с нулевым IP-адресом. В строке 104 после создания экземпляра DHCP-клиента индексу интерфейса этого DHCP-клиента присваивается значение 1 (т. е. смещение относительно основного интерфейса, которому соответствует индекс 0) путем вызова *nx_dhcp_set_interface_index*. После этого DHCP-клиент готов к запуску в строке 108.

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

Рис. 1.2. Пример DHCP для NetX с поддержкой нескольких интерфейсов

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a>Одновременный запуск DHCP-клиента на нескольких интерфейсах

Чтобы запускать DHCP-клиент на нескольких интерфейсах, для параметра NX_MAX_PHYSICAL_INTERFACES в *nx_api.h* должно быть задано число физических интерфейсов, подключенных к устройству. По умолчанию это значение равно 1 (т. е. это основной интерфейс). Чтобы зарегистрировать дополнительный интерфейс для экземпляра IP, используйте службу *nx_ip_interface_attach*. Сведения о подключении дополнительных интерфейсов приведены в руководстве пользователя NetX.

Следующим шагом является задание для параметра NX_DHCP_CLIENT_MAX_RECORDS в файле *nx_dhcp.h* ожидаемого максимального числа интерфейсов, на которых будет одновременно выполняться протокол DHCP. Обратите внимание на то, что значение NX_DHCP_CLIENT_MAX_RECORDS может быть не равно значению NX_MAX_PHYSICAL_INTERFACES. Например, параметр NX_MAX_PHYSICAL_INTERFACES может иметь значение 3, а NX_DHCP_CLIENT_MAX_RECORDS — 2. В такой конфигурации только два (и это могут быть любые два из трех физических интерфейсов в любой момент) из трех физических интерфейсов могут запускать протокол DHCP одновременно. Записи DHCP-клиентов не сопоставляются однозначно с сетевыми интерфейсами. Например, запись клиента 1 не будет автоматически сопоставлена с индексом физического интерфейса 1.

Кроме того, для параметра NX_DHCP_CLIENT_MAX_RECORDS можно задать значение больше значения NX_MAX_PHYSICAL_INTERFACES, но это приведет к созданию неиспользуемых записей клиентов и неэффективному использованию памяти.

Прежде чем запустить протокол DHCP на каком-либо интерфейсе, приложение должно включить эти интерфейсы, вызвав *nx_dhcp_interface_enable*. Обратите внимание на то, что исключением является основной интерфейс, который автоматически включается в вызове *nx_dhcp_create* (его можно отключить с помощью службы *nx_dhcp_interface_disable*, описанной ниже).

В любое время на интерфейсе можно отключить протокол DHCP, кроме того, протокол DHCP на этом интерфейсе может быть остановлен независимо от других интерфейсов, использующих DHCP.

Как упоминалось выше, чтобы включить протокол DHCP для конкретного интерфейса, используйте службу *nx_dhcp_interface_enable* и укажите индекс физического интерфейса в качестве входного аргумента. Включить протокол можно для числа интерфейсов, не превышающего значение NX_DHCP_CLIENT_MAX_RECORDS. Единственное ограничение состоит в том, что входной аргумент индекса интерфейса должен быть меньше значения NX_MAX_PHYSICAL_INTERFACES.

Чтобы запустить протокол DHCP на определенном интерфейсе, используйте службу *nx_dhcp_interface_start*. Чтобы запустить протокол DHCP на всех интерфейсах, используйте службу *nx_dhcp_start*. (Интерфейсы, для которых протокол DHCP уже запущен, не будут затронуты вызовом *nx_dhcp_start*.)

Чтобы остановить протокол DHCP на интерфейсе, используйте службу *nx_dhcp_interface_stop*. Протокол DHCP уже запущен на этом интерфейсе или возвращено состояние ошибки. Чтобы остановить протокол DHCP на всех интерфейсах, используйте службу *nx_dhcp_stop*. Протокол DHCP можно в любое время остановить независимо от других интерфейсов.

Большинство существующих служб DHCP-клиента имеют эквивалент для интерфейсов. Например, служба *nx_dhcp_interface_release* является предназначенным для интерфейсов службы *nx_dhcp_release*. Если для DHCP-клиента настроен один интерфейс, он выполняет то же действие.

Обратите внимание на то, что службы DHCP-клиента, не относящиеся к интерфейсам, обычно применяются ко всем интерфейсам, но все из них. В последнем случае служба, не относящаяся к интерфейсам, применяется к первому интерфейсу с поддержкой DHCP, найденному в списке записей интерфейсов DHCP-клиента. Сведения о том, как работает служба, не относящаяся к интерфейсам, в случае включения протокола DHCP на нескольких интерфейсах, приведены в **описании служб** в главе 3.

В приведенном ниже примере для экземпляра IP заданы два сетевых интерфейса, и сначала протокол DHCP выполняется на дополнительном интерфейсе. Через некоторое время протокол DHCP запускается на основном интерфейсе. Затем освобождается IP-адрес основного интерфейса и протокол DHCP перезапускается на основном интерфейсе.

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

Полный список служб, связанных с интерфейсами, приведен в **описании служб** в главе 3.

## <a name="configuration-options"></a>Параметры конфигурации

Настраиваемые пользователем параметры DHCP в файле *nx_dhcp.h* позволяют ведущему приложению настроить DHCP-клиент в соответствии с конкретными требованиями. Ниже приведен список этих параметров:  
  
- **NX_DHCP_ENABLE_BOOTP**: если этот параметр определен, то он включает протокол BOOTP вместо DHCP. Этот параметр по умолчанию отключен.

- **NX_DHCP_CLIENT_RESTORE_STATE**: если этот параметр определен, DHCP-клиент сохраняет свое текущее состояние аренды, включая оставшееся время аренды, и восстанавливает это состояние после перезагрузки клиентского приложения DHCP. По умолчанию эта политика отключена.

- **NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL**: если этот параметр задан, DHCP-клиент не будет создавать собственный пул пакетов. Ведущее приложение должно использовать службу nx_dhcp_packet_pool_set, чтобы задать пул пакетов DHCP-клиента. По умолчанию эта политика отключена.

- **NX_DHCP_CLIENT_SEND_ARP_PROBE**: если этот параметр определен, он позволяет DHCP-клиенту отправить пробу ARP после назначения IP-адреса, чтобы убедиться, что назначенный адрес DHCP не принадлежит другому узлу. Этот параметр по умолчанию отключен.

- **NX_DHCP_ARP_PROBE_WAIT**: определяет период времени, в течение которого DHCP-клиент ожидает ответ после отправки пробы ARP. Значение по умолчанию — 1 секунда (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCP_ARP_PROBE_MIN**: определяет минимальное изменение интервала между отправками проб ARP. Значение по умолчанию — 1 секунда.

- **NX_DHCP_ARP_PROBE_MAX**: определяет максимальное изменение интервала между отправками проб ARP. Значение по умолчанию — 2 секунды.

- **NX_DHCP_ARP_PROBE_NUM**: определяет количество отправленных проб ARP, позволяющее определить, используется ли другим узлом IP-адрес, назначенный DHCP-сервером. Значение по умолчанию — 3 пробы.

- **NX_DHCP_RESTART_WAIT**: определяет период времени, в течение которого DHCP-клиент ожидает перезапуска протокола DHCP, если IP-адрес, назначенный этому DHCP-клиенту, уже используется. Значение по умолчанию — 10 секунд.

- **NX_DHCP_CLIENT_MAX_RECORDS**: указывает максимальное число записей интерфейсов, сохраняемых в экземпляре DHCP-клиента. Запись интерфейса DHCP-клиента — это запись о DHCP-клиенте, запущенном на определенном интерфейсе. Значение по умолчанию равно количеству физических интерфейсов (NX_MAX_PHYSICAL_INTERFACES).

- **NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION**: если этот параметр определен, он позволяет DHCP-клиенту передавать максимальный размер сообщения DHCP. Этот параметр по умолчанию отключен.

- **NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK**: если этот параметр определен, он позволяет DHCP-клиенту проверять входное имя узла в вызове nx_dhcp_create на допустимость символов и длины. Этот параметр по умолчанию отключен.

- **NX_DHCP_THREAD_PRIORITY**: приоритет потока DHCP. По умолчанию поток DHCP выполняется с приоритетом 3.

- **NX_DHCP_THREAD_STACK_SIZE**: размер стека потоков DHCP. По умолчанию размер составляет 2048 байт.

- **NX_DHCP_TIME_INTERVAL**: интервал в секундах, по истечении которого выполняется функция истечения срока действия таймера DHCP-клиента. Эта функция обновляет все значения времени ожидания в операциях DHCP (например, если сообщения должны быть отправлены повторно или изменилось состояние DHCP-клиента). По умолчанию это значение равно 1 секунде.

- **NX_DHCP_OPTIONS_BUFFER_SIZE**: размер буфера параметров DHCP. По умолчанию используется значение 312.

- **NX_DHCP_PACKET_PAYLOAD**: задает размер полезных данных пакета DHCP-клиента в байтах. Значение по умолчанию — NX_DHCP_MINIMUM_IP_DATAGRAM + размер физического заголовка. Размером физического заголовка в проводных сетях обычно является размер кадра Ethernet.

- **NX_DHCP_PACKET_POOL_SIZE**: задает размер пула пакетов DHCP-клиента. Значение по умолчанию — 5 *NX_DHCP_PACKET_PAYLOAD, которое обеспечит четыре пакета, а также место для внутренних служебных данных пула пакетов.

- **NX_DHCP_MIN_RETRANS_TIMEOUT**: задает минимальное время ожидания для получения ответа DHCP-сервера на сообщение клиента перед повторной передачей сообщения. Значение по умолчанию — 4 секунды (рекомендация RFC 2131).

- **NX_DHCP_MAX_RETRANS_TIMEOUT**: задает максимальное время ожидания для получения ответа DHCP-сервера на сообщение клиента перед повторной передачей сообщения. Значение по умолчанию — 64 секунды (рекомендация RFC 2131).

- **NX_DHCP_MIN_RENEW_TIMEOUT**: задает минимальное время ожидания для получения сообщения DHCP-сервера и отправки запроса на продление после привязки DHCP-клиента к IP-адресу. Значение по умолчанию — 60 секунд. Однако DHCP-клиент использует значения времени истечения срока действия для продления и повторной привязки из сообщения DHCP-сервера, прежде чем использовать минимальное время ожидания продления.

- **NX_DHCP_TYPE_OF_SERVICE**: тип службы, необходимый для UDP-запросов DHCP. По умолчанию это значение определено как NX_IP_NORMAL для указания обычной службы IP-пакетов.

- **NX_DHCP_FRAGMENT_OPTION**: включение фрагментации для UDP-запросов DHCP. По умолчанию имеет значение NX_DONT_FRAGMENT, которое отключает фрагментацию UDP в DHCP.

- **NX_DHCP_TIME_TO_LIVE**: указывает число маршрутизаторов, которые может пройти этот пакет, прежде чем он будет удален. Значение по умолчанию — 0x80.

- **NX_DHCP_QUEUE_DEPTH**: указывает максимальное значение глубины очереди получения. По умолчанию задано значение 4.
