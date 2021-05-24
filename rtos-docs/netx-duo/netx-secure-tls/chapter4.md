---
title: Глава 4. Описание служб NetX Secure для ОСРВ Azure
description: В этой главе приведено описание всех служб NetX Secure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 80ec22058ab64ed0c6258bb3d9364ec44f9a741b
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223398"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="7d037-103">Глава 4. Описание служб NetX Secure для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="7d037-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="7d037-104">В этой главе приведено описание всех служб NetX Secure для ОСРВ Azure, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="7d037-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="7d037-105">В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, выделенные **полужирным шрифтом**, не затрагиваются макросом **NX_SECURE_DISABLE_ERROR_CHECKING**, который используется для отключения проверки API на предмет ошибок. Значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="7d037-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="7d037-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="7d037-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="7d037-107">Выполнение самостоятельного тестирования для методов шифрования</span><span class="sxs-lookup"><span data-stu-id="7d037-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="7d037-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="7d037-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="7d037-109">Вычисление хэш-значения с помощью пользовательской хэш-функции</span><span class="sxs-lookup"><span data-stu-id="7d037-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="7d037-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="7d037-111">Установка активного сертификата удостоверения для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="7d037-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="7d037-113">Установка общего ключа для сеанса клиента NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="7d037-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="7d037-115">Инициализация модуля NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="7d037-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="7d037-117">Добавление локального сертификата в сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="7d037-119">Поиск локального сертификата в сеансе NetX Secure TLS по общему имени</span><span class="sxs-lookup"><span data-stu-id="7d037-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="7d037-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="7d037-121">Удалить локальный сертификат из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="7d037-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="7d037-123">Вычисление размера криптографических метаданных для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="7d037-125">Выделение пакета для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="7d037-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="7d037-127">Добавление общего ключа в сеанс TLS в NetX Secure</span><span class="sxs-lookup"><span data-stu-id="7d037-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="7d037-129">Выделение пространства для сертификата, предоставленного удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="7d037-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="7d037-131">Выделение пространства для всех сертификатов, предоставленных удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="7d037-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="7d037-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="7d037-133">Освобождение места, выделенного для входящих сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="7d037-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="7d037-135">Добавление сертификата специально для серверов TLS с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="7d037-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="7d037-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="7d037-137">Поиск сертификата по числовому идентификатору</span><span class="sxs-lookup"><span data-stu-id="7d037-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="7d037-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="7d037-139">Удаление сертификата локального сервера с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="7d037-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="7d037-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="7d037-141">Настройка обратного вызова для протокола TLS, который будет использоваться для дополнительной проверки сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="7d037-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="7d037-143">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения клиента TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="7d037-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="7d037-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="7d037-145">Включение проверки X.509 клиента и выделение места для сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="7d037-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="7d037-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="7d037-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="7d037-147">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7d037-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="7d037-149">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="7d037-151">Создание сеанса NetX Secure TLS для обеспечения безопасности подключений</span><span class="sxs-lookup"><span data-stu-id="7d037-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="7d037-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="7d037-153">Удаление сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="7d037-155">Завершение активного сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="7d037-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="7d037-157">Установка буфера повторной сборки пакетов для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="7d037-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="7d037-159">Переопределение версии протокола TLS по умолчанию для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="7d037-161">Получение данных из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="7d037-163">Назначение обратного вызова, который будет выполняться в начале повторного согласования сеанса</span><span class="sxs-lookup"><span data-stu-id="7d037-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="7d037-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="7d037-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="7d037-165">Инициация подтверждения повторного согласования сеанса с удаленным узлом</span><span class="sxs-lookup"><span data-stu-id="7d037-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="7d037-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="7d037-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="7d037-167">Очистка и сброс сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="7d037-169">Отправка данных через сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="7d037-171">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения сервера TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="7d037-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="7d037-173">Анализ расширения указания имени сервера (SNI), полученного от клиента TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="7d037-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="7d037-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="7d037-175">Установка DNS-имени расширения указания имени сервера (SNI) для отправки на удаленный сервер</span><span class="sxs-lookup"><span data-stu-id="7d037-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="7d037-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="7d037-177">Запуск сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="7d037-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="7d037-179">Назначение функции метки времени в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="7d037-181">Добавление доверенного сертификата в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="7d037-183">Удаление доверенного сертификата из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="7d037-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="7d037-185">Инициализация сертификата X.509 для NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="7d037-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="7d037-187">Проверка DNS-имени на соответствие сертификату X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="7d037-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="7d037-189">Проверка сертификата X.509 на соответствие заданному списку отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="7d037-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="7d037-191">Инициализация структуры DNS-имени X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="7d037-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="7d037-193">Поиск и анализ расширения расширенного использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="7d037-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7d037-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="7d037-195">Поиск и возврат расширения X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="7d037-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="7d037-197">Поиск и анализ расширения использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="7d037-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="7d037-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="7d037-199">Выполнение самостоятельного тестирования для методов шифрования</span><span class="sxs-lookup"><span data-stu-id="7d037-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="7d037-201">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-201">Description</span></span>

<span data-ttu-id="7d037-202">Эта служба выполняет самостоятельное тестирование методов шифрования для проверки.</span><span class="sxs-lookup"><span data-stu-id="7d037-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="7d037-203">Самостоятельное тестирование доступно только в том случае, если библиотека NetX Secure создана с определенным символом NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK.</span><span class="sxs-lookup"><span data-stu-id="7d037-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="7d037-204">Для каждого поддерживаемого метода шифрования самостоятельное тестирование предоставляет предварительно определенные входные данные и проверяет их на соответствие предварительно определенному ожидаемому значению.</span><span class="sxs-lookup"><span data-stu-id="7d037-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="7d037-205">Самостоятельное тестирование шифрования NetX Secure поддерживает следующие алгоритмы и размеры ключей:</span><span class="sxs-lookup"><span data-stu-id="7d037-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="7d037-206">DES: шифрование и расшифровка;</span><span class="sxs-lookup"><span data-stu-id="7d037-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="7d037-207">Triple DES (3DES): шифрование и расшифровка;</span><span class="sxs-lookup"><span data-stu-id="7d037-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="7d037-208">AES: 128-, 192-, 256-битный размер ключа, шифрование и расшифровка в режиме CBC и режиме счетчика;</span><span class="sxs-lookup"><span data-stu-id="7d037-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="7d037-209">HMAC-MD5: проверка подлинности и вычисление хэша;</span><span class="sxs-lookup"><span data-stu-id="7d037-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="7d037-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2-512, проверка подлинности и вычисление хэша;</span><span class="sxs-lookup"><span data-stu-id="7d037-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="7d037-211">MD5: проверка подлинности;</span><span class="sxs-lookup"><span data-stu-id="7d037-211">MD5: authentication</span></span>
- <span data-ttu-id="7d037-212">псевдослучайная функция (PRF): PRF_HMAC_SHA1 и PRF_HMAC_SHA2-256;</span><span class="sxs-lookup"><span data-stu-id="7d037-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="7d037-213">RSA: 1024-, 2048-, 4096-битная операция модуля питания RSA;</span><span class="sxs-lookup"><span data-stu-id="7d037-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="7d037-214">SHA: проверка подлинности SHA1 (96- и 160-битная), SHA2 (256-, 384-, 512-битная).</span><span class="sxs-lookup"><span data-stu-id="7d037-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="7d037-215">Эта функция имеет встроенные векторы для алгоритмов шифрования, перечисленных выше.</span><span class="sxs-lookup"><span data-stu-id="7d037-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="7d037-216">Однако она проверяет только алгоритмы, перечисленные в параметре *cipher_table*, переданном в эту функцию.</span><span class="sxs-lookup"><span data-stu-id="7d037-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="7d037-217">Например, для сеанса TLS используется только набор шифров TLS_RSA_WITH_AES_128_CBC_SHA. Эта функция выполняет самостоятельное тестирование в RSA (1024-, 2048-, 4096-битные), AES-CBC (128-битный) и SHA1.</span><span class="sxs-lookup"><span data-stu-id="7d037-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-218">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-218">Parameters</span></span>

- <span data-ttu-id="7d037-219">**crypto_table** — указатель на таблицу шифрования, используемую сеансом TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="7d037-220">Это тот же параметр crypto_table, который передается в вызов **_nx_secure_tls_session_create()_**.</span><span class="sxs-lookup"><span data-stu-id="7d037-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="7d037-221">**metadata** — указатель на пространство для области метаданных шифрования.</span><span class="sxs-lookup"><span data-stu-id="7d037-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="7d037-222">.</span><span class="sxs-lookup"><span data-stu-id="7d037-222">.</span></span>
- <span data-ttu-id="7d037-223">**metadata_size** — размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="7d037-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-224">Return Values</span></span>

- <span data-ttu-id="7d037-225">**NX_SECURE_TLS_SUCCESS** (0x00) — предоставленные методы шифрования успешно протестированы.</span><span class="sxs-lookup"><span data-stu-id="7d037-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="7d037-226">**NX_PTR_ERROR** (0x07) — недопустимая структура метода шифрования.</span><span class="sxs-lookup"><span data-stu-id="7d037-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="7d037-227">**NX_NOT_SUCCESSFUL** (0x43) — сбой самостоятельного тестирования шифрования.</span><span class="sxs-lookup"><span data-stu-id="7d037-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-228">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-228">Allowed From</span></span>

<span data-ttu-id="7d037-229">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-230">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-230">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-231">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-231">See Also</span></span>

- <span data-ttu-id="7d037-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="7d037-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="7d037-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="7d037-234">Вычисление хэш-значения с помощью пользовательской хэш-функции</span><span class="sxs-lookup"><span data-stu-id="7d037-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-235">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="7d037-236">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-236">Description</span></span>

<span data-ttu-id="7d037-237">Эта функция вычисляет хэш-значение потока данных в указанной области памяти, используя указанный метод шифрования HMAC и строку ключа.</span><span class="sxs-lookup"><span data-stu-id="7d037-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="7d037-238">Функция вычисления хэша модуля доступна, только если библиотека NetX Secure создана со следующим определяемым символом: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="7d037-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-239">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-239">Parameters</span></span>

- <span data-ttu-id="7d037-240">**hmac_ptr** — указатель на метод шифрования HMAC, используемый для вычисления хэш-значения.</span><span class="sxs-lookup"><span data-stu-id="7d037-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="7d037-241">**start_address** — начальный адрес буфера данных.</span><span class="sxs-lookup"><span data-stu-id="7d037-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="7d037-242">**end_address** — конечный адрес буфера данных.</span><span class="sxs-lookup"><span data-stu-id="7d037-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="7d037-243">Обратите внимание, что вычисление хэша не распространяется на данные, расположенные по этому адресу end_address.</span><span class="sxs-lookup"><span data-stu-id="7d037-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="7d037-244">**key** — строка ключа, используемая в вычислении HMAC.</span><span class="sxs-lookup"><span data-stu-id="7d037-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="7d037-245">**key_length** — размер строки ключа в байтах.</span><span class="sxs-lookup"><span data-stu-id="7d037-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="7d037-246">**metadata** — указатель на пространство, используемое алгоритмом HMAC.</span><span class="sxs-lookup"><span data-stu-id="7d037-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="7d037-247">**metadata_size** — размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="7d037-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="7d037-248">**output_buffer** — место в памяти, где хранятся выходные данные хэша.</span><span class="sxs-lookup"><span data-stu-id="7d037-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="7d037-249">**output_buffer_size** — доступное место в буфере вывода в байтах.</span><span class="sxs-lookup"><span data-stu-id="7d037-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="7d037-250">**actual_size** — параметр, возвращаемый функцией, которая указывает фактическое число байтов, записываемых в параметр output_buffer.</span><span class="sxs-lookup"><span data-stu-id="7d037-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-251">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-251">Return Values</span></span>

- <span data-ttu-id="7d037-252">**0** — вычисление хэш-значения успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="7d037-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="7d037-253">**1** — не удалось выполнить вычисление хэша.</span><span class="sxs-lookup"><span data-stu-id="7d037-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-254">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-254">Allowed From</span></span>

<span data-ttu-id="7d037-255">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-256">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-256">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-257">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-257">See Also</span></span>

- <span data-ttu-id="7d037-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="7d037-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="7d037-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="7d037-260">Установка активного сертификата удостоверения для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-261">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="7d037-262">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-262">Description</span></span>

<span data-ttu-id="7d037-263">Эта служба должна вызываться из обратного вызова сеанса (см. nx_secure_tls_session_client_callback_set и nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="7d037-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="7d037-264">При вызове с ранее инициализированной структурой NX_SECURE_X509_CERT этот сертификат будет использоваться вместо сертификата удостоверения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7d037-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="7d037-265">В большинстве случаев сертификат необходимо добавить в локальное хранилище (см. nx_secure_tls_local_certificate_add), иначе подтверждение TLS может завершиться ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="7d037-266">Эта служба предназначена для того, чтобы протокол TLS поддерживал несколько сертификатов удостоверений.</span><span class="sxs-lookup"><span data-stu-id="7d037-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="7d037-267">Это полезно для сервера TLS, который обслуживает несколько сетевых адресов, чтобы сервер мог выбрать соответствующий сертификат для удаленного клиента в зависимости от точки входа клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="7d037-268">В клиенте TLS эту подпрограмму можно использовать для изменения сертификата, отправленного на удаленный сервер во время выполнения, после идентификации сервера в подтверждении TLS (это происходит реже, чем в случае использования сервера TLS).</span><span class="sxs-lookup"><span data-stu-id="7d037-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="7d037-269">Если несколько сертификатов могут совместно использовать одно и то же различающееся имя X.509, их необходимо добавить с использованием параметра nx_secure_tls_server_certificate_add, который представляет числовой идентификатор, отделенный от сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-270">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-270">Parameters</span></span>

- <span data-ttu-id="7d037-271">**session_ptr** — указатель на экземпляр сеанса TLS, переданный в обратный вызов сеанса.</span><span class="sxs-lookup"><span data-stu-id="7d037-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="7d037-272">**certificate** — указатель на инициализированный сертификат X.509, который будет использоваться в текущем сеансе.</span><span class="sxs-lookup"><span data-stu-id="7d037-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-273">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-273">Return Values</span></span>

- <span data-ttu-id="7d037-274">**NX_SUCCESS** (0x00) — сертификат успешно назначен сеансу.</span><span class="sxs-lookup"><span data-stu-id="7d037-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="7d037-275">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-276">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-276">Allowed From</span></span>

<span data-ttu-id="7d037-277">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-278">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-278">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-279">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-279">See Also</span></span>

- <span data-ttu-id="7d037-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7d037-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="7d037-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="7d037-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7d037-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="7d037-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="7d037-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="7d037-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="7d037-288">Установка общего ключа для сеанса клиента NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-289">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="7d037-290">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-290">Description</span></span>

<span data-ttu-id="7d037-291">Эта служба добавляет общий ключ (PSK), строку идентификатора и указание удостоверения в блок управления сеансом TLS и задает использование этого PSK в последующих подключениях клиентов TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="7d037-292">Если включены и используются наборы шифров PSK, то вместо цифрового сертификата используется PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="7d037-293">В этом случае PSK связывается с конкретным удаленным сервером TLS, с которым клиент TLS будет обмениваться данными.</span><span class="sxs-lookup"><span data-stu-id="7d037-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="7d037-294">PSK, заданный через этот API, будет предоставляться узлу удаленного сервера TLS во время следующего подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-295">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-295">Parameters</span></span>

- <span data-ttu-id="7d037-296">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-297">**pre_shared_key** — фактическое значение PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="7d037-298">**psk_length**: длина значения PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="7d037-299">**psk_identity**: строка, используемая для идентификации этого значения PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="7d037-300">**identity_length**: длина удостоверения PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="7d037-301">**hint**: строка, используемая для выбора группы PSK на сервере TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="7d037-302">**hint_length**: длина строки указания.</span><span class="sxs-lookup"><span data-stu-id="7d037-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-303">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-303">Return Values</span></span>

- <span data-ttu-id="7d037-304">**NX_SUCCESS** (0x00) — успешное добавление PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="7d037-305">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) — невозможно добавить еще один PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-307">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-307">Allowed From</span></span>

<span data-ttu-id="7d037-308">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-309">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-310">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-310">See Also</span></span>

- <span data-ttu-id="7d037-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="7d037-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="7d037-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="7d037-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="7d037-317">Инициализация модуля NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-318">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="7d037-319">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-319">Description</span></span>

<span data-ttu-id="7d037-320">Эта служба инициализирует модуль NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="7d037-321">Его необходимо вызвать до доступа к другим службам NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="7d037-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-322">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-322">Parameters</span></span>

<span data-ttu-id="7d037-323">None</span><span class="sxs-lookup"><span data-stu-id="7d037-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-324">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-324">Return Values</span></span>

<span data-ttu-id="7d037-325">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-326">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-326">Allowed From</span></span>

<span data-ttu-id="7d037-327">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-328">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="7d037-329">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-329">See Also</span></span>

- <span data-ttu-id="7d037-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="7d037-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="7d037-332">Добавление локального сертификата в сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-333">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-334">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-334">Description</span></span>

<span data-ttu-id="7d037-335">Эта служба добавляет инициализированный экземпляр структуры NX_SECURE_X509_CERT в локальное хранилище сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="7d037-336">Этот сертификат может использоваться стеком TLS для идентификации устройства во время подтверждения TLS (если оно было помечено как сертификат удостоверения во время инициализации структуры сертификата с помощью nx_secure_x509_certificate_initialize) или в качестве издателя в составе цепочки сертификатов, предоставленной удаленному узлу во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="7d037-337">Если требуется несколько локальных сертификатов с одинаковым общим именем, их можно добавить с помощью службы *nx_secure_tls_server_certificate_add* (см. предупреждение ниже).</span><span class="sxs-lookup"><span data-stu-id="7d037-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="7d037-338">Сертификат **требуется** для режима сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="7d037-339">Для режима клиента TLS сертификат *необязателен*.</span><span class="sxs-lookup"><span data-stu-id="7d037-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-340">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.</span><span class="sxs-lookup"><span data-stu-id="7d037-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-341">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-341">Parameters</span></span>

