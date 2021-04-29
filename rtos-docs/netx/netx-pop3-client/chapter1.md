---
title: Глава 1. Введение в POP3-клиент NetX для ОСРВ Azure
description: API POP3-клиента NetX для ОСРВ Azure предоставляет почтовую транспортную систему, позволяющую небольшим рабочим станциям обращаться к почтовым ящикам клиента на POP3-серверах для получения почты клиента.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815167"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a><span data-ttu-id="714cd-103">Глава 1. Введение в POP3-клиент NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="714cd-103">Chapter 1 - Introduction to Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="714cd-104">Протокол POP3 (Post Office Protocol Version 3) — это протокол, предназначенный для предоставления почтовой транспортной системы, позволяющей небольшим рабочим станциям обращаться к почтовым ящикам клиента на POP3-серверах для получения почты клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="714cd-105">Для передачи почты протокол POP3 использует службы протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="714cd-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="714cd-106">Поэтому POP3 является надежным протоколом для обмена содержимым.</span><span class="sxs-lookup"><span data-stu-id="714cd-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="714cd-107">Однако протокол POP3 не предоставляет комплексных операций по обработке почты.</span><span class="sxs-lookup"><span data-stu-id="714cd-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="714cd-108">Как правило, почта скачивается клиентом, а затем удаляется из почтового ящика сервера.</span><span class="sxs-lookup"><span data-stu-id="714cd-108">Typically, mail is downloaded by the Client and then deleted from the Server's maildrop.</span></span>

## <a name="netx-pop3-client-requirements"></a><span data-ttu-id="714cd-109">Требования к использованию POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="714cd-109">NetX POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="714cd-110">Требования клиента</span><span class="sxs-lookup"><span data-stu-id="714cd-110">Client Requirements</span></span>

<span data-ttu-id="714cd-111">Для использования API POP3-клиента NetX для OCPB Azure требуется экземпляр IP NetX, созданный с помощью *nx_ip_create*, и пул пакетов NetX, созданный с помощью *nx_packet_pool_create*.</span><span class="sxs-lookup"><span data-stu-id="714cd-111">The Azure RTOS NetX POP3 Client API requires a previously created NetX IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="714cd-112">Так как POP3-клиент NetX применяет службы TCP, перед использованием служб POP3-клиента NetX на этом же экземпляре IP необходимо включить протокол TCP с помощью вызова *nx_tcp_enable*.</span><span class="sxs-lookup"><span data-stu-id="714cd-112">Because the NetX POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX POP3 Client services on that same IP instance.</span></span> <span data-ttu-id="714cd-113">POP3-клиент использует TCP-сокет для подключения к POP3-серверу через POP3-порт сервера.</span><span class="sxs-lookup"><span data-stu-id="714cd-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server's POP3 port.</span></span> <span data-ttu-id="714cd-114">Обычно это *хорошо известный порт 110, хотя ни POP3-клиент, ни сервер не обязаны использовать именно его.*</span><span class="sxs-lookup"><span data-stu-id="714cd-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server is required to use this port.*</span></span>

<span data-ttu-id="714cd-115">Размер пула пакетов, используемого при создании POP3-клиента, настраивается пользователем с точки зрения полезных данных пакета и количества доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="714cd-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="714cd-116">Если пакет используется только в службе создания POP3-клиента, полезная нагрузка пакета не должна превышать 100–120 байт в зависимости от длины имени пользователя и пароля или дайджеста APOP.</span><span class="sxs-lookup"><span data-stu-id="714cd-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="714cd-117">Возможно, команда USER с именем пользователя локального узла является самым длинным сообщением, отправляемым POP3-клиентом.</span><span class="sxs-lookup"><span data-stu-id="714cd-117">The USER command with the local host's user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="714cd-118">В nx_ip_create (пул пакетов IP по умолчанию) можно использовать тот же пул пакетов, так как для выполнения внутренних операций IP не требуется слишком большая полезная нагрузка пакетов для отправки и получения управляющих данных TCP.</span><span class="sxs-lookup"><span data-stu-id="714cd-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operations do not require a very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="714cd-119">Однако использование сетевым драйвером пула пакетов, совпадающего с пулом пакетов POP3-клиента, может быть нецелесообразным.</span><span class="sxs-lookup"><span data-stu-id="714cd-119">However, it may not be advantageous for the network driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="714cd-120">Как правило, полезные данные пула пакетов получения задаются с помощью MTU экземпляра IP (обычно 1500 байт) сетевого интерфейса, размер которого значительно превышает размер сообщений POP3-клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="714cd-121">Как правило, входящие сообщения POP3 имеют гораздо больший объем данных, чем исходящие сообщения POP3-клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-121">Incoming POP3 messages would usually be much larger data then outgoing POP3 Client messages</span></span>

