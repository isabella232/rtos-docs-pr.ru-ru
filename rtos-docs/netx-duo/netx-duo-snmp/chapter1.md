---
title: Глава 1. Введение в SNMP для NetX Duo в ОСРВ Azure
description: Реализация SNMP NetX Duo является агентом SNMP. Агент отвечает за реагирование на команды диспетчера SNMP и отправку ловушек, управляемых событиями.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814575"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="e64a6-104">Глава 1. Введение в SNMP для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="e64a6-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="e64a6-105">Протокол SNMP — это протокол, предназначенный для управления устройствами в сети.</span><span class="sxs-lookup"><span data-stu-id="e64a6-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="e64a6-106">Протокол SNMP для управляющей функции использует протокол UDP без контроля соединения.</span><span class="sxs-lookup"><span data-stu-id="e64a6-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="e64a6-107">Реализация SNMP NetX Duo для ОСРВ Azure является агентом SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="e64a6-108">Агент отвечает за реагирование на команды диспетчера SNMP и отправку ловушек, управляемых событиями.</span><span class="sxs-lookup"><span data-stu-id="e64a6-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="e64a6-109">SNMP NetX Duo поддерживает обмен данными с диспетчерами SNMP по протоколам IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="e64a6-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="e64a6-110">Приложения SNMP NetX должны компилироваться и выполняться в SNMP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="e64a6-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="e64a6-111">Однако разработчику рекомендуется перенести существующие SNMP-приложения на использование эквивалентных служб "Duo".</span><span class="sxs-lookup"><span data-stu-id="e64a6-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="e64a6-112">Например, при отправке сообщений SNMP-ловушки следующие службы "Duo" должны заменить их эквиваленты NetX:</span><span class="sxs-lookup"><span data-stu-id="e64a6-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="e64a6-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="e64a6-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="e64a6-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="e64a6-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="e64a6-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="e64a6-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="e64a6-116">Дополнительные сведения см. в разделах **Описание служб агента SNMP** в данном руководстве пользователя.</span><span class="sxs-lookup"><span data-stu-id="e64a6-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="e64a6-117">Требования для агента SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="e64a6-118">Для пакета SNMP NetX Duo требуется, чтобы заранее был создан экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="e64a6-119">Кроме того, в таком экземпляре IP должен быть включен протокол UDP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="e64a6-120">Агент SNMP NetX Duo имеет несколько дополнительных требований.</span><span class="sxs-lookup"><span data-stu-id="e64a6-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="e64a6-121">Во-первых, для обработки всех запросов диспетчером SNMP требуется доступ к порту 161.</span><span class="sxs-lookup"><span data-stu-id="e64a6-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="e64a6-122">Также требуется доступ к порту 162 для отправки менеджеру сообщений ловушек.</span><span class="sxs-lookup"><span data-stu-id="e64a6-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="e64a6-123">Чтобы использовать агент SNMP NetX Duo по протоколу IPv6 и получать объекты IPv6, необходимо включить IPv6 в NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="e64a6-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="e64a6-124">Дополнительные сведения о включении в экземпляре IP поддержку служб IPv6 см. в ***Руководстве пользователя по NetX Duo***.</span><span class="sxs-lookup"><span data-stu-id="e64a6-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="e64a6-125">Ограничения SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="e64a6-126">Протокол SNMP NetX Duo реализует SNMP версий 1, 2 и 3.</span><span class="sxs-lookup"><span data-stu-id="e64a6-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="e64a6-127">Реализация SNMPv3 поддерживает проверку подлинности MD5 и SHA, а также шифрование DES.</span><span class="sxs-lookup"><span data-stu-id="e64a6-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="e64a6-128">Эта версия агента SNMP NetX Duo имеет следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="e64a6-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="e64a6-129">Один агент SNMP на один экземпляр IP NetX.</span><span class="sxs-lookup"><span data-stu-id="e64a6-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="e64a6-130">Отсутствует поддержка RMON.</span><span class="sxs-lookup"><span data-stu-id="e64a6-130">No support for RMON</span></span>
3. <span data-ttu-id="e64a6-131">Информационные сообщения SNMP v3 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="e64a6-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="e64a6-132">Типы данных OPAQUE и NSAP не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="e64a6-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="e64a6-133">Адреса IPv6 определяются как строки октетов, а проверка правильности форматирования лежит на приложении.</span><span class="sxs-lookup"><span data-stu-id="e64a6-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="e64a6-134">Имена объектов SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-134">SNMP Object Names</span></span>

