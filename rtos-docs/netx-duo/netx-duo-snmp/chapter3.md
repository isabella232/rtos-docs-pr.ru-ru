---
title: Глава 3. Описание служб агентов SNMP для NetX Duo в ОСРВ Azure
description: Эта часть содержит описание всех служб агентов SNMP для NetX Duo, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814564"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="05d20-103">Глава 3. Описание служб агентов SNMP для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="05d20-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="05d20-104">Эта часть содержит описание всех служб агентов SNMP для NetX Duo в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="05d20-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="05d20-105">В разделе "Возвращаемые значения" в описаниях API ниже значения, выделенные **полужирным шрифтом**, не затрагиваются определением параметра **NX_DISABLE_ERROR_CHECKING**, который используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="05d20-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="05d20-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="05d20-107">*Указание ключа проверки подлинности (только SNMP версии 3) для сообщений ловушки*</span><span class="sxs-lookup"><span data-stu-id="05d20-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="05d20-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="05d20-109">*Указание ключа проверки подлинности (только SNMP версии 3) для сообщений-ответов*</span><span class="sxs-lookup"><span data-stu-id="05d20-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="05d20-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="05d20-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="05d20-111">*Получение имени сообщества*</span><span class="sxs-lookup"><span data-stu-id="05d20-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="05d20-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="05d20-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="05d20-113">*Задание обработчика контекста (только для SNMP версии 3)*</span><span class="sxs-lookup"><span data-stu-id="05d20-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="05d20-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="05d20-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="05d20-115">*Задание имени контекста (только для SNMP версии 3)*</span><span class="sxs-lookup"><span data-stu-id="05d20-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="05d20-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="05d20-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="05d20-117">*Создание агента SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="05d20-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="05d20-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="05d20-119">*Получение версии SNMP полученного пакета*</span><span class="sxs-lookup"><span data-stu-id="05d20-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="05d20-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="05d20-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="05d20-121">*Указание типа последнего запроса SNMP: GET или SET*</span><span class="sxs-lookup"><span data-stu-id="05d20-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="05d20-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="05d20-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="05d20-123">*Определение того, соответствует ли строка частной строке агента*</span><span class="sxs-lookup"><span data-stu-id="05d20-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="05d20-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="05d20-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="05d20-125">*Определение того, соответствует ли строка общедоступной строке агента*</span><span class="sxs-lookup"><span data-stu-id="05d20-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="05d20-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="05d20-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="05d20-127">*Настройка сетевого интерфейса для обмена сообщениями SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="05d20-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="05d20-129">*Задание частной строки доступа агента SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="05d20-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="05d20-131">*Задание общедоступной строки доступа агента SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="05d20-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="05d20-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="05d20-133">*Задание статуса агента SNMP для всех версий SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="05d20-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="05d20-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="05d20-135">*Удаление агента SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="05d20-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="05d20-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="05d20-137">*Создание ключа md5 (только SNMP версии 3)*</span><span class="sxs-lookup"><span data-stu-id="05d20-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="05d20-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="05d20-139">*Создание ключа md5 (только SNMP версии 3)*</span><span class="sxs-lookup"><span data-stu-id="05d20-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="05d20-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="05d20-141">*Указание ключа шифрования (только SNMP версии 3) для сообщений ловушки*</span><span class="sxs-lookup"><span data-stu-id="05d20-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="05d20-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="05d20-143">*Указание ключа шифрования (только SNMP версии 3) для сообщений-ответов*</span><span class="sxs-lookup"><span data-stu-id="05d20-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="05d20-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="05d20-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="05d20-145">*Создание ключа sha (только SNMP версии 3)*</span><span class="sxs-lookup"><span data-stu-id="05d20-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="05d20-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="05d20-147">*Создание ключа sha (только SNMP версии 3)*</span><span class="sxs-lookup"><span data-stu-id="05d20-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="05d20-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="05d20-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="05d20-149">*Запуск агента SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="05d20-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="05d20-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="05d20-151">*Остановка агента SNMP*</span><span class="sxs-lookup"><span data-stu-id="05d20-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="05d20-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="05d20-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="05d20-153">*Отправка SNMP-ловушки версии 1 (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="05d20-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="05d20-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="05d20-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="05d20-155">*Отправка SNMP-ловушки версии 2 (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="05d20-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="05d20-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="05d20-157">*Отправка SNMP-ловушки версии 2 (только IPv4) с указанием OID*</span><span class="sxs-lookup"><span data-stu-id="05d20-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="05d20-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="05d20-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="05d20-159">*Отправка SNMP-ловушки версии 3 (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="05d20-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="05d20-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="05d20-161">*Отправка SNMP-ловушки версии 2 (только IPv4) с указанием OID*</span><span class="sxs-lookup"><span data-stu-id="05d20-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="05d20-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="05d20-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="05d20-163">*Отправка SNMP-ловушки версии 1 (IPv4 и IPv6)*</span><span class="sxs-lookup"><span data-stu-id="05d20-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="05d20-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="05d20-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="05d20-165">*Отправка SNMP-ловушки версии 2 (IPv4 и IPv6)*</span><span class="sxs-lookup"><span data-stu-id="05d20-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="05d20-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="05d20-167">*Отправка SNMP-ловушки версии 2 (IPv4 или IPv6) с указанием OID*</span><span class="sxs-lookup"><span data-stu-id="05d20-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="05d20-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="05d20-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="05d20-169">*Отправка SNMP-ловушки версии 3 (IPv4 и IPv6)*</span><span class="sxs-lookup"><span data-stu-id="05d20-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="05d20-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="05d20-171">*Отправка SNMP-ловушки версии 2 (IPv4 или IPv6) с указанием OID*</span><span class="sxs-lookup"><span data-stu-id="05d20-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="05d20-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="05d20-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="05d20-173">*Задание количества перезагрузок*</span><span class="sxs-lookup"><span data-stu-id="05d20-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="05d20-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="05d20-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="05d20-175">*Сравнение двух объектов*</span><span class="sxs-lookup"><span data-stu-id="05d20-175">*Compare two objects*</span></span>
- [<span data-ttu-id="05d20-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="05d20-177">*Сравнение двух объектов*</span><span class="sxs-lookup"><span data-stu-id="05d20-177">*Compare two objects*</span></span>
- [<span data-ttu-id="05d20-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="05d20-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="05d20-179">*Копирование объекта*</span><span class="sxs-lookup"><span data-stu-id="05d20-179">*Copy an object*</span></span>
- [<span data-ttu-id="05d20-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="05d20-181">*Копирование объекта*</span><span class="sxs-lookup"><span data-stu-id="05d20-181">*Copy an object*</span></span>
- [<span data-ttu-id="05d20-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="05d20-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="05d20-183">*Получение объекта счетчика*</span><span class="sxs-lookup"><span data-stu-id="05d20-183">*Get counter object*</span></span>
- [<span data-ttu-id="05d20-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="05d20-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="05d20-185">*Задание объекта счетчика*</span><span class="sxs-lookup"><span data-stu-id="05d20-185">*Set counter object*</span></span>
- [<span data-ttu-id="05d20-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="05d20-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="05d20-187">*Получение 64-разрядного объекта счетчика*</span><span class="sxs-lookup"><span data-stu-id="05d20-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="05d20-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="05d20-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="05d20-189">*Настройка 64-разрядного объекта счетчика*</span><span class="sxs-lookup"><span data-stu-id="05d20-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="05d20-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="05d20-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="05d20-191">*Задание значения окончания MIB*</span><span class="sxs-lookup"><span data-stu-id="05d20-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="05d20-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="05d20-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="05d20-193">*Получение объекта датчика*</span><span class="sxs-lookup"><span data-stu-id="05d20-193">*Get gauge object*</span></span>
- [<span data-ttu-id="05d20-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="05d20-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="05d20-195">*Задание объекта датчика*</span><span class="sxs-lookup"><span data-stu-id="05d20-195">*Set gauge object*</span></span>
- [<span data-ttu-id="05d20-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="05d20-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="05d20-197">*Получение идентификатора объекта*</span><span class="sxs-lookup"><span data-stu-id="05d20-197">*Get object id*</span></span>
- [<span data-ttu-id="05d20-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="05d20-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="05d20-199">*Задание идентификатора объекта*</span><span class="sxs-lookup"><span data-stu-id="05d20-199">*Set object id*</span></span>
- [<span data-ttu-id="05d20-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="05d20-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="05d20-201">*Получение объекта целого числа*</span><span class="sxs-lookup"><span data-stu-id="05d20-201">*Get integer object*</span></span>
- [<span data-ttu-id="05d20-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="05d20-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="05d20-203">*Задание объекта целого числа*</span><span class="sxs-lookup"><span data-stu-id="05d20-203">*Set integer object*</span></span>
- [<span data-ttu-id="05d20-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="05d20-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="05d20-205">*Получение объекта IP-адреса (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="05d20-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="05d20-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="05d20-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="05d20-207">*Задание объекта IP адреса (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="05d20-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="05d20-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="05d20-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="05d20-209">*Получение объекта IP-адреса (только IPv6)*</span><span class="sxs-lookup"><span data-stu-id="05d20-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="05d20-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="05d20-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="05d20-211">*Задание объекта IP-адреса (только IPv6)*</span><span class="sxs-lookup"><span data-stu-id="05d20-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="05d20-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="05d20-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="05d20-213">*Задание значения "экземпляр отсутствует"*</span><span class="sxs-lookup"><span data-stu-id="05d20-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="05d20-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="05d20-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="05d20-215">*Задание значения "не найдено"*</span><span class="sxs-lookup"><span data-stu-id="05d20-215">*Set not-found value*</span></span>
- [<span data-ttu-id="05d20-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="05d20-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="05d20-217">*Получение объекта октетной строки*</span><span class="sxs-lookup"><span data-stu-id="05d20-217">*Get octet string object*</span></span>
- [<span data-ttu-id="05d20-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="05d20-219">*Задание объекта октетной строки*</span><span class="sxs-lookup"><span data-stu-id="05d20-219">*Set octet string object*</span></span>
- [<span data-ttu-id="05d20-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="05d20-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="05d20-221">*Получение объекта строки ASCII*</span><span class="sxs-lookup"><span data-stu-id="05d20-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="05d20-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="05d20-223">*Задание объекта строки ASCII*</span><span class="sxs-lookup"><span data-stu-id="05d20-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="05d20-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="05d20-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="05d20-225">*Получение объекта timetics*</span><span class="sxs-lookup"><span data-stu-id="05d20-225">*Get timetics object*</span></span>
- [<span data-ttu-id="05d20-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="05d20-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="05d20-227">*Задание объекта timetics*</span><span class="sxs-lookup"><span data-stu-id="05d20-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="05d20-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="05d20-229">Указание ключа проверки подлинности для сообщений ловушки</span><span class="sxs-lookup"><span data-stu-id="05d20-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-230">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="05d20-231">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-231">Description</span></span>

<span data-ttu-id="05d20-232">Эта служба позволяет указать ключ, используемый для настройки параметров проверки подлинности в заголовке безопасности SNMP версии 3 в сообщениях ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="05d20-233">Если задать для ключа значение NX_NULL, проверка подлинности будет отключена.</span><span class="sxs-lookup"><span data-stu-id="05d20-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="05d20-234">Ключ нужно создать заранее.</span><span class="sxs-lookup"><span data-stu-id="05d20-234">The key must be previously created.</span></span> <span data-ttu-id="05d20-235">См. nx_snmp_agent_md5_key_create или nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="05d20-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-236">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-236">Input Parameters</span></span>

- <span data-ttu-id="05d20-237">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-238">**key** — указатель на ранее созданный ключ MD5 или SHA.</span><span class="sxs-lookup"><span data-stu-id="05d20-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-239">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-239">Return Values</span></span>

- <span data-ttu-id="05d20-240">**NX_SUCCESS** (0x00) — ключ проверки подлинности успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="05d20-241">**NX_NOT_ENABLED** (0x14) — защита SNMP отключена.</span><span class="sxs-lookup"><span data-stu-id="05d20-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="05d20-242">**NX_PTR_ERROR** (0x07) — недопустимый указатель агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-243">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-243">Allowed From</span></span>

<span data-ttu-id="05d20-244">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-245">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="05d20-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="05d20-247">Указание ключа проверки подлинности для сообщений-ответов</span><span class="sxs-lookup"><span data-stu-id="05d20-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-248">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="05d20-249">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-249">Description</span></span>

<span data-ttu-id="05d20-250">Эта служба позволяет указать ключ, используемый для параметров проверки подлинности, в параметре безопасности SNMP версии 3 для всех запросов, которые будут выполняться после задания этого ключа.</span><span class="sxs-lookup"><span data-stu-id="05d20-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="05d20-251">Если задать для ключа значение NX_NULL, проверка подлинности будет отключена.</span><span class="sxs-lookup"><span data-stu-id="05d20-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="05d20-252">Ключ нужно создать заранее.</span><span class="sxs-lookup"><span data-stu-id="05d20-252">The key must be previously created.</span></span> <span data-ttu-id="05d20-253">См. nx_snmp_agent_md5_key_create или nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="05d20-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-254">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-254">Input Parameters</span></span>

- <span data-ttu-id="05d20-255">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-256">**key** — указатель на ранее созданный ключ MD5 или SHA.</span><span class="sxs-lookup"><span data-stu-id="05d20-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-257">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-257">Return Values</span></span>

- <span data-ttu-id="05d20-258">**NX_SUCCESS** (0x00) — ключ SNMP успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="05d20-259">**NX_NOT_ENABLED** (0x14) — защита SNMP отключена.</span><span class="sxs-lookup"><span data-stu-id="05d20-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="05d20-260">**NX_PTR_ERROR** (0x07) — недопустимый указатель агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-261">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-261">Allowed From</span></span>

<span data-ttu-id="05d20-262">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-263">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="05d20-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="05d20-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="05d20-265">Получение имени сообщества</span><span class="sxs-lookup"><span data-stu-id="05d20-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-266">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="05d20-267">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-267">Description</span></span>

<span data-ttu-id="05d20-268">Эта служба позволяет получить имя сообщества из самого последнего запроса SNMP, полученного агентом SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-269">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-269">Input Parameters</span></span>

- <span data-ttu-id="05d20-270">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-271">**community_string_ptr** — указатель на указатель строки для возврата строки доступа агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-272">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-272">Return Values</span></span>

- <span data-ttu-id="05d20-273">**NX_SUCCESS** (0x00) — сведения о сообществе SNMP успешно получено.</span><span class="sxs-lookup"><span data-stu-id="05d20-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="05d20-274">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-275">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-275">Allowed From</span></span>

<span data-ttu-id="05d20-276">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-277">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="05d20-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="05d20-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="05d20-279">Указание типа последнего запроса SNMP: GET или SET</span><span class="sxs-lookup"><span data-stu-id="05d20-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-280">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="05d20-281">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-281">Description</span></span>

<span data-ttu-id="05d20-282">Эта служба указывает на тип самого последнего запроса из диспетчера SNMP: GET (GET, GETNEXT или GETBULK) или SET.</span><span class="sxs-lookup"><span data-stu-id="05d20-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="05d20-283">Ее следует использовать с ответным вызовом username, в котором приложение SNMP версии 1 или SNMP версии 2 будет сравнивать полученную строку доступа с общедоступной строкой агента SNMP, если типом запроса является GET, или с частной строкой агента SNMP, если — SET.</span><span class="sxs-lookup"><span data-stu-id="05d20-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-284">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-284">Input Parameters</span></span>

- <span data-ttu-id="05d20-285">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-286">**is_get_type** — указатель на состояние типа запроса:</span><span class="sxs-lookup"><span data-stu-id="05d20-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="05d20-287">NX_TRUE, если типом является GET;</span><span class="sxs-lookup"><span data-stu-id="05d20-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="05d20-288">NX_FALSE, если типом является SET.</span><span class="sxs-lookup"><span data-stu-id="05d20-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-289">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-289">Return Values</span></span>

- <span data-ttu-id="05d20-290">**NX_SUCCESS** (0x00) — тип возвращаемого значения получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="05d20-291">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-292">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-292">Allowed From</span></span>

<span data-ttu-id="05d20-293">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-294">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="05d20-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="05d20-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="05d20-296">Задание обработчика контекста (только для SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-297">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="05d20-298">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-298">Description</span></span>

<span data-ttu-id="05d20-299">Эта служба задает обработчик контекста для агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="05d20-300">Применима только для обработки SNMP версии 3.</span><span class="sxs-lookup"><span data-stu-id="05d20-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="05d20-301">Если приложение использует проверку подлинности и шифрование, эту службу нужно вызывать перед созданием ключей безопасности, так как идентификатор обработчика контекста используется в процессе создания ключа.</span><span class="sxs-lookup"><span data-stu-id="05d20-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="05d20-302">В противном случае протокол SNMP NetX Duo предоставит в начале *nxd_snmp.c:* стандартный идентификатор обработчика контекста</span><span class="sxs-lookup"><span data-stu-id="05d20-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="05d20-303">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-303">Input Parameters</span></span>

- <span data-ttu-id="05d20-304">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-305">**context_engine** — указатель на строку обработчика контекста.</span><span class="sxs-lookup"><span data-stu-id="05d20-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="05d20-306">**context_engine_size** — размер строки обработчика контекста.</span><span class="sxs-lookup"><span data-stu-id="05d20-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="05d20-307">Обратите внимание, что максимальное число байтов в обработчике контекста определяет служба NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="05d20-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-308">Return Values</span></span>

- <span data-ttu-id="05d20-309">**NX_SUCCESS** (0x00) — обработчик контекста SNMP успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="05d20-310">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 3 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="05d20-311">**NX_SNMP_ERROR** (0x100) — ошибка при указании размера обработчика контекста.</span><span class="sxs-lookup"><span data-stu-id="05d20-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="05d20-312">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-313">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-313">Allowed From</span></span>

<span data-ttu-id="05d20-314">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-315">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="05d20-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="05d20-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="05d20-317">Задание имени контекста (только для SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-318">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="05d20-319">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-319">Description</span></span>

<span data-ttu-id="05d20-320">Эта служба задает имя контекста для агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="05d20-321">Применима только для обработки SNMP версии 3.</span><span class="sxs-lookup"><span data-stu-id="05d20-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="05d20-322">Если не вызвать эту службу, агент SNMP NetX Duo оставит поле имени контекста пустым.</span><span class="sxs-lookup"><span data-stu-id="05d20-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-323">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-323">Input Parameters</span></span>

- <span data-ttu-id="05d20-324">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-325">**context_name** — указатель на строку имени контекста.</span><span class="sxs-lookup"><span data-stu-id="05d20-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="05d20-326">**context_name_size** — размер строки имени контекста.</span><span class="sxs-lookup"><span data-stu-id="05d20-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="05d20-327">Обратите внимание, что максимальное число байтов в имени контекста определяет служба NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="05d20-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-328">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-328">Return Values</span></span>

- <span data-ttu-id="05d20-329">**NX_SUCCESS** (0x00) — имя контекста SNMP успешно задано.</span><span class="sxs-lookup"><span data-stu-id="05d20-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="05d20-330">**NX_SNMP_ERROR** (0x100) — ошибка при указании размера имени контекста.</span><span class="sxs-lookup"><span data-stu-id="05d20-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="05d20-331">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-332">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-332">Allowed From</span></span>

<span data-ttu-id="05d20-333">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-334">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="05d20-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="05d20-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="05d20-336">Создание агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-337">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="05d20-338">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-338">Description</span></span>

<span data-ttu-id="05d20-339">Эта служба создает агент SNMP в указанном экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="05d20-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-340">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-340">Input Parameters</span></span>

- <span data-ttu-id="05d20-341">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-342">**snmp_agent_name** — указатель на строку имени агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="05d20-343">**ip_ptr** — указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="05d20-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="05d20-344">**stack_ptr** — указатель на указатель стека потока агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="05d20-345">**stack_size** — размер стека в байтах.</span><span class="sxs-lookup"><span data-stu-id="05d20-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="05d20-346">**pool_ptr** — указатель на пул пакетов по умолчанию для этого агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="05d20-347">**snmp_agent_username_process** — указатель функции на подпрограмму обработки имени пользователя приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="05d20-348">**snmp_agent_get_process** — указатель функции на подпрограмму обработки запроса GET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="05d20-349">**snmp_agent_getnext_process** — указатель функции на подпрограмму обработки запроса GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="05d20-350">**snmp_agent_set_process** — указатель функции на подпрограмму обработки запроса SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-351">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-351">Return Values</span></span>

- <span data-ttu-id="05d20-352">**NX_SUCCESS** (0x00) — агент SNMP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="05d20-353">**NX_SNMP_ERROR** (0x100) — ошибка при создании агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="05d20-354">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-355">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-355">Allowed From</span></span>

<span data-ttu-id="05d20-356">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-357">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="05d20-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="05d20-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="05d20-359">Получение версии пакета SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-360">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="05d20-361">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-361">Description</span></span>

<span data-ttu-id="05d20-362">Эта служба позволяет получить версию SNMP, проанализированную из последнего полученного пакета SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-363">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-363">Input Parameters</span></span>

- <span data-ttu-id="05d20-364">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-365">**version** — указатель на версию SNMP, проанализированную из полученного пакета SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-366">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-366">Return Values</span></span>

- <span data-ttu-id="05d20-367">**NX_SUCCESS** (0x00) — сведения о версии SNMP успешно получены.</span><span class="sxs-lookup"><span data-stu-id="05d20-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="05d20-368">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="05d20-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-369">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-369">Allowed From</span></span>

<span data-ttu-id="05d20-370">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-371">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="05d20-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="05d20-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="05d20-373">Проверка того, соответствует ли частная строка частной строке агента</span><span class="sxs-lookup"><span data-stu-id="05d20-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-374">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="05d20-375">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-375">Description</span></span>

<span data-ttu-id="05d20-376">Эта служба сравнивает входную строку доступа, оканчивающуюся нулевым символом, с частной строкой агента SNMP и указывает, совпадают ли они.</span><span class="sxs-lookup"><span data-stu-id="05d20-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-377">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-377">Input Parameters</span></span>

- <span data-ttu-id="05d20-378">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-379">**community_string** — указатель на строку для сравнения.</span><span class="sxs-lookup"><span data-stu-id="05d20-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="05d20-380">**is_private** — указатель на результат сравнения</span><span class="sxs-lookup"><span data-stu-id="05d20-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="05d20-381">NX_TRUE — строка совпадает;</span><span class="sxs-lookup"><span data-stu-id="05d20-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="05d20-382">NX_FALSE — строка не совпадает.</span><span class="sxs-lookup"><span data-stu-id="05d20-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-383">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-383">Return Values</span></span>

- <span data-ttu-id="05d20-384">**NX_SUCCESS** (0x00) — сравнение успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="05d20-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="05d20-385">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="05d20-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-386">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-386">Allowed From</span></span>

<span data-ttu-id="05d20-387">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-388">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="05d20-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="05d20-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="05d20-390">Проверка того, соответствует ли полученная общедоступная строка общедоступной строке агента</span><span class="sxs-lookup"><span data-stu-id="05d20-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-391">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="05d20-392">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-392">Description</span></span>

<span data-ttu-id="05d20-393">Эта служба сравнивает входную строку доступа, оканчивающуюся нулевым символом, с общедоступной строкой агента SNMP и указывает, совпадают ли они.</span><span class="sxs-lookup"><span data-stu-id="05d20-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-394">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-394">Input Parameters</span></span>

- <span data-ttu-id="05d20-395">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-396">**community_string** — указатель на строку для сравнения.</span><span class="sxs-lookup"><span data-stu-id="05d20-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="05d20-397">**is_public** — указатель на результат сравнения</span><span class="sxs-lookup"><span data-stu-id="05d20-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="05d20-398">NX_TRUE — строка совпадает;</span><span class="sxs-lookup"><span data-stu-id="05d20-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="05d20-399">NX_FALSE — строка не совпадает.</span><span class="sxs-lookup"><span data-stu-id="05d20-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-400">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-400">Return Values</span></span>

- <span data-ttu-id="05d20-401">**NX_SUCCESS** (0x00) — сравнение успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="05d20-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="05d20-402">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="05d20-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-403">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-403">Allowed From</span></span>

<span data-ttu-id="05d20-404">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-405">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="05d20-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="05d20-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="05d20-407">Задание статуса агента SNMP для каждой версии SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-408">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="05d20-409">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-409">Description</span></span>

<span data-ttu-id="05d20-410">Эта служба задает состояние (включено или отключено) для каждой из версий SNMP (версии 1, 2 и 3) в агенте SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="05d20-411">Обратите внимание, что эти параметры времени выполнения будут переопределять настраиваемые параметры, такие как NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 и NX_SNMP_DISABLE_V3.</span><span class="sxs-lookup"><span data-stu-id="05d20-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="05d20-412">По умолчанию агент SNMP поддерживает все три версии.</span><span class="sxs-lookup"><span data-stu-id="05d20-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-413">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-413">Input Parameters</span></span>

- <span data-ttu-id="05d20-414">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-415">**enabled_v1** — задает для состояния включения SNMP версии 1 значение "Вкл." или "Выкл.".</span><span class="sxs-lookup"><span data-stu-id="05d20-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="05d20-416">**enabled_v2** — задает для состояния включения SNMP версии 2 значение "Вкл." или "Выкл.".</span><span class="sxs-lookup"><span data-stu-id="05d20-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="05d20-417">**enabled_v3** — задает для состояния включения SNMP версии 3 значение "Вкл." или "Выкл.".</span><span class="sxs-lookup"><span data-stu-id="05d20-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-418">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-418">Return Values</span></span>

- <span data-ttu-id="05d20-419">**NX_SUCCESS** (0x00) — версия SNMP успешно задана.</span><span class="sxs-lookup"><span data-stu-id="05d20-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="05d20-420">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="05d20-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-421">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-421">Allowed From</span></span>

<span data-ttu-id="05d20-422">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-423">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="05d20-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="05d20-425">Задание частной строки агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-426">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="05d20-427">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-427">Description</span></span>

<span data-ttu-id="05d20-428">Эта служба задает как частную строку доступа агента SNMP входную строку, оканчивающуюся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="05d20-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="05d20-429">Значение по умолчанию — NULL (без набора частных строк), следовательно, любой пакет SNMP, полученный с помощью "частной" строки доступа, не будет приниматься агентом SNMP для доступа на чтение и запись.</span><span class="sxs-lookup"><span data-stu-id="05d20-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="05d20-430">Входная строка должна быть меньше пользовательского настраиваемого параметра NX_SNMP_MAX_USER_NAME-1 или быть равной ему (чтобы обеспечить место для завершающего нулевого символа).</span><span class="sxs-lookup"><span data-stu-id="05d20-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-431">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-431">Input Parameters</span></span>

- <span data-ttu-id="05d20-432">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-433">**community_string** — указатель на частную строку для назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-434">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-434">Return Values</span></span>

- <span data-ttu-id="05d20-435">**NX_SUCCESS** (0x00) — частная строка успешно задана.</span><span class="sxs-lookup"><span data-stu-id="05d20-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="05d20-436">**NX_SNMP_ERROR_TOOBIG** (0x01) — размер строки слишком большой.</span><span class="sxs-lookup"><span data-stu-id="05d20-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="05d20-437">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="05d20-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-438">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-438">Allowed From</span></span>

<span data-ttu-id="05d20-439">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-440">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="05d20-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="05d20-442">Задание общедоступной строки агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-443">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="05d20-444">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-444">Description</span></span>

<span data-ttu-id="05d20-445">Эта служба задает как общедоступную строку доступа агента SNMP входную строку, оканчивающуюся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="05d20-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="05d20-446">Строка доступа должна быть меньше пользовательского настраиваемого параметра NX_SNMP_MAX_USER_NAME-1 или быть равной ему (чтобы обеспечить место для завершающего нулевого символа).</span><span class="sxs-lookup"><span data-stu-id="05d20-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-447">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-447">Input Parameters</span></span>

- <span data-ttu-id="05d20-448">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-449">**community_string** — указатель на общедоступную строку для назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-450">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-450">Return Values</span></span>

- <span data-ttu-id="05d20-451">**NX_SUCCESS** (0x00) — общедоступная строка успешно задана.</span><span class="sxs-lookup"><span data-stu-id="05d20-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="05d20-452">**NX_SNMP_ERROR_TOOBIG** (0x01) — размер строки слишком большой.</span><span class="sxs-lookup"><span data-stu-id="05d20-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="05d20-453">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="05d20-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-454">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-454">Allowed From</span></span>

<span data-ttu-id="05d20-455">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-456">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="05d20-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="05d20-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="05d20-458">Удаление агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-459">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-460">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-460">Description</span></span>

<span data-ttu-id="05d20-461">Эта служба удаляет созданный ранее агент SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-462">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-462">Input Parameters</span></span>

- <span data-ttu-id="05d20-463">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-464">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-464">Return Values</span></span>

- <span data-ttu-id="05d20-465">**NX_SUCCESS** (0x00) — агент SNMP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="05d20-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="05d20-466">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-467">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-467">Allowed From</span></span>

<span data-ttu-id="05d20-468">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-469">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="05d20-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="05d20-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="05d20-471">Задание сетевого интерфейса агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-472">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="05d20-473">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-473">Description</span></span>

<span data-ttu-id="05d20-474">Эта служба задает сетевой интерфейс SNMP для агента SNMP, как указано в индексе входного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="05d20-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="05d20-475">Эта служба будет полезна только для ведущих приложений SNMP в NetX Duo 5.6 или более поздней версии, поддерживающих несколько сетевых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="05d20-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="05d20-476">Для основного интерфейса значение по умолчанию (если его не задаст узел) будет равно нулю.</span><span class="sxs-lookup"><span data-stu-id="05d20-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-477">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-477">Input Parameters</span></span>

- <span data-ttu-id="05d20-478">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-479">**If_index** — индекс, указывающий интерфейс SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-480">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-480">Return Values</span></span>

- <span data-ttu-id="05d20-481">**NX_SUCCESS** (0x00) — интерфейс SNMP успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="05d20-482">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-483">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-483">Allowed From</span></span>

<span data-ttu-id="05d20-484">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-485">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="05d20-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="05d20-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="05d20-487">Создание ключа md5 (только SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-488">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="05d20-489">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-489">Description</span></span>

<span data-ttu-id="05d20-490">Эта служба создает ключ MD5, который можно использовать для проверки подлинности и шифрования.</span><span class="sxs-lookup"><span data-stu-id="05d20-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="05d20-491">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="05d20-491">This service is deprecated.</span></span> <span data-ttu-id="05d20-492">Разработчикам рекомендуется перейти на использование *nx_snmp_agent_md5_key_create_extended()* .</span><span class="sxs-lookup"><span data-stu-id="05d20-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-493">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-493">Input Parameters</span></span>

- <span data-ttu-id="05d20-494">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-495">**password** — указатель на строку пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="05d20-496">**destination_key** — указатель на структуру данных ключа SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-497">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-497">Return Values</span></span>

- <span data-ttu-id="05d20-498">**NX_SUCCESS** (0x00) — ключ успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="05d20-499">**NX_NOT_ENABLED** (0x14) — средства безопасности не включены.</span><span class="sxs-lookup"><span data-stu-id="05d20-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="05d20-500">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-501">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-501">Allowed From</span></span>

<span data-ttu-id="05d20-502">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-503">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="05d20-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="05d20-505">Создание ключа md5 (только SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-506">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="05d20-507">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-507">Description</span></span>

<span data-ttu-id="05d20-508">Эта служба создает ключ MD5, который можно использовать для проверки подлинности и шифрования.</span><span class="sxs-lookup"><span data-stu-id="05d20-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="05d20-509">Эта служба заменяет *nx_snmp_agent_md5_key_create ().*</span><span class="sxs-lookup"><span data-stu-id="05d20-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="05d20-510">При использовании этой версии нужно, чтобы вызывающий объект предоставлял сведения о длине пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-511">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-511">Input Parameters</span></span>

- <span data-ttu-id="05d20-512">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-513">**password** — указатель на строку пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="05d20-514">**password_length** — длина строки пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="05d20-515">**destination_key** — указатель на структуру данных ключа SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-516">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-516">Return Values</span></span>

- <span data-ttu-id="05d20-517">**NX_SUCCESS** (0x00) — ключ успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="05d20-518">**NX_NOT_ENABLED** (0x14) — средства безопасности не включены.</span><span class="sxs-lookup"><span data-stu-id="05d20-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="05d20-519">**NX_SNMP_FAILED** (0x102) — ошибка протокола SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="05d20-520">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-521">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-521">Allowed From</span></span>

<span data-ttu-id="05d20-522">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-523">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="05d20-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="05d20-525">Указание ключа шифрования для сообщений о ловушке</span><span class="sxs-lookup"><span data-stu-id="05d20-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-526">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="05d20-527">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-527">Description</span></span>

<span data-ttu-id="05d20-528">Эта служба указывает, что ранее созданный ключ конфиденциальности следует использовать для шифрования и расшифровки сообщений о ловушках SNMP версии 3.</span><span class="sxs-lookup"><span data-stu-id="05d20-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="05d20-529">*Ключ проверки подлинности нужно создавать заранее. Для обеспечения конфиденциальности (шифрования) SNMP версии 3 требуется проверка подлинности. Дополнительные сведения см. в описании nx_snmp_agent_auth_trap_key_use.*</span><span class="sxs-lookup"><span data-stu-id="05d20-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-530">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-530">Input Parameters</span></span>

- <span data-ttu-id="05d20-531">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-532">**key** — указатель на ранее созданный ключ.</span><span class="sxs-lookup"><span data-stu-id="05d20-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-533">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-533">Return Values</span></span>

- <span data-ttu-id="05d20-534">**NX_SUCCESS** (0x00) — набор ключей конфиденциальности успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="05d20-535">**NX_NOT_ENABLED** (0x14) — средства безопасности не включены.</span><span class="sxs-lookup"><span data-stu-id="05d20-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="05d20-536">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-537">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-537">Allowed From</span></span>

<span data-ttu-id="05d20-538">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-539">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="05d20-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="05d20-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="05d20-541">Указание ключа шифрования для сообщений-ответов</span><span class="sxs-lookup"><span data-stu-id="05d20-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-542">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="05d20-543">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-543">Description</span></span>

<span data-ttu-id="05d20-544">Эта служба указывает, что ранее созданный ключ следует использовать для шифрования и расшифровки сообщений-ответов SNMP версии 3.</span><span class="sxs-lookup"><span data-stu-id="05d20-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="05d20-545">*Ключ проверки подлинности следует указывать заранее. Ключ проверки подлинности нужно создать, чтобы обеспечить шифрование SNMP версии 3. Дополнительные сведения см. в описании nx_snmp_agent_authentiation_key_use.*</span><span class="sxs-lookup"><span data-stu-id="05d20-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-546">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-546">Input Parameters</span></span>

- <span data-ttu-id="05d20-547">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-548">**key** — указатель на ранее созданный ключ.</span><span class="sxs-lookup"><span data-stu-id="05d20-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-549">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-549">Return Values</span></span>

- <span data-ttu-id="05d20-550">**NX_SUCCESS** (0x00) — набор ключей конфиденциальности успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="05d20-551">**NX_NOT_ENABLED** (0x14) — средства безопасности не включены.</span><span class="sxs-lookup"><span data-stu-id="05d20-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="05d20-552">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-553">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-553">Allowed From</span></span>

<span data-ttu-id="05d20-554">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-555">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="05d20-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="05d20-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="05d20-557">Создание ключа SHA (только SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-558">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="05d20-559">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-559">Description</span></span>

<span data-ttu-id="05d20-560">Эта служба создает ключ SHA, который можно использовать для проверки подлинности и шифрования.</span><span class="sxs-lookup"><span data-stu-id="05d20-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="05d20-561">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="05d20-561">This service is deprecated.</span></span> <span data-ttu-id="05d20-562">Разработчикам рекомендуется перейти на использование *nx_snmp_agent_sha_key_create_extended()* .</span><span class="sxs-lookup"><span data-stu-id="05d20-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-563">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-563">Input Parameters</span></span>

- <span data-ttu-id="05d20-564">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-565">**password** — указатель на строку пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="05d20-566">**destination_key** — указатель на структуру данных ключа SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-567">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-567">Return Values</span></span>

- <span data-ttu-id="05d20-568">**NX_SUCCESS** (0x00) — ключ успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="05d20-569">**NX_SNMP_ERROR** (0x100) — ошибка при создании ключа.</span><span class="sxs-lookup"><span data-stu-id="05d20-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="05d20-570">**NX_PTR_ERROR** (0x07) — недопустимый указатель агента или ключа SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-571">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-571">Allowed From</span></span>

<span data-ttu-id="05d20-572">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-573">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="05d20-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="05d20-575">Создание ключа SHA (только SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-576">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="05d20-577">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-577">Description</span></span>

<span data-ttu-id="05d20-578">Эта служба создает ключ SHA, который можно использовать для проверки подлинности и шифрования.</span><span class="sxs-lookup"><span data-stu-id="05d20-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="05d20-579">Эта служба заменяет *nx_snmp_agent_sha_key_create ().*</span><span class="sxs-lookup"><span data-stu-id="05d20-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="05d20-580">При использовании этой версии нужно, чтобы вызывающий объект предоставлял сведения о длине пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-581">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-581">Input Parameters</span></span>

- <span data-ttu-id="05d20-582">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-583">**password** — указатель на строку пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="05d20-584">**password_length** — длина строки пароля.</span><span class="sxs-lookup"><span data-stu-id="05d20-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="05d20-585">**destination_key** — указатель на структуру данных ключа SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-586">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-586">Return Values</span></span>

- <span data-ttu-id="05d20-587">**NX_SUCCESS** (0x00) — ключ успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="05d20-588">**NX_SNMP_ERROR** (0x100) — ошибка при создании ключа.</span><span class="sxs-lookup"><span data-stu-id="05d20-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="05d20-589">**NX_SNMP_FAILED** (0x102) — ключ не удалось создать.</span><span class="sxs-lookup"><span data-stu-id="05d20-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="05d20-590">**NX_PTR_ERROR** (0x07) — недопустимый указатель агента или ключа SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-591">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-591">Allowed From</span></span>

<span data-ttu-id="05d20-592">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-593">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="05d20-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="05d20-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="05d20-595">Запуск агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-596">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-597">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-597">Description</span></span>

<span data-ttu-id="05d20-598">Эта служба связывает сокет UDP и порт 161 SNMP и запускает задачу потока агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-599">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-599">Input Parameters</span></span>

- <span data-ttu-id="05d20-600">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-601">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-601">Return Values</span></span>

- <span data-ttu-id="05d20-602">**NX_SUCCESS** (0x00) — успешный запуск агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="05d20-603">**NX_SNMP_ERROR** (0x100) — ошибка при запуске агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="05d20-604">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-605">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-605">Allowed From</span></span>

<span data-ttu-id="05d20-606">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-607">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="05d20-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="05d20-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="05d20-609">Остановка агента SNMP</span><span class="sxs-lookup"><span data-stu-id="05d20-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-610">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-611">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-611">Description</span></span>

<span data-ttu-id="05d20-612">Эта служба останавливает задачу потока агента SNMP и отменяет привязку между сокетом UDP и портом SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-613">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-613">Input Parameters</span></span>

- <span data-ttu-id="05d20-614">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-615">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-615">Return Values</span></span>

- <span data-ttu-id="05d20-616">**NX_SUCCESS** (0x00) — успешная остановка агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="05d20-617">**NX_PTR_ERROR** (0x07) — недопустимый указатель агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-618">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-618">Allowed From</span></span>

<span data-ttu-id="05d20-619">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-620">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="05d20-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="05d20-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="05d20-622">Отправка SNMP-ловушки версии 1 *(только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="05d20-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-623">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="05d20-624">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-624">Description</span></span>

<span data-ttu-id="05d20-625">Эта служба отправляет SNMP-ловушку диспетчеру SNMP по указанному адресу IPv4.</span><span class="sxs-lookup"><span data-stu-id="05d20-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="05d20-626">Предпочтительный метод отправки SNMP-ловушек в NetX Duo — использование службы *nxd_snmp_agent_trap_send*.</span><span class="sxs-lookup"><span data-stu-id="05d20-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="05d20-627">*nx_snmp_agent_trap_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-628">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-628">Input Parameters</span></span>

- <span data-ttu-id="05d20-629">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-630">**ip_address** — адрес IPv4 диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="05d20-631">**enterprise** — строка идентификатора корпоративного объекта (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="05d20-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="05d20-632">**trap_type** — тип запрашиваемой ловушки, например:</span><span class="sxs-lookup"><span data-stu-id="05d20-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="05d20-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="05d20-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="05d20-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="05d20-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="05d20-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="05d20-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="05d20-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="05d20-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="05d20-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="05d20-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="05d20-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="05d20-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="05d20-639">**trap_code** — код ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="05d20-640">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-641">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-642">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-643">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-643">Return Values</span></span>

- <span data-ttu-id="05d20-644">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-645">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-646">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 1 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="05d20-647">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-648">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-648">Allowed From</span></span>

<span data-ttu-id="05d20-649">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-650">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="05d20-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="05d20-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="05d20-652">Отправка SNMP-ловушки версии 1 *(IPv4 и IPv6)*</span><span class="sxs-lookup"><span data-stu-id="05d20-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-653">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-654">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-654">Description</span></span>

<span data-ttu-id="05d20-655">Эта служба отправляет SNMP-ловушку диспетчеру SNMP по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="05d20-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="05d20-656">Эквивалентом отправки SNMP-ловушки в NetX является использование службы *nxd_snmp_agent_trap_send*.</span><span class="sxs-lookup"><span data-stu-id="05d20-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-657">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-657">Input Parameters</span></span>

- <span data-ttu-id="05d20-658">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-659">**ip_address** — адрес IPv4 или IPv6 диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="05d20-660">**enterprise** — строка идентификатора корпоративного объекта (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="05d20-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="05d20-661">**trap_type** — тип запрашиваемой ловушки, например:</span><span class="sxs-lookup"><span data-stu-id="05d20-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="05d20-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="05d20-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="05d20-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="05d20-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="05d20-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="05d20-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="05d20-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="05d20-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="05d20-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="05d20-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="05d20-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="05d20-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="05d20-668">**trap_code** — код ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="05d20-669">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-670">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-671">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-672">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-672">Return Values</span></span>

- <span data-ttu-id="05d20-673">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-674">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-675">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 1 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="05d20-676">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-677">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-677">Allowed From</span></span>

<span data-ttu-id="05d20-678">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-679">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="05d20-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="05d20-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="05d20-681">Отправка SNMP-ловушки версии 2 (только IPv4)</span><span class="sxs-lookup"><span data-stu-id="05d20-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-682">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-683">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-683">Description</span></span>

<span data-ttu-id="05d20-684">Эта служба отправляет SNMP-ловушку версии 2 диспетчеру SNMP по указанному адресу IPv4.</span><span class="sxs-lookup"><span data-stu-id="05d20-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="05d20-685">Предпочтительный метод отправки SNMP-ловушек в NetX Duo — использование службы *nxd_snmp_agent_trapv2_send*.</span><span class="sxs-lookup"><span data-stu-id="05d20-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="05d20-686">*nx_snmp_agent_trapv2_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-687">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-687">Input Parameters</span></span>

- <span data-ttu-id="05d20-688">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-689">**ip_address** — адрес IPv4 диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="05d20-690">**community** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-690">**community** Community name (username).</span></span>
- <span data-ttu-id="05d20-691">**trap_type** —</span><span class="sxs-lookup"><span data-stu-id="05d20-691">**trap_type**</span></span>  
   <span data-ttu-id="05d20-692">Тип запрошенной ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-692">Type of trap requested.</span></span> <span data-ttu-id="05d20-693">Стандартными событиями являются:</span><span class="sxs-lookup"><span data-stu-id="05d20-693">The standard events are:</span></span>  
   - <span data-ttu-id="05d20-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="05d20-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="05d20-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="05d20-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="05d20-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="05d20-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="05d20-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="05d20-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="05d20-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="05d20-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="05d20-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="05d20-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="05d20-700">Для защищаемых данных:</span><span class="sxs-lookup"><span data-stu-id="05d20-700">For proprietary data:</span></span>  
   - <span data-ttu-id="05d20-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="05d20-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="05d20-702">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-703">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-704">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-705">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-705">Return Values</span></span>

- <span data-ttu-id="05d20-706">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-707">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-708">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 2 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="05d20-709">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-710">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-710">Allowed From</span></span>

<span data-ttu-id="05d20-711">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-712">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="05d20-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="05d20-714">Отправка SNMP-ловушки версии 2 с непосредственным указанием OID</span><span class="sxs-lookup"><span data-stu-id="05d20-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-715">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-716">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-716">Description</span></span>

<span data-ttu-id="05d20-717">Эта служба отправляет SNMP-ловушку версии 2 в диспетчер SNMP по указанному IP-адресу (только IPv4) и позволяет вызывающему объекту напрямую указывать OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="05d20-718">Предпочтительный метод отправки SNMP-ловушек с указанием OID в NetX Duo — использование службы *nxd_snmp_agent_trapv2_oid_send*.</span><span class="sxs-lookup"><span data-stu-id="05d20-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="05d20-719">*nx_snmp_agent_trapv2_oid_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-720">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-720">Input Parameters</span></span>

- <span data-ttu-id="05d20-721">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-722">**ip_address** — IP-адрес диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="05d20-723">**community** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-723">**community** Community name (username).</span></span>
- <span data-ttu-id="05d20-724">**oid** — указатель на буфер, содержащий OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="05d20-725">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-726">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-727">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-728">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-728">Return Values</span></span>

- <span data-ttu-id="05d20-729">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-730">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-731">**NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="05d20-732">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="05d20-733">**NX_OPTION_ERROR** (0x0a) — недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-734">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-734">Allowed From</span></span>

<span data-ttu-id="05d20-735">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-736">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="05d20-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="05d20-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="05d20-738">Отправка SNMP-ловушки версии 2 (IPv4 и IPv6)</span><span class="sxs-lookup"><span data-stu-id="05d20-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-739">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-740">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-740">Description</span></span>

<span data-ttu-id="05d20-741">Эта служба отправляет SNMP-ловушку версии 2 диспетчеру SNMP по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="05d20-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-742">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-742">Input Parameters</span></span>

- <span data-ttu-id="05d20-743">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-744">**ip_address** — IP-адрес (IPv4 или IPv6) диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="05d20-745">**community** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-745">**community** Community name (username).</span></span>
- <span data-ttu-id="05d20-746">**trap_type** —</span><span class="sxs-lookup"><span data-stu-id="05d20-746">**trap_type**</span></span>  
   <span data-ttu-id="05d20-747">Тип запрошенной ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-747">Type of trap requested.</span></span> <span data-ttu-id="05d20-748">Стандартными событиями являются:</span><span class="sxs-lookup"><span data-stu-id="05d20-748">The standard events are:</span></span>  
   - <span data-ttu-id="05d20-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="05d20-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="05d20-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="05d20-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="05d20-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="05d20-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="05d20-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="05d20-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="05d20-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="05d20-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="05d20-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="05d20-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="05d20-755">Для защищаемых данных:</span><span class="sxs-lookup"><span data-stu-id="05d20-755">For proprietary data:</span></span>

   - <span data-ttu-id="05d20-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="05d20-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="05d20-757">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-758">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-759">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-760">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-760">Return Values</span></span>

- <span data-ttu-id="05d20-761">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-762">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-763">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 2 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="05d20-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) — неподдерживаемая версия IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="05d20-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="05d20-765">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-766">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-766">Allowed From</span></span>

<span data-ttu-id="05d20-767">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-768">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="05d20-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="05d20-770">Отправка SNMP-ловушки версии 2 с непосредственным указанием OID</span><span class="sxs-lookup"><span data-stu-id="05d20-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-771">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-772">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-772">Description</span></span>

<span data-ttu-id="05d20-773">Эта служба отправляет SNMP-ловушку версии 2 диспетчеру SNMP по указанному IP-адресу (IPv4 или IPv6) и позволяет вызывающему объекту напрямую указывать OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-774">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-774">Input Parameters</span></span>

- <span data-ttu-id="05d20-775">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-776">**ip_address** — IP-адрес диспетчера SNMP (IPv4 или IPv6).</span><span class="sxs-lookup"><span data-stu-id="05d20-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="05d20-777">**community** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-777">**community** Community name (username).</span></span>
- <span data-ttu-id="05d20-778">**oid** — указатель на буфер, содержащий OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="05d20-779">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-780">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-781">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-782">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-782">Return Values</span></span>

- <span data-ttu-id="05d20-783">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-784">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-785">**NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="05d20-786">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="05d20-787">**NX_OPTION_ERROR** (0x0a) — недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-788">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-788">Allowed From</span></span>

<span data-ttu-id="05d20-789">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-790">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="05d20-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="05d20-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="05d20-792">Отправка SNMP-ловушки версии 3 (только IPv4)</span><span class="sxs-lookup"><span data-stu-id="05d20-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-793">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="05d20-794">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-794">Description</span></span>

<span data-ttu-id="05d20-795">Эта служба отправляет SNMP-ловушку версии 3 диспетчеру SNMP по указанному адресу IPv4.</span><span class="sxs-lookup"><span data-stu-id="05d20-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="05d20-796">Предпочтительный метод отправки SNMP-ловушек в NetX Duo — использование службы *nxd_snmp_agent_trapv3_send*.</span><span class="sxs-lookup"><span data-stu-id="05d20-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="05d20-797">*nx_snmp_agent_trapv3_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-798">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-798">Input Parameters</span></span>

- <span data-ttu-id="05d20-799">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-800">**ip_address** — адрес IPv4 диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="05d20-801">**username** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-801">**username** Community name (username).</span></span>
- <span data-ttu-id="05d20-802">**trap_type** —</span><span class="sxs-lookup"><span data-stu-id="05d20-802">**trap_type**</span></span>  
   <span data-ttu-id="05d20-803">тип запрошенной ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-803">Type of trap requested.</span></span> <span data-ttu-id="05d20-804">Стандартными событиями являются:</span><span class="sxs-lookup"><span data-stu-id="05d20-804">The standard events are:</span></span>  
   - <span data-ttu-id="05d20-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="05d20-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="05d20-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="05d20-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="05d20-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="05d20-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="05d20-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="05d20-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="05d20-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="05d20-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="05d20-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="05d20-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="05d20-811">Для защищаемых данных:</span><span class="sxs-lookup"><span data-stu-id="05d20-811">For proprietary data:</span></span>
   - <span data-ttu-id="05d20-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="05d20-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="05d20-813">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-814">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-815">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-816">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-816">Return Values</span></span>

- <span data-ttu-id="05d20-817">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-818">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-819">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 3 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="05d20-820">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-821">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-821">Allowed From</span></span>

<span data-ttu-id="05d20-822">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-823">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="05d20-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="05d20-825">Отправка SNMP-ловушки версии 3 с непосредственным указанием OID</span><span class="sxs-lookup"><span data-stu-id="05d20-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-826">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-827">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-827">Description</span></span>

<span data-ttu-id="05d20-828">Эта служба отправляет SNMP-ловушку версии 3 диспетчеру SNMP по указанному IP-адресу (только IPv4) и позволяет вызывающему объекту напрямую указывать OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="05d20-829">Предпочтительный метод отправки SNMP-ловушек с указанием OID в NetX Duo — использование службы *nxd_snmp_agent_trapv3_oid_send*.</span><span class="sxs-lookup"><span data-stu-id="05d20-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="05d20-830">*nx_snmp_agent_trapv3_oid_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-831">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-831">Input Parameters</span></span>

- <span data-ttu-id="05d20-832">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-833">**ip_address** — IP-адрес диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="05d20-834">**username** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-834">**username** Community name (username).</span></span>
- <span data-ttu-id="05d20-835">**oid** — указатель на буфер, содержащий OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="05d20-836">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-837">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-838">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-839">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-839">Return Values</span></span>

- <span data-ttu-id="05d20-840">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-841">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-842">**NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="05d20-843">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="05d20-844">**NX_OPTION_ERROR** (0x0a) — недопустимый параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-845">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-845">Allowed From</span></span>

<span data-ttu-id="05d20-846">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-847">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="05d20-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="05d20-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="05d20-849">Отправка SNMP-ловушки версии 3 (IPv4 и IPv6)</span><span class="sxs-lookup"><span data-stu-id="05d20-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-850">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-851">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-851">Description</span></span>

<span data-ttu-id="05d20-852">Эта служба отправляет SNMP-ловушку диспетчеру SNMP по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="05d20-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="05d20-853">Эта ловушка, по сути, аналогична SNMP-ловушке версии 2, за исключением того, что в ней формат сообщений ловушки содержится в PDU SNMP версии 3.</span><span class="sxs-lookup"><span data-stu-id="05d20-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-854">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-854">Input Parameters</span></span>

- <span data-ttu-id="05d20-855">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-856">**ip_address** — IP-адрес (IPv4 или IPv6) диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="05d20-857">**username** — имя для доступа (имя пользователя).</span><span class="sxs-lookup"><span data-stu-id="05d20-857">**username** Community name (username).</span></span>
- <span data-ttu-id="05d20-858">**trap_type** —</span><span class="sxs-lookup"><span data-stu-id="05d20-858">**trap_type**</span></span>  
   <span data-ttu-id="05d20-859">тип запрошенной ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-859">Type of trap requested.</span></span> <span data-ttu-id="05d20-860">Стандартными событиями являются:</span><span class="sxs-lookup"><span data-stu-id="05d20-860">The standard events are:</span></span>
   - <span data-ttu-id="05d20-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="05d20-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="05d20-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="05d20-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="05d20-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="05d20-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="05d20-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="05d20-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="05d20-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="05d20-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="05d20-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="05d20-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="05d20-867">Для защищаемых данных:</span><span class="sxs-lookup"><span data-stu-id="05d20-867">For proprietary data:</span></span>
   - <span data-ttu-id="05d20-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)</span><span class="sxs-lookup"><span data-stu-id="05d20-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="05d20-869">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-870">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-871">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-872">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-872">Return Values</span></span>

- <span data-ttu-id="05d20-873">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-874">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-875">**NX_NOT_ENABLED** (0x14) — протокол SNMP версии 3 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="05d20-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) — неподдерживаемая версия IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="05d20-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="05d20-877">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-878">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-878">Allowed From</span></span>

<span data-ttu-id="05d20-879">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-880">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="05d20-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="05d20-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="05d20-882">Отправка SNMP-ловушки версии 3 с непосредственным указанием OID</span><span class="sxs-lookup"><span data-stu-id="05d20-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-883">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="05d20-884">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-884">Description</span></span>

<span data-ttu-id="05d20-885">Эта служба отправляет SNMP-ловушку версии 3 диспетчеру SNMP по указанному IP-адресу (IPv4 или IPv6) и позволяет вызывающему объекту напрямую указывать OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-886">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-886">Input Parameters</span></span>

- <span data-ttu-id="05d20-887">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="05d20-888">**ip_address** — указатель на IP-адрес диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="05d20-889">**username** — имя пользователя (имя для доступа).</span><span class="sxs-lookup"><span data-stu-id="05d20-889">**username** Username (community name).</span></span>
- <span data-ttu-id="05d20-890">**oid** — указатель на буфер, содержащий OID.</span><span class="sxs-lookup"><span data-stu-id="05d20-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="05d20-891">**elapsed_time** — система времени исправна (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="05d20-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="05d20-892">**object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку.</span><span class="sxs-lookup"><span data-stu-id="05d20-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="05d20-893">Список завершается значением NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="05d20-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-894">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-894">Return Values</span></span>

- <span data-ttu-id="05d20-895">**NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="05d20-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="05d20-896">**NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="05d20-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="05d20-897">**NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.</span><span class="sxs-lookup"><span data-stu-id="05d20-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="05d20-898">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-899">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-899">Allowed From</span></span>

<span data-ttu-id="05d20-900">Потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-901">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="05d20-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="05d20-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="05d20-903">Задание количества перезагрузок (если включен протокол SNMP версии 3)</span><span class="sxs-lookup"><span data-stu-id="05d20-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-904">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="05d20-905">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-905">Description</span></span>

<span data-ttu-id="05d20-906">Эта служба задает количество перезагрузок, записанных агентом SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="05d20-907">Эта служба доступна, только если для агента SNMP включен протокол SNMP версии 3, так как счетчик загрузок поддерживается только в протоколе SNMP версии 3.</span><span class="sxs-lookup"><span data-stu-id="05d20-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-908">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-908">Input Parameters</span></span>

- <span data-ttu-id="05d20-909">**agent_ptr** — указатель на блок управления агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="05d20-910">**boots** — значение, которое нужно задать для счетчика загрузок агента SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-911">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-911">Return Values</span></span>

- <span data-ttu-id="05d20-912">**NX_SUCCESS** (0x00) — количество загрузок успешно задано.</span><span class="sxs-lookup"><span data-stu-id="05d20-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="05d20-913">**NX_SNMP_ERROR** (0x100) — ошибка при установке счетчика загрузки.</span><span class="sxs-lookup"><span data-stu-id="05d20-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="05d20-914">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-915">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-915">Allowed From</span></span>

<span data-ttu-id="05d20-916">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-917">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="05d20-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="05d20-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="05d20-919">Сравнение двух объектов</span><span class="sxs-lookup"><span data-stu-id="05d20-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-920">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="05d20-921">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-921">Description</span></span>

<span data-ttu-id="05d20-922">Эта служба сравнивает указанный идентификатор объекта с идентификатором эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="05d20-923">Оба идентификатора объекта указаны в нотации SMI ASCII, например, оба объекта должны начинаться со строки ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="05d20-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="05d20-924">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="05d20-924">This service is deprecated.</span></span> <span data-ttu-id="05d20-925">Разработчикам рекомендуется перейти на использование *nx_snmp_object_compare_extended ().*</span><span class="sxs-lookup"><span data-stu-id="05d20-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-926">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-926">Input Parameters</span></span>

- <span data-ttu-id="05d20-927">**object** — указатель на идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="05d20-928">**reference_object** — указатель на идентификатор эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-929">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-929">Return Values</span></span>

- <span data-ttu-id="05d20-930">**NX_SUCCESS** (0x00) — объект соответствует эталонному объекту.</span><span class="sxs-lookup"><span data-stu-id="05d20-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="05d20-931">**NX_SNMP_NEXT_ENTRY** (0x101) — объект меньше эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="05d20-932">**NX_SNMP_ERROR** (0x100) — объект больше эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="05d20-933">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-934">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-934">Allowed From</span></span>

<span data-ttu-id="05d20-935">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-936">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="05d20-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="05d20-938">Сравнение двух объектов</span><span class="sxs-lookup"><span data-stu-id="05d20-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-939">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="05d20-940">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-940">Description</span></span>

<span data-ttu-id="05d20-941">Эта служба сравнивает указанный идентификатор объекта с идентификатором эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="05d20-942">Оба идентификатора объекта указаны в нотации SMI ASCII, например, оба объекта должны начинаться со строки ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="05d20-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="05d20-943">Эта служба заменяет *nx_snmp_object_compare().*</span><span class="sxs-lookup"><span data-stu-id="05d20-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="05d20-944">В этой версии требуется, чтобы вызывающие объекты предоставляли сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="05d20-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-945">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-945">Input Parameters</span></span>

- <span data-ttu-id="05d20-946">**request_object** — указатель на идентификатор объекта запроса.</span><span class="sxs-lookup"><span data-stu-id="05d20-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="05d20-947">**request_object_length** — длина идентификатора объекта запроса.</span><span class="sxs-lookup"><span data-stu-id="05d20-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="05d20-948">**reference_object** — указатель на идентификатор эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="05d20-949">**reference_object_length** — длина идентификатора объекта запроса.</span><span class="sxs-lookup"><span data-stu-id="05d20-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-950">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-950">Return Values</span></span>

- <span data-ttu-id="05d20-951">**NX_SUCCESS** (0x00) — объект соответствует эталонному объекту.</span><span class="sxs-lookup"><span data-stu-id="05d20-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="05d20-952">**NX_SNMP_NEXT_ENTRY** (0x101) — объект меньше эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="05d20-953">**NX_SNMP_ERROR** (0x100) — объект больше эталонного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="05d20-954">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-955">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-955">Allowed From</span></span>

<span data-ttu-id="05d20-956">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-957">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="05d20-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="05d20-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="05d20-959">Копирование объекта</span><span class="sxs-lookup"><span data-stu-id="05d20-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-960">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="05d20-961">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-961">Description</span></span>

<span data-ttu-id="05d20-962">Эта служба копирует исходный объект в целевой в нотации SIM ASCII.</span><span class="sxs-lookup"><span data-stu-id="05d20-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="05d20-963">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="05d20-963">This service is deprecated.</span></span> <span data-ttu-id="05d20-964">Разработчикам рекомендуется перейти на использование *nx_snmp_object_copy_extended().*</span><span class="sxs-lookup"><span data-stu-id="05d20-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-965">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-965">Input Parameters</span></span>

- <span data-ttu-id="05d20-966">**source_object_name** — указатель на идентификатор исходного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="05d20-967">**destination_object_name** — указатель на идентификатор целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-968">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-968">Return Values</span></span>

- <span data-ttu-id="05d20-969">**Размер** — число байтов, скопированных в имя назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="05d20-970">При наличии ошибки возвращаемым значением будет ноль.</span><span class="sxs-lookup"><span data-stu-id="05d20-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-971">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-971">Allowed From</span></span>

<span data-ttu-id="05d20-972">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-973">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="05d20-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="05d20-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="05d20-975">Копирование объекта</span><span class="sxs-lookup"><span data-stu-id="05d20-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-976">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="05d20-977">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-977">Description</span></span>

<span data-ttu-id="05d20-978">Эта служба копирует исходный объект в целевой в нотации SIM ASCII.</span><span class="sxs-lookup"><span data-stu-id="05d20-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="05d20-979">Эта служба заменяет *nx_snmp_object_copy().*</span><span class="sxs-lookup"><span data-stu-id="05d20-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="05d20-980">В этой версии требуется, чтобы вызывающие объекты предоставляли сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="05d20-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-981">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-981">Input Parameters</span></span>

- <span data-ttu-id="05d20-982">**source_object_name** — указатель на идентификатор исходного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="05d20-983">**source_object_name_length** — длина идентификатора исходного объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="05d20-984">**destination_object_name_buffer** — указатель на буфер целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="05d20-985">**destination_object_name_buffer_size** — размер буфера целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-986">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-986">Return Values</span></span>

- <span data-ttu-id="05d20-987">**Размер** — число байтов, скопированных в имя назначения.</span><span class="sxs-lookup"><span data-stu-id="05d20-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="05d20-988">При наличии ошибки возвращаемым значением будет ноль.</span><span class="sxs-lookup"><span data-stu-id="05d20-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-989">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-989">Allowed From</span></span>

<span data-ttu-id="05d20-990">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-991">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="05d20-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="05d20-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="05d20-993">Получение объекта счетчика</span><span class="sxs-lookup"><span data-stu-id="05d20-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-994">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="05d20-995">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-995">Description</span></span>

<span data-ttu-id="05d20-996">Эта служба получает объект счетчика по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-997">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-998">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-998">Input Parameters</span></span>

- <span data-ttu-id="05d20-999">**source_ptr** — указатель на источник счетчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="05d20-1000">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1001">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1001">Return Values</span></span>

- <span data-ttu-id="05d20-1002">**NX_SUCCESS** (0x00) — объект счетчика успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1003">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1004">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1004">Allowed From</span></span>

<span data-ttu-id="05d20-1005">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1006">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="05d20-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="05d20-1008">Задание объекта счетчика</span><span class="sxs-lookup"><span data-stu-id="05d20-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1009">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1010">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1010">Description</span></span>

<span data-ttu-id="05d20-1011">Эта служба устанавливает счетчик по адресу, предоставленному указателем назначения, задавая значение счетчика в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1012">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1013">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1013">Input Parameters</span></span>

- <span data-ttu-id="05d20-1014">**destination_ptr** — указатель на назначение счетчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="05d20-1015">**object_data** — указатель на структуру исходного объекта счетчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1016">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1016">Return Values</span></span>

- <span data-ttu-id="05d20-1017">**NX_SUCCESS** (0x00) — объект счетчика успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="05d20-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1019">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1020">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1020">Allowed From</span></span>

<span data-ttu-id="05d20-1021">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1022">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="05d20-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="05d20-1024">Получение 64-разрядного объекта счетчика</span><span class="sxs-lookup"><span data-stu-id="05d20-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1025">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1026">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1026">Description</span></span>

<span data-ttu-id="05d20-1027">Эта служба получает 64-разрядный объект счетчика по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1028">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1029">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1029">Input Parameters</span></span>

- <span data-ttu-id="05d20-1030">**source_ptr** — указатель на источник счетчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="05d20-1031">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1032">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1032">Return Values</span></span>

- <span data-ttu-id="05d20-1033">**NX_SUCCESS** (0x00) — объект счетчика успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1034">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1035">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1035">Allowed From</span></span>

<span data-ttu-id="05d20-1036">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1037">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="05d20-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="05d20-1039">Настройка 64-разрядного объекта счетчика</span><span class="sxs-lookup"><span data-stu-id="05d20-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1040">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="05d20-1041">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1041">Description</span></span>

<span data-ttu-id="05d20-1042">Эта служба устанавливает 64-разрядный счетчик по адресу, предоставленному указателем назначения, задавая значение счетчика в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1043">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1044">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1044">Input Parameters</span></span>

- <span data-ttu-id="05d20-1045">**destination_ptr** — указатель на назначение счетчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="05d20-1046">**object_data** — указатель на структуру исходного объекта счетчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1047">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1047">Return Values</span></span>

- <span data-ttu-id="05d20-1048">**NX_SUCCESS** (0x00) — объект счетчика успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="05d20-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1050">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1051">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1051">Allowed From</span></span>

<span data-ttu-id="05d20-1052">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1053">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="05d20-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="05d20-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="05d20-1055">Задание значения окончания MIB</span><span class="sxs-lookup"><span data-stu-id="05d20-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1056">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1057">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1057">Description</span></span>

<span data-ttu-id="05d20-1058">Эта служба создает объект, сигнализирующий об окончании MIB. Обычно ее следует вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1059">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1059">Input Parameters</span></span>

- <span data-ttu-id="05d20-1060">**not_used_ptr** — указатель на значение "Не используется, нужно использовать NX_NULL".</span><span class="sxs-lookup"><span data-stu-id="05d20-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="05d20-1061">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1062">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1062">Return Values</span></span>

- <span data-ttu-id="05d20-1063">**NX_SUCCESS** (0x00) — объект end-of-mib успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="05d20-1064">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1065">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1065">Allowed From</span></span>

<span data-ttu-id="05d20-1066">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1067">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="05d20-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="05d20-1069">Получение объекта датчика</span><span class="sxs-lookup"><span data-stu-id="05d20-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1070">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1071">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1071">Description</span></span>

<span data-ttu-id="05d20-1072">Эта служба получает объект датчика по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1073">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1074">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1074">Input Parameters</span></span>

- <span data-ttu-id="05d20-1075">**source_ptr** — указатель на источник датчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="05d20-1076">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1077">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1077">Return Values</span></span>

- <span data-ttu-id="05d20-1078">**NX_SUCCESS** (0x00) — объект датчика успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1079">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1080">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1080">Allowed From</span></span>

<span data-ttu-id="05d20-1081">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1082">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="05d20-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="05d20-1084">Задание объекта датчика</span><span class="sxs-lookup"><span data-stu-id="05d20-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1085">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1086">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1086">Description</span></span>

<span data-ttu-id="05d20-1087">Эта служба устанавливает датчик по адресу, предоставленному указателем назначения, задавая значение датчика в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1088">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1089">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1089">Input Parameters</span></span>

- <span data-ttu-id="05d20-1090">**destination_ptr** — указатель на назначение датчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="05d20-1091">**object_data** — указатель на структуру исходного объекта датчика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1092">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1092">Return Values</span></span>

- <span data-ttu-id="05d20-1093">**NX_SUCCESS** (0x00) — объект датчика успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="05d20-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1095">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1096">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1096">Allowed From</span></span>

<span data-ttu-id="05d20-1097">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1098">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="05d20-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="05d20-1100">Получение идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="05d20-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1101">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1102">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1102">Description</span></span>

<span data-ttu-id="05d20-1103">Эта служба получает идентификатор объекта (в нотации SIM ASCII) по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1104">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1105">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1105">Input Parameters</span></span>

- <span data-ttu-id="05d20-1106">**source_ptr** — указатель на источник идентификатора объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="05d20-1107">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1108">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1108">Return Values</span></span>

- <span data-ttu-id="05d20-1109">**NX_SUCCESS** (0x00) — идентификатор объекта успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1110">**NX_SNMP_ERROR** (0x100) — недопустимая длина объекта</span><span class="sxs-lookup"><span data-stu-id="05d20-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="05d20-1111">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1112">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1112">Allowed From</span></span>

<span data-ttu-id="05d20-1113">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1114">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="05d20-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="05d20-1116">Задание идентификатора объекта</span><span class="sxs-lookup"><span data-stu-id="05d20-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1117">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1118">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1118">Description</span></span>

<span data-ttu-id="05d20-1119">Эта служба устанавливает идентификатор объекта (в нотации SIM ASCII) по адресу, предоставленному указателем назначения, задавая в структуре данных объекта NetX идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1120">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1121">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1121">Input Parameters</span></span>

- <span data-ttu-id="05d20-1122">**destination_ptr** — указатель на назначение идентификатора объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="05d20-1123">**object_data** — указатель на структуру объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1124">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1124">Return Values</span></span>

- <span data-ttu-id="05d20-1125">**NX_SUCCESS** (0x00) — идентификатор объекта успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="05d20-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1127">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1128">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1128">Allowed From</span></span>

<span data-ttu-id="05d20-1129">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1130">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="05d20-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="05d20-1132">Получение объекта целого числа</span><span class="sxs-lookup"><span data-stu-id="05d20-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1133">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1134">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1134">Description</span></span>

<span data-ttu-id="05d20-1135">Эта служба получает объект целого числа по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1136">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1137">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1137">Input Parameters</span></span>

- <span data-ttu-id="05d20-1138">**source_ptr** — указатель на источник целого числа.</span><span class="sxs-lookup"><span data-stu-id="05d20-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="05d20-1139">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1140">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1140">Return Values</span></span>

- <span data-ttu-id="05d20-1141">**NX_SUCCESS** (0x00) — объект целого числа успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1142">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1143">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1143">Allowed From</span></span>

<span data-ttu-id="05d20-1144">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1145">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="05d20-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="05d20-1147">Задание объекта целого числа</span><span class="sxs-lookup"><span data-stu-id="05d20-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1148">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1149">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1149">Description</span></span>

<span data-ttu-id="05d20-1150">Эта служба устанавливает целое число по адресу, предоставленному указателем назначения, задавая значение целого числа в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1151">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1152">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1152">Input Parameters</span></span>

- <span data-ttu-id="05d20-1153">**destination_ptr** — указатель на назначение целого числа.</span><span class="sxs-lookup"><span data-stu-id="05d20-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="05d20-1154">**object_data** — указатель на структуру исходного объекта целого числа.</span><span class="sxs-lookup"><span data-stu-id="05d20-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1155">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1155">Return Values</span></span>

- <span data-ttu-id="05d20-1156">**NX_SUCCESS** (0x00) — объект целого числа успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="05d20-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1158">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1159">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1159">Allowed From</span></span>

<span data-ttu-id="05d20-1160">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1161">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="05d20-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="05d20-1163">Получение объекта IP-адреса (только IPv4)</span><span class="sxs-lookup"><span data-stu-id="05d20-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-1164">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1165">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1165">Description</span></span>

<span data-ttu-id="05d20-1166">Эта служба получает объект IP-адреса по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1167">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1168">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1168">Input Parameters</span></span>

- <span data-ttu-id="05d20-1169">**source_ptr** — указатель на источник адреса IPv4.</span><span class="sxs-lookup"><span data-stu-id="05d20-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="05d20-1170">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1171">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1171">Return Values</span></span>

- <span data-ttu-id="05d20-1172">**NX_SUCCESS** (0x00) — объект IP-адреса успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1173">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1174">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1174">Allowed From</span></span>

<span data-ttu-id="05d20-1175">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1176">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="05d20-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="05d20-1178">Получение объекта IP-адреса (только IPv6)</span><span class="sxs-lookup"><span data-stu-id="05d20-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="05d20-1179">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1180">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1180">Description</span></span>

<span data-ttu-id="05d20-1181">Эта служба получает объект адреса IPv6 по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="05d20-1182">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1183">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1183">Input Parameters</span></span>

- <span data-ttu-id="05d20-1184">**source_ptr** — указатель на источник адреса IPv6.</span><span class="sxs-lookup"><span data-stu-id="05d20-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="05d20-1185">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1186">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1186">Return Values</span></span>

- <span data-ttu-id="05d20-1187">**NX_SUCCESS** (0x00) — объект IP-адреса успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый код входного объекта SNMP.</span><span class="sxs-lookup"><span data-stu-id="05d20-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="05d20-1189">**NX_NOT_ENABLED** (0x14) — адрес IPv6 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="05d20-1190">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1191">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1191">Allowed From</span></span>

<span data-ttu-id="05d20-1192">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1193">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="05d20-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="05d20-1195">Задание объекта адреса IPv4</span><span class="sxs-lookup"><span data-stu-id="05d20-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1196">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1197">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1197">Description</span></span>

<span data-ttu-id="05d20-1198">Эта служба устанавливает адрес IPv4 по адресу, предоставленному указателем назначения, задавая IP-адрес в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1199">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1200">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1200">Input Parameters</span></span>

- <span data-ttu-id="05d20-1201">**destination_ptr** — указатель на IP-адрес, который необходимо задать.</span><span class="sxs-lookup"><span data-stu-id="05d20-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="05d20-1202">**object_data** — указатель на структуру объектов IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="05d20-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1203">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1203">Return Values</span></span>

- <span data-ttu-id="05d20-1204">**NX_SUCCESS** (0x00) — объект IP-адреса успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="05d20-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1206">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1207">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1207">Allowed From</span></span>

<span data-ttu-id="05d20-1208">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1209">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="05d20-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="05d20-1211">Задание объекта адреса IPv6</span><span class="sxs-lookup"><span data-stu-id="05d20-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1212">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1213">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1213">Description</span></span>

<span data-ttu-id="05d20-1214">Эта служба устанавливает адрес IPv6 по адресу, предоставленному указателем назначения, задавая IP-адрес в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1215">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1216">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1216">Input Parameters</span></span>

- <span data-ttu-id="05d20-1217">**destination_ptr** — указатель на IP-адрес, который необходимо задать.</span><span class="sxs-lookup"><span data-stu-id="05d20-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="05d20-1218">**object_data** — указатель на структуру объектов IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="05d20-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1219">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1219">Return Values</span></span>

- <span data-ttu-id="05d20-1220">**NX_SUCCESS** (0x00) — адрес IPv6 успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="05d20-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1222">**NX_NOT_ENABLED** (0x14) — адрес IPv6 не включен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="05d20-1223">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1224">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1224">Allowed From</span></span>

<span data-ttu-id="05d20-1225">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1226">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="05d20-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="05d20-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="05d20-1228">Задание объекта без экземпляра</span><span class="sxs-lookup"><span data-stu-id="05d20-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1229">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1230">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1230">Description</span></span>

<span data-ttu-id="05d20-1231">Эта служба создает объект, который будет сигнализировать об отсутствии экземпляра указанного объекта. Обычно ее нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1232">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1232">Input Parameters</span></span>

- <span data-ttu-id="05d20-1233">**not_used_ptr** — указатель на значение "Не используется, нужно использовать NX_NULL".</span><span class="sxs-lookup"><span data-stu-id="05d20-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="05d20-1234">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1235">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1235">Return Values</span></span>

- <span data-ttu-id="05d20-1236">**NX_SUCCESS** (0x00) — объект без экземпляра успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="05d20-1237">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1238">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1238">Allowed From</span></span>

<span data-ttu-id="05d20-1239">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1240">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="05d20-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="05d20-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="05d20-1242">Задание объекта со значением "не найдено"</span><span class="sxs-lookup"><span data-stu-id="05d20-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1243">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1244">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1244">Description</span></span>

<span data-ttu-id="05d20-1245">Эта служба создает объект, сигнализирующий о том, что объект не удалось найти. Обычно ее следует вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1246">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1246">Input Parameters</span></span>

- <span data-ttu-id="05d20-1247">**not_used_ptr** — указатель на значение "Не используется, нужно использовать NX_NULL".</span><span class="sxs-lookup"><span data-stu-id="05d20-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="05d20-1248">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1249">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1249">Return Values</span></span>

- <span data-ttu-id="05d20-1250">**NX_SUCCESS** (0x00) — объект со значением "не найдено" успешно создан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="05d20-1251">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1252">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1252">Allowed From</span></span>

<span data-ttu-id="05d20-1253">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1254">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="05d20-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="05d20-1256">Получение объекта октетной строки</span><span class="sxs-lookup"><span data-stu-id="05d20-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1257">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="05d20-1258">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1258">Description</span></span>

<span data-ttu-id="05d20-1259">Эта служба получает октетную строку по адресу, предоставленному указателем источника, и помещает ее в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1260">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1261">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1261">Input Parameters</span></span>

- <span data-ttu-id="05d20-1262">**source_ptr** — указатель на источник октетной строки.</span><span class="sxs-lookup"><span data-stu-id="05d20-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="05d20-1263">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="05d20-1264">**Длина** — число байтов в октетной строке.</span><span class="sxs-lookup"><span data-stu-id="05d20-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1265">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1265">Return Values</span></span>

- <span data-ttu-id="05d20-1266">**NX_SUCCESS** (0x00) — октетная строка успешно получена.</span><span class="sxs-lookup"><span data-stu-id="05d20-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1267">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1268">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1268">Allowed From</span></span>

<span data-ttu-id="05d20-1269">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1270">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="05d20-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="05d20-1272">Задание объекта октетной строки</span><span class="sxs-lookup"><span data-stu-id="05d20-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1273">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1274">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1274">Description</span></span>

<span data-ttu-id="05d20-1275">Эта служба задает октетную строку по адресу, предоставленному указателем назначения, задавая октетную строку в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1276">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1277">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1277">Input Parameters</span></span>

- <span data-ttu-id="05d20-1278">**destination_ptr** — указатель на цель для октетной строки.</span><span class="sxs-lookup"><span data-stu-id="05d20-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="05d20-1279">**object_data** — указатель на структуру исходного объекта октетной строки.</span><span class="sxs-lookup"><span data-stu-id="05d20-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1280">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1280">Return Values</span></span>

- <span data-ttu-id="05d20-1281">**NX_SUCCESS** (0x00) — октетная строка успешно задана.</span><span class="sxs-lookup"><span data-stu-id="05d20-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="05d20-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1283">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1284">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1284">Allowed From</span></span>

<span data-ttu-id="05d20-1285">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1286">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="05d20-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="05d20-1288">Получение объекта строки ASCII</span><span class="sxs-lookup"><span data-stu-id="05d20-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1289">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1290">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1290">Description</span></span>

<span data-ttu-id="05d20-1291">Эта служба получает строку ASCII по адресу, предоставленному указателем источника, и помещает ее в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1292">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1293">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1293">Input Parameters</span></span>

- <span data-ttu-id="05d20-1294">**source_ptr** — указатель на источник строки ASCII.</span><span class="sxs-lookup"><span data-stu-id="05d20-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="05d20-1295">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1296">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1296">Return Values</span></span>

- <span data-ttu-id="05d20-1297">**NX_SUCCESS** (0x00) — строка ASCII успешно получена.</span><span class="sxs-lookup"><span data-stu-id="05d20-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1298">**NX_SNMP_ERROR** (0x100) — строка слишком велика.</span><span class="sxs-lookup"><span data-stu-id="05d20-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="05d20-1299">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1300">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1300">Allowed From</span></span>

<span data-ttu-id="05d20-1301">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1302">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="05d20-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="05d20-1304">Задание объекта строки ASCII</span><span class="sxs-lookup"><span data-stu-id="05d20-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1305">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1306">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1306">Description</span></span>

<span data-ttu-id="05d20-1307">Эта служба задает строку ASCII по адресу, предоставленному указателем назначения, задавая строку ASCII в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1308">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1309">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1309">Input Parameters</span></span>

- <span data-ttu-id="05d20-1310">**destination_ptr** — указатель на цель для строки ASCII.</span><span class="sxs-lookup"><span data-stu-id="05d20-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="05d20-1311">**object_data** — указатель на структуру исходного объекта строки ASCII.</span><span class="sxs-lookup"><span data-stu-id="05d20-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1312">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1312">Return Values</span></span>

- <span data-ttu-id="05d20-1313">**NX_SUCCESS** (0x00) — строка ASCII успешно задана.</span><span class="sxs-lookup"><span data-stu-id="05d20-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="05d20-1314">**NX_SNMP_ERROR** (0x100) — размер строки слишком велик.</span><span class="sxs-lookup"><span data-stu-id="05d20-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="05d20-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) — строка содержит недопустимый символ.</span><span class="sxs-lookup"><span data-stu-id="05d20-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="05d20-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1317">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1318">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1318">Allowed From</span></span>

<span data-ttu-id="05d20-1319">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1320">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="05d20-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="05d20-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="05d20-1322">Получение объекта timetics</span><span class="sxs-lookup"><span data-stu-id="05d20-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1323">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1324">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1324">Description</span></span>

<span data-ttu-id="05d20-1325">Эта служба получает объект timetics по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="05d20-1326">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1327">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1327">Input Parameters</span></span>

- <span data-ttu-id="05d20-1328">**source_ptr** — указатель на источник объекта timetics.</span><span class="sxs-lookup"><span data-stu-id="05d20-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="05d20-1329">**object_data** — указатель на структуру целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1330">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1330">Return Values</span></span>

- <span data-ttu-id="05d20-1331">**NX_SUCCESS** (0x00) — объект timetics успешно получен.</span><span class="sxs-lookup"><span data-stu-id="05d20-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="05d20-1332">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1333">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1333">Allowed From</span></span>

<span data-ttu-id="05d20-1334">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1335">Например, .</span><span class="sxs-lookup"><span data-stu-id="05d20-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="05d20-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="05d20-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="05d20-1337">Задание объекта timetics</span><span class="sxs-lookup"><span data-stu-id="05d20-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="05d20-1338">Прототип</span><span class="sxs-lookup"><span data-stu-id="05d20-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="05d20-1339">Описание</span><span class="sxs-lookup"><span data-stu-id="05d20-1339">Description</span></span>

<span data-ttu-id="05d20-1340">Эта служба задает переменную timetics по адресу, предоставленному указателем назначения, задавая timetics в структуре данных объекта NetX.</span><span class="sxs-lookup"><span data-stu-id="05d20-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="05d20-1341">Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.</span><span class="sxs-lookup"><span data-stu-id="05d20-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="05d20-1342">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="05d20-1342">Input Parameters</span></span>

- <span data-ttu-id="05d20-1343">**destination_ptr** — указатель на назначение для timetics.</span><span class="sxs-lookup"><span data-stu-id="05d20-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="05d20-1344">**object_data** — указатель на структуру исходного объекта timetics.</span><span class="sxs-lookup"><span data-stu-id="05d20-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="05d20-1345">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="05d20-1345">Return Values</span></span>

- <span data-ttu-id="05d20-1346">**NX_SUCCESS** (0x00) — объект timetics успешно задан.</span><span class="sxs-lookup"><span data-stu-id="05d20-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="05d20-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="05d20-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="05d20-1348">**NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="05d20-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="05d20-1349">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="05d20-1349">Allowed From</span></span>

<span data-ttu-id="05d20-1350">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="05d20-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="05d20-1351">Пример</span><span class="sxs-lookup"><span data-stu-id="05d20-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```