- <span data-ttu-id="7d037-342">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-343">**certificate_ptr** — указатель на инициализированный экземпляр сертификата TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-344">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-344">Return Values</span></span>

- <span data-ttu-id="7d037-345">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7d037-346">**NX_INVALID_PARAMETERS** (0x4D) — выполнена попытка добавления недопустимого сертификата или дубликата сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="7d037-347">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-348">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-348">Allowed From</span></span>

<span data-ttu-id="7d037-349">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-350">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-351">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-351">See Also</span></span>

- <span data-ttu-id="7d037-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="7d037-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="7d037-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="7d037-358">Поиск локального сертификата в сеансе NetX Secure TLS по общему имени</span><span class="sxs-lookup"><span data-stu-id="7d037-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-359">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="7d037-360">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-360">Description</span></span>

<span data-ttu-id="7d037-361">Эта служба находит сертификат в хранилище сертификатов локального устройства в сеансе TLS и возвращает указатель на структуру NX_SECURE_X509_CERT в хранилище.</span><span class="sxs-lookup"><span data-stu-id="7d037-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="7d037-362">Параметр common_name и его длина (name_length) используются для обнаружения сертификата в хранилище путем сопоставления поля общего имени субъекта X.509 сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="7d037-363">При наличии нескольких сертификатов с одним общим именем будет возвращен только первый из них. Используйте *nx_secure_tls_server_certificate_find*.</span><span class="sxs-lookup"><span data-stu-id="7d037-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-364">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.</span><span class="sxs-lookup"><span data-stu-id="7d037-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-365">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-365">Parameters</span></span>

- <span data-ttu-id="7d037-366">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-367">**certificate** — возврат указателя на сопоставленный сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="7d037-368">**common_name** — строка общего имени для сопоставления (DNS-имя).</span><span class="sxs-lookup"><span data-stu-id="7d037-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="7d037-369">**name_length** — длина строковых данных параметра common_name.</span><span class="sxs-lookup"><span data-stu-id="7d037-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-370">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-370">Return Values</span></span>

- <span data-ttu-id="7d037-371">**NX_SUCCESS** (0x00) — сертификат найден, а указатель возвращен в параметре certificate.</span><span class="sxs-lookup"><span data-stu-id="7d037-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="7d037-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат с указанным общим именем не найден.</span><span class="sxs-lookup"><span data-stu-id="7d037-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="7d037-373">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS, указатель сертификата или строка общего имени.</span><span class="sxs-lookup"><span data-stu-id="7d037-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-374">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-374">Allowed From</span></span>

<span data-ttu-id="7d037-375">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-376">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-376">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-377">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-377">See Also</span></span>

- <span data-ttu-id="7d037-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="7d037-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="7d037-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="7d037-384">Удалить локальный сертификат из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-385">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="7d037-386">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-386">Description</span></span>

<span data-ttu-id="7d037-387">Эта служба удаляет экземпляр локального сертификата из сеанса TLS, введенный в поле общего имени сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-388">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_server_certificate_add. API сертификата сервера использует уникальный числовой идентификатор для каждого сертификата, а nx_secure_tls_local_certificate_add использует индексы на основе общего имени X.509. Службы локальных сертификатов предоставляют удобную альтернативу числовому идентификатору для приложений, использующих только один сертификат удостоверения — общее имя. Приложению не нужно отслеживать числовые идентификаторы*.</span><span class="sxs-lookup"><span data-stu-id="7d037-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-389">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-389">Parameters</span></span>

- <span data-ttu-id="7d037-390">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-391">**common_name** — значение общего имени удаляемого сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="7d037-392">**common_name_length** — длина строки общего имени.</span><span class="sxs-lookup"><span data-stu-id="7d037-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-393">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-393">Return Values</span></span>

- <span data-ttu-id="7d037-394">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7d037-395">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат не найден.</span><span class="sxs-lookup"><span data-stu-id="7d037-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-397">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-397">Allowed From</span></span>

<span data-ttu-id="7d037-398">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-399">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-400">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-400">See Also</span></span>

- <span data-ttu-id="7d037-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="7d037-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="7d037-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="7d037-406">Вычисление размера криптографических метаданных для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-407">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="7d037-408">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-408">Description</span></span>

<span data-ttu-id="7d037-409">Эта служба вычисляет и возвращает размер криптографических метаданных, необходимых для конкретного сеанса TLS и таблицы шифрования TLS (дополнительные сведения о таблице криптографических шифров см. в разделе «Инициализация TLS с помощью методов шифрования»).</span><span class="sxs-lookup"><span data-stu-id="7d037-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="7d037-410">Эту службу следует вызывать вместе с необходимой криптографической таблицей для вычисления размера буфера метаданных, переданного в nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="7d037-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-411">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-411">Parameters</span></span>

- <span data-ttu-id="7d037-412">**crypto_table** — указатель на заполненную таблицу шифрования NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="7d037-413">**metadata_size** — выходные данные вычисления размера в байтах.</span><span class="sxs-lookup"><span data-stu-id="7d037-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-414">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-414">Return Values</span></span>

- <span data-ttu-id="7d037-415">**NX_SUCCESS** (0x00) — вычисление размера метаданных выполнено успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="7d037-416">**NX_PTR_ERROR** (0x07) — недопустимая таблица шифрования или указатель на возвращаемый размер.</span><span class="sxs-lookup"><span data-stu-id="7d037-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-417">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-417">Allowed From</span></span>

<span data-ttu-id="7d037-418">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-419">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-419">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-420">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-420">See Also</span></span>

- <span data-ttu-id="7d037-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="7d037-422">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-422">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="7d037-423">Выделение пакета для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-423">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-424">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-424">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d037-425">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-425">Description</span></span>

<span data-ttu-id="7d037-426">Эта служба выделяет пакет NX_PACKET для указанного активного сеанса TLS из заданного пула NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="7d037-426">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="7d037-427">Приложение должно вызывать эту службу для выделения пакетов данных, которые отправляют через подключение TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-427">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="7d037-428">Перед вызовом этой службы необходимо инициализировать сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-428">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="7d037-429">Выделенный пакет инициализируется таким образом, чтобы после заполнения данных пакета можно было добавить данные верхнего и нижнего колонтитулов TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-429">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="7d037-430">В противном случае поведение идентично службе *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="7d037-430">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-431">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-431">Parameters</span></span>

- <span data-ttu-id="7d037-432">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-432">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-433">**pool_ptr** — указатель на пул NX_PACKET_POOL, из которого выделяется пакет.</span><span class="sxs-lookup"><span data-stu-id="7d037-433">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="7d037-434">**packet_ptr**: указатель вывода на выделенный пакет.</span><span class="sxs-lookup"><span data-stu-id="7d037-434">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="7d037-435">**wait_option**: параметр приостановки выделения пакетов.</span><span class="sxs-lookup"><span data-stu-id="7d037-435">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-436">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-436">Return Values</span></span>

- <span data-ttu-id="7d037-437">**NX_SUCCESS** (0x00) — пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-437">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="7d037-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить базовый пакет.</span><span class="sxs-lookup"><span data-stu-id="7d037-438">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="7d037-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-439">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-440">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-440">Allowed From</span></span>

<span data-ttu-id="7d037-441">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-442">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-442">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-443">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-443">See Also</span></span>

- <span data-ttu-id="7d037-444">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-444">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7d037-445">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-445">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-446">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-446">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-447">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-447">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-448">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-448">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-449">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-449">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-450">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-450">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-451">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-451">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7d037-452">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-452">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="7d037-453">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="7d037-453">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="7d037-454">Добавление общего ключа в сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-454">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-455">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-455">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="7d037-456">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-456">Description</span></span>

<span data-ttu-id="7d037-457">Эта служба добавляет общий ключ (PSK), строку удостоверения и указание удостоверения в блок управления сеансом TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-457">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="7d037-458">Если включены и используются наборы шифров PSK, то вместо цифрового сертификата используется PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-458">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-459">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-459">Parameters</span></span>

- <span data-ttu-id="7d037-460">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-460">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-461">**pre_shared_key** — фактическое значение PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-461">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="7d037-462">**psk_length**: длина значения PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-462">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="7d037-463">**psk_identity**: строка, используемая для идентификации этого значения PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-463">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="7d037-464">**identity_length**: длина удостоверения PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-464">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="7d037-465">**hint**: строка, используемая для выбора группы PSK на сервере TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-465">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="7d037-466">**hint_length**: длина строки указания.</span><span class="sxs-lookup"><span data-stu-id="7d037-466">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-467">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-467">Return Values</span></span>

- <span data-ttu-id="7d037-468">**NX_SUCCESS** (0x00) — успешное добавление PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-468">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="7d037-469">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-469">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) — невозможно добавить еще один PSK.</span><span class="sxs-lookup"><span data-stu-id="7d037-470">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-471">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-471">Allowed From</span></span>

<span data-ttu-id="7d037-472">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-473">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-473">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-474">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-474">See Also</span></span>

- <span data-ttu-id="7d037-475">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="7d037-475">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="7d037-476">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-476">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-477">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-477">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-478">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-478">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-479">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-479">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="7d037-480">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-480">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="7d037-481">Выделение пространства для сертификата, предоставленного удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-481">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-482">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-482">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="7d037-483">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-483">Description</span></span>

<span data-ttu-id="7d037-484">Эта служба добавляет неинициализированный экземпляр структуры NX_SECURE_X509_CERT в сеанс TLS с целью выделения места для сертификатов, которые предоставляет удаленный узел во время сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-484">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="7d037-485">Данные удаленного сертификата анализируются с помощью NetX Secure TLS. Эти сведения затем используют для заполнения экземпляра структуры сертификата, предоставленного в эту функцию.</span><span class="sxs-lookup"><span data-stu-id="7d037-485">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="7d037-486">Сертификаты, добавленные таким способом, помещаются в связанный список.</span><span class="sxs-lookup"><span data-stu-id="7d037-486">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="7d037-487">Если предполагается, что удаленный узел предоставит несколько сертификатов, эту функцию следует вызывать повторно, чтобы выделить место для всех сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-487">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="7d037-488">Дополнительные сертификаты добавляются в конец связанного списка сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-488">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="7d037-489">Сбой выделения удаленного сертификата приведет к сбою режима клиента TLS во время подтверждения TLS, если не используется набор шифров для общего ключа (PSK).</span><span class="sxs-lookup"><span data-stu-id="7d037-489">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="7d037-490">Параметр *raw_certificate_buffer* указывает на место, выделенное для хранения входящего удаленного сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-490">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="7d037-491">Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов.</span><span class="sxs-lookup"><span data-stu-id="7d037-491">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="7d037-492">Буфер должен быть достаточно большим, чтобы вместить этот размер, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше.</span><span class="sxs-lookup"><span data-stu-id="7d037-492">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="7d037-493">Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-493">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="7d037-494">Для режима сервера TLS удаленное выделение сертификатов требуется только в том случае, если включена проверка подлинности с помощью сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-494">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-495">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-495">Parameters</span></span>

- <span data-ttu-id="7d037-496">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-496">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-497">**certificate_ptr** — указатель на неинициализированный экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-497">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="7d037-498">**raw_certificate_buffer** — указатель на буфер для хранения непроанализированного сертификата, полученного с удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-498">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="7d037-499">**buffer_size** — размер необработанного буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-499">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-500">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-500">Return Values</span></span>

- <span data-ttu-id="7d037-501">**NX_SUCCESS** (0x00) — сертификат успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="7d037-501">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="7d037-502">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-502">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="7d037-503">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="7d037-504">**NX_INVALID_PARAMETERS** (0x4D) — попытка добавить недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-504">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-505">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-505">Allowed From</span></span>

<span data-ttu-id="7d037-506">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-507">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-507">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-508">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-508">See Also</span></span>

- <span data-ttu-id="7d037-509">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="7d037-509">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="7d037-510">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-510">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="7d037-511">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-511">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="7d037-512">Выделение пространства для всех сертификатов, предоставленных удаленным узлом TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-512">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-513">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-513">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7d037-514">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-514">Description</span></span>

<span data-ttu-id="7d037-515">Эта служба выделяет место для обработки входящих цепочек сертификатов с удаленных узлов сервера для выполнения проверки подлинности X.509 и проверки в экземпляре клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-515">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="7d037-516">Для режима сервера TLS удаленное выделение сертификатов требуется только в том случае, если включена проверка подлинности клиента X.509. Для экземпляров сервера TLS следует использовать службу *nx_secure_tls_session_x509_client_verify_configure*.</span><span class="sxs-lookup"><span data-stu-id="7d037-516">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="7d037-517">Сбой выделения удаленных сертификатов приведет к сбою режима клиента TLS во время подтверждения TLS, если не используется набор шифров для общего ключа (PSK).</span><span class="sxs-lookup"><span data-stu-id="7d037-517">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="7d037-518">Параметр *certificate_buffer* указывает на место, выделенное для хранения входящих удаленных сертификатов и блоков управления, необходимых для этих сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-518">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="7d037-519">Буфер будет разделен по количеству сертификатов (*certs_number*) на равные части для каждого сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-519">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="7d037-520">Параметр *buffer_size* указывает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="7d037-520">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="7d037-521">Необходимый объем пространства можно вычислить по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="7d037-521">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="7d037-522">Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов.</span><span class="sxs-lookup"><span data-stu-id="7d037-522">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="7d037-523">Буфер должен быть достаточно большим, чтобы вместить этот размер для каждого сертификата, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше.</span><span class="sxs-lookup"><span data-stu-id="7d037-523">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="7d037-524">Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-524">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-525">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-525">Parameters</span></span>

- <span data-ttu-id="7d037-526">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-526">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="7d037-527">**certs_number** — количество сертификатов, выделенных из предоставленного буфера.</span><span class="sxs-lookup"><span data-stu-id="7d037-527">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="7d037-528">**certificate_buffer** — указатель на буфер для хранения сертификатов, полученных с удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-528">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="7d037-529">**buffer_size** — размер буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-529">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-530">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-530">Return Values</span></span>

- <span data-ttu-id="7d037-531">**NX_SUCCESS** (0x00) — сертификат успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="7d037-531">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="7d037-532">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель буфера.</span><span class="sxs-lookup"><span data-stu-id="7d037-532">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="7d037-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="7d037-533">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="7d037-534">**NX_INVALID_PARAMETERS** (0x4D) — буфер слишком мал, чтобы вместить необходимое количество сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-534">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-535">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-535">Allowed From</span></span>

<span data-ttu-id="7d037-536">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-536">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-537">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-537">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-538">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-538">See Also</span></span>

- <span data-ttu-id="7d037-539">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-539">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-540">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-540">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="7d037-541">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="7d037-541">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="7d037-542">Освобождение места, выделенного для входящих сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-542">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-543">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-543">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-544">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-544">Description</span></span>

<span data-ttu-id="7d037-545">Эта служба используется для высвобождения всех буферов сертификатов, выделенных для определенного сеанса TLS з помощью nx_secure_tls_remote_certificate_allocated, путем их возврата в свободное место на этом сеансе.</span><span class="sxs-lookup"><span data-stu-id="7d037-545">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="7d037-546">Это может быть необходимо, если приложение повторно использует объект сеанса TLS без удаления и повторного создания этого объекта с помощью nx_secure_tls_session_delete и nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="7d037-546">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="7d037-547">Обратите внимание, что удаленное пространство сертификатов автоматически восстанавливается при сбросе сеанса TLS, как это происходит в nx_secure_tls_session_end, поэтому большинству приложений не требуется вызывать эту службу.</span><span class="sxs-lookup"><span data-stu-id="7d037-547">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-548">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-548">Parameters</span></span>

- <span data-ttu-id="7d037-549">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-549">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-550">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-550">Return Values</span></span>

- <span data-ttu-id="7d037-551">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-551">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="7d037-552">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-552">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-553">**NX_INVALID_PARAMETERS** (0x4D) — внутренняя ошибка — вероятное повреждение хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-553">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-554">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-554">Allowed From</span></span>

<span data-ttu-id="7d037-555">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-555">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-556">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-556">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-557">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-557">See Also</span></span>

- <span data-ttu-id="7d037-558">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-558">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-559">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-559">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-560">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-560">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-561">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-561">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="7d037-562">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-562">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="7d037-563">Добавление сертификата специально для серверов TLS с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="7d037-563">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-564">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-564">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="7d037-565">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-565">Description</span></span>

<span data-ttu-id="7d037-566">Эта служба используется для добавления сертификата в локальное хранилище сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.</span><span class="sxs-lookup"><span data-stu-id="7d037-566">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="7d037-567">Числовой идентификатор не зависит от сертификата и позволяет добавлять на сервер TLS несколько сертификатов в качестве сертификатов удостоверений, а также позволяет добавлять несколько сертификатов с одинаковым общим именем в одно и то же локальное хранилище сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-567">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="7d037-568">Эту же службу можно использовать для сертификатов клиента, но в клиенте TLS крайне редко бывает несколько сертификатов удостоверений.</span><span class="sxs-lookup"><span data-stu-id="7d037-568">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="7d037-569">Параметр cert_id — это ненулевое положительное целое число, которое назначает приложение.</span><span class="sxs-lookup"><span data-stu-id="7d037-569">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="7d037-570">Фактическое значение не играет роли (кроме нуля), но оно должно быть уникальным в хранилище для указанного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-570">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="7d037-571">Значение cert_id можно использовать для поиска и удаления сертификатов из локального хранилища с помощью nx_secure_tls_server_certificate_find и nx_secure_tls_server_certificate_remove соответственно.</span><span class="sxs-lookup"><span data-stu-id="7d037-571">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-572">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_local_certificate_add. API nx_secure_tls_server_certificate_add использует уникальный числовой идентификатор для каждого сертификата и локальный индекс служб сертификатов на основе общего имени X.509. Службы сертификатов сервера позволяют хранить несколько сертификатов с общими данными (особенно общим именем) в одном локальном хранилище — это полезно для сервера с несколькими удостоверениями.*</span><span class="sxs-lookup"><span data-stu-id="7d037-572">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-573">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-573">Parameters</span></span>

