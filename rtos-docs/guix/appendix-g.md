---
title: Приложение Ж. Структура шрифта GUIX
description: Узнайте о структуре шрифта GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5f0232e6c21851014b85cfe7b07795062fd1e8d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815564"
---
# <a name="appendix-g---guix-font-structure"></a><span data-ttu-id="9f457-103">Приложение Ж. Структура шрифта GUIX</span><span class="sxs-lookup"><span data-stu-id="9f457-103">Appendix G - GUIX Font Structure</span></span>

<span data-ttu-id="9f457-104">Шрифты GUIX обычно создаются приложением GUIX Studio, а глифы шрифтов отображаются драйвером дисплея GUIX.</span><span class="sxs-lookup"><span data-stu-id="9f457-104">GUIX fonts are normally produced by the GUIX Studio application, and font glyphs are rendered by the GUIX display driver.</span></span> <span data-ttu-id="9f457-105">Программное обеспечение приложения должно указывать только шрифт и цвета, которые должны использоваться каждым мини-приложением с текстом.</span><span class="sxs-lookup"><span data-stu-id="9f457-105">The application software need only specify the font and colors that each text display widget should use.</span></span> <span data-ttu-id="9f457-106">Структуры данных шрифтов GUIX описаны здесь для полноты информации. Это позволит разработчикам создавать собственные методы для формирования шрифтов или преобразования других шрифтов в формат шрифта GUIX.</span><span class="sxs-lookup"><span data-stu-id="9f457-106">The GUIX font data structures are documented here for completeness, and to enable developers to create their own methods for generating or converting other fonts into the GUIX font format.</span></span>

<span data-ttu-id="9f457-107">Каждый шрифт GUIX начинается со структуры GX_FONT.</span><span class="sxs-lookup"><span data-stu-id="9f457-107">Each GUIX font starts with a GX_FONT structure.</span></span> <span data-ttu-id="9f457-108">Структура GX_FONT определяет глобальные параметры шрифта, такие как символ шрифта и высота строки шрифта.</span><span class="sxs-lookup"><span data-stu-id="9f457-108">The GX_FONT structure defines global font parameters, such as the character included within the font and the line height of the font.</span></span> <span data-ttu-id="9f457-109">Структура GX_FONT указывает на массив структур GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="9f457-109">The GX_FONT structure points at an array of GX_GLYPH structures.</span></span> <span data-ttu-id="9f457-110">Каждая структура GX_GLYPH определяет ширину, высоту и смещение от базовой линии для определенного глифа символа.</span><span class="sxs-lookup"><span data-stu-id="9f457-110">Each GX_GLYPH structure defines the width, height, and baseline offset of one specific character glyph.</span></span> <span data-ttu-id="9f457-111">Структура GX_GLYPH также указывает на фактические данные растрового изображения глифа (которые могут иметь значение NULL для символов пробела).</span><span class="sxs-lookup"><span data-stu-id="9f457-111">The GX_GLYPH structure also points to the actual glyph bitmap data (which may be NULL for whitespace characters).</span></span>

<span data-ttu-id="9f457-112">Структура GX_FONT, содержащаяся в файле gx_api.h, объявляется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9f457-112">The GX_FONT structure, contained in gx_api.h, is declared as follows:</span></span>

```c
typedef struct GX_FONT_STRUCT
{
    GX_UBYTE                     gx_font_format
    GX_UBYTE                     gx_font_prespace
    GX_UBYTE                     gx_font_postspace
    GX_UBYTE                     gx_font_line_height 
    GX_UBYTE                     gx_font_baseline
    USHORT                       gx_font_first_glyph
    USHORT                       gx_font_last_glyph 
    GX_CONST GX_GLYPH           *gx_font_glyphs
    const struct GX_FONT_STRUCT *gx_font_next_page
} GX_FONT;
```

<span data-ttu-id="9f457-113">Поле gx_font_format определяет число битов на пиксель для шрифта и другие флаги, определенные в файле заголовка gx_api.h.</span><span class="sxs-lookup"><span data-stu-id="9f457-113">The gx_font_format field defines the font bits-per-pixel and other flags, as defined in the gx_api.h header file.</span></span>

