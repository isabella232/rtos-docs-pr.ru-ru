---
title: Глава 1. Введение в NetX BSD для ОСРВ Azure
description: Программа-оболочка соответствия API сокетов NetX BSD для ОСРВ Azure поддерживает некоторые из базовых вызовов API сокетов BSD с некоторыми ограничениями и в фоне использует примитивы NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: fce781ac97ae75c4148614453eeb35c3064f8849
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814459"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-bsd"></a><span data-ttu-id="25099-103">Глава 1. Введение в NetX BSD для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="25099-103">Chapter 1 - Introduction to Azure RTOS NetX BSD</span></span>

<span data-ttu-id="25099-104">Оболочка соответствия API сокетов NetX BSD поддерживает некоторые из базовых вызовов API сокетов BSD с некоторыми ограничениями и в фоне использует примитивы NetX.</span><span class="sxs-lookup"><span data-stu-id="25099-104">The NetX BSD Sockets API Compliancy Wrapper supports some of the basic BSD Sockets API calls with some limitations and utilizes NetX primitives underneath.</span></span> <span data-ttu-id="25099-105">Этот уровень совместимости API для сокетов BSD обычно работает с той же или немного большей скоростью, что и стандартные реализации BSD, так как эта программа-оболочка использует внутренние примитивы NetX и обходит базовую проверку ошибок NetX.</span><span class="sxs-lookup"><span data-stu-id="25099-105">This BSD Sockets API compatibility layer should perform as fast or slightly faster than typical BSD implementations, since this Wrapper utilizes internal NetX primitives and bypasses basic NetX error checking.</span></span>

## <a name="bsd-sockets-api-compliancy-wrapper-source"></a><span data-ttu-id="25099-106">Источник программы-оболочки соответствия API сокетов BSD</span><span class="sxs-lookup"><span data-stu-id="25099-106">BSD Sockets API Compliancy Wrapper Source</span></span>

<span data-ttu-id="25099-107">Исходный код программы-оболочки BSD специально создавался простым, он размещен всего в двух файлах: *nx_bsd.h* и *nx_bsd.c*.</span><span class="sxs-lookup"><span data-stu-id="25099-107">The BSD Wrapper source code is designed for simplicity and is comprised of only two files, *nx_bsd.h* and *nx_bsd.c*.</span></span> <span data-ttu-id="25099-108">Файл *nx_bsd.h* определяет все необходимые константы программы-оболочки API сокетов BSD и прототипы подпрограмм, а *nx_bsd.c* содержит фактический исходный код совместимости API для сокетов BSD.</span><span class="sxs-lookup"><span data-stu-id="25099-108">The *nx_bsd.h* file defines all the necessary BSD Sockets API Wrapper constants and subroutine prototypes, while *nx_bsd.c* contains the actual BSD Sockets API compatibility source code.</span></span> <span data-ttu-id="25099-109">Такие исходные файлы программы-оболочки BSD используются во всех пакетах поддержки NetX.</span><span class="sxs-lookup"><span data-stu-id="25099-109">These BSD Wrapper source files are common to all NetX support packages.</span></span>

<span data-ttu-id="25099-110">В этот пакет входит следующее:</span><span class="sxs-lookup"><span data-stu-id="25099-110">The package consists of:</span></span>

- <span data-ttu-id="25099-111">**nx_bsd.c**: исходный код оболочки.</span><span class="sxs-lookup"><span data-stu-id="25099-111">**nx_bsd.c**: Wrapper source code</span></span>
- <span data-ttu-id="25099-112">**nx_bsd.h**: основной файл заголовка.</span><span class="sxs-lookup"><span data-stu-id="25099-112">**nx_bsd.h**: Main header file</span></span>

<span data-ttu-id="25099-113">Примеры демонстрационных программ:</span><span class="sxs-lookup"><span data-stu-id="25099-113">Sample demo programs:</span></span>

- <span data-ttu-id="25099-114">**bsd_demo_tcp.c**: *демонстрация с одним TCP-сервером и клиентом.*</span><span class="sxs-lookup"><span data-stu-id="25099-114">**bsd_demo_tcp.c**: *Demo with a single TCP server and client*</span></span>
- <span data-ttu-id="25099-115">**bsd_demo_udp.c**: *демонстрация с двумя UDP-клиентами и одним UDP-сервером.*</span><span class="sxs-lookup"><span data-stu-id="25099-115">**bsd_demo_udp.c**: *Demo with two UDP clients and a UDP server*</span></span>
