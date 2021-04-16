---
title: Глава 1. Введение в LWM2M-клиент в NetX Duo для ОСРВ Azure
description: В этой главе приведены основные сведения об клиенте протокола LWM2M в NetX Duo для ОСРВ Azure.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 12f13c154668b3cadfae0924e59b55631dc27424
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814691"
---
# <a name="chapter-1--introduction-to-lwm2m-client"></a><span data-ttu-id="13ad7-103">Глава 1. Введение в LWM2M-клиент</span><span class="sxs-lookup"><span data-stu-id="13ad7-103">Chapter 1  Introduction to LWM2M Client</span></span>

<span data-ttu-id="13ad7-104">Протокол LWM2M-клиента в NetX Duo для ОСРВ Azure реализует клиентскую часть для стандарта LWM2M.</span><span class="sxs-lookup"><span data-stu-id="13ad7-104">The Azure RTOS NetX Duo LWM2M Client Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span> <span data-ttu-id="13ad7-105">(LWM2M 1.0-20170208A)</span><span class="sxs-lookup"><span data-stu-id="13ad7-105">(LWM2M 1.0-20170208A)</span></span>

## <a name="netx-lwm2m-client-requirements"></a><span data-ttu-id="13ad7-106">Требования к LWM2M-клиенту в NetX</span><span class="sxs-lookup"><span data-stu-id="13ad7-106">NetX LWM2M Client Requirements</span></span>

<span data-ttu-id="13ad7-107">Для правильной работы библиотеки времени выполнения LWM2M-клиента требуется, чтобы экземпляр NetX IP уже был создан.</span><span class="sxs-lookup"><span data-stu-id="13ad7-107">In order to function properly, the LWM2M Client run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="13ad7-108">Пакет LWM2M-клиента в NetX не имеет дополнительных требований.</span><span class="sxs-lookup"><span data-stu-id="13ad7-108">The NetX LWM2M Client package has no further requirements.</span></span>

## <a name="netx-lwm2m-client-rfcs"></a><span data-ttu-id="13ad7-109">Стандарты RFC для LWM2M-клиента в NetX</span><span class="sxs-lookup"><span data-stu-id="13ad7-109">NetX LWM2M Client RFCs</span></span>

<span data-ttu-id="13ad7-110">LWM2M-клиент совместим со стандартом OMA-TS-LightweightM2M-V1\_0-20170208-A и следующими RFC, связанными с протоколом CoAP.</span><span class="sxs-lookup"><span data-stu-id="13ad7-110">LWM2M Client is compliant with OMA-TS-LightweightM2M-V1\_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP).</span></span>

* <span data-ttu-id="13ad7-111">RFC 7252 "Протокол ограниченного применения (CoAP)".</span><span class="sxs-lookup"><span data-stu-id="13ad7-111">RFC 7252 The Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="13ad7-112">RFC 7641 Наблюдение за ресурсами в протоколе ограниченного применения (CoAP)".</span><span class="sxs-lookup"><span data-stu-id="13ad7-112">RFC 7641 Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

* <span data-ttu-id="13ad7-113">RFC 6690 "Формат ссылок для ограниченных сред RESTful (CoRE)".</span><span class="sxs-lookup"><span data-stu-id="13ad7-113">RFC 6690 Constrained RESTful Environments (CoRE) Link Format</span></span>

<span data-ttu-id="13ad7-114">Дополнительные сведения см. на странице [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span><span class="sxs-lookup"><span data-stu-id="13ad7-114">For more information, please see [OMA-TS-LightweightM2M-V1\_0-2017208-A](http://www.openmobilealliance.org/release/LightweightM2M/V1_0-20170208-A/OMA-TS-LightweightM2M-V1_0-20170208-A.pdf).</span></span>