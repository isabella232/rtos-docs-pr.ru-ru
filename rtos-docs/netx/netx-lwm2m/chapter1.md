---
title: Глава 1. Введение в ОСРВ Azure NetX LWM2M
description: Протокол ОСРВ Azure NetX LWM2M реализует клиентскую часть для стандарта LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fe9c90ec10b241c72c71882b28b5fe0e3e60e3913435ec27f797eade4ca4eca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784926"
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