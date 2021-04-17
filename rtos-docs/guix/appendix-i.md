---
title: Приложение I. Информационные структуры в GUIX
description: Сведения об информационных структурах в GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dc7775cdde8f1aa89ca650561713f54ac6c069eb
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550224"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="3227e-103">Приложение I. Информационные структуры в GUIX</span><span class="sxs-lookup"><span data-stu-id="3227e-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="3227e-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-105">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| <span data-ttu-id="3227e-106">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-106">Members</span></span> | <span data-ttu-id="3227e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-107">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="3227e-108">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="3227e-108">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="3227e-109">Текст для изменения порядка.</span><span class="sxs-lookup"><span data-stu-id="3227e-109">Text for reordering</span></span> |
| <span data-ttu-id="3227e-110">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="3227e-110">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="3227e-111">Шрифт для отображения текста. Укажите значение GX_NULL, если разбиение строк не требуется.</span><span class="sxs-lookup"><span data-stu-id="3227e-111">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="3227e-112">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-112">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="3227e-113">Доступная для отображения ширина. Установите значение -1, если разбиение строк не требуется.</span><span class="sxs-lookup"><span data-stu-id="3227e-113">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="3227e-114">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-114">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-115">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-115">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| <span data-ttu-id="3227e-116">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-116">Members</span></span> | <span data-ttu-id="3227e-117">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-117">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="3227e-118">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="3227e-118">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="3227e-119">Указатель на массив переупорядоченного двунаправленного текста.</span><span class="sxs-lookup"><span data-stu-id="3227e-119">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="3227e-120">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="3227e-120">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="3227e-121">Общее число строк разрешенного двунаправленного текста в одном абзаце.</span><span class="sxs-lookup"><span data-stu-id="3227e-121">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="3227e-122">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="3227e-122">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="3227e-123">Информация о разрешенном двунаправленном тексте для следующего абзаца.</span><span class="sxs-lookup"><span data-stu-id="3227e-123">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="3227e-124">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-124">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="3227e-125">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-125">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```

| <span data-ttu-id="3227e-126">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-126">Members</span></span> | <span data-ttu-id="3227e-127">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-127">Description</span></span> |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="3227e-128">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="3227e-128">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="3227e-129">Общее число шагов, которые пройдет стрелка при перемещении из текущего положения в новое.</span><span class="sxs-lookup"><span data-stu-id="3227e-129">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="3227e-130">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="3227e-130">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="3227e-131">Число тактов часов GUIX между последовательными шагами анимации.</span><span class="sxs-lookup"><span data-stu-id="3227e-131">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="3227e-132">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="3227e-132">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="3227e-133">Расстояние от левого края мини-приложения датчика до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-133">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="3227e-134">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="3227e-134">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="3227e-135">Расстояние от верхнего края мини-приложения датчика до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-135">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="3227e-136">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="3227e-136">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="3227e-137">Расстояние от левого края изображения стрелки до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-137">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="3227e-138">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="3227e-138">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="3227e-139">Расстояние от верхнего края изображения стрелки до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-139">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="3227e-140">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-140">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="3227e-141">Идентификатор ресурса для растрового изображения, которое будет использоваться для отрисовки стрелки датчика.</span><span class="sxs-lookup"><span data-stu-id="3227e-141">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="3227e-142">Это изображение будет повернуто мини-приложением датчика на нужный угол, чтобы правильно отображать стрелку в любом положении.</span><span class="sxs-lookup"><span data-stu-id="3227e-142">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="3227e-143">Следующая схема демонстрирует применение координат xpos, ypos и xcor, ycor:</span><span class="sxs-lookup"><span data-stu-id="3227e-143">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Схема координат Y и X для стрелки](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="3227e-145">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-145">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="3227e-146">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-146">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

| <span data-ttu-id="3227e-147">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-147">Members</span></span> | <span data-ttu-id="3227e-148">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-148">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="3227e-149">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-149">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="3227e-150">Минимальное значение данных, которое используется для расчета масштаба.</span><span class="sxs-lookup"><span data-stu-id="3227e-150">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="3227e-151">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-151">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="3227e-152">Максимальное значение данных, которое используется для расчета масштаба.</span><span class="sxs-lookup"><span data-stu-id="3227e-152">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="3227e-153">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="3227e-153">**gx_line_chart_data**</span></span>             | <span data-ttu-id="3227e-154">Указатель на массив целых чисел.</span><span class="sxs-lookup"><span data-stu-id="3227e-154">Pointer to an array of integer values.</span></span> <span data-ttu-id="3227e-155">Эти целые числа отображаются на мини-приложении графика.</span><span class="sxs-lookup"><span data-stu-id="3227e-155">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="3227e-156">**gx_line_<side>_margin**</span><span class="sxs-lookup"><span data-stu-id="3227e-156">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="3227e-157">Отступ от внешней границы окна схемы до области фактической отрисовки графика.</span><span class="sxs-lookup"><span data-stu-id="3227e-157">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="3227e-158">Ось схемы и линия данных всегда отображаются внутри этой границы, что позволяет приложению рисовать метки и другие данные внутри окна схемы, но без перекрытия с областью отображения графика.</span><span class="sxs-lookup"><span data-stu-id="3227e-158">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="3227e-159">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="3227e-159">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="3227e-160">Допустимое количество значений данных.</span><span class="sxs-lookup"><span data-stu-id="3227e-160">The number of data values which may be present.</span></span> <span data-ttu-id="3227e-161">Этот параметр используется для расчета масштабирования по оси X или интервала для размещения точек данных.</span><span class="sxs-lookup"><span data-stu-id="3227e-161">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="3227e-162">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="3227e-162">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="3227e-163">Количество значений данных, которые реально присутствуют в массиве данных.</span><span class="sxs-lookup"><span data-stu-id="3227e-163">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="3227e-164">В некоторых случаях график может быть настроен на отображение, к примеру, 100 значений, но в одном из обновлений может присутствовать меньший объем данных.</span><span class="sxs-lookup"><span data-stu-id="3227e-164">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="3227e-165">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-165">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="3227e-166">Ширина линии, которая используется для горизонтальной и вертикальной осей.</span><span class="sxs-lookup"><span data-stu-id="3227e-166">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="3227e-167">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-167">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="3227e-168">Ширина отображаемой на графике линии</span><span class="sxs-lookup"><span data-stu-id="3227e-168">Width of the plotted data line</span></span> |
| <span data-ttu-id="3227e-169">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-169">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="3227e-170">Идентификатор ресурса для того цвета, который используется для отрисовки осей.</span><span class="sxs-lookup"><span data-stu-id="3227e-170">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="3227e-171">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-171">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="3227e-172">Идентификатор ресурса для того цвета, который используется для линии графика.</span><span class="sxs-lookup"><span data-stu-id="3227e-172">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="3227e-173">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-173">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-174">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-174">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| <span data-ttu-id="3227e-175">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-175">Members</span></span> | <span data-ttu-id="3227e-176">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-176">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="3227e-177">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-177">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="3227e-178">Идентификатор ресурса для изображения курсора мыши.</span><span class="sxs-lookup"><span data-stu-id="3227e-178">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="3227e-179">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="3227e-179">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="3227e-180">Отступ от левого края изображения курсора до активной зоны на этом изображении.</span><span class="sxs-lookup"><span data-stu-id="3227e-180">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="3227e-181">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="3227e-181">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="3227e-182">Отступ от верхнего края изображения курсора до активной зоны на этом изображении.</span><span class="sxs-lookup"><span data-stu-id="3227e-182">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="3227e-183">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="3227e-183">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-184">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-184">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| <span data-ttu-id="3227e-185">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-185">Members</span></span> | <span data-ttu-id="3227e-186">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-186">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="3227e-187">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="3227e-187">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="3227e-188">Минимальное расстояние перетаскивания за один такт таймера GUIX, которое требуется для срабатывания события FLICK.</span><span class="sxs-lookup"><span data-stu-id="3227e-188">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="3227e-189">Вызовите GX_FIXED_VAL_MAKE, чтобы создать значение с типом данных числа с фиксированной точкой.</span><span class="sxs-lookup"><span data-stu-id="3227e-189">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="3227e-190">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="3227e-190">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="3227e-191">Максимальная скорость перетаскивания в тактах таймера GUIX, которая требуется для срабатывания события FLICK.</span><span class="sxs-lookup"><span data-stu-id="3227e-191">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="3227e-192">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-192">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-193">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-193">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| <span data-ttu-id="3227e-194">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-194">Members</span></span> | <span data-ttu-id="3227e-195">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-195">Description</span></span> |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="3227e-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="3227e-197">Идентификатор ресурса для растрового изображения, которое используется для заполнения до отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-197">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="3227e-198">Если верхнее растровое изображение для фона не задано, этот же ресурс используется для заполнения как до, так и после отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-198">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="3227e-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="3227e-200">Идентификатор ресурса для растрового изображения, которое используется для заполнения после отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-200">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="3227e-201">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-201">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="3227e-202">Идентификатор ресурса для растрового изображения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-202">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="3227e-203">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-203">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-204">**Определение**</span><span class="sxs-lookup"><span data-stu-id="3227e-204">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="3227e-205">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-205">Members</span></span> | <span data-ttu-id="3227e-206">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-206">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="3227e-207">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-207">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="3227e-208">Минимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="3227e-208">Minimum reported value</span></span> |
| <span data-ttu-id="3227e-209">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-209">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="3227e-210">Максимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="3227e-210">Maximum reported value</span></span> |
| <span data-ttu-id="3227e-211">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-211">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="3227e-212">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="3227e-212">Current value</span></span> |
| <span data-ttu-id="3227e-213">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-213">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="3227e-214">Идентификатор ресурса для шрифта, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-214">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="3227e-215">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-215">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="3227e-216">Идентификатор ресурса для цвета текста нормального состояния, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-216">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-217">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-217">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="3227e-218">Идентификатор ресурса для цвета текста при наведении фокуса, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-218">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-219">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-219">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="3227e-220">Идентификатор ресурса для цвета текста при отключении GX_STYLE_ENABLED, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-220">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-221">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-221">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="3227e-222">Идентификатор ресурса растрового изображения для заполнения фона.</span><span class="sxs-lookup"><span data-stu-id="3227e-222">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="3227e-223">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-223">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="3227e-224">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-224">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="3227e-225">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-225">Members</span></span> | <span data-ttu-id="3227e-226">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-226">Description</span></span> |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="3227e-227">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="3227e-227">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="3227e-228">Координата X для положения мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="3227e-228">Widget position in x coordinate</span></span> |
| <span data-ttu-id="3227e-229">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="3227e-229">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="3227e-230">Координата Y для положения мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="3227e-230">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="3227e-231">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="3227e-231">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="3227e-232">Радиус круга, обозначающего ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-232">Radius of the progress circle</span></span> |
| <span data-ttu-id="3227e-233">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-233">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="3227e-234">Текущее значение в пределах от –360 до +360, которое обозначает угловую разницу между положением привязки и верхней точкой верхней дуги. Отрицательные значения означают отрисовку дуги в направлении по часовой стрелке, начиная от положения привязки.</span><span class="sxs-lookup"><span data-stu-id="3227e-234">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="3227e-235">При положительном значении дуга отрисовывается в направлении против часовой стрелки, начиная от положения привязки.</span><span class="sxs-lookup"><span data-stu-id="3227e-235">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="3227e-236">Приложение должно самостоятельно масштабировать значения реальных величин, используемых для определения угла поворота в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-236">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="3227e-237">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-237">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="3227e-238">Начальный угол для верхней дуги хода выполнения. Это значение задается целым числом градусов, где значение 0 соответствует положению "строго направо", а значение 90 — "строго вверх".</span><span class="sxs-lookup"><span data-stu-id="3227e-238">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="3227e-239">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-239">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="3227e-240">Идентификатор ресурса для шрифта, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-240">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-241">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-241">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="3227e-242">Идентификатор ресурса для цвета текста нормального состояния, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-242">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-243">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-243">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="3227e-244">Идентификатор ресурса для цвета текста при наведении фокуса, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-244">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-245">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-245">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="3227e-246">Идентификатор ресурса для цвета текста при отключении GX_STYLE_ENABLED, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-246">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="3227e-247">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-247">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="3227e-248">Ширина нижнего круга хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-248">Width of the lower progress circle</span></span> |
| <span data-ttu-id="3227e-249">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-249">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="3227e-250">Ширина верхней дуги хода выполнения, при этом она может быть уже, шире или одной ширины с нижним кругом.</span><span class="sxs-lookup"><span data-stu-id="3227e-250">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="3227e-251">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-251">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="3227e-252">Идентификатор ресурса для цвета, которым заполняется нижний круг хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-252">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="3227e-253">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-253">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="3227e-254">Идентификатор ресурса для цвета, которым заполняется верхняя дуга хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="3227e-254">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="3227e-255">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-255">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-256">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-256">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

| <span data-ttu-id="3227e-257">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-257">Members</span></span> | <span data-ttu-id="3227e-258">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-258">Description</span></span> |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="3227e-259">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="3227e-259">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="3227e-260">Расстояние от левого края мини-приложения ползунка до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-260">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="3227e-261">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="3227e-261">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="3227e-262">Расстояние от верхнего края мини-приложения ползунка до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-262">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="3227e-263">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="3227e-263">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="3227e-264">Радиус круга для радиального ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-264">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="3227e-265">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-265">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="3227e-266">Ширина дорожки для радиального ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-266">Width of radial slider track</span></span> |
| <span data-ttu-id="3227e-267">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="3227e-267">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="3227e-268">Текущий угол поворота ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-268">Current slider angle</span></span> |
| <span data-ttu-id="3227e-269">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="3227e-269">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="3227e-270">Минимальный угол поворота ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-270">Minimum slider angle</span></span> |
| <span data-ttu-id="3227e-271">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="3227e-271">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="3227e-272">Максимальный угол поворота ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-272">Maximum slider angle</span></span> |
| <span data-ttu-id="3227e-273">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="3227e-273">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="3227e-274">Список значений угла, который определяет положения привязки. Если этот параметр задан, ползунок может находиться только в одном из определенных этим списком положений.</span><span class="sxs-lookup"><span data-stu-id="3227e-274">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="3227e-275">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="3227e-275">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="3227e-276">Число положений привязки.</span><span class="sxs-lookup"><span data-stu-id="3227e-276">Number of anchor angles</span></span> |
| <span data-ttu-id="3227e-277">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-277">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="3227e-278">Идентификатор ресурса для фонового растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-278">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="3227e-279">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-279">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="3227e-280">Идентификатор ресурса для растрового изображения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-280">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="3227e-281">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="3227e-281">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="3227e-282">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-282">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| <span data-ttu-id="3227e-283">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-283">Members</span></span> | <span data-ttu-id="3227e-284">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-284">Description</span></span> |
| -------------------------------- | ------------------------|
| <span data-ttu-id="3227e-285">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="3227e-285">**gx_rectangle_left**</span></span>            | <span data-ttu-id="3227e-286">Левый край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="3227e-286">Left of the rectangle</span></span>   |  
| <span data-ttu-id="3227e-287">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="3227e-287">**gx_rectangle_top**</span></span>             | <span data-ttu-id="3227e-288">Верхний край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="3227e-288">Top of the rectangle</span></span>    | 
| <span data-ttu-id="3227e-289">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="3227e-289">**gx_rectangle_right**</span></span>           | <span data-ttu-id="3227e-290">Правый край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="3227e-290">Right of the rectangle</span></span>  |
| <span data-ttu-id="3227e-291">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="3227e-291">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="3227e-292">Нижний край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="3227e-292">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="3227e-293">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="3227e-293">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-294">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-294">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| <span data-ttu-id="3227e-295">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-295">Members</span></span> | <span data-ttu-id="3227e-296">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-296">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="3227e-297">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-297">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="3227e-298">Идентификатор ресурса для нормального шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="3227e-298">Resource ID of normal text font</span></span> |
| <span data-ttu-id="3227e-299">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-299">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="3227e-300">Идентификатор ресурса для полужирного шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="3227e-300">Resource ID of bold text font</span></span> |
| <span data-ttu-id="3227e-301">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-301">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="3227e-302">Идентификатор ресурса для курсивного шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="3227e-302">Resource ID of italic text font</span></span> |
| <span data-ttu-id="3227e-303">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="3227e-303">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="3227e-304">Идентификатор ресурса для полужирного курсивного шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="3227e-304">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="3227e-305">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-305">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="3227e-306">**Определение**</span><span class="sxs-lookup"><span data-stu-id="3227e-306">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

| <span data-ttu-id="3227e-307">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-307">Members</span></span> | <span data-ttu-id="3227e-308">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-308">Description</span></span> |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="3227e-309">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="3227e-309">**gx_scroll_value**</span></span>     | <span data-ttu-id="3227e-310">Текущее положение прокрутки</span><span class="sxs-lookup"><span data-stu-id="3227e-310">Current scroll position</span></span>       |
| <span data-ttu-id="3227e-311">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="3227e-311">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="3227e-312">Минимальное отображаемое положение.</span><span class="sxs-lookup"><span data-stu-id="3227e-312">Minimum reported position</span></span>     |
| <span data-ttu-id="3227e-313">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="3227e-313">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="3227e-314">Максимальное отображаемое положение.</span><span class="sxs-lookup"><span data-stu-id="3227e-314">Maximum reported position</span></span>     |
| <span data-ttu-id="3227e-315">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="3227e-315">**gx_scroll_visible**</span></span>   | <span data-ttu-id="3227e-316">Видимый диапазон родительского окна.</span><span class="sxs-lookup"><span data-stu-id="3227e-316">Parent window visible range</span></span>   |
| <span data-ttu-id="3227e-317">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="3227e-317">**gx_scroll_increment**</span></span> | <span data-ttu-id="3227e-318">Минимальное значение диапазона для полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="3227e-318">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="3227e-319">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="3227e-319">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="3227e-320">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-320">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

| <span data-ttu-id="3227e-321">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-321">Members</span></span> | <span data-ttu-id="3227e-322">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-322">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="3227e-323">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-323">**gx_scroll_width**</span></span>                      | <span data-ttu-id="3227e-324">Ширина мини-приложения полосы прокрутки, в пикселях.</span><span class="sxs-lookup"><span data-stu-id="3227e-324">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="3227e-325">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-325">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="3227e-326">Ширина бегунка, скользящего по полосе прокрутки, в пикселях.</span><span class="sxs-lookup"><span data-stu-id="3227e-326">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="3227e-327">Это значение обычно на несколько пикселей меньше, чем общая ширина полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="3227e-327">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="3227e-328">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="3227e-328">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="3227e-329">Смещение от конца полосы прокрутки до точки минимального хода ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-329">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="3227e-330">Это ограничение не позволяет уводить ползунок до самого края полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="3227e-330">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="3227e-331">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="3227e-331">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="3227e-332">Смещение от конца полосы прокрутки до точки максимального хода ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-332">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="3227e-333">Это ограничение не позволяет уводить ползунок до самого края полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="3227e-333">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="3227e-334">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="3227e-334">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="3227e-335">Стиль границы для ползунка</span><span class="sxs-lookup"><span data-stu-id="3227e-335">Border styles of thumb button</span></span> |
| <span data-ttu-id="3227e-336">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-336">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="3227e-337">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-337">Optional pixelmap ID.</span></span> <span data-ttu-id="3227e-338">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве фона.</span><span class="sxs-lookup"><span data-stu-id="3227e-338">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="3227e-339">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-339">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="3227e-340">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-340">Optional pixelmap ID.</span></span> <span data-ttu-id="3227e-341">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве изображения полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="3227e-341">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="3227e-342">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-342">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="3227e-343">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-343">Optional pixelmap ID.</span></span> <span data-ttu-id="3227e-344">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве левой или верхней кнопки в конце.</span><span class="sxs-lookup"><span data-stu-id="3227e-344">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="3227e-345">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-345">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="3227e-346">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-346">Optional pixelmap ID.</span></span> <span data-ttu-id="3227e-347">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве правой или нижней кнопки в конце.</span><span class="sxs-lookup"><span data-stu-id="3227e-347">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="3227e-348">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-348">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="3227e-349">Идентификатор ресурса для цвета, которым заливается ползунок.</span><span class="sxs-lookup"><span data-stu-id="3227e-349">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="3227e-350">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-350">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="3227e-351">Идентификатор ресурса для цвета, которым отображается граница ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-351">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="3227e-352">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="3227e-352">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="3227e-353">Идентификатор ресурса для цвета, которым заливаются торцевые кнопки полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="3227e-353">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="3227e-354">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="3227e-354">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="3227e-355">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-355">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

| <span data-ttu-id="3227e-356">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-356">Members</span></span> | <span data-ttu-id="3227e-357">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-357">Description</span></span> |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="3227e-358">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-358">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="3227e-359">Минимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="3227e-359">Minimum reported value</span></span> |
| <span data-ttu-id="3227e-360">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="3227e-360">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="3227e-361">Максимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="3227e-361">Maximum reported value</span></span> |
| <span data-ttu-id="3227e-362">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="3227e-362">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="3227e-363">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="3227e-363">Current value</span></span> |
| <span data-ttu-id="3227e-364">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="3227e-364">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="3227e-365">Ограничение перемещения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-365">Needle travel limit</span></span> |
| <span data-ttu-id="3227e-366">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="3227e-366">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="3227e-367">Ограничение перемещения стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-367">Needle travel limit</span></span> |
| <span data-ttu-id="3227e-368">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="3227e-368">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="3227e-369">Ширина стрелки в пикселях.</span><span class="sxs-lookup"><span data-stu-id="3227e-369">Needle width in pixel</span></span> |
| <span data-ttu-id="3227e-370">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="3227e-370">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="3227e-371">Высота стрелки в пикселях.</span><span class="sxs-lookup"><span data-stu-id="3227e-371">Needle height in pixel</span></span> |
|<span data-ttu-id="3227e-372">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="3227e-372">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="3227e-373">Положение отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="3227e-373">Needle draw position.</span></span> <span data-ttu-id="3227e-374">Если задан параметр GX_STYLE_SLIDER_VERTICAL, этот параметр определяет смещение стрелки от начальной позиции до левого края ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-374">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="3227e-375">В противном случае он определяет смещение стрелки от начальной позиции до верхнего края ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-375">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="3227e-376">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="3227e-376">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="3227e-377">Смещение активной зоны стрелки, которое определяет смещение от начальной позиции отрисовки стрелки до активной зоны ползунка.</span><span class="sxs-lookup"><span data-stu-id="3227e-377">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="3227e-378">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="3227e-378">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="3227e-379">Определение</span><span class="sxs-lookup"><span data-stu-id="3227e-379">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

| <span data-ttu-id="3227e-380">Элементы</span><span class="sxs-lookup"><span data-stu-id="3227e-380">Members</span></span> | <span data-ttu-id="3227e-381">Описание</span><span class="sxs-lookup"><span data-stu-id="3227e-381">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="3227e-382">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="3227e-382">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="3227e-383">Идентификатор ресурса для растрового изображения, которое отображается для этого кадра.</span><span class="sxs-lookup"><span data-stu-id="3227e-383">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="3227e-384">Этот идентификатор может быть равен 0.</span><span class="sxs-lookup"><span data-stu-id="3227e-384">The ID can be 0.</span></span> |
| <span data-ttu-id="3227e-385">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="3227e-385">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="3227e-386">Смещение от левого края мини-приложения спрайта до растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-386">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="3227e-387">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="3227e-387">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="3227e-388">Смещение от верхнего края мини-приложения спрайта до растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-388">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="3227e-389">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="3227e-389">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="3227e-390">Значение задержки в тактах таймера GUIX, с момента отображения текущего кадра до перехода к следующему кадру спрайта.</span><span class="sxs-lookup"><span data-stu-id="3227e-390">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="3227e-391">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="3227e-391">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="3227e-392">Определяет то, как удаляется фон.</span><span class="sxs-lookup"><span data-stu-id="3227e-392">Define how the background should be erased.</span></span> <span data-ttu-id="3227e-393">Возможные значения для этого поля:</span><span class="sxs-lookup"><span data-stu-id="3227e-393">Possible values for this field are:</span></span><br /><span data-ttu-id="3227e-394">GX_SPRITE_BACKGROUND_NO_ACTION: нет заливки между кадрами;</span><span class="sxs-lookup"><span data-stu-id="3227e-394">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="3227e-395">GX_SPRITE_BACKGROUND_SOLID_FILL: перерисовывается фон спрайта;</span><span class="sxs-lookup"><span data-stu-id="3227e-395">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="3227e-396">GX_SPRITE_BACKGROUND_RESTORE: восстанавливается предыдущее растровое изображение.</span><span class="sxs-lookup"><span data-stu-id="3227e-396">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="3227e-397">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="3227e-397">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="3227e-398">Значение альфа-фактора, которое используется для корректировки отображаемого растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="3227e-398">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="3227e-399">Значение 255 означает, что не нужно применять дополнительный альфа-фактор.</span><span class="sxs-lookup"><span data-stu-id="3227e-399">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="3227e-400">Если растровое изображение содержит альфа-канал, этот альфа-канал будет использоваться вместе с альфа-фактором кадра.</span><span class="sxs-lookup"><span data-stu-id="3227e-400">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
