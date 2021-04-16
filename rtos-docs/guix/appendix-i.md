---
title: Приложение I. Информационные структуры в GUIX
description: Сведения об информационных структурах в GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815527"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="b7275-103">Приложение I. Информационные структуры в GUIX</span><span class="sxs-lookup"><span data-stu-id="b7275-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="b7275-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-105">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="b7275-106">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7275-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b7275-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="b7275-108">Текст для изменения порядка.</span><span class="sxs-lookup"><span data-stu-id="b7275-108">Text for reordering</span></span> |
| <span data-ttu-id="b7275-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="b7275-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="b7275-110">Шрифт для отображения текста. Укажите значение GX_NULL, если разбиение строк не требуется.</span><span class="sxs-lookup"><span data-stu-id="b7275-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="b7275-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="b7275-112">Доступная для отображения ширина. Установите значение -1, если разбиение строк не требуется.</span><span class="sxs-lookup"><span data-stu-id="b7275-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="b7275-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-114">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="b7275-115">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7275-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b7275-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="b7275-117">Указатель на массив переупорядоченного двунаправленного текста.</span><span class="sxs-lookup"><span data-stu-id="b7275-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="b7275-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="b7275-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="b7275-119">Общее число строк разрешенного двунаправленного текста в одном абзаце.</span><span class="sxs-lookup"><span data-stu-id="b7275-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="b7275-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="b7275-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="b7275-121">Информация о разрешенном двунаправленном тексте для следующего абзаца.</span><span class="sxs-lookup"><span data-stu-id="b7275-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="b7275-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7275-123">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-123">Definition</span></span>

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
### <a name="members"></a><span data-ttu-id="b7275-124">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="b7275-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="b7275-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="b7275-126">Общее число шагов, которые пройдет стрелка при перемещении из текущего положения в новое.</span><span class="sxs-lookup"><span data-stu-id="b7275-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="b7275-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="b7275-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="b7275-128">Число тактов часов GUIX между последовательными шагами анимации.</span><span class="sxs-lookup"><span data-stu-id="b7275-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="b7275-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="b7275-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="b7275-130">Расстояние от левого края мини-приложения датчика до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7275-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="b7275-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="b7275-132">Расстояние от верхнего края мини-приложения датчика до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7275-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="b7275-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="b7275-134">Расстояние от левого края изображения стрелки до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7275-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="b7275-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="b7275-136">Расстояние от верхнего края изображения стрелки до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7275-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="b7275-138">Идентификатор ресурса для растрового изображения, которое будет использоваться для отрисовки стрелки датчика.</span><span class="sxs-lookup"><span data-stu-id="b7275-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="b7275-139">Это изображение будет повернуто мини-приложением датчика на нужный угол, чтобы правильно отображать стрелку в любом положении.</span><span class="sxs-lookup"><span data-stu-id="b7275-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="b7275-140">Следующая схема демонстрирует применение координат xpos, ypos и xcor, ycor:</span><span class="sxs-lookup"><span data-stu-id="b7275-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Схема координат Y и X для стрелки](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="b7275-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7275-143">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-143">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-144">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7275-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="b7275-146">Минимальное значение данных, которое используется для расчета масштаба.</span><span class="sxs-lookup"><span data-stu-id="b7275-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="b7275-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="b7275-148">Максимальное значение данных, которое используется для расчета масштаба.</span><span class="sxs-lookup"><span data-stu-id="b7275-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="b7275-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="b7275-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="b7275-150">Указатель на массив целых чисел.</span><span class="sxs-lookup"><span data-stu-id="b7275-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="b7275-151">Эти целые числа отображаются на мини-приложении графика.</span><span class="sxs-lookup"><span data-stu-id="b7275-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="b7275-152">**gx_line_<side>_margin**</span><span class="sxs-lookup"><span data-stu-id="b7275-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="b7275-153">Отступ от внешней границы окна схемы до области фактической отрисовки графика.</span><span class="sxs-lookup"><span data-stu-id="b7275-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="b7275-154">Ось схемы и линия данных всегда отображаются внутри этой границы, что позволяет приложению рисовать метки и другие данные внутри окна схемы, но без перекрытия с областью отображения графика.</span><span class="sxs-lookup"><span data-stu-id="b7275-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="b7275-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="b7275-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="b7275-156">Допустимое количество значений данных.</span><span class="sxs-lookup"><span data-stu-id="b7275-156">The number of data values which may be present.</span></span> <span data-ttu-id="b7275-157">Этот параметр используется для расчета масштабирования по оси X или интервала для размещения точек данных.</span><span class="sxs-lookup"><span data-stu-id="b7275-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="b7275-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="b7275-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="b7275-159">Количество значений данных, которые реально присутствуют в массиве данных.</span><span class="sxs-lookup"><span data-stu-id="b7275-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="b7275-160">В некоторых случаях график может быть настроен на отображение, к примеру, 100 значений, но в одном из обновлений может присутствовать меньший объем данных.</span><span class="sxs-lookup"><span data-stu-id="b7275-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="b7275-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="b7275-162">Ширина линии, которая используется для горизонтальной и вертикальной осей.</span><span class="sxs-lookup"><span data-stu-id="b7275-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="b7275-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="b7275-164">Ширина отображаемой на графике линии</span><span class="sxs-lookup"><span data-stu-id="b7275-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="b7275-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="b7275-166">Идентификатор ресурса для того цвета, который используется для отрисовки осей.</span><span class="sxs-lookup"><span data-stu-id="b7275-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="b7275-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="b7275-168">Идентификатор ресурса для того цвета, который используется для линии графика.</span><span class="sxs-lookup"><span data-stu-id="b7275-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="b7275-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-170">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="b7275-171">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7275-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="b7275-173">Идентификатор ресурса для изображения курсора мыши.</span><span class="sxs-lookup"><span data-stu-id="b7275-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="b7275-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="b7275-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="b7275-175">Отступ от левого края изображения курсора до активной зоны на этом изображении.</span><span class="sxs-lookup"><span data-stu-id="b7275-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="b7275-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="b7275-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="b7275-177">Отступ от верхнего края изображения курсора до активной зоны на этом изображении.</span><span class="sxs-lookup"><span data-stu-id="b7275-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="b7275-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="b7275-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-179">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="b7275-180">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b7275-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="b7275-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="b7275-182">Минимальное расстояние перетаскивания за один такт таймера GUIX, которое требуется для срабатывания события FLICK.</span><span class="sxs-lookup"><span data-stu-id="b7275-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="b7275-183">Вызовите GX_FIXED_VAL_MAKE, чтобы создать значение с типом данных числа с фиксированной точкой.</span><span class="sxs-lookup"><span data-stu-id="b7275-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="b7275-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="b7275-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="b7275-185">Максимальная скорость перетаскивания в тактах таймера GUIX, которая требуется для срабатывания события FLICK.</span><span class="sxs-lookup"><span data-stu-id="b7275-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="b7275-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-187">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="b7275-188">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="b7275-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="b7275-190">Идентификатор ресурса для растрового изображения, которое используется для заполнения до отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="b7275-191">Если верхнее растровое изображение для фона не задано, этот же ресурс используется для заполнения как до, так и после отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="b7275-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="b7275-193">Идентификатор ресурса для растрового изображения, которое используется для заполнения после отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="b7275-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="b7275-195">Идентификатор ресурса для растрового изображения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="b7275-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-197">**Определение**</span><span class="sxs-lookup"><span data-stu-id="b7275-197">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-198">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b7275-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="b7275-200">Минимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="b7275-200">Minimum reported value</span></span> |
| <span data-ttu-id="b7275-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="b7275-202">Максимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="b7275-202">Maximum reported value</span></span> |
| <span data-ttu-id="b7275-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="b7275-204">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="b7275-204">Current value</span></span> |
| <span data-ttu-id="b7275-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="b7275-206">Идентификатор ресурса для шрифта, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="b7275-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="b7275-208">Идентификатор ресурса для цвета текста нормального состояния, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="b7275-210">Идентификатор ресурса для цвета текста при наведении фокуса, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="b7275-212">Идентификатор ресурса для цвета текста при отключении GX_STYLE_ENABLED, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="b7275-214">Идентификатор ресурса растрового изображения для заполнения фона.</span><span class="sxs-lookup"><span data-stu-id="b7275-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="b7275-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7275-216">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-216">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-217">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="b7275-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b7275-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="b7275-219">Координата X для положения мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="b7275-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="b7275-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b7275-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="b7275-221">Координата Y для положения мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="b7275-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="b7275-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b7275-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="b7275-223">Радиус круга, обозначающего ход выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="b7275-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="b7275-225">Текущее значение в пределах от –360 до +360, которое обозначает угловую разницу между положением привязки и верхней точкой верхней дуги. Отрицательные значения означают отрисовку дуги в направлении по часовой стрелке, начиная от положения привязки.</span><span class="sxs-lookup"><span data-stu-id="b7275-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b7275-226">При положительном значении дуга отрисовывается в направлении против часовой стрелки, начиная от положения привязки.</span><span class="sxs-lookup"><span data-stu-id="b7275-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b7275-227">Приложение должно самостоятельно масштабировать значения реальных величин, используемых для определения угла поворота в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="b7275-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="b7275-229">Начальный угол для верхней дуги хода выполнения. Это значение задается целым числом градусов, где значение 0 соответствует положению "строго направо", а значение 90 — "строго вверх".</span><span class="sxs-lookup"><span data-stu-id="b7275-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="b7275-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="b7275-231">Идентификатор ресурса для шрифта, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="b7275-233">Идентификатор ресурса для цвета текста нормального состояния, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="b7275-235">Идентификатор ресурса для цвета текста при наведении фокуса, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="b7275-237">Идентификатор ресурса для цвета текста при отключении GX_STYLE_ENABLED, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7275-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="b7275-239">Ширина нижнего круга хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="b7275-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="b7275-241">Ширина верхней дуги хода выполнения, при этом она может быть уже, шире или одной ширины с нижним кругом.</span><span class="sxs-lookup"><span data-stu-id="b7275-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="b7275-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="b7275-243">Идентификатор ресурса для цвета, которым заполняется нижний круг хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="b7275-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="b7275-245">Идентификатор ресурса для цвета, которым заполняется верхняя дуга хода выполнения.</span><span class="sxs-lookup"><span data-stu-id="b7275-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="b7275-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-247">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-247">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-248">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="b7275-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b7275-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="b7275-250">Расстояние от левого края мини-приложения ползунка до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b7275-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b7275-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="b7275-252">Расстояние от верхнего края мини-приложения ползунка до центра вращения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b7275-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b7275-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="b7275-254">Радиус круга для радиального ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="b7275-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="b7275-256">Ширина дорожки для радиального ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-256">Width of radial slider track</span></span> |
| <span data-ttu-id="b7275-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="b7275-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="b7275-258">Текущий угол поворота ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-258">Current slider angle</span></span> |
| <span data-ttu-id="b7275-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="b7275-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="b7275-260">Минимальный угол поворота ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-260">Minimum slider angle</span></span> |
| <span data-ttu-id="b7275-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="b7275-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="b7275-262">Максимальный угол поворота ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-262">Maximum slider angle</span></span> |
| <span data-ttu-id="b7275-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="b7275-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="b7275-264">Список значений угла, который определяет положения привязки. Если этот параметр задан, ползунок может находиться только в одном из определенных этим списком положений.</span><span class="sxs-lookup"><span data-stu-id="b7275-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="b7275-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="b7275-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="b7275-266">Число положений привязки.</span><span class="sxs-lookup"><span data-stu-id="b7275-266">Number of anchor angles</span></span> |
| <span data-ttu-id="b7275-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="b7275-268">Идентификатор ресурса для фонового растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="b7275-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="b7275-270">Идентификатор ресурса для растрового изображения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="b7275-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="b7275-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="b7275-272">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="b7275-273">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="b7275-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="b7275-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="b7275-275">Левый край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="b7275-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="b7275-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="b7275-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="b7275-277">Верхний край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="b7275-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="b7275-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="b7275-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="b7275-279">Правый край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="b7275-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="b7275-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="b7275-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="b7275-281">Нижний край прямоугольника.</span><span class="sxs-lookup"><span data-stu-id="b7275-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="b7275-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="b7275-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-283">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="b7275-284">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7275-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="b7275-286">Идентификатор ресурса для нормального шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="b7275-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="b7275-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="b7275-288">Идентификатор ресурса для полужирного шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="b7275-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="b7275-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="b7275-290">Идентификатор ресурса для курсивного шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="b7275-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="b7275-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b7275-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="b7275-292">Идентификатор ресурса для полужирного курсивного шрифта текста.</span><span class="sxs-lookup"><span data-stu-id="b7275-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="b7275-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="b7275-294">**Определение**</span><span class="sxs-lookup"><span data-stu-id="b7275-294">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-295">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="b7275-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="b7275-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="b7275-297">Текущее положение прокрутки</span><span class="sxs-lookup"><span data-stu-id="b7275-297">Current scroll position</span></span>       |
| <span data-ttu-id="b7275-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="b7275-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="b7275-299">Минимальное отображаемое положение.</span><span class="sxs-lookup"><span data-stu-id="b7275-299">Minimum reported position</span></span>     |
| <span data-ttu-id="b7275-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="b7275-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="b7275-301">Максимальное отображаемое положение.</span><span class="sxs-lookup"><span data-stu-id="b7275-301">Maximum reported position</span></span>     |
| <span data-ttu-id="b7275-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="b7275-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="b7275-303">Видимый диапазон родительского окна.</span><span class="sxs-lookup"><span data-stu-id="b7275-303">Parent window visible range</span></span>   |
| <span data-ttu-id="b7275-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="b7275-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="b7275-305">Минимальное значение диапазона для полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="b7275-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="b7275-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="b7275-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="b7275-307">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-307">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-308">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b7275-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="b7275-310">Ширина мини-приложения полосы прокрутки, в пикселях.</span><span class="sxs-lookup"><span data-stu-id="b7275-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="b7275-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="b7275-312">Ширина бегунка, скользящего по полосе прокрутки, в пикселях.</span><span class="sxs-lookup"><span data-stu-id="b7275-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="b7275-313">Это значение обычно на несколько пикселей меньше, чем общая ширина полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="b7275-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="b7275-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="b7275-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="b7275-315">Смещение от конца полосы прокрутки до точки минимального хода ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="b7275-316">Это ограничение не позволяет уводить ползунок до самого края полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="b7275-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b7275-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="b7275-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="b7275-318">Смещение от конца полосы прокрутки до точки максимального хода ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="b7275-319">Это ограничение не позволяет уводить ползунок до самого края полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="b7275-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b7275-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="b7275-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="b7275-321">Стиль границы для ползунка</span><span class="sxs-lookup"><span data-stu-id="b7275-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="b7275-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="b7275-323">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-323">Optional pixelmap ID.</span></span> <span data-ttu-id="b7275-324">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве фона.</span><span class="sxs-lookup"><span data-stu-id="b7275-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="b7275-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="b7275-326">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-326">Optional pixelmap ID.</span></span> <span data-ttu-id="b7275-327">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве изображения полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="b7275-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="b7275-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="b7275-329">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-329">Optional pixelmap ID.</span></span> <span data-ttu-id="b7275-330">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве левой или верхней кнопки в конце.</span><span class="sxs-lookup"><span data-stu-id="b7275-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="b7275-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="b7275-332">Необязательный идентификатор растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-332">Optional pixelmap ID.</span></span> <span data-ttu-id="b7275-333">Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве правой или нижней кнопки в конце.</span><span class="sxs-lookup"><span data-stu-id="b7275-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="b7275-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="b7275-335">Идентификатор ресурса для цвета, которым заливается ползунок.</span><span class="sxs-lookup"><span data-stu-id="b7275-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="b7275-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="b7275-337">Идентификатор ресурса для цвета, которым отображается граница ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="b7275-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="b7275-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="b7275-339">Идентификатор ресурса для цвета, которым заливаются торцевые кнопки полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="b7275-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="b7275-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b7275-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7275-341">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-341">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-342">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="b7275-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="b7275-344">Минимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="b7275-344">Minimum reported value</span></span> |
| <span data-ttu-id="b7275-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b7275-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="b7275-346">Максимальное отображаемое значение.</span><span class="sxs-lookup"><span data-stu-id="b7275-346">Maximum reported value</span></span> |
| <span data-ttu-id="b7275-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="b7275-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="b7275-348">Текущее значение</span><span class="sxs-lookup"><span data-stu-id="b7275-348">Current value</span></span> |
| <span data-ttu-id="b7275-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="b7275-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="b7275-350">Ограничение перемещения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-350">Needle travel limit</span></span> |
| <span data-ttu-id="b7275-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="b7275-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="b7275-352">Ограничение перемещения стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-352">Needle travel limit</span></span> |
| <span data-ttu-id="b7275-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="b7275-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="b7275-354">Ширина стрелки в пикселях.</span><span class="sxs-lookup"><span data-stu-id="b7275-354">Needle width in pixel</span></span> |
| <span data-ttu-id="b7275-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="b7275-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="b7275-356">Высота стрелки в пикселях.</span><span class="sxs-lookup"><span data-stu-id="b7275-356">Needle height in pixel</span></span> |
|<span data-ttu-id="b7275-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="b7275-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="b7275-358">Положение отрисовки стрелки.</span><span class="sxs-lookup"><span data-stu-id="b7275-358">Needle draw position.</span></span> <span data-ttu-id="b7275-359">Если задан параметр GX_STYLE_SLIDER_VERTICAL, этот параметр определяет смещение стрелки от начальной позиции до левого края ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="b7275-360">В противном случае он определяет смещение стрелки от начальной позиции до верхнего края ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="b7275-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="b7275-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="b7275-362">Смещение активной зоны стрелки, которое определяет смещение от начальной позиции отрисовки стрелки до активной зоны ползунка.</span><span class="sxs-lookup"><span data-stu-id="b7275-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="b7275-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="b7275-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="b7275-364">Определение</span><span class="sxs-lookup"><span data-stu-id="b7275-364">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7275-365">Элементы</span><span class="sxs-lookup"><span data-stu-id="b7275-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b7275-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7275-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="b7275-367">Идентификатор ресурса для растрового изображения, которое отображается для этого кадра.</span><span class="sxs-lookup"><span data-stu-id="b7275-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="b7275-368">Этот идентификатор может быть равен 0.</span><span class="sxs-lookup"><span data-stu-id="b7275-368">The ID can be 0.</span></span> |
| <span data-ttu-id="b7275-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="b7275-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="b7275-370">Смещение от левого края мини-приложения спрайта до растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="b7275-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="b7275-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="b7275-372">Смещение от верхнего края мини-приложения спрайта до растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="b7275-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="b7275-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="b7275-374">Значение задержки в тактах таймера GUIX, с момента отображения текущего кадра до перехода к следующему кадру спрайта.</span><span class="sxs-lookup"><span data-stu-id="b7275-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="b7275-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="b7275-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="b7275-376">Определяет то, как удаляется фон.</span><span class="sxs-lookup"><span data-stu-id="b7275-376">Define how the background should be erased.</span></span> <span data-ttu-id="b7275-377">Возможные значения для этого поля:</span><span class="sxs-lookup"><span data-stu-id="b7275-377">Possible values for this field are:</span></span><br /><span data-ttu-id="b7275-378">GX_SPRITE_BACKGROUND_NO_ACTION: нет заливки между кадрами;</span><span class="sxs-lookup"><span data-stu-id="b7275-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="b7275-379">GX_SPRITE_BACKGROUND_SOLID_FILL: перерисовывается фон спрайта;</span><span class="sxs-lookup"><span data-stu-id="b7275-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="b7275-380">GX_SPRITE_BACKGROUND_RESTORE: восстанавливается предыдущее растровое изображение.</span><span class="sxs-lookup"><span data-stu-id="b7275-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="b7275-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="b7275-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="b7275-382">Значение альфа-фактора, которое используется для корректировки отображаемого растрового изображения.</span><span class="sxs-lookup"><span data-stu-id="b7275-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="b7275-383">Значение 255 означает, что не нужно применять дополнительный альфа-фактор.</span><span class="sxs-lookup"><span data-stu-id="b7275-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="b7275-384">Если растровое изображение содержит альфа-канал, этот альфа-канал будет использоваться вместе с альфа-фактором кадра.</span><span class="sxs-lookup"><span data-stu-id="b7275-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
