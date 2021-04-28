---
title: Глава 4. Описание служб NetX Secure для ОСРВ Azure
description: В этой главе приведено описание всех служб NetX Secure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815352"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="3d147-103">Глава 4. Описание служб NetX Secure для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="3d147-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="3d147-104">В этой главе приведено описание всех служб NetX Secure для ОСРВ Azure, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="3d147-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="3d147-105">В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, выделенные **полужирным шрифтом**, не затрагиваются макросом **NX_SECURE_DISABLE_ERROR_CHECKING**, который используется для отключения проверки API на предмет ошибок. Значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="3d147-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="3d147-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="3d147-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="3d147-107">Выполнение самостоятельного тестирования для методов шифрования</span><span class="sxs-lookup"><span data-stu-id="3d147-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="3d147-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="3d147-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="3d147-109">Вычисление хэш-значения с помощью пользовательской хэш-функции</span><span class="sxs-lookup"><span data-stu-id="3d147-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="3d147-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="3d147-111">Установка активного сертификата удостоверения для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="3d147-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="3d147-113">Установка общего ключа для сеанса клиента NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="3d147-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="3d147-115">Инициализация модуля NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="3d147-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="3d147-117">Добавление локального сертификата в сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="3d147-119">Поиск локального сертификата в сеансе NetX Secure TLS по общему имени</span><span class="sxs-lookup"><span data-stu-id="3d147-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="3d147-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="3d147-121">Удалить локальный сертификат из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="3d147-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="3d147-123">Вычисление размера криптографических метаданных для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="3d147-125">Выделение пакета для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="3d147-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="3d147-127">Добавление общего ключа в сеанс TLS в NetX Secure</span><span class="sxs-lookup"><span data-stu-id="3d147-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="3d147-129">Выделение пространства для сертификата, предоставленного удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="3d147-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="3d147-131">Выделение пространства для всех сертификатов, предоставленных удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="3d147-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="3d147-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="3d147-133">Освобождение места, выделенного для входящих сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="3d147-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="3d147-135">Добавление сертификата специально для серверов TLS с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="3d147-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="3d147-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="3d147-137">Поиск сертификата по числовому идентификатору</span><span class="sxs-lookup"><span data-stu-id="3d147-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="3d147-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="3d147-139">Удаление сертификата локального сервера с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="3d147-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="3d147-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="3d147-141">Настройка обратного вызова для протокола TLS, который будет использоваться для дополнительной проверки сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="3d147-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="3d147-143">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения клиента TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="3d147-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="3d147-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="3d147-145">Включение проверки X.509 клиента и выделение места для сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="3d147-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="3d147-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="3d147-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="3d147-147">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="3d147-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="3d147-149">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="3d147-151">Создание сеанса NetX Secure TLS для обеспечения безопасности подключений</span><span class="sxs-lookup"><span data-stu-id="3d147-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="3d147-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="3d147-153">Удаление сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="3d147-155">Завершение активного сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="3d147-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="3d147-157">Установка буфера повторной сборки пакетов для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="3d147-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="3d147-159">Переопределение версии протокола TLS по умолчанию для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="3d147-161">Получение данных из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="3d147-163">Назначение обратного вызова, который будет выполняться в начале повторного согласования сеанса</span><span class="sxs-lookup"><span data-stu-id="3d147-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="3d147-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="3d147-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="3d147-165">Инициация подтверждения повторного согласования сеанса с удаленным узлом</span><span class="sxs-lookup"><span data-stu-id="3d147-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="3d147-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="3d147-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="3d147-167">Очистка и сброс сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="3d147-169">Отправка данных через сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="3d147-171">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения сервера TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="3d147-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="3d147-173">Анализ расширения указания имени сервера (SNI), полученного от клиента TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="3d147-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="3d147-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="3d147-175">Установка DNS-имени расширения указания имени сервера (SNI) для отправки на удаленный сервер</span><span class="sxs-lookup"><span data-stu-id="3d147-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="3d147-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="3d147-177">Запуск сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="3d147-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="3d147-179">Назначение функции метки времени в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="3d147-181">Добавление доверенного сертификата в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="3d147-183">Удаление доверенного сертификата из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="3d147-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="3d147-185">Инициализация сертификата X.509 для NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="3d147-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="3d147-187">Проверка DNS-имени на соответствие сертификату X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="3d147-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="3d147-189">Проверка сертификата X.509 на соответствие заданному списку отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="3d147-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="3d147-191">Инициализация структуры DNS-имени X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="3d147-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="3d147-193">Поиск и анализ расширения расширенного использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="3d147-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="3d147-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="3d147-195">Поиск и возврат расширения X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="3d147-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="3d147-197">Поиск и анализ расширения использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="3d147-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="3d147-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="3d147-199">Выполнение самостоятельного тестирования для методов шифрования</span><span class="sxs-lookup"><span data-stu-id="3d147-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="3d147-201">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-201">Description</span></span>

<span data-ttu-id="3d147-202">Эта служба выполняет самостоятельное тестирование методов шифрования для проверки.</span><span class="sxs-lookup"><span data-stu-id="3d147-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="3d147-203">Самостоятельное тестирование доступно только в том случае, если библиотека NetX Secure создана с определенным символом NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK.</span><span class="sxs-lookup"><span data-stu-id="3d147-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="3d147-204">Для каждого поддерживаемого метода шифрования самостоятельное тестирование предоставляет предварительно определенные входные данные и проверяет их на соответствие предварительно определенному ожидаемому значению.</span><span class="sxs-lookup"><span data-stu-id="3d147-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="3d147-205">Самостоятельное тестирование шифрования NetX Secure поддерживает следующие алгоритмы и размеры ключей:</span><span class="sxs-lookup"><span data-stu-id="3d147-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="3d147-206">DES: шифрование и расшифровка;</span><span class="sxs-lookup"><span data-stu-id="3d147-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="3d147-207">Triple DES (3DES): шифрование и расшифровка;</span><span class="sxs-lookup"><span data-stu-id="3d147-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="3d147-208">AES: 128-, 192-, 256-битный размер ключа, шифрование и расшифровка в режиме CBC и режиме счетчика;</span><span class="sxs-lookup"><span data-stu-id="3d147-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="3d147-209">HMAC-MD5: проверка подлинности и вычисление хэша;</span><span class="sxs-lookup"><span data-stu-id="3d147-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="3d147-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, проверка подлинности и вычисление хэша;</span><span class="sxs-lookup"><span data-stu-id="3d147-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="3d147-211">MD5: проверка подлинности;</span><span class="sxs-lookup"><span data-stu-id="3d147-211">MD5: authentication</span></span>
- <span data-ttu-id="3d147-212">псевдослучайная функция (PRF): PRF_HMAC_SHA1 и PRF_HMAC_SHA2-256;</span><span class="sxs-lookup"><span data-stu-id="3d147-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="3d147-213">RSA: 1024-, 2048-, 4096-битная операция модуля питания RSA;</span><span class="sxs-lookup"><span data-stu-id="3d147-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="3d147-214">SHA: проверка подлинности SHA1 (96- и 160-битная), SHA2 (256-, 384-, 512-битная).</span><span class="sxs-lookup"><span data-stu-id="3d147-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="3d147-215">Эта функция имеет встроенные векторы для алгоритмов шифрования, перечисленных выше.</span><span class="sxs-lookup"><span data-stu-id="3d147-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="3d147-216">Однако она проверяет только алгоритмы, перечисленные в параметре *cipher_table*, переданном в эту функцию.</span><span class="sxs-lookup"><span data-stu-id="3d147-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="3d147-217">Например, для сеанса TLS используется только набор шифров TLS_RSA_WITH_AES_128_CBC_SHA. Эта функция выполняет самостоятельное тестирование в RSA (1024-, 2048-, 4096-битные), AES-CBC (128-битный) и SHA1.</span><span class="sxs-lookup"><span data-stu-id="3d147-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-218">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-218">Parameters</span></span>

- <span data-ttu-id="3d147-219">**crypto_table** — указатель на таблицу шифрования, используемую сеансом TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="3d147-220">Это тот же параметр crypto_table, который передается в вызов **_nx_secure_tls_session_create()_**.</span><span class="sxs-lookup"><span data-stu-id="3d147-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="3d147-221">**metadata** — указатель на пространство для области метаданных шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d147-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="3d147-222">.</span><span class="sxs-lookup"><span data-stu-id="3d147-222">.</span></span>
- <span data-ttu-id="3d147-223">**metadata_size** — размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="3d147-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-224">Return Values</span></span>

- <span data-ttu-id="3d147-225">**NX_SECURE_TLS_SUCCESS** (0x00) — предоставленные методы шифрования успешно протестированы.</span><span class="sxs-lookup"><span data-stu-id="3d147-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="3d147-226">**NX_PTR_ERROR** (0x07) — недопустимая структура метода шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d147-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="3d147-227">**NX_NOT_SUCCESSFUL** (0x43) — сбой самостоятельного тестирования шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d147-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-228">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-228">Allowed From</span></span>

<span data-ttu-id="3d147-229">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-230">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="3d147-231">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-231">See Also</span></span>

- <span data-ttu-id="3d147-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="3d147-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="3d147-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="3d147-234">Вычисление хэш-значения с помощью пользовательской хэш-функции</span><span class="sxs-lookup"><span data-stu-id="3d147-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-235">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="3d147-236">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-236">Description</span></span>

<span data-ttu-id="3d147-237">Эта функция вычисляет хэш-значение потока данных в указанной области памяти, используя указанный метод шифрования HMAC и строку ключа.</span><span class="sxs-lookup"><span data-stu-id="3d147-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="3d147-238">Функция вычисления хэша модуля доступна, только если библиотека NetX Secure создана со следующим определяемым символом: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="3d147-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-239">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-239">Parameters</span></span>

- <span data-ttu-id="3d147-240">**hmac_ptr** — указатель на метод шифрования HMAC, используемый для вычисления хэш-значения.</span><span class="sxs-lookup"><span data-stu-id="3d147-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="3d147-241">**start_address** — начальный адрес буфера данных.</span><span class="sxs-lookup"><span data-stu-id="3d147-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="3d147-242">**end_address** — конечный адрес буфера данных.</span><span class="sxs-lookup"><span data-stu-id="3d147-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="3d147-243">Обратите внимание, что вычисление хэша не распространяется на данные, расположенные по этому адресу end_address.</span><span class="sxs-lookup"><span data-stu-id="3d147-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="3d147-244">**key** — строка ключа, используемая в вычислении HMAC.</span><span class="sxs-lookup"><span data-stu-id="3d147-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="3d147-245">**key_length** — размер строки ключа в байтах.</span><span class="sxs-lookup"><span data-stu-id="3d147-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="3d147-246">**metadata** — указатель на пространство, используемое алгоритмом HMAC.</span><span class="sxs-lookup"><span data-stu-id="3d147-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="3d147-247">**metadata_size** — размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="3d147-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="3d147-248">**output_buffer** — место в памяти, где хранятся выходные данные хэша.</span><span class="sxs-lookup"><span data-stu-id="3d147-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="3d147-249">**output_buffer_size** — доступное место в буфере вывода в байтах.</span><span class="sxs-lookup"><span data-stu-id="3d147-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="3d147-250">**actual_size** — параметр, возвращаемый функцией, которая указывает фактическое число байтов, записываемых в параметр output_buffer.</span><span class="sxs-lookup"><span data-stu-id="3d147-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-251">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-251">Return Values</span></span>

- <span data-ttu-id="3d147-252">**0** — вычисление хэш-значения успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="3d147-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="3d147-253">**1** — не удалось выполнить вычисление хэша.</span><span class="sxs-lookup"><span data-stu-id="3d147-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-254">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-254">Allowed From</span></span>

<span data-ttu-id="3d147-255">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-256">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="3d147-257">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-257">See Also</span></span>

- <span data-ttu-id="3d147-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="3d147-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="3d147-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="3d147-260">Установка активного сертификата удостоверения для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-261">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="3d147-262">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-262">Description</span></span>

<span data-ttu-id="3d147-263">Эта служба должна вызываться из обратного вызова сеанса (см. nx_secure_tls_session_client_callback_set и nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="3d147-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="3d147-264">При вызове с ранее инициализированной структурой NX_SECURE_X509_CERT этот сертификат будет использоваться вместо сертификата удостоверения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3d147-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="3d147-265">В большинстве случаев сертификат необходимо добавить в локальное хранилище (см. nx_secure_tls_local_certificate_add), иначе подтверждение TLS может завершиться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="3d147-266">Эта служба предназначена для того, чтобы протокол TLS поддерживал несколько сертификатов удостоверений.</span><span class="sxs-lookup"><span data-stu-id="3d147-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="3d147-267">Это полезно для сервера TLS, который обслуживает несколько сетевых адресов, чтобы сервер мог выбрать соответствующий сертификат для удаленного клиента в зависимости от точки входа клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="3d147-268">В клиенте TLS эту подпрограмму можно использовать для изменения сертификата, отправленного на удаленный сервер во время выполнения, после идентификации сервера в подтверждении TLS (это происходит реже, чем в случае использования сервера TLS).</span><span class="sxs-lookup"><span data-stu-id="3d147-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="3d147-269">Если несколько сертификатов могут совместно использовать одно и то же различающееся имя X.509, их необходимо добавить с использованием параметра nx_secure_tls_server_certificate_add, который представляет числовой идентификатор, отделенный от сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-270">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-270">Parameters</span></span>

- <span data-ttu-id="3d147-271">**session_ptr** — указатель на экземпляр сеанса TLS, переданный в обратный вызов сеанса.</span><span class="sxs-lookup"><span data-stu-id="3d147-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="3d147-272">**certificate** — указатель на инициализированный сертификат X.509, который будет использоваться в текущем сеансе.</span><span class="sxs-lookup"><span data-stu-id="3d147-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-273">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-273">Return Values</span></span>

- <span data-ttu-id="3d147-274">**NX_SUCCESS** (0x00) — сертификат успешно назначен сеансу.</span><span class="sxs-lookup"><span data-stu-id="3d147-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="3d147-275">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-276">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-276">Allowed From</span></span>

<span data-ttu-id="3d147-277">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-278">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-279">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-279">See Also</span></span>

- <span data-ttu-id="3d147-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="3d147-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="3d147-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="3d147-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="3d147-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="3d147-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="3d147-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="3d147-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="3d147-288">Установка общего ключа для сеанса клиента NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-289">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="3d147-290">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-290">Description</span></span>

<span data-ttu-id="3d147-291">Эта служба добавляет общий ключ (PSK), строку идентификатора и указание удостоверения в блок управления сеансом TLS и задает использование этого PSK в последующих подключениях клиентов TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="3d147-292">Если включены и используются наборы шифров PSK, то вместо цифрового сертификата используется PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="3d147-293">В этом случае PSK связывается с конкретным удаленным сервером TLS, с которым клиент TLS будет обмениваться данными.</span><span class="sxs-lookup"><span data-stu-id="3d147-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="3d147-294">PSK, заданный через этот API, будет предоставляться узлу удаленного сервера TLS во время следующего подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-295">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-295">Parameters</span></span>

- <span data-ttu-id="3d147-296">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-297">**pre_shared_key** — фактическое значение PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="3d147-298">**psk_length** — длина значения PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="3d147-299">**psk_identity** — строка, используемая для идентификации этого значения PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="3d147-300">**identity_length** — длина удостоверения PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="3d147-301">**hint** — строка, используемая для указания группы ключей PSK, из которой необходимо выбрать ключ на сервере TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="3d147-302">**hint_length** — длина строки указания.</span><span class="sxs-lookup"><span data-stu-id="3d147-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-303">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-303">Return Values</span></span>

- <span data-ttu-id="3d147-304">**NX_SUCCESS** (0x00) — успешное добавление PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="3d147-305">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) — невозможно добавить еще один PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-307">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-307">Allowed From</span></span>

<span data-ttu-id="3d147-308">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-309">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-310">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-310">See Also</span></span>

- <span data-ttu-id="3d147-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="3d147-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="3d147-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="3d147-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="3d147-317">Инициализация модуля NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-318">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="3d147-319">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-319">Description</span></span>

<span data-ttu-id="3d147-320">Эта служба инициализирует модуль NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="3d147-321">Его необходимо вызвать до доступа к другим службам NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="3d147-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-322">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-322">Parameters</span></span>

<span data-ttu-id="3d147-323">None</span><span class="sxs-lookup"><span data-stu-id="3d147-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-324">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-324">Return Values</span></span>

<span data-ttu-id="3d147-325">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-326">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-326">Allowed From</span></span>

<span data-ttu-id="3d147-327">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-328">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="3d147-329">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-329">See Also</span></span>

- <span data-ttu-id="3d147-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="3d147-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="3d147-332">Добавление локального сертификата в сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-333">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-334">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-334">Description</span></span>

<span data-ttu-id="3d147-335">Эта служба добавляет инициализированный экземпляр структуры NX_SECURE_X509_CERT в локальное хранилище сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="3d147-336">Этот сертификат может использоваться стеком TLS для идентификации устройства во время подтверждения TLS (если оно было помечено как сертификат удостоверения во время инициализации структуры сертификата с помощью nx_secure_x509_certificate_initialize) или в качестве издателя в составе цепочки сертификатов, предоставленной удаленному узлу во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="3d147-337">Если требуется несколько локальных сертификатов с одинаковым общим именем, их можно добавить с помощью службы *nx_secure_tls_server_certificate_add* (см. предупреждение ниже).</span><span class="sxs-lookup"><span data-stu-id="3d147-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="3d147-338">Сертификат **требуется** для режима сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="3d147-339">Для режима клиента TLS сертификат *необязателен*.</span><span class="sxs-lookup"><span data-stu-id="3d147-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-340">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.</span><span class="sxs-lookup"><span data-stu-id="3d147-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-341">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-341">Parameters</span></span>

- <span data-ttu-id="3d147-342">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-343">**certificate_ptr** — указатель на инициализированный экземпляр сертификата TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-344">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-344">Return Values</span></span>

