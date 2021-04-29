---
title: Глава 1. Знакомство с GUIX
description: GUIX — это высокопроизводительная, работающая в реальном времени реализация графического пользовательского интерфейса, разработанная исключительно для встраиваемых приложений на основе ОСРВ Azure ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815523"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="d9475-103">Глава 1. Знакомство с GUIX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="d9475-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="d9475-104">GUIX для ОСРВ Azure — это высокопроизводительная, работающая в реальном времени реализация платформы графического интерфейса, разработанная исключительно для встраиваемых приложений на основе ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d9475-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="d9475-105">В этой главе содержатся общие сведения о GUIX, в том числе описываются аспекты его прикладного применения и преимущества.</span><span class="sxs-lookup"><span data-stu-id="d9475-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="d9475-106">Обзор возможностей GUIX</span><span class="sxs-lookup"><span data-stu-id="d9475-106">GUIX Feature Overview</span></span>

<span data-ttu-id="d9475-107">В отличие от многих других реализаций графического пользовательского интерфейса, GUIX обладает гибкостью — его можно легко использовать как с компактными приложениями для микроконтроллеров, так и с приложениями для мощных процессоров RISC и DSP.</span><span class="sxs-lookup"><span data-stu-id="d9475-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="d9475-108">Это резко контрастирует с общедоступными или другими коммерческими реализациями, которые изначально разрабатывались для сред рабочих станций, а затем адаптировались под встраиваемые системы.</span><span class="sxs-lookup"><span data-stu-id="d9475-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="d9475-109">Ниже приводится обзор возможностей GUIX:</span><span class="sxs-lookup"><span data-stu-id="d9475-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="d9475-110">Простота в работе благодаря размещенному инструменту проектирования GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="d9475-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="d9475-111">Среда выполнения Win32 GUIX для полностью размещенного создания прототипов</span><span class="sxs-lookup"><span data-stu-id="d9475-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="d9475-112">Поддержка большинства процессоров, поддерживаемых ThreadX</span><span class="sxs-lookup"><span data-stu-id="d9475-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="d9475-113">Написание исключительно на ANSI C</span><span class="sxs-lookup"><span data-stu-id="d9475-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="d9475-114">Независимость от порядка байтов</span><span class="sxs-lookup"><span data-stu-id="d9475-114">Endian neutral</span></span>

- <span data-ttu-id="d9475-115">Самый маленький и быстрый встраиваемый графический пользовательский интерфейс</span><span class="sxs-lookup"><span data-stu-id="d9475-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="d9475-116">Возможность настройки количества объектов, размера экрана и других параметров во время выполнения</span><span class="sxs-lookup"><span data-stu-id="d9475-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="d9475-117">Простота написания интерфейса для драйвера дисплея</span><span class="sxs-lookup"><span data-stu-id="d9475-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="d9475-118">Поддержка цветного (глубина цвета до 32 бит/пкс), монохромного режимов и режима оттенков серого</span><span class="sxs-lookup"><span data-stu-id="d9475-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="d9475-119">Многоязычная поддержка с использованием кодирования строк UTF8 и строковых ресурсов</span><span class="sxs-lookup"><span data-stu-id="d9475-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="d9475-120">Бесплатные шрифты по умолчанию и простота добавления новых шрифтов</span><span class="sxs-lookup"><span data-stu-id="d9475-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="d9475-121">Поддержка нескольких холстов разного размера</span><span class="sxs-lookup"><span data-stu-id="d9475-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="d9475-122">Поддержка нескольких экранов разного размера с разными параметрами глубины цвета</span><span class="sxs-lookup"><span data-stu-id="d9475-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="d9475-123">Поддержка экранных переходов (появление, исчезание, прокрутка и т. д.)</span><span class="sxs-lookup"><span data-stu-id="d9475-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="d9475-124">Поддержка сенсорного ввода, жестов и виртуальной клавиатуры</span><span class="sxs-lookup"><span data-stu-id="d9475-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="d9475-125">Сжатие растрового изображения</span><span class="sxs-lookup"><span data-stu-id="d9475-125">Bitmap compression</span></span>

