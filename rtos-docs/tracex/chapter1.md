---
title: Глава 1. Введение в TraceX для ОСРВ Azure
description: TraceX для ОСРВ Azure — это средство системного анализа корпорации Майкрософт, которое отображает сведения о системных событиях, собираемые системой ThreadX на встраиваемой целевой системе.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815843"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a><span data-ttu-id="fab90-103">Глава 1. Введение в TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="fab90-103">Chapter 1 - Introduction to Azure RTOS TraceX</span></span>

<span data-ttu-id="fab90-104">TraceX для ОСРВ Azure — это средство системного анализа корпорации Майкрософт, которое отображает сведения о системных событиях, собираемые системой ThreadX на встраиваемой целевой системе.</span><span class="sxs-lookup"><span data-stu-id="fab90-104">Azure RTOS TraceX is a Microsoft system analysis tool that displays system event information gathered by ThreadX running on an embedded target.</span></span> <span data-ttu-id="fab90-105">Пользователь должен самостоятельно обеспечить передачу буфера трассировки, сохраняемого в ОЗУ на встраиваемой целевой системе, в двоичный файл на главном компьютере.</span><span class="sxs-lookup"><span data-stu-id="fab90-105">The user is responsible for transferring the trace buffer stored in RAM in the embedded target to a binary file on the host computer.</span></span> <span data-ttu-id="fab90-106">Затем пользователь сможет открыть этот файл в TraceX и в графической среде анализировать события на целевой системе, обнаруживать проблемы и настраивать работающие приложения для повышения производительности и управления ресурсами.</span><span class="sxs-lookup"><span data-stu-id="fab90-106">The user can then open this file with TraceX and graphically analyze the target events, diagnosing system problems and tuning a working application to improve performance and resource management.</span></span>

## <a name="tracex-requirements"></a><span data-ttu-id="fab90-107">Требования TraceX</span><span class="sxs-lookup"><span data-stu-id="fab90-107">TraceX Requirements</span></span>

<span data-ttu-id="fab90-108">Для TraceX требуется Windows XP или более поздняя версия.</span><span class="sxs-lookup"><span data-stu-id="fab90-108">TraceX requires Windows XP (or above).</span></span> <span data-ttu-id="fab90-109">В системе должно быть как минимум 192 МБ ОЗУ, 2 ГБ свободного места на жестком диске и экран с разрешением не ниже 1024×768 с поддержкой 256 цветов.</span><span class="sxs-lookup"><span data-stu-id="fab90-109">The system should have a minimum of 192 MB of RAM, 2 GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="fab90-110">Кроме того, приложение должно работать на ThreadX версии 5.0 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="fab90-110">In addition, the application must be running on ThreadX V5.0 or later.</span></span>

<span data-ttu-id="fab90-111">Для TraceX также нужно установить платформу Microsoft.NET, что автоматически выполняется установщиком TraceX.</span><span class="sxs-lookup"><span data-stu-id="fab90-111">TraceX also requires the Microsoft .NET framework be installed, which the TraceX installer does automatically.</span></span>

## <a name="tracex-constraints"></a><span data-ttu-id="fab90-112">Ограничения TraceX</span><span class="sxs-lookup"><span data-stu-id="fab90-112">TraceX Constraints</span></span>

<span data-ttu-id="fab90-113">Для TraceX действуют следующие ограничения:</span><span class="sxs-lookup"><span data-stu-id="fab90-113">TraceX has the following constraints:</span></span>

- <span data-ttu-id="fab90-114">Файлы TraceX могут содержать не более 32 768 событий (примерно 1 МБ).</span><span class="sxs-lookup"><span data-stu-id="fab90-114">TraceX files are limited to a maximum of 32,768 events (roughly 1 MB ).</span></span>
- <span data-ttu-id="fab90-115">Источник меток времени должен иметь разумное разрешение.</span><span class="sxs-lookup"><span data-stu-id="fab90-115">The time-stamp source must have reasonable resolution.</span></span> <span data-ttu-id="fab90-116">Если разрешение слишком мало, события будут перекрываться.</span><span class="sxs-lookup"><span data-stu-id="fab90-116">If the resolution is too low, the events will overlap.</span></span> <span data-ttu-id="fab90-117">Если разрешение слишком велико, будут возникать длительные промежутки между событиями.</span><span class="sxs-lookup"><span data-stu-id="fab90-117">If the resolution is too high, there is potential for long gaps between events.</span></span>
- <span data-ttu-id="fab90-118">TraceX не может точно измерять интервалы между событиями, если они превышают период таймера.</span><span class="sxs-lookup"><span data-stu-id="fab90-118">TraceX cannot accurately measure intervals between events greater than the timer period.</span></span>
