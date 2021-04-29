---
title: Глава 1. Введение в ОСРВ Azure NetX LWM2M
description: Протокол ОСРВ Azure NetX LWM2M реализует клиентскую часть для стандарта LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c29af430975266eed684bd1de38d9e5d7e2586a6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815192"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a><span data-ttu-id="ebf19-103">Глава 1. Введение в ОСРВ Azure NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="ebf19-103">Chapter 1 - Introduction to Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="ebf19-104">Протокол ОСРВ Azure NetX LWM2M реализует клиентскую часть для стандарта LWM2M.</span><span class="sxs-lookup"><span data-stu-id="ebf19-104">The Azure RTOS NetX LWM2M Protocol implements the client part of the Lightweight Machine to Machine protocol standard.</span></span>

## <a name="netx-lwm2m-requirements"></a><span data-ttu-id="ebf19-105">Требования для протокола NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="ebf19-105">NetX LWM2M Requirements</span></span>

<span data-ttu-id="ebf19-106">Для правильной работы библиотеки времени выполнения NetX LWM2M требуется, чтобы экземпляр NetX IP уже был создан.</span><span class="sxs-lookup"><span data-stu-id="ebf19-106">In order to function properly, the NetX LWM2M run-time library requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="ebf19-107">Пакет NetX LWM2M не имеет дополнительных требований.</span><span class="sxs-lookup"><span data-stu-id="ebf19-107">The NetX LWM2M package has no further requirements.</span></span>

## <a name="netx-lwm2m-rfcs"></a><span data-ttu-id="ebf19-108">Соответствие NetX LWM2M спецификациям RFC</span><span class="sxs-lookup"><span data-stu-id="ebf19-108">NetX LWM2M RFCs</span></span>

<span data-ttu-id="ebf19-109">Протокол NetX LWM2M соответствует требованиям стандарта OMA-TS-LightweightM2M-V1_0-20170208-A и приведенных ниже спецификаций RFC, связанных с протоколом CoAP.</span><span class="sxs-lookup"><span data-stu-id="ebf19-109">NetX LWM2M is compliant with OMA-TS-LightweightM2M-V1_0-20170208-A and the following RFCs related to the Constrained Application Protocol (CoAP):</span></span>

- <span data-ttu-id="ebf19-110">**RFC 7252**: протокол ограниченного применения (CoAP).</span><span class="sxs-lookup"><span data-stu-id="ebf19-110">**RFC 7252**: The Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="ebf19-111">**RFC 7641**: наблюдение за ресурсами в протоколе ограниченного применения (CoAP).</span><span class="sxs-lookup"><span data-stu-id="ebf19-111">**RFC 7641**: Observing Resources in the Constrained Application Protocol (CoAP)</span></span>

- <span data-ttu-id="ebf19-112">**RFC 6690**: формат ссылок для ограниченных сред RESTful (CoRE).</span><span class="sxs-lookup"><span data-stu-id="ebf19-112">**RFC 6690**: Constrained RESTful Environments (CoRE) Link Format</span></span>