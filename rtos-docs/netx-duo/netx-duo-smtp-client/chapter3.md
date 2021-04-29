---
title: Глава 3. Описание служб клиента SMTP
description: Эта глава содержит описание всех служб клиента NetX Duo SMTP (перечисленных ниже) в порядке использования в типичном клиентском приложении SMTP.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f590ba5a4c020b4a0aec6628a89c0e5f0f8579d9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814579"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a><span data-ttu-id="0fa53-103">Глава 3. Описание служб клиента SMTP</span><span class="sxs-lookup"><span data-stu-id="0fa53-103">Chapter 3 - Client description of SMTP Client services</span></span>

<span data-ttu-id="0fa53-104">Эта глава содержит описание всех служб клиента NetX Duo SMTP (перечисленных ниже) в порядке использования в типичном клиентском приложении SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-104">This chapter contains a description of all NetX Duo SMTP Client services (listed below) in order of usage in a typical SMTP Client application.</span></span>

> [!NOTE]
> <span data-ttu-id="0fa53-105">В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, выделенные **полужирным шрифтом**, не зависят от определения параметра **_NX_DISABLE_ERROR_CHECKING_**, который используется для отключения проверки на ошибки API, а значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="0fa53-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **_NX_DISABLE_ERROR_CHECKING_** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nxd_smtp_client_create"></a><span data-ttu-id="0fa53-106">nxd_smtp_client_create</span><span class="sxs-lookup"><span data-stu-id="0fa53-106">nxd_smtp_client_create</span></span>

<span data-ttu-id="0fa53-107">Создание экземпляра клиента SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-107">Create an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0fa53-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="0fa53-108">Prototype</span></span>

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="0fa53-109">Описание</span><span class="sxs-lookup"><span data-stu-id="0fa53-109">Description</span></span>

<span data-ttu-id="0fa53-110">Эта служба создает экземпляр клиента SMTP в указанном экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-110">This service creates an SMTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0fa53-111">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0fa53-111">Input Parameters</span></span>

- <span data-ttu-id="0fa53-112">**client_ptr**: указатель на блок управления клиентом SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-112">**client_ptr** Pointer to SMTP Client control block;</span></span>
- <span data-ttu-id="0fa53-113">**ip_ptr**: указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-113">**ip_ptr** Pointer to IP instance;</span></span>
- <span data-ttu-id="0fa53-114">**packet_pool_ptr**: указатель на пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="0fa53-114">**packet_pool_ptr** Pointer to Client packet pool;</span></span>
- <span data-ttu-id="0fa53-115">**username**: имя пользователя для проверки подлинности, оканчивающееся нулевым символом\*\*.</span><span class="sxs-lookup"><span data-stu-id="0fa53-115">**username** NULL-terminated\*\* Username for authentication</span></span>
- <span data-ttu-id="0fa53-116">**password**: пароль для проверки подлинности, оканчивающийся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="0fa53-116">**password** NULL-terminated password for authentication</span></span>
- <span data-ttu-id="0fa53-117">**from_address**: адрес отправителя, оканчивающийся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="0fa53-117">**from_address** NULL-terminated sender’s address</span></span>
- <span data-ttu-id="0fa53-118">**client_domain**: доменное имя, заканчивающееся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="0fa53-118">**client_domain** NULL-terminated domain name</span></span>
- <span data-ttu-id="0fa53-119">**authentication_type**: тип проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="0fa53-119">**authentication_type** Client authentication type.</span></span> <span data-ttu-id="0fa53-120">Поддерживаемые типы:</span><span class="sxs-lookup"><span data-stu-id="0fa53-120">Supported types are:</span></span>
  - <span data-ttu-id="0fa53-121">NX_SMTP_CLIENT_AUTH_LOGIN</span><span class="sxs-lookup"><span data-stu-id="0fa53-121">NX_SMTP_CLIENT_AUTH_LOGIN</span></span>
  - <span data-ttu-id="0fa53-122">NX_SMTP_CLIENT_AUTH_PLAIN</span><span class="sxs-lookup"><span data-stu-id="0fa53-122">NX_SMTP_CLIENT_AUTH_PLAIN</span></span>
  - <span data-ttu-id="0fa53-123">NX_SMTP_CLIENT_AUTH_NONE</span><span class="sxs-lookup"><span data-stu-id="0fa53-123">NX_SMTP_CLIENT_AUTH_NONE</span></span>
