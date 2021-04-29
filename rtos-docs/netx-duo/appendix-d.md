---
title: Приложение D. Интерфейс API совместимого с BSD сокета в NetX Duo для ОСРВ Azure
description: Сведения об интерфейсе API совместимого с BSD сокета для IPv4 и IPv6.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82439184d9facb6ddcc08ce81bc51182d7f34429
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814875"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>Приложение D. Интерфейс API совместимого с BSD сокета в NetX Duo для ОСРВ Azure

## <a name="bsd-compatible-socket-api"></a>API совместимого с BSD сокета 
Интерфейс API совместимого с BSD сокета поддерживает подмножество вызовов API для сокетов BSD (с некоторыми ограничениями), автоматически используя примитивы NetX Duo&reg;. Поддерживаются протоколы и сетевая адресация IPv4 и IPv6. Этот уровень API совместимых с BSD сокетов обычно работает с той же скоростью, что и стандартные реализации BSD, или немного большей, так как этот интерфейс API использует внутренние примитивы NetX Duo и обходит ненужную проверку ошибок NetX.  

Настраиваемые параметры позволяют ведущему приложению определять максимальное число сокетов, максимальный размер окна TCP и глубину очереди прослушивания.

Из-за ограничений производительности и архитектуры этот совместимый с BSD API сокетов поддерживает не все вызовы сокетов BSD. Кроме того, для служб BSD доступны не все параметры BSD, в частности действуют следующие ограничения.

  - Вызов ***select** _ работает только с fd_set \_readfds, и в нем не поддерживаются другие аргументы, например writefds или exceptfds.
  - Аргумент int flags не поддерживается для вызовов ***send** _, _*_recv_*_, _*_sendto_*_ и _ *_recvfrom_**. 
  - Совместимый с BSD API сокетов поддерживает только ограниченный набор вызовов для сокетов BSD.

Исходный код отличается простотой и размещен всего в двух файлах: ***nxd_bsd.c** _ и _*_nxd_bsd.h_*_. Для установки необходимо добавить эти два файла в проект сборки (но не в библиотеку NetX) и создать ведущее приложение, которое будет использовать вызовы службы сокетов BSD. Файл _ *_nxd_bsd.h_** также нужно включить в исходный код приложения. Демонстрационные примеры файлов для приложений на основе IPv4 и IPv6 включены в свободно распространяемый дистрибутив NetX Duo. Дополнительные сведения см. в файлах справки и сведений, которые входят в пакет интерфейса API совместимого с BSD сокета.

Совместимый с BSD API сокетов поддерживает следующие вызовы API.

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```