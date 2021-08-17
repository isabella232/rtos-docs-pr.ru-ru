---
title: Приложение I. Информационные структуры в GUIX
description: Сведения об информационных структурах в GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8730dbfc49ed51716f32c118a25ebffc907b19a54d98d83ede4155f87fbecb7b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784172"
---
# <a name="appendix-i---guix-information-structures"></a>Приложение I. Информационные структуры в GUIX 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>Определение

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| Элементы | Описание |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | Текст для изменения порядка. |
| **gx_bidi_text_info_font**               | Шрифт для отображения текста. Укажите значение GX_NULL, если разбиение строк не требуется. |
| **gx_bidi_text_info_display_width**      | Доступная для отображения ширина. Установите значение -1, если разбиение строк не требуется. |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>Определение

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| Элементы | Описание |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | Указатель на массив переупорядоченного двунаправленного текста. |
| **gx_bidi_resolved_text_info_total_lines**      | Общее число строк разрешенного двунаправленного текста в одном абзаце. |
| **gx_bidi_resolved_text_info_next**             | Информация о разрешенном двунаправленном тексте для следующего абзаца. |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | Общее число шагов, которые пройдет стрелка при перемещении из текущего положения в новое. |
| **gx_circular_gauge_info_animation_delay**       | Число тактов часов GUIX между последовательными шагами анимации. |
| **gx_circular_gauge_info_needle_xpos**           | Расстояние от левого края мини-приложения датчика до центра вращения стрелки. |
| **gx_circular_gauge_info_needle_ypos**           | Расстояние от верхнего края мини-приложения датчика до центра вращения стрелки. |
| **gx_circular_gauge_info_needle_xcor**           | Расстояние от левого края изображения стрелки до центра вращения стрелки. |
| **gx_circular_gauge_info_needle_ycor**           | Расстояние от верхнего края изображения стрелки до центра вращения стрелки. |
| **gx_circular_gauge_info_needle_pixelmap**       | Идентификатор ресурса для растрового изображения, которое будет использоваться для отрисовки стрелки датчика. Это изображение будет повернуто мини-приложением датчика на нужный угол, чтобы правильно отображать стрелку в любом положении. |

Следующая схема демонстрирует применение координат xpos, ypos и xcor, ycor:

![Схема координат Y и X для стрелки](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | Минимальное значение данных, которое используется для расчета масштаба.
| **gx_line_chart_max_val**          | Максимальное значение данных, которое используется для расчета масштаба. |
| **gx_line_chart_data**             | Указатель на массив целых чисел. Эти целые числа отображаются на мини-приложении графика. |
| **gx_line_<side>_margin**          | Отступ от внешней границы окна схемы до области фактической отрисовки графика. Ось схемы и линия данных всегда отображаются внутри этой границы, что позволяет приложению рисовать метки и другие данные внутри окна схемы, но без перекрытия с областью отображения графика. |
| **gx_line_chart_max_data_count**   | Допустимое количество значений данных. Этот параметр используется для расчета масштабирования по оси X или интервала для размещения точек данных. |
| **gx_line_active_data_count**      | Количество значений данных, которые реально присутствуют в массиве данных. В некоторых случаях график может быть настроен на отображение, к примеру, 100 значений, но в одном из обновлений может присутствовать меньший объем данных. |
| **gx_line_axis_line_width**        | Ширина линии, которая используется для горизонтальной и вертикальной осей. |
| **gx_line_data_line_width**        | Ширина отображаемой на графике линии |
| **gx_line_chart_axis_color**       | Идентификатор ресурса для того цвета, который используется для отрисовки осей. |
| **gx_line_chart_line_color**       | Идентификатор ресурса для того цвета, который используется для линии графика. |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>Определение

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| Элементы | Описание |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | Идентификатор ресурса для изображения курсора мыши. |
| **gx_mouse_cursor_hotspot_x**      | Отступ от левого края изображения курсора до активной зоны на этом изображении. |
| **gx_mouse_cursor_hotspot_y**      | Отступ от верхнего края изображения курсора до активной зоны на этом изображении. |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>Определение

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| Элементы | Описание |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | Минимальное расстояние перетаскивания за один такт таймера GUIX, которое требуется для срабатывания события FLICK. Вызовите GX_FIXED_VAL_MAKE, чтобы создать значение с типом данных числа с фиксированной точкой. |
| **gx_pen_configuration_max_pen_speed_ticks** | Максимальная скорость перетаскивания в тактах таймера GUIX, которая требуется для срабатывания события FLICK. | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>Определение

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| Элементы | Описание |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Идентификатор ресурса для растрового изображения, которое используется для заполнения до отрисовки стрелки. Если верхнее растровое изображение для фона не задано, этот же ресурс используется для заполнения как до, так и после отрисовки стрелки. |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | Идентификатор ресурса для растрового изображения, которое используется для заполнения после отрисовки стрелки. |
| **gx_pixelmap_slider_info_needle_pixelmap**           | Идентификатор ресурса для растрового изображения стрелки. |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**Определение**

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

| Элементы | Описание |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | Минимальное отображаемое значение. |
| **gx_progress_bar_info_max_val**             | Максимальное отображаемое значение. |
| **gx_progress_bar_info_current_val**         | Текущее значение |
| **gx_progress_bar_info_font_id**             | Идентификатор ресурса для шрифта, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения.      |
| **gx_progress_bar_normal_text_color**        | Идентификатор ресурса для цвета текста нормального состояния, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_progress_bar_selected_text_color**      | Идентификатор ресурса для цвета текста при наведении фокуса, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_progress_bar_disabled_text_color**      | Идентификатор ресурса для цвета текста при отключении GX_STYLE_ENABLED, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_progress_bar_fill_pixelmap**            | Идентификатор ресурса растрового изображения для заполнения фона.|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | Координата X для положения мини-приложения. |
| **gx_radial_progress_bar_info_ycenter**           | Координата Y для положения мини-приложения.  |
| **gx_radial_progress_bar_info_radius**            | Радиус круга, обозначающего ход выполнения. |
| **gx_radial_progress_bar_info_current_val**       | Текущее значение в пределах от –360 до +360, которое обозначает угловую разницу между положением привязки и верхней точкой верхней дуги. Отрицательные значения означают отрисовку дуги в направлении по часовой стрелке, начиная от положения привязки. При положительном значении дуга отрисовывается в направлении против часовой стрелки, начиная от положения привязки. Приложение должно самостоятельно масштабировать значения реальных величин, используемых для определения угла поворота в мини-приложении индикатора выполнения. |
| **gx_radial_progress_bar_anchor_val**             | Начальный угол для верхней дуги хода выполнения. Это значение задается целым числом градусов, где значение 0 соответствует положению "строго направо", а значение 90 — "строго вверх". |
| **gx_radial_progress_bar_font_id**                | Идентификатор ресурса для шрифта, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_radial_progress_bar_normal_text_color**      | Идентификатор ресурса для цвета текста нормального состояния, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_radial_progress_bar_selected_text_color**    |Идентификатор ресурса для цвета текста при наведении фокуса, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_radial_progress_bar_disabled_text_color**    | Идентификатор ресурса для цвета текста при отключении GX_STYLE_ENABLED, который используется для отрисовки необязательного текстового значения в мини-приложении индикатора выполнения. |
| **gx_radial_progress_bar_normal_brush_width**     | Ширина нижнего круга хода выполнения. |
| **gx_radial_progress_bar_selected_brush_width**   | Ширина верхней дуги хода выполнения, при этом она может быть уже, шире или одной ширины с нижним кругом. |
| **gx_radial_progress_bar_normal_brush_color**     | Идентификатор ресурса для цвета, которым заполняется нижний круг хода выполнения. |
| **gx_radial_progress_bar_selected_brush_color**   | Идентификатор ресурса для цвета, которым заполняется верхняя дуга хода выполнения. |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | Расстояние от левого края мини-приложения ползунка до центра вращения стрелки. |
| **gx_radial_slider_info_ycenter**             | Расстояние от верхнего края мини-приложения ползунка до центра вращения стрелки. |
| **gx_radial_slider_info_radius**              | Радиус круга для радиального ползунка. |
| **gx_radial_slider_info_track_width**         | Ширина дорожки для радиального ползунка. |
| **gx_radial_slider_info_current_angle**       | Текущий угол поворота ползунка. |
| **gx_radial_slider_info_min_angle**           | Минимальный угол поворота ползунка. |
| **gx_radial_slider_info_max_angle**           | Максимальный угол поворота ползунка. |
| **gx_radial_slider_info_angle_list**          | Список значений угла, который определяет положения привязки. Если этот параметр задан, ползунок может находиться только в одном из определенных этим списком положений. |
| **gx_radial_slider_info_list_count**          | Число положений привязки. |
| **gx_radial_slider_info_background_pixelmap** | Идентификатор ресурса для фонового растрового изображения. |
| **gx_radial_slider_info_needle_pixelmap**     | Идентификатор ресурса для растрового изображения стрелки. |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>Определение

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| Элементы | Описание |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | Левый край прямоугольника.   |  
| **gx_rectangle_top**             | Верхний край прямоугольника.    | 
| **gx_rectangle_right**           | Правый край прямоугольника.  |
| **gx_rectangle_bottom**          | Нижний край прямоугольника. |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>Определение

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| Элементы | Описание |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | Идентификатор ресурса для нормального шрифта текста. |
| **gx_rich_text_fonts_bold_id**     | Идентификатор ресурса для полужирного шрифта текста. |
| **gx_rich_text_fonts_italic_id**   | Идентификатор ресурса для курсивного шрифта текста. |
| **gx_rich_text_fonts_bold_italic_id** | Идентификатор ресурса для полужирного курсивного шрифта текста. |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**Определение**

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

| Элементы | Описание |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | Текущее положение прокрутки       |
| **gx_scroll_minimum**   | Минимальное отображаемое положение.     |
| **gx_scroll_maximum**   | Максимальное отображаемое положение.     |
| **gx_scroll_visible**   | Видимый диапазон родительского окна.   |
| **gx_scroll_increment** | Минимальное значение диапазона для полосы прокрутки. |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | Ширина мини-приложения полосы прокрутки, в пикселях. |
| **gx_scroll_thumb_width**                | Ширина бегунка, скользящего по полосе прокрутки, в пикселях. Это значение обычно на несколько пикселей меньше, чем общая ширина полосы прокрутки. |
| **gx_scroll_thumb_travel_min**           | Смещение от конца полосы прокрутки до точки минимального хода ползунка. Это ограничение не позволяет уводить ползунок до самого края полосы прокрутки. |
| **gx_scroll_thumb_travel_max**           | Смещение от конца полосы прокрутки до точки максимального хода ползунка. Это ограничение не позволяет уводить ползунок до самого края полосы прокрутки. |
| **gx_scroll_thumb_border_style**         | Стиль границы для ползунка |
| **gx_scroll_fill_pixelmap**              | Необязательный идентификатор растрового изображения. Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве фона. |
| **gx_scroll_thumb_pixelmap**             | Необязательный идентификатор растрового изображения. Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве изображения полосы прокрутки. |
| **gx_scroll_up_pixelmap**                | Необязательный идентификатор растрового изображения. Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве левой или верхней кнопки в конце. |
| **gx_scroll_down_pixelmap**              | Необязательный идентификатор растрового изображения. Если этот идентификатор не равен 0, полоса прокрутки использует указанное растровое изображение в качестве правой или нижней кнопки в конце. |
| **gx_scroll_thumb_color**                | Идентификатор ресурса для цвета, которым заливается ползунок. |
| **gx_scroll_thumb_border_color**         | Идентификатор ресурса для цвета, которым отображается граница ползунка. | 
| **gx_scroll_button_color**               | Идентификатор ресурса для цвета, которым заливаются торцевые кнопки полосы прокрутки. |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | Минимальное отображаемое значение. |
| **gx_slider_info_max_val**              | Максимальное отображаемое значение. |
| **gx_slider_info_current_value**        | Текущее значение |
| **gx_slider_info_min_travel**           | Ограничение перемещения стрелки. |
| **gx_slider_info_max_travel**           | Ограничение перемещения стрелки. |
| **gx_slider_info_needle_width**         | Ширина стрелки в пикселях. |
| **gx_slider_info_needle_height**        | Высота стрелки в пикселях. |
|**gx_slider_info_needle_inset**          | Положение отрисовки стрелки. Если задан параметр GX_STYLE_SLIDER_VERTICAL, этот параметр определяет смещение стрелки от начальной позиции до левого края ползунка. В противном случае он определяет смещение стрелки от начальной позиции до верхнего края ползунка. |
| **gx_slider_info_needle_hotspot_offset** | Смещение активной зоны стрелки, которое определяет смещение от начальной позиции отрисовки стрелки до активной зоны ползунка. |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>Определение

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

| Элементы | Описание |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | Идентификатор ресурса для растрового изображения, которое отображается для этого кадра. Этот идентификатор может быть равен 0. |
| **gx_sprite_frame_x_offset**             | Смещение от левого края мини-приложения спрайта до растрового изображения. |
| **gx_sprite_frame_y_offset**             | Смещение от верхнего края мини-приложения спрайта до растрового изображения. |
| **gx_sprite_frame_delay**                | Значение задержки в тактах таймера GUIX, с момента отображения текущего кадра до перехода к следующему кадру спрайта. |
| **gx_sprite_frame_background_operation** | Определяет то, как удаляется фон. Возможные значения для этого поля:<br />GX_SPRITE_BACKGROUND_NO_ACTION: нет заливки между кадрами;<br />GX_SPRITE_BACKGROUND_SOLID_FILL: перерисовывается фон спрайта;<br />GX_SPRITE_BACKGROUND_RESTORE: восстанавливается предыдущее растровое изображение. |
| **gx_sprite_frame_alpha**                | Значение альфа-фактора, которое используется для корректировки отображаемого растрового изображения. Значение 255 означает, что не нужно применять дополнительный альфа-фактор. Если растровое изображение содержит альфа-канал, этот альфа-канал будет использоваться вместе с альфа-фактором кадра. |