- <span data-ttu-id="3d147-345">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="3d147-346">**NX_INVALID_PARAMETERS** (0x4D) — выполнена попытка добавления недопустимого сертификата или дубликата сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="3d147-347">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-348">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-348">Allowed From</span></span>

<span data-ttu-id="3d147-349">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-350">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-351">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-351">See Also</span></span>

- <span data-ttu-id="3d147-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="3d147-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="3d147-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="3d147-358">Поиск локального сертификата в сеансе NetX Secure TLS по общему имени</span><span class="sxs-lookup"><span data-stu-id="3d147-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-359">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="3d147-360">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-360">Description</span></span>

<span data-ttu-id="3d147-361">Эта служба находит сертификат в хранилище сертификатов локального устройства в сеансе TLS и возвращает указатель на структуру NX_SECURE_X509_CERT в хранилище.</span><span class="sxs-lookup"><span data-stu-id="3d147-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="3d147-362">Параметр common_name и его длина (name_length) используются для обнаружения сертификата в хранилище путем сопоставления поля общего имени субъекта X.509 сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="3d147-363">При наличии нескольких сертификатов с одним общим именем будет возвращен только первый из них. Используйте *nx_secure_tls_server_certificate_find*.</span><span class="sxs-lookup"><span data-stu-id="3d147-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-364">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.</span><span class="sxs-lookup"><span data-stu-id="3d147-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-365">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-365">Parameters</span></span>

- <span data-ttu-id="3d147-366">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-367">**certificate** — возврат указателя на сопоставленный сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="3d147-368">**common_name** — строка общего имени для сопоставления (DNS-имя).</span><span class="sxs-lookup"><span data-stu-id="3d147-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="3d147-369">**name_length** — длина строковых данных параметра common_name.</span><span class="sxs-lookup"><span data-stu-id="3d147-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-370">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-370">Return Values</span></span>

- <span data-ttu-id="3d147-371">**NX_SUCCESS** (0x00) — сертификат найден, а указатель возвращен в параметре certificate.</span><span class="sxs-lookup"><span data-stu-id="3d147-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="3d147-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат с указанным общим именем не найден.</span><span class="sxs-lookup"><span data-stu-id="3d147-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="3d147-373">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS, указатель сертификата или строка общего имени.</span><span class="sxs-lookup"><span data-stu-id="3d147-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-374">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-374">Allowed From</span></span>

<span data-ttu-id="3d147-375">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-376">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="3d147-377">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-377">See Also</span></span>

- <span data-ttu-id="3d147-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="3d147-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="3d147-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="3d147-384">Удалить локальный сертификат из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-385">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="3d147-386">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-386">Description</span></span>

<span data-ttu-id="3d147-387">Эта служба удаляет экземпляр локального сертификата из сеанса TLS, введенный в поле общего имени сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-388">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.</span><span class="sxs-lookup"><span data-stu-id="3d147-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-389">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-389">Parameters</span></span>

- <span data-ttu-id="3d147-390">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-391">**common_name** — значение общего имени удаляемого сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="3d147-392">**common_name_length** — длина строки общего имени.</span><span class="sxs-lookup"><span data-stu-id="3d147-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-393">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-393">Return Values</span></span>

- <span data-ttu-id="3d147-394">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="3d147-395">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат не найден.</span><span class="sxs-lookup"><span data-stu-id="3d147-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-397">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-397">Allowed From</span></span>

<span data-ttu-id="3d147-398">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-399">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-400">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-400">See Also</span></span>

- <span data-ttu-id="3d147-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="3d147-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="3d147-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="3d147-406">Вычисление размера криптографических метаданных для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-407">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="3d147-408">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-408">Description</span></span>

<span data-ttu-id="3d147-409">Эта служба вычисляет и возвращает размер криптографических метаданных, необходимых для конкретного сеанса TLS и таблицы шифрования TLS (дополнительные сведения о таблице криптографических шифров см. в разделе «Инициализация TLS с помощью методов шифрования»).</span><span class="sxs-lookup"><span data-stu-id="3d147-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="3d147-410">Эту службу следует вызывать вместе с необходимой криптографической таблицей для вычисления размера буфера метаданных, переданного в nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="3d147-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-411">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-411">Parameters</span></span>

- <span data-ttu-id="3d147-412">**crypto_table** — указатель на заполненную таблицу шифрования NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="3d147-413">**metadata_size** — выходные данные вычисления размера в байтах.</span><span class="sxs-lookup"><span data-stu-id="3d147-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-414">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-414">Return Values</span></span>

- <span data-ttu-id="3d147-415">**NX_SUCCESS** (0x00) — вычисление размера метаданных выполнено успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="3d147-416">**NX_PTR_ERROR** (0x07) — недопустимая таблица шифрования или указатель на возвращаемый размер.</span><span class="sxs-lookup"><span data-stu-id="3d147-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-417">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-417">Allowed From</span></span>

<span data-ttu-id="3d147-418">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-419">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-420">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-420">See Also</span></span>

- <span data-ttu-id="3d147-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="3d147-422">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="3d147-422">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="3d147-423">Вычисление хэш-значения подпрограмм библиотеки NetX Secure</span><span class="sxs-lookup"><span data-stu-id="3d147-423">Compute the hash value of the NetX Secure library routines</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-424">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-424">Prototype</span></span>

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a><span data-ttu-id="3d147-425">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-425">Description</span></span>

<span data-ttu-id="3d147-426">Эта служба инициализирует модуль NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-426">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="3d147-427">Его необходимо вызвать до доступа к другим службам NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="3d147-427">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-428">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-428">Parameters</span></span>

<span data-ttu-id="3d147-429">None</span><span class="sxs-lookup"><span data-stu-id="3d147-429">None</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-430">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-430">Return Values</span></span>

<span data-ttu-id="3d147-431">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-431">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-432">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-432">Allowed From</span></span>

<span data-ttu-id="3d147-433">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-433">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-434">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-434">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="3d147-435">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-435">See Also</span></span>

- <span data-ttu-id="3d147-436">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-436">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="3d147-437">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-437">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="3d147-438">Выделение пакета для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-438">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-439">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-439">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="3d147-440">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-440">Description</span></span>

<span data-ttu-id="3d147-441">Эта служба выделяет пакет NX_PACKET для указанного активного сеанса TLS из заданного пула NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="3d147-441">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="3d147-442">Приложение должно вызывать эту службу для выделения пакетов данных, которые отправляют через подключение TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-442">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="3d147-443">Перед вызовом этой службы необходимо инициализировать сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-443">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="3d147-444">Выделенный пакет инициализируется таким образом, чтобы после заполнения данных пакета можно было добавить данные верхнего и нижнего колонтитулов TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-444">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="3d147-445">В противном случае поведение идентично службе *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="3d147-445">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-446">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-446">Parameters</span></span>

- <span data-ttu-id="3d147-447">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-447">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-448">**pool_ptr** — указатель на пул NX_PACKET_POOL, из которого выделяется пакет.</span><span class="sxs-lookup"><span data-stu-id="3d147-448">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="3d147-449">**packet_ptr** — указатель вывода на вновь выделенный пакет.</span><span class="sxs-lookup"><span data-stu-id="3d147-449">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="3d147-450">**wait_option** — параметр приостановки выделения пакетов.</span><span class="sxs-lookup"><span data-stu-id="3d147-450">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-451">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-451">Return Values</span></span>

- <span data-ttu-id="3d147-452">**NX_SUCCESS** (0x00) — пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-452">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="3d147-453">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить базовый пакет.</span><span class="sxs-lookup"><span data-stu-id="3d147-453">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="3d147-454">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-454">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-455">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-455">Allowed From</span></span>

<span data-ttu-id="3d147-456">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-457">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-457">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-458">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-458">See Also</span></span>

- <span data-ttu-id="3d147-459">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-459">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="3d147-460">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-460">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-461">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-461">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-462">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-462">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-463">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-463">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-464">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-464">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-465">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-465">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-466">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-466">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="3d147-467">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-467">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="3d147-468">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="3d147-468">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="3d147-469">Добавление общего ключа в сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-469">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-470">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-470">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="3d147-471">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-471">Description</span></span>

<span data-ttu-id="3d147-472">Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сеансом TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-472">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="3d147-473">Если включены и используются наборы шифров PSK, то вместо цифрового сертификата используется PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-473">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-474">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-474">Parameters</span></span>

- <span data-ttu-id="3d147-475">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-475">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-476">**pre_shared_key** — фактическое значение PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-476">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="3d147-477">**psk_length** — длина значения PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-477">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="3d147-478">**psk_identity** — строка, используемая для идентификации этого значения PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-478">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="3d147-479">**identity_length** — длина удостоверения PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-479">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="3d147-480">**hint** — строка, используемая для указания группы ключей PSK, из которой необходимо выбрать ключ на сервере TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-480">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="3d147-481">**hint_length** — длина строки указания.</span><span class="sxs-lookup"><span data-stu-id="3d147-481">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-482">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-482">Return Values</span></span>

- <span data-ttu-id="3d147-483">**NX_SUCCESS** (0x00) — успешное добавление PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-483">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="3d147-484">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-484">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-485">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) — невозможно добавить еще один PSK.</span><span class="sxs-lookup"><span data-stu-id="3d147-485">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-486">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-486">Allowed From</span></span>

<span data-ttu-id="3d147-487">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-488">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-488">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-489">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-489">See Also</span></span>

- <span data-ttu-id="3d147-490">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="3d147-490">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="3d147-491">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-491">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-492">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-492">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-493">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-493">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-494">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-494">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="3d147-495">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-495">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="3d147-496">Выделение пространства для сертификата, предоставленного удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-496">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-497">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-497">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="3d147-498">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-498">Description</span></span>

<span data-ttu-id="3d147-499">Эта служба добавляет неинициализированный экземпляр структуры NX_SECURE_X509_CERT в сеанс TLS с целью выделения места для сертификатов, которые предоставляет удаленный узел во время сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-499">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="3d147-500">Данные удаленного сертификата анализируются с помощью NetX Secure TLS. Эти сведения затем используют для заполнения экземпляра структуры сертификата, предоставленного в эту функцию.</span><span class="sxs-lookup"><span data-stu-id="3d147-500">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="3d147-501">Сертификаты, добавленные таким способом, помещаются в связанный список.</span><span class="sxs-lookup"><span data-stu-id="3d147-501">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="3d147-502">Если предполагается, что удаленный узел предоставит несколько сертификатов, эту функцию следует вызывать повторно, чтобы выделить место для всех сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-502">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="3d147-503">Дополнительные сертификаты добавляются в конец связанного списка сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-503">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="3d147-504">Сбой выделения удаленного сертификата приведет к сбою режима клиента TLS во время подтверждения TLS, если не используется набор шифров для общего ключа (PSK).</span><span class="sxs-lookup"><span data-stu-id="3d147-504">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="3d147-505">Параметр *raw_certificate_buffer* указывает на место, выделенное для хранения входящего удаленного сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-505">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="3d147-506">Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов.</span><span class="sxs-lookup"><span data-stu-id="3d147-506">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="3d147-507">Буфер должен быть достаточно большим, чтобы вместить этот размер, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше.</span><span class="sxs-lookup"><span data-stu-id="3d147-507">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="3d147-508">Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-508">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="3d147-509">Для режима сервера TLS удаленное выделение сертификатов требуется только в том случае, если включена проверка подлинности с помощью сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-509">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-510">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-510">Parameters</span></span>

- <span data-ttu-id="3d147-511">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-511">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-512">**certificate_ptr** — указатель на неинициализированный экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-512">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="3d147-513">**raw_certificate_buffer** — указатель на буфер для хранения непроанализированного сертификата, полученного с удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-513">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="3d147-514">**buffer_size** — размер необработанного буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-514">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-515">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-515">Return Values</span></span>

- <span data-ttu-id="3d147-516">**NX_SUCCESS** (0x00) — сертификат успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="3d147-516">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="3d147-517">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-517">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-518">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="3d147-518">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="3d147-519">**NX_INVALID_PARAMETERS** (0x4D) — попытка добавить недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-519">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-520">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-520">Allowed From</span></span>

<span data-ttu-id="3d147-521">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-522">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-522">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-523">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-523">See Also</span></span>

- <span data-ttu-id="3d147-524">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="3d147-524">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="3d147-525">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-525">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="3d147-526">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-526">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="3d147-527">Выделение пространства для всех сертификатов, предоставленных удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-527">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-528">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-528">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="3d147-529">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-529">Description</span></span>

<span data-ttu-id="3d147-530">Эта служба выделяет место для обработки входящих цепочек сертификатов с удаленных узлов сервера для выполнения проверки подлинности X.509 и проверки в экземпляре клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-530">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="3d147-531">Для режима сервера TLS удаленное выделение сертификатов требуется только в том случае, если включена проверка подлинности клиента X.509. Для экземпляров сервера TLS следует использовать службу *nx_secure_tls_session_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="3d147-531">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="3d147-532">Сбой выделения удаленных сертификатов приведет к сбою режима клиента TLS во время подтверждения TLS, если не используется набор шифров для общего ключа (PSK).</span><span class="sxs-lookup"><span data-stu-id="3d147-532">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="3d147-533">Параметр *certificate_buffer* указывает на место, выделенное для хранения входящих удаленных сертификатов и блоков управления, необходимых для этих сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-533">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="3d147-534">Буфер будет разделен по количеству сертификатов (*certs_number*) на равные части для каждого сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-534">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="3d147-535">Параметр *buffer_size* указывает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="3d147-535">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="3d147-536">Необходимый объем пространства можно вычислить по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="3d147-536">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="3d147-537">Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов.</span><span class="sxs-lookup"><span data-stu-id="3d147-537">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="3d147-538">Буфер должен быть достаточно большим, чтобы вместить этот размер для каждого сертификата, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше.</span><span class="sxs-lookup"><span data-stu-id="3d147-538">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="3d147-539">Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-539">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-540">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-540">Parameters</span></span>

- <span data-ttu-id="3d147-541">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-541">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="3d147-542">**certs_number** — количество сертификатов, выделенных из предоставленного буфера.</span><span class="sxs-lookup"><span data-stu-id="3d147-542">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="3d147-543">**certificate_buffer** — указатель на буфер для хранения сертификатов, полученных с удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-543">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="3d147-544">**buffer_size** — размер буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-544">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-545">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-545">Return Values</span></span>

- <span data-ttu-id="3d147-546">**NX_SUCCESS** (0x00) — сертификат успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="3d147-546">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="3d147-547">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель буфера.</span><span class="sxs-lookup"><span data-stu-id="3d147-547">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="3d147-548">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="3d147-548">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="3d147-549">**NX_INVALID_PARAMETERS** (0x4D) — буфер слишком мал, чтобы вместить необходимое количество сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-549">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-550">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-550">Allowed From</span></span>

<span data-ttu-id="3d147-551">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-551">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-552">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-552">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-553">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-553">See Also</span></span>

- <span data-ttu-id="3d147-554">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-554">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-555">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-555">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="3d147-556">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="3d147-556">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="3d147-557">Освобождение места, выделенного для входящих сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-557">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-558">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-558">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-559">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-559">Description</span></span>

<span data-ttu-id="3d147-560">Эта служба используется для высвобождения всех буферов сертификатов, выделенных для определенного сеанса TLS з помощью nx_secure_tls_remote_certificate_allocated, путем их возврата в свободное место на этом сеансе.</span><span class="sxs-lookup"><span data-stu-id="3d147-560">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="3d147-561">Это может быть необходимо, если приложение повторно использует объект сеанса TLS без удаления и повторного создания этого объекта с помощью nx_secure_tls_session_delete и nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="3d147-561">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="3d147-562">Обратите внимание, что удаленное пространство сертификатов автоматически восстанавливается при сбросе сеанса TLS, как это происходит в nx_secure_tls_session_end, поэтому большинству приложений не требуется вызывать эту службу.</span><span class="sxs-lookup"><span data-stu-id="3d147-562">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-563">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-563">Parameters</span></span>

- <span data-ttu-id="3d147-564">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-564">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-565">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-565">Return Values</span></span>

- <span data-ttu-id="3d147-566">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-566">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="3d147-567">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-567">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-568">**NX_INVALID_PARAMETERS** (0x4D) — внутренняя ошибка — вероятное повреждение хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-568">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-569">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-569">Allowed From</span></span>

<span data-ttu-id="3d147-570">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-571">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-571">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="3d147-572">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-572">See Also</span></span>

- <span data-ttu-id="3d147-573">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-573">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-574">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-574">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-575">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-575">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-576">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-576">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="3d147-577">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-577">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="3d147-578">Добавление сертификата специально для серверов TLS с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="3d147-578">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-579">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-579">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="3d147-580">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-580">Description</span></span>

<span data-ttu-id="3d147-581">Эта служба используется для добавления сертификата в локальное хранилище сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.</span><span class="sxs-lookup"><span data-stu-id="3d147-581">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="3d147-582">Числовой идентификатор не зависит от сертификата и позволяет добавлять на сервер TLS несколько сертификатов в качестве сертификатов удостоверений, а также позволяет добавлять несколько сертификатов с одинаковым общим именем в одно и то же локальное хранилище сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-582">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="3d147-583">Эту же службу можно использовать для сертификатов клиента, но в клиенте TLS крайне редко бывает несколько сертификатов удостоверений.</span><span class="sxs-lookup"><span data-stu-id="3d147-583">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="3d147-584">Параметр cert_id — это ненулевое положительное целое число, которое назначает приложение.</span><span class="sxs-lookup"><span data-stu-id="3d147-584">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="3d147-585">Фактическое значение не играет роли (кроме нуля), но оно должно быть уникальным в хранилище для указанного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-585">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="3d147-586">Значение cert_id можно использовать для поиска и удаления сертификатов из локального хранилища с помощью nx_secure_tls_server_certificate_find и nx_secure_tls_server_certificate_remove соответственно.</span><span class="sxs-lookup"><span data-stu-id="3d147-586">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-587">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_local_certificate_add. API nx_secure_tls_server_certificate_add использует уникальный числовой идентификатор для каждого сертификата и локальный индекс служб сертификатов на основе общего имени X.509. Службы сертификатов сервера позволяют хранить несколько сертификатов с общими данными (особенно общим именем) в одном локальном хранилище — это полезно для сервера с несколькими удостоверениями.*</span><span class="sxs-lookup"><span data-stu-id="3d147-587">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-588">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-588">Parameters</span></span>