- <span data-ttu-id="d9475-126">Поддержка альфа-смешения</span><span class="sxs-lookup"><span data-stu-id="d9475-126">Alpha Blending Support</span></span>

- <span data-ttu-id="d9475-127">Поддержка размывания</span><span class="sxs-lookup"><span data-stu-id="d9475-127">Dither Support</span></span>

- <span data-ttu-id="d9475-128">Поддержка сглаживания</span><span class="sxs-lookup"><span data-stu-id="d9475-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="d9475-129">Создание обложек и тем</span><span class="sxs-lookup"><span data-stu-id="d9475-129">Skinning and Themes</span></span>

- <span data-ttu-id="d9475-130">Смешение на холсте</span><span class="sxs-lookup"><span data-stu-id="d9475-130">Canvas Blending</span></span>

- <span data-ttu-id="d9475-131">Полное управление окнами</span><span class="sxs-lookup"><span data-stu-id="d9475-131">Complete Window Management</span></span>

  - <span data-ttu-id="d9475-132">Связи между родительскими и дочерними объектами</span><span class="sxs-lookup"><span data-stu-id="d9475-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="d9475-133">Динамическое создание, удаление, изменение размера и перемещение</span><span class="sxs-lookup"><span data-stu-id="d9475-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="d9475-134">Разделение обработки событий и отрисовки</span><span class="sxs-lookup"><span data-stu-id="d9475-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="d9475-135">Z-порядок</span><span class="sxs-lookup"><span data-stu-id="d9475-135">Z-order</span></span>
  - <span data-ttu-id="d9475-136">Обрезка и представления</span><span class="sxs-lookup"><span data-stu-id="d9475-136">Clipping and views</span></span>

- <span data-ttu-id="d9475-137">Обширный набор мини-приложений</span><span class="sxs-lookup"><span data-stu-id="d9475-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="d9475-138">Различные типы кнопок, ползунков и шкал</span><span class="sxs-lookup"><span data-stu-id="d9475-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="d9475-139">Раскрывающийся список</span><span class="sxs-lookup"><span data-stu-id="d9475-139">Drop Down List</span></span>
  
  - <span data-ttu-id="d9475-140">prompt</span><span class="sxs-lookup"><span data-stu-id="d9475-140">Prompt</span></span>

  - <span data-ttu-id="d9475-141">Представление многострочного текста</span><span class="sxs-lookup"><span data-stu-id="d9475-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="d9475-142">Одиночный и многострочный ввод текста</span><span class="sxs-lookup"><span data-stu-id="d9475-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="d9475-143">Числовые и текстовые колесики прокрутки</span><span class="sxs-lookup"><span data-stu-id="d9475-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="d9475-144">Окна и полосы прокрутки</span><span class="sxs-lookup"><span data-stu-id="d9475-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="d9475-145">Круговой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="d9475-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="d9475-146">Спрайт</span><span class="sxs-lookup"><span data-stu-id="d9475-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="d9475-147">Исходный код ANSI C</span><span class="sxs-lookup"><span data-stu-id="d9475-147">ANSI C Source Code</span></span>

<span data-ttu-id="d9475-148">GUIX написан полностью на ANSI C, и его можно мгновенно перенести практически в любую процессорную архитектуру с поддержкой компилятора ANSI C и ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d9475-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="d9475-149">Несмотря на то, что GUIX написан на ANSI C, в нем используются объектно-ориентированная модель и наследование.</span><span class="sxs-lookup"><span data-stu-id="d9475-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="d9475-150">Отсутствие проблемы "черного ящика"</span><span class="sxs-lookup"><span data-stu-id="d9475-150">Not A Black Box</span></span>

