---
title: Глава 1. Общие сведения о LevelX для ОСРВ Azure
description: LevelX для ОСРВ Azure предоставляет встраиваемым приложениям возможности выравнивания износа флэш-памяти NAND и NOR.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 045446fec74164f125bc0ad27e8b7a904be14ab2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814903"
---
# <a name="chapter-1---overview-of-azure-rtos-levelx"></a><span data-ttu-id="d727e-103">Глава 1. Общие сведения о LevelX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="d727e-103">Chapter 1 - Overview of Azure RTOS LevelX</span></span>

<span data-ttu-id="d727e-104">LevelX для ОСРВ Azure предоставляет встраиваемым приложениям возможности выравнивания износа флэш-памяти NAND и NOR.</span><span class="sxs-lookup"><span data-stu-id="d727e-104">Azure RTOS LevelX provides NAND and NOR flash wear leveling facilities to embedded applications.</span></span> <span data-ttu-id="d727e-105">Поскольку флэш-память NAND и NOR допускает ограниченное количество удалений информации, крайне важно равномерно распределять ее использование.</span><span class="sxs-lookup"><span data-stu-id="d727e-105">Since both NAND and NOR flash memory can only be erased a finite number of times, it's critical to distribute the flash memory use evenly.</span></span> <span data-ttu-id="d727e-106">Достижение этой равномерности часто называют "выравнивание износа", и именно для этого предназначается LevelX.</span><span class="sxs-lookup"><span data-stu-id="d727e-106">This is typically called "wear leveling" and is the purpose behind LevelX.</span></span>

<span data-ttu-id="d727e-107">Алгоритм выбора блока флэш-памяти для повторного использования основывается на счетчике удалений, но учитывает и другие параметры.</span><span class="sxs-lookup"><span data-stu-id="d727e-107">The algorithm that chooses which flash block to reuse is primarily based on the erase count, but not entirely.</span></span> <span data-ttu-id="d727e-108">Блок с минимальным числом удалений не будет выбран для записи, если существует другой блок с допустимой разницей в числе удалений, у которого выше число устаревших сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="d727e-108">The block with the lowest erase count might not be chosen if there is another block that has an erase count within an acceptable delta from the minimal erase count and that has a greater number of obsolete mappings.</span></span> <span data-ttu-id="d727e-109">В таких случаях будет удален и повторно использован блок с большим числом устаревших удалений, что позволяет избежать лишних затрат на перемещение записей сопоставления.</span><span class="sxs-lookup"><span data-stu-id="d727e-109">In such cases, the block with the greatest number of obsolete mappings will be erased and reused, thus saving overhead in moving valid mapping entries.</span></span>

<span data-ttu-id="d727e-110">LevelX поддерживает несколько экземпляров частей NAND и (или) NOR, то есть в одном приложении можно использовать несколько экземпляров LevelX.</span><span class="sxs-lookup"><span data-stu-id="d727e-110">LevelX supports multiple instances of NAND and/or NOR parts, i.e., the application can utilize separate instances of LevelX within the same application.</span></span> <span data-ttu-id="d727e-111">Каждому экземпляру требуется собственный блок управления, предоставленный приложением, а также собственный драйвер флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="d727e-111">Each instance requires its own control block provided by the application as well as its own flash driver.</span></span>

<span data-ttu-id="d727e-112">LevelX предоставляет пользователю массив логических секторов, которые внутренними средствами LevelX сопоставляются с участками физической памяти.</span><span class="sxs-lookup"><span data-stu-id="d727e-112">LevelX presents to the user an array of logical sectors that are mapped to physical flash memory inside of LevelX.</span></span> <span data-ttu-id="d727e-113">Чтобы повысить производительность, LevelX предоставляет также кэш недавно использованных сопоставлений логических секторов.</span><span class="sxs-lookup"><span data-stu-id="d727e-113">To enhance performance, LevelX also provides a cache of the most recent logical sector mappings.</span></span> <span data-ttu-id="d727e-114">Размер этого кэша определяется программистом.</span><span class="sxs-lookup"><span data-stu-id="d727e-114">The size of this cache is defined by the programmer.</span></span> <span data-ttu-id="d727e-115">Приложения могут использовать LevelX в сочетании с FileX или выполнять чтение и запись напрямую в логических секторах.</span><span class="sxs-lookup"><span data-stu-id="d727e-115">Applications may use LevelX in conjunction with FileX or may read/write logical sectors directly.</span></span> <span data-ttu-id="d727e-116">LevelX не зависит от FileX и имеет очень низкий уровень зависимости от ThreadX (используются только простые типы данных ThreadX).</span><span class="sxs-lookup"><span data-stu-id="d727e-116">LevelX has no dependency on FileX and very little dependency on ThreadX (only primitive ThreadX data types are used).</span></span>

<span data-ttu-id="d727e-117">Библиотека LevelX разрабатывалась с упором на отказоустойчивость.</span><span class="sxs-lookup"><span data-stu-id="d727e-117">LevelX is designed for fault tolerance.</span></span> <span data-ttu-id="d727e-118">Обновления флэш-памяти выполняются в несколько этапов, на каждом из которых допустимо прерывание процесса.</span><span class="sxs-lookup"><span data-stu-id="d727e-118">Flash updates are performed in a multiple-step process that can be interrupted in each step.</span></span> <span data-ttu-id="d727e-119">LevelX автоматически восстановит оптимальное состояние памяти при выполнении следующей операции.</span><span class="sxs-lookup"><span data-stu-id="d727e-119">LevelX automatically recovers to the optimal state during the next operation.</span></span>

<span data-ttu-id="d727e-120">Для LevelX требуется, чтобы драйвер флэш-памяти имел физический доступ к базовой памяти.</span><span class="sxs-lookup"><span data-stu-id="d727e-120">LevelX requires a flash driver for physical access to the underlying flash memory.</span></span> <span data-ttu-id="d727e-121">Мы предоставляем примеры имитированных драйверов NAND и NOR, которые станут хорошей основой для реализации собственных драйверов для LevelX.</span><span class="sxs-lookup"><span data-stu-id="d727e-121">Example NAND and NOR simulated drivers are provided and can be used as a good starting point for implementing actual LevelX drivers.</span></span> <span data-ttu-id="d727e-122">Дополнительные требования к драйверам подробно описаны далее в этой документации.</span><span class="sxs-lookup"><span data-stu-id="d727e-122">In addition, driver requirements are detailed later in this documentation.</span></span>

<span data-ttu-id="d727e-123">Следующие главы посвящены описанию работы LevelX с NAND и NOR.</span><span class="sxs-lookup"><span data-stu-id="d727e-123">The following chapters describe the functional operation for the NAND and NOR LevelX support.</span></span>