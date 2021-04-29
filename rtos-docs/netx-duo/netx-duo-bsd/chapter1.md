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
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="2bc8e-103">Глава 1. Введение в ОСРВ Azure NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="2bc8e-103">Chapter 1 - Introduction to Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="2bc8e-104">Программа-оболочка соответствия API сокетов BSD поддерживает часть базовых вызовов API сокетов BSD (с некоторыми ограничениями) при помощи примитивов ОСРВ Azure NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2bc8e-104">The BSD Socket API Compliancy Wrapper supports some of the basic BSD Socket API calls, with some limitations and utilizes Azure RTOS NetX Duo primitives underneath.</span></span>

## <a name="bsd-socket-api-compliancy-wrapper-source"></a><span data-ttu-id="2bc8e-105">Исходный код программы-оболочки для обеспечения соответствия API сокетов BSD</span><span class="sxs-lookup"><span data-stu-id="2bc8e-105">BSD Socket API Compliancy Wrapper Source</span></span>

<span data-ttu-id="2bc8e-106">Исходный код программы-оболочки BSD специально создавался простым, он размещен всего в двух файлах: *nx_bsd.h* и *nx_bsd.c*.</span><span class="sxs-lookup"><span data-stu-id="2bc8e-106">The Wrapper source code is designed for simplicity and is comprised of two files, namely *nxd_bsd.h* and *nxd_bsd.c*.</span></span> <span data-ttu-id="2bc8e-107">Файл *nx_bsd.h* определяет все необходимые константы и прототипы подпрограмм программы-оболочки API сокетов BSD, а *nx_bsd.c* содержит фактический исходный код для обеспечения совместимости API сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="2bc8e-107">The *nxd_bsd.h* file defines all the necessary BSD Socket API wrapper constants and subroutine prototypes, while *nxd_bsd.c* contains the actual BSD Socket API compatibility source code.</span></span> <span data-ttu-id="2bc8e-108">Такие файлы исходного кода программы-оболочки присутствуют во всех пакетах поддержки NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="2bc8e-108">These Wrapper source files are common to all NetX Duo support packages.</span></span>

<span data-ttu-id="2bc8e-109">В этот пакет входит следующее:</span><span class="sxs-lookup"><span data-stu-id="2bc8e-109">The package consists of:</span></span>

- <span data-ttu-id="2bc8e-110">**nxd_bsd.c**: исходный код программы-оболочки;</span><span class="sxs-lookup"><span data-stu-id="2bc8e-110">**nxd_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="2bc8e-111">**nxd_bsd.h**: основной файл заголовка.</span><span class="sxs-lookup"><span data-stu-id="2bc8e-111">**nxd_bsd.h**: Main header file</span></span>

<span data-ttu-id="2bc8e-112">Примеры демонстрационных программ:</span><span class="sxs-lookup"><span data-stu-id="2bc8e-112">Sample demo programs:</span></span>

- <span data-ttu-id="2bc8e-113">**bsd_demo_udp. c**: *демонстрационный файл с двумя одноранговыми узлами UDP (только IPv4)* ;</span><span class="sxs-lookup"><span data-stu-id="2bc8e-113">**bsd_demo_udp.c**: *Demo with two UDP peers (IPv4 only)*</span></span>
- <span data-ttu-id="2bc8e-114">**bsd_demo_tcp.c**: *демонстрационный файл с одним TCP-сервером и TCP-клиентом*;</span><span class="sxs-lookup"><span data-stu-id="2bc8e-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="2bc8e-115">**bsd_demo_raw. c**: *демонстрационный файл с двумя одноранговыми узлами RAW*.</span><span class="sxs-lookup"><span data-stu-id="2bc8e-115">**bsd_demo_raw.c**: *Demo with two RAW peers*</span></span>