- <span data-ttu-id="0fa53-124">**server_address**: указатель на IP-адрес сервера SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-124">**server_address** Pointer to SMTP Server IP address</span></span>
- <span data-ttu-id="0fa53-125">**server_port**: TCP-порт сервера SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-125">**server_port** SMTP Server TCP port</span></span>

### <a name="return-values"></a><span data-ttu-id="0fa53-126">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0fa53-126">Return Values</span></span>

- <span data-ttu-id="0fa53-127">**NX_SUCCESS** (0x00): клиент SMTP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="0fa53-127">**NX_SUCCESS** (0x00) SMTP Client successfully created.</span></span> <span data-ttu-id="0fa53-128">Состояние создания сокета TCP</span><span class="sxs-lookup"><span data-stu-id="0fa53-128">TCP socket creation status</span></span>
- <span data-ttu-id="0fa53-129">NX_SMTP_INVALID_PARAM (0xA5): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="0fa53-129">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="0fa53-130">NX_IP_ADDRESS_ERROR (0x21): недопустимый тип IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="0fa53-130">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address type</span></span>
- <span data-ttu-id="0fa53-131">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="0fa53-131">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0fa53-132">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0fa53-132">Allowed From</span></span>

<span data-ttu-id="0fa53-133">Код приложения</span><span class="sxs-lookup"><span data-stu-id="0fa53-133">Application Code</span></span>

### <a name="example"></a><span data-ttu-id="0fa53-134">Например, .</span><span class="sxs-lookup"><span data-stu-id="0fa53-134">Example</span></span>

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a><span data-ttu-id="0fa53-135">nx_smtp_client_delete</span><span class="sxs-lookup"><span data-stu-id="0fa53-135">nx_smtp_client_delete</span></span>

<span data-ttu-id="0fa53-136">Удаление экземпляра клиента SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-136">Delete an SMTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="0fa53-137">Прототип</span><span class="sxs-lookup"><span data-stu-id="0fa53-137">Prototype</span></span>

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="0fa53-138">Описание</span><span class="sxs-lookup"><span data-stu-id="0fa53-138">Description</span></span>

<span data-ttu-id="0fa53-139">Эта служба удаляет созданный ранее экземпляр клиента SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-139">This service deletes a previously created SMTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0fa53-140">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0fa53-140">Input Parameters</span></span>

- <span data-ttu-id="0fa53-141">**client_ptr**: указатель на экземпляр клиента SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-141">**client_ptr** Pointer to SMTP Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0fa53-142">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0fa53-142">Return Values</span></span>

- <span data-ttu-id="0fa53-143">**NX_SUCCESS** (0x00): клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="0fa53-143">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="0fa53-144">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="0fa53-144">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0fa53-145">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0fa53-145">Allowed From</span></span>

<span data-ttu-id="0fa53-146">Потоки</span><span class="sxs-lookup"><span data-stu-id="0fa53-146">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0fa53-147">Например, .</span><span class="sxs-lookup"><span data-stu-id="0fa53-147">Example</span></span>

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a><span data-ttu-id="0fa53-148">nx_smtp_mail_send</span><span class="sxs-lookup"><span data-stu-id="0fa53-148">nx_smtp_mail_send</span></span>

<span data-ttu-id="0fa53-149">Создание и отправка почтового элемента SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-149">Create and send an SMTP mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="0fa53-150">Прототип</span><span class="sxs-lookup"><span data-stu-id="0fa53-150">Prototype</span></span>

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a><span data-ttu-id="0fa53-151">Описание</span><span class="sxs-lookup"><span data-stu-id="0fa53-151">Description</span></span>

