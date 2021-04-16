---
title: Глава 1. Введение в POP3 для NetX (ОСРВ Azure)
description: API клиента POP3 для NetX Duo предоставляет почтовую транспортную систему, которая позволяет небольшим рабочим станциям обращаться к почтовым ящикам клиента на POP3-серверах для получения почты клиента.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4d41da1e1e87e59c5c40674a58b288ac62ec8c78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814619"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a><span data-ttu-id="f08ec-103">Глава 1. Введение в POP3 для NetX (ОСРВ Azure)</span><span class="sxs-lookup"><span data-stu-id="f08ec-103">Chapter 1 - Introduction to Azure RTOS NetX POP3</span></span>

<span data-ttu-id="f08ec-104">Протокол POP3 (Post Office Protocol Version 3) предназначен для организации почтовой транспортной системы, позволяющей небольшим рабочим станциям обращаться к почтовым ящикам клиента на POP3-серверах для получения почты клиента.</span><span class="sxs-lookup"><span data-stu-id="f08ec-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="f08ec-105">Для передачи почты протокол POP3 использует службы протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="f08ec-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="f08ec-106">Благодаря этому POP3 считается очень надежным протоколом для обмена содержимым.</span><span class="sxs-lookup"><span data-stu-id="f08ec-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="f08ec-107">Но протокол POP3 не предоставляет сложных операций для обработки почты.</span><span class="sxs-lookup"><span data-stu-id="f08ec-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="f08ec-108">Как правило, почта скачивается клиентом, а затем удаляется из почтового ящика на сервере.</span><span class="sxs-lookup"><span data-stu-id="f08ec-108">Typically, mail is downloaded by the Client and then deleted from the Server’s maildrop.</span></span>

## <a name="netx-duo-pop3-client-requirements"></a><span data-ttu-id="f08ec-109">Требования к использованию клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f08ec-109">NetX Duo POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="f08ec-110">Требования клиента</span><span class="sxs-lookup"><span data-stu-id="f08ec-110">Client Requirements</span></span>

<span data-ttu-id="f08ec-111">Для использования API клиента POP3 для NetX требуется экземпляр IP для NetX Duo, созданный с помощью *nx_ip_create*, и пул пакетов NetX, созданный с помощью *nx_packet_pool_create*.</span><span class="sxs-lookup"><span data-stu-id="f08ec-111">The NetX POP3 Client API requires a previously created NetX Duo IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="f08ec-112">Так как клиент POP3 для NetX Duo применяет службы TCP, перед использованием API клиента POP3 для NetX Duo необходимо включить протокол TCP на этом же экземпляре IP с помощью вызова *nx_tcp_enable*.</span><span class="sxs-lookup"><span data-stu-id="f08ec-112">Because the NetX Duo POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX Duo POP3 Client API on that same IP instance.</span></span> <span data-ttu-id="f08ec-113">Клиент POP3 использует TCP-сокет для подключения к серверу POP3 через порт POP3 сервера.</span><span class="sxs-lookup"><span data-stu-id="f08ec-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server’s POP3 port.</span></span> <span data-ttu-id="f08ec-114">Обычно это *хорошо известный порт 110, хотя ни клиент, ни сервер POP3 не обязаны использовать именно его.*</span><span class="sxs-lookup"><span data-stu-id="f08ec-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server are required to use this port.*</span></span>

<span data-ttu-id="f08ec-115">Размер пула пакетов, используемого при создании клиента POP3, настраивается пользователем с учетом полезных данных пакета и количества доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="f08ec-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="f08ec-116">Если пакет используется только в службе создания клиента POP3, полезная нагрузка пакета не должна превышать 100–120 байтов в зависимости от длины имени пользователя и пароля или дайджеста APOP.</span><span class="sxs-lookup"><span data-stu-id="f08ec-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="f08ec-117">Возможно, команда USER с именем пользователя локального узла будет самым длинным сообщением, отправляемым клиентом POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-117">The USER command with the local host’s user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="f08ec-118">При создании пула пакетов IP по умолчанию (nx_ip_create) можно использовать тот же пул пакетов, так как для выполнения внутренних операций IP не требуется слишком большая полезная нагрузка пакетов для отправки и получения управляющих данных TCP.</span><span class="sxs-lookup"><span data-stu-id="f08ec-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operatiosn do not require very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="f08ec-119">Но драйвер Ethernet не получит никаких преимуществ от использования того же пула пакетов, который настроен для клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-119">However, it is not generally advantageous for the Ethernet driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="f08ec-120">Как правило, полезные данные пула пакетов получения задаются с помощью MTU экземпляра IP (обычно 1500 байтов) сетевого интерфейса, размер которого значительно превышает размер сообщений клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="f08ec-121">Как правило, входящие сообщения POP3 имеют гораздо больший объем данных, чем исходящие сообщения клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-121">Incoming POP3 messages would usually be much larger data size then outgoing POP3 Client messages</span></span>