## <a name="netx-pop3-client-creation"></a><span data-ttu-id="714cd-122">Создание POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="714cd-122">NetX POP3 Client Creation</span></span>

<span data-ttu-id="714cd-123">Служба создания POP3-клиента, *nx_pop3_client_create*, создает сокет TCP-сокет и подключается к POP3-серверу.</span><span class="sxs-lookup"><span data-stu-id="714cd-123">The POP3 Client create service, *nx_pop3_client_create* create the TCP socket and connect with the POP3 server.</span></span>

<span data-ttu-id="714cd-124">После подключения к POP3-серверу приложение POP3-клиента может вызвать службу *nx_pop3_client _mail_items_get*, чтобы получить количество почтовых элементов, находящихся в его почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="714cd-124">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

<span data-ttu-id="714cd-125">Если в почтовом ящике клиента находится один элемент или несколько, приложение может получить размер определенного почтового элемента с помощью службы *nx_pop3_client_get_mail_item*:</span><span class="sxs-lookup"><span data-stu-id="714cd-125">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

<span data-ttu-id="714cd-126">Первый почтовый элемент в почтовом ящике находится по индексу 1.</span><span class="sxs-lookup"><span data-stu-id="714cd-126">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="714cd-127">Чтобы получить реальное почтовое сообщение, приложение может вызывать службу *nx_pop3_client_mail_item_get_message_data* для извлечения пакетов почтовых сообщений, пока служба не сообщит о получении последнего пакета с помощью входного аргумента final_packet.</span><span class="sxs-lookup"><span data-stu-id="714cd-127">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

<span data-ttu-id="714cd-128">Чтобы удалить конкретный почтовый элемент, приложение вызывает службу *nx_pop3_client_mail_item_delete* с тем же индексом, который использовался в предыдущем вызове службы *nx_pop3_client_get_mail_item*.</span><span class="sxs-lookup"><span data-stu-id="714cd-128">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="714cd-129">Клиент можно удалить с помощью службы *nx_pop3_client_delete*.</span><span class="sxs-lookup"><span data-stu-id="714cd-129">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="714cd-130">Обратите внимание, что, если использовать пул пакетов POP3-клиента больше не требуется, приложение может удалить его помощью службы *nx_packet_pool_delete*.</span><span class="sxs-lookup"><span data-stu-id="714cd-130">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-pop3-client-constraints"></a><span data-ttu-id="714cd-131">Ограничения для POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="714cd-131">NetX POP3 Client Constraints</span></span>

<span data-ttu-id="714cd-132">В реализации POP3-клиента NetX существуют некоторые ограничения.</span><span class="sxs-lookup"><span data-stu-id="714cd-132">There are some constraints in the NetX POP3 Client implementation:</span></span>

1. <span data-ttu-id="714cd-133">POP3-клиент NetX не поддерживает команду AUTH, хотя он реализует проверку подлинности APOP, используя DIGEST-MD5 для проверки подлинности клиента и сервера.</span><span class="sxs-lookup"><span data-stu-id="714cd-133">The NetX POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>

1. <span data-ttu-id="714cd-134">POP3-клиент NetX поддерживает не все команды POP3 (например, команды TOP или UIDL).</span><span class="sxs-lookup"><span data-stu-id="714cd-134">NetX POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="714cd-135">Ниже приведен список поддерживаемых команд.</span><span class="sxs-lookup"><span data-stu-id="714cd-135">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="714cd-136">NOOP</span><span class="sxs-lookup"><span data-stu-id="714cd-136">NOOP</span></span>
   - <span data-ttu-id="714cd-137">RSET</span><span class="sxs-lookup"><span data-stu-id="714cd-137">RSET</span></span>