- <span data-ttu-id="7d037-574">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-574">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-575">**certificate** — указатель на инициализированный ранее экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-575">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="7d037-576">**cert_id** — положительный, ненулевой, сравнительно уникальный код сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-576">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-577">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-577">Return Values</span></span>

- <span data-ttu-id="7d037-578">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-578">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="7d037-579">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-579">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="7d037-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) — указанный идентификатор сертификата имел недопустимое значение (скорее всего 0).</span><span class="sxs-lookup"><span data-stu-id="7d037-580">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="7d037-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) — указанный идентификатор сертификата уже есть в локальном хранилище.</span><span class="sxs-lookup"><span data-stu-id="7d037-581">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="7d037-582">**NX_INVALID_PARAMETERS** (0x4D) — внутренняя ошибка — вероятное повреждение хранилища сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-582">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-583">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-583">Allowed From</span></span>

<span data-ttu-id="7d037-584">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-585">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-585">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-586">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-586">See Also</span></span>

- <span data-ttu-id="7d037-587">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-587">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-588">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-588">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7d037-589">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-589">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7d037-590">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-590">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="7d037-591">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-591">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="7d037-592">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-592">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="7d037-593">Поиск сертификата по числовому идентификатору</span><span class="sxs-lookup"><span data-stu-id="7d037-593">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-594">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-594">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="7d037-595">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-595">Description</span></span>

<span data-ttu-id="7d037-596">Эта служба используется для поиска сертификата в локальном хранилище сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.</span><span class="sxs-lookup"><span data-stu-id="7d037-596">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="7d037-597">Параметр cert_id — ненулевое положительное целое число, которое назначает приложение при добавлении сертификата в локальное хранилище сеанса TLS с помощью nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="7d037-597">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-598">*Этот API не следует использовать с тем же сеансом TLS при использовании nx_secure_tls_local_certificate_add. API nx_secure_tls_server_certificate_add использует уникальный числовой идентификатор для каждого сертификата и локальный индекс служб сертификатов на основе общего имени X.509. Службы сертификатов сервера позволяют хранить несколько сертификатов с общими данными (особенно общим именем) в одном локальном хранилище — это полезно для сервера с несколькими удостоверениями.*</span><span class="sxs-lookup"><span data-stu-id="7d037-598">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-599">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-599">Parameters</span></span>

- <span data-ttu-id="7d037-600">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-600">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-601">**certificate** — указатель на указатель сертификата X.509 для возврата ссылки на найденный сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-601">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="7d037-602">**cert_id** — ненулевое положительное значение идентификатора сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-602">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-603">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-603">Return Values</span></span>

- <span data-ttu-id="7d037-604">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-604">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="7d037-605">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель на сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-605">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="7d037-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — указанный идентификатор сертификата не соответствует ни одному из локальных хранилищ указанного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-606">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-607">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-607">Allowed From</span></span>

<span data-ttu-id="7d037-608">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-608">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-609">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-609">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-610">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-610">See Also</span></span>

- <span data-ttu-id="7d037-611">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-611">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-612">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-612">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7d037-613">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-613">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7d037-614">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-614">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7d037-615">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-615">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="7d037-616">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-616">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="7d037-617">Удаление сертификата локального сервера с помощью числового идентификатора</span><span class="sxs-lookup"><span data-stu-id="7d037-617">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-618">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-618">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="7d037-619">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-619">Description</span></span>

<span data-ttu-id="7d037-620">Эта служба используется для удаления сертификата из локального хранилища сеанса TLS (см. nx_secure_tls_local_certificate_add) с использованием числового идентификатора вместо индексирования хранилища с помощью субъекта X.509 (общее имя) в сертификате.</span><span class="sxs-lookup"><span data-stu-id="7d037-620">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="7d037-621">Параметр cert_id — ненулевое положительное целое число, которое назначает приложение при добавлении сертификата в локальное хранилище сеанса TLS с помощью nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="7d037-621">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-622">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-622">Parameters</span></span>

- <span data-ttu-id="7d037-623">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-623">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-624">**cert_id** — ненулевое положительное значение идентификатора сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-624">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-625">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-625">Return Values</span></span>

- <span data-ttu-id="7d037-626">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-626">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="7d037-627">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-627">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="7d037-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — указанный идентификатор сертификата не соответствует ни одному из локальных хранилищ указанного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-628">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-629">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-629">Allowed From</span></span>

<span data-ttu-id="7d037-630">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-630">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-631">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-631">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-632">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-632">See Also</span></span>

- <span data-ttu-id="7d037-633">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-633">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-634">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-634">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="7d037-635">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-635">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7d037-636">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-636">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7d037-637">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-637">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="7d037-638">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="7d037-638">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="7d037-639">Получение значения и уровня оповещения TLS, отправленного удаленным узлом</span><span class="sxs-lookup"><span data-stu-id="7d037-639">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-640">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-640">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="7d037-641">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-641">Description</span></span>