## <a name="netx-duo-pop3-client-creation"></a><span data-ttu-id="f08ec-122">Создание клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f08ec-122">NetX Duo POP3 Client Creation</span></span>

<span data-ttu-id="f08ec-123">Существует две службы для создания клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-123">There are two services for creating the POP3 Client.</span></span> <span data-ttu-id="f08ec-124">Мы рекомендуем использовать *nxd_pop3_client_create*, которая принимает тип данных адреса (NXD_ADDRESS) с поддержкой IPv4- и IPv6-адресов сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-124">The recommended service is *nxd_pop3_client_create* which takes an NXD_ADDRESS address data type that accepts IPv4 or IPv6 addresses for the POP3 server.</span></span> <span data-ttu-id="f08ec-125">Другая служба создания клиента POP3, *nx_pop3_client_create*, принимает только IPv4-адреса сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-125">The other POP3 Client create service, *nx_pop3_client_create*, only accepts IPv4 addresses for the POP3 server.</span></span> <span data-ttu-id="f08ec-126">Обе службы привязывают порт сокета TCP и подключаются к серверу POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-126">Both services bind the TCP socket port and connect with the POP3 server.</span></span>

<span data-ttu-id="f08ec-127">После подключения к серверу POP3 приложение клиента POP3 может вызвать службу *nx_pop3_client _mail_items_get*, чтобы получить количество почтовых элементов, находящихся в его почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="f08ec-127">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

<span data-ttu-id="f08ec-128">Если в почтовом ящике клиента есть один или несколько элементов, приложение может получить размер определенного элемента почты с помощью службы *nx_pop3_client_get_mail_item*:</span><span class="sxs-lookup"><span data-stu-id="f08ec-128">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

<span data-ttu-id="f08ec-129">Первый элемент почты в почтовом ящике находится по индексу 1.</span><span class="sxs-lookup"><span data-stu-id="f08ec-129">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="f08ec-130">Чтобы получить реальное почтовое сообщение, приложение может вызывать службу *nx_pop3_client_mail_item_get_message_data* и получать пакеты почтовых сообщений, пока служба не сообщит о передаче последнего пакета с помощью входного аргумента final_packet.</span><span class="sxs-lookup"><span data-stu-id="f08ec-130">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

<span data-ttu-id="f08ec-131">Чтобы удалить определенный элемент электронной почты, приложение вызывает службу *nx_pop3_client_mail_item_delete* с тем же индексом, который использовался в предыдущем вызове службы *nx_pop3_client_get_mail_item*.</span><span class="sxs-lookup"><span data-stu-id="f08ec-131">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="f08ec-132">Клиент можно удалить с помощью службы *nx_pop3_client_delete*.</span><span class="sxs-lookup"><span data-stu-id="f08ec-132">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="f08ec-133">Обратите внимание, что приложение должно самостоятельно удалить пул пакетов клиента POP3 помощью службы *nx_packet_pool_delete*, если этот пул больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="f08ec-133">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-duo-pop3-client-constraints"></a><span data-ttu-id="f08ec-134">Ограничения клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f08ec-134">NetX Duo POP3 Client Constraints</span></span>

<span data-ttu-id="f08ec-135">В реализации клиента POP3 для NetX Duo существуют некоторые ограничения:</span><span class="sxs-lookup"><span data-stu-id="f08ec-135">There are some constraints in the NetX Duo POP3 Client implementation:</span></span>

1. <span data-ttu-id="f08ec-136">Клиент POP3 для NetX Duo не поддерживает команду AUTH, хотя и реализует проверку подлинности APOP, используя DIGEST-MD5 для проверки подлинности клиента и сервера.</span><span class="sxs-lookup"><span data-stu-id="f08ec-136">The NetX Duo POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>
2. <span data-ttu-id="f08ec-137">Клиент POP3 для NetX Duo не поддерживает некоторые команды POP3 (например, TOP или UIDL).</span><span class="sxs-lookup"><span data-stu-id="f08ec-137">NetX Duo POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="f08ec-138">Ниже приведен список поддерживаемых команд:</span><span class="sxs-lookup"><span data-stu-id="f08ec-138">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="f08ec-139">NOOP</span><span class="sxs-lookup"><span data-stu-id="f08ec-139">NOOP</span></span>
   - <span data-ttu-id="f08ec-140">RSET</span><span class="sxs-lookup"><span data-stu-id="f08ec-140">RSET</span></span>