<span data-ttu-id="e64a6-135">Протокол SNMP предназначен для управления устройствами в сети.</span><span class="sxs-lookup"><span data-stu-id="e64a6-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="e64a6-136">Для этого каждое устройство, управляемое SNMP, имеет набор объектов, определенных структурой управляющих данных (SMI), как это определено в документе RFC 1155.</span><span class="sxs-lookup"><span data-stu-id="e64a6-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="e64a6-137">Структура представляет собой иерархический древовидный тип структуры, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e64a6-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![Схема структуры данных управления.](media/image3.png)

<span data-ttu-id="e64a6-139">Каждый узел дерева является объектом.</span><span class="sxs-lookup"><span data-stu-id="e64a6-139">Each node in the tree is an object.</span></span> <span data-ttu-id="e64a6-140">Объект "dod" в дереве определяется нотацией 1.3.6, а объект "internet" в дереве определяется нотацией 1.3.6.1.</span><span class="sxs-lookup"><span data-stu-id="e64a6-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="e64a6-141">Все имена объектов SNMP начинаются с нотации 1.3.6.</span><span class="sxs-lookup"><span data-stu-id="e64a6-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="e64a6-142">Диспетчер SNMP использует эту нотацию объектов, чтобы указать, какой объект на устройстве требуется получить или задать.</span><span class="sxs-lookup"><span data-stu-id="e64a6-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="e64a6-143">Агент SNMP NetX Duo интерпретирует подобные запросы диспетчера и предоставляет приложениям механизмы для выполнения запрошенной операции.</span><span class="sxs-lookup"><span data-stu-id="e64a6-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="e64a6-144">Запросы диспетчера SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-144">SNMP Manager Requests</span></span>