<span data-ttu-id="9f457-114">Поле gx_font_prespace определяет пространство в пикселях, которое будет пропускаться над каждой строкой текста при многострочном отображении.</span><span class="sxs-lookup"><span data-stu-id="9f457-114">The gx_font_prespace defines the pixel space to skip above each line of text in a multi-line text display.</span></span>

<span data-ttu-id="9f457-115">Поле gx_font_postspace определяет пространство в пикселях, которое будет пропускаться под каждой строкой текста при многострочном отображении.</span><span class="sxs-lookup"><span data-stu-id="9f457-115">The gx_font_postspace field defines the pixel space to skip below each line of text in a multi-line text display.</span></span>

<span data-ttu-id="9f457-116">Поле gx_font_line_height определяет высоту наиболее высокого глифа в шрифте.</span><span class="sxs-lookup"><span data-stu-id="9f457-116">The gx_font_line_height field defines the height of the tallest glyph in the font.</span></span>

<span data-ttu-id="9f457-117">Поле gx_font_baseline определяет расстояние (в пикселях) от верхней строки пикселей глифа до базовой линии шрифта.</span><span class="sxs-lookup"><span data-stu-id="9f457-117">The gx_font_baseline field defines the distance, in pixels, from the top row of glyph pixels to the font baseline.</span></span>

<span data-ttu-id="9f457-118">Поле gx_font_first_glyph определяет кодировку первого символа Юникода, добавленного на эту страницу шрифтов.</span><span class="sxs-lookup"><span data-stu-id="9f457-118">The gx_font_first_glyph field defines the first Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="9f457-119">Поле gx_font_last_glyph определяет кодировку последнего символа Юникода, добавленного на эту страницу шрифтов.</span><span class="sxs-lookup"><span data-stu-id="9f457-119">The gx_font_last_glyph field defines the last Unicode character encoding included in this font page.</span></span>

<span data-ttu-id="9f457-120">Указатель gx_font_glyphs указывает на массив структур GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="9f457-120">The gx_font_glyphs pointer points to an array of GX_GLYPH structures.</span></span> <span data-ttu-id="9f457-121">Размер этого массива должен быть равен числу символов, содержащихся на данной странице шрифтов, то есть:</span><span class="sxs-lookup"><span data-stu-id="9f457-121">This array must be equal in size to the number of characters contained on this font page, i.e</span></span> <span data-ttu-id="9f457-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span><span class="sxs-lookup"><span data-stu-id="9f457-122">(gx_font_last_glyph – gx_font_first_glyph) + 1.</span></span>

<span data-ttu-id="9f457-123">Элемент gx_font_next_page используется для многостраничных шрифтов.</span><span class="sxs-lookup"><span data-stu-id="9f457-123">The gx_font_next_page member is used for multiple page fonts.</span></span> <span data-ttu-id="9f457-124">Многостраничные шрифты используются для расширенных кодировок и для оптимизации размера массивов структур GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="9f457-124">Multiple page fonts are used for extended character sets and to optimize the size of the GX_GLYPH structure arrays.</span></span> <span data-ttu-id="9f457-125">Если все символы шрифта содержатся на одной странице шрифтов или если это последняя страница рассматриваемого шрифта, то для элемента gx_font_next_page задается значение GX_NULL.</span><span class="sxs-lookup"><span data-stu-id="9f457-125">If all of the characters of the font are contained within one font page, or if this is the last page of the font in question, the gx_font_next_page member is set to GX_NULL.</span></span>

<span data-ttu-id="9f457-126">Как отмечалось ранее, приведенная выше структура GX_FONT содержит указатель на массив структур GX_GLYPHS.</span><span class="sxs-lookup"><span data-stu-id="9f457-126">As noted above, the GX_FONT structure above contains a pointer to an array of GX_GLYPHS structures.</span></span> <span data-ttu-id="9f457-127">Для каждого символа на странице шрифтов должна существовать одна структура GX_GLYPH.</span><span class="sxs-lookup"><span data-stu-id="9f457-127">There must be one GX_GLYPH structure for each character on the font page.</span></span> <span data-ttu-id="9f457-128">Структура GX_GLYPH определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9f457-128">The GX_GLYPH structure is defined as:</span></span>