## <a name="netx-duo-pop3-client-login"></a><span data-ttu-id="f08ec-141">Выполнение входа для клиента POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f08ec-141">NetX Duo POP3 Client Login</span></span>

<span data-ttu-id="f08ec-142">Для получения доступа к почтовому ящику клиент POP3 для NetX Duo должен пройти на сервере POP3 проверку подлинности по имени.</span><span class="sxs-lookup"><span data-stu-id="f08ec-142">A NetX Duo POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="f08ec-143">Для этого можно в команде USER/PASS передать имя пользователя и пароль, известные серверу POP3, или в команде APOP передать дайджест MD5, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="f08ec-143">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="f08ec-144">Имя пользователя обычно является полным доменным именем (содержит компоненты локального имени и доменного имени, разделенные символом @).</span><span class="sxs-lookup"><span data-stu-id="f08ec-144">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an ‘@’ character).</span></span> <span data-ttu-id="f08ec-145">При использовании команд POP3 USER и PASS клиент отправляет имя пользователя и пароль в незашифрованном виде через Интернет.</span><span class="sxs-lookup"><span data-stu-id="f08ec-145">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="f08ec-146">Чтобы избежать угрозы безопасности, связанной с отправкой имени пользователя и пароля в виде открытого текста, для клиента POP3 для NetX Duo можно настроить проверку подлинности APOP, задав параметр *APOP_authentication* в службе *nx_pop3_client_create*.</span><span class="sxs-lookup"><span data-stu-id="f08ec-146">To avoid the security risk of clear texting username and password, the NetX Duo POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nxd_pop3_client_create* service:</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

<span data-ttu-id="f08ec-147">Для приложений IPv4 можно также использовать службу *nx_pop3_client_create*.</span><span class="sxs-lookup"><span data-stu-id="f08ec-147">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

<span data-ttu-id="f08ec-148">Когда клиент отправляет команду APOP, она принимает в качестве единственного аргумента дайджест MD5, содержащий домен сервера, местное время и идентификатор процесса, извлеченные из приветственного сообщения сервера, а также пароль клиента.</span><span class="sxs-lookup"><span data-stu-id="f08ec-148">When the Client sends the APOP command, it takes as its only argument an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="f08ec-149">Сервер POP3 создаст дайджест MD5, содержащий те же данные, и, если его дайджест MD5 совпадет с дайджестом MD5 клиента, клиент проходит проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="f08ec-149">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client’s MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="f08ec-150">Если проверка подлинности APOP завершится сбоем, клиент POP3 для NetX Duo попытается пройти проверку подлинности с помощью команд USER/PASS.</span><span class="sxs-lookup"><span data-stu-id="f08ec-150">If APOP authentication fails, NetX Duo POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="f08ec-151">Почтовый ящик клиента POP3</span><span class="sxs-lookup"><span data-stu-id="f08ec-151">The POP3 Client Maildrop</span></span>