- <span data-ttu-id="3d147-589">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-589">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-590">**certificate** — указатель на инициализированный ранее экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-590">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="3d147-591">**cert_id** — положительный, ненулевой, сравнительно уникальный код сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-591">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-592">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-592">Return Values</span></span>

- <span data-ttu-id="3d147-593">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-593">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="3d147-594">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-594">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="3d147-595">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) — указанный идентификатор сертификата имел недопустимое значение (скорее всего 0).</span><span class="sxs-lookup"><span data-stu-id="3d147-595">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="3d147-596">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) — указанный идентификатор сертификата уже есть в локальном хранилище.</span><span class="sxs-lookup"><span data-stu-id="3d147-596">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="3d147-597">**NX_INVALID_PARAMETERS** (0x4D) — внутренняя ошибка — вероятное повреждение хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-597">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-598">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-598">Allowed From</span></span>

<span data-ttu-id="3d147-599">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-600">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-600">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-601">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-601">See Also</span></span>

- <span data-ttu-id="3d147-602">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-602">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-603">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-603">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="3d147-604">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-604">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="3d147-605">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-605">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="3d147-606">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-606">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="3d147-607">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-607">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="3d147-608">Поиск сертификата по числовому идентификатору</span><span class="sxs-lookup"><span data-stu-id="3d147-608">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-609">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-609">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="3d147-610">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-610">Description</span></span>

<span data-ttu-id="3d147-611">Эта служба используется для поиска сертификата в локальном хранилище сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.</span><span class="sxs-lookup"><span data-stu-id="3d147-611">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="3d147-612">Параметр cert_id — ненулевое положительное целое число, которое назначает приложение при добавлении сертификата в локальное хранилище сеанса TLS с помощью nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="3d147-612">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-613">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_local_certificate_add. API nx_secure_tls_server_certificate_add использует уникальный числовой идентификатор для каждого сертификата и локальный индекс служб сертификатов на основе общего имени X.509. Службы сертификатов сервера позволяют хранить несколько сертификатов с общими данными (особенно общим именем) в одном локальном хранилище — это полезно для сервера с несколькими удостоверениями.*</span><span class="sxs-lookup"><span data-stu-id="3d147-613">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-614">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-614">Parameters</span></span>

- <span data-ttu-id="3d147-615">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-615">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-616">**certificate** — указатель на указатель сертификата X.509 для возврата ссылки на найденный сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-616">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="3d147-617">**cert_id** — ненулевое положительное значение идентификатора сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-617">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-618">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-618">Return Values</span></span>

- <span data-ttu-id="3d147-619">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-619">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="3d147-620">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-620">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="3d147-621">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — указанный идентификатор сертификата не соответствует ни одному из локальных хранилищ указанного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-621">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-622">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-622">Allowed From</span></span>

<span data-ttu-id="3d147-623">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-623">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-624">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-624">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-625">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-625">See Also</span></span>

- <span data-ttu-id="3d147-626">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-626">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-627">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-627">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="3d147-628">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-628">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="3d147-629">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-629">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="3d147-630">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-630">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="3d147-631">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-631">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="3d147-632">Удаление сертификата локального сервера с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="3d147-632">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-633">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-633">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="3d147-634">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-634">Description</span></span>

<span data-ttu-id="3d147-635">Эта служба используется для удаления сертификата из локального хранилища сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.</span><span class="sxs-lookup"><span data-stu-id="3d147-635">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="3d147-636">Параметр cert_id — ненулевое положительное целое число, которое назначает приложение при добавлении сертификата в локальное хранилище сеанса TLS с помощью nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="3d147-636">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-637">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-637">Parameters</span></span>

- <span data-ttu-id="3d147-638">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-638">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-639">**cert_id** — ненулевое положительное значение идентификатора сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-639">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-640">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-640">Return Values</span></span>

- <span data-ttu-id="3d147-641">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-641">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="3d147-642">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-642">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="3d147-643">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — указанный идентификатор сертификата не соответствует ни одному из локальных хранилищ указанного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-643">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-644">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-644">Allowed From</span></span>

<span data-ttu-id="3d147-645">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-645">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-646">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-646">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-647">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-647">See Also</span></span>

- <span data-ttu-id="3d147-648">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-648">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-649">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-649">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="3d147-650">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-650">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="3d147-651">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-651">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="3d147-652">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-652">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="3d147-653">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="3d147-653">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="3d147-654">Получение значения и уровня оповещения TLS, отправленного удаленным узлом</span><span class="sxs-lookup"><span data-stu-id="3d147-654">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-655">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-655">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="3d147-656">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-656">Description</span></span>

<span data-ttu-id="3d147-657">Эта служба используется для получения уровня и значения оповещения TLS, когда удаленный узел отправляет оповещение в ответ на какую-либо проблему или ошибку.</span><span class="sxs-lookup"><span data-stu-id="3d147-657">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="3d147-658">Значения параметров alert_level и alert_value допустимы только в том случае, если эта функция вызывается сразу после вызова API TLS, который вернул состояние NX_SECURE_TLS_ALERT_RECEIVED (0x114), указывающее на то, что оповещение получено из удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-658">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="3d147-659">Обратите внимание, что если TLS на локальном узле отправляет оповещение, полученные коды ошибок содержат намного больше полезной информации по фактической ошибке, чем само оповещение TLS, так как значения оповещений TLS преднамеренно оставлены неоднозначными для предотвращения определенных типов атак (например, атака типа padding oracle или подобные).</span><span class="sxs-lookup"><span data-stu-id="3d147-659">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="3d147-660">Уровень оповещения принимает одно из двух значений: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) или NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="3d147-660">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="3d147-661">Как правило, только оповещение CloseNotify (используемое для указания успешного завершения сеанса TLS) будет иметь уровень "Предупреждение", хотя некоторые ситуации конфигурации расширения также могут считаться предупреждениями.</span><span class="sxs-lookup"><span data-stu-id="3d147-661">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="3d147-662">Подавляющее большинство оповещений будут иметь значение «Неустранимый», что свидетельствует о возможной ошибке безопасности и приведет к немедленному закрытию TLS-подключения (подтверждения или сеанса).</span><span class="sxs-lookup"><span data-stu-id="3d147-662">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="3d147-663">Значения оповещений TLS определены в документах RFC по протоколу TLS. Ниже приведен список из документа RFC 5246 (TLSv1.2) для справки.</span><span class="sxs-lookup"><span data-stu-id="3d147-663">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="3d147-664">Имя предупреждения</span><span class="sxs-lookup"><span data-stu-id="3d147-664">Alert Name</span></span>                     | <span data-ttu-id="3d147-665">Значение</span><span class="sxs-lookup"><span data-stu-id="3d147-665">Value</span></span> | <span data-ttu-id="3d147-666">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-666">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="3d147-667">close_notify</span><span class="sxs-lookup"><span data-stu-id="3d147-667">close_notify</span></span>                  | <span data-ttu-id="3d147-668">0</span><span class="sxs-lookup"><span data-stu-id="3d147-668">0</span></span>     | <span data-ttu-id="3d147-669">Без ошибок, указывает на успешное завершение сеанса</span><span class="sxs-lookup"><span data-stu-id="3d147-669">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="3d147-670">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="3d147-670">unexpected_message</span></span>            | <span data-ttu-id="3d147-671">10</span><span class="sxs-lookup"><span data-stu-id="3d147-671">10</span></span>    | <span data-ttu-id="3d147-672">Протокол TLS получил неожиданное или неупорядоченное сообщение</span><span class="sxs-lookup"><span data-stu-id="3d147-672">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="3d147-673">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="3d147-673">bad_record_mac</span></span>               | <span data-ttu-id="3d147-674">20</span><span class="sxs-lookup"><span data-stu-id="3d147-674">20</span></span>    | <span data-ttu-id="3d147-675">Сбой расшифровки или проверки MAC</span><span class="sxs-lookup"><span data-stu-id="3d147-675">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="3d147-676">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="3d147-676">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="3d147-677">21</span><span class="sxs-lookup"><span data-stu-id="3d147-677">21</span></span>    | <span data-ttu-id="3d147-678">**Не рекомендуется**. Сбой расшифровки (не рекомендуется из-за атак padding oracle)</span><span class="sxs-lookup"><span data-stu-id="3d147-678">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="3d147-679">record_overflow</span><span class="sxs-lookup"><span data-stu-id="3d147-679">record_overflow</span></span>               | <span data-ttu-id="3d147-680">22</span><span class="sxs-lookup"><span data-stu-id="3d147-680">22</span></span>    | <span data-ttu-id="3d147-681">Размер полученной записи превышает максимальный размер записи TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-681">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="3d147-682">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="3d147-682">decompression_failure</span></span>         | <span data-ttu-id="3d147-683">30</span><span class="sxs-lookup"><span data-stu-id="3d147-683">30</span></span>    | <span data-ttu-id="3d147-684">Возникла проблема при сжатии или распаковке записи TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-684">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="3d147-685">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="3d147-685">handshake_failure</span></span>             | <span data-ttu-id="3d147-686">40</span><span class="sxs-lookup"><span data-stu-id="3d147-686">40</span></span>    | <span data-ttu-id="3d147-687">Произошла неопределенная ошибка подтверждения, не связанная с другим оповещением</span><span class="sxs-lookup"><span data-stu-id="3d147-687">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="3d147-688">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="3d147-688">no_certificate_RESERVED</span></span>      | <span data-ttu-id="3d147-689">41</span><span class="sxs-lookup"><span data-stu-id="3d147-689">41</span></span>    | <span data-ttu-id="3d147-690">**Не рекомендуется** в протоколе TLS (только SSL)</span><span class="sxs-lookup"><span data-stu-id="3d147-690">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="3d147-691">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="3d147-691">bad_certificate</span></span>               | <span data-ttu-id="3d147-692">42</span><span class="sxs-lookup"><span data-stu-id="3d147-692">42</span></span>    | <span data-ttu-id="3d147-693">Полученный сертификат содержал недопустимое форматирование или подписи</span><span class="sxs-lookup"><span data-stu-id="3d147-693">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="3d147-694">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="3d147-694">unsupported_certificate</span></span>       | <span data-ttu-id="3d147-695">43</span><span class="sxs-lookup"><span data-stu-id="3d147-695">43</span></span>    | <span data-ttu-id="3d147-696">Получен сертификат недопустимого типа (например, сертификат только для подписи, используемый для проверки подлинности сервера TLS)</span><span class="sxs-lookup"><span data-stu-id="3d147-696">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="3d147-697">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="3d147-697">certificate_revoked</span></span>           | <span data-ttu-id="3d147-698">44</span><span class="sxs-lookup"><span data-stu-id="3d147-698">44</span></span>    | <span data-ttu-id="3d147-699">Состояние сертификата (предоставленное списком отзыва сертификатов или OCSP) указано как "Отозвано"</span><span class="sxs-lookup"><span data-stu-id="3d147-699">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="3d147-700">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="3d147-700">certificate_expired</span></span>           | <span data-ttu-id="3d147-701">45</span><span class="sxs-lookup"><span data-stu-id="3d147-701">45</span></span>    | <span data-ttu-id="3d147-702">Полученный сертификат находится за пределами допустимого диапазона дат (он еще не действителен или устарел)</span><span class="sxs-lookup"><span data-stu-id="3d147-702">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="3d147-703">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="3d147-703">certificate_unknown</span></span>           | <span data-ttu-id="3d147-704">46</span><span class="sxs-lookup"><span data-stu-id="3d147-704">46</span></span>    | <span data-ttu-id="3d147-705">Обнаружена неизвестная ошибка сертификата, которая не относится к другим оповещениям</span><span class="sxs-lookup"><span data-stu-id="3d147-705">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="3d147-706">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="3d147-706">illegal_parameter</span></span>             | <span data-ttu-id="3d147-707">47</span><span class="sxs-lookup"><span data-stu-id="3d147-707">47</span></span>    | <span data-ttu-id="3d147-708">Конфигурация или согласованное значение в подтверждении TLS являются недопустимыми или находятся за пределами диапазона</span><span class="sxs-lookup"><span data-stu-id="3d147-708">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="3d147-709">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="3d147-709">unknown_ca</span></span>                    | <span data-ttu-id="3d147-710">48</span><span class="sxs-lookup"><span data-stu-id="3d147-710">48</span></span>    | <span data-ttu-id="3d147-711">Не удалось отследить полученный сертификат удостоверения через цепочку сертификатов до доверенного корневого сертификата ЦС.</span><span class="sxs-lookup"><span data-stu-id="3d147-711">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="3d147-712">access_denied</span><span class="sxs-lookup"><span data-stu-id="3d147-712">access_denied</span></span>                 | <span data-ttu-id="3d147-713">49</span><span class="sxs-lookup"><span data-stu-id="3d147-713">49</span></span>    | <span data-ttu-id="3d147-714">Указывает, что был получен допустимый сертификат, но контроль доступа к приложениям указал, что для запрашиваемых ресурсов сертификат был недопустимым.</span><span class="sxs-lookup"><span data-stu-id="3d147-714">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="3d147-715">decode_error</span><span class="sxs-lookup"><span data-stu-id="3d147-715">decode_error</span></span>                  | <span data-ttu-id="3d147-716">50</span><span class="sxs-lookup"><span data-stu-id="3d147-716">50</span></span>    | <span data-ttu-id="3d147-717">Поле или значения в сообщении с заголовком или подтверждением TLS находились вне допустимого диапазона или являются недопустимыми, что привело к сбою при декодировании записи TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-717">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="3d147-718">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="3d147-718">decrypt_error</span></span>                 | <span data-ttu-id="3d147-719">51</span><span class="sxs-lookup"><span data-stu-id="3d147-719">51</span></span>    | <span data-ttu-id="3d147-720">Не удалось проверить хэш подписи или сообщения о завершении подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-720">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="3d147-721">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="3d147-721">export_restriction_RESERVED</span></span>  | <span data-ttu-id="3d147-722">60</span><span class="sxs-lookup"><span data-stu-id="3d147-722">60</span></span>    | <span data-ttu-id="3d147-723">Не рекомендуется для версии TLSv1.2</span><span class="sxs-lookup"><span data-stu-id="3d147-723">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="3d147-724">protocol_version</span><span class="sxs-lookup"><span data-stu-id="3d147-724">protocol_version</span></span>              | <span data-ttu-id="3d147-725">70</span><span class="sxs-lookup"><span data-stu-id="3d147-725">70</span></span>    | <span data-ttu-id="3d147-726">Версия протокола TLS, согласованная во время подтверждения, распознана, но не поддерживается (например, если версия TLSv1.0 предоставлена, но не включена).</span><span class="sxs-lookup"><span data-stu-id="3d147-726">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="3d147-727">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="3d147-727">insufficient_security</span></span>         | <span data-ttu-id="3d147-728">71</span><span class="sxs-lookup"><span data-stu-id="3d147-728">71</span></span>    | <span data-ttu-id="3d147-729">Отправляется при сбое подтверждения из-за отсутствия безопасных шифров (например, если размер ключа слишком мал согласно требованиям приложения).</span><span class="sxs-lookup"><span data-stu-id="3d147-729">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="3d147-730">internal_error</span><span class="sxs-lookup"><span data-stu-id="3d147-730">internal_error</span></span>                | <span data-ttu-id="3d147-731">80</span><span class="sxs-lookup"><span data-stu-id="3d147-731">80</span></span>    | <span data-ttu-id="3d147-732">Произошла ошибка, не относящаяся к протоколу TLS (например, проблемы с выделением памяти или проблемы с приложением), что привело к прекращению сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-732">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="3d147-733">user_canceled</span><span class="sxs-lookup"><span data-stu-id="3d147-733">user_canceled</span></span>                 | <span data-ttu-id="3d147-734">90</span><span class="sxs-lookup"><span data-stu-id="3d147-734">90</span></span>    | <span data-ttu-id="3d147-735">Возвращается, если пользователь или приложение отменили сеанс TLS до завершения подтверждения (подобно оповещению CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="3d147-735">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="3d147-736">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="3d147-736">no_renegotiation</span></span>              | <span data-ttu-id="3d147-737">100</span><span class="sxs-lookup"><span data-stu-id="3d147-737">100</span></span>   | <span data-ttu-id="3d147-738">Указывает, что удаленный узел не может выполнить подтверждения повторного согласования TLS в ответ на запрос на повторное согласование.</span><span class="sxs-lookup"><span data-stu-id="3d147-738">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="3d147-739">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="3d147-739">unsupported_extension</span></span>         | <span data-ttu-id="3d147-740">110</span><span class="sxs-lookup"><span data-stu-id="3d147-740">110</span></span>   | <span data-ttu-id="3d147-741">Отправляется, если клиент TLS получает ServerHello с расширениями, которые явным образом не запрашивались в первоначальном ClientHello (что указывает на проблему с сервером).</span><span class="sxs-lookup"><span data-stu-id="3d147-741">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="3d147-742">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-742">Parameters</span></span>

- <span data-ttu-id="3d147-743">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-743">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-744">**alert_level** — возвращает уровень полученного оповещения (предупреждение или неустранимая ошибка).</span><span class="sxs-lookup"><span data-stu-id="3d147-744">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="3d147-745">**alert_value** — возвращает значение полученного оповещения (см. таблицу).</span><span class="sxs-lookup"><span data-stu-id="3d147-745">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-746">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-746">Return Values</span></span>