<span data-ttu-id="7d037-642">Эта служба используется для получения уровня и значения оповещения TLS, когда удаленный узел отправляет оповещение в ответ на какую-либо проблему или ошибку.</span><span class="sxs-lookup"><span data-stu-id="7d037-642">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="7d037-643">Значения параметров alert_level и alert_value допустимы только в том случае, если эта функция вызывается сразу после вызова API TLS, который вернул состояние NX_SECURE_TLS_ALERT_RECEIVED (0x114), указывающее на то, что оповещение получено из удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-643">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="7d037-644">Обратите внимание, что если TLS на локальном узле отправляет оповещение, полученные коды ошибок содержат намного больше полезной информации по фактической ошибке, чем само оповещение TLS, так как значения оповещений TLS преднамеренно оставлены неоднозначными для предотвращения определенных типов атак (например, атака типа padding oracle или подобные).</span><span class="sxs-lookup"><span data-stu-id="7d037-644">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="7d037-645">Уровень оповещения принимает одно из двух значений: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) или NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="7d037-645">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="7d037-646">Как правило, только оповещение CloseNotify (используемое для указания успешного завершения сеанса TLS) будет иметь уровень "Предупреждение", хотя некоторые ситуации конфигурации расширения также могут считаться предупреждениями.</span><span class="sxs-lookup"><span data-stu-id="7d037-646">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="7d037-647">Подавляющее большинство оповещений будут иметь значение «Неустранимый», что свидетельствует о возможной ошибке безопасности и приведет к немедленному закрытию TLS-подключения (подтверждения или сеанса).</span><span class="sxs-lookup"><span data-stu-id="7d037-647">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="7d037-648">Значения оповещений TLS определены в документах RFC по протоколу TLS. Ниже приведен список из документа RFC 5246 (TLSv1.2) для справки.</span><span class="sxs-lookup"><span data-stu-id="7d037-648">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="7d037-649">Имя предупреждения</span><span class="sxs-lookup"><span data-stu-id="7d037-649">Alert Name</span></span>                     | <span data-ttu-id="7d037-650">Значение</span><span class="sxs-lookup"><span data-stu-id="7d037-650">Value</span></span> | <span data-ttu-id="7d037-651">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-651">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7d037-652">close_notify</span><span class="sxs-lookup"><span data-stu-id="7d037-652">close_notify</span></span>                  | <span data-ttu-id="7d037-653">0</span><span class="sxs-lookup"><span data-stu-id="7d037-653">0</span></span>     | <span data-ttu-id="7d037-654">Без ошибок, указывает на успешное завершение сеанса</span><span class="sxs-lookup"><span data-stu-id="7d037-654">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="7d037-655">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="7d037-655">unexpected_message</span></span>            | <span data-ttu-id="7d037-656">10</span><span class="sxs-lookup"><span data-stu-id="7d037-656">10</span></span>    | <span data-ttu-id="7d037-657">Протокол TLS получил неожиданное или неупорядоченное сообщение</span><span class="sxs-lookup"><span data-stu-id="7d037-657">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="7d037-658">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="7d037-658">bad_record_mac</span></span>               | <span data-ttu-id="7d037-659">20</span><span class="sxs-lookup"><span data-stu-id="7d037-659">20</span></span>    | <span data-ttu-id="7d037-660">Сбой расшифровки или проверки MAC</span><span class="sxs-lookup"><span data-stu-id="7d037-660">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="7d037-661">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="7d037-661">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="7d037-662">21</span><span class="sxs-lookup"><span data-stu-id="7d037-662">21</span></span>    | <span data-ttu-id="7d037-663">**Не рекомендуется**. Сбой расшифровки (не рекомендуется из-за атак padding oracle)</span><span class="sxs-lookup"><span data-stu-id="7d037-663">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="7d037-664">record_overflow</span><span class="sxs-lookup"><span data-stu-id="7d037-664">record_overflow</span></span>               | <span data-ttu-id="7d037-665">22</span><span class="sxs-lookup"><span data-stu-id="7d037-665">22</span></span>    | <span data-ttu-id="7d037-666">Размер полученной записи превышает максимальный размер записи TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-666">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="7d037-667">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="7d037-667">decompression_failure</span></span>         | <span data-ttu-id="7d037-668">30</span><span class="sxs-lookup"><span data-stu-id="7d037-668">30</span></span>    | <span data-ttu-id="7d037-669">Возникла проблема при сжатии или распаковке записи TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-669">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="7d037-670">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="7d037-670">handshake_failure</span></span>             | <span data-ttu-id="7d037-671">40</span><span class="sxs-lookup"><span data-stu-id="7d037-671">40</span></span>    | <span data-ttu-id="7d037-672">Произошла неопределенная ошибка подтверждения, не связанная с другим оповещением</span><span class="sxs-lookup"><span data-stu-id="7d037-672">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="7d037-673">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="7d037-673">no_certificate_RESERVED</span></span>      | <span data-ttu-id="7d037-674">41</span><span class="sxs-lookup"><span data-stu-id="7d037-674">41</span></span>    | <span data-ttu-id="7d037-675">**Не рекомендуется** в протоколе TLS (только SSL)</span><span class="sxs-lookup"><span data-stu-id="7d037-675">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="7d037-676">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="7d037-676">bad_certificate</span></span>               | <span data-ttu-id="7d037-677">42</span><span class="sxs-lookup"><span data-stu-id="7d037-677">42</span></span>    | <span data-ttu-id="7d037-678">Полученный сертификат содержал недопустимое форматирование или подписи</span><span class="sxs-lookup"><span data-stu-id="7d037-678">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="7d037-679">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="7d037-679">unsupported_certificate</span></span>       | <span data-ttu-id="7d037-680">43</span><span class="sxs-lookup"><span data-stu-id="7d037-680">43</span></span>    | <span data-ttu-id="7d037-681">Получен сертификат недопустимого типа (например, сертификат только для подписи, используемый для проверки подлинности сервера TLS)</span><span class="sxs-lookup"><span data-stu-id="7d037-681">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="7d037-682">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="7d037-682">certificate_revoked</span></span>           | <span data-ttu-id="7d037-683">44</span><span class="sxs-lookup"><span data-stu-id="7d037-683">44</span></span>    | <span data-ttu-id="7d037-684">Состояние сертификата (предоставленное списком отзыва сертификатов или OCSP) указано как "Отозвано"</span><span class="sxs-lookup"><span data-stu-id="7d037-684">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="7d037-685">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="7d037-685">certificate_expired</span></span>           | <span data-ttu-id="7d037-686">45</span><span class="sxs-lookup"><span data-stu-id="7d037-686">45</span></span>    | <span data-ttu-id="7d037-687">Полученный сертификат находится за пределами допустимого диапазона дат (он еще не действителен или устарел)</span><span class="sxs-lookup"><span data-stu-id="7d037-687">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="7d037-688">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="7d037-688">certificate_unknown</span></span>           | <span data-ttu-id="7d037-689">46</span><span class="sxs-lookup"><span data-stu-id="7d037-689">46</span></span>    | <span data-ttu-id="7d037-690">Обнаружена неизвестная ошибка сертификата, которая не относится к другим оповещениям</span><span class="sxs-lookup"><span data-stu-id="7d037-690">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="7d037-691">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="7d037-691">illegal_parameter</span></span>             | <span data-ttu-id="7d037-692">47</span><span class="sxs-lookup"><span data-stu-id="7d037-692">47</span></span>    | <span data-ttu-id="7d037-693">Конфигурация или согласованное значение в подтверждении TLS являются недопустимыми или находятся за пределами диапазона</span><span class="sxs-lookup"><span data-stu-id="7d037-693">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="7d037-694">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="7d037-694">unknown_ca</span></span>                    | <span data-ttu-id="7d037-695">48</span><span class="sxs-lookup"><span data-stu-id="7d037-695">48</span></span>    | <span data-ttu-id="7d037-696">Не удалось отследить полученный сертификат удостоверения через цепочку сертификатов до доверенного корневого сертификата ЦС.</span><span class="sxs-lookup"><span data-stu-id="7d037-696">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="7d037-697">access_denied</span><span class="sxs-lookup"><span data-stu-id="7d037-697">access_denied</span></span>                 | <span data-ttu-id="7d037-698">49</span><span class="sxs-lookup"><span data-stu-id="7d037-698">49</span></span>    | <span data-ttu-id="7d037-699">Указывает, что был получен допустимый сертификат, но контроль доступа к приложениям указал, что для запрашиваемых ресурсов сертификат был недопустимым.</span><span class="sxs-lookup"><span data-stu-id="7d037-699">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="7d037-700">decode_error</span><span class="sxs-lookup"><span data-stu-id="7d037-700">decode_error</span></span>                  | <span data-ttu-id="7d037-701">50</span><span class="sxs-lookup"><span data-stu-id="7d037-701">50</span></span>    | <span data-ttu-id="7d037-702">Поле или значения в сообщении с заголовком или подтверждением TLS находились вне допустимого диапазона или являются недопустимыми, что привело к сбою при декодировании записи TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-702">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="7d037-703">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="7d037-703">decrypt_error</span></span>                 | <span data-ttu-id="7d037-704">51</span><span class="sxs-lookup"><span data-stu-id="7d037-704">51</span></span>    | <span data-ttu-id="7d037-705">Не удалось проверить хэш подписи или сообщения о завершении подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-705">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="7d037-706">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="7d037-706">export_restriction_RESERVED</span></span>  | <span data-ttu-id="7d037-707">60</span><span class="sxs-lookup"><span data-stu-id="7d037-707">60</span></span>    | <span data-ttu-id="7d037-708">Не рекомендуется для версии TLSv1.2</span><span class="sxs-lookup"><span data-stu-id="7d037-708">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="7d037-709">protocol_version</span><span class="sxs-lookup"><span data-stu-id="7d037-709">protocol_version</span></span>              | <span data-ttu-id="7d037-710">70</span><span class="sxs-lookup"><span data-stu-id="7d037-710">70</span></span>    | <span data-ttu-id="7d037-711">Версия протокола TLS, согласованная во время подтверждения, распознана, но не поддерживается (например, если версия TLSv1.0 предоставлена, но не включена).</span><span class="sxs-lookup"><span data-stu-id="7d037-711">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="7d037-712">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="7d037-712">insufficient_security</span></span>         | <span data-ttu-id="7d037-713">71</span><span class="sxs-lookup"><span data-stu-id="7d037-713">71</span></span>    | <span data-ttu-id="7d037-714">Отправляется при сбое подтверждения из-за отсутствия безопасных шифров (например, если размер ключа слишком мал согласно требованиям приложения).</span><span class="sxs-lookup"><span data-stu-id="7d037-714">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="7d037-715">internal_error</span><span class="sxs-lookup"><span data-stu-id="7d037-715">internal_error</span></span>                | <span data-ttu-id="7d037-716">80</span><span class="sxs-lookup"><span data-stu-id="7d037-716">80</span></span>    | <span data-ttu-id="7d037-717">Произошла ошибка, не относящаяся к протоколу TLS (например, проблемы с выделением памяти или проблемы с приложением), что привело к прекращению сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-717">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="7d037-718">user_canceled</span><span class="sxs-lookup"><span data-stu-id="7d037-718">user_canceled</span></span>                 | <span data-ttu-id="7d037-719">90</span><span class="sxs-lookup"><span data-stu-id="7d037-719">90</span></span>    | <span data-ttu-id="7d037-720">Возвращается, если пользователь или приложение отменили сеанс TLS до завершения подтверждения (подобно оповещению CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="7d037-720">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="7d037-721">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="7d037-721">no_renegotiation</span></span>              | <span data-ttu-id="7d037-722">100</span><span class="sxs-lookup"><span data-stu-id="7d037-722">100</span></span>   | <span data-ttu-id="7d037-723">Указывает, что удаленный узел не может выполнить подтверждения повторного согласования TLS в ответ на запрос на повторное согласование.</span><span class="sxs-lookup"><span data-stu-id="7d037-723">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="7d037-724">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="7d037-724">unsupported_extension</span></span>         | <span data-ttu-id="7d037-725">110</span><span class="sxs-lookup"><span data-stu-id="7d037-725">110</span></span>   | <span data-ttu-id="7d037-726">Отправляется, если клиент TLS получает ServerHello с расширениями, которые явным образом не запрашивались в первоначальном ClientHello (что указывает на проблему с сервером).</span><span class="sxs-lookup"><span data-stu-id="7d037-726">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="7d037-727">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-727">Parameters</span></span>

- <span data-ttu-id="7d037-728">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-728">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-729">**alert_level** — возвращает уровень полученного оповещения (предупреждение или неустранимая ошибка).</span><span class="sxs-lookup"><span data-stu-id="7d037-729">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="7d037-730">**alert_value** — возвращает значение полученного оповещения (см. таблицу).</span><span class="sxs-lookup"><span data-stu-id="7d037-730">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-731">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-731">Return Values</span></span>

- <span data-ttu-id="7d037-732">**NX_SUCCESS** (0x00) — операция выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-732">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="7d037-733">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-733">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-734">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-734">Allowed From</span></span>

<span data-ttu-id="7d037-735">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-736">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-736">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-737">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-737">See Also</span></span>

- <span data-ttu-id="7d037-738">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-738">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-739">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-739">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-740">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-740">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="7d037-741">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-741">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="7d037-742">Настройка обратного вызова для протокола TLS, который будет использоваться для дополнительной проверки сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-742">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-743">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-743">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="7d037-744">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-744">Description</span></span>

<span data-ttu-id="7d037-745">Эта служба назначает указатель функции на сеанс TLS, который будет вызываться протоколом TLS при получении сертификата с удаленного узла. Таким образом приложение сможет выполнять такие проверки, как проверка DNS, отзыв сертификата и принудительное применение политики сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-745">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="7d037-746">NetX Secure TLS выполняет базовую проверку пути X.509 для сертификата перед выполнением обратного вызова, чтобы убедиться, что сертификат можно отследить до сертификата в хранилище доверенных сертификатов TLS, но все остальные проверки будут обрабатываться этим обратным вызовом.</span><span class="sxs-lookup"><span data-stu-id="7d037-746">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="7d037-747">Обратный вызов предоставляет указатель сеанса TLS и указатель на сертификат удостоверения удаленного узла (конечный объект в цепочке сертификатов).</span><span class="sxs-lookup"><span data-stu-id="7d037-747">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="7d037-748">Обратный вызов должен возвращать значение NX_SUCCESS, если вся проверка прошла успешно. В противном случае он должен вернуть код ошибки, указывающий на сбой проверки.</span><span class="sxs-lookup"><span data-stu-id="7d037-748">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="7d037-749">Любое значение, кроме NX_SUCCESS, приведет к немедленному прерыванию подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-749">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-750">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-750">Parameters</span></span>

- <span data-ttu-id="7d037-751">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-751">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-752">**func_ptr** — указатель на функцию обратного вызова проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-752">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-753">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-753">Return Values</span></span>

- <span data-ttu-id="7d037-754">**NX_SUCCESS** (0x00) — успешное выделение указателя функции.</span><span class="sxs-lookup"><span data-stu-id="7d037-754">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="7d037-755">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-755">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-756">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-756">Allowed From</span></span>

<span data-ttu-id="7d037-757">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-757">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-758">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-758">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-759">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-759">See Also</span></span>

- <span data-ttu-id="7d037-760">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-760">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-761">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-761">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7d037-762">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-762">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="7d037-763">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-763">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="7d037-764">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения клиента TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-764">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-765">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-765">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="7d037-766">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-766">Description</span></span>

<span data-ttu-id="7d037-767">Эта служба назначает указатель функции сеансу TLS, который будет вызывать протокол TLS, если подтверждение клиента TLS получило сообщение ServerHelloDone.</span><span class="sxs-lookup"><span data-stu-id="7d037-767">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="7d037-768">Функция обратного вызова позволяет приложению обрабатывать любые расширения TLS из полученного сообщения ServerHello, для которого необходимо ввести данные или принять решение.</span><span class="sxs-lookup"><span data-stu-id="7d037-768">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="7d037-769">Обратный вызов выполняется с помощью блока управления сеансом TLS и массива объектов NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="7d037-769">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="7d037-770">Массив объектов расширения необходимо передать во вспомогательную функцию, которая найдет и проанализирует определенное расширение.</span><span class="sxs-lookup"><span data-stu-id="7d037-770">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="7d037-771">Сейчас в NetX Secure не поддерживаются специальные расширения, для которых требуются входные данные клиента TLS. Однако разработчикам приложений доступен обратный вызов для обработки пользовательских или новых расширений, которые могут стать доступными.</span><span class="sxs-lookup"><span data-stu-id="7d037-771">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="7d037-772">Пример вспомогательной функции, которая анализирует расширения TLS, предоставленные в сообщениях приветствия, см. на странице *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="7d037-772">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="7d037-773">Обратный вызов клиента также может использоваться для выбора активного сертификата удостоверения с помощью *nx_secure_tls_active_certificate_set* для клиента TLS в случае, если удаленный сервер запросил сертификат и предоставил сведения, позволяющие клиенту TLS выбирать конкретный сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-773">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="7d037-774">Дополнительные сведения см. в справочнике по nx_secure_tls_active_certificate_set.</span><span class="sxs-lookup"><span data-stu-id="7d037-774">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-775">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-775">Parameters</span></span>

- <span data-ttu-id="7d037-776">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-776">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-777">**func_ptr** — указатель на функцию обратного вызова клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-777">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-778">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-778">Return Values</span></span>

- <span data-ttu-id="7d037-779">**NX_SUCCESS** (0x00) — успешное выделение указателя функции.</span><span class="sxs-lookup"><span data-stu-id="7d037-779">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="7d037-780">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-780">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-781">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-781">Allowed From</span></span>

<span data-ttu-id="7d037-782">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-782">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-783">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-783">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-784">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-784">See Also</span></span>

- <span data-ttu-id="7d037-785">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-785">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-786">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-786">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="7d037-787">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-787">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="7d037-788">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="7d037-788">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="7d037-789">Включение проверки X.509 клиента и выделение места для сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="7d037-789">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-790">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-790">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7d037-791">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-791">Description</span></span>

<span data-ttu-id="7d037-792">Эта служба включает необязательную проверку подлинности клиента X.509 для экземпляра сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-792">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="7d037-793">Она также выделяет пространство, необходимое для обработки входящих цепочек сертификатов с удаленного узла клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-793">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="7d037-794">Сертификаты, которые предоставляет удаленный клиент, будут проверены на соответствие доверенным сертификатам экземпляра сервера TLS, который назначила служба *nx_secure_tls_trusted_certificate_add*.</span><span class="sxs-lookup"><span data-stu-id="7d037-794">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="7d037-795">Для режима клиента TLS требуется удаленное выделение сертификатов и следует использовать службу *nx_secure_tls_remote_certificate_buffer_allocate*.</span><span class="sxs-lookup"><span data-stu-id="7d037-795">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="7d037-796">Включение проверки подлинности клиента X.509 в экземпляре клиента TLS не будет действовать.</span><span class="sxs-lookup"><span data-stu-id="7d037-796">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="7d037-797">Параметр *certificate_buffer* указывает на место, выделенное для хранения входящих удаленных сертификатов и блоков управления, необходимых для этих сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-797">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="7d037-798">Буфер будет разделен по количеству сертификатов (*certs_number*) на равные части для каждого сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-798">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="7d037-799">Параметр *buffer_size* указывает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="7d037-799">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="7d037-800">Необходимый объем пространства можно вычислить по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="7d037-800">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="7d037-801">Размеры типичных сертификатов с 2048-битными ключами RSA, использующих SHA-256 для подписей, находятся в диапазоне от 1000 до 2000 байтов.</span><span class="sxs-lookup"><span data-stu-id="7d037-801">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="7d037-802">Буфер должен быть достаточно большим, чтобы вместить этот размер для каждого сертификата, но в зависимости от сертификатов удаленного узла может быть значительно меньше или больше.</span><span class="sxs-lookup"><span data-stu-id="7d037-802">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="7d037-803">Обратите внимание, если размера буфера недостаточно для хранения входящего сертификата, то подтверждение TLS завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-803">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-804">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-804">Parameters</span></span>

- <span data-ttu-id="7d037-805">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-805">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-806">**certs_number** — число сертификатов, выделенных из предоставленного буфера.</span><span class="sxs-lookup"><span data-stu-id="7d037-806">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="7d037-807">**certificate_buffer** — указатель на буфер для хранения сертификатов, полученных с удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-807">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="7d037-808">**buffer_size** — размер буфера сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-808">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-809">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-809">Return Values</span></span>

- <span data-ttu-id="7d037-810">**NX_SUCCESS** (0x00) — сертификат успешно выделен.</span><span class="sxs-lookup"><span data-stu-id="7d037-810">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="7d037-811">**NX_PTR_ERROR** (0x07) — недопустимый сеанс TLS или указатель буфера.</span><span class="sxs-lookup"><span data-stu-id="7d037-811">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="7d037-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) — указанный буфер слишком мал.</span><span class="sxs-lookup"><span data-stu-id="7d037-812">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="7d037-813">**NX_INVALID_PARAMETERS** (0x4D) — буфер слишком мал, чтобы вместить необходимое количество сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-813">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-814">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-814">Allowed From</span></span>

<span data-ttu-id="7d037-815">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-815">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-816">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-816">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-817">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-817">See Also</span></span>

- <span data-ttu-id="7d037-818">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-818">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-819">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-819">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-820">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-820">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="7d037-821">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="7d037-821">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="7d037-822">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-822">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-823">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-823">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-824">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-824">Description</span></span>

<span data-ttu-id="7d037-825">Эта служба отключает проверку подлинности сертификата клиента для определенного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-825">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="7d037-826">Дополнительные сведения см. в справочнике по nx_secure_tls_session_client_verify_enable.</span><span class="sxs-lookup"><span data-stu-id="7d037-826">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-827">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-827">Parameters</span></span>

- <span data-ttu-id="7d037-828">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-828">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-829">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-829">Return Values</span></span>

- <span data-ttu-id="7d037-830">**NX_SUCCESS** (0x00) — успешное изменение состояния.</span><span class="sxs-lookup"><span data-stu-id="7d037-830">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="7d037-831">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-831">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-832">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-832">Allowed From</span></span>

<span data-ttu-id="7d037-833">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-834">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-834">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-835">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-835">See Also</span></span>

- <span data-ttu-id="7d037-836">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7d037-836">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="7d037-837">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-837">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-838">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-838">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="7d037-839">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7d037-839">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="7d037-840">Отключение проверки подлинности сертификата клиента для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-840">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-841">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-841">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-842">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-842">Description</span></span>

<span data-ttu-id="7d037-843">Эта служба включает проверку подлинности сертификата клиента для определенного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-843">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="7d037-844">Включение проверки подлинности сертификата клиента для экземпляра сервера TLS приведет к тому, что сервер TLS запросит сертификат из любого удаленного клиента TLS во время первоначального подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-844">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="7d037-845">Сертификат, полученный от удаленного клиента TLS, сопровождается сообщением CertificateVerify, которое сервер TLS использует для проверки на наличие прав владения сертификатом у клиента (наличие доступа к закрытому ключу, связанному с этим сертификатом).</span><span class="sxs-lookup"><span data-stu-id="7d037-845">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="7d037-846">Если предоставленный сертификат можно проверить и отследить до сертификата в хранилище доверенных сертификатов сервера TLS с помощью цепочки сертификатов X.509, удаленный клиент TLS проходит проверку подлинности, а подтверждение остается в силе.</span><span class="sxs-lookup"><span data-stu-id="7d037-846">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="7d037-847">В случае возникновения ошибок при обработке сертификата или сообщения CertificateVerify подтверждение TLS завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-847">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="7d037-848">*У сервера TLS должен быть по крайней мере один сертификат, добавленный с помощью nx_secure_tls_trusted_certificate_add, иначе проверка подлинности всегда будет завершаться ошибкой.*</span><span class="sxs-lookup"><span data-stu-id="7d037-848">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-849">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-849">Parameters</span></span>

- <span data-ttu-id="7d037-850">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-850">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-851">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-851">Return Values</span></span>

- <span data-ttu-id="7d037-852">**NX_SUCCESS** (0x00) — успешное изменение состояния.</span><span class="sxs-lookup"><span data-stu-id="7d037-852">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="7d037-853">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-853">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-854">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-854">Allowed From</span></span>

<span data-ttu-id="7d037-855">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-855">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-856">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-856">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-857">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-857">See Also</span></span>

- <span data-ttu-id="7d037-858">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="7d037-858">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="7d037-859">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-859">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-860">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-860">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-861">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-861">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="7d037-862">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-862">nx_secure_tls_session_create</span></span>

<span data-ttu-id="7d037-863">Создание сеанса NetX Secure TLS для обеспечения безопасности подключений</span><span class="sxs-lookup"><span data-stu-id="7d037-863">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-864">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-864">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="7d037-865">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-865">Description</span></span>

<span data-ttu-id="7d037-866">Эта служба инициализирует экземпляр структуры NX_SECURE_TLS_SESSION для использования во время безопасного взаимодействия по протоколу TLS через сетевое подключение.</span><span class="sxs-lookup"><span data-stu-id="7d037-866">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="7d037-867">Метод принимает объект NX_SECURE_TLS_CRYPTO, который заполняется доступными криптографическими методами для использования с протоколом TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-867">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="7d037-868">*encryption_metadata_area* указывает на буфер, выделенный для использования протоколом TLS для "метаданных", которые используются криптографическими методами в таблице NX_SECURE_TLS_CRYPTO для вычислений.</span><span class="sxs-lookup"><span data-stu-id="7d037-868">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="7d037-869">Размер таблицы можно определить с помощью службы nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="7d037-869">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="7d037-870">Дополнительные сведения см. в разделе "Шифрование в NetX Secure TLS" главы 3.</span><span class="sxs-lookup"><span data-stu-id="7d037-870">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-871">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-871">Parameters</span></span>

- <span data-ttu-id="7d037-872">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-872">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-873">**cipher_table** — указатель на криптографические методы TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-873">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="7d037-874">**encryption_metadata_area** — указатель на пространство для метаданных шифрования.</span><span class="sxs-lookup"><span data-stu-id="7d037-874">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="7d037-875">**encryption_metadata_size** — размер буфера метаданных.</span><span class="sxs-lookup"><span data-stu-id="7d037-875">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-876">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-876">Return Values</span></span>

- <span data-ttu-id="7d037-877">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-877">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-878">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-878">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7d037-879">**NX_INVALID_PARAMETERS** (0x4D) — буфер метаданных слишком мал для указанных методов.</span><span class="sxs-lookup"><span data-stu-id="7d037-879">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="7d037-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) — необходимый метод шифра для включенной версии TLS не указан в таблице шифров.</span><span class="sxs-lookup"><span data-stu-id="7d037-880">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-881">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-881">Allowed From</span></span>

<span data-ttu-id="7d037-882">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-882">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-883">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-883">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-884">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-884">See Also</span></span>

- <span data-ttu-id="7d037-885">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-885">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-886">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="7d037-886">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="7d037-887">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-887">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-888">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-888">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-889">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-889">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7d037-890">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-890">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-891">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-891">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-892">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-892">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-893">Шифрование для NetX Secure TLS в главе 3</span><span class="sxs-lookup"><span data-stu-id="7d037-893">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="7d037-894">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-894">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="7d037-895">Удаление сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-895">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-896">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-896">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-897">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-897">Description</span></span>

<span data-ttu-id="7d037-898">Эта служба удаляет сеанс TLS, представленный экземпляром структуры NX_SECURE_TLS_SESSION, и освобождает все системные ресурсы этого экземпляра сеанса.</span><span class="sxs-lookup"><span data-stu-id="7d037-898">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-899">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-899">Parameters</span></span>

- <span data-ttu-id="7d037-900">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-900">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-901">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-901">Return Values</span></span>

- <span data-ttu-id="7d037-902">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-902">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-903">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-903">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-904">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-904">Allowed From</span></span>

<span data-ttu-id="7d037-905">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-906">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-906">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-907">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-907">See Also</span></span>

- <span data-ttu-id="7d037-908">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-908">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-909">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-909">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-910">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-910">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-911">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-911">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7d037-912">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-912">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-913">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-913">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-914">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-914">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="7d037-915">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-915">nx_secure_tls_session_end</span></span>

<span data-ttu-id="7d037-916">Завершение активного сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-916">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-917">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-917">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d037-918">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-918">Description</span></span>

<span data-ttu-id="7d037-919">Эта служба завершает сеанс TLS, представленный экземпляром структуры NX_SECURE_TLS_SESSION, путем отправления сообщения CloseNotify протокола TLS на удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="7d037-919">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="7d037-920">Затем служба ожидает ответа от удаленного узла с собственным сообщением CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="7d037-920">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="7d037-921">Если удаленный узел не отправляет сообщение CloseNotify, протокол TLS считает это ошибкой и возможным нарушением безопасности, поэтому проверка возвращаемого значения важна для безопасного подключения.</span><span class="sxs-lookup"><span data-stu-id="7d037-921">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="7d037-922">Параметр **wait_option** можно использовать для управления длительностью ожидания ответа для службы перед возвращением управления вызывающему потоку.</span><span class="sxs-lookup"><span data-stu-id="7d037-922">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-923">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-923">Parameters</span></span>

- <span data-ttu-id="7d037-924">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-924">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-925">**wait_option** — указывает на длительность ожидания ответа для службы от удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-925">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-926">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-926">Return Values</span></span>

- <span data-ttu-id="7d037-927">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-927">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) — не получен ответ от удаленного узла до истечения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="7d037-928">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="7d037-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить пакет для отправки сообщения CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="7d037-929">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="7d037-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить сообщение CloseNotify по TCP-сокету.</span><span class="sxs-lookup"><span data-stu-id="7d037-930">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="7d037-931">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-931">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-932">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-932">Allowed From</span></span>

<span data-ttu-id="7d037-933">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-933">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-934">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-934">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-935">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-935">See Also</span></span>

- <span data-ttu-id="7d037-936">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-936">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-937">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-937">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-938">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-938">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-939">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-939">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-940">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-940">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-941">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-941">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-942">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-942">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="7d037-943">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="7d037-943">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="7d037-944">Установка буфера повторной сборки пакетов для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-944">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-945">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-945">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="7d037-946">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-946">Description</span></span>

<span data-ttu-id="7d037-947">Эта служба связывает буфер повторной сборки пакетов с сеансом TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-947">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="7d037-948">Для расшифровки и анализа входящих записей TLS необходимо собрать данные в каждой записи из базовых TCP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="7d037-948">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="7d037-949">Размер записей TLS может составлять до 16 КБ (хотя обычно намного меньше), поэтому они могут не поместиться в один TCP-пакет.</span><span class="sxs-lookup"><span data-stu-id="7d037-949">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="7d037-950">Если известно, что размер входящего сообщения будет меньше предельного числа записей TLS, равного 16 КБ, размер буфера можно уменьшить. Однако для обработки неизвестных входящих данных буфер следует сделать максимально большим.</span><span class="sxs-lookup"><span data-stu-id="7d037-950">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="7d037-951">Если входящая запись больше, чем заданный буфер, то сеанс TLS завершится с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-951">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-952">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-952">Parameters</span></span>

- <span data-ttu-id="7d037-953">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-953">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-954">**buffer_ptr** — указатель на буфер для протокола TLS, используемый для повторной сборки пакетов.</span><span class="sxs-lookup"><span data-stu-id="7d037-954">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="7d037-955">**buffer_size** — размер заданного буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="7d037-955">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-956">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-956">Return Values</span></span>

- <span data-ttu-id="7d037-957">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-957">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-958">**NX_INVALID_PARAMETERS** (0x4D) — недопустимый буфер или указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-958">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="7d037-959">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-959">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-960">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-960">Allowed From</span></span>

<span data-ttu-id="7d037-961">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-961">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-962">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-962">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-963">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-963">See Also</span></span>

- <span data-ttu-id="7d037-964">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-964">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-965">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-965">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-966">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-966">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-967">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-967">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-968">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-968">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-969">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-969">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-970">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-970">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="7d037-971">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="7d037-971">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="7d037-972">Переопределение версии протокола TLS по умолчанию для сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-972">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-973">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-973">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="7d037-974">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-974">Description</span></span>

<span data-ttu-id="7d037-975">Эта служба переопределяет версию протокола TLS по умолчанию (самую новую), используемую в определенном сеансе.</span><span class="sxs-lookup"><span data-stu-id="7d037-975">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="7d037-976">Это позволяет NetX Secure TLS использовать более раннюю версию протокола TLS для определенного сеанса протокола, не отключая ее во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="7d037-976">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="7d037-977">Это может быть полезно в приложениях, которым может потребоваться обмен данными с узлом более ранней версии, который не поддерживает последнюю версию TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-977">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-978">*Начиная с версии 5.11 с пакетом обновления 3 (SP3), NetX Secure TLS поддерживает RFC 7507 (см. примечание ниже) и любое переопределение более старой версии с помощью этого API приведет к тому, что в ClientHello будет отправлено резервное SCSV. Если сервер поддерживает более новую версию TLS и резервное SCSV добавлено в ClientHello, этот сервер прервет подтверждение TLS с оповещением "Неприемлемый резерв". SCSV отправляется, только если версия переопределения является более старой, чем используемая версия TLS (например, при переопределении версии до TLS 1.2 SCSV не будет отправлен).*</span><span class="sxs-lookup"><span data-stu-id="7d037-978">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="7d037-979">Допустимыми значениями параметра protocol_version являются следующие макросы: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 и NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="7d037-979">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="7d037-980">Макросы NX_SECURE_TLS_DISABLE_TLS_1_1 и NX_SECURE_TLS_ENABLE_TLS_1_0 могут использоваться для управления версиями TLS, компилируемыми в приложение.</span><span class="sxs-lookup"><span data-stu-id="7d037-980">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="7d037-981">Протокол TLS версии 1.2 всегда включен.</span><span class="sxs-lookup"><span data-stu-id="7d037-981">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="7d037-982">Обратите внимание, что если удаленный узел не поддерживает предоставленную версию, произойдет сбой подключения. Только предоставленная версия переопределения будет согласовываться с помощью NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-982">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-983">RFC 7507: резервное SCSV протокола TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-983">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="7d037-984">Этот документ RFC предназначен для устранения проблемы безопасности, которая изначально была вызвана серверами, которые обрабатывали согласование с предыдущими протоколами ненадлежащим образом и отказались от других допустимых сообщений ClientHello.</span><span class="sxs-lookup"><span data-stu-id="7d037-984">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="7d037-985">При попытке сохранить совместимость с этими старыми серверами некоторые клиентские приложения TLS начали повторно выполнять завершившиеся сбоем подтверждения с помощью более старой версии TLS (например, при сбое TLS 1.2 использовали TLS 1.1).</span><span class="sxs-lookup"><span data-stu-id="7d037-985">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="7d037-986">Однако это обходное решение создало новую проблему. Злоумышленники могут заставить клиента перейти на более раннюю версию, искусственно вызывая ошибку сети или пакета, из-за которой происходит сбой подключения к серверу, даже если сервер поддерживает более новую версию TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-986">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="7d037-987">При переходе на более старую версию злоумышленник может использовать слабые места в этой версии (SSLv3<sup>21</sup> особенно подвержен атаке POODLE).</span><span class="sxs-lookup"><span data-stu-id="7d037-987">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="7d037-988">Чтобы предотвратить такую ситуацию, в документе RFC 7507 представлено "резервное SCSV" — псевдокомплект шифров <sup>22</sup>. Этот комплект отправляется в ClientHello, которое уведомляет сервер TLS, когда клиент протокола TLS использует не самую новую поддерживаемую версию протокола.</span><span class="sxs-lookup"><span data-stu-id="7d037-988">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="7d037-989">Таким образом, сервер, поддерживающий более новую версию, может отклонить ClientHello, содержащее резервное SCSV, и предотвратить атаку, предполагающую переход на более раннюю версию.</span><span class="sxs-lookup"><span data-stu-id="7d037-989">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="7d037-990">NetX Secure не применяет SSLv3 из-за наличия серьезных слабых мест, таких как POODLE.</span><span class="sxs-lookup"><span data-stu-id="7d037-990">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="7d037-991">Псевдокомплект шифров или SCSV (сигнальное значение комплекта шифров) — это зарезервированное число комплектов шифров, которое используется для оповещения включенных реализаций TLS о функциях, которые были недоступны в более старых версиях TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-991">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="7d037-992">Примерами являются резервное SCSV и TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746).</span><span class="sxs-lookup"><span data-stu-id="7d037-992">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-993">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-993">Parameters</span></span>

- <span data-ttu-id="7d037-994">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-994">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-995">**protocol_version** — макрос версии TLS для конкретной версии TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-995">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-996">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-996">Return Values</span></span>

- <span data-ttu-id="7d037-997">**NX_SUCCESS** (0x00) — успешное изменение состояния.</span><span class="sxs-lookup"><span data-stu-id="7d037-997">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="7d037-998">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-998">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) — известная, но неподдерживаемая версия TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-999">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="7d037-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — недопустимая версия протокола.</span><span class="sxs-lookup"><span data-stu-id="7d037-1000">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1001">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1001">Allowed From</span></span>

<span data-ttu-id="7d037-1002">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1002">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1003">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1003">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="7d037-1004">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1004">See Also</span></span>

- <span data-ttu-id="7d037-1005">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1005">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1006">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1006">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="7d037-1007">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1007">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="7d037-1008">Получение данных из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1008">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1009">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1009">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d037-1010">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1010">Description</span></span>

<span data-ttu-id="7d037-1011">Эта служба получает данные из указанного активного сеанса TLS, выполняя расшифровку этих данных перед их предоставлением вызывающему объекту в параметре NX_PACKET.</span><span class="sxs-lookup"><span data-stu-id="7d037-1011">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="7d037-1012">Если в указанном сеансе в очереди нет данных, вызов приостанавливается в зависимости от указанного параметра ожидания.</span><span class="sxs-lookup"><span data-stu-id="7d037-1012">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-1013">*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен.*</span><span class="sxs-lookup"><span data-stu-id="7d037-1013">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1014">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1014">Parameters</span></span>

- <span data-ttu-id="7d037-1015">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1015">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1016">**packet_ptr** — указатель на выделенный указатель пакета TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1016">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="7d037-1017">**wait_option** — указывает, как долго служба должна ожидать пакет от удаленного узла перед возвратом.</span><span class="sxs-lookup"><span data-stu-id="7d037-1017">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1018">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1018">Return Values</span></span>

- <span data-ttu-id="7d037-1019">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1019">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-1020">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="7d037-1020">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7d037-1021">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="7d037-1021">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7d037-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — полученное сообщение не прошло проверку подлинности хэша.</span><span class="sxs-lookup"><span data-stu-id="7d037-1022">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="7d037-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения указана неизвестная версия протокола.</span><span class="sxs-lookup"><span data-stu-id="7d037-1023">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="7d037-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — от удаленного узла получено оповещение TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1024">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="7d037-1025">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1025">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7d037-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1026">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1027">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1027">Allowed From</span></span>

<span data-ttu-id="7d037-1028">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1028">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1029">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1029">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="7d037-1030">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1030">See Also</span></span>

- <span data-ttu-id="7d037-1031">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1031">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7d037-1032">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1032">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1033">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1033">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1034">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1034">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1035">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-1035">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-1036">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-1036">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-1037">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-1037">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7d037-1038">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1038">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="7d037-1039">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1039">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="7d037-1040">Назначение обратного вызова, который будет выполняться в начале повторного согласования сеанса</span><span class="sxs-lookup"><span data-stu-id="7d037-1040">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1041">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1041">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="7d037-1042">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1042">Description</span></span>

<span data-ttu-id="7d037-1043">Эта служба назначает обратный вызов сеансу TLS, который будет вызываться при получении первого сообщения о подтверждении повторного согласования сеанса от удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-1043">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="7d037-1044">Функция обратного вызова предназначена для уведомления приложения о начале подтверждения повторного согласования. Приложение может завершить сеанс TLS, возвратив любое ненулевое значение из обратного вызова, которое приведет к завершению сеанса TLS с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-1044">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="7d037-1045">Если приложение продолжает повторное согласование, обратный вызов должен возвращать значение NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1045">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="7d037-1046">*Из-за семантики повторного согласования TLS обратный вызов будет выполняться для клиентов NetX Secure TLS при получении HelloRequest с удаленного сервера, но не в момент инициации клиентом повторного согласования. На серверах NetX Secure TLS обратный вызов будет выполняться при каждом получении повторного согласования ClientHello (любое сообщение ClientHello, полученное в контексте активного сеанса TLS). Это означает, что обратный вызов будет выполняться независимо от того, инициировал ли повторное согласование удаленный узел или локальное приложение, так как сервер TLS отправит HelloRequest, на который будет отвечать удаленный клиент.*</span><span class="sxs-lookup"><span data-stu-id="7d037-1046">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="7d037-1047">NetX Secure TLS вводит в действие расширение для указания безопасного повторного согласования из документа RFC 5746, чтобы гарантировать, что подтверждения повторного согласования не будут подвергаться атакам "злоумышленник в середине".</span><span class="sxs-lookup"><span data-stu-id="7d037-1047">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1048">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1048">Parameters</span></span>

- <span data-ttu-id="7d037-1049">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1049">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1050">**func_ptr** — указатель на функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="7d037-1050">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1051">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1051">Return Values</span></span>

- <span data-ttu-id="7d037-1052">**NX_SUCCESS** (0x00) — функция обратного вызова успешно назначена.</span><span class="sxs-lookup"><span data-stu-id="7d037-1052">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="7d037-1053">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя для функции обратного вызова или сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1053">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1054">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1054">Allowed From</span></span>

<span data-ttu-id="7d037-1055">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1055">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1056">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1056">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1057">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1057">See Also</span></span>

- <span data-ttu-id="7d037-1058">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1058">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1059">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1059">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1060">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1060">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-1061">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-1061">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-1062">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="7d037-1062">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="7d037-1063">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="7d037-1063">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="7d037-1064">Инициация подтверждения повторного согласования сеанса с удаленным узлом</span><span class="sxs-lookup"><span data-stu-id="7d037-1064">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1065">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1065">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="7d037-1066">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1066">Description</span></span>

<span data-ttu-id="7d037-1067">Эта служба инициирует подтверждение *повторного согласования* сеанса с подключенным удаленным узлом TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1067">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="7d037-1068">Повторное согласование состоит из второго подтверждения TLS в контексте ранее установленного сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1068">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="7d037-1069">Каждое новое сообщение подтверждения шифруется с помощью сеанса TLS до создания новых ключей сеанса и обмена сообщениями ChangeCipherSpec, при этом новые ключи используются для шифрования всех сообщений.</span><span class="sxs-lookup"><span data-stu-id="7d037-1069">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="7d037-1070">Повторное согласование можно инициировать в любое время после установки сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1070">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="7d037-1071">Если повторное согласование выполняется во время подтверждения TLS или до установки сеанса TLS, никакие действия не выполняются.</span><span class="sxs-lookup"><span data-stu-id="7d037-1071">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="7d037-1072">*При вызове этой службы будет выполнено полное подтверждение TLS, поэтому время выполнения и возврата состояния будет зависеть от текущих параметров TLS и параметров сеанса.*</span><span class="sxs-lookup"><span data-stu-id="7d037-1072">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="7d037-1073">NetX Secure TLS вводит в действие расширение для указания безопасного повторного согласования из документа RFC 5746, чтобы гарантировать, что подтверждения повторного согласования не будут подвергаться атакам "злоумышленник в середине".</span><span class="sxs-lookup"><span data-stu-id="7d037-1073">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1074">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1074">Parameters</span></span>

- <span data-ttu-id="7d037-1075">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1075">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1076">**wait_option** — указывает, как долго служба должна ожидать пакет от удаленного узла перед возвратом.</span><span class="sxs-lookup"><span data-stu-id="7d037-1076">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="7d037-1077">Это передается всем службам NetX в TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1077">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1078">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1078">Return Values</span></span>

- <span data-ttu-id="7d037-1079">**NX_SUCCESS** (0x00) — повторное согласование выполнено успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-1079">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="7d037-1080">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="7d037-1080">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7d037-1081">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="7d037-1081">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7d037-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) — полученное сообщение не прошло проверку подлинности хэша.</span><span class="sxs-lookup"><span data-stu-id="7d037-1082">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="7d037-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) — в заголовке полученного сообщения указана неизвестная версия протокола.</span><span class="sxs-lookup"><span data-stu-id="7d037-1083">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="7d037-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) — от удаленного узла получено оповещение TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1084">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="7d037-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) — локальный или удаленный сеанс TLS неактивен, из-за чего выполнение повторного согласования невозможно.</span><span class="sxs-lookup"><span data-stu-id="7d037-1085">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="7d037-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) — удаленный узел не предоставил ни SCSV, ни расширение безопасного повторного согласования, из-за чего не удалось выполнить повторное согласование.</span><span class="sxs-lookup"><span data-stu-id="7d037-1086">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="7d037-1087">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1087">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7d037-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1088">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="7d037-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) — не удалось выделить базовый пакет.</span><span class="sxs-lookup"><span data-stu-id="7d037-1089">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1090">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1090">Allowed From</span></span>