<span data-ttu-id="e64a6-145">Протокол SNMP имеет простой механизм управления устройствами.</span><span class="sxs-lookup"><span data-stu-id="e64a6-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="e64a6-146">Существует набор стандартных команд SNMP, которые выдает диспетчер SNMP устройству SNMP через *порт 161*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="e64a6-147">Ниже приведены некоторые основные команды диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="e64a6-148">Команда SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-148">SNMP Command</span></span> | <span data-ttu-id="e64a6-149">Значение</span><span class="sxs-lookup"><span data-stu-id="e64a6-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="e64a6-150">GET</span><span class="sxs-lookup"><span data-stu-id="e64a6-150">GET</span></span>          | <span data-ttu-id="e64a6-151">*Получить указанный объект*</span><span class="sxs-lookup"><span data-stu-id="e64a6-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="e64a6-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="e64a6-152">GETNEXT</span></span>      | <span data-ttu-id="e64a6-153">*Получить следующий логический объект после указанного идентификатора объекта*</span><span class="sxs-lookup"><span data-stu-id="e64a6-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="e64a6-154">GETBULK</span><span class="sxs-lookup"><span data-stu-id="e64a6-154">GETBULK</span></span>      | <span data-ttu-id="e64a6-155">*Получить несколько логических объектов после указанного идентификатора объекта*</span><span class="sxs-lookup"><span data-stu-id="e64a6-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="e64a6-156">SET</span><span class="sxs-lookup"><span data-stu-id="e64a6-156">SET</span></span>          | <span data-ttu-id="e64a6-157">*Установить указанный объект*</span><span class="sxs-lookup"><span data-stu-id="e64a6-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="e64a6-158">Эти команды кодируются в первой версии абстрактного синтаксиса данных (ASN.1) и размещаются в полезных данных пакета UDP, отправляемого диспетчером SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="e64a6-159">Агент SNMP NetX Duo обрабатывает запрос, а затем вызывает соответствующую подпрограмму обработки, указанную в вызове ***nx_snmp_agent_create***.</span><span class="sxs-lookup"><span data-stu-id="e64a6-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="e64a6-160">Ловушки агента SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="e64a6-161">Агент SNMP NetX Duo позволяет также асинхронно оповещать диспетчер SNMP о событиях.</span><span class="sxs-lookup"><span data-stu-id="e64a6-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="e64a6-162">Это делается с помощью команды SNMP-ловушки.</span><span class="sxs-lookup"><span data-stu-id="e64a6-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="e64a6-163">Для каждой версии SNMP существует свой уникальный API для отправки ловушек диспетчеру SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="e64a6-164">По умолчанию ловушки отправляются диспетчеру SNMP по порту 162.</span><span class="sxs-lookup"><span data-stu-id="e64a6-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="e64a6-165">Агент SNMP NetX Duo предоставляет отдельные ключи безопасности для сообщений о ловушках протокола SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="e64a6-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="e64a6-166">Для этого SNMP-приложение должно создать отдельный набор ключей, применяемых к ответам на запросы диспетчера.</span><span class="sxs-lookup"><span data-stu-id="e64a6-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="e64a6-167">Система безопасности ловушек позволяет агенту SNMP использовать одни и те же или разные пароли для проверки подлинности и конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="e64a6-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="e64a6-168">Дополнительные сведения о создании ключей безопасности см. в разделе **Проверка подлинности и шифрование SNMP NetX Duo**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="e64a6-169">Список стандартных переменных ловушек SNMP приведен в начале файла *nxd_snmp.h:*</span><span class="sxs-lookup"><span data-stu-id="e64a6-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="e64a6-170">Переменные</span><span class="sxs-lookup"><span data-stu-id="e64a6-170">Variables</span></span>                                 | <span data-ttu-id="e64a6-171">Значение</span><span class="sxs-lookup"><span data-stu-id="e64a6-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="e64a6-172">#define NX_SNMP_TRAP_COLDSTART</span><span class="sxs-lookup"><span data-stu-id="e64a6-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="e64a6-173">0</span><span class="sxs-lookup"><span data-stu-id="e64a6-173">0</span></span> |
| <span data-ttu-id="e64a6-174">#define NX_SNMP_TRAP_WARMSTART</span><span class="sxs-lookup"><span data-stu-id="e64a6-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="e64a6-175">1</span><span class="sxs-lookup"><span data-stu-id="e64a6-175">1</span></span> |
| <span data-ttu-id="e64a6-176">#define NX_SNMP_TRAP_LINKDOWN</span><span class="sxs-lookup"><span data-stu-id="e64a6-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="e64a6-177">2</span><span class="sxs-lookup"><span data-stu-id="e64a6-177">2</span></span> |
| <span data-ttu-id="e64a6-178">#define NX_SNMP_TRAP_LINKUP</span><span class="sxs-lookup"><span data-stu-id="e64a6-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="e64a6-179">3</span><span class="sxs-lookup"><span data-stu-id="e64a6-179">3</span></span> |
| <span data-ttu-id="e64a6-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span><span class="sxs-lookup"><span data-stu-id="e64a6-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="e64a6-181">4</span><span class="sxs-lookup"><span data-stu-id="e64a6-181">4</span></span> |
| <span data-ttu-id="e64a6-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span><span class="sxs-lookup"><span data-stu-id="e64a6-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="e64a6-183">5</span><span class="sxs-lookup"><span data-stu-id="e64a6-183">5</span></span> |
| <span data-ttu-id="e64a6-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span><span class="sxs-lookup"><span data-stu-id="e64a6-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="e64a6-185">6</span><span class="sxs-lookup"><span data-stu-id="e64a6-185">6</span></span> |