- <span data-ttu-id="3d147-747">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-747">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="3d147-748">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-748">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-749">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-749">Allowed From</span></span>

<span data-ttu-id="3d147-750">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-750">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-751">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-751">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-752">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-752">See Also</span></span>

- <span data-ttu-id="3d147-753">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-753">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-754">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-754">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-755">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-755">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="3d147-756">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-756">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="3d147-757">Настройка обратного вызова для протокола TLS, который будет использоваться для дополнительной проверки сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-757">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-758">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-758">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="3d147-759">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-759">Description</span></span>

<span data-ttu-id="3d147-760">Эта служба назначает указатель функции на сеанс TLS, который будет вызываться протоколом TLS при получении сертификата с удаленного узла. Таким образом приложение сможет выполнять такие проверки, как проверка DNS, отзыв сертификата и принудительное применение политики сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-760">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="3d147-761">NetX Secure TLS выполняет базовую проверку пути X.509 для сертификата перед выполнением обратного вызова, чтобы убедиться, что сертификат можно отследить до сертификата в хранилище доверенных сертификатов TLS, но все остальные проверки будут обрабатываться этим обратным вызовом.</span><span class="sxs-lookup"><span data-stu-id="3d147-761">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="3d147-762">Обратный вызов предоставляет указатель сеанса TLS и указатель на сертификат удостоверения удаленного узла (конечный объект в цепочке сертификатов).</span><span class="sxs-lookup"><span data-stu-id="3d147-762">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="3d147-763">Обратный вызов должен возвращать значение NX_SUCCESS, если вся проверка прошла успешно. В противном случае он должен вернуть код ошибки, указывающий на сбой проверки.</span><span class="sxs-lookup"><span data-stu-id="3d147-763">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="3d147-764">Любое значение, кроме NX_SUCCESS, приведет к немедленному прерыванию подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-764">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-765">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-765">Parameters</span></span>

- <span data-ttu-id="3d147-766">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-766">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-767">**func_ptr** — указатель на функцию обратного вызова проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-767">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-768">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-768">Return Values</span></span>

- <span data-ttu-id="3d147-769">**NX_SUCCESS** (0x00) — успешное выделение указателя функции.</span><span class="sxs-lookup"><span data-stu-id="3d147-769">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="3d147-770">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-770">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-771">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-771">Allowed From</span></span>

<span data-ttu-id="3d147-772">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-773">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-773">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-774">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-774">See Also</span></span>

- <span data-ttu-id="3d147-775">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-775">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-776">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-776">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="3d147-777">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-777">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="3d147-778">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-778">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="3d147-779">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения клиента TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-779">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-780">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-780">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="3d147-781">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-781">Description</span></span>

<span data-ttu-id="3d147-782">Эта служба назначает указатель функции сеансу TLS, который будет вызывать протокол TLS, если подтверждение клиента TLS получило сообщение ServerHelloDone.</span><span class="sxs-lookup"><span data-stu-id="3d147-782">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="3d147-783">Функция обратного вызова позволяет приложению обрабатывать любые расширения TLS из полученного сообщения ServerHello, для которого необходимо ввести данные или принять решение.</span><span class="sxs-lookup"><span data-stu-id="3d147-783">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="3d147-784">Обратный вызов выполняется с помощью блока управления сеансом TLS и массива объектов NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="3d147-784">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="3d147-785">Массив объектов расширения необходимо передать во вспомогательную функцию, которая найдет и проанализирует определенное расширение.</span><span class="sxs-lookup"><span data-stu-id="3d147-785">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="3d147-786">Сейчас в NetX Secure не поддерживаются специальные расширения, для которых требуются входные данные клиента TLS. Однако разработчикам приложений доступен обратный вызов для обработки пользовательских или новых расширений, которые могут стать доступными.</span><span class="sxs-lookup"><span data-stu-id="3d147-786">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="3d147-787">Пример вспомогательной функции, которая анализирует расширения TLS, предоставленные в сообщениях приветствия, см. на странице *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="3d147-787">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="3d147-788">Обратный вызов клиента также может использоваться для выбора активного сертификата удостоверения с помощью *nx_secure_tls_active_certificate_set* для клиента TLS в случае, если удаленный сервер запросил сертификат и предоставил сведения, позволяющие клиенту TLS выбирать конкретный сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-788">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="3d147-789">Дополнительные сведения см. в справочнике по nx_secure_tls_active_certificate_set.</span><span class="sxs-lookup"><span data-stu-id="3d147-789">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-790">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-790">Parameters</span></span>

- <span data-ttu-id="3d147-791">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-791">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-792">**func_ptr** — указатель на функцию обратного вызова клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-792">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-793">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-793">Return Values</span></span>

- <span data-ttu-id="3d147-794">**NX_SUCCESS** (0x00) — успешное выделение указателя функции.</span><span class="sxs-lookup"><span data-stu-id="3d147-794">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="3d147-795">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-795">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-796">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-796">Allowed From</span></span>

<span data-ttu-id="3d147-797">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-797">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-798">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-798">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-799">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-799">See Also</span></span>

- <span data-ttu-id="3d147-800">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-800">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-801">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-801">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="3d147-802">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-802">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="3d147-803">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="3d147-803">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="3d147-804">Включение проверки X.509 клиента и выделение места для сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="3d147-804">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-805">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-805">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="3d147-806">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-806">Description</span></span>

<span data-ttu-id="3d147-807">Эта служба включает необязательную проверку подлинности клиента X.509 для экземпляра сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-807">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="3d147-808">Она также выделяет пространство, необходимое для обработки входящих цепочек сертификатов с удаленного узла клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-808">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="3d147-809">Сертификаты, которые предоставляет удаленный клиент, будут проверены на соответствие доверенным сертификатам экземпляра сервера TLS, который назначила служба *nx_secure_tls_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="3d147-809">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="3d147-810">Для режима клиента TLS требуется удаленное выделение сертификатов и следует использовать службу *nx_secure_tls_remote_certificate_buffer_allocate*.</span><span class="sxs-lookup"><span data-stu-id="3d147-810">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="3d147-811">Включение проверки подлинности клиента X.509 в экземпляре клиента TLS не будет действовать.</span><span class="sxs-lookup"><span data-stu-id="3d147-811">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="3d147-812">Параметр *certificate_buffer* указывает на место, выделенное для хранения входящих удаленных сертификатов и блоков управления, необходимых для этих сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-812">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="3d147-813">Буфер будет разделен по количеству сертификатов (*certs_number*) на равные части для каждого сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-813">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="3d147-814">Параметр *buffer_size* указывает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="3d147-814">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="3d147-815">Необходимый объем пространства можно вычислить по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="3d147-815">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="3d147-816">Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов.</span><span class="sxs-lookup"><span data-stu-id="3d147-816">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="3d147-817">Буфер должен быть достаточно большим, чтобы вместить этот размер для каждого сертификата, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше.</span><span class="sxs-lookup"><span data-stu-id="3d147-817">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="3d147-818">Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-818">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-819">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-819">Parameters</span></span>

- <span data-ttu-id="3d147-820">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-820">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-821">**certs_number** — число сертификатов, выделенных из предоставленного буфера.</span><span class="sxs-lookup"><span data-stu-id="3d147-821">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="3d147-822">**certificate_buffer** — указатель на буфер для хранения сертификатов, полученных с удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-822">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="3d147-823">**buffer_size** — размер буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-823">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-824">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-824">Return Values</span></span>

- <span data-ttu-id="3d147-825">**NX_SUCCESS** (0x00) — сертификат успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="3d147-825">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="3d147-826">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель буфера.</span><span class="sxs-lookup"><span data-stu-id="3d147-826">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="3d147-827">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="3d147-827">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="3d147-828">**NX_INVALID_PARAMETERS** (0x4D) — буфер слишком мал, чтобы вместить необходимое количество сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-828">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-829">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-829">Allowed From</span></span>

<span data-ttu-id="3d147-830">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-830">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-831">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-831">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-832">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-832">See Also</span></span>

- <span data-ttu-id="3d147-833">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-833">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-834">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-834">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-835">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-835">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="3d147-836">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="3d147-836">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="3d147-837">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-837">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-838">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-838">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-839">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-839">Description</span></span>

<span data-ttu-id="3d147-840">Эта служба отключает проверку подлинности сертификата клиента для определенного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-840">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="3d147-841">Дополнительные сведения см. в справочнике по nx_secure_tls_session_client_verify_enable.</span><span class="sxs-lookup"><span data-stu-id="3d147-841">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-842">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-842">Parameters</span></span>

- <span data-ttu-id="3d147-843">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-843">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-844">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-844">Return Values</span></span>

- <span data-ttu-id="3d147-845">**NX_SUCCESS** (0x00) — успешное изменение состояния.</span><span class="sxs-lookup"><span data-stu-id="3d147-845">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="3d147-846">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-846">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-847">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-847">Allowed From</span></span>

<span data-ttu-id="3d147-848">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-848">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-849">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-849">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-850">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-850">See Also</span></span>

- <span data-ttu-id="3d147-851">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="3d147-851">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="3d147-852">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-852">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-853">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-853">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="3d147-854">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="3d147-854">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="3d147-855">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-855">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-856">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-856">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-857">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-857">Description</span></span>

<span data-ttu-id="3d147-858">Эта служба включает проверку подлинности сертификата клиента для определенного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-858">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="3d147-859">Включение проверки подлинности сертификата клиента для экземпляра сервера TLS приведет к тому, что сервер TLS запросит сертификат из любого удаленного клиента TLS во время первоначального подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-859">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="3d147-860">Сертификат, полученный от удаленного клиента TLS, сопровождается сообщением CertificateVerify, которое сервер TLS использует для проверки на наличие прав владения сертификатом у клиента (наличие доступа к закрытому ключу, связанному с этим сертификатом).</span><span class="sxs-lookup"><span data-stu-id="3d147-860">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="3d147-861">Если предоставленный сертификат можно проверить и отследить до сертификата в хранилище доверенных сертификатов сервера TLS с помощью цепочки сертификатов X.509, удаленный клиент TLS проходит проверку подлинности, а подтверждение остается в силе.</span><span class="sxs-lookup"><span data-stu-id="3d147-861">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="3d147-862">В случае возникновения ошибок при обработке сертификата или сообщения CertificateVerify подтверждение TLS завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-862">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="3d147-863">*У сервера TLS должен быть по крайней мере один сертификат, добавленный с помощью nx_secure_tls_trusted_certificate_add, иначе проверка подлинности всегда будет завершаться ошибкой.*</span><span class="sxs-lookup"><span data-stu-id="3d147-863">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-864">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-864">Parameters</span></span>

- <span data-ttu-id="3d147-865">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-865">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-866">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-866">Return Values</span></span>

- <span data-ttu-id="3d147-867">**NX_SUCCESS** (0x00) — успешное изменение состояния.</span><span class="sxs-lookup"><span data-stu-id="3d147-867">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="3d147-868">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-868">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-869">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-869">Allowed From</span></span>

<span data-ttu-id="3d147-870">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-871">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-871">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-872">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-872">See Also</span></span>

- <span data-ttu-id="3d147-873">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="3d147-873">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="3d147-874">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-874">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-875">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-875">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-876">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-876">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="3d147-877">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-877">nx_secure_tls_session_create</span></span>

<span data-ttu-id="3d147-878">Создание сеанса NetX Secure TLS для обеспечения безопасности подключений</span><span class="sxs-lookup"><span data-stu-id="3d147-878">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-879">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-879">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="3d147-880">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-880">Description</span></span>

<span data-ttu-id="3d147-881">Эта служба инициализирует экземпляр структуры NX_SECURE_TLS_SESSION для использования во время безопасного взаимодействия по протоколу TLS через сетевое подключение.</span><span class="sxs-lookup"><span data-stu-id="3d147-881">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="3d147-882">Метод принимает объект NX_SECURE_TLS_CRYPTO, который заполняется доступными криптографическими методами для использования с протоколом TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-882">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="3d147-883">*encryption_metadata_area* указывает на буфер, выделенный для использования протоколом TLS для "метаданных", которые используются криптографическими методами в таблице NX_SECURE_TLS_CRYPTO для вычислений.</span><span class="sxs-lookup"><span data-stu-id="3d147-883">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="3d147-884">Размер таблицы можно определить с помощью службы nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="3d147-884">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="3d147-885">Дополнительные сведения см. в разделе "Шифрование в NetX Secure TLS" главы 3.</span><span class="sxs-lookup"><span data-stu-id="3d147-885">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-886">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-886">Parameters</span></span>

- <span data-ttu-id="3d147-887">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-887">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-888">**cipher_table** — указатель на криптографические методы TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-888">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="3d147-889">**encryption_metadata_area** — указатель на пространство для метаданных шифрования.</span><span class="sxs-lookup"><span data-stu-id="3d147-889">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="3d147-890">**encryption_metadata_size** — размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="3d147-890">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-891">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-891">Return Values</span></span>

- <span data-ttu-id="3d147-892">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-892">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-893">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-893">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="3d147-894">**NX_INVALID_PARAMETERS** (0x4D) — буфер метаданных слишком мал для указанных методов.</span><span class="sxs-lookup"><span data-stu-id="3d147-894">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="3d147-895">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) — необходимый метод шифра для включенной версии TLS не указан в таблице шифров.</span><span class="sxs-lookup"><span data-stu-id="3d147-895">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-896">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-896">Allowed From</span></span>

<span data-ttu-id="3d147-897">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-897">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-898">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-898">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-899">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-899">See Also</span></span>

- <span data-ttu-id="3d147-900">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-900">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-901">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="3d147-901">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="3d147-902">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-902">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-903">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-903">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-904">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-904">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="3d147-905">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-905">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-906">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-906">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-907">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-907">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-908">Шифрование для NetX Secure TLS в главе 3</span><span class="sxs-lookup"><span data-stu-id="3d147-908">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="3d147-909">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-909">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="3d147-910">Удаление сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-910">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-911">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-911">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-912">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-912">Description</span></span>

<span data-ttu-id="3d147-913">Эта служба удаляет сеанс TLS, представленный экземпляром структуры NX_SECURE_TLS_SESSION, и освобождает все системные ресурсы этого экземпляра сеанса.</span><span class="sxs-lookup"><span data-stu-id="3d147-913">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-914">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-914">Parameters</span></span>

- <span data-ttu-id="3d147-915">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-915">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-916">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-916">Return Values</span></span>

- <span data-ttu-id="3d147-917">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-917">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-918">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-918">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-919">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-919">Allowed From</span></span>

<span data-ttu-id="3d147-920">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-920">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-921">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-921">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-922">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-922">See Also</span></span>

- <span data-ttu-id="3d147-923">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-923">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-924">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-924">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-925">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-925">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-926">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-926">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="3d147-927">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-927">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-928">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-928">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-929">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-929">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="3d147-930">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-930">nx_secure_tls_session_end</span></span>

<span data-ttu-id="3d147-931">Завершение активного сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-931">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-932">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-932">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="3d147-933">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-933">Description</span></span>

<span data-ttu-id="3d147-934">Эта служба завершает сеанс TLS, представленный экземпляром структуры NX_SECURE_TLS_SESSION, путем отправления сообщения CloseNotify протокола TLS на удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="3d147-934">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="3d147-935">Затем служба ожидает ответа от удаленного узла с собственным сообщением CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="3d147-935">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="3d147-936">Если удаленный узел не отправляет сообщение CloseNotify, протокол TLS считает это ошибкой и возможным нарушением безопасности, поэтому проверка возвращаемого значения важна для безопасного подключения.</span><span class="sxs-lookup"><span data-stu-id="3d147-936">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="3d147-937">Параметр **wait_option** можно использовать для управления длительностью ожидания ответа для службы перед возвращением управления вызывающему потоку.</span><span class="sxs-lookup"><span data-stu-id="3d147-937">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-938">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-938">Parameters</span></span>

- <span data-ttu-id="3d147-939">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-939">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-940">**wait_option** — указывает на длительность ожидания ответа для службы от удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-940">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-941">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-941">Return Values</span></span>

- <span data-ttu-id="3d147-942">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-942">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-943">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) — не получен ответ от удаленного узла до истечения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="3d147-943">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="3d147-944">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить пакет для отправки сообщения CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="3d147-944">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="3d147-945">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить сообщение CloseNotify по TCP-сокету.</span><span class="sxs-lookup"><span data-stu-id="3d147-945">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="3d147-946">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-946">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-947">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-947">Allowed From</span></span>

<span data-ttu-id="3d147-948">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-948">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-949">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-949">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-950">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-950">See Also</span></span>

- <span data-ttu-id="3d147-951">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-951">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-952">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-952">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-953">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-953">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-954">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-954">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-955">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-955">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-956">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-956">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-957">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-957">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="3d147-958">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="3d147-958">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="3d147-959">Установка буфера повторной сборки пакетов для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-959">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-960">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-960">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="3d147-961">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-961">Description</span></span>

<span data-ttu-id="3d147-962">Эта служба связывает буфер повторной сборки пакетов с сеансом TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-962">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="3d147-963">Для расшифровки и анализа входящих записей TLS необходимо собрать данные в каждой записи из базовых TCP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="3d147-963">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="3d147-964">Размер записей TLS может составлять до 16 КБ (хотя обычно намного меньше), поэтому они могут не поместиться в один TCP-пакет.</span><span class="sxs-lookup"><span data-stu-id="3d147-964">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="3d147-965">Если известно, что размер входящего сообщения будет меньше предельного числа записей TLS, равного 16 КБ, размер буфера можно уменьшить. Однако для обработки неизвестных входящих данных буфер следует сделать максимально большим.</span><span class="sxs-lookup"><span data-stu-id="3d147-965">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="3d147-966">Если входящая запись больше, чем заданный буфер, то сеанс TLS завершится с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-966">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-967">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-967">Parameters</span></span>