<span data-ttu-id="7d037-1091">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1091">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1092">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1092">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1093">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1093">See Also</span></span>

- <span data-ttu-id="7d037-1094">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1094">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1095">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1095">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1096">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1096">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-1097">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-1097">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-1098">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1098">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="7d037-1099">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="7d037-1099">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="7d037-1100">Очистка и сброс сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1100">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1101">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1101">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-1102">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1102">Description</span></span>

<span data-ttu-id="7d037-1103">Эта служба очищает сеанс TLS и сбрасывает состояние, как если бы сеанс был только что создан, чтобы существующий объект сеанса TLS можно было повторно использовать для нового сеанса.</span><span class="sxs-lookup"><span data-stu-id="7d037-1103">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1104">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1104">Parameters</span></span>

- <span data-ttu-id="7d037-1105">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1105">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1106">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1106">Return Values</span></span>

- <span data-ttu-id="7d037-1107">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1107">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-1108">**NX_INVALID_PARAMETERS** (0x4D) — недопустимый указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1108">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-1109">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1109">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1110">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1110">Allowed From</span></span>

<span data-ttu-id="7d037-1111">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1111">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1112">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1112">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="7d037-1113">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1113">See Also</span></span>

- <span data-ttu-id="7d037-1114">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1114">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1115">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1115">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1116">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1116">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1117">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-1117">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-1118">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-1118">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-1119">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1119">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-1120">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1120">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="7d037-1121">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-1121">nx_secure_tls_session_send</span></span>

<span data-ttu-id="7d037-1122">Отправка данных через сеанс NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1122">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1123">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1123">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d037-1124">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1124">Description</span></span>

<span data-ttu-id="7d037-1125">Эта служба отправляет данные в указанном NX_PACKET, используя указанный активный сеанс TLS, и выполняет шифрование этих данных перед их отправкой на удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="7d037-1125">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="7d037-1126">Если последний объявленный размер окна получателя меньше, чем этот запрос, служба при необходимости приостанавливает выполнение в соответствии с указанными параметрами ожидания.</span><span class="sxs-lookup"><span data-stu-id="7d037-1126">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-1127">*Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Иначе это приведет к непредсказуемым результатам, так как сетевой драйвер освободит пакет после передачи*.</span><span class="sxs-lookup"><span data-stu-id="7d037-1127">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1128">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1128">Parameters</span></span>

- <span data-ttu-id="7d037-1129">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1129">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1130">**packet_ptr** — указатель на пакет TLS, содержащий данные для отправки.</span><span class="sxs-lookup"><span data-stu-id="7d037-1130">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="7d037-1131">**wait_option** — определяет поведение службы в случае, если запрос превышает размер окна получателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1131">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1132">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1132">Return Values</span></span>

- <span data-ttu-id="7d037-1133">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1133">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-1134">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="7d037-1134">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="7d037-1135">**NX_NOT_CONNECTED** (0x38) — базовый TCP-сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="7d037-1135">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7d037-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) — не удалось отправить данные через базовый TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="7d037-1136">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="7d037-1137">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1137">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7d037-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) — указанный сеанс TLS не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1138">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1139">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1139">Allowed From</span></span>

<span data-ttu-id="7d037-1140">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1140">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1141">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1141">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="7d037-1142">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1142">See Also</span></span>

- <span data-ttu-id="7d037-1143">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1143">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7d037-1144">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1144">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1145">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1145">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1146">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1146">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="7d037-1147">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1147">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1148">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-1148">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-1149">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1149">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-1150">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-1150">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7d037-1151">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1151">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="7d037-1152">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1152">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="7d037-1153">Настройка обратного вызова для протокола TLS для вызова в начале подтверждения сервера TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1153">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1154">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1154">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="7d037-1155">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1155">Description</span></span>