## <a name="netx-pop3-client-login"></a><span data-ttu-id="714cd-138">Имя входа POP3-клиента NetX</span><span class="sxs-lookup"><span data-stu-id="714cd-138">NetX POP3 Client Login</span></span>

<span data-ttu-id="714cd-139">Для получения доступа к почтовому ящику POP3-клиент NetX должен подтвердить свою подлинность (имя входа) на POP3-сервере.</span><span class="sxs-lookup"><span data-stu-id="714cd-139">A NetX POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="714cd-140">Это можно сделать с помощью команд USER/PASS и указания имени пользователя и пароля, известных POP3-серверу, или с помощью команды APOP и дайджеста MD5, как описано ниже.</span><span class="sxs-lookup"><span data-stu-id="714cd-140">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="714cd-141">Имя пользователя обычно является полным доменным именем (содержит компонент "local-part" и имя домена, разделенные символом @).</span><span class="sxs-lookup"><span data-stu-id="714cd-141">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an '@' character).</span></span> <span data-ttu-id="714cd-142">При использовании команд POP3 USER и PASS клиент отправляет свое имя пользователя и пароль в незашифрованном виде через Интернет.</span><span class="sxs-lookup"><span data-stu-id="714cd-142">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="714cd-143">Чтобы избежать угрозы безопасности, связанной с отправкой имени пользователя и пароля в виде открытого текста, POP3-клиент NetX можно настроить для использования проверки подлинности APOP, задав параметр *APOP_authentication* в службе *nx_pop3_client_create*.</span><span class="sxs-lookup"><span data-stu-id="714cd-143">To avoid the security risk of clear texting username and password, the NetX POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nx_pop3_client_create* service:</span></span>

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="714cd-144">Или только для приложений IPv4 использовать службу *nx_pop3_client_create*.</span><span class="sxs-lookup"><span data-stu-id="714cd-144">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="714cd-145">Когда клиент отправляет команду APOP, он принимает дайджест MD5, содержащий домен сервера, местное время и идентификатор процесса, извлеченные из приветственного сообщения сервера, а также пароль клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-145">When the Client sends the APOP command, it takes an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="714cd-146">POP3-сервер создаст дайджест MD5, содержащий те же данные, и, если его дайджест MD5 совпадет с дайджестом MD5 клиента, клиент проходит проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="714cd-146">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client's MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="714cd-147">Если проверка подлинности APOP завершается сбоем, POP3-клиент NetX попытается пройти проверку подлинности с помощью команд USER/PASS.</span><span class="sxs-lookup"><span data-stu-id="714cd-147">If APOP authentication fails, NetX POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="714cd-148">Почтовый ящик POP3-клиента</span><span class="sxs-lookup"><span data-stu-id="714cd-148">The POP3 Client Maildrop</span></span>