```c
typedef struct GX_GLYPH_STRUCT
{
    GX_CONST GX_UBYTE *gx_glyph_map;
    GX_BYTE            gx_glyph_ascent;
    GX_BYTE            gx_glyph_descent;
    GX_BYTE            gx_glyph_advance;
    GX_BYTE            gx_glyph_leading;
    GX_UBYTE           gx_glyph_width;
    GX_UBYTE           gx_glyph_height;
} GX_GLYPH;
```

<span data-ttu-id="9f457-129">Указатель gx_glyph_map указывает на растровое изображение глифа.</span><span class="sxs-lookup"><span data-stu-id="9f457-129">The gx_glyph_map pointer points to the glyph bitmap.</span></span> <span data-ttu-id="9f457-130">Этот указатель может иметь значение GX_NULL для символов пробела.</span><span class="sxs-lookup"><span data-stu-id="9f457-130">This pointer may be GX_NULL for whitespace characters.</span></span> <span data-ttu-id="9f457-131">Данные растрового изображения кодируются с альфа-фактором 1 бит/пкс, 2 бит/пкс, 4 бит/пкс или 8 бит/пкс.</span><span class="sxs-lookup"><span data-stu-id="9f457-131">The bitmap data is encoded as 1 bpp, 2 bpp, 4 bpp, or 8 bpp alpha values.</span></span> <span data-ttu-id="9f457-132">Для 1-битных данных значение 1 указывает, что пиксель должен быть записан в цвете переднего плана, а значение 0 указывает, что пиксель прозрачный.</span><span class="sxs-lookup"><span data-stu-id="9f457-132">For 1 bit data, a value of 1 indicates that the pixel should be written in the foreground color, and a value of 0 indicates that the pixel is transparent.</span></span> <span data-ttu-id="9f457-133">Для 8-битных данных значения находятся в диапазоне от 0 (полностью прозрачный) до 255 (полностью непрозрачный).</span><span class="sxs-lookup"><span data-stu-id="9f457-133">For 8 bit data, the values range from 0 (fully transparent) to 255 (fully opague).</span></span> <span data-ttu-id="9f457-134">Все промежуточные значения представляют собой значение смешения для шрифтов со сглаживанием.</span><span class="sxs-lookup"><span data-stu-id="9f457-134">All intermediate value represent a blending value for anti-aliased fonts.</span></span> <span data-ttu-id="9f457-135">Данные растровых изображений глифов всегда заполняются байтами до полного выравнивания для форматов, использующих значения данных с альфа-фактором меньше 8 бит/пкс.</span><span class="sxs-lookup"><span data-stu-id="9f457-135">The glyph bitmap data is always padded to full byte alignment for formats using less than 8bpp data values.</span></span>

<span data-ttu-id="9f457-136">Значения gx_glyph_ascent и gx_glyph_descent позволяют расположить глифа вертикально относительно базовой линии шрифта.</span><span class="sxs-lookup"><span data-stu-id="9f457-136">The gx_glyph_ascent and gx_glyph_descent values position the glyph vertically with respect to the font baseline.</span></span>

<span data-ttu-id="9f457-137">Значения gx_glyph_width и gx_glyph_height определяют размер данных растрового изображения глифа.</span><span class="sxs-lookup"><span data-stu-id="9f457-137">The gx_glyph_width and gx_glyph_height values specify the size of the glyph bitmap data.</span></span>

<span data-ttu-id="9f457-138">Значение gx_glyph_advance задает величину смещения в пикселях позиции отрисовки после отображения глифа (она может не совпадать с шириной глифа).</span><span class="sxs-lookup"><span data-stu-id="9f457-138">The gx_glyph_advance value specifies the pixel width to advance the drawing position after drawing the glyph (this may not be equal to the glyph width).</span></span>

<span data-ttu-id="9f457-139">Значение gx_glyph_leading указывает смещение по оси X в пикселях перед отрисовкой глифа.</span><span class="sxs-lookup"><span data-stu-id="9f457-139">The gx_glyph_leading value specifies the pixels to advance in the x-direction prior to rendering the glyph.</span></span>