<span data-ttu-id="0fa53-152">Эта служба создает и отправляет почтовый элемент SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-152">This service creates and sends an SMTP mail item.</span></span> <span data-ttu-id="0fa53-153">Клиент SMTP устанавливает TCP-подключение к серверу SMTP и отправляет серию команд SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-153">The SMTP Client establishes a TCP connection with the SMTP Server and sends a series of SMTP commands.</span></span> <span data-ttu-id="0fa53-154">Если ошибки не обнаружены, он передает почтовое сообщение на сервер.</span><span class="sxs-lookup"><span data-stu-id="0fa53-154">If no errors are encountered, it will transmit the mail message to the Server.</span></span> <span data-ttu-id="0fa53-155">Независимо от того, было ли успешно отправлено сообщение, TCP-подключение разрывается и возвращается состояние, указывающее на результат передачи почты.</span><span class="sxs-lookup"><span data-stu-id="0fa53-155">Regardless if the mail is sent successfully it will terminate the TCP connection and return a status indicating outcome of the mail transmission.</span></span> <span data-ttu-id="0fa53-156">Приложение может вызывать эту службу для любого количества почтовых сообщений, которые необходимо отправить.</span><span class="sxs-lookup"><span data-stu-id="0fa53-156">The application may call this service for as many mail messages as it needs to send without limit.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0fa53-157">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0fa53-157">Input Parameters</span></span>

- <span data-ttu-id="0fa53-158">**client_ptr**: указатель на клиент SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-158">**client_ptr** Pointer to SMTP Client</span></span>
- <span data-ttu-id="0fa53-159">**recipient_address**: адрес получателя, оканчивающийся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="0fa53-159">**recipient_address** NULL-terminated recipient address.</span></span>
- <span data-ttu-id="0fa53-160">**subject**: текст строки темы, оканчивающийся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="0fa53-160">**subject** NULL-terminated subject line text;.</span></span>
- <span data-ttu-id="0fa53-161">**priority**: уровень приоритета доставки почты.</span><span class="sxs-lookup"><span data-stu-id="0fa53-161">**priority** Priority level at which mail is delivered</span></span>
- <span data-ttu-id="0fa53-162">**mail_body**: указатель на почтовое сообщение.</span><span class="sxs-lookup"><span data-stu-id="0fa53-162">**mail_body** Pointer to mail message</span></span>
- <span data-ttu-id="0fa53-163">**mail_body_length**: размер почтового сообщения.</span><span class="sxs-lookup"><span data-stu-id="0fa53-163">**mail_body_length** Size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="0fa53-164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0fa53-164">Return Values</span></span>

- <span data-ttu-id="0fa53-165">**NX_SUCCESS** (0x00): почта успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="0fa53-165">**NX_SUCCESS** (0x00) Mail successfully sent</span></span>
- <span data-ttu-id="0fa53-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2): экземпляр клиента SMTP не инициализирован для состояния сеанса SMTP, соответствующего результату сеанса SMTP.</span><span class="sxs-lookup"><span data-stu-id="0fa53-166">**NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2) SMTP Client instance not initialized for SMTP session status Outcome of SMTP session</span></span>
- <span data-ttu-id="0fa53-167">NX_PTR_ERROR (0x07): недопустимый параметр указателя.</span><span class="sxs-lookup"><span data-stu-id="0fa53-167">NX_PTR_ERROR (0x07) Invalid pointer parameter</span></span>
- <span data-ttu-id="0fa53-168">NX_SMTP_INVALID_PARAM (0xA5): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="0fa53-168">NX_SMTP_INVALID_PARAM (0xA5) Invalid non pointer input</span></span>
- <span data-ttu-id="0fa53-169">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="0fa53-169">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0fa53-170">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0fa53-170">Allowed From</span></span>

<span data-ttu-id="0fa53-171">Потоки</span><span class="sxs-lookup"><span data-stu-id="0fa53-171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0fa53-172">Пример</span><span class="sxs-lookup"><span data-stu-id="0fa53-172">Example</span></span>

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