- <span data-ttu-id="3d147-968">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-968">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-969">**buffer_ptr** — указатель на буфер для протокола TLS, используемый для повторной сборки пакетов.</span><span class="sxs-lookup"><span data-stu-id="3d147-969">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="3d147-970">**buffer_size** — размер заданного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="3d147-970">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-971">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-971">Return Values</span></span>

- <span data-ttu-id="3d147-972">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-972">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-973">**NX_INVALID_PARAMETERS** (0x4D) — недопустимый буфер или указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-973">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="3d147-974">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-974">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-975">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-975">Allowed From</span></span>

<span data-ttu-id="3d147-976">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-976">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-977">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-977">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-978">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-978">See Also</span></span>

- <span data-ttu-id="3d147-979">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-979">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-980">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-980">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-981">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-981">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-982">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-982">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-983">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-983">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-984">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-984">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-985">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-985">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="3d147-986">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="3d147-986">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="3d147-987">Переопределение версии протокола TLS по умолчанию для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-987">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-988">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-988">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="3d147-989">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-989">Description</span></span>

<span data-ttu-id="3d147-990">Эта служба переопределяет версию протокола TLS по умолчанию (самую новую), используемую в определенном сеансе.</span><span class="sxs-lookup"><span data-stu-id="3d147-990">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="3d147-991">Это позволяет NetX Secure TLS использовать более раннюю версию протокола TLS для определенного сеанса протокола, не отключая ее во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="3d147-991">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="3d147-992">Это может быть полезно в приложениях, которым может потребоваться обмен данными с узлом более ранней версии, который не поддерживает последнюю версию TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-992">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-993">*Начиная с версии 5.11 с пакетом обновления 3 (SP3), NetX Secure TLS поддерживает RFC 7507 (см. примечание ниже) и любое переопределение более старой версии с помощью этого API приведет к тому, что в ClientHello будет отправлено резервное SCSV. Если сервер поддерживает более новую версию TLS и резервное SCSV добавлено в ClientHello, этот сервер прервет подтверждение TLS с оповещением "Неприемлемый резерв". SCSV отправляется, только если версия переопределения является более старой, чем используемая версия TLS (например, при переопределении версии до TLS 1.2 SCSV не будет отправлен).*</span><span class="sxs-lookup"><span data-stu-id="3d147-993">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="3d147-994">Допустимыми значениями параметра protocol_version являются следующие макросы: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 и NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="3d147-994">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="3d147-995">Макросы NX_SECURE_TLS_DISABLE_TLS_1_1 и NX_SECURE_TLS_ENABLE_TLS_1_0 могут использоваться для управления версиями TLS, компилируемыми в приложение.</span><span class="sxs-lookup"><span data-stu-id="3d147-995">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="3d147-996">Протокол TLS версии 1.2 всегда включен.</span><span class="sxs-lookup"><span data-stu-id="3d147-996">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="3d147-997">Обратите внимание, что если удаленный узел не поддерживает предоставленную версию, произойдет сбой подключения. Только предоставленная версия переопределения будет согласовываться с помощью NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-997">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-998">RFC 7507: резервное SCSV протокола TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-998">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="3d147-999">Этот документ RFC предназначен для устранения проблемы безопасности, которая изначально была вызвана серверами, которые обрабатывали согласование с предыдущими протоколами ненадлежащим образом и отказались от других допустимых сообщений ClientHello.</span><span class="sxs-lookup"><span data-stu-id="3d147-999">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="3d147-1000">При попытке сохранить совместимость с этими старыми серверами некоторые клиентские приложения TLS начали повторно выполнять завершившиеся сбоем подтверждения с помощью более старой версии TLS (например, при сбое TLS 1.2 использовали TLS 1.1).</span><span class="sxs-lookup"><span data-stu-id="3d147-1000">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="3d147-1001">Однако это обходное решение создало новую проблему. Злоумышленники могут заставить клиента перейти на более раннюю версию, искусственно вызывая ошибку сети или пакета, из-за которой происходит сбой подключения к серверу, даже если сервер поддерживает более новую версию TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1001">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="3d147-1002">При переходе на более старую версию злоумышленник может использовать слабые места в этой версии (SSLv3<sup>21</sup> особенно подвержен атаке POODLE).</span><span class="sxs-lookup"><span data-stu-id="3d147-1002">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="3d147-1003">Чтобы предотвратить такую ситуацию, в документе RFC 7507 представлено "резервное SCSV" — псевдокомплект шифров <sup>22</sup>. Этот комплект отправляется в ClientHello, которое уведомляет сервер TLS, когда клиент протокола TLS использует не самую новую поддерживаемую версию протокола.</span><span class="sxs-lookup"><span data-stu-id="3d147-1003">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="3d147-1004">Таким образом, сервер, поддерживающий более новую версию, может отклонить ClientHello, содержащее резервное SCSV, и предотвратить атаку, предполагающую переход на более раннюю версию.</span><span class="sxs-lookup"><span data-stu-id="3d147-1004">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="3d147-1005">NetX Secure не применяет SSLv3 из-за наличия серьезных слабых мест, таких как POODLE.</span><span class="sxs-lookup"><span data-stu-id="3d147-1005">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="3d147-1006">Псевдокомплект шифров или SCSV (сигнальное значение комплекта шифров) — это зарезервированное число комплектов шифров, которое используется для оповещения включенных реализаций TLS о функциях, которые были недоступны в более старых версиях TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1006">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="3d147-1007">Примерами являются резервное SCSV и TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746).</span><span class="sxs-lookup"><span data-stu-id="3d147-1007">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1008">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1008">Parameters</span></span>

- <span data-ttu-id="3d147-1009">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1009">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1010">**protocol_version** — макрос версии TLS для конкретной версии TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1010">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1011">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1011">Return Values</span></span>

- <span data-ttu-id="3d147-1012">**NX_SUCCESS** (0x00) — успешное изменение состояния.</span><span class="sxs-lookup"><span data-stu-id="3d147-1012">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="3d147-1013">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1013">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-1014">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) — известная, но неподдерживаемая версия TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1014">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="3d147-1015">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — недопустимая версия протокола.</span><span class="sxs-lookup"><span data-stu-id="3d147-1015">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1016">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1016">Allowed From</span></span>

<span data-ttu-id="3d147-1017">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1017">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1018">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1018">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1019">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1019">See Also</span></span>

- <span data-ttu-id="3d147-1020">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1020">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1021">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1021">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="3d147-1022">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1022">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="3d147-1023">Получение данных из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1023">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1024">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1024">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="3d147-1025">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1025">Description</span></span>

<span data-ttu-id="3d147-1026">Эта служба получает данные из указанного активного сеанса TLS, выполняя расшифровку этих данных перед их предоставлением вызывающему объекту в параметре NX_PACKET.</span><span class="sxs-lookup"><span data-stu-id="3d147-1026">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="3d147-1027">Если в указанном сеансе в очереди нет данных, вызов приостанавливается в зависимости от указанного параметра ожидания.</span><span class="sxs-lookup"><span data-stu-id="3d147-1027">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-1028">*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен.*</span><span class="sxs-lookup"><span data-stu-id="3d147-1028">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1029">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1029">Parameters</span></span>

- <span data-ttu-id="3d147-1030">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1030">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1031">**packet_ptr** — указатель на выделенный указатель пакета TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1031">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="3d147-1032">**wait_option** — указывает, как долго служба должна ожидать пакет от удаленного узла перед возвратом.</span><span class="sxs-lookup"><span data-stu-id="3d147-1032">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1033">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1033">Return Values</span></span>

- <span data-ttu-id="3d147-1034">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1034">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-1035">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="3d147-1035">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="3d147-1036">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="3d147-1036">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="3d147-1037">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — полученное сообщение не прошло проверку подлинности хэша.</span><span class="sxs-lookup"><span data-stu-id="3d147-1037">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="3d147-1038">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения указана неизвестная версия протокола.</span><span class="sxs-lookup"><span data-stu-id="3d147-1038">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="3d147-1039">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — от удаленного узла получено оповещение TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1039">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="3d147-1040">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1040">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="3d147-1041">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1041">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1042">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1042">Allowed From</span></span>

<span data-ttu-id="3d147-1043">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1043">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1044">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1044">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="3d147-1045">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1045">See Also</span></span>

- <span data-ttu-id="3d147-1046">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1046">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="3d147-1047">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1047">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1048">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1048">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1049">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1049">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1050">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-1050">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-1051">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-1051">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-1052">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-1052">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="3d147-1053">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1053">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="3d147-1054">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1054">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="3d147-1055">Назначение обратного вызова, который будет выполняться в начале повторного согласования сеанса</span><span class="sxs-lookup"><span data-stu-id="3d147-1055">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1056">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1056">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="3d147-1057">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1057">Description</span></span>

<span data-ttu-id="3d147-1058">Эта служба назначает обратный вызов сеансу TLS, который будет вызываться при получении первого сообщения о подтверждении повторного согласования сеанса от удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-1058">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="3d147-1059">Функция обратного вызова предназначена для уведомления приложения о начале подтверждения повторного согласования. Приложение может завершить сеанс TLS, возвратив любое ненулевое значение из обратного вызова, которое приведет к завершению сеанса TLS с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-1059">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="3d147-1060">Если приложение продолжает повторное согласование, обратный вызов должен возвращать значение NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1060">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="3d147-1061">*Из-за семантики повторного согласования TLS обратный вызов будет выполняться для клиентов NetX Secure TLS при получении HelloRequest с удаленного сервера, но не в момент инициации клиентом повторного согласования. На серверах NetX Secure TLS обратный вызов будет выполняться при каждом получении повторного согласования ClientHello (любое сообщение ClientHello, полученное в контексте активного сеанса TLS). Это означает, что обратный вызов будет выполняться независимо от того, инициировал ли повторное согласование удаленный узел или локальное приложение, так как сервер TLS отправит HelloRequest, на который будет отвечать удаленный клиент.*</span><span class="sxs-lookup"><span data-stu-id="3d147-1061">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="3d147-1062">NetX Secure TLS вводит в действие расширение для указания безопасного повторного согласования из документа RFC 5746, чтобы гарантировать, что подтверждения повторного согласования не будут подвергаться атакам "злоумышленник в середине".</span><span class="sxs-lookup"><span data-stu-id="3d147-1062">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1063">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1063">Parameters</span></span>

- <span data-ttu-id="3d147-1064">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1064">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1065">**func_ptr** — указатель на функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="3d147-1065">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1066">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1066">Return Values</span></span>

- <span data-ttu-id="3d147-1067">**NX_SUCCESS** (0x00) — функция обратного вызова успешно назначена.</span><span class="sxs-lookup"><span data-stu-id="3d147-1067">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="3d147-1068">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя для функции обратного вызова или сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1068">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1069">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1069">Allowed From</span></span>

<span data-ttu-id="3d147-1070">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1070">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1071">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1071">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1072">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1072">See Also</span></span>

- <span data-ttu-id="3d147-1073">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1073">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1074">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1074">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1075">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1075">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-1076">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-1076">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-1077">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="3d147-1077">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="3d147-1078">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="3d147-1078">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="3d147-1079">Инициация подтверждения повторного согласования сеанса с удаленным узлом</span><span class="sxs-lookup"><span data-stu-id="3d147-1079">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1080">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1080">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="3d147-1081">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1081">Description</span></span>

<span data-ttu-id="3d147-1082">Эта служба инициирует подтверждение *повторного согласования* сеанса с подключенным удаленным узлом TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1082">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="3d147-1083">Повторное согласование состоит из второго подтверждения TLS в контексте ранее установленного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1083">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="3d147-1084">Каждое новое сообщение подтверждения шифруется с помощью сеанса TLS до создания новых ключей сеанса и обмена сообщениями ChangeCipherSpec, при этом новые ключи используются для шифрования всех сообщений.</span><span class="sxs-lookup"><span data-stu-id="3d147-1084">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="3d147-1085">Повторное согласование можно инициировать в любое время после установки сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1085">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="3d147-1086">Если повторное согласование выполняется во время подтверждения TLS или до установки сеанса TLS, никакие действия не выполняются.</span><span class="sxs-lookup"><span data-stu-id="3d147-1086">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="3d147-1087">*При вызове этой службы будет выполнено полное подтверждение TLS, поэтому время выполнения и возврата состояния будет зависеть от текущих параметров TLS и параметров сеанса.*</span><span class="sxs-lookup"><span data-stu-id="3d147-1087">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="3d147-1088">NetX Secure TLS вводит в действие расширение для указания безопасного повторного согласования из документа RFC 5746, чтобы гарантировать, что подтверждения повторного согласования не будут подвергаться атакам "злоумышленник в середине".</span><span class="sxs-lookup"><span data-stu-id="3d147-1088">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1089">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1089">Parameters</span></span>

- <span data-ttu-id="3d147-1090">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1090">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1091">**wait_option** — указывает, как долго служба должна ожидать пакет от удаленного узла перед возвратом.</span><span class="sxs-lookup"><span data-stu-id="3d147-1091">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="3d147-1092">Это передается всем службам NetX в TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1092">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1093">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1093">Return Values</span></span>

- <span data-ttu-id="3d147-1094">**NX_SUCCESS** (0x00) — повторное согласование выполнено успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-1094">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="3d147-1095">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="3d147-1095">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="3d147-1096">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="3d147-1096">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="3d147-1097">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — полученное сообщение не прошло проверку подлинности хэша.</span><span class="sxs-lookup"><span data-stu-id="3d147-1097">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="3d147-1098">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения указана неизвестная версия протокола.</span><span class="sxs-lookup"><span data-stu-id="3d147-1098">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="3d147-1099">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — от удаленного узла получено оповещение TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1099">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="3d147-1100">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) — локальный или удаленный сеанс TLS неактивен, из-за чего выполнение повторного согласования невозможно.</span><span class="sxs-lookup"><span data-stu-id="3d147-1100">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="3d147-1101">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) — удаленный узел не предоставил ни SCSV, ни расширение безопасного повторного согласования, из-за чего не удалось выполнить повторное согласование.</span><span class="sxs-lookup"><span data-stu-id="3d147-1101">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="3d147-1102">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1102">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="3d147-1103">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1103">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="3d147-1104">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить базовый пакет.</span><span class="sxs-lookup"><span data-stu-id="3d147-1104">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1105">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1105">Allowed From</span></span>

<span data-ttu-id="3d147-1106">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1106">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1107">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1107">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1108">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1108">See Also</span></span>

- <span data-ttu-id="3d147-1109">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1109">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1110">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1110">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1111">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1111">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-1112">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-1112">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-1113">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1113">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="3d147-1114">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="3d147-1114">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="3d147-1115">Очистка и сброс сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1115">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1116">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1116">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-1117">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1117">Description</span></span>

<span data-ttu-id="3d147-1118">Эта служба очищает сеанс TLS и сбрасывает состояние, как если бы сеанс был только что создан, чтобы существующий объект сеанса TLS можно было повторно использовать для нового сеанса.</span><span class="sxs-lookup"><span data-stu-id="3d147-1118">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1119">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1119">Parameters</span></span>

- <span data-ttu-id="3d147-1120">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1120">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1121">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1121">Return Values</span></span>

- <span data-ttu-id="3d147-1122">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1122">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-1123">**NX_INVALID_PARAMETERS** (0x4D) — недопустимый указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1123">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-1124">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1124">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1125">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1125">Allowed From</span></span>

<span data-ttu-id="3d147-1126">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1126">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1127">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1127">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="3d147-1128">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1128">See Also</span></span>

- <span data-ttu-id="3d147-1129">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1129">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1130">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1130">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1131">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1131">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1132">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-1132">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-1133">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-1133">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-1134">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1134">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-1135">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1135">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="3d147-1136">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-1136">nx_secure_tls_session_send</span></span>

<span data-ttu-id="3d147-1137">Отправка данных через сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1137">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1138">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1138">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="3d147-1139">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1139">Description</span></span>

<span data-ttu-id="3d147-1140">Эта служба отправляет данные в указанном NX_PACKET, используя указанный активный сеанс TLS, и выполняет шифрование этих данных перед их отправкой на удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="3d147-1140">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="3d147-1141">Если последний объявленный размер окна получателя меньше, чем этот запрос, служба при необходимости приостанавливает выполнение в соответствии с указанными параметрами ожидания.</span><span class="sxs-lookup"><span data-stu-id="3d147-1141">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-1142">*Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Иначе это приведет к непредсказуемым результатам, так как сетевой драйвер освободит пакет после передачи*.</span><span class="sxs-lookup"><span data-stu-id="3d147-1142">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1143">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1143">Parameters</span></span>

- <span data-ttu-id="3d147-1144">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1144">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1145">**packet_ptr** — указатель на пакет TLS, содержащий данные для отправки.</span><span class="sxs-lookup"><span data-stu-id="3d147-1145">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="3d147-1146">**wait_option** — определяет поведение службы в случае, если запрос превышает размер окна получателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1146">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1147">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1147">Return Values</span></span>

- <span data-ttu-id="3d147-1148">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1148">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-1149">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="3d147-1149">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="3d147-1150">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="3d147-1150">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="3d147-1151">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить данные через базовый TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="3d147-1151">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="3d147-1152">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1152">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="3d147-1153">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1153">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1154">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1154">Allowed From</span></span>

<span data-ttu-id="3d147-1155">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1156">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1156">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="3d147-1157">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1157">See Also</span></span>

- <span data-ttu-id="3d147-1158">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1158">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="3d147-1159">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1159">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1160">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1160">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1161">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1161">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="3d147-1162">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1162">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1163">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-1163">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-1164">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1164">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-1165">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-1165">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="3d147-1166">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1166">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="3d147-1167">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1167">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="3d147-1168">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения сервера TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1168">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1169">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1169">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="3d147-1170">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1170">Description</span></span>

