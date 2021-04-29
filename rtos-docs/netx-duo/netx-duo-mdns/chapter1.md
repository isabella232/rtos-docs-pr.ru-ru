---
title: Глава 1. Введение в mDNS/DNS-SD в NetX Duo для ОСРВ Azure
description: mDNS/DNS-SD в NetX Duo для ОСРВ Azure дополняет традиционную службу DNS.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b46539ee4d502fa4c90fb3392e25cd3bee40dc5b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814671"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a><span data-ttu-id="a3fc9-103">Глава 1. Введение в mDNS/DNS-SD в NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="a3fc9-103">Chapter 1 - Introduction to Azure RTOS NetX Duo mDNS/DNS-SD</span></span>

<span data-ttu-id="a3fc9-104">mDNS и DNS-SD — это протоколы, разработанные для дополнения традиционной службы DNS.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-104">The mDNS and DNS-SD are protocols designed to augment the traditional DNS service.</span></span> <span data-ttu-id="a3fc9-105">mDNS предоставляет имя узла и поиск службы для узлов в локальной сети.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-105">mDNS provides host name and service lookup to the nodes on the local network.</span></span> <span data-ttu-id="a3fc9-106">Каждый узел использует многоадресный канал IPv4 или IPv6 для объявления служб, которые он предлагает соседним узлам, отвечает на запросы от соседних узлов и отправляет запросы от имени своих приложений.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-106">Each node uses IPv4 or IPv6 multicast channel to announce services it offers to its neighbors, responds to queries from its neighbors, and sends queries on behave of its applications.</span></span> <span data-ttu-id="a3fc9-107">Изначально mDNS работает в распределенной среде, благодаря чему исключается централизованное обслуживание.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-107">By design, mDNS operates in a distributed environment, thus eliminates a centralized serve.</span></span>

<span data-ttu-id="a3fc9-108">Протокол DNS-SD основан на mDNS.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-108">DNS-SD is built on top of mDNS.</span></span> <span data-ttu-id="a3fc9-109">Он позволяет узлам объявлять службы, которые они предоставляют локальной сети, или обнаруживать службы, предлагаемые другими узлами в локальной сети.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-109">DNS-SD allows nodes to announce services they provide to the local network or to discover services offered by other nodes on the local network.</span></span> <span data-ttu-id="a3fc9-110">В документации под термином *mDNS* понимаются службы, которые охватываются как спецификацией mDNS, так и спецификацией DNS-SD.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-110">Throughout the document, the term *mDNS* refers to the services that cover both the mDNS specification and the DNS-SD specification.</span></span>

## <a name="mdns-standard"></a><span data-ttu-id="a3fc9-111">Стандарт mDNS</span><span class="sxs-lookup"><span data-stu-id="a3fc9-111">mDNS Standard</span></span>

<span data-ttu-id="a3fc9-112">Реализация протоколов mDNS и DNS-SD в NetX Duo соответствует следующим документам RFC.</span><span class="sxs-lookup"><span data-stu-id="a3fc9-112">NetX Duo mDNS/DNS-SD implementation conforms to the following RFCs:</span></span>

- <span data-ttu-id="a3fc9-113">RFC 6762. Спецификация mDNS</span><span class="sxs-lookup"><span data-stu-id="a3fc9-113">RFC 6762: mDNS Specification</span></span>
- <span data-ttu-id="a3fc9-114">RFC 6763. Спецификация DNS-SD</span><span class="sxs-lookup"><span data-stu-id="a3fc9-114">RFC 6763: DNS-SD Specification</span></span>