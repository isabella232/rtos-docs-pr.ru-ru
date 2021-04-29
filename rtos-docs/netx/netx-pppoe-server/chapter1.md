---
title: Глава 1. Введение в PPPoE-сервер NetX для ОСРВ Azure
description: В этом документе рассматриваются сведения о модуле PPPoE NetX в ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85a762f669e31c7e753f78b270ced15677a87c4c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815127"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="6b0c1-103">Глава 1. Введение в PPPoE-сервер NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="6b0c1-103">Chapter 1 - Introduction to Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="6b0c1-104">PPP через Ethernet (PPPoE) позволяет узлам подключаться к PPP-серверу через Ethernet, а не по стандартному каналу связи на основе символов.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-104">PPP over Ethernet (PPPoE) allows hosts to connect to PPP server via Ethernet instead of the traditional character-based serial line communication.</span></span> <span data-ttu-id="6b0c1-105">Технические сведения о протоколе PPPoE описаны в документе RFC 2516, "Метод передачи PPP через Ethernet (PPPoE)".</span><span class="sxs-lookup"><span data-stu-id="6b0c1-105">The technical details of PPPoE are described in RFC 2516: A Method for Transmitting PPP over Ethernet (PPPoE).</span></span> <span data-ttu-id="6b0c1-106">В этом документе рассматриваются сведения о модуле PPPoE NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-106">This document focuses on the details of Azure RTOS NetX PPPoE module.</span></span>

<span data-ttu-id="6b0c1-107">Чтобы обеспечить подключение типа "точка — точка" через Ethernet, каждый сеанс PPP должен знать адрес Ethernet удаленного кэширующего узла, а также установить уникальный идентификатор сеанса.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-107">To provide a point-to-point connection over Ethernet, each PPP session must learn the Ethernet address of the remote peer, as well as establish a unique session identifier.</span></span>

<span data-ttu-id="6b0c1-108">Согласно стандарту RFC 2516, PPPoE состоит из двух этапов: этапа обнаружения и этапа сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-108">According to RFC 2516, PPPoE consists of two stages: the Discovery stage, and PPPoE Session stage.</span></span> <span data-ttu-id="6b0c1-109">Когда узлу (клиенту) нужно начать сеанс PPP, он должен сначала выполнить обнаружение для поиска сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-109">When a host (client) wishes to start a PPP session, it must first perform Discovery to find PPPoE server.</span></span> <span data-ttu-id="6b0c1-110">Этот шаг также позволяет серверу и клиенту определить MAC-адрес Ethernet и SESSION_ID друг друга, которые будут использоваться в оставшейся части сеанса PPP.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-110">This step also allows the server and the client to identify each other's Ethernet MAC address and SESSION_ID, which will be used for the rest of the PPP session.</span></span>

<span data-ttu-id="6b0c1-111">Кадр Ethernet выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-111">An Ethernet frame is as follows:</span></span>

![Схема кадра Ethernet.](media/netx-pppoe-server-01.png)

<span data-ttu-id="6b0c1-113">Полезные данные Ethernet для протокола PPPoE</span><span class="sxs-lookup"><span data-stu-id="6b0c1-113">The Ethernet payload for PPPoE is as follows:</span></span>

![Схема полезных данных Ethernet для PPPoE](media/netx-pppoe-server-02.png)

## <a name="pppoe-discovery-stage"></a><span data-ttu-id="6b0c1-115">Этап обнаружения PPPoE</span><span class="sxs-lookup"><span data-stu-id="6b0c1-115">PPPoE Discovery Stage</span></span>

<span data-ttu-id="6b0c1-116">На этапе обнаружения PPPoE клиенты могут выбрать сервер из всех доступных серверов в сети, чтобы создать сеанс до обмена кадрами PPP.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-116">The PPPoE Discovery stage allows clients to select a server from all available servers on the network, effectively to create a session prior to PPP frames being exchanged.</span></span> <span data-ttu-id="6b0c1-117">В конце этапа обнаружения клиент и сервер должны согласовать подключение с помощью уникального ИД сеанса и обеим сторонам необходимо знать MAC-адреса друг друга.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-117">At the end of the discovery stage, both the client and the server shall agree on a unique session ID, and both sides need to know peer's MAC address.</span></span>

