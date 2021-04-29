---
title: Руководство пользователя ОСРВ Azure GUIX
description: Это руководство содержит исчерпывающие сведения об ОСРВ Azure GUIX — высокопроизводительном продукте с графическим пользовательским интерфейсом от корпорации Майкрософт.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b7af0fba59b599c9c8db3ab80a3271eacfd11992
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815580"
---
# <a name="about-guix-user-guide"></a><span data-ttu-id="aeb34-103">О руководстве пользователя GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-103">About GUIX User Guide</span></span>

<span data-ttu-id="aeb34-104">Это руководство содержит исчерпывающие сведения об ОСРВ Azure GUIX — высокопроизводительном продукте с графическим пользовательским интерфейсом от корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="aeb34-104">This guide contains comprehensive information about Azure RTOS GUIX, the high-performance GUI product from Microsoft.</span></span> <span data-ttu-id="aeb34-105">Оно предназначено для разработчиков встроенного программного обеспечения реального времени, знакомых с основными принципами работы графического пользовательского интерфейса, ОСРВ Azure ThreadX и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="aeb34-105">It is intended for embedded real-time software developers familiar with basic GUI concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="aeb34-106">План</span><span class="sxs-lookup"><span data-stu-id="aeb34-106">Organization</span></span>

[<span data-ttu-id="aeb34-107">Глава 1. Введение в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-107">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>](chapter-1.md)

[<span data-ttu-id="aeb34-108">Глава 2. Установка и использование ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-108">Chapter 2 - Installation and use of Azure RTOS GUIX</span></span>](chapter-2.md)

[<span data-ttu-id="aeb34-109">Глава 3. Функциональный обзор ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-109">Chapter 3 - Functional Overview of Azure RTOS GUIX</span></span>](chapter-3.md)

[<span data-ttu-id="aeb34-110">Глава 4. Описание служб ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-110">Chapter 4 - Description of Azure RTOS GUIX Services</span></span>](chapter-4.md)

[<span data-ttu-id="aeb34-111">Глава 5. Драйверы дисплея ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-111">Chapter 5 - Azure RTOS GUIX Display Drivers</span></span>](chapter-5.md)  

[<span data-ttu-id="aeb34-112">Пример для ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-112">Azure RTOS GUIX Example</span></span>](guix-example.md)

[<span data-ttu-id="aeb34-113">Приложение А. Определения цветов в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-113">Appendix A - Azure RTOS GUIX Color Definitions</span></span>](appendix-a.md)

[<span data-ttu-id="aeb34-114">Приложение Б. Форматы цветов в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-114">Appendix B - Azure RTOS GUIX Color Formats</span></span>](appendix-b.md)

[<span data-ttu-id="aeb34-115">Приложение В. Стили мини-приложений в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-115">Appendix C - Azure RTOS GUIX Widget Styles</span></span>](appendix-c.md)

[<span data-ttu-id="aeb34-116">Приложение Г. Атрибуты кисти, холста и градиента в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-116">Appendix D - Azure RTOS GUIX Brush, Canvas and Gradient Attributes</span></span>](appendix-d.md)

[<span data-ttu-id="aeb34-117">Приложение Д. Описание событий ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-117">Appendix E - Azure RTOS GUIX Event Description</span></span>](appendix-e.md)

[<span data-ttu-id="aeb34-118">Приложение Е. Службы привязки ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-118">Appendix F - Azure RTOS GUIX RTOS Binding Services</span></span>](appendix-f.md)

[<span data-ttu-id="aeb34-119">Приложение Ж. Структура шрифта в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-119">Appendix G - Azure RTOS GUIX Font Structure</span></span>](appendix-g.md)

[<span data-ttu-id="aeb34-120">Приложение З. Флаги конфигурации времени сборки ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-120">Appendix H - Azure RTOS GUIX Build-Time Configuration flags</span></span>](appendix-h.md)

[<span data-ttu-id="aeb34-121">Приложение И. Информационные структуры ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-121">Appendix I - Azure RTOS GUIX Information Structures</span></span>](appendix-i.md)

## <a name="guide-conventions"></a><span data-ttu-id="aeb34-122">Условные обозначения в руководстве</span><span class="sxs-lookup"><span data-stu-id="aeb34-122">Guide Conventions</span></span>

<span data-ttu-id="aeb34-123">*Курсив* используется для написания названий книг, выделения важных слов и обозначения переменных.</span><span class="sxs-lookup"><span data-stu-id="aeb34-123">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="aeb34-124">**Полужирным** шрифтом выделены имена файлов и ключевые слова, а также им дополнительно подчеркнуты важные слова и переменные.</span><span class="sxs-lookup"><span data-stu-id="aeb34-124">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aeb34-125">Информационные символы привлекают внимание к важной или дополнительной информации, которая может повлиять на производительность или функцию.</span><span class="sxs-lookup"><span data-stu-id="aeb34-125">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

## <a name="azure-rtos-guix-data-types"></a><span data-ttu-id="aeb34-126">Типы данных в ОСРВ Azure GUIX</span><span class="sxs-lookup"><span data-stu-id="aeb34-126">Azure RTOS GUIX Data Types</span></span>

<span data-ttu-id="aeb34-127">Помимо пользовательских типов данных структур управления ОСРВ Azure GUIX существует ряд специальных типов данных, которые используются в интерфейсах вызова службы ОСРВ Azure GUIX.</span><span class="sxs-lookup"><span data-stu-id="aeb34-127">In addition to the custom Azure RTOS GUIX control structure data types, there are several special data types that are used in Azure RTOS GUIX service call interfaces.</span></span> <span data-ttu-id="aeb34-128">Эти специальные типы данных сопоставляются непосредственно с типами данных базового компилятора C.</span><span class="sxs-lookup"><span data-stu-id="aeb34-128">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="aeb34-129">Это необходимо для обеспечения переносимости кода между разными компиляторами C.</span><span class="sxs-lookup"><span data-stu-id="aeb34-129">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="aeb34-130">Конкретная реализация наследуется от ThreadX и представлена в файле ***tx_port.h***, включенном в состав дистрибутива ThreadX.</span><span class="sxs-lookup"><span data-stu-id="aeb34-130">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="aeb34-131">Ниже приведен список типов данных вызова служб ОСРВ Azure GUIX и их значений.</span><span class="sxs-lookup"><span data-stu-id="aeb34-131">The following is a list of Azure RTOS GUIX service call data types and their associated meanings:</span></span>

| <!-- --> | <!-- --> |
| --------------------- | --------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="aeb34-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="aeb34-132">**UINT**</span></span>             | <span data-ttu-id="aeb34-133">Простое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-133">Basic unsigned integer.</span></span> <span data-ttu-id="aeb34-134">Этот тип сопоставлен с наиболее подходящим типом данных без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-134">This type is mapped to the most convenient unsigned data type.</span></span>                                |
| <span data-ttu-id="aeb34-135">**INT**</span><span class="sxs-lookup"><span data-stu-id="aeb34-135">**INT**</span></span>              | <span data-ttu-id="aeb34-136">Простое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="aeb34-136">Basic signed integer.</span></span> <span data-ttu-id="aeb34-137">Этот тип сопоставлен с наиболее подходящим типом данных со знаком.</span><span class="sxs-lookup"><span data-stu-id="aeb34-137">This type is mapped to the most convenient signed data type.</span></span>                                    |
| <span data-ttu-id="aeb34-138">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="aeb34-138">**ULONG**</span></span>            | <span data-ttu-id="aeb34-139">Длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-139">Unsigned long type.</span></span> <span data-ttu-id="aeb34-140">Этот тип должен поддерживать 32-разрядные данные без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-140">This type must support 32-bit unsigned data.</span></span>                                                      |
| <span data-ttu-id="aeb34-141">**VOID**</span><span class="sxs-lookup"><span data-stu-id="aeb34-141">**VOID**</span></span>             | <span data-ttu-id="aeb34-142">Почти всегда эквивалентен типу void компилятора.</span><span class="sxs-lookup"><span data-stu-id="aeb34-142">Almost always equivalent to the compiler’s void type.</span></span>                                                                 |
| <span data-ttu-id="aeb34-143">**GX_CHAR**</span><span class="sxs-lookup"><span data-stu-id="aeb34-143">**GX_CHAR**</span></span>         | <span data-ttu-id="aeb34-144">Чаще всего определяется с помощью typedef как тип char, определенный компилятором.</span><span class="sxs-lookup"><span data-stu-id="aeb34-144">Most often typedefed as the compiler defined char type.</span></span>                                                               |
| <span data-ttu-id="aeb34-145">**GX_BYTE**</span><span class="sxs-lookup"><span data-stu-id="aeb34-145">**GX_BYTE**</span></span>          | <span data-ttu-id="aeb34-146">8-разрядное число со знаком.</span><span class="sxs-lookup"><span data-stu-id="aeb34-146">8-bit signed type.</span></span>                                                                                                    |
| <span data-ttu-id="aeb34-147">**GX_UBYTE**</span><span class="sxs-lookup"><span data-stu-id="aeb34-147">**GX_UBYTE**</span></span>         | <span data-ttu-id="aeb34-148">8-разрядное число без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-148">8-bit unsigned type.</span></span>                                                                                                  |
| <span data-ttu-id="aeb34-149">**GX_VALUE**</span><span class="sxs-lookup"><span data-stu-id="aeb34-149">**GX_VALUE**</span></span>        | <span data-ttu-id="aeb34-150">16- или 32-разрядное число со знаком.</span><span class="sxs-lookup"><span data-stu-id="aeb34-150">16 or 32 bit signed type.</span></span> <span data-ttu-id="aeb34-151">Определяется в соответствии с требованиями для обеспечения максимальной производительности на целевом оборудовании.</span><span class="sxs-lookup"><span data-stu-id="aeb34-151">Defined as needed for best performance on the target system.</span></span>                                |
| <span data-ttu-id="aeb34-152">**GX_FIXED_VAL**</span><span class="sxs-lookup"><span data-stu-id="aeb34-152">**GX_FIXED_VAL**</span></span>   | <span data-ttu-id="aeb34-153">Числовой тип данных с фиксированной запятой.</span><span class="sxs-lookup"><span data-stu-id="aeb34-153">Fixed point numeric data type.</span></span>                                                                                        |
| <span data-ttu-id="aeb34-154">**GX_RESOURCE_ID**</span><span class="sxs-lookup"><span data-stu-id="aeb34-154">**GX_RESOURCE_ID**</span></span> | <span data-ttu-id="aeb34-155">Длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-155">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="aeb34-156">**GX_COLOR**</span><span class="sxs-lookup"><span data-stu-id="aeb34-156">**GX_COLOR**</span></span>        | <span data-ttu-id="aeb34-157">Длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="aeb34-157">Unsigned long type.</span></span>                                                                                                   |
| <span data-ttu-id="aeb34-158">**GX_STRING**</span><span class="sxs-lookup"><span data-stu-id="aeb34-158">**GX_STRING**</span></span>       | <span data-ttu-id="aeb34-159">Структура, содержащая GX_CHAR \*gx_string_ptr и UINT gx_string_length.</span><span class="sxs-lookup"><span data-stu-id="aeb34-159">Structure containing GX_CHAR \*gx_string_ptr and UINT gx_string_length.</span></span>                                          |
| <span data-ttu-id="aeb34-160">**GX_POINT**</span><span class="sxs-lookup"><span data-stu-id="aeb34-160">**GX_POINT**</span></span>        | <span data-ttu-id="aeb34-161">Структура, содержащая gx_point_x и gx_point_y.</span><span class="sxs-lookup"><span data-stu-id="aeb34-161">Structure containing gx_point_x and gx_point_y.</span></span>                                                                   |
| <span data-ttu-id="aeb34-162">**GX_RECTANGLE**</span><span class="sxs-lookup"><span data-stu-id="aeb34-162">**GX_RECTANGLE**</span></span>    | <span data-ttu-id="aeb34-163">Структура, содержащая поля gx_rectangle_left, gx_rectangle_top, gx_rectangle_right и gx_rectangle_bottom.</span><span class="sxs-lookup"><span data-stu-id="aeb34-163">Structure containing gx_rectangle_left, gx_rectangle_top, gx_rectangle_right, and gx_rectangle_bottom fields.</span></span> |
| <span data-ttu-id="aeb34-164">**GX_GLYPH**</span><span class="sxs-lookup"><span data-stu-id="aeb34-164">**GX_GLYPH**</span></span>        | <span data-ttu-id="aeb34-165">Структура, содержащая метрики глифа.</span><span class="sxs-lookup"><span data-stu-id="aeb34-165">Structure containing glyph metrics.</span></span>                                                                                   |
| <span data-ttu-id="aeb34-166">**GX_FONT**</span><span class="sxs-lookup"><span data-stu-id="aeb34-166">**GX_FONT**</span></span>         | <span data-ttu-id="aeb34-167">Структура, содержащая метрики шрифта.</span><span class="sxs-lookup"><span data-stu-id="aeb34-167">Structure containing font metrics.</span></span>                                                                                    |
| <span data-ttu-id="aeb34-168">**GX_BRUSH**</span><span class="sxs-lookup"><span data-stu-id="aeb34-168">**GX_BRUSH**</span></span>        | <span data-ttu-id="aeb34-169">Структура, содержащая метрики кисти.</span><span class="sxs-lookup"><span data-stu-id="aeb34-169">Structure containing brush metrics.</span></span>                                                                               |
<span data-ttu-id="aeb34-170">**GX_PIXELMAP**</span><span class="sxs-lookup"><span data-stu-id="aeb34-170">**GX_PIXELMAP**</span></span>       | <span data-ttu-id="aeb34-171">Структура, содержащая метрики карты отображения пикселей.</span><span class="sxs-lookup"><span data-stu-id="aeb34-171">Structure containing pixelmap metrics.</span></span>

<span data-ttu-id="aeb34-172">В исходном коде ОСРВ Azure GUIX используются дополнительные типы данных.</span><span class="sxs-lookup"><span data-stu-id="aeb34-172">Additional data types are used within the Azure RTOS GUIX source.</span></span> <span data-ttu-id="aeb34-173">Они находятся в файлах \***tx_port.h** _ или _ \*_gx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="aeb34-173">They are located in either the ***tx_port.h** _ or _ *_gx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="aeb34-174">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="aeb34-174">Customer Support Center</span></span>

<span data-ttu-id="aeb34-175">Если у вас возникли вопросы или требуется помощь при выполнении приведенных здесь шагов, отправьте запрос в службу поддержки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="aeb34-175">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="aeb34-176">Предоставьте нам следующие сведения в сообщении электронной почты, чтобы мы могли более эффективно решить ваш запрос в службу поддержки:</span><span class="sxs-lookup"><span data-stu-id="aeb34-176">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="aeb34-177">Подробное описание проблемы, включая частоту возникновения и действия, позволяющие гарантированно воспроизвести эту проблему (если это возможно).</span><span class="sxs-lookup"><span data-stu-id="aeb34-177">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="aeb34-178">Подробное описание любых изменений в приложении и (или) ОСРВ Azure GUIX, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="aeb34-178">A detailed description of any changes to the application and/or Azure RTOS GUIX that preceded the problem.</span></span>

3. <span data-ttu-id="aeb34-179">Содержимое строк _tx_version_id и _gx_version_id из файлов \***tx_port.h**_  и _ *_gx_port.h_*\* вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="aeb34-179">The contents of the _tx_version_id and _gx_version_id strings found in the \***tx_port.h**_ and _ *_gx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="aeb34-180">Эти строки предоставят нам полезную информацию о вашей среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="aeb34-180">These strings will provide us valuable Information regarding your run-time environment.</span></span>

4. <span data-ttu-id="aeb34-181">Содержимое ОЗУ для следующих переменных ULONG:</span><span class="sxs-lookup"><span data-stu-id="aeb34-181">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="aeb34-182">**_tx_build_options** **_gx_system_build_options**</span><span class="sxs-lookup"><span data-stu-id="aeb34-182">**_tx_build_options** **_gx_system_build_options**</span></span>

    <span data-ttu-id="aeb34-183">Эти переменные позволят нам узнать, как были созданы библиотеки ОСРВ Azure ThreadX и ОСРВ Azure GUIX.</span><span class="sxs-lookup"><span data-stu-id="aeb34-183">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS GUIX libraries were built.</span></span>

5. <span data-ttu-id="aeb34-184">Содержимое ОЗУ для следующих переменных ULONG:</span><span class="sxs-lookup"><span data-stu-id="aeb34-184">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="aeb34-185">**_gx_system_last_error** **_gx_system_error_count**</span><span class="sxs-lookup"><span data-stu-id="aeb34-185">**_gx_system_last_error** **_gx_system_error_count**</span></span>

    <span data-ttu-id="aeb34-186">Эти переменные содержат данные об отслеживании внутренних системных ошибок в ОСРВ Azure GUIX.</span><span class="sxs-lookup"><span data-stu-id="aeb34-186">These variables keep track of internal system errors in Azure RTOS GUIX.</span></span> <span data-ttu-id="aeb34-187">Если значение _gx_system_error_count больше единицы, установите точку останова на возвращении функции в функции _gx_system_error_process и укажите значение _gx_system_last_error в этой точке.</span><span class="sxs-lookup"><span data-stu-id="aeb34-187">If the _gx_system_error_count is greater than one, please set a breakpoint on the function return in the _gx_system_error_process function and provide the value of _gx_system_last_error at this point.</span></span> <span data-ttu-id="aeb34-188">Это позволит получить первую внутреннюю системную ошибку ОСРВ Azure GUIX.</span><span class="sxs-lookup"><span data-stu-id="aeb34-188">This will yield the first internal Azure RTOS GUIX system error.</span></span>

6. <span data-ttu-id="aeb34-189">Буфер трассировки, записанный сразу после обнаружения проблемы.</span><span class="sxs-lookup"><span data-stu-id="aeb34-189">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="aeb34-190">Для этого необходимо создать библиотеки ОСРВ Azure ThreadX и ОСРВ Azure GUIX с параметром TX_ENABLE_EVENT_TRACE и вызвать tx_trace_enable, указав данные буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="aeb34-190">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS GUIX libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>

7. <span data-ttu-id="aeb34-191">Проект ОСРВ Azure GUIX Studio, с которым вы работаете, если это возможно, или как минимум небольшой проект, достаточный для демонстрации недостатка, о котором вы сообщаете.</span><span class="sxs-lookup"><span data-stu-id="aeb34-191">The Azure RTOS GUIX Studio project you are using, if applicable, or at a minimum a small project sufficient to demonstrate the deficiency you are reporting.</span></span>
