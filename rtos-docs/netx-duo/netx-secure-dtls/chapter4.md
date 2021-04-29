---
title: Глава 4. Описание служб ОСРВ Azure NetX Secure DTLS
description: В этой главе приведено описание всех служб ОСРВ Azure NetX Secure DTLS, перечисленных в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e795a5fa35a4590e508c7fe2eec53f5494809657
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814512"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a><span data-ttu-id="1ca36-103">Глава 4. Описание служб ОСРВ Azure NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="1ca36-103">Chapter 4: Description of Azure RTOS NetX Secure DTLS services</span></span>

<span data-ttu-id="1ca36-104">В этой главе приведено описание всех служб ОСРВ Azure NetX Secure DTLS (см. ниже), перечисленных в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="1ca36-104">This chapter contains a description of all Azure RTOS NetX Secure DTLS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="1ca36-105">В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, **выделенные жирным шрифтом**, не обрабатываются макросом **NX_SECURE_DISABLE_ERROR_CHECKING**, который используется, чтобы отключить проверку ошибок API, в то время как для значений, не выделенных жирным шрифтом, эта проверка полностью отключена.</span><span class="sxs-lookup"><span data-stu-id="1ca36-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="1ca36-106">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-106">nx_secure_dtls_client_session_start</span></span>](#nx_secure_dtls_client_session_start)
- [<span data-ttu-id="1ca36-107">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="1ca36-107">nx_secure_dtls_packet_allocate</span></span>](#nx_secure_dtls_packet_allocate)
- [<span data-ttu-id="1ca36-108">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-108">nx_secure_dtls_psk_add</span></span>](#nx_secure_dtls_psk_add)
- [<span data-ttu-id="1ca36-109">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-109">nx_secure_dtls_server_create</span></span>](#nx_secure_dtls_server_create)
- [<span data-ttu-id="1ca36-110">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-110">nx_secure_dtls_server_delete</span></span>](#nx_secure_dtls_server_delete)
- [<span data-ttu-id="1ca36-111">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-111">nx_secure_dtls_server_local_certificate_add</span></span>](#nx_secure_dtls_server_local_certificate_add)
- [<span data-ttu-id="1ca36-112">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-112">nx_secure_dtls_server_local_certificate_remove</span></span>](#nx_secure_dtls_server_local_certificate_remove)
- [<span data-ttu-id="1ca36-113">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="1ca36-113">nx_secure_dtls_server_notify_set</span></span>](#nx_secure_dtls_server_notify_set)
- [<span data-ttu-id="1ca36-114">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-114">nx_secure_dtls_server_psk_add</span></span>](#nx_secure_dtls_server_psk_add)
- [<span data-ttu-id="1ca36-115">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-115">nx_secure_dtls_server_session_send</span></span>](#nx_secure_dtls_server_session_send)
- [<span data-ttu-id="1ca36-116">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-116">nx_secure_dtls_server_session_start</span></span>](#nx_secure_dtls_server_session_start)
- [<span data-ttu-id="1ca36-117">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-117">nx_secure_dtls_server_start</span></span>](#nx_secure_dtls_server_start)
- [<span data-ttu-id="1ca36-118">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-118">nx_secure_dtls_server_stop</span></span>](#nx_secure_dtls_server_stop)
- [<span data-ttu-id="1ca36-119">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-119">nx_secure_dtls_server_trusted_certificate_add</span></span>](#nx_secure_dtls_server_trusted_certificate_add)
- [<span data-ttu-id="1ca36-120">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-120">nx_secure_dtls_server_trusted_certificate_remove</span></span>](#nx_secure_dtls_server_trusted_certificate_remove)
- [<span data-ttu-id="1ca36-121">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="1ca36-121">nx_secure_dtls_server_x509_client_verify_configure</span></span>](#nx_secure_dtls_server_x509_client_verify_configure)
- [<span data-ttu-id="1ca36-122">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="1ca36-122">nx_secure_dtls_server_x509_client_verify_disable</span></span>](#nx_secure_dtls_server_x509_client_verify_disable)
- [<span data-ttu-id="1ca36-123">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="1ca36-123">nx_secure_dtls_session_client_info_get</span></span>](#nx_secure_dtls_session_client_info_get)
- [<span data-ttu-id="1ca36-124">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-124">nx_secure_dtls_session_create</span></span>](#nx_secure_dtls_session_create)
- [<span data-ttu-id="1ca36-125">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-125">nx_secure_dtls_session_delete</span></span>](#nx_secure_dtls_session_delete)
- [<span data-ttu-id="1ca36-126">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="1ca36-126">nx_secure_dtls_session_end</span></span>](#nx_secure_dtls_session_end)
- [<span data-ttu-id="1ca36-127">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-127">nx_secure_dtls_session_local_certificate_add</span></span>](#nx_secure_dtls_session_local_certificate_add)
- [<span data-ttu-id="1ca36-128">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-128">nx_secure_dtls_session_local_certificate_remove</span></span>](#nx_secure_dtls_session_local_certificate_remove)
- [<span data-ttu-id="1ca36-129">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-129">nx_secure_dtls_session_receive</span></span>](#nx_secure_dtls_session_receive)
- [<span data-ttu-id="1ca36-130">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="1ca36-130">nx_secure_dtls_session_reset</span></span>](#nx_secure_dtls_session_reset)
- [<span data-ttu-id="1ca36-131">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-131">nx_secure_dtls_ session_send</span></span>](#nx_secure_dtls_-session_send)
- [<span data-ttu-id="1ca36-132">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-132">nx_secure_dtls_session_trusted_certificate_add</span></span>](#nx_secure_dtls_session_trusted_certificate_add)
- [<span data-ttu-id="1ca36-133">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-133">nx_secure_dtls_session_trusted_certificate_remove</span></span>](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a><span data-ttu-id="1ca36-134">nx_secure_dtls_client_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-134">nx_secure_dtls_client_session_start</span></span>

<span data-ttu-id="1ca36-135">Запуск сеанса клиента NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-135">Start a NetX Secure DTLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-136">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-136">Prototype</span></span>

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="1ca36-137">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-137">Description</span></span>

<span data-ttu-id="1ca36-138">Эта служба запускает сеанс клиента DTLS, подключаясь к серверу по указанному IP-адресу и UDP-порту с помощью предоставленного сокета UDP для сетевого взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="1ca36-138">This service starts a DTLS Client session, connecting to the server at the provided IP address and UDP port, using the provided UDP socket for network communications.</span></span>

<span data-ttu-id="1ca36-139">Перед вызовом этой службы нужно инициализировать блок управления сеансом DTLS с помощью службы nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="1ca36-139">The DTLS session control block must be initialized prior to calling this service using nx_secure_dtls_session_create.</span></span> <span data-ttu-id="1ca36-140">Кроме того, клиент DTLS требует, чтобы в сеанс был добавлен по крайней мере один сертификат доверенного ЦС с помощью nx_secure_dtls_session_trusted_certificate_add или включены и настроены общие ключи.</span><span class="sxs-lookup"><span data-stu-id="1ca36-140">Additionally, the DTLS Client requires that at least one trusted CA certificate has been added to the session using nx_secure_dtls_session_trusted_certificate_add or Pre-Shared Keys are enabled and configured.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-141">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-141">Parameters</span></span>

- <span data-ttu-id="1ca36-142">**dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.</span><span class="sxs-lookup"><span data-stu-id="1ca36-142">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="1ca36-143">**udp_socket**: инициализированный сокет UDP, который будет использоваться для установления сетевого подключения к удаленному серверу DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-143">**udp_socket** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="1ca36-144">**ip_address**: указатель на структуру IP-адреса, содержащую адрес удаленного сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-144">**ip_address** Pointer to IP address structure containing the address of the remote DTLS server.</span></span>
- <span data-ttu-id="1ca36-145">**port**: инициализированный порт, который будет использоваться для установления сетевого подключения к удаленному серверу DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-145">**port** Initialized UDP socket that will be used to establish network communications with the remote DTLS server.</span></span>
- <span data-ttu-id="1ca36-146">**wait_option**: параметр приостановки для попытки подключения.</span><span class="sxs-lookup"><span data-stu-id="1ca36-146">**wait_option** Suspension option for connection attempt.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-147">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-147">Return Values</span></span>

- <span data-ttu-id="1ca36-148">**NX_SUCCESS** (0X00): сертификат успешно назначен сеансу.</span><span class="sxs-lookup"><span data-stu-id="1ca36-148">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="1ca36-149">**NX_NOT_CONNECTED** (0x38): сервер недоступен по указанному адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="1ca36-149">**NX_NOT_CONNECTED** (0x38) The server cannot be reached at the given address and port.</span></span>
- <span data-ttu-id="1ca36-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102): получен неправильный тип сообщения TLS или DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-150">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS/DTLS message type is incorrect.</span></span>
- <span data-ttu-id="1ca36-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106): шифр, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="1ca36-151">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="1ca36-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107): не удалось обработать сообщение во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-152">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="1ca36-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108): не удалось проверить хэш MAC во входящем сообщении.</span><span class="sxs-lookup"><span data-stu-id="1ca36-153">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="1ca36-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): не удалось отправить данные через базовый сокет TCP.</span><span class="sxs-lookup"><span data-stu-id="1ca36-154">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="1ca36-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A): входящее сообщение содержало недопустимое поле длины.</span><span class="sxs-lookup"><span data-stu-id="1ca36-155">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="1ca36-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B): неправильное входящее сообщение ChangeCipherSpec.</span><span class="sxs-lookup"><span data-stu-id="1ca36-156">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="1ca36-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C): входящий сертификат TLS невозможно использовать для идентификации удаленного сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-157">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote DTLS server.</span></span>
- <span data-ttu-id="1ca36-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D): шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="1ca36-158">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="1ca36-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-159">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure DTLS stack.</span></span>
- <span data-ttu-id="1ca36-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F): в заголовке полученного сообщения DTLS указана неизвестная версия DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-160">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received DTLS message had an unknown DTLS version in its header.</span></span>
- <span data-ttu-id="1ca36-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110): в заголовке полученного сообщения DTLS указана неподдерживаемая версия DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-161">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received DTLS message had a known but unsupported DTLS version in its header.</span></span>
- <span data-ttu-id="1ca36-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить внутренний пакет TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-162">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="1ca36-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112): удаленный узел предоставил недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="1ca36-163">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="1ca36-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114): удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-164">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="1ca36-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B): запись в таблице комплектов шифров содержала указатель на функцию со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="1ca36-165">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="1ca36-166">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс, сокет или адрес.</span><span class="sxs-lookup"><span data-stu-id="1ca36-166">**NX_PTR_ERROR** (0x07) Invalid session, socket, or address pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-167">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-167">Allowed From</span></span>

<span data-ttu-id="1ca36-168">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-169">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-169">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-170">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-170">See Also</span></span>

- <span data-ttu-id="1ca36-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-171">nx_secure_dtls_session_receive, nx_secure_dtls_session_send,</span></span>
- <span data-ttu-id="1ca36-172">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-172">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_packet_allocate"></a><span data-ttu-id="1ca36-173">nx_secure_dtls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="1ca36-173">nx_secure_dtls_packet_allocate</span></span>

<span data-ttu-id="1ca36-174">Выделение пакета для сеанса NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-174">Allocate a packet for a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-175">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-175">Prototype</span></span>

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="1ca36-176">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-176">Description</span></span>

<span data-ttu-id="1ca36-177">Эта служба выделяет пакет NX_PACKET для указанного активного сеанса DTLS из заданного пула NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="1ca36-177">This service allocates an NX_PACKET for the specified active DTLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="1ca36-178">Приложение должно вызывать эту службу для выделения пакетов данных, отправляемых через подключение DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-178">This service should be called by the application to allocate data packets to be sent over a DTLS connection.</span></span> <span data-ttu-id="1ca36-179">Перед вызовом данной службы необходимо инициализировать сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-179">The DTLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="1ca36-180">Выделенный пакет инициализируется таким образом, чтобы после заполнения данных пакета могли быть добавлены данные заголовка и примечания DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-180">The allocated packet is properly initialized so that DTLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="1ca36-181">В противном случае поведение идентично службе *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-181">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-182">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-182">Parameters</span></span>

- <span data-ttu-id="1ca36-183">**session_ptr**: указатель на экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-183">**session_ptr** Pointer to a DTLS Session instance.</span></span>
- <span data-ttu-id="1ca36-184">**pool_ptr**: указатель на пул NX_PACKET_POOL, из которого выделяется пакет.</span><span class="sxs-lookup"><span data-stu-id="1ca36-184">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="1ca36-185">**packet_ptr**: указатель вывода на выделенный пакет.</span><span class="sxs-lookup"><span data-stu-id="1ca36-185">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="1ca36-186">**wait_option**: параметр приостановки выделения пакетов.</span><span class="sxs-lookup"><span data-stu-id="1ca36-186">**wait_option** Suspension option for packet allocation.</span></span>


### <a name="return-values"></a><span data-ttu-id="1ca36-187">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-187">Return Values</span></span>

- <span data-ttu-id="1ca36-188">**NX_SUCCESS** (0x00): пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="1ca36-188">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="1ca36-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить базовый пакет.</span><span class="sxs-lookup"><span data-stu-id="1ca36-189">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="1ca36-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101): указанный сеанс DTLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="1ca36-190">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied DTLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-191">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-191">Allowed From</span></span>

<span data-ttu-id="1ca36-192">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-192">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-193">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-193">Example</span></span>

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a><span data-ttu-id="1ca36-194">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-194">See Also</span></span>

- <span data-ttu-id="1ca36-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-195">nx_secure_x509_certificate_initialize, nx_secure_dtls_session_create,</span></span>
- <span data-ttu-id="1ca36-196">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-196">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="1ca36-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-197">nx_secure_dtls_session_send, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-198">nx_secure_dtls_session_end, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_psk_add"></a><span data-ttu-id="1ca36-199">nx_secure_dtls_psk_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-199">nx_secure_dtls_psk_add</span></span>

<span data-ttu-id="1ca36-200">Добавление общего ключа в сеанс NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-200">Add a Pre-Shared Key to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-201">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-201">Prototype</span></span>

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="1ca36-202">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-202">Description</span></span>

<span data-ttu-id="1ca36-203">Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сеансом DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-203">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Session control block.</span></span> <span data-ttu-id="1ca36-204">Если включены и используются комплекты шифров PSK, то вместо цифрового сертификата используется PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-204">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-205">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-205">Parameters</span></span>

- <span data-ttu-id="1ca36-206">**session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-206">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="1ca36-207">**pre_shared_key**: фактическое значение PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-207">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="1ca36-208">**psk_length**: длина значения PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-208">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="1ca36-209">**psk_identity**: строка, используемая для идентификации этого значения PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-209">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="1ca36-210">**identity_length**: длина удостоверения PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-210">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="1ca36-211">**hint**: строка, используемая для выбора группы PSK на сервере TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-211">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="1ca36-212">**hint_length**: длина строки указания.</span><span class="sxs-lookup"><span data-stu-id="1ca36-212">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-213">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-213">Return Values</span></span>

- <span data-ttu-id="1ca36-214">**NX_SUCCESS** (0X00): PSK успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-214">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="1ca36-215">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-215">**NX_PTR_ERROR** (0x07) Invalid DTLS session pointer.</span></span>
- <span data-ttu-id="1ca36-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125): невозможно добавить еще один PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-216">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-217">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-217">Allowed From</span></span>

<span data-ttu-id="1ca36-218">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-218">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-219">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-219">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a><span data-ttu-id="1ca36-220">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-220">See Also</span></span>

- <span data-ttu-id="1ca36-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-221">nx_secure_dtls_server_psk_add, nx_secure_dtls_client_session_create</span></span>

## <a name="nx_secure_dtls_server_create"></a><span data-ttu-id="1ca36-222">nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-222">nx_secure_dtls_server_create</span></span>

<span data-ttu-id="1ca36-223">Создание сервера NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-223">Create a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-224">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-224">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a><span data-ttu-id="1ca36-225">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-225">Description</span></span>

<span data-ttu-id="1ca36-226">Эта служба создает экземпляр сервера DTLS для обработки входящих запросов DTLS на определенном UDP-порте.</span><span class="sxs-lookup"><span data-stu-id="1ca36-226">This service creates an instance of a DTLS server to handle incoming DTLS requests on a particular UDP port.</span></span> <span data-ttu-id="1ca36-227">Так как протокол UDP не использует состояния, запросы DTLS от нескольких клиентов могут поступить на один порт, когда активны другие сеансы DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-227">Due to the fact that UDP is stateless, DTLS requests from multiple clients can come in on a single port while other DTLS sessions are active.</span></span> <span data-ttu-id="1ca36-228">Следовательно, необходим сервер для поддержания активных сеансов и правильного перенаправления входящих сообщений в соответствующий обработчик.</span><span class="sxs-lookup"><span data-stu-id="1ca36-228">Thus, the server is needed to maintain active sessions and properly route incoming messages to the proper handler.</span></span>

<span data-ttu-id="1ca36-229">Параметр ip_ptr указывает на экземпляр NX_IP, который будет использоваться для внутреннего сокета UDP, связанного с сервером DTLS (и хранящегося в блоке управления NX_SECURE_DTLS_SERVER).</span><span class="sxs-lookup"><span data-stu-id="1ca36-229">The ip_ptr parameter points to an NX_IP instance to be used for the internal UDP socket associated with the DTLS Server (and stored in the NX_SECURE_DTLS_SERVER control block).</span></span> <span data-ttu-id="1ca36-230">Экземпляр IP и порт используются для определения интерфейса UDP, в котором создается экземпляр сервера службой nx_secure_dtls_server_start.</span><span class="sxs-lookup"><span data-stu-id="1ca36-230">The IP instance and port are used to define the UDP interface upon which the server is instantiated with the nx_secure_dtls_server_start service.</span></span>

<span data-ttu-id="1ca36-231">Параметр буфера сеанса используется для хранения блоков управления всех возможных одновременных сеансов DTLS для сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-231">The session buffer parameter is used to hold the control blocks for all the possible simultaneous DTLS sessions for the DTLS server.</span></span> <span data-ttu-id="1ca36-232">Выделяемый размер должен быть кратен размеру структуры блока управления NX_SECURE_DTLS_SESSION.</span><span class="sxs-lookup"><span data-stu-id="1ca36-232">It should be allocated with a size that is an even multiple of the size of the NX_SECURE_DTLS_SESSION control block structure.</span></span>

<span data-ttu-id="1ca36-233">Чтобы вычислить необходимый размер метаданных, можно использовать API nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="1ca36-233">To calculate the necessary metadata size, the API nx_secure_tls_metadata_size_calculate may be used.</span></span>

<span data-ttu-id="1ca36-234">Параметр packet_reassembly_buffer используется протоколом DTLS для преобразования датаграмм UDP в полную запись DTLS, которая используется для расшифровки и должна быть достаточно большой, чтобы вместить самую большую запись DTLS (16 КБ — это максимальный размер записи DTLS, но многие приложения не отправляют данные такого объема в одной записи).</span><span class="sxs-lookup"><span data-stu-id="1ca36-234">The packet_reassembly_buffer parameter is used by DTLS to reassemble UDP datagrams into a complete DTLS record for the purposes of decryption and should be large enough to accommodate the largest expected DTLS record (16KB is the DTLS maximum record size but many applications don’t send that much data in a single record).</span></span>

<span data-ttu-id="1ca36-235">Процедура обратного вызова connect_notify вызывается всякий раз, когда новый клиент DTLS подключается к серверу.</span><span class="sxs-lookup"><span data-stu-id="1ca36-235">The connect_notify callback routine is invoked whenever a new DTLS client connects to the server.</span></span> <span data-ttu-id="1ca36-236">Приложение запускает сеанс DTLS с помощью службы *nx_secure_dtls_server_session_start*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-236">It is up to the application to then start the DTLS session using the service *nx_secure_dtls_server_session_start*.</span></span> <span data-ttu-id="1ca36-237">Хотя сеанс может быть запущен в самом обратном вызове, рекомендуется использовать обратный вызов только для уведомления о потоке приложения (или выделенном потоке DTLS, созданном приложением) для подключения, так как обратный вызов выполняется потоком IP, который используется для обработки всех сетевых операций нижнего уровня (например, UDP).</span><span class="sxs-lookup"><span data-stu-id="1ca36-237">While the session may be started in the callback itself, it is recommended that the callback only be used to notify the application thread (or dedicated DTLS thread created by the application) of the connection as the callback is invoked by the IP thread which is used to process all lower-level network processing (e.g. UDP).</span></span> <span data-ttu-id="1ca36-238">Это может быть не сложнее, чем просто сохранить параметр сеанса DTLS (предоставленный в качестве параметра обратного вызова) и вызвать nx_secure_dtls_server_session_start в другом потоке.</span><span class="sxs-lookup"><span data-stu-id="1ca36-238">This can be as simple as saving the DTLS session parameter (provided as a parameter to the callback) and invoking nx_secure_dtls_server_session_start in the other thread.</span></span> <span data-ttu-id="1ca36-239">Обратный вызов connect_notify обычно должен возвращать NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-239">The connect_notify callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="1ca36-240">Процедура обратного вызова receive_notify вызывается всякий раз, когда получена запись DTLS, которая соответствует уже установленному сеансу DTLS (IP-адрес и порт удаленного узла используются для идентификации существующего сеанса).</span><span class="sxs-lookup"><span data-stu-id="1ca36-240">The receive_notify callback routine is invoked whenever a DTLS record is received that matches an existing established DTLS session (the remote host IP address and port are used to identify an existing session).</span></span> <span data-ttu-id="1ca36-241">Так представляются "данные приложения", которые шифруются и отправляются по протоколу DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-241">This represents the “application data” that is encrypted and sent over DTLS.</span></span> <span data-ttu-id="1ca36-242">Приложение должно вызвать службу *nx_secure_dtls_session_receive* в предоставленном сеансе DTLS, чтобы извлечь полученные данные.</span><span class="sxs-lookup"><span data-stu-id="1ca36-242">The application must call the service *nx_secure_dtls_session_receive* on the provided DTLS session to retrieve the received data.</span></span> <span data-ttu-id="1ca36-243">Как и в случае с обратным вызовом connect_receive, рекомендуется передавать сеанс другому потоку для обработки сообщений, так как обратный вызов выполняется из потока IP.</span><span class="sxs-lookup"><span data-stu-id="1ca36-243">As with the connect_receive callback, it is recommended that the session be passed to another thread to handle the message processing as the callback is invoked from the IP thread.</span></span> <span data-ttu-id="1ca36-244">Обратный вызов receive_notify обычно должен возвращать NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-244">The receive_notify callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-245">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-245">Parameters</span></span>

- <span data-ttu-id="1ca36-246">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-246">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-247">**ip_ptr**: указатель на инициализированный блок управления NX_IP, используемый в качестве сетевого интерфейса сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-247">**ip_ptr** Pointer to an initialized NX_IP control block to use as the network interface for the DTLS server.</span></span>
- <span data-ttu-id="1ca36-248">**port**: локальный UDP-порт, к которому привязан сокет UDP сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-248">**port** The local UDP port to which the DTLS server UDP socket is bound.</span></span>
- <span data-ttu-id="1ca36-249">**timeout**: значение времени ожидания сетевых операций.</span><span class="sxs-lookup"><span data-stu-id="1ca36-249">**timeout** Timeout value to use for network operations.</span></span>
- <span data-ttu-id="1ca36-250">**session_buffer**: буферное пространство для хранения блоков управления всех экземпляров NX_SECURE_DTLS_SESSION, назначенных этому экземпляру сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-250">**session_buffer** Buffer space to contain control blocks for all instances of NX_SECURE_DTLS_SESSION assigned to this DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-251">**session_buffer_size**: размер буфера сеанса.</span><span class="sxs-lookup"><span data-stu-id="1ca36-251">**session_buffer_size** Size of the session buffer.</span></span> <span data-ttu-id="1ca36-252">Определяет количество сеансов DTLS, назначенных серверу DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-252">This determines the number of DTLS sessions assigned to the DTLS Server.</span></span>
- <span data-ttu-id="1ca36-253">**crypto_table**: указатель на структуру таблицы шифрования TLS или DTLS, используемую для всех криптографических операций.</span><span class="sxs-lookup"><span data-stu-id="1ca36-253">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="1ca36-254">**crypto_metadata_buffer**: буферное пространство для вычислений криптографических операций и хранения сведений о состоянии.</span><span class="sxs-lookup"><span data-stu-id="1ca36-254">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="1ca36-255">**crypto_metadata_size**: размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="1ca36-255">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="1ca36-256">**packet_reassembly_buffer**: буфер, используемый протоколом DTLS для преобразования данных UDP в записи DTLS для расшифровки.</span><span class="sxs-lookup"><span data-stu-id="1ca36-256">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="1ca36-257">**packet_reassembly_buffer_size**: размер буфера преобразования данных.</span><span class="sxs-lookup"><span data-stu-id="1ca36-257">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="1ca36-258">Обычно размер этого буфера должен быть больше 16 КБ, но он может быть меньше, что зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="1ca36-258">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="1ca36-259">**connect_notify**: процедура обратного вызова, вызываемая всякий раз, когда удаленный клиент DTLS пытается подключиться к этому серверу DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-259">**connect_notify** Callback routine invoked whenever a remote DTLS Client attempts to connect to this DTLS server.</span></span>
- <span data-ttu-id="1ca36-260">**receive_notify**: обратный вызов, выполняемый при получении данных приложения через имеющийся сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-260">**receive_notify** Callback invoked whenever application data is received over an existing DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-261">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-261">Return Values</span></span>

- <span data-ttu-id="1ca36-262">**NX_SUCCESS** (0X00): сервер DTLS успешно создан.</span><span class="sxs-lookup"><span data-stu-id="1ca36-262">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="1ca36-263">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-263">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-264">**NX_INVALID_PARAMETERS** (0x4D): недостаточно пространства буфера для сеансов, повторной сборки пакетов или шифрования.</span><span class="sxs-lookup"><span data-stu-id="1ca36-264">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for sessions, packet reassembly, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-265">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-265">Allowed From</span></span>

<span data-ttu-id="1ca36-266">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-266">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-267">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-267">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-268">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-268">See Also</span></span>

- <span data-ttu-id="1ca36-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-269">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="1ca36-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-270">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-271">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-271">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-272">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-272">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-273">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-273">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_delete"></a><span data-ttu-id="1ca36-274">nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-274">nx_secure_dtls_server_delete</span></span>

<span data-ttu-id="1ca36-275">Освобождение ресурсов, используемых сервером NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-275">Free up resources used by a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-276">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-276">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="1ca36-277">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-277">Description</span></span>

<span data-ttu-id="1ca36-278">Эта служба освобождает ресурсы, выделенные экземпляру сервера DTLS, включая внутренний сокет UDP, используемый сервером.</span><span class="sxs-lookup"><span data-stu-id="1ca36-278">This service frees up the resources allocated to a DTLS Server instance, including the internal UDP socket used by the server.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-279">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-279">Parameters</span></span>

- <span data-ttu-id="1ca36-280">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-280">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-281">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-281">Return Values</span></span>

- <span data-ttu-id="1ca36-282">**NX_SUCCESS** (0X00): сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="1ca36-282">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="1ca36-283">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-283">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-284">**NX_STILL_BOUND** (0x42): сокет UDP все еще привязан.</span><span class="sxs-lookup"><span data-stu-id="1ca36-284">**NX_STILL_BOUND** (0x42) UDP socket is still bound.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-285">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-285">Allowed From</span></span>

<span data-ttu-id="1ca36-286">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-287">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-287">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-288">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-288">See Also</span></span>

- <span data-ttu-id="1ca36-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span><span class="sxs-lookup"><span data-stu-id="1ca36-289">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-290">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-291">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-291">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_local_certificate_add"></a><span data-ttu-id="1ca36-292">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-292">nx_secure_dtls_server_local_certificate_add</span></span>

<span data-ttu-id="1ca36-293">Добавление локального удостоверяющего сертификата сервера на сервер NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-293">Add a local server identity certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-294">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-294">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-295">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-295">Description</span></span>

<span data-ttu-id="1ca36-296">Эта служба добавляет локальный сертификат удостоверения сервера в экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-296">This service adds a local server identity certificate to a DTLS Server instance.</span></span> <span data-ttu-id="1ca36-297">Для подключения клиентов к серверу DTLS требуется по крайней мере один сертификат удостоверения, если не используется альтернативный механизм проверки подлинности (например, общие ключи).</span><span class="sxs-lookup"><span data-stu-id="1ca36-297">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="1ca36-298">Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="1ca36-298">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="1ca36-299">Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-299">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="1ca36-300">Дополнительные сведения о сертификатах сервера X.509 см. в руководстве пользователя NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-300">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-301">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-301">Parameters</span></span>

- <span data-ttu-id="1ca36-302">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-302">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-303">**certificate**: указатель на инициализированную ранее структуру сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="1ca36-303">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="1ca36-304">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-304">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-305">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-305">Return Values</span></span>

- <span data-ttu-id="1ca36-306">**NX_SUCCESS** (0X00): сертификат успешно добавлен на сервер DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-306">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="1ca36-307">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-307">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-308">**NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-308">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-309">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-309">Allowed From</span></span>

<span data-ttu-id="1ca36-310">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-311">Например, .</span><span class="sxs-lookup"><span data-stu-id="1ca36-311">Example</span></span>

<span data-ttu-id="1ca36-312">\* Более полный пример доступен в справочнике по службе *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-312">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-313">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-313">See Also</span></span>

- <span data-ttu-id="1ca36-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-314">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-315">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-316">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-316">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-317">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-317">nx_secure_dtls_server_local_certificate_remove,</span></span>
- <span data-ttu-id="1ca36-318">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-318">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_local_certificate_remove"></a><span data-ttu-id="1ca36-319">nx_secure_dtls_server_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-319">nx_secure_dtls_server_local_certificate_remove</span></span>

<span data-ttu-id="1ca36-320">Удаление локального удостоверяющего сертификата сервера с сервера NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="1ca36-320">Remove a local server identity certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-321">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-321">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-322">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-322">Description</span></span>

<span data-ttu-id="1ca36-323">Эта служба удаляет локальный сертификат удостоверения сервера из экземпляра сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-323">This service removes a local server identity certificate from a DTLS Server instance.</span></span> <span data-ttu-id="1ca36-324">Для подключения клиентов к серверу DTLS требуется по крайней мере один сертификат удостоверения, если не используется альтернативный механизм проверки подлинности (например, общие ключи).</span><span class="sxs-lookup"><span data-stu-id="1ca36-324">At least one identity certificate is required for clients to connect to a DTLS server unless an alternate authentication mechanism (e.g. Pre-Shared Keys) is used.</span></span>

<span data-ttu-id="1ca36-325">Удаляемый сертификат можно идентифицировать по его общему имени X.509 или числовому значению cert_id, которое было назначено в вызове *nx_secure_dtls_server_local_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-325">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_local_certificate_add*.</span></span> <span data-ttu-id="1ca36-326">Значение cert_id используется только для идентификации сертификата и управляется приложением.</span><span class="sxs-lookup"><span data-stu-id="1ca36-326">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="1ca36-327">Если вместо числового идентификатора сертификата используется общее имя, параметру cert_id должно быть присвоено значение 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-327">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="1ca36-328">Удаление сертификата во время обработки подтверждения DTLS приведет к непредвиденному поведению.</span><span class="sxs-lookup"><span data-stu-id="1ca36-328">Removing a certificate while a DTLS handshake is being processed will result in unexpected behavior.</span></span> <span data-ttu-id="1ca36-329">Перед удалением сертификатов необходимо вызвать службу *nx_secure_dtls_server_stop*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-329">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-330">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-330">Parameters</span></span>

- <span data-ttu-id="1ca36-331">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-331">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-332">**common_name**: общее имя X.509 сертификата, который необходимо удалить.</span><span class="sxs-lookup"><span data-stu-id="1ca36-332">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="1ca36-333">Если используется этот параметр, присвойте параметру cert_id значение 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-333">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="1ca36-334">**common_name_length**: длина common_name в байтах.</span><span class="sxs-lookup"><span data-stu-id="1ca36-334">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="1ca36-335">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-335">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="1ca36-336">Если используется этот параметр, присвойте значение NX_NULL параметру common_name.</span><span class="sxs-lookup"><span data-stu-id="1ca36-336">If this is used, pass NX_NULL for the common_name parameter.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-337">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-337">Return Values</span></span>

- <span data-ttu-id="1ca36-338">**NX_SUCCESS** (0X00): сертификат успешно удален с сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-338">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="1ca36-339">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-339">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден на данном сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-340">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-341">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-341">Allowed From</span></span>

<span data-ttu-id="1ca36-342">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-343">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-343">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-344">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-344">See Also</span></span>

- <span data-ttu-id="1ca36-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-345">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-346">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-346">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-347">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-347">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-348">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-348">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="1ca36-349">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-349">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_notify_set"></a><span data-ttu-id="1ca36-350">nx_secure_dtls_server_notify_set</span><span class="sxs-lookup"><span data-stu-id="1ca36-350">nx_secure_dtls_server_notify_set</span></span>

<span data-ttu-id="1ca36-351">Назначение необязательных процедур обратного вызова для уведомления серверу NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-351">Assign optional notification callback routines to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-352">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-352">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a><span data-ttu-id="1ca36-353">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-353">Description</span></span>

<span data-ttu-id="1ca36-354">Эту службу можно использовать для добавления на сервер DTLS необязательных процедур обратного вызова для уведомления.</span><span class="sxs-lookup"><span data-stu-id="1ca36-354">This service can be used to add optional notification callback routines to a DTLS server.</span></span> <span data-ttu-id="1ca36-355">Если требуется только один ответный вызов, можно передать параметр обратного вызова NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="1ca36-355">Either callback parameter may be passed as NX_NULL if only one callback is desired.</span></span>

<span data-ttu-id="1ca36-356">Когда удаленный клиент завершает сеанс DTLS, выполняется обратный вызов disconnect_notify.</span><span class="sxs-lookup"><span data-stu-id="1ca36-356">The disconnect_notify callback is invoked when a remote client ends a DTLS session.</span></span> <span data-ttu-id="1ca36-357">Параметр dtls_session указывает экземпляр сеанса, который был закрыт.</span><span class="sxs-lookup"><span data-stu-id="1ca36-357">The dtls_session parameter is the session instance that was closed.</span></span> <span data-ttu-id="1ca36-358">Обратный вызов обычно должен возвращать значение NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-358">The callback should generally return NX_SUCCESS.</span></span>

<span data-ttu-id="1ca36-359">Обратный вызов error_notify выполняется при возникновении ошибки или истечении времени ожидания DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-359">The error_notify callback is invoked whenever a DTLS error or timeout occurs.</span></span> <span data-ttu-id="1ca36-360">Параметр dtls_session указывает экземпляр сеанса, в котором произошла ошибка, а error_code — числовой код состояния ошибки, вызвавшей проблему (см. приложение А).</span><span class="sxs-lookup"><span data-stu-id="1ca36-360">The dtls_session parameter is the session instance for which the error occurred, and error_code is the numeric status code for the error that caused the issue (see Appendix A)</span></span>

<span data-ttu-id="1ca36-361">Ознакомьтесь со списком возвращаемых значений и кодов ошибок NetX Secure, чтобы узнать больше о возможных кодах ошибок.</span><span class="sxs-lookup"><span data-stu-id="1ca36-361">NetX Secure Return/Error Codes for a list of error codes that may be returned).</span></span> <span data-ttu-id="1ca36-362">Обратный вызов обычно должен возвращать значение NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-362">The callback should generally return NX_SUCCESS.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-363">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-363">Parameters</span></span>

- <span data-ttu-id="1ca36-364">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-364">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-365">**disconnect_notify**: процедуры обратного вызова, вызываемые, когда удаленный клиентский узел закрывает сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-365">**disconnect_notify** Callback routine invoked whenever a remote client host closes a DTLS session.</span></span>
- <span data-ttu-id="1ca36-366">**error_notify**: процедуры обратного вызова, вызываемые при возникновении ошибки или истечении времени ожидания DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-366">**error_notify** Callback routine invoked whenever DTLS encounters an error or timeout.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-367">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-367">Return Values</span></span>

- <span data-ttu-id="1ca36-368">**NX_SUCCESS** (0X00): процедуры обратного вызова успешно назначены.</span><span class="sxs-lookup"><span data-stu-id="1ca36-368">**NX_SUCCESS** (0x00) Successful assignment of callback routines.</span></span>
- <span data-ttu-id="1ca36-369">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-369">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-370">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-370">Allowed From</span></span>

<span data-ttu-id="1ca36-371">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-371">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-372">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-372">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-373">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-373">See Also</span></span>

- <span data-ttu-id="1ca36-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-374">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-375">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-375">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-376">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-376">nx_secure_dtls_server_session_stop</span></span>

## <a name="nx_secure_dtls_server_psk_add"></a><span data-ttu-id="1ca36-377">nx_secure_dtls_server_psk_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-377">nx_secure_dtls_server_psk_add</span></span>

<span data-ttu-id="1ca36-378">Добавление общего ключа на сервер NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-378">Add a Pre-Shared Key to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-379">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-379">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a><span data-ttu-id="1ca36-380">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-380">Description</span></span>

<span data-ttu-id="1ca36-381">Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сервером DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-381">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a DTLS Server control block.</span></span> <span data-ttu-id="1ca36-382">Если включены и используются комплекты шифров PSK, то вместо цифрового сертификата используется PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-382">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="1ca36-383">Добавленный PSK реплицируется во всех сеансах DTLS, назначенных серверу DTLS (через буфер сеанса, указанный в вызове nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="1ca36-383">The PSK that is added is replicated across all the DTLS sessions assigned to the DTLS Server (via the session buffer given in the call to nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-384">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-384">Parameters</span></span>

- <span data-ttu-id="1ca36-385">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-385">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-386">**pre_shared_key**: фактическое значение PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-386">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="1ca36-387">**psk_length**: длина значения PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-387">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="1ca36-388">**psk_identity**: строка, используемая для идентификации этого значения PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-388">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="1ca36-389">**identity_length**: длина удостоверения PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-389">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="1ca36-390">**hint**: строка, используемая для выбора группы PSK на сервере TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-390">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="1ca36-391">**hint_length**: длина строки указания.</span><span class="sxs-lookup"><span data-stu-id="1ca36-391">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-392">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-392">Return Values</span></span>

- <span data-ttu-id="1ca36-393">**NX_SUCCESS** (0X00): PSK успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-393">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="1ca36-394">**NX_PTR_ERROR** (0x07): недопустимый указатель на сервер DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-394">**NX_PTR_ERROR** (0x07) Invalid DTLS server pointer.</span></span>
- <span data-ttu-id="1ca36-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125): невозможно добавить еще один PSK.</span><span class="sxs-lookup"><span data-stu-id="1ca36-395">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-396">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-396">Allowed From</span></span>

<span data-ttu-id="1ca36-397">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-398">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-398">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a><span data-ttu-id="1ca36-399">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-399">See Also</span></span>

- <span data-ttu-id="1ca36-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-400">nx_secure_dtls_psk_add, nx_secure_dtls_server_create</span></span>

## <a name="nx_secure_dtls_server_session_send"></a><span data-ttu-id="1ca36-401">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-401">nx_secure_dtls_server_session_send</span></span>

<span data-ttu-id="1ca36-402">Отправка данных через сеанс DTLS, установленный с помощью сервера NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-402">Send data over a DTLS session established with a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-403">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-403">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="1ca36-404">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-404">Description</span></span>

<span data-ttu-id="1ca36-405">Эта служба отправляет пакет данных через установленный сеанс сервера DTLS на удаленный узел клиента DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-405">This service sends a packet of data over an established DTLS Server session to a remote DTLS Client host.</span></span> <span data-ttu-id="1ca36-406">Используемый сеанс передается в процедуре обратного вызова receive_notify, предоставленной службе nx_secure_dtls_session_create.</span><span class="sxs-lookup"><span data-stu-id="1ca36-406">The session used is obtained in the receive_notify callback routine provided to nx_secure_dtls_session_create.</span></span>

<span data-ttu-id="1ca36-407">Данные в пакете, который должен быть выделен с помощью *nx_secure_dtls_packet_allocate*, шифруются с помощью криптографических параметров и процедур сеанса DTLS, а затем отправляются на удаленный узел через внутренний UDP-порт сервера DTLS на IP-адрес и порт подключенного клиента (которые хранятся в сеансе DTLS).</span><span class="sxs-lookup"><span data-stu-id="1ca36-407">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Server internal UDP port to the attached client’s IP address and port (stored in the DTLS Session).</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-408">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-408">Parameters</span></span>

- <span data-ttu-id="1ca36-409">**session_ptr**: указатель на экземпляр сеанса DTLS, полученный из процедуры обратного вызова receive_notify, предоставленной приложением.</span><span class="sxs-lookup"><span data-stu-id="1ca36-409">**session_ptr** Pointer to a DTLS session instance obtained from the receive_notify callback routine provided by the application.</span></span>
- <span data-ttu-id="1ca36-410">**packet_ptr**: указатель на экземпляр NX_PACKET, выделенный ранее и заполненный данными приложения.</span><span class="sxs-lookup"><span data-stu-id="1ca36-410">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-411">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-411">Return Values</span></span>

- <span data-ttu-id="1ca36-412">**NX_SUCCESS** (0X00): сервер DTLS успешно создан.</span><span class="sxs-lookup"><span data-stu-id="1ca36-412">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="1ca36-413">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-413">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): произошла ошибка в базовой операции отправки по протоколу UDP.</span><span class="sxs-lookup"><span data-stu-id="1ca36-414">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-415">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-415">Allowed From</span></span>

<span data-ttu-id="1ca36-416">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-417">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-417">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-418">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-418">See Also</span></span>

- <span data-ttu-id="1ca36-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-419">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="1ca36-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-420">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_create,</span></span>
- <span data-ttu-id="1ca36-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-421">nx_secure_dtls_server_session_start, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-422">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-422">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_session_start"></a><span data-ttu-id="1ca36-423">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-423">nx_secure_dtls_server_session_start</span></span>

<span data-ttu-id="1ca36-424">Запуск сеанса DTLS с сервера NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-424">Start a DTLS Session from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-425">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-425">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="1ca36-426">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-426">Description</span></span>

<span data-ttu-id="1ca36-427">Эта служба запускает сеанс сервера DTLS, выполняя подтверждение DTLS на стороне сервера, когда удаленный клиент DTLS подключается к серверу и запрашивает подключение DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-427">This service starts a DTLS Server session by performing the server-side DTLS handshake when a remote DTLS Client has connected to the server and requested a DTLS connection.</span></span>

<span data-ttu-id="1ca36-428">Сеанс DTLS извлекается из процедуры обратного вызова connect_notify, переданной службе nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="1ca36-428">The DTLS Session is obtained in the connect_notify callback routine provided to nx_secure_dtls_server_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-429">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-429">Parameters</span></span>

- <span data-ttu-id="1ca36-430">**session_ptr**: указатель на экземпляр сеанса DTLS, полученный из обратного вызова connect_notify сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-430">**session_ptr** Pointer to a DTLS Session instance obtained from a DTLS Server connect_notify callback.</span></span>
- <span data-ttu-id="1ca36-431">**wait_option**: значение ожидания ThreadX, используемое для сетевых операций.</span><span class="sxs-lookup"><span data-stu-id="1ca36-431">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-432">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-432">Return Values</span></span>

- <span data-ttu-id="1ca36-433">**NX_SUCCESS** (0X00): сервер DTLS успешно создан.</span><span class="sxs-lookup"><span data-stu-id="1ca36-433">**NX_SUCCESS** (0x00) Successful creation of DTLS server.</span></span>
- <span data-ttu-id="1ca36-434">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-434">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить пакет для подтверждения DTLS (пул пакетов пуст).</span><span class="sxs-lookup"><span data-stu-id="1ca36-435">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a DTLS handshake packet (packet pool empty).</span></span>
- <span data-ttu-id="1ca36-436">**NX_SECURE_TLS_INVALID_PACKET** (0X104): получены данные, которые не являются допустимой записью DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-436">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="1ca36-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108): не удалось правильно хэшировать запись DTLS (ошибка шифрования).</span><span class="sxs-lookup"><span data-stu-id="1ca36-437">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="1ca36-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A): ошибка проверки заполнения шифрования.</span><span class="sxs-lookup"><span data-stu-id="1ca36-438">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="1ca36-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114): во время подтверждения DTLS от удаленного узла получено оповещение.</span><span class="sxs-lookup"><span data-stu-id="1ca36-439">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host during the DTLS handshake.</span></span>
- <span data-ttu-id="1ca36-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102): во время подтверждения DTLS получено нераспознанное сообщение.</span><span class="sxs-lookup"><span data-stu-id="1ca36-440">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) Received an unrecognized message during the DTLS handshake.</span></span>
- <span data-ttu-id="1ca36-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A): получена запись DTLS с недопустимой длиной.</span><span class="sxs-lookup"><span data-stu-id="1ca36-441">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="1ca36-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): получено сообщение ClientHello, не содержащее поддерживаемых комплектов шифров DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-442">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) Received a ClientHello with no supported DTLS ciphersuites.</span></span>
- <span data-ttu-id="1ca36-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0X118): получено сообщение ClientHello с неизвестным методом сжатия.</span><span class="sxs-lookup"><span data-stu-id="1ca36-443">**NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) Recevied a ClientHello with a unknown compression method.</span></span>
- <span data-ttu-id="1ca36-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0X107): общая (неопределенная) ошибка подтверждения, обычно возникающая из-за проблем с обработкой расширения.</span><span class="sxs-lookup"><span data-stu-id="1ca36-444">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Generic (unspecified) handshake failure, usually due to problems with extension processing.</span></span>
- <span data-ttu-id="1ca36-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130): функция, которая еще не поддерживается, была вызвана во время подтверждения DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-445">**NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) A feature that is not yet supported was invoked during the DTLS handshake.</span></span>
- <span data-ttu-id="1ca36-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): обнаружен неизвестный комплект шифров (внутренняя ошибка шифрования).</span><span class="sxs-lookup"><span data-stu-id="1ca36-446">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicated internal cryptography error).</span></span>
- <span data-ttu-id="1ca36-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E): получена запись DTLS с несоответствующей версией DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-447">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>
- <span data-ttu-id="1ca36-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0X115): не удалось проверить хэш подтверждения DTLS (недопустимый сеанс).</span><span class="sxs-lookup"><span data-stu-id="1ca36-448">**NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) Failed to validate the DTLS handshake hash, session is invalid.</span></span>
- <span data-ttu-id="1ca36-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): сбой при внутренней операции отправки по протоколу UDP.</span><span class="sxs-lookup"><span data-stu-id="1ca36-449">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Internal UDP send failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-450">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-450">Allowed From</span></span>

<span data-ttu-id="1ca36-451">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-452">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-452">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-453">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-453">See Also</span></span>

- <span data-ttu-id="1ca36-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-454">nx_secure_dtls_server_start, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="1ca36-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-455">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-456">nx_secure_dtls_server_session_create, nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-457">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-457">nx_secure_dtls_server_local_certificate_add</span></span>

## <a name="nx_secure_dtls_server_start"></a><span data-ttu-id="1ca36-458">nx_secure_dtls_server_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-458">nx_secure_dtls_server_start</span></span>

<span data-ttu-id="1ca36-459">Запуск экземпляра сервера NetX Secure DTLS, ожидающего передачи данных через настроенный UDP-порт.</span><span class="sxs-lookup"><span data-stu-id="1ca36-459">Start a NetX Secure DTLS Server instance listening on the configured UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-460">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-460">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="1ca36-461">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-461">Description</span></span>

<span data-ttu-id="1ca36-462">Эта служба запускает сервер DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-462">This service starts a DTLS Server.</span></span> <span data-ttu-id="1ca36-463">После возвращения вызова сервер становится активным и начинает обрабатывать входящие запросы от клиентов DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-463">After the call returns, the server is active and will begin processing incoming requests from DTLS clients.</span></span> <span data-ttu-id="1ca36-464">Экземпляр сервера должен быть настроен с помощью службы *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-464">The server instance must have been configured with the service *nx_secure_dtls_server_create*.</span></span>

> [!NOTE]
> <span data-ttu-id="1ca36-465">Эта служба привязывает внутренний UDP-порт сервера DTLS к настроенному локальному порту, поэтому большинство возникающих проблем связано с обменом данными по протоколу UDP и конфигурацией сети.</span><span class="sxs-lookup"><span data-stu-id="1ca36-465">This service binds the internal DTLS Server UDP port to the configured local port so most issues encountered will have to do with UDP communications and network configuration.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-466">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-466">Parameters</span></span>

- <span data-ttu-id="1ca36-467">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-467">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-468">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-468">Return Values</span></span>

- <span data-ttu-id="1ca36-469">**NX_SUCCESS** (0X00): сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-469">**NX_SUCCESS** (0x00) Successful start of server.</span></span>
- <span data-ttu-id="1ca36-470">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-470">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-471">**NX_NOT_ENABLED** (0X14): протокол UDP не включен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-471">**NX_NOT_ENABLED** (0x14) UDP not enabled.</span></span>
- <span data-ttu-id="1ca36-472">**NX_NO_FREE_PORTS** (0X45): нет доступных UDP-портов.</span><span class="sxs-lookup"><span data-stu-id="1ca36-472">**NX_NO_FREE_PORTS** (0x45) No available UDP ports.</span></span>
- <span data-ttu-id="1ca36-473">**NX_INVALID_PORT** (0x46): недопустимый UDP-порт.</span><span class="sxs-lookup"><span data-stu-id="1ca36-473">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="1ca36-474">**NX_ALREADY_BOUND** (0X22): UDP-порт уже привязан.</span><span class="sxs-lookup"><span data-stu-id="1ca36-474">**NX_ALREADY_BOUND** (0x22) UDP port already bound.</span></span>
- <span data-ttu-id="1ca36-475">**NX_PORT_UNAVAILABLE** (0x23): UDP-порт недоступен для использования.</span><span class="sxs-lookup"><span data-stu-id="1ca36-475">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-476">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-476">Allowed From</span></span>

<span data-ttu-id="1ca36-477">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-478">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-478">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-479">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-479">See Also</span></span>

- <span data-ttu-id="1ca36-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-480">nx_secure_dtls_server_stop, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-481">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-482">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-482">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-483">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-483">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_stop"></a><span data-ttu-id="1ca36-484">nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-484">nx_secure_dtls_server_stop</span></span>

<span data-ttu-id="1ca36-485">Остановка активного экземпляра сервера NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-485">Stop an active NetX Secure DTLS Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-486">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-486">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="1ca36-487">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-487">Description</span></span>

<span data-ttu-id="1ca36-488">Эта служба завершает ожидание сервером DTLS передачи данных через UDP-порт и сбрасывает все связанные сеансы DTLS, прекращая все выполняемые операции обмена данными по протоколу DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-488">This service stops a DTLS Server from listening on the configure UDP port and resets all the associated DTLS sessions, halting any in-progress DTLS communications.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-489">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-489">Parameters</span></span>

- <span data-ttu-id="1ca36-490">**server_ptr**: указатель на активный экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-490">**server_ptr** Pointer to an active DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-491">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-491">Return Values</span></span>

- <span data-ttu-id="1ca36-492">**NX_SUCCESS** (0x00): сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-492">**NX_SUCCESS** (0x00) Successful stop of server.</span></span>
- <span data-ttu-id="1ca36-493">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-493">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-494">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-494">Allowed From</span></span>

<span data-ttu-id="1ca36-495">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-495">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-496">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-496">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-497">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-497">See Also</span></span>

- <span data-ttu-id="1ca36-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-498">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-499">nx_secure_dtls_server_delete, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-500">nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-500">nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-501">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-501">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a><span data-ttu-id="1ca36-502">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-502">nx_secure_dtls_server_trusted_certificate_add</span></span>

<span data-ttu-id="1ca36-503">Добавление сертификата доверенного ЦС на сервер NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-503">Add a trusted CA certificate to a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-504">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-504">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-505">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-505">Description</span></span>

<span data-ttu-id="1ca36-506">Эта служба добавляет сертификат доверенного или промежуточного ЦС в экземпляр сервера DTLS, который назначается всем внутренним сеансам сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-506">This service adds a trusted CA or intermediate CA certificate to a DTLS Server instance and assigned to all the internal DTLS server sessions.</span></span> <span data-ttu-id="1ca36-507">Это необходимо, только если включена проверка подлинности на основе сертификата клиента X.509 с помощью службы *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-507">This is only necessary if X.509 Client certificate authentication is enabled using *nx_secure_dtls_server_x509_client_verify_configure*.</span></span> <span data-ttu-id="1ca36-508">Добавленный сертификат будет использоваться для проверки входящих сертификатов клиента X.509.</span><span class="sxs-lookup"><span data-stu-id="1ca36-508">The added certificate will be used to verify incoming Client X.509 certificates.</span></span>

<span data-ttu-id="1ca36-509">Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="1ca36-509">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="1ca36-510">Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-510">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS server store.</span></span> <span data-ttu-id="1ca36-511">Дополнительные сведения о сертификатах сервера X.509 см. в руководстве пользователя NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-511">See the NetX Secure TLS User Guide for more information about X.509 server certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-512">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-512">Parameters</span></span>

- <span data-ttu-id="1ca36-513">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-513">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-514">**certificate**: указатель на инициализированную ранее структуру сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="1ca36-514">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="1ca36-515">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-515">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-516">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-516">Return Values</span></span>

- <span data-ttu-id="1ca36-517">**NX_SUCCESS** (0X00): сертификат успешно добавлен на сервер DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-517">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS server.</span></span>
- <span data-ttu-id="1ca36-518">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-518">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-519">**NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-519">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-520">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-520">Allowed From</span></span>

<span data-ttu-id="1ca36-521">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-522">Например, .</span><span class="sxs-lookup"><span data-stu-id="1ca36-522">Example</span></span>

<span data-ttu-id="1ca36-523">\* Более полный пример доступен в справочнике по службе *nx_secure_dtls_server_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-523">\*See reference for *nx_secure_dtls_server_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-524">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-524">See Also</span></span>

- <span data-ttu-id="1ca36-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-525">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-526">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-527">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-527">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-528">nx_secure_dtls_server_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-528">nx_secure_dtls_server_local_certificate_add,</span></span>
- <span data-ttu-id="1ca36-529">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-529">nx_secure_dtls_server_trusted_certificate_remove,</span></span>
- <span data-ttu-id="1ca36-530">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-530">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a><span data-ttu-id="1ca36-531">nx_secure_dtls_server_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-531">nx_secure_dtls_server_trusted_certificate_remove</span></span>

<span data-ttu-id="1ca36-532">Удаление сертификата доверенного ЦС с сервера NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-532">Remove a trusted CA certificate from a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-533">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-533">Prototype</span></span>

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-534">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-534">Description</span></span>

<span data-ttu-id="1ca36-535">Эта служба удаляет сертификат доверенного ЦС из экземпляра сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-535">This service removes a trusted CA certificate from a DTLS Server instance.</span></span> <span data-ttu-id="1ca36-536">Сертификаты доверенного ЦС необходимы только для сервера DTLS, для которого включена проверка на основе сертификата клиента X.509 путем вызова службы *nx_secure_dtls_server_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-536">Trusted CA certificates are only necessary for a DTLS Server for which X.509 Client certificate verification has been enabled by calling *nx_secure_dtls_server_x509_client_verify_configure*.</span></span>

<span data-ttu-id="1ca36-537">Удаляемый сертификат можно идентифицировать по его общему имени X.509 или числовому значению cert_id, которое было назначено в вызове *nx_secure_dtls_server_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-537">The certificate to be removed can be identified either by its X.509 Common Name or by the numeric cert_id that was assigned in the call to *nx_secure_dtls_server_trusted_certificate_add*.</span></span> <span data-ttu-id="1ca36-538">Значение cert_id используется только для идентификации сертификата и управляется приложением.</span><span class="sxs-lookup"><span data-stu-id="1ca36-538">The cert_id is only used to identify the certificate and is maintained by the application.</span></span> <span data-ttu-id="1ca36-539">Если вместо числового идентификатора сертификата используется общее имя, параметру cert_id должно быть присвоено значение 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-539">If the Common Name is used instead of the numeric certificate identifier, the cert_id parameter should be set to 0.</span></span>

> [!NOTE]
> <span data-ttu-id="1ca36-540">Удаление сертификата во время обработки подтверждения DTLS может привести к непредвиденному поведению.</span><span class="sxs-lookup"><span data-stu-id="1ca36-540">Removing a certificate while a DTLS handshake is being processed may result in unexpected behavior.</span></span> <span data-ttu-id="1ca36-541">Перед удалением сертификатов необходимо вызвать службу *nx_secure_dtls_server_stop*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-541">The service *nx_secure_dtls_server_stop* should be called before removing certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-542">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-542">Parameters</span></span>

- <span data-ttu-id="1ca36-543">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-543">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-544">**common_name**: общее имя X.509 сертификата, который необходимо удалить.</span><span class="sxs-lookup"><span data-stu-id="1ca36-544">**common_name** X.509 CommonName of the certificate to remove.</span></span> <span data-ttu-id="1ca36-545">Если используется этот параметр, присвойте параметру cert_id значение 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-545">If this is used, pass cert_id as zero.</span></span>
- <span data-ttu-id="1ca36-546">**common_name_length**: длина common_name в байтах.</span><span class="sxs-lookup"><span data-stu-id="1ca36-546">**common_name_length** Length of common_name string in bytes.</span></span>
- <span data-ttu-id="1ca36-547">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-547">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span> <span data-ttu-id="1ca36-548">Если используется этот параметр, присвойте значение NX_NULL параметру common_name.</span><span class="sxs-lookup"><span data-stu-id="1ca36-548">If this is used, pass NX_NULL for the common_name parameter.</span></span>


### <a name="return-values"></a><span data-ttu-id="1ca36-549">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-549">Return Values</span></span>

- <span data-ttu-id="1ca36-550">**NX_SUCCESS** (0X00): сертификат успешно удален с сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-550">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS server.</span></span>
- <span data-ttu-id="1ca36-551">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-551">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден на данном сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-552">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS server.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-553">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-553">Allowed From</span></span>

<span data-ttu-id="1ca36-554">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-555">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-555">Example</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-556">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-556">See Also</span></span>

- <span data-ttu-id="1ca36-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-557">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-558">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-558">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-559">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-559">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-560">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-560">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="1ca36-561">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-561">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a><span data-ttu-id="1ca36-562">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="1ca36-562">nx_secure_dtls_server_x509_client_verify_configure</span></span>

<span data-ttu-id="1ca36-563">Настройка сервера NetX Secure DTLS для запроса и проверки сертификатов клиентов.</span><span class="sxs-lookup"><span data-stu-id="1ca36-563">Configure a NetX Secure DTLS Server to request and verify client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-564">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-564">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a><span data-ttu-id="1ca36-565">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-565">Description</span></span>

<span data-ttu-id="1ca36-566">Эта служба настраивает сервер DTLS для запроса и проверки сертификатов клиента DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-566">This service configures a DTLS Server to request and verify DTLS Client certificates.</span></span> <span data-ttu-id="1ca36-567">Эта дополнительная функция используется, когда сертификаты X.509 предпочтительнее использовать для проверки подлинности клиентов, чем другие механизмы (например, общие ключи).</span><span class="sxs-lookup"><span data-stu-id="1ca36-567">This optional feature is used when X.509 certificates are desired for client authentication in place of other mechanisms (e.g. a Pre-Shared Key).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ca36-568">*Если сервер DTLS настроен для проверки сертификатов клиента с помощью этой службы, необходимо добавить по крайней мере один сертификат доверенного ЦС на сервер, вызвав службу nx_secure_dtls_server_trusted_certificate_add, иначе сервер будет отклонять все входящие клиентские подключения, так как не сможет проверить сертификаты клиента с помощью доверенного хранилища.*</span><span class="sxs-lookup"><span data-stu-id="1ca36-568">*When a DTLS Server is configured to verify client certificates using this service, at least one trusted CA certificate must be added to the server using nx_secure_dtls_server_trusted_certificate_add or the server will reject all incoming client connections because it will be unable to verify client certificates against the trusted store.*</span></span>

<span data-ttu-id="1ca36-569">После вызова этой службы экземпляр сервера DTLS (после запуска) будет запрашивать сертификаты клиента в ходе подтверждения DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-569">Upon calling this service, the DTLS Server instance will (once started) request client certificates as part of the DTLS handshake.</span></span> <span data-ttu-id="1ca36-570">Предполагая, что для клиента правильно настроен сертификат удостоверения (и связанная цепочка сертификатов, когда это применимо), серверу DTLS потребуется выделить память для обработки данных сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="1ca36-570">Assuming the client is properly configured with an identity certificate (and associated certificate chain when applicable), the DTLS Server requires memory to be allocated to process the client certificate data.</span></span> <span data-ttu-id="1ca36-571">Этот объем памяти передается в качестве параметра *certs_buffer*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-571">This memory is passed in as the *certs_buffer* parameter.</span></span>

<span data-ttu-id="1ca36-572">Величина certs_buffer должна соответствовать размеру самой большой цепочки сертификатов от клиента DTLS, *умноженному на количество сеансов сервера DTLS*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-572">The certs_buffer must be sized to accommodate the largest expected certificate chain from a DTLS client, *times the number of DTLS server sessions*.</span></span> <span data-ttu-id="1ca36-573">Этот буфер распределяется между доступными сеансами с помощью параметра *certs_per_session*, который задает максимальное ожидаемое число сертификатов в цепочке сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="1ca36-573">The buffer is divided amongst the available sessions using the *certs_per_session* parameter which represents the maximum expected number of certificates in a Client certificate chain.</span></span> <span data-ttu-id="1ca36-574">Буфер также должен предоставить пространство для структуры данных NX_SECURE_X509_CERT, которая используется для анализа данных сертификата.</span><span class="sxs-lookup"><span data-stu-id="1ca36-574">The buffer also needs to provide space for the NX_SECURE_X509_CERT data structure which is used to parse the certificate data.</span></span>

<span data-ttu-id="1ca36-575">Вычислить правильный размер буфера можно с помощью следующей формулы:</span><span class="sxs-lookup"><span data-stu-id="1ca36-575">Calculating the proper buffer size can be done with the following formula:</span></span>

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- <span data-ttu-id="1ca36-576">Количество сеансов DTLS определяется размером буфера сеанса, переданного в nx_secure_dtls_server_create.</span><span class="sxs-lookup"><span data-stu-id="1ca36-576">The number of DTLS sessions is determined by the size of the session buffer passed into nx_secure_dtls_server_create.</span></span>
- <span data-ttu-id="1ca36-577">Для параметра certs_per_session должно быть задано ожидаемое максимальное число сертификатов в любой цепочке сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="1ca36-577">certs_per_session should be set to the maximum expected number of certificates in any client certificate chain.</span></span>
- <span data-ttu-id="1ca36-578">Ожидаемый максимальный размер сертификата зависит от приложения, размеров ключей и других факторов, но 2 КБ обычно достаточно.</span><span class="sxs-lookup"><span data-stu-id="1ca36-578">The maximum expected certificate size is dependent on the application, key sizes, and other factors but 2KB is generally sufficient.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-579">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-579">Parameters</span></span>

- <span data-ttu-id="1ca36-580">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-580">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>
- <span data-ttu-id="1ca36-581">**certs_per_session**: число сертификатов, выделяемых для каждого сеанса сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-581">**certs_per_session** Number of certificates to allocate to each DTLS server session.</span></span>
- <span data-ttu-id="1ca36-582">**certs_buffer**: пространство буфера для данных входящего сертификата.</span><span class="sxs-lookup"><span data-stu-id="1ca36-582">**certs_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="1ca36-583">**buffer_size**: размер буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="1ca36-583">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-584">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-584">Return Values</span></span>

- <span data-ttu-id="1ca36-585">**NX_SUCCESS** (0X00): проверка клиента X.509 успешно настроена.</span><span class="sxs-lookup"><span data-stu-id="1ca36-585">**NX_SUCCESS** (0x00) Successful configuration of X.509 Client verification.</span></span>
- <span data-ttu-id="1ca36-586">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-586">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-587">**NX_INVALID_PARAMETERS** (0X4D): недопустимое хранилище сертификатов (возможно, экземпляр сервера DTLS не инициализирован).</span><span class="sxs-lookup"><span data-stu-id="1ca36-587">**NX_INVALID_PARAMETERS** (0x4D) Invalid certificate store (DTLSserver instance not initalized?).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-588">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-588">Allowed From</span></span>

<span data-ttu-id="1ca36-589">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-590">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-590">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-591">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-591">See Also</span></span>

- <span data-ttu-id="1ca36-592">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="1ca36-592">nx_secure_dtls_server_x509_client_verify_disable,</span></span>
- <span data-ttu-id="1ca36-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-593">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-594">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-594">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-595">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-595">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-596">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-596">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="1ca36-597">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-597">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a><span data-ttu-id="1ca36-598">nx_secure_dtls_server_x509_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="1ca36-598">nx_secure_dtls_server_x509_client_verify_disable</span></span>

<span data-ttu-id="1ca36-599">Отключение проверки сертификатов клиента X.509 для сервера NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-599">Disables client X.509 certificate verification for a NetX Secure DTLS Server</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-600">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-600">Prototype</span></span>

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="1ca36-601">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-601">Description</span></span>

<span data-ttu-id="1ca36-602">Эта служба отключает проверку сертификатов клиента X.509 на сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-602">This service disables X.509 Client certificate verification on a DTLS Server.</span></span> <span data-ttu-id="1ca36-603">Эта служба не действует, если не включена проверка на основе сертификата клиента X.509.</span><span class="sxs-lookup"><span data-stu-id="1ca36-603">The service has no effect if X.509 Client certificate verification is not enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="1ca36-604">Отключение проверки подлинности клиента в активном экземпляре сервера DTLS может привести к непредсказуемому поведению.</span><span class="sxs-lookup"><span data-stu-id="1ca36-604">Disabling client authentication on an active DTLS Server instance may result in unpredictable behavior.</span></span> <span data-ttu-id="1ca36-605">Перед изменением состояния сервера необходимо вызвать службу nx_secure_dtls_server_stop.</span><span class="sxs-lookup"><span data-stu-id="1ca36-605">The nx_secure_dtls_server_stop service should be called before changing server state.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-606">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-606">Parameters</span></span>

- <span data-ttu-id="1ca36-607">**server_ptr**: указатель на созданный ранее экземпляр сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-607">**server_ptr** Pointer to a previously created DTLS Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-608">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-608">Return Values</span></span>

- <span data-ttu-id="1ca36-609">**NX_SUCCESS** (0X00): проверка подлинности клиента X.509 успешно отключена.</span><span class="sxs-lookup"><span data-stu-id="1ca36-609">**NX_SUCCESS** (0x00) Successful disabling of X.509 client authentication.</span></span>
- <span data-ttu-id="1ca36-610">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-610">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-611">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-611">Allowed From</span></span>

<span data-ttu-id="1ca36-612">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-613">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-613">Example</span></span>

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-614">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-614">See Also</span></span>

- <span data-ttu-id="1ca36-615">nx_secure_dtls_server_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="1ca36-615">nx_secure_dtls_server_x509_client_verify_configure,</span></span>
- <span data-ttu-id="1ca36-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-616">nx_secure_dtls_server_start, nx_secure_dtls_server_create,</span></span>
- <span data-ttu-id="1ca36-617">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-617">nx_secure_dtls_server_session_start,</span></span>
- <span data-ttu-id="1ca36-618">nx_secure_dtls_server_session_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-618">nx_secure_dtls_server_session_stop,</span></span>
- <span data-ttu-id="1ca36-619">nx_secure_dtls_server_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-619">nx_secure_dtls_server_trusted_certificate_add,</span></span>
- <span data-ttu-id="1ca36-620">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-620">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_client_info_get"></a><span data-ttu-id="1ca36-621">nx_secure_dtls_session_client_info_get</span><span class="sxs-lookup"><span data-stu-id="1ca36-621">nx_secure_dtls_session_client_info_get</span></span>

<span data-ttu-id="1ca36-622">Получение сведений об удаленном клиенте из сеанса сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-622">Get remote client information from a DTLS Server session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-623">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-623">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a><span data-ttu-id="1ca36-624">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-624">Description</span></span>

<span data-ttu-id="1ca36-625">Эта служба возвращает сведения о сети клиента DTLS, подключенного к определенному сеансу сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-625">This service returns the network information about a DTLS Client that is connected to a particular DTLS Server session.</span></span> <span data-ttu-id="1ca36-626">Возвращаемые сведения содержат IP-адрес удаленного клиента и UDP-порт, а также локальный порт сервера, к которому подключен клиент.</span><span class="sxs-lookup"><span data-stu-id="1ca36-626">The information returned consists of the remote client’s IP address and UDP port, as well as the local server port to which the client is connected.</span></span>

<span data-ttu-id="1ca36-627">В общем случае экземпляр сеанса DTLS будет получен в результате вызова одной из процедур обратного вызова для уведомления DTLS (например, процедуры обратного вызова connect_notify или receive_notify, переданной в nx_secure_dtls_server_create).</span><span class="sxs-lookup"><span data-stu-id="1ca36-627">In general, the DTLS session instance will be the one obtained in the invocation of one of the DTLS notification callback routines (e.g. the connect_notify or receive_notify callbacks passed into nx_secure_dtls_server_create).</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-628">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-628">Parameters</span></span>

- <span data-ttu-id="1ca36-629">**session_ptr**: указатель на активный экземпляр сеанса сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-629">**session_ptr** Pointer to an active DTLS server session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-630">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-630">Return Values</span></span>

- <span data-ttu-id="1ca36-631">**NX_SUCCESS** (0X00): сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="1ca36-631">**NX_SUCCESS** (0x00) Successful deletion of server.</span></span>
- <span data-ttu-id="1ca36-632">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-632">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-633">**NX_INVALID_SOCKET** (0x13): недопустимый связанный сокет UDP (возможно, сеанс не инициализирован).</span><span class="sxs-lookup"><span data-stu-id="1ca36-633">**NX_INVALID_SOCKET** (0x13) The associated UDP socket is not valid (session not initialized?).</span></span>
- <span data-ttu-id="1ca36-634">**NX_NOT_CONNECTED** (0X38): сокет UDP не подключен; подключение клиента удалено или еще не установлено.</span><span class="sxs-lookup"><span data-stu-id="1ca36-634">**NX_NOT_CONNECTED** (0x38) UDP socket is not connected – client connection dropped or not yet established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-635">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-635">Allowed From</span></span>

<span data-ttu-id="1ca36-636">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-637">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-637">Example</span></span>

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-638">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-638">See Also</span></span>

- <span data-ttu-id="1ca36-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop</span><span class="sxs-lookup"><span data-stu-id="1ca36-639">nx_secure_dtls_server_start, nx_secure_dtls_server_stop,</span></span>
- <span data-ttu-id="1ca36-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-640">nx_secure_dtls_server_create, nx_secure_dtls_server_delete,</span></span>
- <span data-ttu-id="1ca36-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-641">nx_secure_dtls_session_receive, nx_secure_dtls_server_session_send,</span></span>
- <span data-ttu-id="1ca36-642">nx_secure_dtls_server_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-642">nx_secure_dtls_server_session_start</span></span>

## <a name="nx_secure_dtls_session_create"></a><span data-ttu-id="1ca36-643">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-643">nx_secure_dtls_session_create</span></span>

<span data-ttu-id="1ca36-644">Создание и настройка сеанса NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-644">Create and configure a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-645">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-645">Prototype</span></span>

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a><span data-ttu-id="1ca36-646">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-646">Description</span></span>

<span data-ttu-id="1ca36-647">Эта служба создает и настраивает сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-647">This service creates and configures a DTLS session.</span></span> <span data-ttu-id="1ca36-648">Как правило, она используется для создания сеансов клиента DTLS, так как сеансами сервера DTLS управляет механизм сервера DTLS (см. описание службы *nx_secure_dtls_server_create*), но возможны случаи, в которых приложению необходимо создать единственный изолированный экземпляр сеанса сервера DTLS, для чего можно использовать эту службу<sup>7</sup>.</span><span class="sxs-lookup"><span data-stu-id="1ca36-648">Generally, this will be used to create DTLS Client sessions as DTLS Server sessions are managed with the DTLS Server mechanism (see *nx_secure_dtls_server_create*), but there may be instances where an application needs to create a single stand-alone DTLS Server session instance in which case this service may be used<sup>7</sup>.</span></span>

<span data-ttu-id="1ca36-649">Параметры определяют сведения и выделение памяти, необходимые для создания экземпляра сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-649">The parameters configure the information and memory allocation needed to instantiate a DTLS session.</span></span> <span data-ttu-id="1ca36-650">Параметр crypto_table указывает таблицу TLS, содержащую все криптографические процедуры, необходимые для шифрования и проверки подлинности TLS или DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-650">The crypto_table parameter is a TLS table containing all of the cryptographic routines needed for TLS/DTLS encryption and authentication.</span></span> <span data-ttu-id="1ca36-651">Параметр metadata_buffer используется для вычислительных операций шифрования (см. описание службы nx_secure_tls_metadata_size_calculate в руководстве пользователя NetX Secure TLS), а параметр packet_reassembly_buffer используется для преобразования датаграмм UDP в полные записи DTLS для расшифровки.</span><span class="sxs-lookup"><span data-stu-id="1ca36-651">The metadata_buffer is used for encryption caclulations (see nx_secure_tls_metadata_size_calculate in the NetX Secure TLS User Guide), and the packet_reassembly_buffer is used to reassemble UDP datagrams into a complete DTLS record for decryption.</span></span>

<span data-ttu-id="1ca36-652">Параметры certs_number и remote_certificate_buffer необходимы для клиентов DTLS, которым требуется пространство для хранения и обработки входящей цепочки сертификатов сервера DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-652">The certs_number and remote_certificate_buffer are required for DTLS Clients which need space to store and process the incoming DTLS Server certificate chain.</span></span> <span data-ttu-id="1ca36-653">Буфер должен вмещать ожидаемый максимальный размер цепочки сертификатов для любого сервера, к которому будет подключаться клиент.</span><span class="sxs-lookup"><span data-stu-id="1ca36-653">The buffer must be able to accommodate the maximum expected size of the certificate chain for any server to which it will connect.</span></span> <span data-ttu-id="1ca36-654">Буфер распределяется между всеми ожидаемыми сертификатами (их число задает параметр certs_number). Он должен быть достаточно большим, чтобы вместить одну структуру NX_SECURE_X509_CERT на сертификат.</span><span class="sxs-lookup"><span data-stu-id="1ca36-654">The buffer is divided up by the number of expected certificates (certs_number parameter) and must also be large enough to hold one NX_SECURE_X509_CERT structure per certificate.</span></span> <span data-ttu-id="1ca36-655">Размер буфера можно определить с помощью следующей формулы:</span><span class="sxs-lookup"><span data-stu-id="1ca36-655">The buffer size can be determined using the following formula:</span></span>

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- <span data-ttu-id="1ca36-656">Параметр certs_number задает ожидаемое максимальное число сертификатов в цепочке сертификатов сервера.</span><span class="sxs-lookup"><span data-stu-id="1ca36-656">certs_number is the expected maximum number of certificates in the server’s certificate chain</span></span>
- <span data-ttu-id="1ca36-657">Максимальный размер сертификата зависит от размера используемых ключей и сведений в сертификате, но 2 КБ обычно достаточно.</span><span class="sxs-lookup"><span data-stu-id="1ca36-657">Maximum certificate size is dependent on the size of keys being used and the information in the certificate, but 2KB is generally sufficient.</span></span>

<span data-ttu-id="1ca36-658">**7** Создание сеансов сервера DTLS с помощью этой процедуры не рекомендуется и связано с определенными ограничениями.</span><span class="sxs-lookup"><span data-stu-id="1ca36-658">**7** Creating DTLS Server sessions with this routine is not recommended and comes with some limitations.</span></span> <span data-ttu-id="1ca36-659">Основной проблемой является то, что сеанс не будет корректно работать с дополнительными подключениями клиентов. Так как протокол UDP не зависит от подключения, а второй клиент вполне может отправить данные на UDP-порт сервера, пока предыдущий сеанс DTLS еще активен, это вызовет завершение сбоем сеанса сервера.</span><span class="sxs-lookup"><span data-stu-id="1ca36-659">The primary issue is that the session will not handle additional client connections gracefully – since UDP is connectionless a second client can legally send data to the server’s UDP port when a previous DTLS session is still active which would cause the server session to end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-660">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-660">Parameters</span></span>

- <span data-ttu-id="1ca36-661">**dtls_session**: указатель на неинициализированную структуру сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-661">**dtls_session** Pointer to an uninitialized DTLS Session structure.</span></span>
- <span data-ttu-id="1ca36-662">**crypto_table**: указатель на структуру таблицы шифрования TLS или DTLS, используемую для всех криптографических операций.</span><span class="sxs-lookup"><span data-stu-id="1ca36-662">**crypto_table** Pointer to a TLS/DTLS encryption table structure used for all cryptographic operations.</span></span>
- <span data-ttu-id="1ca36-663">**crypto_metadata_buffer**: буферное пространство для вычислений криптографических операций и хранения сведений о состоянии.</span><span class="sxs-lookup"><span data-stu-id="1ca36-663">**crypto_metadata_buffer** Buffer space for cryptographic operation calculations and state information.</span></span>
- <span data-ttu-id="1ca36-664">**crypto_metadata_size**: размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="1ca36-664">**crypto_metadata_size** Size of metadata buffer.</span></span>
- <span data-ttu-id="1ca36-665">**packet_reassembly_buffer**: буфер, используемый протоколом DTLS для преобразования данных UDP в записи DTLS для расшифровки.</span><span class="sxs-lookup"><span data-stu-id="1ca36-665">**packet_reassembly_buffer** Buffer used by DTLS to reassemble UDP data into DTLS records for decryption.</span></span>
- <span data-ttu-id="1ca36-666">**packet_reassembly_buffer_size**: размер буфера преобразования данных.</span><span class="sxs-lookup"><span data-stu-id="1ca36-666">**packet_reassembly_buffer_size** Size of reassembly buffer.</span></span> <span data-ttu-id="1ca36-667">Обычно размер этого буфера должен быть больше 16 КБ, но он может быть меньше, что зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="1ca36-667">Generally should be greater than 16KB but may be smaller depending on application.</span></span>
- <span data-ttu-id="1ca36-668">**certs_number**: ожидаемое максимальное число сертификатов в цепочке сертификатов удаленного сервера.</span><span class="sxs-lookup"><span data-stu-id="1ca36-668">**certs_number** Maximum expected number of certificates in the remote server’s certificate chain.</span></span>
- <span data-ttu-id="1ca36-669">**remote_certificate_buffer**: пространство буфера для данных входящего сертификата.</span><span class="sxs-lookup"><span data-stu-id="1ca36-669">**remote_certificate_buffer** Buffer space for incoming certificate data.</span></span>
- <span data-ttu-id="1ca36-670">**remote_certificate_buffer_size**: размер буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="1ca36-670">**remote_certificate_buffer_size** Size of the certificate buffer.</span></span>


### <a name="return-values"></a><span data-ttu-id="1ca36-671">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-671">Return Values</span></span>

- <span data-ttu-id="1ca36-672">**NX_SUCCESS** (0X00): сеанс успешно создан.</span><span class="sxs-lookup"><span data-stu-id="1ca36-672">**NX_SUCCESS** (0x00) Successful creation of session.</span></span>
- <span data-ttu-id="1ca36-673">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.</span><span class="sxs-lookup"><span data-stu-id="1ca36-673">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="1ca36-674">**NX_INVALID_PARAMETERS** (0x4D): недостаточно пространства буфера для повторной сборки пакетов, сертификатов или шифрования.</span><span class="sxs-lookup"><span data-stu-id="1ca36-674">**NX_INVALID_PARAMETERS** (0x4D) Not enough buffer space for packet reassembly, certificates, or cryptography.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-675">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-675">Allowed From</span></span>

<span data-ttu-id="1ca36-676">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-677">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-677">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-678">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-678">See Also</span></span>

- <span data-ttu-id="1ca36-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-679">nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-680">nx_secure_dtls_session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-680">nx_secure_dtls_session_send</span></span>

## <a name="nx_secure_dtls_session_delete"></a><span data-ttu-id="1ca36-681">nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-681">nx_secure_dtls_session_delete</span></span>

<span data-ttu-id="1ca36-682">Освобождение ресурсов, используемых сеансом NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-682">Free up resources used by a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-683">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-683">Prototype</span></span>

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a><span data-ttu-id="1ca36-684">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-684">Description</span></span>

<span data-ttu-id="1ca36-685">Эта служба удаляет сеанс DTLS, освобождая все ресурсы, которые были выделены при его создании.</span><span class="sxs-lookup"><span data-stu-id="1ca36-685">This service deletes a DTLS session, freeing up any resources that were allocated when it was created.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-686">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-686">Parameters</span></span>

- <span data-ttu-id="1ca36-687">**dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.</span><span class="sxs-lookup"><span data-stu-id="1ca36-687">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-688">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-688">Return Values</span></span>

- <span data-ttu-id="1ca36-689">**NX_SUCCESS** (0X00): сеанс успешно удален.</span><span class="sxs-lookup"><span data-stu-id="1ca36-689">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="1ca36-690">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.</span><span class="sxs-lookup"><span data-stu-id="1ca36-690">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-691">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-691">Allowed From</span></span>

<span data-ttu-id="1ca36-692">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-693">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-693">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-694">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-694">See Also</span></span>

- <span data-ttu-id="1ca36-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-695">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-696">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_end"></a><span data-ttu-id="1ca36-697">nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="1ca36-697">nx_secure_dtls_session_end</span></span>

<span data-ttu-id="1ca36-698">Завершение активного сеанса NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-698">Shut down an active NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-699">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-699">Prototype</span></span>

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="1ca36-700">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-700">Description</span></span>

<span data-ttu-id="1ca36-701">Эта служба завершает активный сеанс DTLS, отправляя оповещение CloseNotify (TLS или DTLS) на удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="1ca36-701">This service ends an active DTLS session by sending a TLS/DTLS CloseNotify alert to the remote host.</span></span> <span data-ttu-id="1ca36-702">Используются IP-адрес и порт, указанные в предыдущем вызове nx_secure_dtls_session_send.</span><span class="sxs-lookup"><span data-stu-id="1ca36-702">The IP address and port used are those used in the previous call to nx_secure_dtls_session_send.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-703">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-703">Parameters</span></span>

- <span data-ttu-id="1ca36-704">**dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.</span><span class="sxs-lookup"><span data-stu-id="1ca36-704">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="1ca36-705">**wait_option**: значение ожидания ThreadX, используемое для сетевых операций.</span><span class="sxs-lookup"><span data-stu-id="1ca36-705">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-706">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-706">Return Values</span></span>

- <span data-ttu-id="1ca36-707">**NX_SUCCESS** (0X00): сеанс успешно удален.</span><span class="sxs-lookup"><span data-stu-id="1ca36-707">**NX_SUCCESS** (0x00) Successful deletion of session.</span></span>
- <span data-ttu-id="1ca36-708">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.</span><span class="sxs-lookup"><span data-stu-id="1ca36-708">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>
- <span data-ttu-id="1ca36-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить пакеты для оповещения CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="1ca36-709">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate packet(s) for CloseNotify alert.</span></span>
- <span data-ttu-id="1ca36-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): возможно, внутренняя ошибка; не распознана криптографическая процедура.</span><span class="sxs-lookup"><span data-stu-id="1ca36-710">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) Likely internal error – cryptographic routine not recognized.</span></span>
- <span data-ttu-id="1ca36-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): сбой при базовой операции отправки по протоколу UDP.</span><span class="sxs-lookup"><span data-stu-id="1ca36-711">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Underlying UDP send failed.</span></span>
- <span data-ttu-id="1ca36-712">**NX_IP_ADDRESS_ERROR** (0x21): ошибка из-за IP-адреса удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="1ca36-712">**NX_IP_ADDRESS_ERROR** (0x21) Error with remote host IP address.</span></span>
- <span data-ttu-id="1ca36-713">**NX_NOT_BOUND** (0X24): базовый сокет UDP не привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="1ca36-713">**NX_NOT_BOUND** (0x24) Underlying UDP socket not bound to port.</span></span>
- <span data-ttu-id="1ca36-714">**NX_INVALID_PORT** (0x46): недопустимый UDP-порт.</span><span class="sxs-lookup"><span data-stu-id="1ca36-714">**NX_INVALID_PORT** (0x46) Invalid UDP port.</span></span>
- <span data-ttu-id="1ca36-715">**NX_PORT_UNAVAILABLE** (0x23): UDP-порт недоступен для использования.</span><span class="sxs-lookup"><span data-stu-id="1ca36-715">**NX_PORT_UNAVAILABLE** (0x23) UDP port not available for use.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-716">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-716">Allowed From</span></span>

<span data-ttu-id="1ca36-717">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-717">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-718">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-718">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a><span data-ttu-id="1ca36-719">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-719">See Also</span></span>

- <span data-ttu-id="1ca36-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-720">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-721">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_local_certificate_add"></a><span data-ttu-id="1ca36-722">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-722">nx_secure_dtls_session_local_certificate_add</span></span>

<span data-ttu-id="1ca36-723">Добавление локального удостоверяющего сертификата в сеанс NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-723">Add a local identity certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-724">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-724">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-725">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-725">Description</span></span>

<span data-ttu-id="1ca36-726">Эта служба добавляет локальный сертификат удостоверения в экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-726">This service adds a local identity certificate to a DTLS Session instance.</span></span> <span data-ttu-id="1ca36-727">В общем случае эта служба используется, когда сеансу клиента DTLS требуется предоставить сертификат удостоверения для узла удаленного сервера.</span><span class="sxs-lookup"><span data-stu-id="1ca36-727">In general, this service will be used when a DTLS Client session needs to provide an identity certificate to a remote server host.</span></span> <span data-ttu-id="1ca36-728">Это необязательная конфигурация для протокола DTLS, поэтому сертификат для клиентов DTLS, как правило, не требуется.</span><span class="sxs-lookup"><span data-stu-id="1ca36-728">This is an optional configuration for DTLS so a certificate is not generally required for DTLS Clients.</span></span> <span data-ttu-id="1ca36-729">Для сертификата удостоверения требуется связанный закрытый ключ.</span><span class="sxs-lookup"><span data-stu-id="1ca36-729">An identity certificate requires an associated private key.</span></span>

<span data-ttu-id="1ca36-730">Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="1ca36-730">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="1ca36-731">Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-731">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="1ca36-732">Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-732">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-733">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-733">Parameters</span></span>

- <span data-ttu-id="1ca36-734">**session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-734">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="1ca36-735">**certificate**: указатель на инициализированную ранее структуру сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="1ca36-735">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="1ca36-736">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-736">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-737">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-737">Return Values</span></span>

- <span data-ttu-id="1ca36-738">**NX_SUCCESS** (0X00): сертификат успешно добавлен в сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-738">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="1ca36-739">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-739">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-740">**NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-740">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-741">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-741">Allowed From</span></span>

<span data-ttu-id="1ca36-742">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-742">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-743">Например, .</span><span class="sxs-lookup"><span data-stu-id="1ca36-743">Example</span></span>

<span data-ttu-id="1ca36-744">\* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-744">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-745">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-745">See Also</span></span>

- <span data-ttu-id="1ca36-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-746">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-747">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="1ca36-748">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-748">nx_secure_dtls_session_local_certificate_remove,</span></span>
- <span data-ttu-id="1ca36-749">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-749">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_local_certificate_remove"></a><span data-ttu-id="1ca36-750">nx_secure_dtls_session_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-750">nx_secure_dtls_session_local_certificate_remove</span></span>

<span data-ttu-id="1ca36-751">Удаление локального удостоверяющего сертификата из сеанса NetX Secure DTLS</span><span class="sxs-lookup"><span data-stu-id="1ca36-751">Remove a local identity certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-752">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-752">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-753">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-753">Description</span></span>

<span data-ttu-id="1ca36-754">Эта служба удаляет локальный сертификат удостоверения из экземпляра сеанса DTLS, используя идентификационный номер сертификата (назначенный при добавлении сертификата с помощью службы nx_secure_dtls_session_local_certificate_add) или поле общего имени X.509, CommonName.</span><span class="sxs-lookup"><span data-stu-id="1ca36-754">This service removes a local identity certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_local_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="1ca36-755">Если для сопоставления сертификатов используется параметр common_name, то параметру cert_id должно быть присвоено значение 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-755">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="1ca36-756">Если используется параметр cert_id, то параметру common_name должно быть присвоено значение NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="1ca36-756">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="1ca36-757">Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="1ca36-757">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="1ca36-758">Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-758">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="1ca36-759">Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-759">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-760">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-760">Parameters</span></span>

- <span data-ttu-id="1ca36-761">**session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-761">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="1ca36-762">**common_name**: указатель на строку CommonName для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="1ca36-762">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="1ca36-763">**common_name_length**: длина строки common_name.</span><span class="sxs-lookup"><span data-stu-id="1ca36-763">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="1ca36-764">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-764">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-765">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-765">Return Values</span></span>

- <span data-ttu-id="1ca36-766">**NX_SUCCESS** (0X00): сертификат успешно удален из сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-766">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="1ca36-767">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-767">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден в данном сеансе DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-768">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-769">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-769">Allowed From</span></span>

<span data-ttu-id="1ca36-770">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-770">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-771">Например, .</span><span class="sxs-lookup"><span data-stu-id="1ca36-771">Example</span></span>

<span data-ttu-id="1ca36-772">\* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-772">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-773">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-773">See Also</span></span>

- <span data-ttu-id="1ca36-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-774">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-775">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="1ca36-776">nx_secure_dtls_session_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-776">nx_secure_dtls_session_local_certificate_add,</span></span>
- <span data-ttu-id="1ca36-777">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-777">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_receive"></a><span data-ttu-id="1ca36-778">nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-778">nx_secure_dtls_session_receive</span></span>

<span data-ttu-id="1ca36-779">Получение данных приложения через установленный сеанс NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-779">Receive application data over an established NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-780">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-780">Prototype</span></span>

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a><span data-ttu-id="1ca36-781">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-781">Description</span></span>

<span data-ttu-id="1ca36-782">Эта служба возвращает данные приложения, полученные активным сеансом DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-782">This service returns application data received by an active DTLS Session.</span></span> <span data-ttu-id="1ca36-783">Это может быть либо сеанс сервера DTLS (управляемый экземпляром сервера DTLS), либо сеанс клиента DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-783">The DTLS Session may be either a DTLS Server session (managed by a DTLS Server instance) or a DTLS Client session.</span></span> <span data-ttu-id="1ca36-784">Возвращаемый пакет может обрабатываться с помощью любой из служб API NX_PACKET (дополнительные сведения см. в документации по NetX).</span><span class="sxs-lookup"><span data-stu-id="1ca36-784">The returned packet may be processed using any of the NX_PACKET API services (see the NetX documentation for more information).</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-785">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-785">Parameters</span></span>

- <span data-ttu-id="1ca36-786">**dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.</span><span class="sxs-lookup"><span data-stu-id="1ca36-786">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>
- <span data-ttu-id="1ca36-787">**packet_ptr_ptr**: указатель на указатель NX_PACKET для возвращаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="1ca36-787">**packet_ptr_ptr** Pointer to an NX_PACKET pointer for the return packet.</span></span>
- <span data-ttu-id="1ca36-788">**wait_option**: значение ожидания ThreadX, используемое для сетевых операций.</span><span class="sxs-lookup"><span data-stu-id="1ca36-788">**wait_option** ThreadX wait value to use for network operations.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-789">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-789">Return Values</span></span>

- <span data-ttu-id="1ca36-790">**NX_SUCCESS** (0X00): пакет данных приложения успешно получен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-790">**NX_SUCCESS** (0x00) Successful receipt of application data packet.</span></span>
- <span data-ttu-id="1ca36-791">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или пакет.</span><span class="sxs-lookup"><span data-stu-id="1ca36-791">**NX_PTR_ERROR** (0x07) Invalid session or packet pointer.</span></span>
- <span data-ttu-id="1ca36-792">**NX_NOT_ENABLED** (0X14): протокол UDP не включен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-792">**NX_NOT_ENABLED** (0x14) UDP is not enabled.</span></span>
- <span data-ttu-id="1ca36-793">**NX_NOT_BOUND** (0X24): сокет UDP не привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="1ca36-793">**NX_NOT_BOUND** (0x24) UDP socket not bound to port.</span></span>
- <span data-ttu-id="1ca36-794">**NX_SECURE_TLS_INVALID_PACKET** (0X104): получены данные, которые не являются допустимой записью DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-794">**NX_SECURE_TLS_INVALID_PACKET** (0x104) Recevied data that was not a valid DTLS record.</span></span>
- <span data-ttu-id="1ca36-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108): не удалось правильно хэшировать запись DTLS (ошибка шифрования).</span><span class="sxs-lookup"><span data-stu-id="1ca36-795">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A DTLS record failed to be properly hashed (encryption error).</span></span>
- <span data-ttu-id="1ca36-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A): ошибка проверки заполнения шифрования.</span><span class="sxs-lookup"><span data-stu-id="1ca36-796">**NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) Encryption padding check failure.</span></span>
- <span data-ttu-id="1ca36-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114): от удаленного узла получено оповещение.</span><span class="sxs-lookup"><span data-stu-id="1ca36-797">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Recevied an alert from the remote host.</span></span>
- <span data-ttu-id="1ca36-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0X102): получено нераспознанное сообщение.</span><span class="sxs-lookup"><span data-stu-id="1ca36-798">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE**    (0x102) Received an unrecognized message.</span></span>
- <span data-ttu-id="1ca36-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0X10A): получена запись DTLS с недопустимой длиной.</span><span class="sxs-lookup"><span data-stu-id="1ca36-799">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) Recevied a DTLS record with an invalid length.</span></span>
- <span data-ttu-id="1ca36-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): обнаружен неизвестный комплект шифров (внутренняя ошибка шифрования).</span><span class="sxs-lookup"><span data-stu-id="1ca36-800">**NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) An unknown ciphersuite was encountered (indicates internal cryptography error).</span></span>
- <span data-ttu-id="1ca36-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0X12E): получена запись DTLS с несоответствующей версией DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-801">**NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) Recevied a DTLS record with a mismatched DTLS version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-802">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-802">Allowed From</span></span>

<span data-ttu-id="1ca36-803">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-804">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-804">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-805">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-805">See Also</span></span>

- <span data-ttu-id="1ca36-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end</span><span class="sxs-lookup"><span data-stu-id="1ca36-806">nx_secure_dtls_client_session_start, nx_secure_dtls_session_end,</span></span>
- <span data-ttu-id="1ca36-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-807">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_session_reset"></a><span data-ttu-id="1ca36-808">nx_secure_dtls_session_reset</span><span class="sxs-lookup"><span data-stu-id="1ca36-808">nx_secure_dtls_session_reset</span></span>

<span data-ttu-id="1ca36-809">Очистка данных в экземпляре сеанса NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-809">Clear data in an NetX Secure DTLS Session instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-810">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-810">Prototype</span></span>

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a><span data-ttu-id="1ca36-811">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-811">Description</span></span>

<span data-ttu-id="1ca36-812">Эта служба сбрасывает сеанс DTLS, удаляя все временные криптографические данные и позволяя повторно использовать структуру для нового сеанса.</span><span class="sxs-lookup"><span data-stu-id="1ca36-812">This service resets a DTLS session, clearing all ephemeral cryptographic data and allowing the structure to be re-used for a new session.</span></span> <span data-ttu-id="1ca36-813">Постоянные данные (например, хранилища сертификатов) сохраняются, чтобы службу nx_secure_dtls_session_create не нужно было вызывать повторно.</span><span class="sxs-lookup"><span data-stu-id="1ca36-813">Persistent data (e.g. certificate stores) are maintained so that nx_secure_dtls_session_create need not be called repeatedly.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-814">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-814">Parameters</span></span>

- <span data-ttu-id="1ca36-815">**dtls_session**: указатель на структуру сеанса DTLS, которая была инициализирована ранее.</span><span class="sxs-lookup"><span data-stu-id="1ca36-815">**dtls_session** Pointer to a DTLS Session structure that was initialized previously.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-816">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-816">Return Values</span></span>

- <span data-ttu-id="1ca36-817">**NX_SUCCESS** (0X00): сеанс успешно сброшен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-817">**NX_SUCCESS** (0x00) Successful reset of session.</span></span>
- <span data-ttu-id="1ca36-818">**NX_PTR_ERROR** (0x07): недопустимый указатель на сеанс или буфер.</span><span class="sxs-lookup"><span data-stu-id="1ca36-818">**NX_PTR_ERROR** (0x07) Invalid session or buffer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-819">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-819">Allowed From</span></span>

<span data-ttu-id="1ca36-820">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-820">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-821">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-821">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-822">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-822">See Also</span></span>

- <span data-ttu-id="1ca36-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-823">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span><span class="sxs-lookup"><span data-stu-id="1ca36-824">nx_secure_dtls_session_send, nx_secure_dtls_session_delete</span></span>

## <a name="nx_secure_dtls_-session_send"></a><span data-ttu-id="1ca36-825">nx_secure_dtls_ session_send</span><span class="sxs-lookup"><span data-stu-id="1ca36-825">nx_secure_dtls_ session_send</span></span>

<span data-ttu-id="1ca36-826">Отправка данных через сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-826">Send data over a DTLS session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-827">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-827">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a><span data-ttu-id="1ca36-828">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-828">Description</span></span>

<span data-ttu-id="1ca36-829">Эта служба отправляет пакет данных через установленный сеанс DTLS на удаленный узел DTLS, используя заданные IP-адрес и порт.</span><span class="sxs-lookup"><span data-stu-id="1ca36-829">This service sends a packet of data over an established DTLS Session to a remote DTLS host at the given IP address and port.</span></span> <span data-ttu-id="1ca36-830">Для этого используется активный сеанс клиента DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-830">The session used is an active DTLS Client session.</span></span> <span data-ttu-id="1ca36-831">Обратите внимание на то, что IP-адрес и порт предоставляются ввиду особенностей протокола UDP, в котором состояния не сохраняются, но в общем случае они должны соответствовать адресу и порту, используемым в службе nx_secure_dtls_session_start для запуска сеанса.</span><span class="sxs-lookup"><span data-stu-id="1ca36-831">Note that the IP address and port are provided due to the stateless nature of UDP but should generally match the address and port used to start the session in nx_secure_dtls_session_start.</span></span>

<span data-ttu-id="1ca36-832">Данные в пакете, который должен быть выделены с помощью службы *nx_secure_dtls_packet_allocate*, шифруются с помощью криптографических параметров и процедур сеанса DTLS, а затем отправляются на удаленный узел через сокет UDP сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-832">The data provided in the packet, which must be allocated using *nx_secure_dtls_packet_allocate*, is encrypted using the DTLS session cryptographic parameters and routines and then sent to the remote host over the DTLS Session’s UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-833">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-833">Parameters</span></span>

- <span data-ttu-id="1ca36-834">**session_ptr**: указатель на активный экземпляр сеанса клиента DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-834">**session_ptr** Pointer to an active DTLS client session instance.</span></span>
- <span data-ttu-id="1ca36-835">**packet_ptr**: указатель на экземпляр NX_PACKET, выделенный ранее и заполненный данными приложения.</span><span class="sxs-lookup"><span data-stu-id="1ca36-835">**packet_ptr** Pointer to an NX_PACKET instance allocated previously and populated with application data.</span></span>
- <span data-ttu-id="1ca36-836">**ip_address**: указатель на структуру NXD_ADDRESS, содержащую IP-адрес удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="1ca36-836">**ip_address** Pointer to an NXD_ADDRESS structure containing the IP address of the remote host.</span></span>
- <span data-ttu-id="1ca36-837">**port**: UDP-порт на удаленном узле.</span><span class="sxs-lookup"><span data-stu-id="1ca36-837">**port** UDP port on the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-838">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-838">Return Values</span></span>

- <span data-ttu-id="1ca36-839">**NX_SUCCESS** (0X00): пакет успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="1ca36-839">**NX_SUCCESS** (0x00) Successful send of packet.</span></span>
- <span data-ttu-id="1ca36-840">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-840">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): произошла ошибка в базовой операции отправки по протоколу UDP.</span><span class="sxs-lookup"><span data-stu-id="1ca36-841">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An error occurred in the underlying UDP send operation.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-842">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-842">Allowed From</span></span>

<span data-ttu-id="1ca36-843">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-843">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-844">Пример</span><span class="sxs-lookup"><span data-stu-id="1ca36-844">Example</span></span>

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-845">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-845">See Also</span></span>

- <span data-ttu-id="1ca36-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-846">nx_secure_dtls_client_session_start, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-847">nx_secure_dtls_session_create</span><span class="sxs-lookup"><span data-stu-id="1ca36-847">nx_secure_dtls_session_create</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a><span data-ttu-id="1ca36-848">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-848">nx_secure_dtls_session_trusted_certificate_add</span></span>

<span data-ttu-id="1ca36-849">Добавление сертификата доверенного ЦС в сеанс NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-849">Add a trusted CA certificate to a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-850">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-850">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-851">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-851">Description</span></span>

<span data-ttu-id="1ca36-852">Эта служба добавляет сертификат доверенного или промежуточного ЦС X.509 в экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-852">This service adds a trusted CA or intermediate CA X.509 certificate to a DTLS Session instance.</span></span> <span data-ttu-id="1ca36-853">Клиент DTLS должен иметь по крайней мере один доверенный сертификат для проверки сертификатов удаленных серверов, если не используется альтернативный механизм проверки подлинности (например, общие ключи).</span><span class="sxs-lookup"><span data-stu-id="1ca36-853">A DTLS Client requires at least one trusted certificate in order to validate remote server certificates unless an alternative authentication mechanism is used (e.g. Pre-Shared Keys).</span></span> <span data-ttu-id="1ca36-854">Доверенный сертификат обычно не имеет закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="1ca36-854">A trusted certificate does not usually have a private key.</span></span>

<span data-ttu-id="1ca36-855">Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="1ca36-855">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="1ca36-856">Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-856">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="1ca36-857">Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-857">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-858">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-858">Parameters</span></span>

- <span data-ttu-id="1ca36-859">**session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-859">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="1ca36-860">**certificate**: указатель на инициализированную ранее структуру сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="1ca36-860">**certificate** Pointer to a previously initialized X.509 certificate structure.</span></span>
- <span data-ttu-id="1ca36-861">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-861">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>

### <a name="return-values"></a><span data-ttu-id="1ca36-862">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-862">Return Values</span></span>

- <span data-ttu-id="1ca36-863">**NX_SUCCESS** (0X00): сертификат успешно добавлен в сеанс DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-863">**NX_SUCCESS** (0x00) Successful addition of certificate to DTLS session.</span></span>
- <span data-ttu-id="1ca36-864">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-864">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-865">**NX_INVALID_PARAMETERS** (0x4D): передан идентификатор сертификата, равный 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-865">**NX_INVALID_PARAMETERS** (0x4D) A certificate ID of 0 was passed in.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-866">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-866">Allowed From</span></span>

<span data-ttu-id="1ca36-867">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-868">Например, .</span><span class="sxs-lookup"><span data-stu-id="1ca36-868">Example</span></span>

<span data-ttu-id="1ca36-869">\* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-869">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-870">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-870">See Also</span></span>

- <span data-ttu-id="1ca36-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-871">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-872">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="1ca36-873">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-873">nx_secure_dtls_session_trusted_certificate_remove,</span></span>
- <span data-ttu-id="1ca36-874">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-874">nx_secure_x509_certificate_initialize</span></span>

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a><span data-ttu-id="1ca36-875">nx_secure_dtls_session_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="1ca36-875">nx_secure_dtls_session_trusted_certificate_remove</span></span>

<span data-ttu-id="1ca36-876">Удаление сертификата доверенного ЦС из сеанса NetX Secure DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-876">Remove a trusted CA certificate from a NetX Secure DTLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="1ca36-877">Прототип</span><span class="sxs-lookup"><span data-stu-id="1ca36-877">Prototype</span></span>

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a><span data-ttu-id="1ca36-878">Описание</span><span class="sxs-lookup"><span data-stu-id="1ca36-878">Description</span></span>

<span data-ttu-id="1ca36-879">Эта служба удаляет сертификат доверенного ЦС из экземпляра сеанса DTLS, используя идентификационный номер сертификата (назначенный при добавлении сертификата с помощью службы nx_secure_dtls_session_local_certificate_add) или поле общего имени X.509, CommonName.</span><span class="sxs-lookup"><span data-stu-id="1ca36-879">This service removes a trusted CA certificate from a DTLS Session instance using either a certificate ID number (assigned when the certificate was added with nx_secure_dtls_session_trusted_certificate_add) or the X.509 CommonName field.</span></span>

<span data-ttu-id="1ca36-880">Если для сопоставления сертификатов используется параметр common_name, то параметру cert_id должно быть присвоено значение 0.</span><span class="sxs-lookup"><span data-stu-id="1ca36-880">If the common_name is used to match the certificate, the cert_id parameter should be set to 0.</span></span> <span data-ttu-id="1ca36-881">Если используется параметр cert_id, то параметру common_name должно быть присвоено значение NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="1ca36-881">If cert_id is used, common_name should be passed a value of NX_NULL.</span></span>

<span data-ttu-id="1ca36-882">Параметр cert_id — это числовой идентификатор сертификата, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="1ca36-882">The cert_id parameter is a numeric, non-zero identifier for the certificate.</span></span> <span data-ttu-id="1ca36-883">Он позволяет легко удалить сертификат или найти его в событии с несколькими сертификатами удостоверений, для которых указано одинаковое общее имя X.509 в хранилище сертификатов DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-883">This enables the certificate to be easily removed or found in the event there are multiple identity certificates with the same X.509 Common Name present in the DTLS certificate store.</span></span> <span data-ttu-id="1ca36-884">Дополнительные сведения о сертификатах X.509 см. в руководстве пользователя NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-884">See the NetX Secure TLS User Guide for more information about X.509 certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="1ca36-885">Параметры</span><span class="sxs-lookup"><span data-stu-id="1ca36-885">Parameters</span></span>

- <span data-ttu-id="1ca36-886">**session_ptr**: указатель на созданный ранее экземпляр сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-886">**session_ptr** Pointer to a previously created DTLS Session instance.</span></span>
- <span data-ttu-id="1ca36-887">**common_name**: указатель на строку CommonName для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="1ca36-887">**common_name** Pointer to the CommonName string to match.</span></span>
- <span data-ttu-id="1ca36-888">**common_name_length**: длина строки common_name.</span><span class="sxs-lookup"><span data-stu-id="1ca36-888">**common_name_length** Length of the common_name string.</span></span>
- <span data-ttu-id="1ca36-889">**cert_ID**: отличный от нуля уникальный числовой идентификатор данного сертификата на этом сервере DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-889">**cert_id** Numeric non-zero unique identifier for this certificate in this DTLS server.</span></span>


### <a name="return-values"></a><span data-ttu-id="1ca36-890">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1ca36-890">Return Values</span></span>

- <span data-ttu-id="1ca36-891">**NX_SUCCESS** (0X00): сертификат успешно удален из сеанса DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-891">**NX_SUCCESS** (0x00) Successful removal of certificate from DTLS session.</span></span>
- <span data-ttu-id="1ca36-892">**NX_PTR_ERROR** (0x07): передан недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="1ca36-892">**NX_PTR_ERROR** (0x07) Invalid pointer passed.</span></span>
- <span data-ttu-id="1ca36-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119): сертификат, соответствующий cert_id или common_name, не найден в данном сеансе DTLS.</span><span class="sxs-lookup"><span data-stu-id="1ca36-893">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate matching the cert_id or common_name was found in the given DTLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1ca36-894">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1ca36-894">Allowed From</span></span>

<span data-ttu-id="1ca36-895">Потоки</span><span class="sxs-lookup"><span data-stu-id="1ca36-895">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1ca36-896">Например, .</span><span class="sxs-lookup"><span data-stu-id="1ca36-896">Example</span></span>

<span data-ttu-id="1ca36-897">\* Более полный пример доступен в справочнике по службе *nx_secure_dtls_session_create*.</span><span class="sxs-lookup"><span data-stu-id="1ca36-897">\*See reference for *nx_secure_dtls_session_create* for a more complete example.</span></span>

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a><span data-ttu-id="1ca36-898">См. также:</span><span class="sxs-lookup"><span data-stu-id="1ca36-898">See Also</span></span>

- <span data-ttu-id="1ca36-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive</span><span class="sxs-lookup"><span data-stu-id="1ca36-899">nx_secure_dtls_session_create, nx_secure_dtls_session_receive,</span></span>
- <span data-ttu-id="1ca36-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start</span><span class="sxs-lookup"><span data-stu-id="1ca36-900">nx_secure_dtls_session_send, nx_secure_dtls_session_start,</span></span>
- <span data-ttu-id="1ca36-901">nx_secure_dtls_session_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="1ca36-901">nx_secure_dtls_session_trusted_certificate_add,</span></span>
- <span data-ttu-id="1ca36-902">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="1ca36-902">nx_secure_x509_certificate_initialize</span></span>