<span data-ttu-id="3d147-1171">Эта служба назначает указатель функции сеансу TLS, который будет вызывать протокол TLS, если подтверждение сервера TLS получило сообщение ClientHello.</span><span class="sxs-lookup"><span data-stu-id="3d147-1171">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="3d147-1172">Функция обратного вызова позволяет приложению обрабатывать любые расширения TLS из полученного сообщения ClientHello, для которого необходимо ввести данные или принять решение.</span><span class="sxs-lookup"><span data-stu-id="3d147-1172">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="3d147-1173">Обратный вызов выполняется с помощью блока управления сеансом TLS и массива объектов NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="3d147-1173">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="3d147-1174">Массив объектов расширения необходимо передать во вспомогательную функцию, которая найдет и проанализирует определенное расширение.</span><span class="sxs-lookup"><span data-stu-id="3d147-1174">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="3d147-1175">Пример вспомогательной функции, которая анализирует расширения TLS, предоставленные в сообщениях приветствия, см. на странице *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="3d147-1175">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="3d147-1176">Обратный вызов сервера также можно использовать для выбора активного сертификата удостоверения с помощью *nx_secure_tls_active_certificate_set* для сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1176">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="3d147-1177">Чаще всего это происходит в ответ на расширение указания имени сервера (SNI), которое позволяет клиенту TLS указывать, какой сервер пытается связаться.</span><span class="sxs-lookup"><span data-stu-id="3d147-1177">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="3d147-1178">Дополнительные сведения см. в справочниках по *nx_secure_tls_session_sni_extension_parse* и *nx_secure_tls_active_certificate_set*.</span><span class="sxs-lookup"><span data-stu-id="3d147-1178">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1179">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1179">Parameters</span></span>

- <span data-ttu-id="3d147-1180">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1180">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1181">**func_ptr** — указатель на функцию обратного вызова сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1181">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1182">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1182">Return Values</span></span>

- <span data-ttu-id="3d147-1183">**NX_SUCCESS** (0x00) — успешное выделение указателя функции.</span><span class="sxs-lookup"><span data-stu-id="3d147-1183">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="3d147-1184">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1184">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1185">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1185">Allowed From</span></span>

<span data-ttu-id="3d147-1186">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1186">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1187">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1187">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-1188">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1188">See Also</span></span>

- <span data-ttu-id="3d147-1189">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1189">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1190">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1190">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="3d147-1191">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1191">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="3d147-1192">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1192">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="3d147-1193">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-1193">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="3d147-1194">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="3d147-1194">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="3d147-1195">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1195">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="3d147-1196">Анализ расширения указания имени сервера (SNI), полученного от клиента TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1196">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1197">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1197">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="3d147-1198">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1198">Description</span></span>

<span data-ttu-id="3d147-1199">Эта служба должна вызываться из обратного вызова сеанса сервера TLS, который добавляется в сеанс TLS с помощью nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="3d147-1199">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="3d147-1200">Обратный вызов вызывается после получения сообщения ClientHello от удаленного клиента TLS и предоставляет массив доступных расширений (и количество расширений в массиве).</span><span class="sxs-lookup"><span data-stu-id="3d147-1200">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="3d147-1201">Этот массив и его длину можно передать непосредственно в эту подпрограмму, чтобы определить наличие расширения SNI. Если нет, возвращается NX_SECURE_TLS_EXTENSION_NOT_FOUND, указывая, что клиент решил не использовать расширение SNI (это не ошибка).</span><span class="sxs-lookup"><span data-stu-id="3d147-1201">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="3d147-1202">Если обнаружено расширение SNI, то в структуре dns_name возвращается DNS-имя X.509, предоставленное клиентом TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1202">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="3d147-1203">Сейчас расширение SNI предоставляет только одну запись DNS-имени, которая может использоваться сервером TLS для определения сертификата удостоверения, отправляемого удаленному клиенту.\*\*</span><span class="sxs-lookup"><span data-stu-id="3d147-1203">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="3d147-1204">Структура NX_SECURE_X509_DNS_NAME содержит только DNS-имя в виде строки UCHAR в поле *nx_secure_x509_dns_name* и длину строки имени в поле *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="3d147-1204">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="3d147-1205">Макрос NX_SECURE_X509_DNS_NAME_MAX определяет размер буфера nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="3d147-1205">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1206">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1206">Parameters</span></span>

- <span data-ttu-id="3d147-1207">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1207">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1208">**extensions** — указатель на массив расширений протокола TLS Hello (из обратного вызова сеанса).</span><span class="sxs-lookup"><span data-stu-id="3d147-1208">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="3d147-1209">**num_extensions** — количество расширений в массиве (из обратного вызова сеанса).</span><span class="sxs-lookup"><span data-stu-id="3d147-1209">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="3d147-1210">**dns_name** — возвращает DNS-имя, заданное в расширении SNI.</span><span class="sxs-lookup"><span data-stu-id="3d147-1210">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1211">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1211">Return Values</span></span>

- <span data-ttu-id="3d147-1212">**NX_SUCCESS** (0x00) — успешное выполнение анализа расширения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1212">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="3d147-1213">**NX_PTR_ERROR** (0x07) — недопустимый массив расширений или указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1213">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="3d147-1214">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) — расширение SNI не найдено.</span><span class="sxs-lookup"><span data-stu-id="3d147-1214">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="3d147-1215">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) — недопустимый формат расширения SNI.</span><span class="sxs-lookup"><span data-stu-id="3d147-1215">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1216">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1216">Allowed From</span></span>

<span data-ttu-id="3d147-1217">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1218">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1218">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="3d147-1219">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1219">See Also</span></span>

- <span data-ttu-id="3d147-1220">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1220">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="3d147-1221">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1221">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="3d147-1222">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1222">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="3d147-1223">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1223">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="3d147-1224">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1224">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="3d147-1225">Установка DNS-имени расширения указания имени сервера (SNI) для отправки на удаленный сервер</span><span class="sxs-lookup"><span data-stu-id="3d147-1225">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1226">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1226">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="3d147-1227">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1227">Description</span></span>

<span data-ttu-id="3d147-1228">Эта служба позволяет приложению клиента TLS предоставлять предпочитаемое DNS-имя сервера удаленному серверу TLS с помощью расширения указания имени сервера (SNI) TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1228">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="3d147-1229">Расширение SNI позволяет серверу выбрать правильный сертификат удостоверения и параметры на основе указанных предпочтений для сервера клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-1229">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="3d147-1230">Сейчас расширение SNI поддерживает отправку только одного DNS-имени, поэтому параметр имени имеет единственное число.</span><span class="sxs-lookup"><span data-stu-id="3d147-1230">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="3d147-1231">Параметр dns_name необходимо инициализировать с помощью *nx_secure_x509_dns_name_initialize* и он будет содержать предпочитаемый сервер клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-1231">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="3d147-1232">Чтобы удалить имя расширения, просто вызовите эту службу, задав для параметра dns_name значение NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="3d147-1232">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="3d147-1233">Структура NX_SECURE_X509_DNS_NAME содержит только DNS-имя в виде строки UCHAR в поле *nx_secure_x509_dns_name* и длину строки имени в поле *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="3d147-1233">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="3d147-1234">Макрос NX_SECURE_X509_DNS_NAME_MAX определяет размер буфера nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="3d147-1234">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="3d147-1235">*Эту подпрограмму следует вызывать до вызова nx_secure_tls_session_start, иначе ClientHello не будет содержать расширение SNI*.</span><span class="sxs-lookup"><span data-stu-id="3d147-1235">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1236">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1236">Parameters</span></span>

- <span data-ttu-id="3d147-1237">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1237">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1238">**dns_name** — DNS-имя, предоставленное приложением.</span><span class="sxs-lookup"><span data-stu-id="3d147-1238">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1239">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1239">Return Values</span></span>

- <span data-ttu-id="3d147-1240">**NX_SUCCESS** (0x00) — DNS-имя сервера успешно добавлено.</span><span class="sxs-lookup"><span data-stu-id="3d147-1240">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="3d147-1241">**NX_PTR_ERROR** (0x07) — недопустимое DNS-имя или указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1241">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1242">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1242">Allowed From</span></span>

<span data-ttu-id="3d147-1243">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1243">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1244">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1244">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-1245">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1245">See Also</span></span>

- <span data-ttu-id="3d147-1246">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1246">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1247">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1247">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="3d147-1248">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1248">nx_secure_tls_session_start</span></span>

<span data-ttu-id="3d147-1249">Запуск сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1249">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1250">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1250">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="3d147-1251">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1251">Description</span></span>

<span data-ttu-id="3d147-1252">Эта служба запускает сеанс TLS, используя указанный блок управления сеансом TLS и подключенный TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="3d147-1252">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="3d147-1253">TCP-соединение должно завершиться после успешного вызова nx_tcp_client_socket_connect или nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="3d147-1253">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="3d147-1254">Эта служба определит тип сеанса TLS (клиент или сервер) из TCP-сокета.</span><span class="sxs-lookup"><span data-stu-id="3d147-1254">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="3d147-1255">Параметр ожидания определяет поведение службы во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1255">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1256">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1256">Parameters</span></span>

- <span data-ttu-id="3d147-1257">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1257">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1258">**tcp_socket_ptr** — указатель на подключенный TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="3d147-1258">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="3d147-1259">**wait_option** — определяет поведение службы во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1259">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1260">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1260">Return Values</span></span>

- <span data-ttu-id="3d147-1261">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1261">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-1262">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="3d147-1262">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="3d147-1263">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) — получен неправильный тип сообщения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1263">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="3d147-1264">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) — шифр, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3d147-1264">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="3d147-1265">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) — не удалось обработать сообщение во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1265">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="3d147-1266">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — не удалось проверить хэш MAC во входящем сообщении.</span><span class="sxs-lookup"><span data-stu-id="3d147-1266">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="3d147-1267">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить данные через базовый TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="3d147-1267">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="3d147-1268">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) — входящее сообщение содержало недопустимое поле длины.</span><span class="sxs-lookup"><span data-stu-id="3d147-1268">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="3d147-1269">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) — неправильное входящее сообщение ChangeCipherSpec.</span><span class="sxs-lookup"><span data-stu-id="3d147-1269">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="3d147-1270">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) — входящий сертификат TLS невозможно использовать для идентификации удаленного сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1270">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="3d147-1271">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) — шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3d147-1271">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="3d147-1272">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) — на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1272">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="3d147-1273">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения TLS указана неизвестная версия TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1273">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="3d147-1274">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) — в заголовке полученного сообщения TLS указана известная, но неподдерживаемая версия TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1274">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="3d147-1275">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить внутренний пакет TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1275">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="3d147-1276">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) — удаленный узел предоставил недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-1276">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="3d147-1277">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1277">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="3d147-1278">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) —запись в таблице комплектов шифров содержала указатель на функцию со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="3d147-1278">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="3d147-1279">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) — удаленное ClientHello TLS включало резервное SCSV и была выполнена попытка отката версии.</span><span class="sxs-lookup"><span data-stu-id="3d147-1279">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="3d147-1280">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1280">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1281">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1281">Allowed From</span></span>

<span data-ttu-id="3d147-1282">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1283">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1283">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1284">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1284">See Also</span></span>

- <span data-ttu-id="3d147-1285">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1285">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="3d147-1286">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1286">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1287">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1287">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1288">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="3d147-1288">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="3d147-1289">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-1289">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-1290">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1290">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-1291">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1291">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="3d147-1292">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="3d147-1292">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="3d147-1293">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1293">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1294">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="3d147-1294">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="3d147-1295">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="3d147-1295">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="3d147-1296">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="3d147-1296">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="3d147-1297">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="3d147-1297">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="3d147-1298">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="3d147-1298">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="3d147-1299">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-1299">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="3d147-1300">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1300">nx_packet_allocate</span></span>
- <span data-ttu-id="3d147-1301">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="3d147-1301">nx_packet_data_append</span></span>
- <span data-ttu-id="3d147-1302">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="3d147-1302">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="3d147-1303">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1303">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="3d147-1304">Назначение функции метки времени в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1304">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1305">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1305">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="3d147-1306">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1306">Description</span></span>

<span data-ttu-id="3d147-1307">Эта функция устанавливает указатель функции, который будет вызываться проколом TLS, когда необходимо получить текущее время, которое используется в различных сообщениях подтверждения TLS и для проверки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-1307">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="3d147-1308">Функция должна вернуть текущее время GMT в 32-битном формате UNIX (секунды с момента полуночи 1 января 1970 г., в формате UTC, игнорируя корректировочные секунды) согласно требованиям ClientHello в документе TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="3d147-1308">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="3d147-1309">Если функция метки времени не назначена, в подтверждении TLS для метки времени будет использоваться значение 0 и проверка истечения срока действия сертификата не будет работать.</span><span class="sxs-lookup"><span data-stu-id="3d147-1309">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1310">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1310">Parameters</span></span>

- <span data-ttu-id="3d147-1311">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1311">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1312">**time_func_ptr** — указатель на функцию, которая возвращает текущее время (GMT) в 32-битном формате UNIX.</span><span class="sxs-lookup"><span data-stu-id="3d147-1312">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1313">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1313">Return Values</span></span>

- <span data-ttu-id="3d147-1314">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="3d147-1314">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="3d147-1315">**NX_INVALID_PARAMETERS** (0x4D) — недопустимый указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1315">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-1316">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1316">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1317">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1317">Allowed From</span></span>

<span data-ttu-id="3d147-1318">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1318">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1319">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1319">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="3d147-1320">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1320">See Also</span></span>

- <span data-ttu-id="3d147-1321">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1321">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1322">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1322">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1323">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="3d147-1323">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="3d147-1324">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="3d147-1324">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="3d147-1325">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="3d147-1325">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="3d147-1326">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1326">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="3d147-1327">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-1327">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="3d147-1328">Добавление доверенного сертификата в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1328">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1329">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1329">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="3d147-1330">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1330">Description</span></span>

<span data-ttu-id="3d147-1331">Эта служба добавляет инициализированный экземпляр структуры NX_SECURE_X509_CERT в сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1331">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="3d147-1332">Этот сертификат используется в стеке TLS для проверки сертификатов, предоставляемых удаленным узлом во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1332">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="3d147-1333">Доверенные сертификаты необходимы для режима клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1333">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="3d147-1334">Доверенные сертификаты требуются только для режима сервера TLS, если включена проверка подлинности с помощью сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-1334">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1335">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1335">Parameters</span></span>

- <span data-ttu-id="3d147-1336">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1336">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1337">**certificate_ptr** — указатель на инициализированный экземпляр сертификата TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1337">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1338">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1338">Return Values</span></span>

- <span data-ttu-id="3d147-1339">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1339">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="3d147-1340">**NX_INVALID_PARAMETERS** (0x4D) — попытка добавить недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-1340">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="3d147-1341">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1341">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1342">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1342">Allowed From</span></span>

<span data-ttu-id="3d147-1343">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1343">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1344">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1344">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-1345">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1345">See Also</span></span>

- <span data-ttu-id="3d147-1346">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1346">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1347">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1347">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1348">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1348">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1349">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-1349">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="3d147-1350">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="3d147-1350">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="3d147-1351">Удаление доверенного сертификата из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1351">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1352">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1352">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="3d147-1353">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1353">Description</span></span>

<span data-ttu-id="3d147-1354">Эта служба удаляет доверенный сертификат из сеанса TLS, введенный в поле "Общее имя" сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1354">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1355">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1355">Parameters</span></span>

- <span data-ttu-id="3d147-1356">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1356">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="3d147-1357">**common_name** — значение общего имени удаляемого сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1357">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="3d147-1358">**common_name_length** — длина строки общего имени.</span><span class="sxs-lookup"><span data-stu-id="3d147-1358">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1359">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1359">Return Values</span></span>

- <span data-ttu-id="3d147-1360">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1360">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="3d147-1361">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1361">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="3d147-1362">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат не найден.</span><span class="sxs-lookup"><span data-stu-id="3d147-1362">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1363">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1363">Allowed From</span></span>

<span data-ttu-id="3d147-1364">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1364">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1365">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1365">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-1366">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1366">See Also</span></span>

- <span data-ttu-id="3d147-1367">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1367">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="3d147-1368">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1368">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1369">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1369">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1370">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-1370">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="3d147-1371">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1371">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="3d147-1372">Инициализация сертификата X.509 для NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1372">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1373">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1373">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="3d147-1374">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1374">Description</span></span>