<span data-ttu-id="d9475-151">Большинство дистрибутивов GUIX включают полный исходный код на C.</span><span class="sxs-lookup"><span data-stu-id="d9475-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="d9475-152">Это устраняет проблему "черного ящика", которая характерна для многих коммерческих реализаций графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d9475-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="d9475-153">Используя GUIX, разработчики приложений могут отслеживать все без исключения операции графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d9475-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="d9475-154">Доступность исходного кода также позволяет вносить изменения с учетом конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="d9475-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="d9475-155">Хотя это и не рекомендуется, но возможность при необходимости изменить графический пользовательский интерфейс является плюсом.</span><span class="sxs-lookup"><span data-stu-id="d9475-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="d9475-156">Эти функции особенно полезны разработчикам, которые привыкли работать с корпоративными или общедоступными продуктами.</span><span class="sxs-lookup"><span data-stu-id="d9475-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="d9475-157">Они привыкли, что исходный код доступен и его можно изменить.</span><span class="sxs-lookup"><span data-stu-id="d9475-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="d9475-158">GUIX — это лучшее программное обеспечение графического пользовательского интерфейса для таких разработчиков.</span><span class="sxs-lookup"><span data-stu-id="d9475-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="d9475-159">Встраиваемые приложения с графическим пользовательским интерфейсом</span><span class="sxs-lookup"><span data-stu-id="d9475-159">Embedded GUI Applications</span></span>

<span data-ttu-id="d9475-160">Встраиваемые приложения с графическим пользовательским интерфейсом — это приложения, которым требуется пользовательский интерфейс и которые работают на микропроцессорах, установленных в таких продуктах, как сотовые телефоны, коммуникационное оборудование, двигатели, лазерные принтеры, медицинские изделия и т. д.</span><span class="sxs-lookup"><span data-stu-id="d9475-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="d9475-161">Такие приложения почти всегда имеют некоторые ограничения по объему памяти и производительности.</span><span class="sxs-lookup"><span data-stu-id="d9475-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="d9475-162">Еще одно отличие встраиваемых приложений с графическим пользовательским интерфейсом — это то, что их программные и аппаратные компоненты имеют определенные цели.</span><span class="sxs-lookup"><span data-stu-id="d9475-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="d9475-163">Программное обеспечение реального времени с графическим пользовательским интерфейсом</span><span class="sxs-lookup"><span data-stu-id="d9475-163">Real-time GUI Software</span></span>

<span data-ttu-id="d9475-164">Программное обеспечение с графическим пользовательским интерфейсом, которое должно выполнять операции обработки за определенный период времени, называется *ПО реального времени с графическим пользовательским интерфейсом*, и при наличии временных ограничений для таких приложений они считаются приложениями реального времени.</span><span class="sxs-lookup"><span data-stu-id="d9475-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="d9475-165">Встраиваемые приложения с графическим пользовательским интерфейсом практически всегда работают в реальном времени, так как они взаимодействуют с внешней средой.</span><span class="sxs-lookup"><span data-stu-id="d9475-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="d9475-166">Преимущества GUIX</span><span class="sxs-lookup"><span data-stu-id="d9475-166">GUIX Benefits</span></span>

<span data-ttu-id="d9475-167">Основными преимуществами использования GUIX для встраиваемых приложений являются высокая производительность, широкий выбор возможностей и небольшие требования к памяти.</span><span class="sxs-lookup"><span data-stu-id="d9475-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="d9475-168">Кроме того, протокол GUIX полностью интегрирован с высокопроизводительной, многозадачной операционной системой ОСРВ Azure ThreadX, работающей в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="d9475-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="d9475-169">Повышенная скорость реагирования</span><span class="sxs-lookup"><span data-stu-id="d9475-169">Improved Responsiveness</span></span>

<span data-ttu-id="d9475-170">Благодаря высокой производительности GUIX приложения реагируют быстрее, чем когда-либо ранее.</span><span class="sxs-lookup"><span data-stu-id="d9475-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="d9475-171">Это особенно важно для встраиваемых приложений, которые работают со значительным объемом визуальных данных или имеют строгие ограничения по времени, затрачиваемому на отображение такой информации.</span><span class="sxs-lookup"><span data-stu-id="d9475-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="d9475-172">Обслуживание программного обеспечения</span><span class="sxs-lookup"><span data-stu-id="d9475-172">Software Maintenance</span></span>