<span data-ttu-id="f08ec-152">Почта для клиента хранится на сервере POP3 в так называемом почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="f08ec-152">Client mail is stored on a POP3 Server in a mailbox or “maildrop.”</span></span> <span data-ttu-id="f08ec-153">Почтовый ящик клиента на сервере POP3 представлен в виде списка элементов почты, которые нумеруются последовательно, начиная с номера 1.</span><span class="sxs-lookup"><span data-stu-id="f08ec-153">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="f08ec-154">Это означает, что каждое сообщение определяется по его индексу в списке. Первый почтовый элемент имеет индекс 1 (а не 0).</span><span class="sxs-lookup"><span data-stu-id="f08ec-154">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="f08ec-155">Команды POP3 ссылаются на элементы почты по индексу в этом списке.</span><span class="sxs-lookup"><span data-stu-id="f08ec-155">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="f08ec-156">Конечный автомат протокола POP3</span><span class="sxs-lookup"><span data-stu-id="f08ec-156">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="f08ec-157">Для работы протокола POP3 требуется, чтобы клиент и сервер поддерживали состояние сеанса POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-157">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="f08ec-158">Сначала клиент пытается подключиться к серверу POP3.</span><span class="sxs-lookup"><span data-stu-id="f08ec-158">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="f08ec-159">В случае успеха он применяет три состояния протокола POP3, определенные стандартом RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="f08ec-159">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="f08ec-160">Начальным считается состояние авторизации, в котором клиент должен пройти идентификацию на сервере.</span><span class="sxs-lookup"><span data-stu-id="f08ec-160">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="f08ec-161">В состоянии авторизации клиент POP3 может передавать только команды USER и PASS (строго в таком порядке) или команду APOP.</span><span class="sxs-lookup"><span data-stu-id="f08ec-161">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="f08ec-162">После проверки подлинности сеанс клиента POP3 переходит в состояние транзакции.</span><span class="sxs-lookup"><span data-stu-id="f08ec-162">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="f08ec-163">В этом состоянии клиент может скачивать почту и запрашивать ее удаление.</span><span class="sxs-lookup"><span data-stu-id="f08ec-163">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="f08ec-164">В состоянии транзакции допускаются команды LIST, STAT, RETR, DELE, RSET и QUIT.</span><span class="sxs-lookup"><span data-stu-id="f08ec-164">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="f08ec-165">Обычно клиент POP3 отправляет команду STAT, за которой следует ряд команд RETR (по одной для каждого элемента электронной почты в почтовом ящике).</span><span class="sxs-lookup"><span data-stu-id="f08ec-165">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="f08ec-166">Когда клиент выдает команду QUIT, сеанс POP3 переходит в состояние обновления, в котором инициируется отключение канала TCP от сервера.</span><span class="sxs-lookup"><span data-stu-id="f08ec-166">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="f08ec-167">Чтобы снова получить почту, приложение клиента POP3 может вызвать nx_pop3_client_mail_items_get для проверки наличия новых элементов в почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="f08ec-167">To download mail at another time, the POP3 Client application can call nx_pop3_client_mail_items_get to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="f08ec-168">Коды ответа сервера POP3</span><span class="sxs-lookup"><span data-stu-id="f08ec-168">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="f08ec-169">+OK: сервер использует этот ответ для подтверждения команды клиента.</span><span class="sxs-lookup"><span data-stu-id="f08ec-169">+OK The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="f08ec-170">Сервер может отправить дополнительные сведения после ответа "+OK", но не может ожидать, что клиент будет учитывать эту информацию, за исключением сценариев со скачиванием данных почтового сообщения или выполнением команд LIST или DELE.</span><span class="sxs-lookup"><span data-stu-id="f08ec-170">The Server can include additional information after the ‘+OK’ but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="f08ec-171">В последнем случае после команды указывается аргумент, который обозначает индекс элемента электронной почты в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="f08ec-171">In the latter case, the ‘argument’ after the command references the index of the mail item in the Client maildrop.</span></span>
- <span data-ttu-id="f08ec-172">-ERR: сервер использует этот ответ для отклонения команды клиента.</span><span class="sxs-lookup"><span data-stu-id="f08ec-172">-ERR The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="f08ec-173">Сервер может отправить дополнительные сведения после ответа -ERR, но не может ожидать, что клиент будет обрабатывать эту информацию.</span><span class="sxs-lookup"><span data-stu-id="f08ec-173">The Server may send additional information following the ‘-ERR’ but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="f08ec-174">Пример сеанса POP3 между клиентом и сервером</span><span class="sxs-lookup"><span data-stu-id="f08ec-174">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="f08ec-175">**Простой пример сеанса POP3 с использованием команд USER/PASS**</span><span class="sxs-lookup"><span data-stu-id="f08ec-175">**Basic POP3 example using USER/PASS:**</span></span>

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

<span data-ttu-id="f08ec-176">**Простой пример сеанса POP3 с использованием команды APOP (и LIST вместо STAT)**</span><span class="sxs-lookup"><span data-stu-id="f08ec-176">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

```
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a><span data-ttu-id="f08ec-177">Стандарты RFC, поддерживаемые клиентом POP3 для NetX Duo</span><span class="sxs-lookup"><span data-stu-id="f08ec-177">RFCs Supported by NetX Duo POP3 Client</span></span>

<span data-ttu-id="f08ec-178">Клиент POP3 для NetX Duo соответствует стандарту RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="f08ec-178">NetX Duo Client POP3 is compliant with RFC 1939.</span></span>