<span data-ttu-id="3d147-1375">Эта служба инициализирует структуру NX_SECURE_X509_CERT из цифрового сертификата X.509 в двоичной кодировке для использования в сеансе TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1375">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="3d147-1376">Данные сертификата **должны** быть данными допустимого цифрового сертификата X.509 в формате двоичной кодировки DER.</span><span class="sxs-lookup"><span data-stu-id="3d147-1376">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="3d147-1377">Любой объект может стать источником данных (например, файловая система, скомпилированный буфер констант и т. д.), если на эти данные предоставлен указатель UCHAR.</span><span class="sxs-lookup"><span data-stu-id="3d147-1377">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="3d147-1378">Параметр *raw_data_buffer* и его размер являются необязательными параметрами, которые указывают выделенный буфер, в который копируются данные сертификата перед синтаксическим анализом.</span><span class="sxs-lookup"><span data-stu-id="3d147-1378">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="3d147-1379">Если raw_data_buffer передается со значением NX_NULL, то структура NX_SECURE_X509_CERT будет указывать непосредственно в массив certificate_data (в этом случае buffer_size игнорируется).</span><span class="sxs-lookup"><span data-stu-id="3d147-1379">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="3d147-1380">Если raw_data_buffer передается со значением NX_NULL, ***не*** изменяйте данные, на которые указывает указатель certificate_data, иначе обработка сертификата, скорее всего, завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="3d147-1380">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="3d147-1381">Параметр закрытого ключа предназначен для локальных сертификатов удостоверений. Закрытый ключ используется серверами для расшифровки входных данных ключа от клиента (зашифрованных с помощью открытого ключа сервера) и клиентами для проверки их удостоверений на сервере, когда сервер запрашивает сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="3d147-1381">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="3d147-1382">При добавлении закрытого ключа с помощью этого API соответствующий сертификат автоматически помечается как сертификат удостоверения для приложения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1382">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="3d147-1383">При инициализации сертификатов для других целей (например, доверенного хранилища) параметр *private_key_data* должен передаваться со значением NULL, *private_key_data_length* — с 0, а *private_key_type* — с NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="3d147-1383">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="3d147-1384">Параметр *private_key_type* указывает форматирование закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="3d147-1384">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="3d147-1385">Например, если закрытый ключ является закрытым ключом RSA в формате PKCS#1 с кодировкой DER, private_key_type необходимо передавать со значением NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER. Этот тип также известен NetX Secure, как тип, который будет немедленно проанализирован и сохранен для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="3d147-1385">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="3d147-1386">private_key_type также поддерживает определяемые пользователем типы ключей<sup>23</sup> для платформ и приложений, имеющих определенные форматы ключей или другие потребности.</span><span class="sxs-lookup"><span data-stu-id="3d147-1386">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="3d147-1387">Например, аппаратное средство шифрования может использовать конкретный формат, не распознаваемый программным обеспечением NetX Secure, либо закрытый ключ может быть зашифрован или представлен криптографическим маркером, как это может быть в случае с таким оборудованием шифрования, как доверенный платформенный модуль (TPM) или PKCS#11.</span><span class="sxs-lookup"><span data-stu-id="3d147-1387">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="3d147-1388">При использовании определяемого пользователем типа ключа данные ключа передаются в соответствующую криптографическую подпрограмму. Например, закрытый ключ RSA передается без какого-либо анализа или обработки непосредственно в подпрограмму шифрования RSA, предоставляемую для TLS в таблице комплектов шифров.</span><span class="sxs-lookup"><span data-stu-id="3d147-1388">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="3d147-1389">Определяемый пользователем тип ключа также передается в подпрограммы шифрования (в случае RSA это параметр "op").</span><span class="sxs-lookup"><span data-stu-id="3d147-1389">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="3d147-1390">Диапазон определяемых пользователем ключей охватывает верхнюю половину 32-битного целого числа без знака от значения 0x0001 0000-0xFFFF FFFF.</span><span class="sxs-lookup"><span data-stu-id="3d147-1390">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="3d147-1391">Значения меньше 0x0001 0000 зарезервированы для использования в NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="3d147-1391">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="3d147-1392">Определяемые пользователем типы ключей представляют собой дополнительную возможность, требующую пользовательских криптографических подпрограмм для обработки необработанных данных закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="3d147-1392">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="3d147-1393">Если вам нужна эта возможность, обратитесь к своему представителю Express Logic.</span><span class="sxs-lookup"><span data-stu-id="3d147-1393">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1394">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1394">Parameters</span></span>

- <span data-ttu-id="3d147-1395">**certificate_ptr** — указатель на неинициализированный экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-1395">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="3d147-1396">**certificate_data** — указатель на двоичные данные X.509 в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="3d147-1396">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="3d147-1397">**raw_data_buffer** — указатель на необязательный буфер данных выделенного сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1397">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="3d147-1398">**buffer_size** — размер необязательного буфера данных выделенного сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1398">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="3d147-1399">**certificate_data_length** — длина двоичных данных сертификата в байтах.</span><span class="sxs-lookup"><span data-stu-id="3d147-1399">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="3d147-1400">**private_key_data** — указатель на необязательные данные закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="3d147-1400">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="3d147-1401">**private_key_data_length** — длина данных закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="3d147-1401">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="3d147-1402">**private_key_type** — идентификатор типа ключа.</span><span class="sxs-lookup"><span data-stu-id="3d147-1402">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1403">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1403">Return Values</span></span>

- <span data-ttu-id="3d147-1404">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1404">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="3d147-1405">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1405">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="3d147-1406">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) — данные сертификата не содержат сертификат X.509 в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="3d147-1406">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="3d147-1407">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) — в сертификате отсутствует шифр открытого ключа, поддерживаемый в NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="3d147-1407">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="3d147-1408">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) — закрытый ключ или сертификат не содержат допустимую последовательность ASN.1.</span><span class="sxs-lookup"><span data-stu-id="3d147-1408">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="3d147-1409">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) — предоставленный закрытый ключ не является допустимым ключом PKCS#1 RSA.</span><span class="sxs-lookup"><span data-stu-id="3d147-1409">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="3d147-1410">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) — указанный тип закрытого ключа не был определен пользователем и не соответствует ни одному известному типу.</span><span class="sxs-lookup"><span data-stu-id="3d147-1410">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1411">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1411">Allowed From</span></span>

<span data-ttu-id="3d147-1412">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1413">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1413">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="3d147-1414">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1414">See Also</span></span>

- <span data-ttu-id="3d147-1415">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="3d147-1415">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="3d147-1416">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1416">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1417">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="3d147-1417">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="3d147-1418">Импорт сертификатов X.509 в NetX Secure в главе 3.</span><span class="sxs-lookup"><span data-stu-id="3d147-1418">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="3d147-1419">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1419">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="3d147-1420">Проверка DNS-имени на соответствие сертификату X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1420">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1421">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1421">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="3d147-1422">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1422">Description</span></span>

<span data-ttu-id="3d147-1423">Эта служба проверяет общее имя сертификата на соответствие доменному имени верхнего уровня (TLD), предоставленному вызывающим объектом в целях проверки DNS удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="3d147-1423">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="3d147-1424">Эту служебную функцию должна вызывать предоставленная приложением подпрограмма обратного вызова для проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1424">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="3d147-1425">Имя TLD должно быть верхней частью URL-адреса, используемого для доступа к удаленному узлу (строка, разделенная "."перед первой косой чертой).</span><span class="sxs-lookup"><span data-stu-id="3d147-1425">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="3d147-1426">Если общее имя содержит подстановочный знак (например, *.example.com), то подстановочный знак будет соответствовать любому суффиксу. Обратите внимание, что только первый обнаруженный подстановочный знак ("* ") (при чтении справа налево) будет учитываться при сопоставлении с подстановочными знаками, например abc.\*.example.com будет соответствовать *любому* имени, которое заканчивается на ".example.com".</span><span class="sxs-lookup"><span data-stu-id="3d147-1426">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="3d147-1427">Если общее имя не совпадает с указанной строкой, то будет выполняться анализ расширения subjectAltName (если оно есть в сертификате), а также будут сравниваться все записи DNSName.</span><span class="sxs-lookup"><span data-stu-id="3d147-1427">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="3d147-1428">Если ни одна из этих записей не совпадает с указанной строкой, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="3d147-1428">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="3d147-1429">Важно понимать, в каком формате находится общее имя (и записи subjectAltName) в ожидаемых сертификатах.</span><span class="sxs-lookup"><span data-stu-id="3d147-1429">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="3d147-1430">Например, некоторые сертификаты могут использовать необработанный IP-адрес или подстановочный знак.</span><span class="sxs-lookup"><span data-stu-id="3d147-1430">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="3d147-1431">Строка доменов верхнего уровня DNS должна быть отформатирована таким образом, чтоб она соответствовала ожидаемым значениям в полученных сертификатах.</span><span class="sxs-lookup"><span data-stu-id="3d147-1431">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1432">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1432">Parameters</span></span>

- <span data-ttu-id="3d147-1433">**certificate_ptr** — указатель на экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-1433">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="3d147-1434">**dns_tld** — имя домена верхнего уровня для сравнения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1434">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="3d147-1435">**dns_tld_length** — длина строки TLD.</span><span class="sxs-lookup"><span data-stu-id="3d147-1435">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1436">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1436">Return Values</span></span>

- <span data-ttu-id="3d147-1437">**NX_SUCCESS** (0x00) — успешное сравнение с общим именем или subjectAltName.</span><span class="sxs-lookup"><span data-stu-id="3d147-1437">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="3d147-1438">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) — соответствующее имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="3d147-1438">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="3d147-1439">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1439">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1440">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1440">Allowed From</span></span>

<span data-ttu-id="3d147-1441">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1442">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1442">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1443">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1443">See Also</span></span>

- <span data-ttu-id="3d147-1444">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1444">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1445">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1445">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="3d147-1446">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1446">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="3d147-1447">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1447">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="3d147-1448">Проверка сертификата X.509 на соответствие заданному списку отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-1448">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1449">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1449">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="3d147-1450">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1450">Description</span></span>

<span data-ttu-id="3d147-1451">Эта служба принимает список отзыва сертификатов в кодировке DER и ищет конкретный сертификат в этом списке.</span><span class="sxs-lookup"><span data-stu-id="3d147-1451">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="3d147-1452">Издатель списка отзыва сертификатов проверяется на соответствие предоставленному хранилищу сертификатов. Издатель списка отзыва сертификатов должен совпадать с издателем проверяемого сертификата, а серийный номер рассматриваемого сертификата используется для поиска по списку отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-1452">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="3d147-1453">Если издатели совпадают, подпись извлекается, а сертификат **отсутствует** в списке, вызов завершается успешно.</span><span class="sxs-lookup"><span data-stu-id="3d147-1453">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="3d147-1454">Во всех остальных случаях возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="3d147-1454">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1455">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1455">Parameters</span></span>

- <span data-ttu-id="3d147-1456">**crl_data** — указатель на список отзыва сертификатов в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="3d147-1456">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="3d147-1457">**crl_length** — длина данных списка отзыва сертификатов в байтах.</span><span class="sxs-lookup"><span data-stu-id="3d147-1457">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="3d147-1458">**store** — указатель на хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-1458">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="3d147-1459">**certificate_ptr** — указатель на экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-1459">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1460">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1460">Return Values</span></span>

- <span data-ttu-id="3d147-1461">**NX_SUCCESS** (0x00) — успешная проверка того, что сертификат не был отозван.</span><span class="sxs-lookup"><span data-stu-id="3d147-1461">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="3d147-1462">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат издателя списка отзыва сертификатов не найден.</span><span class="sxs-lookup"><span data-stu-id="3d147-1462">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="3d147-1463">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** (0x11B) — сертификат издателя сертификатов не найден.</span><span class="sxs-lookup"><span data-stu-id="3d147-1463">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="3d147-1464">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — список отзыва сертификатов ASN.1 содержит поле недопустимой длины.</span><span class="sxs-lookup"><span data-stu-id="3d147-1464">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="3d147-1465">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG** (0x189) — список отзыва сертификатов содержал недопустимый ASN.1.</span><span class="sxs-lookup"><span data-stu-id="3d147-1465">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="3d147-1466">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) — не удалось проверить цепочку сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-1466">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="3d147-1467">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) — список отзыва сертификатов и издатели сертификатов не совпадают.</span><span class="sxs-lookup"><span data-stu-id="3d147-1467">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="3d147-1468">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** (0x198) — недопустимая подпись списка отзыва сертификатов.</span><span class="sxs-lookup"><span data-stu-id="3d147-1468">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="3d147-1469">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) — проверяемый сертификат был найден в списке отзыва сертификатов и поэтому отозван.</span><span class="sxs-lookup"><span data-stu-id="3d147-1469">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="3d147-1470">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1470">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1471">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1471">Allowed From</span></span>

<span data-ttu-id="3d147-1472">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1473">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1473">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1474">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1474">See Also</span></span>

- <span data-ttu-id="3d147-1475">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1475">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1476">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1476">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="3d147-1477">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1477">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="3d147-1478">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="3d147-1478">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="3d147-1479">Инициализация структуры DNS-имени X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1479">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1480">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1480">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="3d147-1481">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1481">Description</span></span>

<span data-ttu-id="3d147-1482">Эта служба инициализирует DNS-имя X.509 для использования с определенными службами API, для которых необходим определенный формат имени.</span><span class="sxs-lookup"><span data-stu-id="3d147-1482">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="3d147-1483">Например, служба *nx_secure_tls_sni_extension_parse* ожидает объект NX_SECURE_X509_DNS_NAME, чтобы сопоставить имя, которое предоставил удаленный узел в расширении указания имени сервера во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="3d147-1483">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="3d147-1484">DNS-имя — это просто строка символов, которая имеет длину. Максимально допустимой длиной DNS-имени (и размером внутреннего буфера в NX_SECURE_X509_DNS_NAME) управляет макрос NX_SECURE_X509_DNS_NAME_MAX (по умолчанию 100 байт).</span><span class="sxs-lookup"><span data-stu-id="3d147-1484">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1485">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1485">Parameters</span></span>

- <span data-ttu-id="3d147-1486">**dns_name** — структура DNS-имени для инициализации.</span><span class="sxs-lookup"><span data-stu-id="3d147-1486">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="3d147-1487">**name_string** — данные строки DNS-имени.</span><span class="sxs-lookup"><span data-stu-id="3d147-1487">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="3d147-1488">**length** — длина строки имени.</span><span class="sxs-lookup"><span data-stu-id="3d147-1488">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1489">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1489">Return Values</span></span>

- <span data-ttu-id="3d147-1490">**NX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="3d147-1490">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="3d147-1491">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) — заданная строка имени превысила значение NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="3d147-1491">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="3d147-1492">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1492">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1493">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1493">Allowed From</span></span>

<span data-ttu-id="3d147-1494">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1494">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1495">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1495">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="3d147-1496">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1496">See Also</span></span>

- <span data-ttu-id="3d147-1497">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="3d147-1497">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="3d147-1498">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1498">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="3d147-1499">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1499">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="3d147-1500">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1500">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="3d147-1501">Поиск и анализ расширения расширенного использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1501">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1502">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1502">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="3d147-1503">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1503">Description</span></span>

<span data-ttu-id="3d147-1504">Эта служба должна вызываться из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set)* .</span><span class="sxs-lookup"><span data-stu-id="3d147-1504">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="3d147-1505">Она выполнит поиск конкретного идентификатора объекта расширенного использования ключа в сертификате X.509 и возвратит сведения о том, присутствует ли этот идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="3d147-1505">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="3d147-1506">Параметр key_usage — это сопоставление целых чисел идентификаторов объектов, которые используются внутри NetX Secure X.509 и TLS для избежания передачи строк идентификатора объекта переменной длины в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="3d147-1506">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="3d147-1507">Соответствующие идентификаторы объектов для расширения расширенного использования ключа приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="3d147-1507">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="3d147-1508">В типичной реализации клиента TLS, предусматривающей проверку расширенного использования ключа в полученном сертификате сервера TLS, будет выполнена проверка наличия идентификатора объекта NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH. Если расширение есть, а не идентификатора объекта нет, сертификат будет считаться недопустимым для идентификации узла в качестве сервера TLS, а обратный вызов проверки сертификата возвратит ошибку.</span><span class="sxs-lookup"><span data-stu-id="3d147-1508">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="3d147-1509">Приложение может выбирать, требуется ли продолжать подтверждение TLS, если само расширение отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3d147-1509">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="3d147-1510">В обратном вызове проверки сертификата код возврата ошибки NX_SECURE_X509_KEY_USAGE_ERROR зарезервирован для использования приложением.</span><span class="sxs-lookup"><span data-stu-id="3d147-1510">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="3d147-1511">Если при проверке использования ключа возникает ошибка, обратный вызов может возвратить это значение для указания причины сбоя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1511">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="3d147-1512">Идентификатор NetX Secure</span><span class="sxs-lookup"><span data-stu-id="3d147-1512">NetX Secure Identifier</span></span>                                | <span data-ttu-id="3d147-1513">Значение идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="3d147-1513">OID Value</span></span>         | <span data-ttu-id="3d147-1514">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1514">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="3d147-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="3d147-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="3d147-1516">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="3d147-1516">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="3d147-1517">Сертификат можно использовать для определения сервера TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1517">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="3d147-1518">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="3d147-1518">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="3d147-1519">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="3d147-1519">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="3d147-1520">Сертификат можно использовать для определения клиента TLS</span><span class="sxs-lookup"><span data-stu-id="3d147-1520">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="3d147-1521">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="3d147-1521">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="3d147-1522">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="3d147-1522">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="3d147-1523">Сертификат можно использовать для подписи кода</span><span class="sxs-lookup"><span data-stu-id="3d147-1523">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="3d147-1524">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="3d147-1524">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="3d147-1525">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="3d147-1525">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="3d147-1526">Сертификат можно использовать для подписи сообщений электронной почты</span><span class="sxs-lookup"><span data-stu-id="3d147-1526">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="3d147-1527">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="3d147-1527">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="3d147-1528">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="3d147-1528">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="3d147-1529">Сертификат можно использовать для подписи меток времени</span><span class="sxs-lookup"><span data-stu-id="3d147-1529">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="3d147-1530">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="3d147-1530">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="3d147-1531">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="3d147-1531">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="3d147-1532">Сертификат можно использовать для подписи ответов OCSP</span><span class="sxs-lookup"><span data-stu-id="3d147-1532">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="3d147-1533">Идентификаторы объектов и сопоставления для расширения расширенного использования ключа X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1533">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1534">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1534">Parameters</span></span>

- <span data-ttu-id="3d147-1535">**certificate** — указатель на проверяемый сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-1535">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="3d147-1536">**key_usage** — сопоставление целых чисел идентификатора объекта из таблицы выше.</span><span class="sxs-lookup"><span data-stu-id="3d147-1536">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1537">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1537">Return Values</span></span>

- <span data-ttu-id="3d147-1538">**NX_SUCCESS** (0x00) — указанный идентификатор объекта использования ключа найден.</span><span class="sxs-lookup"><span data-stu-id="3d147-1538">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="3d147-1539">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1539">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="3d147-1540">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1540">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1541">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1541">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1542">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1542">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1543">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — расширение расширенного использования ключа не найдено в указанном сертификате.</span><span class="sxs-lookup"><span data-stu-id="3d147-1543">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="3d147-1544">**NX_PTR_ERROR** (0x07) — недопустимый указатель сертификата.</span><span class="sxs-lookup"><span data-stu-id="3d147-1544">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1545">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1545">Allowed From</span></span>

<span data-ttu-id="3d147-1546">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1546">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1547">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1547">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-1548">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1548">See Also</span></span>