<span data-ttu-id="d9475-173">С GUIX разработчики могут с легкостью секционировать аспекты собственных встраиваемых приложений, связанные с графическим пользовательским интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="d9475-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="d9475-174">Такое секционирование упрощает весь процесс разработки и значительно расширяет возможности по будущему обслуживанию программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="d9475-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="d9475-175">Повышение пропускной способности</span><span class="sxs-lookup"><span data-stu-id="d9475-175">Increased Throughput</span></span>

<span data-ttu-id="d9475-176">GUIX предоставляет графический интерфейс пользователя с наивысшей возможной производительностью напрямую встраиваемому приложению.</span><span class="sxs-lookup"><span data-stu-id="d9475-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="d9475-177">Приложения GUIX могут обрабатывать данные пользовательского интерфейса быстрее любых других приложений.</span><span class="sxs-lookup"><span data-stu-id="d9475-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="d9475-178">Изолированность от процессора</span><span class="sxs-lookup"><span data-stu-id="d9475-178">Processor Isolation</span></span>

<span data-ttu-id="d9475-179">GUIX предоставляет надежный, независимый от процессора интерфейс между приложением, базовым процессором и дисплеем.</span><span class="sxs-lookup"><span data-stu-id="d9475-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="d9475-180">Это позволяет разработчикам сосредоточиться на высокоуровневых аспектах пользовательского интерфейса, не тратя время на решение вопросов, связанных с оборудованием.</span><span class="sxs-lookup"><span data-stu-id="d9475-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="d9475-181">Удобство использования</span><span class="sxs-lookup"><span data-stu-id="d9475-181">Ease of Use</span></span>

<span data-ttu-id="d9475-182">GUIX предназначается для разработчиков приложений.</span><span class="sxs-lookup"><span data-stu-id="d9475-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="d9475-183">Архитектура и интерфейс вызовов служб GUIX отличаются простотой.</span><span class="sxs-lookup"><span data-stu-id="d9475-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="d9475-184">Поэтому разработчики GUIX могут с легкостью использовать его расширенные функции.</span><span class="sxs-lookup"><span data-stu-id="d9475-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="d9475-185">Сокращение времени выхода на рынок</span><span class="sxs-lookup"><span data-stu-id="d9475-185">Improve Time to Market</span></span>

<span data-ttu-id="d9475-186">Мощные функции GUIX ускоряют разработку программного обеспечения.</span><span class="sxs-lookup"><span data-stu-id="d9475-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="d9475-187">GUIX абстрагирует большинство проблем с процессором и дисплеем, фактически устраняя их в большинстве реализаций пользовательского интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="d9475-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="d9475-188">В сочетании с простотой использования и набором расширенных функций это значительно ускоряет выход на рынок.</span><span class="sxs-lookup"><span data-stu-id="d9475-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="d9475-189">Защита инвестиций в программное обеспечение</span><span class="sxs-lookup"><span data-stu-id="d9475-189">Protecting the Software Investment</span></span>

<span data-ttu-id="d9475-190">Для разработки GUIX используется исключительно ANSI C. При этом он полностью интегрирован с операционной системой ОСРВ Azure ThreadX, работающей в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="d9475-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="d9475-191">Это означает, что приложения GUIX можно мгновенно перенести на все поддерживаемые ThreadX процессоры.</span><span class="sxs-lookup"><span data-stu-id="d9475-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="d9475-192">Более того, поддержку новой процессорной архитектуры в ThreadX можно реализовать всего за несколько недель.</span><span class="sxs-lookup"><span data-stu-id="d9475-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="d9475-193">В результате использование GUIX обеспечивает беспроблемную миграцию приложения и защищает изначальные инвестиции в разработку.</span><span class="sxs-lookup"><span data-stu-id="d9475-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