<span data-ttu-id="7d037-1156">Эта служба назначает указатель функции сеансу TLS, который будет вызывать протокол TLS, если подтверждение сервера TLS получило сообщение ClientHello.</span><span class="sxs-lookup"><span data-stu-id="7d037-1156">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="7d037-1157">Функция обратного вызова позволяет приложению обрабатывать любые расширения TLS из полученного сообщения ClientHello, для которого необходимо ввести данные или принять решение.</span><span class="sxs-lookup"><span data-stu-id="7d037-1157">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="7d037-1158">Обратный вызов выполняется с помощью блока управления сеансом TLS и массива объектов NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="7d037-1158">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="7d037-1159">Массив объектов расширения необходимо передать во вспомогательную функцию, которая найдет и проанализирует определенное расширение.</span><span class="sxs-lookup"><span data-stu-id="7d037-1159">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="7d037-1160">Пример вспомогательной функции, которая анализирует расширения TLS, предоставленные в сообщениях приветствия, см. на странице *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="7d037-1160">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="7d037-1161">Обратный вызов сервера также можно использовать для выбора активного сертификата удостоверения с помощью *nx_secure_tls_active_certificate_set* для сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1161">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="7d037-1162">Чаще всего это происходит в ответ на расширение указания имени сервера (SNI), которое позволяет клиенту TLS указывать, какой сервер пытается связаться.</span><span class="sxs-lookup"><span data-stu-id="7d037-1162">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="7d037-1163">Дополнительные сведения см. в справочниках по *nx_secure_tls_session_sni_extension_parse* и *nx_secure_tls_active_certificate_set*.</span><span class="sxs-lookup"><span data-stu-id="7d037-1163">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1164">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1164">Parameters</span></span>

- <span data-ttu-id="7d037-1165">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1165">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1166">**func_ptr** — указатель на функцию обратного вызова сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1166">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1167">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1167">Return Values</span></span>

- <span data-ttu-id="7d037-1168">**NX_SUCCESS** (0x00) — успешное выделение указателя функции.</span><span class="sxs-lookup"><span data-stu-id="7d037-1168">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="7d037-1169">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1169">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1170">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1170">Allowed From</span></span>

<span data-ttu-id="7d037-1171">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1171">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1172">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1172">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1173">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1173">See Also</span></span>

- <span data-ttu-id="7d037-1174">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1174">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1175">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1175">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="7d037-1176">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1176">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="7d037-1177">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1177">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="7d037-1178">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-1178">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="7d037-1179">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="7d037-1179">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="7d037-1180">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1180">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="7d037-1181">Анализ расширения указания имени сервера (SNI), полученного от клиента TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1181">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1182">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1182">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="7d037-1183">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1183">Description</span></span>

<span data-ttu-id="7d037-1184">Эта служба должна вызываться из обратного вызова сеанса сервера TLS, который добавляется в сеанс TLS с помощью nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="7d037-1184">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="7d037-1185">Обратный вызов вызывается после получения сообщения ClientHello от удаленного клиента TLS и предоставляет массив доступных расширений (и количество расширений в массиве).</span><span class="sxs-lookup"><span data-stu-id="7d037-1185">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="7d037-1186">Этот массив и его длину можно передать непосредственно в эту подпрограмму, чтобы определить наличие расширения SNI. Если нет, возвращается NX_SECURE_TLS_EXTENSION_NOT_FOUND, указывая, что клиент решил не использовать расширение SNI (это не ошибка).</span><span class="sxs-lookup"><span data-stu-id="7d037-1186">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="7d037-1187">Если обнаружено расширение SNI, то в структуре dns_name возвращается DNS-имя X.509, предоставленное клиентом TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1187">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="7d037-1188">Сейчас расширение SNI предоставляет только одну запись DNS-имени, которая может использоваться сервером TLS для определения сертификата удостоверения, отправляемого удаленному клиенту.\*\*</span><span class="sxs-lookup"><span data-stu-id="7d037-1188">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="7d037-1189">Структура NX_SECURE_X509_DNS_NAME содержит только DNS-имя в виде строки UCHAR в поле *nx_secure_x509_dns_name* и длину строки имени в поле *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="7d037-1189">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="7d037-1190">Макрос NX_SECURE_X509_DNS_NAME_MAX определяет размер буфера nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="7d037-1190">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1191">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1191">Parameters</span></span>

- <span data-ttu-id="7d037-1192">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1192">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1193">**extensions** — указатель на массив расширений протокола TLS Hello (из обратного вызова сеанса).</span><span class="sxs-lookup"><span data-stu-id="7d037-1193">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="7d037-1194">**num_extensions** — количество расширений в массиве (из обратного вызова сеанса).</span><span class="sxs-lookup"><span data-stu-id="7d037-1194">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="7d037-1195">**dns_name** — возвращает DNS-имя, заданное в расширении SNI.</span><span class="sxs-lookup"><span data-stu-id="7d037-1195">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1196">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1196">Return Values</span></span>

- <span data-ttu-id="7d037-1197">**NX_SUCCESS** (0x00) — успешное выполнение анализа расширения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1197">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="7d037-1198">**NX_PTR_ERROR** (0x07) — недопустимый массив расширений или указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1198">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="7d037-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) — расширение SNI не найдено.</span><span class="sxs-lookup"><span data-stu-id="7d037-1199">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="7d037-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) — недопустимый формат расширения SNI.</span><span class="sxs-lookup"><span data-stu-id="7d037-1200">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1201">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1201">Allowed From</span></span>

<span data-ttu-id="7d037-1202">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1203">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1203">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="7d037-1204">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1204">See Also</span></span>

- <span data-ttu-id="7d037-1205">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1205">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="7d037-1206">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1206">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="7d037-1207">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1207">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="7d037-1208">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1208">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="7d037-1209">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1209">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="7d037-1210">Установка DNS-имени расширения указания имени сервера (SNI) для отправки на удаленный сервер</span><span class="sxs-lookup"><span data-stu-id="7d037-1210">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1211">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1211">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="7d037-1212">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1212">Description</span></span>

<span data-ttu-id="7d037-1213">Эта служба позволяет приложению клиента TLS предоставлять предпочитаемое DNS-имя сервера удаленному серверу TLS с помощью расширения указания имени сервера (SNI) TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1213">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="7d037-1214">Расширение SNI позволяет серверу выбрать правильный сертификат удостоверения и параметры на основе указанных предпочтений для сервера клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-1214">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="7d037-1215">Сейчас расширение SNI поддерживает отправку только одного DNS-имени, поэтому параметр имени имеет единственное число.</span><span class="sxs-lookup"><span data-stu-id="7d037-1215">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="7d037-1216">Параметр dns_name необходимо инициализировать с помощью *nx_secure_x509_dns_name_initialize* и он будет содержать предпочитаемый сервер клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-1216">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="7d037-1217">Чтобы удалить имя расширения, просто вызовите эту службу, задав для параметра dns_name значение NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="7d037-1217">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="7d037-1218">Структура NX_SECURE_X509_DNS_NAME содержит только DNS-имя в виде строки UCHAR в поле *nx_secure_x509_dns_name* и длину строки имени в поле *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="7d037-1218">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="7d037-1219">Макрос NX_SECURE_X509_DNS_NAME_MAX определяет размер буфера nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="7d037-1219">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="7d037-1220">*Эту подпрограмму следует вызывать до вызова nx_secure_tls_session_start, иначе ClientHello не будет содержать расширение SNI*.</span><span class="sxs-lookup"><span data-stu-id="7d037-1220">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1221">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1221">Parameters</span></span>

- <span data-ttu-id="7d037-1222">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1222">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1223">**dns_name** — DNS-имя, предоставленное приложением.</span><span class="sxs-lookup"><span data-stu-id="7d037-1223">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1224">Return Values</span></span>

- <span data-ttu-id="7d037-1225">**NX_SUCCESS** (0x00) — DNS-имя сервера успешно добавлено.</span><span class="sxs-lookup"><span data-stu-id="7d037-1225">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="7d037-1226">**NX_PTR_ERROR** (0x07) — недопустимое DNS-имя или указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1226">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1227">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1227">Allowed From</span></span>

<span data-ttu-id="7d037-1228">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1228">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1229">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1229">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1230">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1230">See Also</span></span>

- <span data-ttu-id="7d037-1231">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1231">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1232">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1232">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="7d037-1233">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1233">nx_secure_tls_session_start</span></span>

<span data-ttu-id="7d037-1234">Запуск сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1234">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1235">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1235">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="7d037-1236">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1236">Description</span></span>

<span data-ttu-id="7d037-1237">Эта служба запускает сеанс TLS, используя указанный блок управления сеансом TLS и подключенный TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="7d037-1237">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="7d037-1238">TCP-соединение должно завершиться после успешного вызова nx_tcp_client_socket_connect или nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="7d037-1238">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="7d037-1239">Эта служба определит тип сеанса TLS (клиент или сервер) из TCP-сокета.</span><span class="sxs-lookup"><span data-stu-id="7d037-1239">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="7d037-1240">Параметр ожидания определяет поведение службы во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1240">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1241">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1241">Parameters</span></span>

- <span data-ttu-id="7d037-1242">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1242">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1243">**tcp_socket_ptr** — указатель на подключенный TCP-сокет.</span><span class="sxs-lookup"><span data-stu-id="7d037-1243">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="7d037-1244">**wait_option** — определяет поведение службы во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1244">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1245">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1245">Return Values</span></span>

- <span data-ttu-id="7d037-1246">**TX_SUCCESS** (0x00): сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1246">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-1247">**NX_NOT_CONNECTED** (0x38): базовый сокет TCP больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="7d037-1247">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="7d037-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102): получен неправильный тип сообщения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1248">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="7d037-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106): шифр, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7d037-1249">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="7d037-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107): не удалось обработать сообщение во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1250">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="7d037-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108): не удалось проверить хэш MAC во входящем сообщении.</span><span class="sxs-lookup"><span data-stu-id="7d037-1251">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="7d037-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): не удалось отправить данные через базовый сокет TCP.</span><span class="sxs-lookup"><span data-stu-id="7d037-1252">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="7d037-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A): входящее сообщение содержало недопустимое поле длины.</span><span class="sxs-lookup"><span data-stu-id="7d037-1253">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="7d037-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) — неправильное входящее сообщение ChangeCipherSpec.</span><span class="sxs-lookup"><span data-stu-id="7d037-1254">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="7d037-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) — входящий сертификат TLS невозможно использовать для идентификации удаленного сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1255">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="7d037-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) — шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7d037-1256">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="7d037-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1257">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="7d037-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F): в заголовке полученного сообщения TLS указана неизвестная версия TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1258">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="7d037-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110): в заголовке полученного сообщения TLS указана неподдерживаемая версия TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1259">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="7d037-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить внутренний пакет TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1260">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="7d037-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112): удаленный узел предоставил недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-1261">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="7d037-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114): удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1262">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="7d037-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) —запись в таблице комплектов шифров содержала указатель на функцию со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="7d037-1263">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="7d037-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) — удаленное ClientHello TLS включало резервное SCSV и была выполнена попытка отката версии.</span><span class="sxs-lookup"><span data-stu-id="7d037-1264">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="7d037-1265">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1265">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1266">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1266">Allowed From</span></span>

<span data-ttu-id="7d037-1267">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1268">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1268">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1269">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1269">See Also</span></span>

- <span data-ttu-id="7d037-1270">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1270">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="7d037-1271">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1271">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1272">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1272">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1273">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="7d037-1273">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="7d037-1274">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-1274">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-1275">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1275">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-1276">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1276">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="7d037-1277">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="7d037-1277">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="7d037-1278">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1278">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1279">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="7d037-1279">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="7d037-1280">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="7d037-1280">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="7d037-1281">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="7d037-1281">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="7d037-1282">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="7d037-1282">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="7d037-1283">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="7d037-1283">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="7d037-1284">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-1284">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="7d037-1285">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1285">nx_packet_allocate</span></span>
- <span data-ttu-id="7d037-1286">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="7d037-1286">nx_packet_data_append</span></span>
- <span data-ttu-id="7d037-1287">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="7d037-1287">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="7d037-1288">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1288">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="7d037-1289">Назначение функции метки времени в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1289">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1290">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1290">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="7d037-1291">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1291">Description</span></span>

<span data-ttu-id="7d037-1292">Эта функция устанавливает указатель функции, который будет вызываться проколом TLS, когда необходимо получить текущее время, которое используется в различных сообщениях подтверждения TLS и для проверки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-1292">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="7d037-1293">Функция должна вернуть текущее время GMT в 32-битном формате UNIX (секунды с момента полуночи 1 января 1970 г., в формате UTC, игнорируя корректировочные секунды) согласно требованиям ClientHello в документе TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="7d037-1293">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="7d037-1294">Если функция метки времени не назначена, в подтверждении TLS для метки времени будет использоваться значение 0 и проверка истечения срока действия сертификата не будет работать.</span><span class="sxs-lookup"><span data-stu-id="7d037-1294">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1295">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1295">Parameters</span></span>

- <span data-ttu-id="7d037-1296">**session_ptr** — указатель на экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1296">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1297">**time_func_ptr** — указатель на функцию, которая возвращает текущее время (GMT) в 32-битном формате UNIX.</span><span class="sxs-lookup"><span data-stu-id="7d037-1297">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1298">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1298">Return Values</span></span>

- <span data-ttu-id="7d037-1299">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="7d037-1299">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="7d037-1300">**NX_INVALID_PARAMETERS** (0x4D) — недопустимый указатель сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1300">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-1301">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1301">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1302">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1302">Allowed From</span></span>

<span data-ttu-id="7d037-1303">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1303">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1304">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1304">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1305">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1305">See Also</span></span>

- <span data-ttu-id="7d037-1306">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1306">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1307">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1307">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1308">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="7d037-1308">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="7d037-1309">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="7d037-1309">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="7d037-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="7d037-1310">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="7d037-1311">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1311">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="7d037-1312">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-1312">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="7d037-1313">Добавление доверенного сертификата в сеансе NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1313">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1314">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1314">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="7d037-1315">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1315">Description</span></span>

<span data-ttu-id="7d037-1316">Эта служба добавляет инициализированный экземпляр структуры NX_SECURE_X509_CERT в сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1316">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="7d037-1317">Этот сертификат используется в стеке TLS для проверки сертификатов, предоставляемых удаленным узлом во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1317">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="7d037-1318">Доверенные сертификаты необходимы для режима клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1318">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="7d037-1319">Доверенные сертификаты требуются только для режима сервера TLS, если включена проверка подлинности с помощью сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-1319">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1320">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1320">Parameters</span></span>

- <span data-ttu-id="7d037-1321">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1321">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1322">**certificate_ptr** — указатель на инициализированный экземпляр сертификата TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1322">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1323">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1323">Return Values</span></span>

- <span data-ttu-id="7d037-1324">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1324">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7d037-1325">**NX_INVALID_PARAMETERS** (0x4D) — попытка добавить недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-1325">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="7d037-1326">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1326">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1327">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1327">Allowed From</span></span>

<span data-ttu-id="7d037-1328">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1328">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1329">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1329">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1330">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1330">See Also</span></span>

- <span data-ttu-id="7d037-1331">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1331">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1332">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1332">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1333">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1333">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1334">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-1334">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="7d037-1335">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="7d037-1335">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="7d037-1336">Удаление доверенного сертификата из сеанса NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1336">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1337">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1337">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="7d037-1338">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1338">Description</span></span>

<span data-ttu-id="7d037-1339">Эта служба удаляет доверенный сертификат из сеанса TLS, введенный в поле "Общее имя" сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1339">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1340">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1340">Parameters</span></span>

- <span data-ttu-id="7d037-1341">**session_ptr** — указатель на созданный ранее экземпляр сеанса TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1341">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="7d037-1342">**common_name** — значение общего имени удаляемого сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1342">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="7d037-1343">**common_name_length** — длина строки общего имени.</span><span class="sxs-lookup"><span data-stu-id="7d037-1343">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1344">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1344">Return Values</span></span>

- <span data-ttu-id="7d037-1345">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7d037-1346">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1346">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="7d037-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат не найден.</span><span class="sxs-lookup"><span data-stu-id="7d037-1347">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1348">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1348">Allowed From</span></span>

<span data-ttu-id="7d037-1349">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1350">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1350">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-1351">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1351">See Also</span></span>

- <span data-ttu-id="7d037-1352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="7d037-1353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1355">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-1355">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="7d037-1356">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1356">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="7d037-1357">Инициализация сертификата X.509 для NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1357">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1358">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1358">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="7d037-1359">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1359">Description</span></span>

