---
title: Приложение В. Стили мини-приложений в GUIX
description: Сведения о стилях мини-приложений в GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815572"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="bb781-103">Приложение В. Стили мини-приложений в GUIX</span><span class="sxs-lookup"><span data-stu-id="bb781-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="bb781-104">__***Общие стили (используются с большинством типов мини-приложений):***__</span><span class="sxs-lookup"><span data-stu-id="bb781-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="bb781-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="bb781-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="bb781-106">Значение: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="bb781-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="bb781-107">Описание: используйте этот стиль для отрисовки мини-приложения без границы.</span><span class="sxs-lookup"><span data-stu-id="bb781-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="bb781-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="bb781-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="bb781-109">Значение: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="bb781-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="bb781-110">Описание: отрисовка мини-приложения с приподнятой границей.</span><span class="sxs-lookup"><span data-stu-id="bb781-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="bb781-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="bb781-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="bb781-112">Значение: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="bb781-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="bb781-113">Описание: отрисовка мини-приложения с утопленной границей.</span><span class="sxs-lookup"><span data-stu-id="bb781-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="bb781-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="bb781-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="bb781-115">Значение: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="bb781-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="bb781-116">Описание: отрисовка границы шириной один пиксель.</span><span class="sxs-lookup"><span data-stu-id="bb781-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="bb781-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="bb781-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="bb781-118">Значение: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="bb781-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="bb781-119">Описание: отрисовка мини-приложения с толстой границей.</span><span class="sxs-lookup"><span data-stu-id="bb781-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="bb781-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="bb781-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="bb781-121">Значение: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="bb781-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="bb781-122">Описание: значение маски, используемое для тестирования только полей стиля элемента стиля мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="bb781-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="bb781-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="bb781-124">Значение: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="bb781-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="bb781-125">Описание: создание, по крайней мере частично, прозрачного мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="bb781-126">Этот стиль следует использовать, когда мини-приложение не отрисовывается как полностью непрозрачное, в том числе если в качестве фона мини-приложения используется полупрозрачная пиксельная карта.</span><span class="sxs-lookup"><span data-stu-id="bb781-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="bb781-127">Этот флаг стиля сообщает GUIX о том, что родительское мини-приложение должно обновить область фона мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="bb781-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="bb781-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="bb781-129">Значение: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="bb781-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="bb781-130">Описание: указывает, что мини-приложение должно быть отрисовано с использованием цветов и шрифтов состояния выбора.</span><span class="sxs-lookup"><span data-stu-id="bb781-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="bb781-131">Различные типы мини-приложений используют стиль DRAW_SELECTED по-разному, чтобы указать, что мини-приложение в настоящее время выбрано.</span><span class="sxs-lookup"><span data-stu-id="bb781-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="bb781-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="bb781-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="bb781-133">Значение: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="bb781-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="bb781-134">Описание: мини-приложение помечается как включенное, что позволяет ему принимать события пользовательского ввода и формировать выходные сигналы.</span><span class="sxs-lookup"><span data-stu-id="bb781-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="bb781-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="bb781-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="bb781-136">Значение: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="bb781-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="bb781-137">Описание: указывает, что память блока управления мини-приложения выделяется динамически с помощью службы gx_system_memory_allocator при создании мини-приложения и высвобождается при его уничтожении.</span><span class="sxs-lookup"><span data-stu-id="bb781-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="bb781-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="bb781-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="bb781-139">Значение: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="bb781-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="bb781-140">Описание: предписывает функциям рисования GUIX использовать локальный альфа-фактор мини-приложения при его отрисовке.</span><span class="sxs-lookup"><span data-stu-id="bb781-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="bb781-141">Этот флаг обычно используется внутренней логикой GUIX для реализации анимации исчезания мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="bb781-142">__***Стили выравнивания текста (применяются ко всем мини-приложениям, в которых отрисовывается текст):***__</span><span class="sxs-lookup"><span data-stu-id="bb781-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="bb781-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="bb781-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="bb781-144">Значение: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="bb781-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="bb781-145">Описание: текст отрисовывается с выравниванием по левому краю в клиентской области мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="bb781-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="bb781-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="bb781-147">Значение: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="bb781-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="bb781-148">Описание: текст отрисовывается с выравниванием по правому краю в клиентской области мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="bb781-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="bb781-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="bb781-150">Значение: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="bb781-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="bb781-151">Описание: текст отрисовывается с выравниванием по центру в клиентской области мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="bb781-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="bb781-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="bb781-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="bb781-153">Значение: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="bb781-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="bb781-154">Описание: по умолчанию мини-приложения, которые отрисовывают текст, сохраняют только указатель на текст, передаваемый приложением.</span><span class="sxs-lookup"><span data-stu-id="bb781-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="bb781-155">Для статически определенного текста в таблице строк мини-приложению нет смысла создавать частную копию назначенного текста.</span><span class="sxs-lookup"><span data-stu-id="bb781-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="bb781-156">Однако если текст, назначенный мини-приложению, создается динамически с помощью таких функций, как sprint() или gx_utility_ltoa, то часто бывает удобно, чтобы мини-приложение сохраняло собственную частную копию такого текста.</span><span class="sxs-lookup"><span data-stu-id="bb781-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="bb781-157">Это позволяет приложению использовать автоматические или временные переменные при определении текстовых строк. В противном случае ему потребовалось бы определять статические символьные массивы для каждого текстового мини-приложения, использующего динамически определяемый текст.</span><span class="sxs-lookup"><span data-stu-id="bb781-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="bb781-158">Если этот флаг стиля установлен, мини-приложение будет использовать функцию gx_system_memory_allocator для динамического выделения блока памяти, необходимого для хранения частной копии назначенной строки.</span><span class="sxs-lookup"><span data-stu-id="bb781-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="bb781-159">Поэтому этот флаг стиля должен использоваться в приложении, в котором определены функции memory_allocator и memory_deallocator.</span><span class="sxs-lookup"><span data-stu-id="bb781-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="bb781-160">Флаг GX_STYLE_TEXT_COPY не следует снимать после установки, так как это приведет к непредсказуемым результатам.</span><span class="sxs-lookup"><span data-stu-id="bb781-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="bb781-161">__***Стили кнопок (применяются только к типам мини-приложений с кнопками GUIX):***__</span><span class="sxs-lookup"><span data-stu-id="bb781-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="bb781-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="bb781-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="bb781-163">Значение: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="bb781-163">Value 0x00000010</span></span>
  - <span data-ttu-id="bb781-164">Описание: указывает, что кнопка находится в состоянии нажатия или выбора.</span><span class="sxs-lookup"><span data-stu-id="bb781-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="bb781-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="bb781-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="bb781-166">Значение: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="bb781-166">Value 0x00000020</span></span>
  - <span data-ttu-id="bb781-167">Описание: кнопка меняет состояние с нажатого на отжатое и наоборот при каждом событии щелчка мышью.</span><span class="sxs-lookup"><span data-stu-id="bb781-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="bb781-168">Этот стиль обычно используется с кнопками типа "флажок".</span><span class="sxs-lookup"><span data-stu-id="bb781-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="bb781-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="bb781-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="bb781-170">Значение: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="bb781-170">Value 0x00000040</span></span>
  - <span data-ttu-id="bb781-171">Описание: этот стиль указывает, что кнопка может быть единственной выбранной; при ее выборе отменяется выбор других кнопок в группе.</span><span class="sxs-lookup"><span data-stu-id="bb781-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="bb781-172">Этот стиль обычно используется с кнопками типа "переключатель".</span><span class="sxs-lookup"><span data-stu-id="bb781-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="bb781-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="bb781-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="bb781-174">Значение: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="bb781-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="bb781-175">Описание: указывает, что кнопка создает событие щелчка мышью при первоначальном нажатии.</span><span class="sxs-lookup"><span data-stu-id="bb781-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="bb781-176">По умолчанию событие щелчка мышью создается при отпускании кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="bb781-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="bb781-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="bb781-178">Значение: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="bb781-178">Value 0x00000100</span></span>
  - <span data-ttu-id="bb781-179">Описание: указывает, что кнопка должна непрерывно отправлять события щелчка мыши родительскому элементу, когда она удерживается в нажатом состоянии.</span><span class="sxs-lookup"><span data-stu-id="bb781-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="bb781-180">__***Стили списка (применяются только к мини-приложениям GUIX списочного типа):***__</span><span class="sxs-lookup"><span data-stu-id="bb781-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="bb781-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="bb781-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="bb781-182">Значение: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="bb781-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="bb781-183">Описание: зарезервировано</span><span class="sxs-lookup"><span data-stu-id="bb781-183">Description: Reserved</span></span>