| <span data-ttu-id="6b0c1-118">Сообщение обнаружения</span><span class="sxs-lookup"><span data-stu-id="6b0c1-118">Discovery Message</span></span>                                  | <span data-ttu-id="6b0c1-119">Код</span><span class="sxs-lookup"><span data-stu-id="6b0c1-119">Code</span></span> | <span data-ttu-id="6b0c1-120">Направление</span><span class="sxs-lookup"><span data-stu-id="6b0c1-120">Direction</span></span>                                     |
| -------------------------------------------------- | ---- | --------------------------------------------- |
| <span data-ttu-id="6b0c1-121">Инициация активного обнаружения PPPoE (PADI)</span><span class="sxs-lookup"><span data-stu-id="6b0c1-121">PPPoE Active Discovery Initiation (PADI)</span></span>           | <span data-ttu-id="6b0c1-122">0x09</span><span class="sxs-lookup"><span data-stu-id="6b0c1-122">0x09</span></span> | <span data-ttu-id="6b0c1-123">От клиента к широковещательной рассылке</span><span class="sxs-lookup"><span data-stu-id="6b0c1-123">From Client to broadcast</span></span>                      |
| <span data-ttu-id="6b0c1-124">Предложение активного обнаружения PPPoE (PADO)</span><span class="sxs-lookup"><span data-stu-id="6b0c1-124">PPPoE Active Discovery Offer (PADO)</span></span>                | <span data-ttu-id="6b0c1-125">0x07</span><span class="sxs-lookup"><span data-stu-id="6b0c1-125">0x07</span></span> | <span data-ttu-id="6b0c1-126">От сервера к клиенту</span><span class="sxs-lookup"><span data-stu-id="6b0c1-126">From Server to Client</span></span>                         |
| <span data-ttu-id="6b0c1-127">Запрос на активное обнаружение PPPoE (PADR)</span><span class="sxs-lookup"><span data-stu-id="6b0c1-127">PPPoE Active Discovery Request (PADR)</span></span>              | <span data-ttu-id="6b0c1-128">0x19</span><span class="sxs-lookup"><span data-stu-id="6b0c1-128">0x19</span></span> | <span data-ttu-id="6b0c1-129">От клиента к серверу</span><span class="sxs-lookup"><span data-stu-id="6b0c1-129">From Client to Server</span></span>                         |
| <span data-ttu-id="6b0c1-130">Подтверждение сеанса активного обнаружения PPPOE (PADS)</span><span class="sxs-lookup"><span data-stu-id="6b0c1-130">PPPOE Active Discovery Session-confirmation (PADS)</span></span> | <span data-ttu-id="6b0c1-131">0x65</span><span class="sxs-lookup"><span data-stu-id="6b0c1-131">0x65</span></span> | <span data-ttu-id="6b0c1-132">От сервера к клиенту</span><span class="sxs-lookup"><span data-stu-id="6b0c1-132">From Server to Client</span></span>                         |
| <span data-ttu-id="6b0c1-133">Завершение активного обнаружения PPPoE (PADT)</span><span class="sxs-lookup"><span data-stu-id="6b0c1-133">PPPoE Active Discovery Terminate (PADT)</span></span>            | <span data-ttu-id="6b0c1-134">0xa7</span><span class="sxs-lookup"><span data-stu-id="6b0c1-134">0xa7</span></span> | <span data-ttu-id="6b0c1-135">Может быть инициировано как с сервера, так и с клиента</span><span class="sxs-lookup"><span data-stu-id="6b0c1-135">Can be initiated from either server or client</span></span> |

<span data-ttu-id="6b0c1-136">Во всех кадрах обнаружения Ethernet в поле ETHER_TYPE указано значение 0x8863.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-136">All Discovery Ethernet frames have the ETHER_TYPE field set to the value 0x8863.</span></span>

## <a name="pppoe-session-message"></a><span data-ttu-id="6b0c1-137">Сообщение сеанса PPPoE</span><span class="sxs-lookup"><span data-stu-id="6b0c1-137">PPPoE Session Message</span></span>

<span data-ttu-id="6b0c1-138">После того как клиент и сервер создали сеанс, кадры PPP могут передаваться как сообщения сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-138">After the client and the server create a session, PPP frames can be transferred as PPPoE Session messages.</span></span> <span data-ttu-id="6b0c1-139">Во время сеанса SESSION_ID не должен изменяться и должен быть значением, назначенным сервером на этапе обнаружения.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-139">During a session, the SESSION_ID must not change and must be the value the server assigned during the Discovery stage.</span></span>

<span data-ttu-id="6b0c1-140">Для всех кадров Ethernet сеанса PPPoE для поля ETHER_TYPE задано значение 0x8864.</span><span class="sxs-lookup"><span data-stu-id="6b0c1-140">All PPPoE Session Ethernet frames have the ETHER_TYPE field set to the value 0x8864.</span></span>