<span data-ttu-id="7d037-1360">Эта служба инициализирует структуру NX_SECURE_X509_CERT из цифрового сертификата X.509 в двоичной кодировке для использования в сеансе TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1360">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="7d037-1361">Данные сертификата **должны** быть данными допустимого цифрового сертификата X.509 в формате двоичной кодировки DER.</span><span class="sxs-lookup"><span data-stu-id="7d037-1361">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="7d037-1362">Любой объект может стать источником данных (например, файловая система, скомпилированный буфер констант и т. д.), если на эти данные предоставлен указатель UCHAR.</span><span class="sxs-lookup"><span data-stu-id="7d037-1362">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="7d037-1363">Параметр *raw_data_buffer* и его размер являются необязательными параметрами, которые указывают выделенный буфер, в который копируются данные сертификата перед синтаксическим анализом.</span><span class="sxs-lookup"><span data-stu-id="7d037-1363">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="7d037-1364">Если raw_data_buffer передается со значением NX_NULL, то структура NX_SECURE_X509_CERT будет указывать непосредственно в массив certificate_data (в этом случае buffer_size игнорируется).</span><span class="sxs-lookup"><span data-stu-id="7d037-1364">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="7d037-1365">Если raw_data_buffer передается со значением NX_NULL, ***не*** изменяйте данные, на которые указывает указатель certificate_data, иначе обработка сертификата, скорее всего, завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="7d037-1365">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="7d037-1366">Параметр закрытого ключа предназначен для локальных сертификатов удостоверений. Закрытый ключ используется серверами для расшифровки входных данных ключа от клиента (зашифрованных с помощью открытого ключа сервера) и клиентами для проверки их удостоверений на сервере, когда сервер запрашивает сертификат клиента.</span><span class="sxs-lookup"><span data-stu-id="7d037-1366">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="7d037-1367">При добавлении закрытого ключа с помощью этого API соответствующий сертификат автоматически помечается как сертификат удостоверения для приложения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1367">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="7d037-1368">При инициализации сертификатов для других целей (например, доверенного хранилища) параметр *private_key_data* должен передаваться со значением NULL, *private_key_data_length* — с 0, а *private_key_type* — с NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="7d037-1368">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="7d037-1369">Параметр *private_key_type* указывает форматирование закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="7d037-1369">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="7d037-1370">Например, если закрытый ключ является закрытым ключом RSA в формате PKCS#1 с кодировкой DER, private_key_type необходимо передавать со значением NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER. Этот тип также известен NetX Secure, как тип, который будет немедленно проанализирован и сохранен для последующего использования.</span><span class="sxs-lookup"><span data-stu-id="7d037-1370">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="7d037-1371">private_key_type также поддерживает определяемые пользователем типы ключей<sup>23</sup> для платформ и приложений, имеющих определенные форматы ключей или другие потребности.</span><span class="sxs-lookup"><span data-stu-id="7d037-1371">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="7d037-1372">Например, аппаратное средство шифрования может использовать конкретный формат, не распознаваемый программным обеспечением NetX Secure, либо закрытый ключ может быть зашифрован или представлен криптографическим маркером, как это может быть в случае с таким оборудованием шифрования, как доверенный платформенный модуль (TPM) или PKCS#11.</span><span class="sxs-lookup"><span data-stu-id="7d037-1372">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="7d037-1373">При использовании определяемого пользователем типа ключа данные ключа передаются в соответствующую криптографическую подпрограмму. Например, закрытый ключ RSA передается без какого-либо анализа или обработки непосредственно в подпрограмму шифрования RSA, предоставляемую для TLS в таблице комплектов шифров.</span><span class="sxs-lookup"><span data-stu-id="7d037-1373">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="7d037-1374">Определяемый пользователем тип ключа также передается в подпрограммы шифрования (в случае RSA это параметр "op").</span><span class="sxs-lookup"><span data-stu-id="7d037-1374">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="7d037-1375">Диапазон определяемых пользователем ключей охватывает верхнюю половину 32-битного целого числа без знака от значения 0x0001 0000-0xFFFF FFFF.</span><span class="sxs-lookup"><span data-stu-id="7d037-1375">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="7d037-1376">Значения меньше 0x0001 0000 зарезервированы для использования в NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="7d037-1376">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="7d037-1377">Определяемые пользователем типы ключей представляют собой дополнительную возможность, требующую пользовательских криптографических подпрограмм для обработки необработанных данных закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="7d037-1377">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="7d037-1378">Если вам нужна эта возможность, обратитесь к своему представителю Express Logic.</span><span class="sxs-lookup"><span data-stu-id="7d037-1378">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1379">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1379">Parameters</span></span>

- <span data-ttu-id="7d037-1380">**certificate_ptr** — указатель на неинициализированный экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-1380">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="7d037-1381">**certificate_data** — указатель на двоичные данные X.509 в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="7d037-1381">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="7d037-1382">**raw_data_buffer** — указатель на необязательный буфер данных выделенного сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1382">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="7d037-1383">**buffer_size** — размер необязательного буфера данных выделенного сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1383">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="7d037-1384">**certificate_data_length** — длина двоичных данных сертификата в байтах.</span><span class="sxs-lookup"><span data-stu-id="7d037-1384">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="7d037-1385">**private_key_data** — указатель на необязательные данные закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="7d037-1385">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="7d037-1386">**private_key_data_length** — длина данных закрытого ключа.</span><span class="sxs-lookup"><span data-stu-id="7d037-1386">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="7d037-1387">**private_key_type** — идентификатор типа ключа.</span><span class="sxs-lookup"><span data-stu-id="7d037-1387">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1388">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1388">Return Values</span></span>

- <span data-ttu-id="7d037-1389">**NX_SUCCESS** (0x00) — успешное добавление сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1389">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="7d037-1390">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1390">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="7d037-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) — данные сертификата не содержат сертификат X.509 в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="7d037-1391">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="7d037-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) — в сертификате отсутствует шифр открытого ключа, поддерживаемый в NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="7d037-1392">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="7d037-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) — закрытый ключ или сертификат не содержат допустимую последовательность ASN.1.</span><span class="sxs-lookup"><span data-stu-id="7d037-1393">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="7d037-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) — предоставленный закрытый ключ не является допустимым ключом PKCS#1 RSA.</span><span class="sxs-lookup"><span data-stu-id="7d037-1394">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="7d037-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) — указанный тип закрытого ключа не был определен пользователем и не соответствует ни одному известному типу.</span><span class="sxs-lookup"><span data-stu-id="7d037-1395">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1396">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1396">Allowed From</span></span>

<span data-ttu-id="7d037-1397">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1398">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1398">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="7d037-1399">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1399">See Also</span></span>

- <span data-ttu-id="7d037-1400">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="7d037-1400">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="7d037-1401">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1401">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1402">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="7d037-1402">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="7d037-1403">Импорт сертификатов X.509 в NetX Secure в главе 3.</span><span class="sxs-lookup"><span data-stu-id="7d037-1403">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="7d037-1404">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1404">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="7d037-1405">Проверка DNS-имени на соответствие сертификату X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1405">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1406">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1406">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="7d037-1407">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1407">Description</span></span>

<span data-ttu-id="7d037-1408">Эта служба проверяет общее имя сертификата на соответствие доменному имени верхнего уровня (TLD), предоставленному вызывающим объектом в целях проверки DNS удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="7d037-1408">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="7d037-1409">Эту служебную функцию должна вызывать предоставленная приложением подпрограмма обратного вызова для проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1409">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="7d037-1410">Имя TLD должно быть верхней частью URL-адреса, используемого для доступа к удаленному узлу (строка, разделенная "."перед первой косой чертой).</span><span class="sxs-lookup"><span data-stu-id="7d037-1410">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="7d037-1411">Если общее имя содержит подстановочный знак (например, *.example.com), то подстановочный знак будет соответствовать любому суффиксу. Обратите внимание, что только первый обнаруженный подстановочный знак ("* ") (при чтении справа налево) будет учитываться при сопоставлении с подстановочными знаками, например abc.\*.example.com будет соответствовать *любому* имени, которое заканчивается на ".example.com".</span><span class="sxs-lookup"><span data-stu-id="7d037-1411">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="7d037-1412">Если общее имя не совпадает с указанной строкой, то будет выполняться анализ расширения subjectAltName (если оно есть в сертификате), а также будут сравниваться все записи DNSName.</span><span class="sxs-lookup"><span data-stu-id="7d037-1412">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="7d037-1413">Если ни одна из этих записей не совпадает с указанной строкой, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="7d037-1413">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="7d037-1414">Важно понимать, в каком формате находится общее имя (и записи subjectAltName) в ожидаемых сертификатах.</span><span class="sxs-lookup"><span data-stu-id="7d037-1414">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="7d037-1415">Например, некоторые сертификаты могут использовать необработанный IP-адрес или подстановочный знак.</span><span class="sxs-lookup"><span data-stu-id="7d037-1415">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="7d037-1416">Строка доменов верхнего уровня DNS должна быть отформатирована таким образом, чтоб она соответствовала ожидаемым значениям в полученных сертификатах.</span><span class="sxs-lookup"><span data-stu-id="7d037-1416">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1417">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1417">Parameters</span></span>

- <span data-ttu-id="7d037-1418">**certificate_ptr** — указатель на экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-1418">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="7d037-1419">**dns_tld** — имя домена верхнего уровня для сравнения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1419">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="7d037-1420">**dns_tld_length** — длина строки TLD.</span><span class="sxs-lookup"><span data-stu-id="7d037-1420">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1421">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1421">Return Values</span></span>

- <span data-ttu-id="7d037-1422">**NX_SUCCESS** (0x00) — успешное сравнение с общим именем или subjectAltName.</span><span class="sxs-lookup"><span data-stu-id="7d037-1422">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="7d037-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) — соответствующее имя не найдено.</span><span class="sxs-lookup"><span data-stu-id="7d037-1423">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="7d037-1424">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1424">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1425">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1425">Allowed From</span></span>

<span data-ttu-id="7d037-1426">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1426">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1427">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1427">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1428">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1428">See Also</span></span>

- <span data-ttu-id="7d037-1429">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1429">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1430">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1430">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7d037-1431">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1431">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="7d037-1432">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1432">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="7d037-1433">Проверка сертификата X.509 на соответствие заданному списку отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-1433">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1434">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1434">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="7d037-1435">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1435">Description</span></span>

<span data-ttu-id="7d037-1436">Эта служба принимает список отзыва сертификатов в кодировке DER и ищет конкретный сертификат в этом списке.</span><span class="sxs-lookup"><span data-stu-id="7d037-1436">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="7d037-1437">Издатель списка отзыва сертификатов проверяется на соответствие предоставленному хранилищу сертификатов. Издатель списка отзыва сертификатов должен совпадать с издателем проверяемого сертификата, а серийный номер рассматриваемого сертификата используется для поиска по списку отозванных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-1437">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="7d037-1438">Если издатели совпадают, подпись извлекается, а сертификат **отсутствует** в списке, вызов завершается успешно.</span><span class="sxs-lookup"><span data-stu-id="7d037-1438">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="7d037-1439">Во всех остальных случаях возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="7d037-1439">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1440">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1440">Parameters</span></span>

- <span data-ttu-id="7d037-1441">**crl_data** — указатель на список отзыва сертификатов в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="7d037-1441">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="7d037-1442">**crl_length** — длина данных списка отзыва сертификатов в байтах.</span><span class="sxs-lookup"><span data-stu-id="7d037-1442">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="7d037-1443">**store** — указатель на хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-1443">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="7d037-1444">**certificate_ptr** — указатель на экземпляр сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-1444">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1445">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1445">Return Values</span></span>

- <span data-ttu-id="7d037-1446">**NX_SUCCESS** (0x00) — успешная проверка того, что сертификат не был отозван.</span><span class="sxs-lookup"><span data-stu-id="7d037-1446">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="7d037-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) — сертификат издателя списка отзыва сертификатов не найден.</span><span class="sxs-lookup"><span data-stu-id="7d037-1447">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="7d037-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** (0x11B) — сертификат издателя сертификатов не найден.</span><span class="sxs-lookup"><span data-stu-id="7d037-1448">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="7d037-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — список отзыва сертификатов ASN.1 содержит поле недопустимой длины.</span><span class="sxs-lookup"><span data-stu-id="7d037-1449">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="7d037-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG** (0x189) — список отзыва сертификатов содержал недопустимый ASN.1.</span><span class="sxs-lookup"><span data-stu-id="7d037-1450">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="7d037-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) — не удалось проверить цепочку сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-1451">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="7d037-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) — список отзыва сертификатов и издатели сертификатов не совпадают.</span><span class="sxs-lookup"><span data-stu-id="7d037-1452">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="7d037-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** (0x198) — недопустимая подпись списка отзыва сертификатов.</span><span class="sxs-lookup"><span data-stu-id="7d037-1453">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="7d037-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) — проверяемый сертификат был найден в списке отзыва сертификатов и поэтому отозван.</span><span class="sxs-lookup"><span data-stu-id="7d037-1454">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="7d037-1455">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1455">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1456">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1456">Allowed From</span></span>

<span data-ttu-id="7d037-1457">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1458">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1458">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1459">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1459">See Also</span></span>

- <span data-ttu-id="7d037-1460">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1460">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1461">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1461">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7d037-1462">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1462">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="7d037-1463">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="7d037-1463">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="7d037-1464">Инициализация структуры DNS-имени X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1464">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1465">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1465">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="7d037-1466">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1466">Description</span></span>

<span data-ttu-id="7d037-1467">Эта служба инициализирует DNS-имя X.509 для использования с определенными службами API, для которых необходим определенный формат имени.</span><span class="sxs-lookup"><span data-stu-id="7d037-1467">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="7d037-1468">Например, служба *nx_secure_tls_sni_extension_parse* ожидает объект NX_SECURE_X509_DNS_NAME, чтобы сопоставить имя, которое предоставил удаленный узел в расширении указания имени сервера во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="7d037-1468">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="7d037-1469">DNS-имя — это просто строка символов, которая имеет длину. Максимально допустимой длиной DNS-имени (и размером внутреннего буфера в NX_SECURE_X509_DNS_NAME) управляет макрос NX_SECURE_X509_DNS_NAME_MAX (по умолчанию 100 байт).</span><span class="sxs-lookup"><span data-stu-id="7d037-1469">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1470">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1470">Parameters</span></span>

- <span data-ttu-id="7d037-1471">**dns_name** — структура DNS-имени для инициализации.</span><span class="sxs-lookup"><span data-stu-id="7d037-1471">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="7d037-1472">**name_string** — данные строки DNS-имени.</span><span class="sxs-lookup"><span data-stu-id="7d037-1472">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="7d037-1473">**length** — длина строки имени.</span><span class="sxs-lookup"><span data-stu-id="7d037-1473">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1474">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1474">Return Values</span></span>

- <span data-ttu-id="7d037-1475">**NX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="7d037-1475">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="7d037-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) — заданная строка имени превысила значение NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="7d037-1476">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="7d037-1477">**NX_PTR_ERROR** (0x07) — выполнена попытка использования недопустимого указателя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1477">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1478">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1478">Allowed From</span></span>

<span data-ttu-id="7d037-1479">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1480">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1480">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="7d037-1481">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1481">See Also</span></span>

- <span data-ttu-id="7d037-1482">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="7d037-1482">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="7d037-1483">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1483">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="7d037-1484">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1484">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="7d037-1485">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1485">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="7d037-1486">Поиск и анализ расширения расширенного использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1486">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1487">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1487">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="7d037-1488">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1488">Description</span></span>

<span data-ttu-id="7d037-1489">Эта служба должна вызываться из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set)* .</span><span class="sxs-lookup"><span data-stu-id="7d037-1489">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="7d037-1490">Она выполнит поиск конкретного идентификатора объекта расширенного использования ключа в сертификате X.509 и возвратит сведения о том, присутствует ли этот идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="7d037-1490">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="7d037-1491">Параметр key_usage — это сопоставление целых чисел идентификаторов объектов, которые используются внутри NetX Secure X.509 и TLS для избежания передачи строк идентификатора объекта переменной длины в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="7d037-1491">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="7d037-1492">Соответствующие идентификаторы объектов для расширения расширенного использования ключа приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="7d037-1492">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="7d037-1493">В типичной реализации клиента TLS, предусматривающей проверку расширенного использования ключа в полученном сертификате сервера TLS, будет выполнена проверка наличия идентификатора объекта NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH. Если расширение есть, а не идентификатора объекта нет, сертификат будет считаться недопустимым для идентификации узла в качестве сервера TLS, а обратный вызов проверки сертификата возвратит ошибку.</span><span class="sxs-lookup"><span data-stu-id="7d037-1493">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="7d037-1494">Приложение может выбирать, требуется ли продолжать подтверждение TLS, если само расширение отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7d037-1494">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="7d037-1495">В обратном вызове проверки сертификата код возврата ошибки NX_SECURE_X509_KEY_USAGE_ERROR зарезервирован для использования приложением.</span><span class="sxs-lookup"><span data-stu-id="7d037-1495">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="7d037-1496">Если при проверке использования ключа возникает ошибка, обратный вызов может возвратить это значение для указания причины сбоя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1496">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="7d037-1497">Идентификатор NetX Secure</span><span class="sxs-lookup"><span data-stu-id="7d037-1497">NetX Secure Identifier</span></span>                                | <span data-ttu-id="7d037-1498">Значение идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="7d037-1498">OID Value</span></span>         | <span data-ttu-id="7d037-1499">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1499">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="7d037-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="7d037-1500">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="7d037-1501">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="7d037-1501">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="7d037-1502">Сертификат можно использовать для определения сервера TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1502">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="7d037-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="7d037-1503">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="7d037-1504">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="7d037-1504">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="7d037-1505">Сертификат можно использовать для определения клиента TLS</span><span class="sxs-lookup"><span data-stu-id="7d037-1505">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="7d037-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="7d037-1506">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="7d037-1507">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="7d037-1507">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="7d037-1508">Сертификат можно использовать для подписи кода</span><span class="sxs-lookup"><span data-stu-id="7d037-1508">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="7d037-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="7d037-1509">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="7d037-1510">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="7d037-1510">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="7d037-1511">Сертификат можно использовать для подписи сообщений электронной почты</span><span class="sxs-lookup"><span data-stu-id="7d037-1511">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="7d037-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="7d037-1512">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="7d037-1513">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="7d037-1513">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="7d037-1514">Сертификат можно использовать для подписи меток времени</span><span class="sxs-lookup"><span data-stu-id="7d037-1514">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="7d037-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="7d037-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="7d037-1516">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="7d037-1516">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="7d037-1517">Сертификат можно использовать для подписи ответов OCSP</span><span class="sxs-lookup"><span data-stu-id="7d037-1517">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="7d037-1518">Идентификаторы объектов и сопоставления для расширения расширенного использования ключа X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1518">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1519">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1519">Parameters</span></span>

- <span data-ttu-id="7d037-1520">**certificate** — указатель на проверяемый сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-1520">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="7d037-1521">**key_usage** — сопоставление целых чисел идентификатора объекта из таблицы выше.</span><span class="sxs-lookup"><span data-stu-id="7d037-1521">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1522">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1522">Return Values</span></span>

- <span data-ttu-id="7d037-1523">**NX_SUCCESS** (0x00) — указанный идентификатор объекта использования ключа найден.</span><span class="sxs-lookup"><span data-stu-id="7d037-1523">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="7d037-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1524">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="7d037-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1525">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1526">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1527">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — расширение расширенного использования ключа не найдено в указанном сертификате.</span><span class="sxs-lookup"><span data-stu-id="7d037-1528">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="7d037-1529">**NX_PTR_ERROR** (0x07) — недопустимый указатель сертификата.</span><span class="sxs-lookup"><span data-stu-id="7d037-1529">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1530">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1530">Allowed From</span></span>

<span data-ttu-id="7d037-1531">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1532">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1532">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1533">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1533">See Also</span></span>

