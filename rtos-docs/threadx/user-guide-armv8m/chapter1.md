---
title: Глава 1. Общие сведения об ОСРВ Azure ThreadX для ARMv8-M.
description: Эта глава является отправной точкой для ознакомления с дополнением ОСРВ Azure ThreadX для ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 486466f41e64adb9e32ebbd21a22629221ffa9c1
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377538"
---
# <a name="chapter-1--overview"></a><span data-ttu-id="0010d-103">Глава 1. Общие сведения</span><span class="sxs-lookup"><span data-stu-id="0010d-103">Chapter 1  Overview</span></span>

<span data-ttu-id="0010d-104">В архитектуре ARMv8-M содержатся новые функции безопасности, в том числе TrustZone, позволяющие помечать память как безопасную или небезопасную.</span><span class="sxs-lookup"><span data-stu-id="0010d-104">The ARMv8-M architecture introduces new security features, including TrustZone, which allows memory to be tagged as secure or non-secure.</span></span> <span data-ttu-id="0010d-105">Согласно рекомендациям ARM, ThreadX (и пользовательское приложение) предназначены для запуска в небезопасном режиме.</span><span class="sxs-lookup"><span data-stu-id="0010d-105">Following ARM's guidelines, ThreadX (and the user application) is designed to be run in non-secure mode.</span></span> <span data-ttu-id="0010d-106">ThreadX (и пользовательское приложение) можно также запускать в безопасном режиме.</span><span class="sxs-lookup"><span data-stu-id="0010d-106">ThreadX (and the user application) can also be run in secure mode.</span></span> <span data-ttu-id="0010d-107">Для взаимодействия с программным обеспечением безопасного режима необходимы некоторые новые API-интерфейсы ThreadX.</span><span class="sxs-lookup"><span data-stu-id="0010d-107">In order to interface with secure mode software, some new ThreadX APIs are necessary.</span></span> <span data-ttu-id="0010d-108">В этом документе описаны службы ThreadX, относящиеся к архитектуре ARMv8-M, в частности Cortex-M23, Cortex-M33, Cortex-M35P и Cortex-M55.</span><span class="sxs-lookup"><span data-stu-id="0010d-108">This document describes these ThreadX services that are specific to the ARMv8-M architecture, including the Cortex-M23, Cortex-M33, Cortex-M35P, and Cortex-M55.</span></span>
