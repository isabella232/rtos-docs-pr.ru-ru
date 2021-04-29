---
title: Глава 1. Введение в ОСРВ Azure NetX Duo BSD
description: Программа-оболочка соответствия API сокетов BSD поддерживает часть базовых вызовов API сокетов BSD (с некоторыми ограничениями) при помощи примитивов ОСРВ Azure NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e89018dffd2f9f9065efab2ecabdf4364c4f89a3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814827"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a>Глава 1. Введение в ОСРВ Azure NetX Duo BSD

Программа-оболочка соответствия API сокетов BSD поддерживает часть базовых вызовов API сокетов BSD (с некоторыми ограничениями) при помощи примитивов ОСРВ Azure NetX Duo.

## <a name="bsd-socket-api-compliancy-wrapper-source"></a>Исходный код программы-оболочки для обеспечения соответствия API сокетов BSD

Исходный код программы-оболочки BSD специально создавался простым, он размещен всего в двух файлах: *nx_bsd.h* и *nx_bsd.c*. Файл *nx_bsd.h* определяет все необходимые константы и прототипы подпрограмм программы-оболочки API сокетов BSD, а *nx_bsd.c* содержит фактический исходный код для обеспечения совместимости API сокетов BSD. Такие файлы исходного кода программы-оболочки присутствуют во всех пакетах поддержки NetX Duo.

В этот пакет входит следующее:

- **nxd_bsd.c**: исходный код программы-оболочки;
- **nxd_bsd.h**: основной файл заголовка.

Примеры демонстрационных программ:

- **bsd_demo_udp. c**: *демонстрационный файл с двумя одноранговыми узлами UDP (только IPv4)* ;
- **bsd_demo_tcp.c**: *демонстрационный файл с одним TCP-сервером и TCP-клиентом*;
- **bsd_demo_raw. c**: *демонстрационный файл с двумя одноранговыми узлами RAW*.