<span data-ttu-id="e64a6-186">Чтобы включить эти переменные в сообщение ловушки, входному аргументу trap_type в *nx_snmp_agent_trapv2_send* (SNMPv2) или *nx_snmp_agent_trapv3_send* (SNMPv3) присваивается перечисляемое значение этих переменных.</span><span class="sxs-lookup"><span data-stu-id="e64a6-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="e64a6-187">Ниже приведен пример уведомления диспетчера SNMP о событии холодного запуска для протокола SNMPv2:</span><span class="sxs-lookup"><span data-stu-id="e64a6-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="e64a6-188">Чтобы включить в сообщение ловушки собственные переменные, входному аргументу trap_type присваивается значение NX_SNMP_TRAP_CUSTOM и входной аргумент списка ловушек содержит собственные данные.</span><span class="sxs-lookup"><span data-stu-id="e64a6-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="e64a6-189">Обратите внимание, что сообщение ловушки будет содержать время доступности системы (1.3.6.1.6.3.1.1.4.1.0).</span><span class="sxs-lookup"><span data-stu-id="e64a6-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="e64a6-190">Ниже приведен пример для протокола SNMPv2:</span><span class="sxs-lookup"><span data-stu-id="e64a6-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="e64a6-191">Проверка подлинности и шифрование SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="e64a6-192">Различают две разновидности проверки подлинности: *обычную* и *с использованием дайджеста*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="e64a6-193">Обычная проверка подлинности эквивалентна простой проверке подлинности *имени пользователя* в обычном текстовом формате во многих протоколах.</span><span class="sxs-lookup"><span data-stu-id="e64a6-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="e64a6-194">При обычной проверке подлинности SNMP пользователь просто проверяет допустимость заданного имени пользователя для выполнения операций SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="e64a6-195">Обычная проверка подлинности является единственным вариантом для SNMP версий 1 и 2.</span><span class="sxs-lookup"><span data-stu-id="e64a6-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="e64a6-196">Основным недостатком обычной проверки подлинности является то, что имя пользователя передается в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="e64a6-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="e64a6-197">Дайджест-проверка подлинности SNMPv3 решает эту проблему и никогда не передает имя пользователя в виде обычного текста.</span><span class="sxs-lookup"><span data-stu-id="e64a6-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="e64a6-198">Вместо этого используется определенный алгоритм для получения 96-разрядного "дайджеста" из имени пользователя, обработчика контекста и других сведений.</span><span class="sxs-lookup"><span data-stu-id="e64a6-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="e64a6-199">Агент SNMP NetX Duo поддерживает алгоритмы дайджестов MD5 и SHA.</span><span class="sxs-lookup"><span data-stu-id="e64a6-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="e64a6-200">Чтобы включить проверку подлинности, агент SNMP должен задать идентификатор обработчика контекста с помощью службы *nx_snmp_agent_context_engine_set*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="e64a6-201">Идентификатор обработчика контекста используется при создании ключа проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="e64a6-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="e64a6-202">Шифрование данных SNMPv3 доступно с использованием алгоритма DES.</span><span class="sxs-lookup"><span data-stu-id="e64a6-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="e64a6-203">Шифрование требует включения проверки подлинности (нельзя шифровать данные без настройки параметров проверки подлинности).</span><span class="sxs-lookup"><span data-stu-id="e64a6-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="e64a6-204">Для создания ключей проверки подлинности и конфиденциальности используются следующие API:</span><span class="sxs-lookup"><span data-stu-id="e64a6-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="e64a6-205">Затем необходимо настроить агент SNMP для использования этих ключей.</span><span class="sxs-lookup"><span data-stu-id="e64a6-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="e64a6-206">Чтобы зарегистрировать ключ в агенте SNMP, используются следующие API:</span><span class="sxs-lookup"><span data-stu-id="e64a6-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="e64a6-207">Для сообщений о ловушках можно создавать отдельные ключи.</span><span class="sxs-lookup"><span data-stu-id="e64a6-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="e64a6-208">Для применения ключей к сообщениям ловушки доступны следующие API:</span><span class="sxs-lookup"><span data-stu-id="e64a6-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="e64a6-209">Чтобы отключить проверку подлинности или шифрование для ответных сообщений и отправки ловушек, используйте эти службы с входными указателями ключей, установленными в значение NULL.</span><span class="sxs-lookup"><span data-stu-id="e64a6-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="e64a6-210">Строки сообщества SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="e64a6-211">Агент SNMP NetX Duo поддерживает как общедоступные, так и закрытые строки сообщества.</span><span class="sxs-lookup"><span data-stu-id="e64a6-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="e64a6-212">Открытая строка задается с помощью службы *nx_snmp_agent _public_string_set*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="e64a6-213">Закрытая строка агента SNMP NetX Duo задается с помощью службы *nx_snmp_agent_private_string_set*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="e64a6-214">Обратный вызов имени пользователя SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="e64a6-215">Пакет агента SNMP NetX Duo позволяет приложению указать (с помощью вызова ***nx_snmp_agent_create***) обратный вызов имени пользователя, который вызывается в начале обработки каждого запроса SNMP-клиента.</span><span class="sxs-lookup"><span data-stu-id="e64a6-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="e64a6-216">Подпрограммы обратного вызова предоставляют агенту SNMP NetX Duo имя пользователя.</span><span class="sxs-lookup"><span data-stu-id="e64a6-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="e64a6-217">Если указанное имя пользователя является допустимым или проверка имени пользователя не требуется для ответа на запрос, функция обратного вызова имени пользователя должна возвращать значение **NX_SUCCESS**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="e64a6-218">В противном случае подпрограмма должна возвращать **NX_SNMP_ERROR**, чтобы указать, что указанное имя пользователя является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="e64a6-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="e64a6-219">Формат подпрограммы обратного вызова имени пользователя приложения приведен ниже:</span><span class="sxs-lookup"><span data-stu-id="e64a6-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="e64a6-220">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e64a6-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e64a6-221">Параметр</span><span class="sxs-lookup"><span data-stu-id="e64a6-221">Parameter</span></span> | <span data-ttu-id="e64a6-222">Значение</span><span class="sxs-lookup"><span data-stu-id="e64a6-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="e64a6-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e64a6-223">*agent_ptr*</span></span> | <span data-ttu-id="e64a6-224">Указатель на вызывающий агент SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="e64a6-225">username</span><span class="sxs-lookup"><span data-stu-id="e64a6-225">username</span></span>  | <span data-ttu-id="e64a6-226">Назначение для указателя на требуемое имя пользователя</span><span class="sxs-lookup"><span data-stu-id="e64a6-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="e64a6-227">Для сеансов протоколов SNMPv1 и SNMPv2/v2C приложение захочет проверить строку сообщества во входящем SNMP-запросе, чтобы определить, имеет ли SNMP-запрос допустимую строку сообщества.</span><span class="sxs-lookup"><span data-stu-id="e64a6-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="e64a6-228">Для этого приложения SNMP существует несколько служб.есть несколько служб.</span><span class="sxs-lookup"><span data-stu-id="e64a6-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="e64a6-229">Приложение SNMP может запросить, является ли текущий запрос диспетчера SNMP запросом GET (например, GET, GETNEXT или GETBULK) или запросом SET, используя следующую службу:</span><span class="sxs-lookup"><span data-stu-id="e64a6-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="e64a6-230">Если запрос является типом GET, приложение может сравнить входную строку сообщества с общедоступной строкой SNMP-агента:</span><span class="sxs-lookup"><span data-stu-id="e64a6-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="e64a6-231">Аналогично, если запрос является типом SET, приложение может сравнить входную строку сообщества с закрытой строкой SNMP-агента:</span><span class="sxs-lookup"><span data-stu-id="e64a6-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="e64a6-232">Возвращаемые значения is_public и is_private указывают, является ли входная строка сообщества допустимой общедоступной или закрытой строкой сообщества соответственно.</span><span class="sxs-lookup"><span data-stu-id="e64a6-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="e64a6-233">Возвращаемое значение подпрограммы обратного вызова имени пользователя указывает, является ли имя пользователя допустимым.</span><span class="sxs-lookup"><span data-stu-id="e64a6-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="e64a6-234">Значение **NX_SUCCESS** возвращается, если имя пользователя является допустимым, а **NX_SNMP_ERROR** — если имя пользователя является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="e64a6-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="e64a6-235">Обратный вызов GET для агента SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="e64a6-236">Приложение должно задать подпрограммы обратного вызова для обработки запросов объектов GET от диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="e64a6-237">Обратный вызов извлекает значение объекта, указанного в запросе.</span><span class="sxs-lookup"><span data-stu-id="e64a6-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="e64a6-238">Подпрограмма обратного вызова запроса GET приложения определена ниже.</span><span class="sxs-lookup"><span data-stu-id="e64a6-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="e64a6-239">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e64a6-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e64a6-240">Параметр</span><span class="sxs-lookup"><span data-stu-id="e64a6-240">Parameter</span></span>        | <span data-ttu-id="e64a6-241">Значение</span><span class="sxs-lookup"><span data-stu-id="e64a6-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="e64a6-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e64a6-242">*agent_ptr*</span></span>        | <span data-ttu-id="e64a6-243">Указатель на вызывающий агент SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="e64a6-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="e64a6-244">object_requested</span></span> | <span data-ttu-id="e64a6-245">Строка ASCII, представляющая идентификатор объекта, для которого предназначена операция GET.</span><span class="sxs-lookup"><span data-stu-id="e64a6-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="e64a6-246">object_data</span><span class="sxs-lookup"><span data-stu-id="e64a6-246">object_data</span></span>      | <span data-ttu-id="e64a6-247">Структура данных для хранения значения, полученного функцией обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="e64a6-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="e64a6-248">Эту задачу можно выполнить с помощью ряда API SNMP NetX Duo, описанных ниже.</span><span class="sxs-lookup"><span data-stu-id="e64a6-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="e64a6-249">*Для строк октетов объекту должна быть назначена длина, чтобы ее значение знала внутренняя функция, так как сам обратный вызов не имеет аргумента длины:*</span><span class="sxs-lookup"><span data-stu-id="e64a6-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="e64a6-250">Поскольку обратному вызову GET неизвестен тип данных, нет необходимости проверять тип данных.</span><span class="sxs-lookup"><span data-stu-id="e64a6-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="e64a6-251">Длина не будет оказывать влияния на числовые типы и строки с разделителями null.</span><span class="sxs-lookup"><span data-stu-id="e64a6-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="e64a6-252">Затем вызовите внутреннюю функцию:</span><span class="sxs-lookup"><span data-stu-id="e64a6-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="e64a6-253">Если функции обратного вызова не удается найти запрошенный объект, должен возвращаться код ошибки **NX_SNMP_ERROR_NOSUCHNAME**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="e64a6-254">Если обнаружена какая-либо другая ошибка, возвращается **NX_SNMP_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="e64a6-255">Обратный вызов GETNEXT для агента SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="e64a6-256">Приложение также должно задать подпрограммы обратного вызова для запросов объектов GETNEXT из диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="e64a6-257">Обратный вызов GETNEXT извлекает значение следующего объекта, указанного в запросе.</span><span class="sxs-lookup"><span data-stu-id="e64a6-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="e64a6-258">Подпрограмма обратного вызова запроса GETNEXT приложения определена ниже:</span><span class="sxs-lookup"><span data-stu-id="e64a6-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="e64a6-259">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e64a6-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e64a6-260">Параметр</span><span class="sxs-lookup"><span data-stu-id="e64a6-260">Parameter</span></span>        | <span data-ttu-id="e64a6-261">Значение</span><span class="sxs-lookup"><span data-stu-id="e64a6-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="e64a6-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e64a6-262">*agent_ptr*</span></span>        | <span data-ttu-id="e64a6-263">Указатель на вызывающий агент SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="e64a6-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="e64a6-264">object_requested</span></span> | <span data-ttu-id="e64a6-265">Строка ASCII, представляющая идентификатор объекта, для которого предназначена операция GETNEXT.</span><span class="sxs-lookup"><span data-stu-id="e64a6-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="e64a6-266">object_data</span><span class="sxs-lookup"><span data-stu-id="e64a6-266">object_data</span></span>      | <span data-ttu-id="e64a6-267">Структура данных для хранения значения, полученного функцией обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="e64a6-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="e64a6-268">Эту задачу можно выполнить с помощью ряда API SNMP NetX Duo, описанных ниже.</span><span class="sxs-lookup"><span data-stu-id="e64a6-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="e64a6-269">Так же, как и для обратных вызовов GET, для строк октетов объекту должна быть назначена длина, чтобы ее значение знала внутренняя функция, так как сам обратный вызов не имеет аргумента длины:</span><span class="sxs-lookup"><span data-stu-id="e64a6-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="e64a6-270">Поскольку обратному вызову GET неизвестен тип данных, нет необходимости проверять тип данных.</span><span class="sxs-lookup"><span data-stu-id="e64a6-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="e64a6-271">Длина не будет оказывать влияния на числовые типы и строки с разделителями null.</span><span class="sxs-lookup"><span data-stu-id="e64a6-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="e64a6-272">Затем вызовите внутреннюю функцию:</span><span class="sxs-lookup"><span data-stu-id="e64a6-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="e64a6-273">Если функции обратного вызова не удается найти запрошенный объект, должен возвращаться код ошибки **NX_SNMP_ERROR_NOSUCHNAME**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="e64a6-274">Если обнаружена какая-либо другая ошибка, возвращается **NX_SNMP_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="e64a6-275">Обратный вызов SET для агента SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="e64a6-276">Приложение должно задать подпрограммы обратного вызова для обработки запросов объектов SET от диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="e64a6-277">Обратный вызов SET задает значение объекта, указанного в запросе.</span><span class="sxs-lookup"><span data-stu-id="e64a6-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="e64a6-278">Подпрограмма обратного вызова запроса SET приложения определена ниже:</span><span class="sxs-lookup"><span data-stu-id="e64a6-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="e64a6-279">Входные параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e64a6-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="e64a6-280">Параметр</span><span class="sxs-lookup"><span data-stu-id="e64a6-280">Parameter</span></span>        | <span data-ttu-id="e64a6-281">Значение</span><span class="sxs-lookup"><span data-stu-id="e64a6-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="e64a6-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="e64a6-282">*agent_ptr*</span></span>      | <span data-ttu-id="e64a6-283">Указатель на вызывающий агент SNMP</span><span class="sxs-lookup"><span data-stu-id="e64a6-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="e64a6-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="e64a6-284">object_requested</span></span> | <span data-ttu-id="e64a6-285">Строка ASCII, представляющая идентификатор объекта, для которого предназначена операция SET.</span><span class="sxs-lookup"><span data-stu-id="e64a6-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="e64a6-286">object_data</span><span class="sxs-lookup"><span data-stu-id="e64a6-286">object_data</span></span>      | <span data-ttu-id="e64a6-287">Структура данных, содержащая новое значение для указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="e64a6-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="e64a6-288">Непосредственно операцию можно выполнить с помощью API SNMP NetX Duo, описанных ниже.</span><span class="sxs-lookup"><span data-stu-id="e64a6-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="e64a6-289">Обратите внимание, что для строк октета обратный вызов SET должен обновить таблицу MIB, указав длину данных, так как агент SNMP проанализировал данные и знает их тип и длину:</span><span class="sxs-lookup"><span data-stu-id="e64a6-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="e64a6-290">Если функции обратного вызова не удается найти запрошенный объект, должен возвращаться код ошибки **NX_SNMP_ERROR_NOSUCHNAME**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="e64a6-291">Если узел SNMP NetX Duo создал закрытые строки сообщества, а SNMP-отправитель запроса SET не имеет совпадающей закрытой строки, то может возвращаться ошибка **NX_SNMP_ERROR_NOACCESS**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="e64a6-292">Если обнаружена какая-либо другая ошибка, возвращается **NX_SNMP_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="e64a6-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="e64a6-293">*Несмотря на то, что агент SNMP NetX Duo предоставляет базу данных MIB SNMP вместе с дистрибутивом, она предназначен главным образом для тестирования и разработки. Разработчику, скорее всего, потребуется собственная база данных MIB для профессионального использования SNMP.*</span><span class="sxs-lookup"><span data-stu-id="e64a6-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="e64a6-294">Изменение версии SNMP во время выполнения</span><span class="sxs-lookup"><span data-stu-id="e64a6-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="e64a6-295">Узел агента SNMP может изменить версию SNMP на любую из трех версий во время выполнения с помощью службы *nx_snmp_agent_set_version*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="e64a6-296">По умолчанию агент SNMP включен для работы со всеми тремя версиями при его создании в *nx_snmp_agent_create*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="e64a6-297">Однако приложение может ограничить использование некоторым подмножеством версий.</span><span class="sxs-lookup"><span data-stu-id="e64a6-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="e64a6-298">*Если определены параметры конфигурации NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 и (или) NX_SNMP_DISABLE_V3, эта функция не сможет включить соответствующие версии.*</span><span class="sxs-lookup"><span data-stu-id="e64a6-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="e64a6-299">Агент SNMP может получить версию SNMP последнего полученного пакета SNMP с помощью службы *nx_snmp_agent_get_current_version*.</span><span class="sxs-lookup"><span data-stu-id="e64a6-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="e64a6-300">Обнаружение SNMPv3</span><span class="sxs-lookup"><span data-stu-id="e64a6-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="e64a6-301">Агент SNMP, если у него включена поддержка SNMPv3, будет отвечать на запросы обнаружения от диспетчера SNMP.</span><span class="sxs-lookup"><span data-stu-id="e64a6-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="e64a6-302">Такой запрос содержит данные параметров безопасности со значениями NULL для идентификатора подсистемы авторизации, имени пользователя, количества загрузки и времени загрузки.</span><span class="sxs-lookup"><span data-stu-id="e64a6-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="e64a6-303">Параметры проверки подлинности не применяются к сообщению обнаружения DISCOVERY.</span><span class="sxs-lookup"><span data-stu-id="e64a6-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="e64a6-304">Список привязок переменных в таком запросе пуст (не содержит элементов).</span><span class="sxs-lookup"><span data-stu-id="e64a6-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="e64a6-305">Агент SNMP реагирует с нулевым временем и количеством загрузок, а также списком привязок переменных, содержащим 1 элемент *usmStatsUnknownEngineIDs*, который представляет собой количество запросов, полученных с неизвестным идентификатором подсистемы (null).</span><span class="sxs-lookup"><span data-stu-id="e64a6-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="e64a6-306">В последующем запросе GETNEXT от обозревателя или диспетчера параметры данных загрузки и параметры безопасности заполняются только в том случае, если включена безопасность.</span><span class="sxs-lookup"><span data-stu-id="e64a6-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="e64a6-307">Если безопасность включена, то также будет отправлено обновление данных NotInTime в PDU.</span><span class="sxs-lookup"><span data-stu-id="e64a6-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="e64a6-308">Параметры безопасности, например проверка подлинности, подтверждают личность агента для диспетчера.</span><span class="sxs-lookup"><span data-stu-id="e64a6-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="e64a6-309">Более подробные сведения о проверке подлинности SNMPv3 доступны в документе RFC 3414 "Модель безопасности на основе пользователей (USM) для версии 3 протокола простого сетевого управления (SNMPv3)".</span><span class="sxs-lookup"><span data-stu-id="e64a6-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="e64a6-310">Документы RFC для SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="e64a6-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="e64a6-311">Протокол SNMP NetX Duo совместим с RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC3414 и связанными с ними документами RFC.</span><span class="sxs-lookup"><span data-stu-id="e64a6-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
