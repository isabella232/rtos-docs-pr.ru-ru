---
title: Глава 3. Параметры конфигурации ОСРВ Azure NetX Duo DHCPv6
description: Существует ряд параметров конфигурации ОСРВ Azure NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 129d1421215452448b1de4626fdeda530a5466bd63ed0c758676c3ad60f9d6fb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782427"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Глава 3. Параметры конфигурации ОСРВ Azure NetX Duo DHCPv6

Существует ряд параметров конфигурации ОСРВ Azure NetX Duo DHCPv6. Их подробное описание приводится ниже:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** Приоритет клиентского потока. По умолчанию это значение назначает потоку клиента приоритет 2.

- **NX_DHCPV6_MUTEX_WAIT** Параметр времени ожидания для получения монопольной блокировки для клиентского мьютекса DHCPv6. По умолчанию используется значение TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND** Отношение тактов к секундам. Эта величина зависит от процессора. Значение по умолчанию — 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL** Интервал времени в секундах, в течение которого таймер времени существования IP-адреса обновляет период времени, когда текущий IP-адрес будет назначен клиенту. По умолчанию используется значение 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Интервал времени в секундах, в течение которого таймер сеанса обновляет период времени, когда клиент взаимодействует с сервером. По умолчанию используется значение 1.

- **NX_DHCPV6_MAX_IA_ADDRESS** Максимальное количество адресов IA, которые могут быть добавлены в запись клиента. Значение по умолчанию — 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS** Число DNS-серверов для хранения в записи клиента. Значение по умолчанию — 2.

- **NX_DHCPV6_NUM_TIME_SERVERS** Число серверов времени для хранения в записи клиента. Значение по умолчанию — 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE** Размер буфера в записи клиента для хранения доменного имени клиента. Значение по умолчанию — 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE** Размер буфера в записи клиента для хранения часового пояса клиента. Значение по умолчанию — 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** Размер буфера в записи клиента для хранения параметра "сообщение о состоянии" в ответе сервера. Значение по умолчанию — 100 байт.

- **NX_DHCPV6_PACKET_TIME_OUT** Время ожидания в секундах для выделения пакета из пула клиентских пакетов. Значение по умолчанию — 3 секунды.

- **NX_DHCPV6_TYPE_OF_SERVICE** Эта функция определяет тип службы для передачи пакетов UDP из сокета клиента DHCPv6. По умолчанию используется значение **NX_IP_NORMAL**.

- **NX_DHCPV6_TIME_TO_LIVE** Число попыток направления пакета клиента сетевым маршрутизатором до отклонения пакета. Значение по умолчанию — 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Указывает число пакетов, которые могут храниться в очереди получения сокета UDP клиента, прежде чем NetX Duo начнет отклонять пакеты. Значение по умолчанию — 5.

## <a name="dhcpv6-message-transmission"></a>Передача сообщений DHCPv6

Существует набор параметров клиента DHCPv6 для настройки передачи сообщений DHCPv6. А именно: 

  - начальное время ожидания

  - максимальная задержка при первой передаче

  - максимальное время ожидания повторной передачи 

  - максимальное число повторных передач 

  - максимальная длительность ожидания ответа от сервера

Эти параметры применяются к каждому из сообщений клиента DHCPv6:

- SOLICIT

- REQUEST

- RENEW

- REBIND

- RELEASE

- DECLINE

- ПОДТВЕРДИТЬ

- INFORM

Ниже приведен полный список этих настраиваемых параметров и их значения по умолчанию 

values:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

Чтобы отменить ограничение времени ожидания повторной передачи, установите значение 0 для счетчика передаваемых сообщений. Чтобы отменить ограничение количества попыток передачи сообщения клиента DHCPv6, установите значение 0 для счетчика передаваемых сообщений.

> [!NOTE]
> Независимо от длительности ожидания или количества повторных попыток, когда истекает срок действия IPv6-адреса, он удаляется из таблицы IP-адресов, и клиент не сможет его больше использовать. Клиент NetX Duo DHCPv6 автоматически начнет отправлять сообщения SOLICIT, запрашивающие новый IPv6-адрес.