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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mdnsdns-sd"></a>Глава 1. Введение в mDNS/DNS-SD в NetX Duo для ОСРВ Azure

mDNS и DNS-SD — это протоколы, разработанные для дополнения традиционной службы DNS. mDNS предоставляет имя узла и поиск службы для узлов в локальной сети. Каждый узел использует многоадресный канал IPv4 или IPv6 для объявления служб, которые он предлагает соседним узлам, отвечает на запросы от соседних узлов и отправляет запросы от имени своих приложений. Изначально mDNS работает в распределенной среде, благодаря чему исключается централизованное обслуживание.

Протокол DNS-SD основан на mDNS. Он позволяет узлам объявлять службы, которые они предоставляют локальной сети, или обнаруживать службы, предлагаемые другими узлами в локальной сети. В документации под термином *mDNS* понимаются службы, которые охватываются как спецификацией mDNS, так и спецификацией DNS-SD.

## <a name="mdns-standard"></a>Стандарт mDNS

Реализация протоколов mDNS и DNS-SD в NetX Duo соответствует следующим документам RFC.

- RFC 6762. Спецификация mDNS
- RFC 6763. Спецификация DNS-SD