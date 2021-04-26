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
# <a name="chapter-1--overview"></a>Глава 1. Общие сведения

В архитектуре ARMv8-M содержатся новые функции безопасности, в том числе TrustZone, позволяющие помечать память как безопасную или небезопасную. Согласно рекомендациям ARM, ThreadX (и пользовательское приложение) предназначены для запуска в небезопасном режиме. ThreadX (и пользовательское приложение) можно также запускать в безопасном режиме. Для взаимодействия с программным обеспечением безопасного режима необходимы некоторые новые API-интерфейсы ThreadX. В этом документе описаны службы ThreadX, относящиеся к архитектуре ARMv8-M, в частности Cortex-M23, Cortex-M33, Cortex-M35P и Cortex-M55.
