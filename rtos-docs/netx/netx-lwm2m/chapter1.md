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
# <a name="chapter-1---introduction-to-azure-rtos-netx-lwm2m"></a>Глава 1. Введение в ОСРВ Azure NetX LWM2M

Протокол ОСРВ Azure NetX LWM2M реализует клиентскую часть для стандарта LWM2M.

## <a name="netx-lwm2m-requirements"></a>Требования для протокола NetX LWM2M

Для правильной работы библиотеки времени выполнения NetX LWM2M требуется, чтобы экземпляр NetX IP уже был создан. Пакет NetX LWM2M не имеет дополнительных требований.

## <a name="netx-lwm2m-rfcs"></a>Соответствие NetX LWM2M спецификациям RFC

Протокол NetX LWM2M соответствует требованиям стандарта OMA-TS-LightweightM2M-V1_0-20170208-A и приведенных ниже спецификаций RFC, связанных с протоколом CoAP.

- **RFC 7252**: протокол ограниченного применения (CoAP).

- **RFC 7641**: наблюдение за ресурсами в протоколе ограниченного применения (CoAP).

- **RFC 6690**: формат ссылок для ограниченных сред RESTful (CoRE).