- <span data-ttu-id="7d037-1534">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1534">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7d037-1535">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1535">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="7d037-1536">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1536">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="7d037-1537">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1537">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7d037-1538">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7d037-1538">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="7d037-1539">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7d037-1539">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="7d037-1540">Поиск и возврат расширения X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1540">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1541">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1541">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="7d037-1542">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1542">Description</span></span>

<span data-ttu-id="7d037-1543">Эту службу следует вызывать из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set*). Она является расширенной службой X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-1543">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="7d037-1544">Функция будет искать определенное расширение в сертификате X.509 на основе идентификатора объекта и возвратит сведения о том, присутствует ли идентификатор, а также структуру, содержащую ссылки на соответствующие необработанные данные расширения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1544">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="7d037-1545">Параметр extension_id — это сопоставление целых чисел идентификаторов объектов, которые используются внутри NetX Secure X.509 и TLS для избежания передачи строк идентификатора объекта переменной длины в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="7d037-1545">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="7d037-1546">Вспомогательные функции для конкретных расширений (например, *nx_secure_x509_key_usage_extension_parse*) вызывают nx_secure_x509_extension_find внутренне для получения данных расширения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1546">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="7d037-1547">Соответствующие идентификаторы объектов для известных расширений X.509 приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="7d037-1547">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="7d037-1548">Структура NX_SECURE_X509_EXTENSION содержит указатели на сертификат X.509, которые позволяют вспомогательным функциям, таким как *nx_secure_x509_key_usage_extension_parse*, быстро декодировать необработанные данные расширения ASN.1 в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="7d037-1548">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="7d037-1549">Сведения о конкретных расширениях см. в документе RFC 5280 (спецификация X.509) или в справочнике по соответствующим вспомогательным функциям, если они доступны.</span><span class="sxs-lookup"><span data-stu-id="7d037-1549">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="7d037-1550">Текущая версия NetX Secure X.509 имеет ограниченную поддержку расширений X.509.</span><span class="sxs-lookup"><span data-stu-id="7d037-1550">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="7d037-1551">В будущем будут добавлены дополнительные вспомогательные функции.</span><span class="sxs-lookup"><span data-stu-id="7d037-1551">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d037-1552">*Эта служба является расширенной функцией для пользователей, знакомых с расширениями X.509 и ASN.1 в кодировке DER. Она предоставляет этим пользователям доступ к расширениям, для которых NetX Secure X.509 в данный момент не предоставляет вспомогательные функции. Для этих расширений без вспомогательных функций необходимо самостоятельно анализировать необработанный ASN.1 в кодировке DER.*</span><span class="sxs-lookup"><span data-stu-id="7d037-1552">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="7d037-1553">Идентификатор NetX Secure</span><span class="sxs-lookup"><span data-stu-id="7d037-1553">NetX Secure Identifier</span></span>                              | <span data-ttu-id="7d037-1554">Значение идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="7d037-1554">OID Value</span></span> | <span data-ttu-id="7d037-1555">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1555">Description</span></span>                                                                    | <span data-ttu-id="7d037-1556">Вспомогательная функция?</span><span class="sxs-lookup"><span data-stu-id="7d037-1556">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="7d037-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="7d037-1557">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="7d037-1558">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="7d037-1558">2.5.29.9</span></span>  | <span data-ttu-id="7d037-1559">Атрибуты каталога — это основные атрибуты сведений о субъекте сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-1559">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="7d037-1560">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1560">No</span></span>               |
| <span data-ttu-id="7d037-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="7d037-1561">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="7d037-1562">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="7d037-1562">2.5.29.14</span></span> | <span data-ttu-id="7d037-1563">Используется для определения конкретного открытого ключа</span><span class="sxs-lookup"><span data-stu-id="7d037-1563">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="7d037-1564">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1564">No</span></span>               |
| <span data-ttu-id="7d037-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="7d037-1565">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="7d037-1566">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="7d037-1566">2.5.29.15</span></span> | <span data-ttu-id="7d037-1567">Предоставляет сведения о допустимых методах использования открытого ключа сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-1567">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="7d037-1568">Да</span><span class="sxs-lookup"><span data-stu-id="7d037-1568">Yes</span></span>              |
| <span data-ttu-id="7d037-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="7d037-1569">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="7d037-1570">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="7d037-1570">2.5.29.17</span></span> | <span data-ttu-id="7d037-1571">Предоставляет альтернативные DNS-имена для определения сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-1571">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="7d037-1572">Да<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="7d037-1572">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="7d037-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="7d037-1573">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="7d037-1574">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="7d037-1574">2.5.29.18</span></span> | <span data-ttu-id="7d037-1575">Предоставляет альтернативные DNS-имена для определения издателя сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-1575">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="7d037-1576">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1576">No</span></span>               |
| <span data-ttu-id="7d037-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="7d037-1577">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="7d037-1578">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="7d037-1578">2.5.29.19</span></span> | <span data-ttu-id="7d037-1579">Предоставляет основные сведения об ограничении использования сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-1579">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="7d037-1580">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1580">No</span></span>               |
| <span data-ttu-id="7d037-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="7d037-1581">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="7d037-1582">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="7d037-1582">2.5.29.30</span></span> | <span data-ttu-id="7d037-1583">Используется, чтобы ограничить использование имен сертификатов до конкретных доменов</span><span class="sxs-lookup"><span data-stu-id="7d037-1583">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="7d037-1584">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1584">No</span></span>               |
| <span data-ttu-id="7d037-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="7d037-1585">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="7d037-1586">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="7d037-1586">2.5.29.31</span></span> | <span data-ttu-id="7d037-1587">Предоставляет коды URI для распространения списка отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-1587">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="7d037-1588">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1588">No</span></span>               |
| <span data-ttu-id="7d037-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="7d037-1589">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="7d037-1590">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="7d037-1590">2.5.29.32</span></span> | <span data-ttu-id="7d037-1591">Список политик сертификатов для крупных систем PKI</span><span class="sxs-lookup"><span data-stu-id="7d037-1591">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="7d037-1592">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1592">No</span></span>               |
| <span data-ttu-id="7d037-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="7d037-1593">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="7d037-1594">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="7d037-1594">2.5.29.33</span></span> | <span data-ttu-id="7d037-1595">Список политик сертификатов ЦС</span><span class="sxs-lookup"><span data-stu-id="7d037-1595">List of CA certificate policies</span></span>                                                | <span data-ttu-id="7d037-1596">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1596">No</span></span>               |
| <span data-ttu-id="7d037-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="7d037-1597">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="7d037-1598">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="7d037-1598">2.5.29.35</span></span> | <span data-ttu-id="7d037-1599">Используется для идентификации определенного открытого ключа, связанного с подписью сертификата</span><span class="sxs-lookup"><span data-stu-id="7d037-1599">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="7d037-1600">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1600">No</span></span>               |
| <span data-ttu-id="7d037-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="7d037-1601">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="7d037-1602">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="7d037-1602">2.5.29.36</span></span> | <span data-ttu-id="7d037-1603">Ограничения политики ЦС</span><span class="sxs-lookup"><span data-stu-id="7d037-1603">CA policy constraints</span></span>                                                          | <span data-ttu-id="7d037-1604">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1604">No</span></span>               |
| <span data-ttu-id="7d037-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="7d037-1605">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="7d037-1606">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="7d037-1606">2.5.29.37</span></span> | <span data-ttu-id="7d037-1607">Дополнительные сведения об использовании ключа на основе идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="7d037-1607">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="7d037-1608">Да</span><span class="sxs-lookup"><span data-stu-id="7d037-1608">Yes</span></span>              |
| <span data-ttu-id="7d037-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="7d037-1609">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="7d037-1610">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="7d037-1610">2.5.29.46</span></span> | <span data-ttu-id="7d037-1611">Предоставляет сведения для получения разностных списков отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-1611">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="7d037-1612">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1612">No</span></span>               |
| <span data-ttu-id="7d037-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="7d037-1613">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="7d037-1614">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="7d037-1614">2.5.29.54</span></span> | <span data-ttu-id="7d037-1615">Поле сертификата ЦС, указывающее, что AnyPolicy нельзя использовать</span><span class="sxs-lookup"><span data-stu-id="7d037-1615">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="7d037-1616">Нет</span><span class="sxs-lookup"><span data-stu-id="7d037-1616">No</span></span>               |

<span data-ttu-id="7d037-1617">Идентификаторы объектов и сопоставления для расширений X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1617">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="7d037-1618">Расширение SubjectAltName анализируется как часть проверки DNS-имени в службе nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="7d037-1618">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1619">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1619">Parameters</span></span>

- <span data-ttu-id="7d037-1620">**certificate** — указатель на проверяемый сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-1620">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="7d037-1621">**extension** — возвращает структуру, содержащую указатель и длину данных расширения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1621">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="7d037-1622">**extension_id** — сопоставление целых чисел идентификатора объекта из таблицы выше.</span><span class="sxs-lookup"><span data-stu-id="7d037-1622">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1623">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1623">Return Values</span></span>

- <span data-ttu-id="7d037-1624">**NX_SUCCESS** (0x00) — указанный идентификатор объекта расширения найден, а данные возвращены.</span><span class="sxs-lookup"><span data-stu-id="7d037-1624">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="7d037-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1625">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="7d037-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1626">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1627">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение.</span><span class="sxs-lookup"><span data-stu-id="7d037-1628">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="7d037-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — указанный идентификатор объекта расширения не найден в указанном сертификате.</span><span class="sxs-lookup"><span data-stu-id="7d037-1629">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="7d037-1630">**NX_PTR_ERROR** (0x07) — недопустимый сертификат или указатель расширения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1630">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1631">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1631">Allowed From</span></span>

<span data-ttu-id="7d037-1632">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1632">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1633">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1633">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1634">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1634">See Also</span></span>

- <span data-ttu-id="7d037-1635">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1635">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7d037-1636">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1636">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="7d037-1637">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1637">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="7d037-1638">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1638">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7d037-1639">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1639">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="7d037-1640">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1640">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="7d037-1641">Поиск и анализ расширения использования ключа X.509 в сертификате X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1641">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="7d037-1642">Прототип</span><span class="sxs-lookup"><span data-stu-id="7d037-1642">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="7d037-1643">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1643">Description</span></span>

<span data-ttu-id="7d037-1644">Эта служба должна вызываться из обратного вызова проверки сертификата (см. *nx_secure_tls_session_certificate_callback_set)* .</span><span class="sxs-lookup"><span data-stu-id="7d037-1644">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="7d037-1645">Она будет искать расширение использования ключа и, если оно найдено, возвратит битовое поле использования ключа в параметре bitfield.</span><span class="sxs-lookup"><span data-stu-id="7d037-1645">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="7d037-1646">Биты, как определено спецификацией X.509 (RFC 5280), приведены в таблице ниже.</span><span class="sxs-lookup"><span data-stu-id="7d037-1646">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="7d037-1647">Побитовое И с соответствующей битовой маской (и проверкой на наличие ненулевого значения) предоставит значение каждому биту.</span><span class="sxs-lookup"><span data-stu-id="7d037-1647">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="7d037-1648">Обратите внимание, что кодировка DER битового поля устраняет лишние нули, поэтому фактическое положение битов в необработанных данных сертификата, скорее всего, будет отличаться от их положений в декодированном битовом поле.</span><span class="sxs-lookup"><span data-stu-id="7d037-1648">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="7d037-1649">Указанные битовые маски предназначены только для использования в декодированных битовых полях, которые возвращает *nx_secure_x509_key_usage_extension_parse*, а не с необработанными данными сертификата в кодировке DER.</span><span class="sxs-lookup"><span data-stu-id="7d037-1649">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="7d037-1650">В обратном вызове проверки сертификата код возврата ошибки NX_SECURE_X509_KEY_USAGE_ERROR зарезервирован для использования приложением.</span><span class="sxs-lookup"><span data-stu-id="7d037-1650">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="7d037-1651">Если при проверке использования ключа возникает ошибка, обратный вызов может возвратить это значение для указания причины сбоя.</span><span class="sxs-lookup"><span data-stu-id="7d037-1651">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="7d037-1652">Идентификатор NetX Secure</span><span class="sxs-lookup"><span data-stu-id="7d037-1652">NetX Secure Identifier</span></span>                            | <span data-ttu-id="7d037-1653">Позиции</span><span class="sxs-lookup"><span data-stu-id="7d037-1653">Bit position</span></span> | <span data-ttu-id="7d037-1654">Описание</span><span class="sxs-lookup"><span data-stu-id="7d037-1654">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="7d037-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="7d037-1655">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="7d037-1656">0</span><span class="sxs-lookup"><span data-stu-id="7d037-1656">0</span></span>            | <span data-ttu-id="7d037-1657">Сертификат можно использовать для цифровых подписей</span><span class="sxs-lookup"><span data-stu-id="7d037-1657">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="7d037-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="7d037-1658">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="7d037-1659">1</span><span class="sxs-lookup"><span data-stu-id="7d037-1659">1</span></span>            | <span data-ttu-id="7d037-1660">Сертификат можно использовать для проверки цифровых подписей, кроме подписей для сертификатов и списков отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-1660">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="7d037-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="7d037-1661">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="7d037-1662">2</span><span class="sxs-lookup"><span data-stu-id="7d037-1662">2</span></span>            | <span data-ttu-id="7d037-1663">Сертификат можно использовать для шифрования симметричных ключей (транспорт ключей)</span><span class="sxs-lookup"><span data-stu-id="7d037-1663">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="7d037-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="7d037-1664">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="7d037-1665">3</span><span class="sxs-lookup"><span data-stu-id="7d037-1665">3</span></span>            | <span data-ttu-id="7d037-1666">Сертификат можно использовать для прямого шифрования необработанных данных пользователя (редко)</span><span class="sxs-lookup"><span data-stu-id="7d037-1666">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="7d037-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="7d037-1667">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="7d037-1668">4</span><span class="sxs-lookup"><span data-stu-id="7d037-1668">4</span></span>            | <span data-ttu-id="7d037-1669">Сертификат можно использовать для согласования ключей (как в случае Диффи-Хелмана)</span><span class="sxs-lookup"><span data-stu-id="7d037-1669">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="7d037-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="7d037-1670">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="7d037-1671">5</span><span class="sxs-lookup"><span data-stu-id="7d037-1671">5</span></span>            | <span data-ttu-id="7d037-1672">Сертификат можно использовать для подписи и проверки других сертификатов (сертификат относится к ЦС или ICA).</span><span class="sxs-lookup"><span data-stu-id="7d037-1672">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="7d037-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="7d037-1673">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="7d037-1674">6</span><span class="sxs-lookup"><span data-stu-id="7d037-1674">6</span></span>            | <span data-ttu-id="7d037-1675">Открытый ключ сертификата используется для проверки подписей в списках отзыва сертификатов</span><span class="sxs-lookup"><span data-stu-id="7d037-1675">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="7d037-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="7d037-1676">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="7d037-1677">7</span><span class="sxs-lookup"><span data-stu-id="7d037-1677">7</span></span>            | <span data-ttu-id="7d037-1678">Используется с битом согласования ключей (бит 4). После установки ключ сертификата можно использовать только для шифрования во время согласования ключей.</span><span class="sxs-lookup"><span data-stu-id="7d037-1678">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="7d037-1679">Значение не определено, если бит согласования ключей не установлен.</span><span class="sxs-lookup"><span data-stu-id="7d037-1679">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="7d037-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="7d037-1680">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="7d037-1681">8</span><span class="sxs-lookup"><span data-stu-id="7d037-1681">8</span></span>            | <span data-ttu-id="7d037-1682">Используется с битом согласования ключей (бит 4). После установки ключ сертификата можно использовать только для расшифровки во время согласования ключей.</span><span class="sxs-lookup"><span data-stu-id="7d037-1682">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="7d037-1683">Значение не определено, если бит согласования ключей не установлен.</span><span class="sxs-lookup"><span data-stu-id="7d037-1683">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="7d037-1684">Битовые маски и значения для расширения использования ключа X.509</span><span class="sxs-lookup"><span data-stu-id="7d037-1684">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="7d037-1685">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d037-1685">Parameters</span></span>

- <span data-ttu-id="7d037-1686">**certificate** — указатель на проверяемый сертификат.</span><span class="sxs-lookup"><span data-stu-id="7d037-1686">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="7d037-1687">**bitfield** — возврат всего битового поля из расширения.</span><span class="sxs-lookup"><span data-stu-id="7d037-1687">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="7d037-1688">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="7d037-1688">Return Values</span></span>

- <span data-ttu-id="7d037-1689">**NX_SUCCESS** (0x00) — найдено расширение использования ключа и возвращено битовое поле.</span><span class="sxs-lookup"><span data-stu-id="7d037-1689">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="7d037-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) — обнаружен многобайтовый тег ASN.1 (неподдерживаемый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1690">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="7d037-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) — обнаружено недопустимое поле ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1691">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) — обнаружен недопустимый класс тегов ASN.1 (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1692">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) — обнаружено недопустимое расширение (недопустимый сертификат).</span><span class="sxs-lookup"><span data-stu-id="7d037-1693">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="7d037-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) — расширение использования ключа не найдено в указанном сертификате.</span><span class="sxs-lookup"><span data-stu-id="7d037-1694">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="7d037-1695">**NX_PTR_ERROR** (0x07) — недопустимый сертификат или указатель битового поля.</span><span class="sxs-lookup"><span data-stu-id="7d037-1695">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="7d037-1696">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="7d037-1696">Allowed From</span></span>

<span data-ttu-id="7d037-1697">Потоки</span><span class="sxs-lookup"><span data-stu-id="7d037-1697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="7d037-1698">Пример</span><span class="sxs-lookup"><span data-stu-id="7d037-1698">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="7d037-1699">См. также:</span><span class="sxs-lookup"><span data-stu-id="7d037-1699">See Also</span></span>

- <span data-ttu-id="7d037-1700">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="7d037-1700">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="7d037-1701">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="7d037-1701">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="7d037-1702">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1702">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="7d037-1703">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="7d037-1703">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="7d037-1704">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="7d037-1704">nx_secure_x509_extension_find</span></span>