<span data-ttu-id="bb781-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="bb781-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="bb781-185">Значение: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="bb781-185">Value 0x00000020</span></span>
  - <span data-ttu-id="bb781-186">Описание: дочерние элементы списка переносятся из начала в конец, когда список перетаскивается или прокручивается за пределы начального или конечного индекса списка.</span><span class="sxs-lookup"><span data-stu-id="bb781-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="bb781-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="bb781-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="bb781-188">Значение: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="bb781-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="bb781-189">Описание: зарезервировано</span><span class="sxs-lookup"><span data-stu-id="bb781-189">Description: Reserved</span></span>

<span data-ttu-id="bb781-190">__***Стили кнопок "пиксельная карта" и "значок":***__</span><span class="sxs-lookup"><span data-stu-id="bb781-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="bb781-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="bb781-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="bb781-192">Значение: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="bb781-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="bb781-193">Описание: пиксельная карта кнопки должна быть выровнена по центру горизонтальной оси в пределах границы кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="bb781-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="bb781-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="bb781-195">Значение: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="bb781-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="bb781-196">Описание: пиксельная карта кнопки должна быть выровнена по левому краю горизонтальной оси в пределах границы кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="bb781-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="bb781-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="bb781-198">Значение: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="bb781-198">Value 0x00040000</span></span>
  - <span data-ttu-id="bb781-199">Описание: пиксельная карта кнопки должна быть выровнена по правому краю горизонтальной оси в пределах границы кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="bb781-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="bb781-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="bb781-201">Значение: 0x00080000</span><span class="sxs-lookup"><span data-stu-id="bb781-201">Value 0x00080000</span></span>
  - <span data-ttu-id="bb781-202">Описание: пиксельная карта кнопки должна быть выровнена по центру вертикальной оси в пределах границы кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="bb781-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="bb781-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="bb781-204">Значение: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="bb781-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="bb781-205">Описание: пиксельная карта кнопки должна быть выровнена по верхнему краю вертикальной оси в пределах границы кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="bb781-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="bb781-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="bb781-207">Значение: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="bb781-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="bb781-208">Описание: пиксельная карта кнопки должна быть выровнена по нижнему краю вертикальной оси в пределах границы кнопки.</span><span class="sxs-lookup"><span data-stu-id="bb781-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="bb781-209">__***Стили ползунка (применяются только к GX_SLIDER и производным типам мини-приложений):***__</span><span class="sxs-lookup"><span data-stu-id="bb781-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="bb781-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="bb781-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="bb781-211">Значение: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="bb781-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="bb781-212">Описание: этот стиль необходимо добавить для ползунка для отрисовки индикатора стрелки.</span><span class="sxs-lookup"><span data-stu-id="bb781-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="bb781-213">Его можно отключить, если приложение должно отключить стрелку ползунка или нарисовать особый индикатор стрелки.</span><span class="sxs-lookup"><span data-stu-id="bb781-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="bb781-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="bb781-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="bb781-215">Значение: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="bb781-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="bb781-216">Описание: если этот стиль включен, мини-приложение ползунка будет выполнять программную отрисовку пунктирных линий делений.</span><span class="sxs-lookup"><span data-stu-id="bb781-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="bb781-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="bb781-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="bb781-218">Значение: 0x00000800</span><span class="sxs-lookup"><span data-stu-id="bb781-218">Value 0x00000800</span></span>
  - <span data-ttu-id="bb781-219">Описание: установите этот флаг стиля, чтобы создать вертикальный ползунок; снимите его, чтобы создать горизонтальный ползунок.</span><span class="sxs-lookup"><span data-stu-id="bb781-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="bb781-220">__***Стили спрайтов (применяются только к типам мини-приложений GX_SPRITE):***__</span><span class="sxs-lookup"><span data-stu-id="bb781-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="bb781-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="bb781-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="bb781-222">Значение: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="bb781-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="bb781-223">Описание: указывает, что анимация спрайта будет запускаться автоматически, когда мини-приложение спрайта получает событие GX_EVENT_SHOW.</span><span class="sxs-lookup"><span data-stu-id="bb781-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="bb781-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="bb781-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="bb781-225">Значение: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="bb781-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="bb781-226">Описание: при использовании этого стиля мини-приложение спрайта будет поочередно отображать кадры анимации спрайта до тех пор, пока спрайт не будет остановлен приложением.</span><span class="sxs-lookup"><span data-stu-id="bb781-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="bb781-227">__***Стили ползунка на основе пиксельной карты:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="bb781-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="bb781-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="bb781-229">Значение: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="bb781-229">Value 0x00001000</span></span>
  - <span data-ttu-id="bb781-230">Описание: фоновое изображение ползунка мозаично заполняет ограничивающий прямоугольник спрайта.</span><span class="sxs-lookup"><span data-stu-id="bb781-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="bb781-231">Это позволяет использовать небольшое вертикальное или горизонтальное изображение для заполнения фона ползунка.</span><span class="sxs-lookup"><span data-stu-id="bb781-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="bb781-232">__***Дополнительные стили индикатора выполнения:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="bb781-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="bb781-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="bb781-234">Значение: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="bb781-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="bb781-235">Описание: когда задан этот стиль, на индикаторе выполнения отображается процентное значение, а не абсолютное.</span><span class="sxs-lookup"><span data-stu-id="bb781-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="bb781-236">Текст выравнивается по центру ограничивающего прямоугольника индикатора выполнения.</span><span class="sxs-lookup"><span data-stu-id="bb781-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="bb781-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="bb781-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="bb781-238">Значение: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="bb781-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="bb781-239">Описание: текущее значение индикатора выполнения отрисовывается в виде десятичного числа по центру индикатора.</span><span class="sxs-lookup"><span data-stu-id="bb781-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="bb781-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="bb781-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="bb781-241">Значение: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="bb781-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="bb781-242">Описание: указывает, что индикатор выполнения имеет вертикальную ориентацию.</span><span class="sxs-lookup"><span data-stu-id="bb781-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="bb781-243">По умолчанию используется горизонтальная ориентация.</span><span class="sxs-lookup"><span data-stu-id="bb781-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="bb781-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**</span><span class="sxs-lookup"><span data-stu-id="bb781-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="bb781-245">**Значение**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="bb781-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="bb781-246">Описание: значение индикатора выполнения обозначается в виде сегментированных прямоугольников с заливкой, а не в виде сплошной заливки.</span><span class="sxs-lookup"><span data-stu-id="bb781-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="bb781-247">__***Дополнительные стили кругового индикатора выполнения:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="bb781-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="bb781-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="bb781-249">Значение: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="bb781-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="bb781-250">Описание: круговой индикатор выполнения отрисовывается с использованием стилей кисти со сглаживанием.</span><span class="sxs-lookup"><span data-stu-id="bb781-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="bb781-251">Для этого требуется больше ресурсов ЦП, но индикатор выглядит лучше.</span><span class="sxs-lookup"><span data-stu-id="bb781-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="bb781-252">На устройствах с низкой производительностью ЦП снятие этого флага стиля приведет к ускорению отрисовки.</span><span class="sxs-lookup"><span data-stu-id="bb781-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="bb781-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="bb781-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="bb781-254">Значение: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="bb781-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="bb781-255">Описание: использование стиля кисти со скругленными концами линии при отрисовке дуги кругового индикатора выполнения. По умолчанию используются квадратные концы линий.</span><span class="sxs-lookup"><span data-stu-id="bb781-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="bb781-256">__***Дополнительные стили ввода текста:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="bb781-257">**GX_STYLE_ CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="bb781-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="bb781-258">Значение: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="bb781-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="bb781-259">Описание: курсор мини-приложения ввода текста будет мигать.</span><span class="sxs-lookup"><span data-stu-id="bb781-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="bb781-260">**GX_STYLE_ CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="bb781-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="bb781-261">Значение: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="bb781-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="bb781-262">Описание.</span><span class="sxs-lookup"><span data-stu-id="bb781-262">Description.</span></span> <span data-ttu-id="bb781-263">Курсор мини-приложения ввода текста обычно отображается, только когда мини-приложение получает фокус ввода.</span><span class="sxs-lookup"><span data-stu-id="bb781-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="bb781-264">Этот флаг стиля делает курсор видимым всегда независимо от фокуса ввода.</span><span class="sxs-lookup"><span data-stu-id="bb781-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="bb781-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="bb781-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="bb781-266">Значение: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="bb781-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="bb781-267">Описание: когда установлен этот флаг стиля, событие GX_EVENT_TEXT_EDITED создается при каждом получении события нажатия клавиши в мини-приложении ввода текста.</span><span class="sxs-lookup"><span data-stu-id="bb781-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="bb781-268">__***Дополнительные стили окна:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="bb781-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="bb781-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="bb781-270">Значение: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="bb781-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="bb781-271">Описание: клиентский прямоугольник окна мозаично заполняется назначенным изображением обоев.</span><span class="sxs-lookup"><span data-stu-id="bb781-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="bb781-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="bb781-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="bb781-273">Значение: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="bb781-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="bb781-274">Описание: зарезервировано для использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="bb781-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="bb781-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="bb781-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="bb781-276">Значение: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="bb781-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="bb781-277">Описание: зарезервировано для использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="bb781-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="bb781-278">__***Дополнительные стили меню:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="bb781-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="bb781-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="bb781-280">Значение: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="bb781-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="bb781-281">Описание: мини-приложение меню типа "гармошка" изначально находится в развернутом состоянии.</span><span class="sxs-lookup"><span data-stu-id="bb781-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="bb781-282">__***Дополнительные стили представления в виде дерева:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="bb781-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="bb781-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="bb781-284">Значение: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="bb781-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="bb781-285">Описание: мини-приложение представления в виде дерева должно рисовать линии от значка узла к корневому узлу дерева.</span><span class="sxs-lookup"><span data-stu-id="bb781-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="bb781-286">__***Дополнительные стили полосы прокрутки:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="bb781-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="bb781-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="bb781-288">Значение: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="bb781-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="bb781-289">Описание: зарезервировано для использования в будущем.</span><span class="sxs-lookup"><span data-stu-id="bb781-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="bb781-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="bb781-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="bb781-291">Значение: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="bb781-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="bb781-292">Описание: ширина горизонтальной или высота вертикальной полосы прокрутки вычисляется на основе отношения видимой области родительского окна к минимальному и максимальному диапазону полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="bb781-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="bb781-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="bb781-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="bb781-294">Значение: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="bb781-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="bb781-295">Описание: полоса прокрутки автоматически создает и прикрепляет кнопки в каждом конце области полосы прокрутки.</span><span class="sxs-lookup"><span data-stu-id="bb781-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="bb781-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="bb781-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="bb781-297">Значение: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="bb781-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="bb781-298">Описание: для полосы прокрутки используется вертикальная ориентация.</span><span class="sxs-lookup"><span data-stu-id="bb781-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="bb781-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="bb781-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="bb781-300">Значение: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="bb781-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="bb781-301">Описание: для полосы прокрутки используется горизонтальная ориентация.</span><span class="sxs-lookup"><span data-stu-id="bb781-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="bb781-302">__***Стили текста колеса прокрутки:***__</span><span class="sxs-lookup"><span data-stu-id="bb781-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="bb781-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="bb781-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="bb781-304">Значение: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="bb781-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="bb781-305">Описание: для отображения колеса прокрутки круглой формы используется синусоидальный алгоритм.</span><span class="sxs-lookup"><span data-stu-id="bb781-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="bb781-306">Этот флаг стиля может создать дополнительную нагрузку на мини-приложение типа "колесо прокрутки", но также может придать ему реалистичный трехмерный вид.</span><span class="sxs-lookup"><span data-stu-id="bb781-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>