- <span data-ttu-id="3d147-1549">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1549">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="3d147-1550">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1550">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="3d147-1551">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1551">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="3d147-1552">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1552">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="3d147-1553">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="3d147-1553">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="3d147-1554">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="3d147-1554">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="3d147-1555">Поиск и возврат расширения X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1555">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1556">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1556">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="3d147-1557">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1557">Description</span></span>

<span data-ttu-id="3d147-1558">Эту службу следует вызывать из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set*). Она является расширенной службой X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-1558">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="3d147-1559">Функция будет искать определенное расширение в сертификате X.509 на основе идентификатора объекта и возвратит сведения о том, присутствует ли идентификатор, а также структуру, содержащую ссылки на соответствующие необработанные данные расширения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1559">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="3d147-1560">Параметр extension_id — это сопоставление целых чисел идентификаторов объектов, которые используются внутри NetX Secure X.509 и TLS для избежания передачи строк идентификатора объекта переменной длины в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="3d147-1560">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="3d147-1561">Вспомогательные функции для конкретных расширений (например, *nx_secure_x509_key_usage_extension_parse*) вызывают nx_secure_x509_extension_find внутренне для получения данных расширения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1561">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="3d147-1562">Соответствующие идентификаторы объектов для известных расширений X.509 приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="3d147-1562">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="3d147-1563">Структура NX_SECURE_X509_EXTENSION содержит указатели на сертификат X.509, которые позволяют вспомогательным функциям, таким как *nx_secure_x509_key_usage_extension_parse*, быстро декодировать необработанные данные расширения ASN.1 в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="3d147-1563">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="3d147-1564">Сведения о конкретных расширениях см. в документе RFC 5280 (спецификация X.509) или в справочнике по соответствующим вспомогательным функциям, если они доступны.</span><span class="sxs-lookup"><span data-stu-id="3d147-1564">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="3d147-1565">Текущая версия NetX Secure X.509 имеет ограниченную поддержку расширений X.509.</span><span class="sxs-lookup"><span data-stu-id="3d147-1565">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="3d147-1566">В будущем будут добавлены дополнительные вспомогательные функции.</span><span class="sxs-lookup"><span data-stu-id="3d147-1566">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d147-1567">*Эта служба является расширенной функцией для пользователей, знакомых с расширениями X.509 и ASN.1 в кодировке DER. Она предоставляет этим пользователям доступ к расширениям, для которых NetX Secure X.509 в данный момент не предоставляет вспомогательные функции. Для этих расширений без вспомогательных функций необходимо самостоятельно анализировать необработанный ASN.1 в кодировке DER.*</span><span class="sxs-lookup"><span data-stu-id="3d147-1567">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="3d147-1568">Идентификатор NetX Secure</span><span class="sxs-lookup"><span data-stu-id="3d147-1568">NetX Secure Identifier</span></span>                              | <span data-ttu-id="3d147-1569">Значение идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="3d147-1569">OID Value</span></span> | <span data-ttu-id="3d147-1570">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1570">Description</span></span>                                                                    | <span data-ttu-id="3d147-1571">Вспомогательная функция?</span><span class="sxs-lookup"><span data-stu-id="3d147-1571">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="3d147-1572">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="3d147-1572">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="3d147-1573">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="3d147-1573">2.5.29.9</span></span>  | <span data-ttu-id="3d147-1574">Атрибуты каталога — это основные атрибуты сведений о субъекте сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-1574">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="3d147-1575">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1575">No</span></span>               |
| <span data-ttu-id="3d147-1576">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="3d147-1576">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="3d147-1577">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="3d147-1577">2.5.29.14</span></span> | <span data-ttu-id="3d147-1578">Используется для определения конкретного открытого ключа</span><span class="sxs-lookup"><span data-stu-id="3d147-1578">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="3d147-1579">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1579">No</span></span>               |
| <span data-ttu-id="3d147-1580">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="3d147-1580">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="3d147-1581">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="3d147-1581">2.5.29.15</span></span> | <span data-ttu-id="3d147-1582">Предоставляет сведения о допустимых методах использования открытого ключа сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-1582">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="3d147-1583">Да</span><span class="sxs-lookup"><span data-stu-id="3d147-1583">Yes</span></span>              |
| <span data-ttu-id="3d147-1584">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="3d147-1584">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="3d147-1585">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="3d147-1585">2.5.29.17</span></span> | <span data-ttu-id="3d147-1586">Предоставляет альтернативные DNS-имена для определения сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-1586">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="3d147-1587">Да<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="3d147-1587">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="3d147-1588">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="3d147-1588">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="3d147-1589">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="3d147-1589">2.5.29.18</span></span> | <span data-ttu-id="3d147-1590">Предоставляет альтернативные DNS-имена для определения издателя сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-1590">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="3d147-1591">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1591">No</span></span>               |
| <span data-ttu-id="3d147-1592">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="3d147-1592">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="3d147-1593">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="3d147-1593">2.5.29.19</span></span> | <span data-ttu-id="3d147-1594">Предоставляет основные сведения об ограничении использования сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-1594">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="3d147-1595">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1595">No</span></span>               |
| <span data-ttu-id="3d147-1596">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="3d147-1596">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="3d147-1597">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="3d147-1597">2.5.29.30</span></span> | <span data-ttu-id="3d147-1598">Используется, чтобы ограничить использование имен сертификатов до конкретных доменов</span><span class="sxs-lookup"><span data-stu-id="3d147-1598">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="3d147-1599">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1599">No</span></span>               |
| <span data-ttu-id="3d147-1600">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="3d147-1600">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="3d147-1601">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="3d147-1601">2.5.29.31</span></span> | <span data-ttu-id="3d147-1602">Предоставляет коды URI для распространения списка отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-1602">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="3d147-1603">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1603">No</span></span>               |
| <span data-ttu-id="3d147-1604">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="3d147-1604">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="3d147-1605">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="3d147-1605">2.5.29.32</span></span> | <span data-ttu-id="3d147-1606">Список политик сертификатов для крупных систем PKI</span><span class="sxs-lookup"><span data-stu-id="3d147-1606">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="3d147-1607">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1607">No</span></span>               |
| <span data-ttu-id="3d147-1608">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="3d147-1608">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="3d147-1609">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="3d147-1609">2.5.29.33</span></span> | <span data-ttu-id="3d147-1610">Список политик сертификатов ЦС</span><span class="sxs-lookup"><span data-stu-id="3d147-1610">List of CA certificate policies</span></span>                                                | <span data-ttu-id="3d147-1611">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1611">No</span></span>               |
| <span data-ttu-id="3d147-1612">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="3d147-1612">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="3d147-1613">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="3d147-1613">2.5.29.35</span></span> | <span data-ttu-id="3d147-1614">Используется для идентификации определенного открытого ключа, связанного с подписью сертификата</span><span class="sxs-lookup"><span data-stu-id="3d147-1614">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="3d147-1615">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1615">No</span></span>               |
| <span data-ttu-id="3d147-1616">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="3d147-1616">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="3d147-1617">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="3d147-1617">2.5.29.36</span></span> | <span data-ttu-id="3d147-1618">Ограничения политики ЦС</span><span class="sxs-lookup"><span data-stu-id="3d147-1618">CA policy constraints</span></span>                                                          | <span data-ttu-id="3d147-1619">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1619">No</span></span>               |
| <span data-ttu-id="3d147-1620">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="3d147-1620">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="3d147-1621">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="3d147-1621">2.5.29.37</span></span> | <span data-ttu-id="3d147-1622">Дополнительные сведения об использовании ключа на основе идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="3d147-1622">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="3d147-1623">Да</span><span class="sxs-lookup"><span data-stu-id="3d147-1623">Yes</span></span>              |
| <span data-ttu-id="3d147-1624">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="3d147-1624">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="3d147-1625">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="3d147-1625">2.5.29.46</span></span> | <span data-ttu-id="3d147-1626">Предоставляет сведения для получения разностных списков отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-1626">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="3d147-1627">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1627">No</span></span>               |
| <span data-ttu-id="3d147-1628">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="3d147-1628">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="3d147-1629">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="3d147-1629">2.5.29.54</span></span> | <span data-ttu-id="3d147-1630">Поле сертификата ЦС, указывающее, что AnyPolicy нельзя использовать</span><span class="sxs-lookup"><span data-stu-id="3d147-1630">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="3d147-1631">Нет</span><span class="sxs-lookup"><span data-stu-id="3d147-1631">No</span></span>               |

<span data-ttu-id="3d147-1632">Идентификаторы объектов и сопоставления для расширений X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1632">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="3d147-1633">Расширение SubjectAltName анализируется как часть проверки DNS-имени в службе nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="3d147-1633">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1634">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1634">Parameters</span></span>

- <span data-ttu-id="3d147-1635">**certificate** — указатель на проверяемый сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-1635">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="3d147-1636">**extension** — возвращает структуру, содержащую указатель и длину данных расширения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1636">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="3d147-1637">**extension_id** — сопоставление целых чисел идентификатора объекта из таблицы выше.</span><span class="sxs-lookup"><span data-stu-id="3d147-1637">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1638">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1638">Return Values</span></span>

- <span data-ttu-id="3d147-1639">**NX_SUCCESS** (0x00) — указанный идентификатор объекта расширения найден, а данные возвращены.</span><span class="sxs-lookup"><span data-stu-id="3d147-1639">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="3d147-1640">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1640">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="3d147-1641">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1641">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1642">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1642">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1643">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение.</span><span class="sxs-lookup"><span data-stu-id="3d147-1643">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="3d147-1644">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — указанный идентификатор объекта расширения не найден в указанном сертификате.</span><span class="sxs-lookup"><span data-stu-id="3d147-1644">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="3d147-1645">**NX_PTR_ERROR** (0x07) — недопустимый сертификат или указатель расширения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1645">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1646">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1646">Allowed From</span></span>

<span data-ttu-id="3d147-1647">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1647">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1648">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1648">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-1649">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1649">See Also</span></span>

- <span data-ttu-id="3d147-1650">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1650">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="3d147-1651">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1651">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="3d147-1652">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1652">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="3d147-1653">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1653">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="3d147-1654">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1654">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="3d147-1655">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1655">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="3d147-1656">Поиск и анализ расширения использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1656">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="3d147-1657">Прототип</span><span class="sxs-lookup"><span data-stu-id="3d147-1657">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="3d147-1658">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1658">Description</span></span>

<span data-ttu-id="3d147-1659">Эта служба должна вызываться из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set)* .</span><span class="sxs-lookup"><span data-stu-id="3d147-1659">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="3d147-1660">Она будет искать расширение использования ключа и, если оно найдено, возвратит битовое поле использования ключа в параметре bitfield.</span><span class="sxs-lookup"><span data-stu-id="3d147-1660">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="3d147-1661">Биты, как определено спецификацией X.509 (RFC 5280), приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="3d147-1661">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="3d147-1662">Побитовое И с соответствующей битовой маской (и проверкой на наличие ненулевого значения) предоставит значение каждому биту.</span><span class="sxs-lookup"><span data-stu-id="3d147-1662">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="3d147-1663">Обратите внимание, что кодировка DER битового поля устраняет лишние нули, поэтому фактическое положение битов в необработанных данных сертификата, скорее всего, будет отличаться от их положений в декодированном битовом поле.</span><span class="sxs-lookup"><span data-stu-id="3d147-1663">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="3d147-1664">Указанные битовые маски предназначены только для использования в декодированных битовых полях, которые возвращает *nx_secure_x509_key_usage_extension_parse*, а не с необработанными данными сертификата в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="3d147-1664">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="3d147-1665">В обратном вызове проверки сертификата код возврата ошибки NX_SECURE_X509_KEY_USAGE_ERROR зарезервирован для использования приложением.</span><span class="sxs-lookup"><span data-stu-id="3d147-1665">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="3d147-1666">Если при проверке использования ключа возникает ошибка, обратный вызов может возвратить это значение для указания причины сбоя.</span><span class="sxs-lookup"><span data-stu-id="3d147-1666">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="3d147-1667">Идентификатор NetX Secure</span><span class="sxs-lookup"><span data-stu-id="3d147-1667">NetX Secure Identifier</span></span>                            | <span data-ttu-id="3d147-1668">Позиции</span><span class="sxs-lookup"><span data-stu-id="3d147-1668">Bit position</span></span> | <span data-ttu-id="3d147-1669">Описание</span><span class="sxs-lookup"><span data-stu-id="3d147-1669">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="3d147-1670">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="3d147-1670">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="3d147-1671">0</span><span class="sxs-lookup"><span data-stu-id="3d147-1671">0</span></span>            | <span data-ttu-id="3d147-1672">Сертификат можно использовать для цифровых подписей</span><span class="sxs-lookup"><span data-stu-id="3d147-1672">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="3d147-1673">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="3d147-1673">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="3d147-1674">1</span><span class="sxs-lookup"><span data-stu-id="3d147-1674">1</span></span>            | <span data-ttu-id="3d147-1675">Сертификат можно использовать для проверки цифровых подписей, кроме подписей для сертификатов и списков отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-1675">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="3d147-1676">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="3d147-1676">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="3d147-1677">2</span><span class="sxs-lookup"><span data-stu-id="3d147-1677">2</span></span>            | <span data-ttu-id="3d147-1678">Сертификат можно использовать для шифрования симметричных ключей (транспорт ключей)</span><span class="sxs-lookup"><span data-stu-id="3d147-1678">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="3d147-1679">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="3d147-1679">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="3d147-1680">3</span><span class="sxs-lookup"><span data-stu-id="3d147-1680">3</span></span>            | <span data-ttu-id="3d147-1681">Сертификат можно использовать для прямого шифрования необработанных данных пользователя (редко)</span><span class="sxs-lookup"><span data-stu-id="3d147-1681">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="3d147-1682">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="3d147-1682">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="3d147-1683">4</span><span class="sxs-lookup"><span data-stu-id="3d147-1683">4</span></span>            | <span data-ttu-id="3d147-1684">Сертификат можно использовать для согласования ключей (как в случае Диффи-Хелмана)</span><span class="sxs-lookup"><span data-stu-id="3d147-1684">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="3d147-1685">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="3d147-1685">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="3d147-1686">5</span><span class="sxs-lookup"><span data-stu-id="3d147-1686">5</span></span>            | <span data-ttu-id="3d147-1687">Сертификат можно использовать для подписи и проверки других сертификатов (сертификат относится к ЦС или ICA).</span><span class="sxs-lookup"><span data-stu-id="3d147-1687">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="3d147-1688">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="3d147-1688">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="3d147-1689">6</span><span class="sxs-lookup"><span data-stu-id="3d147-1689">6</span></span>            | <span data-ttu-id="3d147-1690">Открытый ключ сертификата используется для проверки подписей в списках отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="3d147-1690">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="3d147-1691">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="3d147-1691">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="3d147-1692">7</span><span class="sxs-lookup"><span data-stu-id="3d147-1692">7</span></span>            | <span data-ttu-id="3d147-1693">Используется с битом согласования ключей (бит 4). После установки ключ сертификата можно использовать только для шифрования во время согласования ключей.</span><span class="sxs-lookup"><span data-stu-id="3d147-1693">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="3d147-1694">Значение не определено, если бит согласования ключей не установлен.</span><span class="sxs-lookup"><span data-stu-id="3d147-1694">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="3d147-1695">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="3d147-1695">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="3d147-1696">8</span><span class="sxs-lookup"><span data-stu-id="3d147-1696">8</span></span>            | <span data-ttu-id="3d147-1697">Используется с битом согласования ключей (бит 4). После установки ключ сертификата можно использовать только для расшифровки во время согласования ключей.</span><span class="sxs-lookup"><span data-stu-id="3d147-1697">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="3d147-1698">Значение не определено, если бит согласования ключей не установлен.</span><span class="sxs-lookup"><span data-stu-id="3d147-1698">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="3d147-1699">Битовые маски и значения для расширения использования ключа X.509</span><span class="sxs-lookup"><span data-stu-id="3d147-1699">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="3d147-1700">Параметры</span><span class="sxs-lookup"><span data-stu-id="3d147-1700">Parameters</span></span>

- <span data-ttu-id="3d147-1701">**certificate** — указатель на проверяемый сертификат.</span><span class="sxs-lookup"><span data-stu-id="3d147-1701">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="3d147-1702">**bitfield** — возврат всего битового поля из расширения.</span><span class="sxs-lookup"><span data-stu-id="3d147-1702">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="3d147-1703">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="3d147-1703">Return Values</span></span>

- <span data-ttu-id="3d147-1704">**NX_SUCCESS** (0x00) — найдено расширение использования ключа и возвращено битовое поле.</span><span class="sxs-lookup"><span data-stu-id="3d147-1704">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="3d147-1705">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1705">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="3d147-1706">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1706">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1707">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1707">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1708">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="3d147-1708">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="3d147-1709">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — расширение использования ключа не найдено в указанном сертификате.</span><span class="sxs-lookup"><span data-stu-id="3d147-1709">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="3d147-1710">**NX_PTR_ERROR** (0x07) — недопустимый сертификат или указатель битового поля.</span><span class="sxs-lookup"><span data-stu-id="3d147-1710">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="3d147-1711">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="3d147-1711">Allowed From</span></span>

<span data-ttu-id="3d147-1712">Потоки</span><span class="sxs-lookup"><span data-stu-id="3d147-1712">Threads</span></span>

### <a name="example"></a><span data-ttu-id="3d147-1713">Пример</span><span class="sxs-lookup"><span data-stu-id="3d147-1713">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="3d147-1714">См. также:</span><span class="sxs-lookup"><span data-stu-id="3d147-1714">See Also</span></span>

- <span data-ttu-id="3d147-1715">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="3d147-1715">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="3d147-1716">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="3d147-1716">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="3d147-1717">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1717">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="3d147-1718">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="3d147-1718">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="3d147-1719">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="3d147-1719">nx_secure_x509_extension_find</span></span>
