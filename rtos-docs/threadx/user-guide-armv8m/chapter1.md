---
title: Глава 1. Общие сведения об ОСРВ Azure ThreadX для ARMv8-M.
description: Эта глава является отправной точкой для ознакомления с дополнением ОСРВ Azure ThreadX для ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f0d87ec562c7fcfa6af5d2240655ef526f6e0611d509fe60c745436371413d7
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798254"
---
# <a name="chapter-1--overview"></a>Глава 1. Общие сведения

В архитектуре ARMv8-M содержатся новые функции безопасности, в том числе TrustZone, позволяющие помечать память как безопасную или небезопасную. Согласно рекомендациям ARM, ThreadX (и пользовательское приложение) предназначены для запуска в небезопасном режиме. ThreadX (и пользовательское приложение) можно также запускать в безопасном режиме. Для взаимодействия с программным обеспечением безопасного режима необходимы некоторые новые API-интерфейсы ThreadX. В этом документе описаны службы ThreadX, относящиеся к архитектуре ARMv8-M, в частности Cortex-M23, Cortex-M33, Cortex-M35P и Cortex-M55.
