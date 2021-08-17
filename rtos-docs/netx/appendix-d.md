---
title: Приложение D. Совместимый с BSD API сокета в NetX для ОСРВ Azure
description: Сведения о совместимом с BSD API сокета для IPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bd4a35c19cd794a5135f01abe5595456d39b5306ba25ce2966c3bb1aea14ea17
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790094"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>Приложение D. Совместимый с BSD API сокета в NetX для ОСРВ Azure

## <a name="bsd-compatible-socket-api"></a>Совместимый с BSD API сокета

Совместимый с BSD API сокета поддерживает подмножество вызовов API для сокетов BSD (с некоторыми ограничениями), автоматически используя примитивы NetX для ОСРВ Azure. Поддерживаются протоколы и сетевая адресация IPv4. Этот уровень совместимого с BSD API сокетов обычно работает с той же или немного большей скоростью, что и стандартные реализации BSD, так как этот API использует внутренние примитивы NetX и обходит ненужную проверку ошибок NetX.

Настраиваемые параметры позволяют ведущему приложению определять максимальное число сокетов, максимальный размер окна TCP и глубину очереди прослушивания.

Из-за ограничений производительности и архитектуры этот совместимый с BSD API сокетов поддерживает не все вызовы сокетов BSD. Кроме того, для служб BSD доступны не все параметры BSD, в частности действуют следующие ограничения:

- Функция ***select** _ работает только с _fd_set \*readfds*, и в этом вызове не поддерживаются другие аргументы, например *writefds* или *exceptfds*.
- Аргумент *int flags* не поддерживается для функций ***send** _, _*_recv_*_, _*_sendto_*_ и _ *_recvfrom_* *. Совместимый с BSD API сокетов поддерживает только ограниченный набор вызовов для сокетов BSD.

Исходный код отличается простотой и размещен всего в двух файлах: ***nx_bsd.c** _ и _*_nx_bsd.h_*_. Для установки необходимо добавить эти два файла в проект сборки (но не в библиотеку NetX) и создать ведущее приложение, которое будет использовать вызовы службы сокетов BSD. Файл _ *_nx_bsd.h_** также нужно включить в исходный код приложения. Примеры демонстрационных файлов включены в дистрибутив, который бесплатно поставляется вместе с NetX. Дополнительные сведения см. в справке по совместимому с BSD API сокетов **417** и файлах readme, которые входят в пакет совместимого с BSD API сокетов.

Совместимый с BSD API сокетов поддерживает следующие вызовы API:

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