<span data-ttu-id="714cd-149">Клиентская почта хранится на POP3-сервере в почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="714cd-149">Client mail is stored on a POP3 Server in a mailbox or "maildrop."</span></span> <span data-ttu-id="714cd-150">Почтовый ящик клиента на POP3-сервере имеет вид списка почтовых элементов с отсчетом от 1.</span><span class="sxs-lookup"><span data-stu-id="714cd-150">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="714cd-151">Это означает, что каждое сообщение указывается по его индексу в списке. Первый почтовый элемент находится по индексу 1 (а не по нулевому индексу).</span><span class="sxs-lookup"><span data-stu-id="714cd-151">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="714cd-152">Команды POP3 ссылаются на определенные почтовые элементы по их индексу в этом списке.</span><span class="sxs-lookup"><span data-stu-id="714cd-152">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="714cd-153">Конечный автомат протокола POP3</span><span class="sxs-lookup"><span data-stu-id="714cd-153">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="714cd-154">Для использования протокола POP3 требуется, чтобы клиент и сервер поддерживали состояние сеанса POP3.</span><span class="sxs-lookup"><span data-stu-id="714cd-154">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="714cd-155">Сначала клиент пытается подключиться к POP3-серверу.</span><span class="sxs-lookup"><span data-stu-id="714cd-155">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="714cd-156">В случае успеха он подключается по протоколу POP3, имеющему три различных состояния, определенных стандартом RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="714cd-156">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="714cd-157">Начальное состояние — это состояние авторизации, в котором клиент должен пройти идентификацию на сервере.</span><span class="sxs-lookup"><span data-stu-id="714cd-157">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="714cd-158">В состоянии авторизации POP3-клиент может запускать только команды USER и PASS и только в таком порядке, или же команду APOP.</span><span class="sxs-lookup"><span data-stu-id="714cd-158">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="714cd-159">После проверки подлинности POP3-клиента сеанс клиента переходит в состояние транзакции.</span><span class="sxs-lookup"><span data-stu-id="714cd-159">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="714cd-160">В этом состоянии клиент может скачивать и запрашивать удаление почты.</span><span class="sxs-lookup"><span data-stu-id="714cd-160">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="714cd-161">В состоянии транзакции разрешено использовать команды LIST, STAT, RETR, DELE, RSET и QUIT.</span><span class="sxs-lookup"><span data-stu-id="714cd-161">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="714cd-162">Обычно POP3-клиент отправляет команду STAT, за которой следует ряд команд RETR (по одной для каждого почтового элемента в его почтовом ящике).</span><span class="sxs-lookup"><span data-stu-id="714cd-162">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="714cd-163">Когда клиент выдает команду QUIT, сеанс POP3 переходит в состояние обновления, в котором он инициирует отключение TCP от сервера.</span><span class="sxs-lookup"><span data-stu-id="714cd-163">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="714cd-164">Чтобы скачать почту позже, приложение POP3-клиента может в любое время вызвать `nx_pop3_client_mail_items_get` для проверки наличия новой почты в почтовом ящике.</span><span class="sxs-lookup"><span data-stu-id="714cd-164">To download mail later, the POP3 Client application may call `nx_pop3_client_mail_items_get` at any time to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="714cd-165">Коды ответа POP3-сервера</span><span class="sxs-lookup"><span data-stu-id="714cd-165">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="714cd-166">**+ OK**: сервер использует этот ответ для принятия команды клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-166">**+OK**: The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="714cd-167">Сервер может отправить дополнительные сведения после выдачи ответа "+ OK", но не может предположить, что клиент будет обрабатывать эту информацию, за исключением случаев скачивания данных почтового сообщения или команд LIST или DELE.</span><span class="sxs-lookup"><span data-stu-id="714cd-167">The Server can include additional information after the '+OK' but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="714cd-168">В последнем случае "аргумент" после команды указывает на индекс почтового элемента в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-168">In the latter case, the 'argument' after the command references the index of the mail item in the Client maildrop.</span></span>

- <span data-ttu-id="714cd-169">**-ERR**: сервер использует этот ответ для отклонения команды клиента.</span><span class="sxs-lookup"><span data-stu-id="714cd-169">**-ERR**: The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="714cd-170">Сервер может отправить дополнительные сведения после выдачи ответа "-ERR", но не может предположить, что клиент будет обрабатывать эту информацию.</span><span class="sxs-lookup"><span data-stu-id="714cd-170">The Server may send additional information following the '-ERR' but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="714cd-171">Пример сеанса POP3 для клиента и сервера</span><span class="sxs-lookup"><span data-stu-id="714cd-171">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="714cd-172">**Пример базового сеанса POP3 с использованием команд USER/PASS**</span><span class="sxs-lookup"><span data-stu-id="714cd-172">**Basic POP3 example using USER/PASS:**</span></span>

```c
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

<span data-ttu-id="714cd-173">**Пример базового сеанса POP3 с использованием команды APOP (и LIST вместо STAT)**</span><span class="sxs-lookup"><span data-stu-id="714cd-173">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

```c
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

## <a name="rfcs-supported-by-netx-pop3-client"></a><span data-ttu-id="714cd-174">Стандарты RFC, поддерживаемые POP3-клиентом NetX</span><span class="sxs-lookup"><span data-stu-id="714cd-174">RFCs Supported by NetX POP3 Client</span></span>

<span data-ttu-id="714cd-175">Клиент-POP3 NetX соответствует стандарту RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="714cd-175">NetX Client POP3 is compliant with RFC 1939.</span></span>
