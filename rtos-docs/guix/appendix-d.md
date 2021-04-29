---
title: Приложение Г. Атрибуты кисти, холста и градиента в GUIX
description: Узнайте об атрибутах кисти, холста и градиента в GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815571"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="34f49-103">Приложение Г. Атрибуты кисти, холста и градиента в GUIX</span><span class="sxs-lookup"><span data-stu-id="34f49-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="34f49-104">__**Стили кисти:**__</span><span class="sxs-lookup"><span data-stu-id="34f49-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="34f49-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="34f49-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="34f49-106">Значение: 0x0000</span><span class="sxs-lookup"><span data-stu-id="34f49-106">Value: 0x0000</span></span>
- <span data-ttu-id="34f49-107">Описание: этот стиль кисти применяется к функциям рисования фигур, таким как gx_canvas_rectangle_draw и gx_canvas_polygon_draw.</span><span class="sxs-lookup"><span data-stu-id="34f49-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="34f49-108">Этот стиль указывает, что помимо необязательной заливки фигура должна иметь контур.</span><span class="sxs-lookup"><span data-stu-id="34f49-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="34f49-109">Если задан стиль GX_BRUSH_OUTLINE и значение GX_BRSUH_SOLID_FILL очищено, то отображается только контур фигуры.</span><span class="sxs-lookup"><span data-stu-id="34f49-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="34f49-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="34f49-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="34f49-111">Значение: 0x0001</span><span class="sxs-lookup"><span data-stu-id="34f49-111">Value: 0x0001</span></span>
- <span data-ttu-id="34f49-112">Описание: этот стиль кисти применяется к функциям рисования фигур и указывает, что выбранная фигура должна быть заполнена сплошным цветом с использованием текущего цвета заливки для кисти.</span><span class="sxs-lookup"><span data-stu-id="34f49-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="34f49-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="34f49-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="34f49-114">Значение: 0x0002</span><span class="sxs-lookup"><span data-stu-id="34f49-114">Value: 0x0002</span></span>
- <span data-ttu-id="34f49-115">Описание: этот стиль кисти применяется к функциям рисования фигур и указывает, что выбранная фигура должна быть заполнена узором с использованием текущей карты отображения пикселей для кисти.</span><span class="sxs-lookup"><span data-stu-id="34f49-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="34f49-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="34f49-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="34f49-117">Значение: 0x0004</span><span class="sxs-lookup"><span data-stu-id="34f49-117">Value: 0x0004</span></span>
- <span data-ttu-id="34f49-118">Описание: этот стиль кисти применяется ко всем отображаемым линиям и контурам фигур.</span><span class="sxs-lookup"><span data-stu-id="34f49-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="34f49-119">Если этот флаг установлен, линии и контуры отображаются точнее, но дольше, с применением алгоритмов рисования со сглаживанием.</span><span class="sxs-lookup"><span data-stu-id="34f49-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="34f49-120">Этот флаг стиля используется только для глубин цвета от 16 бит/пкс и выше.</span><span class="sxs-lookup"><span data-stu-id="34f49-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="34f49-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="34f49-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="34f49-122">Значение: 0x0008</span><span class="sxs-lookup"><span data-stu-id="34f49-122">Value: 0x0008</span></span>
- <span data-ttu-id="34f49-123">Описание: этот флаг применяется к отображению текста и указывает, что последующий текст должен быть подчеркнутым.</span><span class="sxs-lookup"><span data-stu-id="34f49-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="34f49-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="34f49-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="34f49-125">Значение: 0x0010</span><span class="sxs-lookup"><span data-stu-id="34f49-125">Value: 0x0010</span></span>
- <span data-ttu-id="34f49-126">Описание: этот флаг применяется к отображению линий и указывает, что концы линий должны иметь круглую или овальную форму, а не квадратную форму по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="34f49-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="34f49-127">__**Флаги холста:**__</span><span class="sxs-lookup"><span data-stu-id="34f49-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="34f49-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="34f49-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="34f49-129">Значение: 0x01</span><span class="sxs-lookup"><span data-stu-id="34f49-129">Value: 0x01</span></span>
- <span data-ttu-id="34f49-130">Описание: холст в памяти, используемый для рисования за пределами экрана.</span><span class="sxs-lookup"><span data-stu-id="34f49-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="34f49-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="34f49-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="34f49-132">Значение: 0x02</span><span class="sxs-lookup"><span data-stu-id="34f49-132">Value: 0x02</span></span>
- <span data-ttu-id="34f49-133">Описание: холст, который автоматически отправляется на активный экран либо в ходе составного процесса сборки, либо в ходе операции переключения буфера для архитектур с одним холстом.</span><span class="sxs-lookup"><span data-stu-id="34f49-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="34f49-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="34f49-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="34f49-135">Значение: 0x04</span><span class="sxs-lookup"><span data-stu-id="34f49-135">Value: 0x04</span></span>
- <span data-ttu-id="34f49-136">Описание: этот флаг можно использовать для включения и отключения холста без потери нарисованного содержимого.</span><span class="sxs-lookup"><span data-stu-id="34f49-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="34f49-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="34f49-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="34f49-138">Значение: 0x08</span><span class="sxs-lookup"><span data-stu-id="34f49-138">Value: 0x08</span></span>
- <span data-ttu-id="34f49-139">Описание: зарезервирован для использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="34f49-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="34f49-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="34f49-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="34f49-141">Значение: 0x20</span><span class="sxs-lookup"><span data-stu-id="34f49-141">Value: 0x20</span></span>
- <span data-ttu-id="34f49-142">Описание: этот флаг используется приложением при настройке системы с несколькими холстами, которая объединяет несколько управляемых холстов в один составной холст, после чего он отправляется в аппаратный буфер кадров.</span><span class="sxs-lookup"><span data-stu-id="34f49-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="34f49-143">__**Типы градиентов:**__</span><span class="sxs-lookup"><span data-stu-id="34f49-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="34f49-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="34f49-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="34f49-145">Значение: 0x01</span><span class="sxs-lookup"><span data-stu-id="34f49-145">Value: 0x01</span></span>
- <span data-ttu-id="34f49-146">Описание: создает вертикальный градиент с альфа-наложением.</span><span class="sxs-lookup"><span data-stu-id="34f49-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="34f49-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="34f49-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="34f49-148">Значение: 0x02</span><span class="sxs-lookup"><span data-stu-id="34f49-148">Value: 0x02</span></span>
- <span data-ttu-id="34f49-149">Описание: создает стиль градиента с альфа-наложением.</span><span class="sxs-lookup"><span data-stu-id="34f49-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="34f49-150">В настоящее время поддерживается только этот стиль градиента.</span><span class="sxs-lookup"><span data-stu-id="34f49-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="34f49-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="34f49-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="34f49-152">Значение: 0x04</span><span class="sxs-lookup"><span data-stu-id="34f49-152">Value: 0x04</span></span>
- <span data-ttu-id="34f49-153">Описание: этот флаг указывает, что градиент должен сгущаться в центре диапазона ширины или высоты и возвращаться к начальному значению по направлению к правому или нижнему краю.</span><span class="sxs-lookup"><span data-stu-id="34f49-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="34f49-154">Без этого флага стиля градиент будет линейным градиентом сверху вниз или слева направо, в зависимости от флага GX_GRADIENT_TYPE_VERTICAL.</span><span class="sxs-lookup"><span data-stu-id="34f49-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>