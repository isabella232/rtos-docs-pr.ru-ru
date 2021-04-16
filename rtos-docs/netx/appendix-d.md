---
title: Приложение D. Совместимый с BSD API сокета в NetX для ОСРВ Azure
description: Сведения о совместимом с BSD API сокета для IPv4.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9062e27d8f447ac8d36e7a09afee5ac14f86f8c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815319"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a><span data-ttu-id="6df06-103">Приложение D. Совместимый с BSD API сокета в NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="6df06-103">Appendix D - Azure RTOS NetX BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="6df06-104">Совместимый с BSD API сокета</span><span class="sxs-lookup"><span data-stu-id="6df06-104">BSD-Compatible Socket API</span></span>

<span data-ttu-id="6df06-105">Совместимый с BSD API сокета поддерживает подмножество вызовов API для сокетов BSD (с некоторыми ограничениями), автоматически используя примитивы NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="6df06-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing Azure RTOS NetX primitives underneath.</span></span> <span data-ttu-id="6df06-106">Поддерживаются протоколы и сетевая адресация IPv4.</span><span class="sxs-lookup"><span data-stu-id="6df06-106">IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="6df06-107">Этот уровень совместимого с BSD API сокетов обычно работает с той же или немного большей скоростью, что и стандартные реализации BSD, так как этот API использует внутренние примитивы NetX и обходит ненужную проверку ошибок NetX.</span><span class="sxs-lookup"><span data-stu-id="6df06-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX primitives and bypasses unnecessary NetX error checking.</span></span>

<span data-ttu-id="6df06-108">Настраиваемые параметры позволяют ведущему приложению определять максимальное число сокетов, максимальный размер окна TCP и глубину очереди прослушивания.</span><span class="sxs-lookup"><span data-stu-id="6df06-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="6df06-109">Из-за ограничений производительности и архитектуры этот совместимый с BSD API сокетов поддерживает не все вызовы сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="6df06-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="6df06-110">Кроме того, для служб BSD доступны не все параметры BSD, в частности действуют следующие ограничения:</span><span class="sxs-lookup"><span data-stu-id="6df06-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

- <span data-ttu-id="6df06-111">Функция ***select** _ работает только с _fd_set \*readfds*, и в этом вызове не поддерживаются другие аргументы, например *writefds* или *exceptfds*.</span><span class="sxs-lookup"><span data-stu-id="6df06-111">The ***select** _ function works with only _fd_set \*readfds*, other arguments in this call e.g., *writefds*, *exceptfds* are not supported.</span></span>
- <span data-ttu-id="6df06-112">Аргумент *int flags* не поддерживается для функций ***send** _, _*_recv_*_, _*_sendto_\*_ и _ *_recvfrom_* \*.</span><span class="sxs-lookup"><span data-stu-id="6df06-112">The *int flags* argument is not supported for the ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** functions.</span></span> <span data-ttu-id="6df06-113">Совместимый с BSD API сокетов поддерживает только ограниченный набор вызовов для сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="6df06-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="6df06-114">Исходный код отличается простотой и размещен всего в двух файлах: ***nx_bsd.c** _ и _*_nx_bsd.h_\*_.</span><span class="sxs-lookup"><span data-stu-id="6df06-114">The source code is designed for simplicity and is comprised of only two files,***nx_bsd.c** _ and _*_nx_bsd.h_\*_.</span></span> <span data-ttu-id="6df06-115">Для установки необходимо добавить эти два файла в проект сборки (но не в библиотеку NetX) и создать ведущее приложение, которое будет использовать вызовы службы сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="6df06-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="6df06-116">Файл _ *_nx_bsd.h_*\* также нужно включить в исходный код приложения.</span><span class="sxs-lookup"><span data-stu-id="6df06-116">The _ *_nx_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="6df06-117">Примеры демонстрационных файлов включены в дистрибутив, который бесплатно поставляется вместе с NetX.</span><span class="sxs-lookup"><span data-stu-id="6df06-117">Sample demo files are included with the distribution which is freely available with NetX.</span></span> <span data-ttu-id="6df06-118">Дополнительные сведения см. в справке по совместимому с BSD API сокетов **417** и файлах readme, которые входят в пакет совместимого с BSD API сокетов.</span><span class="sxs-lookup"><span data-stu-id="6df06-118">Further details are available in the help BSD-Compatible Socket API **417** and Readme files bundled with the BSD-Compatible Socket API package.</span></span>

<span data-ttu-id="6df06-119">Совместимый с BSD API сокетов поддерживает следующие вызовы API:</span><span class="sxs-lookup"><span data-stu-id="6df06-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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
