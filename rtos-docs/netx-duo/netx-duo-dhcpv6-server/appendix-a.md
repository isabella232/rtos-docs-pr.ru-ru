---
title: Приложение А. Коды параметров DHCPv6 в NetX Duo для ОСРВ Azure
description: В этой главе приведено описание всех кодов параметров DHCPv6 в NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 36d673c34479ec2d476eeaa094c0dc02714ee010
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814763"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a><span data-ttu-id="a5055-103">Приложение А. Коды параметров DHCPv6 в NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="a5055-103">Appendix A – Azure RTOS NetX Duo DHCPv6 option codes</span></span>

| <span data-ttu-id="a5055-104">Параметр</span><span class="sxs-lookup"><span data-stu-id="a5055-104">Option</span></span>              | <span data-ttu-id="a5055-105">Код</span><span class="sxs-lookup"><span data-stu-id="a5055-105">Code</span></span>            | <span data-ttu-id="a5055-106">Описание</span><span class="sxs-lookup"><span data-stu-id="a5055-106">Description</span></span> |
| ------------------- | ------------------- | --------------- |
| <span data-ttu-id="a5055-107">Идентификатор DUID клиента</span><span class="sxs-lookup"><span data-stu-id="a5055-107">Client Identifier DUID</span></span> | <span data-ttu-id="a5055-108">1</span><span class="sxs-lookup"><span data-stu-id="a5055-108">1</span></span> | <span data-ttu-id="a5055-109">Уникальный идентификатор узла клиента в сети</span><span class="sxs-lookup"><span data-stu-id="a5055-109">Uniquely identifies a Client host on the network</span></span> |
| <span data-ttu-id="a5055-110">Идентификатор сервера (DUID)</span><span class="sxs-lookup"><span data-stu-id="a5055-110">Server Identifier (DUID)</span></span> | <span data-ttu-id="a5055-111">2</span><span class="sxs-lookup"><span data-stu-id="a5055-111">2</span></span> | <span data-ttu-id="a5055-112">Уникальный идентификатор узла DHCPv6-сервера в сети</span><span class="sxs-lookup"><span data-stu-id="a5055-112">Uniquely identifies the DHCPv6Server host on the network</span></span> |
| <span data-ttu-id="a5055-113">Ассоциация удостоверений для невременных адресов (IANA)</span><span class="sxs-lookup"><span data-stu-id="a5055-113">Identity Association for Non Temporary Addresses (IANA)</span></span> | <span data-ttu-id="a5055-114">3</span><span class="sxs-lookup"><span data-stu-id="a5055-114">3</span></span> | <span data-ttu-id="a5055-115">Параметры для назначения невременного IP-адреса</span><span class="sxs-lookup"><span data-stu-id="a5055-115">Parameters for a non temporary IP address assignment</span></span> |
| <span data-ttu-id="a5055-116">Ассоциация удостоверений для временных адресов (IATA)</span><span class="sxs-lookup"><span data-stu-id="a5055-116">Identity Association for Temporary Addresses (IATA)</span></span> | <span data-ttu-id="a5055-117">4</span><span class="sxs-lookup"><span data-stu-id="a5055-117">4</span></span> | <span data-ttu-id="a5055-118">Параметры для назначения временного IP-адреса</span><span class="sxs-lookup"><span data-stu-id="a5055-118">Parameters for a temporary IP address assignment</span></span> |
| <span data-ttu-id="a5055-119">Адрес IA</span><span class="sxs-lookup"><span data-stu-id="a5055-119">IA Address</span></span> | <span data-ttu-id="a5055-120">5</span><span class="sxs-lookup"><span data-stu-id="a5055-120">5</span></span> | <span data-ttu-id="a5055-121">Фактический IPv6-адрес, назначаемый клиенту, и время его существования</span><span class="sxs-lookup"><span data-stu-id="a5055-121">Actual IPv6 address and IPv6 address lifetimes to be assigned to the Client</span></span> |
| <span data-ttu-id="a5055-122">Запрос параметра</span><span class="sxs-lookup"><span data-stu-id="a5055-122">Option Request</span></span> | <span data-ttu-id="a5055-123">6</span><span class="sxs-lookup"><span data-stu-id="a5055-123">6</span></span> | <span data-ttu-id="a5055-124">Список информационных запросов для получения сведений о сети, таких как DNS-сервер и другие параметры конфигурации сети.</span><span class="sxs-lookup"><span data-stu-id="a5055-124">A list of information requests to obtain network information such as DNS server and other network configuration parameters.</span></span> |
| <span data-ttu-id="a5055-125">Предпочтение</span><span class="sxs-lookup"><span data-stu-id="a5055-125">Preference</span></span> | <span data-ttu-id="a5055-126">7</span><span class="sxs-lookup"><span data-stu-id="a5055-126">7</span></span> | <span data-ttu-id="a5055-127">Включается в серверное сообщение объявления, которое отправляется клиенту и влияет на выбор им серверов.</span><span class="sxs-lookup"><span data-stu-id="a5055-127">Included in server Advertise message to client to influence the Client’s choice of servers.</span></span> <span data-ttu-id="a5055-128">Клиент должен выбрать сервер с более высоким значением приоритета, чем у других серверов.</span><span class="sxs-lookup"><span data-stu-id="a5055-128">The Client must choose a server with higher the preference value over other servers.</span></span> <span data-ttu-id="a5055-129">255 — максимальное значение, а 0 означает, что клиент может выбрать любой ответивший ему сервер.</span><span class="sxs-lookup"><span data-stu-id="a5055-129">255 is the maximum value, while zero indicates the client can choose any server replying back to them</span></span> |
| <span data-ttu-id="a5055-130">Затраченное время</span><span class="sxs-lookup"><span data-stu-id="a5055-130">Elapsed Time</span></span> | <span data-ttu-id="a5055-131">8</span><span class="sxs-lookup"><span data-stu-id="a5055-131">8</span></span> | <span data-ttu-id="a5055-132">Содержит время (с шагом в 0,01 секунды), когда клиент инициирует обмен данными с сервером по протоколу DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a5055-132">Contains the time (in 0.01 seconds) when the Client initiates the DHCPv6 exchange with the server.</span></span> <span data-ttu-id="a5055-133">Используется серверами-получателями для определения того, отвечает ли сервер-источник на запрос клиента вовремя.</span><span class="sxs-lookup"><span data-stu-id="a5055-133">Used by secondary server(s) to determine if the primary server responds in time to the Client request.</span></span> |
| <span data-ttu-id="a5055-134">Сообщение ретрансляции</span><span class="sxs-lookup"><span data-stu-id="a5055-134">Relay Message</span></span> | <span data-ttu-id="a5055-135">9</span><span class="sxs-lookup"><span data-stu-id="a5055-135">9</span></span> | <span data-ttu-id="a5055-136">Содержит исходное сообщение в сообщении ретрансляции.</span><span class="sxs-lookup"><span data-stu-id="a5055-136">Contains the original message in Relay message</span></span> | 
| <span data-ttu-id="a5055-137">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="a5055-137">Authentication</span></span> | <span data-ttu-id="a5055-138">11</span><span class="sxs-lookup"><span data-stu-id="a5055-138">11</span></span> | <span data-ttu-id="a5055-139">Содержит сведения для проверки подлинности удостоверений и содержимого сообщений DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="a5055-139">Contains information to authenticate the identity and content of DHCPv6 messages</span></span> |
| <span data-ttu-id="a5055-140">Одноадресное взаимодействие с сервером</span><span class="sxs-lookup"><span data-stu-id="a5055-140">Server Unicast</span></span> | <span data-ttu-id="a5055-141">12</span><span class="sxs-lookup"><span data-stu-id="a5055-141">12</span></span> | <span data-ttu-id="a5055-142">Сервер отправляет этот параметр, чтобы сообщить клиенту о том, что он будет принимать одноадресные сообщения непосредственно от клиента, а не многоадресные сообщения.</span><span class="sxs-lookup"><span data-stu-id="a5055-142">Server sends this option to let the Client know that the server will accept unicast messages directly from the Client instead of multicast.</span></span> |

<span data-ttu-id="a5055-143">Параметры IATA, сообщения ретрансляции, проверки подлинности и одноадресного взаимодействия с сервером не поддерживаются в этом выпуске DHCPv6-сервера NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="a5055-143">IATA, Relay Message, Authentication and Server Unicast options are not supported in this release of NetX Duo DHCPv6 Server.</span></span> <span data-ttu-id="a5055-144">Текущий код параметра протокола DHCPv6 10 остается неопределенным в RFC 3315.</span><span class="sxs-lookup"><span data-stu-id="a5055-144">The current DHCPv6 protocol option code 10 is left undefined in RFC 3315.</span></span>