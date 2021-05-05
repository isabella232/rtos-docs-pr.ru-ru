---
title: Общие сведения об Azure RTOS GUIX и Azure RTOS GUIX Studio
description: GUIX в ОСРВ Azure — это пакет профессионального качества, созданный в соответствии с потребностями разработчиков внедренных систем.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8f4a1578fcabdabfb213ced9c6593f6cffc964aa
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171409"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="17ca1-103">Общие сведения об Azure RTOS GUIX и Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="17ca1-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="17ca1-104">Встроенный графический пользовательский интерфейс Azure GUIX — это усовершенствованное решение промышленного класса для графического пользовательского интерфейса Майкрософт, специально предназначенное для глубоко внедренных приложений, приложений реального времени и приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="17ca1-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="17ca1-105">Корпорация Майкрософт также предоставляет полнофункциональное средство разработки WYSIWYG для настольных систем, называемое Azure RTOS GUIX Studio, позволяющее разработчикам проектировать графический интерфейс пользователя на рабочем столе и генерировать внедренный код графического пользовательского интерфейса Azure RTOS GUIX, который в дальнейшем можно экспортировать на целевой объект.</span><span class="sxs-lookup"><span data-stu-id="17ca1-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="17ca1-106">Azure RTOS GUIX полностью интегрирована с Azure RTOS ThreadX RTOS и доступна для многих процессоров, поддерживаемых в Azure RTOS ThreadX RTOS.</span><span class="sxs-lookup"><span data-stu-id="17ca1-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="17ca1-107">В сочетании с небольшими требованиями к ресурсам, высокой производительностью и непревзойденной простотой использования Azure RTOS GUIX является идеальным выбором при использовании самых требовательных внедренных приложений Интернета вещей, для которых требуется пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="17ca1-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="17ca1-108">API для Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="17ca1-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="17ca1-109">Мощные API</span><span class="sxs-lookup"><span data-stu-id="17ca1-109">Powerful APIs</span></span>

* <span data-ttu-id="17ca1-110">Полная поддержка рисования прямо на холсте (при необходимости)</span><span class="sxs-lookup"><span data-stu-id="17ca1-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="17ca1-111">Простота взаимодействия с кодом, генерируемом в Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="17ca1-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="17ca1-112">API-интерфейсы для линий, прямоугольников, многоугольников и т. д.</span><span class="sxs-lookup"><span data-stu-id="17ca1-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="17ca1-113">API-интерфейсы для окружностей, дуг, круговых диаграмм, аккордов, эллипсов и т. д.</span><span class="sxs-lookup"><span data-stu-id="17ca1-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="17ca1-114">API-интерфейсы для рисования и размещения текста</span><span class="sxs-lookup"><span data-stu-id="17ca1-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="17ca1-115">Сглаживание, заливка текстурой и сплошная заливка</span><span class="sxs-lookup"><span data-stu-id="17ca1-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="17ca1-116">API-интерфейсы для создания и изменения экранов и мини-приложений</span><span class="sxs-lookup"><span data-stu-id="17ca1-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="17ca1-117">Файлы, генерируемые в Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="17ca1-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="17ca1-118">Автоматически генерируемые исходные файлы ANSI C</span><span class="sxs-lookup"><span data-stu-id="17ca1-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="17ca1-119">Изолирует прикладное программное обеспечение от сведений о макете</span><span class="sxs-lookup"><span data-stu-id="17ca1-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="17ca1-120">Содержит шрифты и изображения, необходимые для разработки пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="17ca1-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="17ca1-121">Генерирует файлы, скомпилированные с кодом приложения</span><span class="sxs-lookup"><span data-stu-id="17ca1-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="17ca1-122">Макет экрана можно обновлять, не влияя на логику приложения</span><span class="sxs-lookup"><span data-stu-id="17ca1-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="17ca1-123">Идентификаторы ресурсов обеспечивают независимость от языка и темы</span><span class="sxs-lookup"><span data-stu-id="17ca1-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="17ca1-124">Функции рисования и обработки событий, настраиваемые пользователем</span><span class="sxs-lookup"><span data-stu-id="17ca1-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="17ca1-125">Библиотека мини-приложений</span><span class="sxs-lookup"><span data-stu-id="17ca1-125">Widget library</span></span>

* <span data-ttu-id="17ca1-126">Предварительно определенный, но настраиваемый набор общих элементов интерфейса</span><span class="sxs-lookup"><span data-stu-id="17ca1-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="17ca1-127">Миниатюрный, компактный и эффективный</span><span class="sxs-lookup"><span data-stu-id="17ca1-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="17ca1-128">Библиотека содержит кнопку, датчик, список, окно, прокрутку, ползунок, индикатор выполнения, подсказку и многое другое</span><span class="sxs-lookup"><span data-stu-id="17ca1-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="17ca1-129">Полностью настраиваемые рисование и внешний вид</span><span class="sxs-lookup"><span data-stu-id="17ca1-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="17ca1-130">Полностью настраиваемая обработка операций и событий</span><span class="sxs-lookup"><span data-stu-id="17ca1-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="17ca1-131">С прикладным программным обеспечением связаны только используемые мини-приложения</span><span class="sxs-lookup"><span data-stu-id="17ca1-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="17ca1-132">Математические функции и служебные программы</span><span class="sxs-lookup"><span data-stu-id="17ca1-132">Math and utilities</span></span>

* <span data-ttu-id="17ca1-133">Функции для синуса, косинуса, арксинуса, арккоссинуса, тангенса, квадратного корня</span><span class="sxs-lookup"><span data-stu-id="17ca1-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="17ca1-134">Функции для работы с областями экрана</span><span class="sxs-lookup"><span data-stu-id="17ca1-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="17ca1-135">Настройка и запуск системы</span><span class="sxs-lookup"><span data-stu-id="17ca1-135">System configuration and startup</span></span>
* <span data-ttu-id="17ca1-136">Определение пула памяти (необязательно)</span><span class="sxs-lookup"><span data-stu-id="17ca1-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="17ca1-137">Управление таймерами</span><span class="sxs-lookup"><span data-stu-id="17ca1-137">Timer Management</span></span>
* <span data-ttu-id="17ca1-138">Диспетчер анимации</span><span class="sxs-lookup"><span data-stu-id="17ca1-138">Animation Management</span></span>
* <span data-ttu-id="17ca1-139">Обслуживание "грязных" списков</span><span class="sxs-lookup"><span data-stu-id="17ca1-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="17ca1-140">Обработка изображений</span><span class="sxs-lookup"><span data-stu-id="17ca1-140">Image processing</span></span>

* <span data-ttu-id="17ca1-141">Функции для декодирования изображений JPEG и PNG в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="17ca1-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="17ca1-142">Применение сглаживания и преобразования цветового пространства</span><span class="sxs-lookup"><span data-stu-id="17ca1-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="17ca1-143">Поворот изображений</span><span class="sxs-lookup"><span data-stu-id="17ca1-143">Image rotation</span></span>
* <span data-ttu-id="17ca1-144">Масштабирование изображений</span><span class="sxs-lookup"><span data-stu-id="17ca1-144">Image scaling</span></span>
* <span data-ttu-id="17ca1-145">Смешение изображений</span><span class="sxs-lookup"><span data-stu-id="17ca1-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="17ca1-146">Обработка событий</span><span class="sxs-lookup"><span data-stu-id="17ca1-146">Event processing</span></span>

* <span data-ttu-id="17ca1-147">Автоматическая приостановка потока Azure RTOS GUIX во время простоя</span><span class="sxs-lookup"><span data-stu-id="17ca1-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="17ca1-148">Модель программирования на основе событий, популярная при проектировании пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="17ca1-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="17ca1-149">Изолирует входные драйверы от потока рисования Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="17ca1-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="17ca1-150">Функции для отправки и получения событий</span><span class="sxs-lookup"><span data-stu-id="17ca1-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="17ca1-151">Предварительно определенные типы событий для всех типов мини-приложений Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="17ca1-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="17ca1-152">Поддержка определяемых пользователем пользовательских событий</span><span class="sxs-lookup"><span data-stu-id="17ca1-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="17ca1-153">Обработка холста</span><span class="sxs-lookup"><span data-stu-id="17ca1-153">Canvas processing</span></span>

* <span data-ttu-id="17ca1-154">Усечение и поддержка Z-порядка</span><span class="sxs-lookup"><span data-stu-id="17ca1-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="17ca1-155">Изолирует библиотеку мини-приложений от сведений об оборудовании</span><span class="sxs-lookup"><span data-stu-id="17ca1-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="17ca1-156">Изолирует приложение от сведений об оборудовании</span><span class="sxs-lookup"><span data-stu-id="17ca1-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="17ca1-157">Автоматическое фоновое обновление "грязных" областей</span><span class="sxs-lookup"><span data-stu-id="17ca1-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="17ca1-158">Несколько холстов с поддержкой уровней и смешения</span><span class="sxs-lookup"><span data-stu-id="17ca1-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="17ca1-159">Может вызываться непосредственно прикладным программным обеспечением</span><span class="sxs-lookup"><span data-stu-id="17ca1-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="17ca1-160">Драйверы устройств ввода</span><span class="sxs-lookup"><span data-stu-id="17ca1-160">Input device driver(s)</span></span>

* <span data-ttu-id="17ca1-161">Специальная поддержка оборудования, Azure RTOS GUIX и приложения изолированы от сведений об оборудовании</span><span class="sxs-lookup"><span data-stu-id="17ca1-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="17ca1-162">Поддержка резистивного сенсорного экрана, емкостного сенсорного ввода и цифровой клавиатуры</span><span class="sxs-lookup"><span data-stu-id="17ca1-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="17ca1-163">Входные события передаются в очередь событий Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="17ca1-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="17ca1-164">Драйверы дисплея</span><span class="sxs-lookup"><span data-stu-id="17ca1-164">Display drivers</span></span>

* <span data-ttu-id="17ca1-165">Поддержка конкретного оборудования</span><span class="sxs-lookup"><span data-stu-id="17ca1-165">Hardware-specific support</span></span>
* <span data-ttu-id="17ca1-166">Универсальные драйверы, предоставляемые для любой глубины и цвета и всех форматов</span><span class="sxs-lookup"><span data-stu-id="17ca1-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="17ca1-167">Настраивается для использования доступных графических ускорителей</span><span class="sxs-lookup"><span data-stu-id="17ca1-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="17ca1-168">Целевое оборудование</span><span class="sxs-lookup"><span data-stu-id="17ca1-168">Target hardware</span></span>

* <span data-ttu-id="17ca1-169">С GUIX совместимо практически любое оборудование, способное выводить данные в графическом формате</span><span class="sxs-lookup"><span data-stu-id="17ca1-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="17ca1-170">Поддерживаются несколько физических дисплеев</span><span class="sxs-lookup"><span data-stu-id="17ca1-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="17ca1-171">Минимальные требования к ОЗУ и флэш-памяти</span><span class="sxs-lookup"><span data-stu-id="17ca1-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="17ca1-172">Создание элегантных пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="17ca1-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="17ca1-173">Azure RTOS GUIX и Azure RTOS GUIX Studio предоставляют все необходимые функции для создания уникальных элегантных пользовательских интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="17ca1-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="17ca1-174">Стандартный пакет Azure RTOS GUIX содержит различные примеры пользовательских интерфейсов, включая справочник по медицинским устройствам, справочник по умным часам, справочник по домашней автоматике, справочник по управлению промышленными процессами, справочник по автомобилестроению, а также различные примеры спрайтов и анимации.</span><span class="sxs-lookup"><span data-stu-id="17ca1-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="17ca1-175">Щелкните приведенные ниже примеры справочников.</span><span class="sxs-lookup"><span data-stu-id="17ca1-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="17ca1-176">Домашняя автоматика</span><span class="sxs-lookup"><span data-stu-id="17ca1-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="17ca1-177">Медицина</span><span class="sxs-lookup"><span data-stu-id="17ca1-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="17ca1-178">Потребители</span><span class="sxs-lookup"><span data-stu-id="17ca1-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="17ca1-179">Белые товары</span><span class="sxs-lookup"><span data-stu-id="17ca1-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="17ca1-180">Автомобилестроение</span><span class="sxs-lookup"><span data-stu-id="17ca1-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="17ca1-181">Промышленный сектор</span><span class="sxs-lookup"><span data-stu-id="17ca1-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="17ca1-182">Каждый справочник в Azure RTOS GUIX содержит соответствующий проект Azure RTOS GUIX Studio, где определены все графические элементы эталонного проекта.</span><span class="sxs-lookup"><span data-stu-id="17ca1-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="17ca1-183">Эталонный проект можно очень легко изменить.</span><span class="sxs-lookup"><span data-stu-id="17ca1-183">Changing a reference design is easy.</span></span> <span data-ttu-id="17ca1-184">Просто откройте соответствующий проект Azure RTOS GUIX, внесите необходимые изменения, сохраните проект, а затем нажмите *Проект*.</span><span class="sxs-lookup"><span data-stu-id="17ca1-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="17ca1-185">Сгенерируйте все выходные файлы, чтобы создать код на C для Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="17ca1-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="17ca1-186">Затем просто перестройте целевое приложение и запустите его, чтобы проверить измененный эталонный проект.</span><span class="sxs-lookup"><span data-stu-id="17ca1-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="memory-footprint"></a><span data-ttu-id="17ca1-187">Занимаемая память</span><span class="sxs-lookup"><span data-stu-id="17ca1-187">Memory footprint</span></span>

<span data-ttu-id="17ca1-188">Azure RTOS GUIX имеет очень небольшой объем флэш-памяти (13,2 КБ) и ОЗУ (4 КБ) для базовой поддержки, не включая память, требуемую для холста.</span><span class="sxs-lookup"><span data-stu-id="17ca1-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="17ca1-189">Для дисплея, где применяются внутренняя память GRAM и технологии автоматического обновления, память холста не требуется.</span><span class="sxs-lookup"><span data-stu-id="17ca1-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="17ca1-190">Однако для повышения качества рисования или для конфигурации дисплея, где память GRAM не используется локально для дисплея, область памяти холста определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="17ca1-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="17ca1-191">Требования к памяти холста зависят от размера холста и глубины цвета, которые определяются по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="17ca1-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="17ca1-192"><i>ОЗУ холста (байты) = (x \* y \* (бит/пкс/8))</i></span><span class="sxs-lookup"><span data-stu-id="17ca1-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="17ca1-193">Где "x" и "y" — размеры холста (дисплей).</span><span class="sxs-lookup"><span data-stu-id="17ca1-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="17ca1-194">Большинство приложений также используют графические ресурсы, которые не включены в базовые требования к хранилищу библиотеки Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="17ca1-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="17ca1-195">К этим ресурсам относятся шрифты, графические значки (карты отображения пикселей) и статические строки.</span><span class="sxs-lookup"><span data-stu-id="17ca1-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="17ca1-196">Эти данные могут храниться в разделе памяти констант (т. е. во флэш-памяти).</span><span class="sxs-lookup"><span data-stu-id="17ca1-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="17ca1-197">Размер этой области памяти зависит от разных факторов, к которым относятся количество и размер используемых уникальных шрифтов, количество и размер используемых графических значков, формат выходного цвета, а также необходимость применения сжатых данных в каждом из ресурсов, так как Azure RTOS GUIX поддерживает сжатие данных, связанных со шрифтами и картами отображения пикселей.</span><span class="sxs-lookup"><span data-stu-id="17ca1-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="17ca1-198">Требования к хранилищу для каждого ресурса отображаются в приложении Azure RTOS GUIX Studio, благодаря чему пользователь может контролировать и отслеживать объем флэш-памяти, который будет использоваться ресурсами приложения.</span><span class="sxs-lookup"><span data-stu-id="17ca1-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="17ca1-199">Как и в случае с Azure RTOS ThreadX, размер Azure RTOS GUIX масштабируется автоматически в зависимости от служб, фактически применяемых приложением.</span><span class="sxs-lookup"><span data-stu-id="17ca1-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="17ca1-200">Это практически полностью устраняет потребность в сложной настройке и параметрах сборки, что упрощает работу разработчика.</span><span class="sxs-lookup"><span data-stu-id="17ca1-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="17ca1-201">Простота использования</span><span class="sxs-lookup"><span data-stu-id="17ca1-201">Simple, easy-to-use</span></span>

<span data-ttu-id="17ca1-202">Azure RTOS GUIX очень прост в использовании, а Azure RTOS GUIX Studio еще более упрощает работу в этой системе, так как позволяет разработчикам визуально проектировать на рабочем столе и генерировать код на языке C, который выполняется на фактическом целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="17ca1-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="17ca1-203">Затем приложения могут добавлять собственные пользовательские функции обработки событий и рисования для создания полнофункционального графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="17ca1-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="17ca1-204">Процедура применения API для Azure RTOS GUIX является очень простой.</span><span class="sxs-lookup"><span data-stu-id="17ca1-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="17ca1-205">Данный API интуитивно понятен и поддерживает много функций.</span><span class="sxs-lookup"><span data-stu-id="17ca1-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="17ca1-206">Названия API состоят из реальных слов, а не из набора букв и (или) сокращенных имен, которые так часто используются в других файловых системах.</span><span class="sxs-lookup"><span data-stu-id="17ca1-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="17ca1-207">Все API-интерфейсы для Azure RTOS GUIX имеют префикс *gx_* и соответствуют соглашению об именовании с использованием конструкции "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="17ca1-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="17ca1-208">Более того, в рамках всего API обеспечивается функциональная согласованность.</span><span class="sxs-lookup"><span data-stu-id="17ca1-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="17ca1-209">Например, все API-интерфейсы, инициализирующие блок управления мини-приложением, называются &lt; widget_type&gt;_create, а параметры создания функции для каждого типа мини-приложения всегда определяются в одном и том же порядке.</span><span class="sxs-lookup"><span data-stu-id="17ca1-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="17ca1-210">Полный набор встроенных мини-приложений</span><span class="sxs-lookup"><span data-stu-id="17ca1-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="17ca1-211">Azure RTOS GUIX предоставляет широкий набор встроенных мини-приложений, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="17ca1-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="17ca1-212">Меню "гармошка"</span><span class="sxs-lookup"><span data-stu-id="17ca1-212">Accordion Menu</span></span>
* <span data-ttu-id="17ca1-213">Кнопка</span><span class="sxs-lookup"><span data-stu-id="17ca1-213">Button</span></span>
* <span data-ttu-id="17ca1-214">Флажок</span><span class="sxs-lookup"><span data-stu-id="17ca1-214">Checkbox</span></span>
* <span data-ttu-id="17ca1-215">Круговой датчик</span><span class="sxs-lookup"><span data-stu-id="17ca1-215">Circular Gauge</span></span>
* <span data-ttu-id="17ca1-216">Раскрывающийся список</span><span class="sxs-lookup"><span data-stu-id="17ca1-216">Drop Down List</span></span>
* <span data-ttu-id="17ca1-217">Горизонтальный список</span><span class="sxs-lookup"><span data-stu-id="17ca1-217">Horizontal List</span></span>
* <span data-ttu-id="17ca1-218">Окно с горизонтальной полосой прокрутки</span><span class="sxs-lookup"><span data-stu-id="17ca1-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="17ca1-219">Значок</span><span class="sxs-lookup"><span data-stu-id="17ca1-219">Icon</span></span>
* <span data-ttu-id="17ca1-220">Кнопка со значком</span><span class="sxs-lookup"><span data-stu-id="17ca1-220">Icon Button</span></span>
* <span data-ttu-id="17ca1-221">График</span><span class="sxs-lookup"><span data-stu-id="17ca1-221">Line Chart</span></span>
* <span data-ttu-id="17ca1-222">Меню</span><span class="sxs-lookup"><span data-stu-id="17ca1-222">Menu</span></span>
* <span data-ttu-id="17ca1-223">Кнопка с многострочным текстом</span><span class="sxs-lookup"><span data-stu-id="17ca1-223">Multi Line Text Button</span></span>
* <span data-ttu-id="17ca1-224">Ввод многострочного текста</span><span class="sxs-lookup"><span data-stu-id="17ca1-224">Multi Line Text Input</span></span>
* <span data-ttu-id="17ca1-225">Представление многострочного текста</span><span class="sxs-lookup"><span data-stu-id="17ca1-225">Multi Line Text View</span></span>
* <span data-ttu-id="17ca1-226">Числовой запрос карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="17ca1-227">Числовой запрос</span><span class="sxs-lookup"><span data-stu-id="17ca1-227">Numeric Prompt</span></span>
* <span data-ttu-id="17ca1-228">Числовое колесо прокрутки</span><span class="sxs-lookup"><span data-stu-id="17ca1-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="17ca1-229">Кнопка карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-229">Pixelmap Button</span></span>
* <span data-ttu-id="17ca1-230">Запрос карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="17ca1-231">Ползунок карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-231">Pixelmap Slider</span></span>
* <span data-ttu-id="17ca1-232">Спрайт карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="17ca1-233">Progress Bar</span><span class="sxs-lookup"><span data-stu-id="17ca1-233">Progress Bar</span></span>
* <span data-ttu-id="17ca1-234">prompt</span><span class="sxs-lookup"><span data-stu-id="17ca1-234">Prompt</span></span>
* <span data-ttu-id="17ca1-235">Круговой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="17ca1-235">Radial Progress Bar</span></span>
* <span data-ttu-id="17ca1-236">Radio Button</span><span class="sxs-lookup"><span data-stu-id="17ca1-236">Radio Button</span></span>
* <span data-ttu-id="17ca1-237">Колесо прокрутки</span><span class="sxs-lookup"><span data-stu-id="17ca1-237">Scroll Wheel</span></span>
* <span data-ttu-id="17ca1-238">Ввод однострочного текста</span><span class="sxs-lookup"><span data-stu-id="17ca1-238">Single Line Text Input</span></span>
* <span data-ttu-id="17ca1-239">Ползунок</span><span class="sxs-lookup"><span data-stu-id="17ca1-239">Slider</span></span>
* <span data-ttu-id="17ca1-240">Строковое колесо прокрутки</span><span class="sxs-lookup"><span data-stu-id="17ca1-240">String Scroll Wheel</span></span>
* <span data-ttu-id="17ca1-241">Кнопка "Текст"</span><span class="sxs-lookup"><span data-stu-id="17ca1-241">Text Button</span></span>
* <span data-ttu-id="17ca1-242">Вид дерева</span><span class="sxs-lookup"><span data-stu-id="17ca1-242">Tree View</span></span>
* <span data-ttu-id="17ca1-243">Вертикальный список</span><span class="sxs-lookup"><span data-stu-id="17ca1-243">Vertical List</span></span>
* <span data-ttu-id="17ca1-244">Вертикальная полоса прокрутки</span><span class="sxs-lookup"><span data-stu-id="17ca1-244">Vertical Scrollbar</span></span>

<span data-ttu-id="17ca1-245">Приложение также легко создает свои собственные мини-приложения клиента.</span><span class="sxs-lookup"><span data-stu-id="17ca1-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="17ca1-246">Полнофункциональный API для низкоуровневого рисования</span><span class="sxs-lookup"><span data-stu-id="17ca1-246">Complete low-level drawing API</span></span>

<span data-ttu-id="17ca1-247">Azure RTOS GUIX предоставляет надежный API для рисования на холсте, благодаря которому приложение может визуализировать сложные графические фигуры.</span><span class="sxs-lookup"><span data-stu-id="17ca1-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="17ca1-248">Все функции поддерживают сглаживание на целевых объектах с большой глубиной цвета, а все фигуры могут быть заполнены по контуру, включая сплошные заливки и узорные заливки с использованием карты отображения пикселей.</span><span class="sxs-lookup"><span data-stu-id="17ca1-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="17ca1-249">Все примитивы рисования поддерживают альфа-фактор кисти при работе с глубиной цвета 16 бит/пкс и больше.</span><span class="sxs-lookup"><span data-stu-id="17ca1-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="17ca1-250">Ниже перечислены функции рисования:</span><span class="sxs-lookup"><span data-stu-id="17ca1-250">Drawing functions include:</span></span>

* <span data-ttu-id="17ca1-251">Рисование дуги</span><span class="sxs-lookup"><span data-stu-id="17ca1-251">Arc Draw</span></span>
* <span data-ttu-id="17ca1-252">Рисование окружности</span><span class="sxs-lookup"><span data-stu-id="17ca1-252">Circle Draw</span></span>
* <span data-ttu-id="17ca1-253">Рисование линии</span><span class="sxs-lookup"><span data-stu-id="17ca1-253">Line Draw</span></span>
* <span data-ttu-id="17ca1-254">Рисование круговых диаграмм</span><span class="sxs-lookup"><span data-stu-id="17ca1-254">Pie Draw</span></span>
* <span data-ttu-id="17ca1-255">Смешение карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-255">Pixelmap Blend</span></span>
* <span data-ttu-id="17ca1-256">Плитка карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-256">Pixelmap Tile</span></span>
* <span data-ttu-id="17ca1-257">Рисование многоугольника</span><span class="sxs-lookup"><span data-stu-id="17ca1-257">Polygon Draw</span></span>
* <span data-ttu-id="17ca1-258">Рисование текста</span><span class="sxs-lookup"><span data-stu-id="17ca1-258">Text Draw</span></span>
* <span data-ttu-id="17ca1-259">Рисование аккорда</span><span class="sxs-lookup"><span data-stu-id="17ca1-259">Chord Draw</span></span>
* <span data-ttu-id="17ca1-260">Рисование эллипса</span><span class="sxs-lookup"><span data-stu-id="17ca1-260">Ellipse Draw</span></span>
* <span data-ttu-id="17ca1-261">Рисование пикселя</span><span class="sxs-lookup"><span data-stu-id="17ca1-261">Pixel Draw</span></span>
* <span data-ttu-id="17ca1-262">Рисование карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-262">Pixelmap Draw</span></span>
* <span data-ttu-id="17ca1-263">Вращение карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="17ca1-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="17ca1-264">Рисование прямоугольника</span><span class="sxs-lookup"><span data-stu-id="17ca1-264">Rectangle Draw</span></span>
* <span data-ttu-id="17ca1-265">Смешение текста</span><span class="sxs-lookup"><span data-stu-id="17ca1-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="17ca1-266">Бесплатные шрифты по умолчанию и простое добавление шрифтов</span><span class="sxs-lookup"><span data-stu-id="17ca1-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="17ca1-267">Azure RTOS GUIX предоставляет бесплатный набор шрифтов TrueType.</span><span class="sxs-lookup"><span data-stu-id="17ca1-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="17ca1-268">При необходимости разработчики могут добавлять дополнительные шрифты TrueType.</span><span class="sxs-lookup"><span data-stu-id="17ca1-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="17ca1-269">Формат шрифтов в Azure RTOS GUIX поддерживает шрифты со сглаживанием 8 бит/пкс, шрифты со сглаживанием 4 бит/пкс и монохромные шрифты 1 бит/пкс.</span><span class="sxs-lookup"><span data-stu-id="17ca1-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="17ca1-270">Для большинства приложений, для которых существуют ограничения по ресурсам, Azure RTOS GUIX выполняет предварительную обработку шрифтов TrueType, чтобы получить сжатый растровый формат, с помощью нашего классического средства GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="17ca1-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="17ca1-271">Реализация пользовательского декодера JPG и PNG</span><span class="sxs-lookup"><span data-stu-id="17ca1-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="17ca1-272">Реализация пользовательского декодера JPG и PNG.</span><span class="sxs-lookup"><span data-stu-id="17ca1-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="17ca1-273">Эта реализация поддерживает преобразование цветового пространства, сглаживание и создание в среде выполнения изображений в формате карты отображения пикселей, совместимых с Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="17ca1-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="17ca1-274">Расширенная поддержка дисплеев и сенсорных экранов</span><span class="sxs-lookup"><span data-stu-id="17ca1-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="17ca1-275">Azure RTOS GUIX предоставляет универсальные драйверы дисплея практически для любых форматов цвета, включая монохромный 1 бит/пкс, палитру 8 бит/пкс, формат 8 бит/пкс 3:3:2,</span><span class="sxs-lookup"><span data-stu-id="17ca1-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="17ca1-276">16 бит/пкс 565 rgb, 16 бит/пкс 4:4:4:4, 32 бит/пкс x:r:g:b и 32 бит/пкс a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="17ca1-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="17ca1-277">Кроме того, Azure RTOS GUIX интегрируется с различными наиболее популярными ЖК-контроллерами и аппаратными ускорителями (ST ChromeArt, Renesas Synergy и т. д.).</span><span class="sxs-lookup"><span data-stu-id="17ca1-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="17ca1-278">Azure RTOS GUIX полностью поддерживает сенсорные экраны (включая поддержку жестов), перья и виртуальные устройства ввода с клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="17ca1-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="17ca1-279">Классическое средство WYSIWYG в Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="17ca1-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="17ca1-280">Azure RTOS GUIX Studio предоставляет законченную среду разработки экранов WYSIWYG, которая позволяет пользователю перетаскивать графические элементы, используемые для построения экранов графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="17ca1-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="17ca1-281">Azure RTOS GUIX Studio автоматически генерирует код на языке C, совместимый с библиотекой Azure RTOS GUIX, который готов к компиляции и выполнению на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="17ca1-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="17ca1-282">С помощью интегрированного средства создания шрифтов в Azure RTOS GUIX Studio разработчики могут создавать предварительно подготовленные для просмотра шрифты для использования в приложении.</span><span class="sxs-lookup"><span data-stu-id="17ca1-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="17ca1-283">Шрифты могут генерироваться в виде монохромного формата или формата со сглаживанием и оптимизируются для экономии места на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="17ca1-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="17ca1-284">Шрифты могут включать в себя любой набор символов, в том числе символы Юникода для многоязычных приложений.</span><span class="sxs-lookup"><span data-stu-id="17ca1-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="17ca1-285">Azure RTOS GUIX Studio упрощает импорт графики из файлов PNG или JPG с преобразованием в сжатые карты отображения пикселей Azure RTOS GUIX для использования в целевой системе.</span><span class="sxs-lookup"><span data-stu-id="17ca1-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="17ca1-286">Мини-приложения Azure RTOS GUIX различного типа позволяют встраивать пользовательскую графику для создания внешнего вида, удобного пользователю.</span><span class="sxs-lookup"><span data-stu-id="17ca1-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="17ca1-287">Кроме того, Azure RTOS GUIX Studio позволяет настраивать цвета и стили рисования по умолчанию, используемые мини-приложениями Azure RTOS GUIX, благодаря чему разработчики могут легко настраивать внешний вид интерфейса Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="17ca1-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="17ca1-288">Azure RTOS GUIX Studio также позволяет генерировать и поддерживать строки приложения, используя специальную встроенную функцию.</span><span class="sxs-lookup"><span data-stu-id="17ca1-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="17ca1-289">Благодаря этому разработчики могут проектировать приложения с помощью одного языка для разработки, а также быстро и удобно добавлять поддержку для дополнительных языков после выпуска продукта.</span><span class="sxs-lookup"><span data-stu-id="17ca1-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="17ca1-290">Законченное приложение Azure RTOS GUIX может выполняться на рабочем столе компьютера в среде Azure RTOS GUIX Studio, что позволяет быстро и легко генерировать и демонстрировать концепции графического пользовательского интерфейса, тестировать потоки экрана, а также наблюдать за переходами экрана и анимацией на экране.</span><span class="sxs-lookup"><span data-stu-id="17ca1-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="17ca1-291">По завершении проект можно экспортировать в виде готовых к работе на целевом объекте структур данных на языке C, которые готовы к компиляции и связаны с библиотеками Azure RTOS GUIX и Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="17ca1-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="17ca1-292">Azure RTOS GUIX и Azure RTOS GUIX Studio поддерживают различные темы ресурсов, что позволяет легко изменять внешний вид приложения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="17ca1-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="17ca1-293">Шрифты, цвета и карты отображения пикселей можно изменять во время выполнения с помощью одного простого API.</span><span class="sxs-lookup"><span data-stu-id="17ca1-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="17ca1-294">Дополнительные сведения о GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="17ca1-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="17ca1-295">Полнофункциональная имитация Win32</span><span class="sxs-lookup"><span data-stu-id="17ca1-295">Complete Win32 simulation</span></span>

<span data-ttu-id="17ca1-296">Azure RTOS GUIX работает на компьютере под управлением Windows, используя точно такую же библиотеку, которая выполняется на целевой плате.</span><span class="sxs-lookup"><span data-stu-id="17ca1-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="17ca1-297">Благодаря применению Azure RTOS GUIX можно создавать и запускать приложение графического пользовательского интерфейса на ПК и использовать тот же код приложения на целевом объекте для отладки, быстрого создания прототипа, демонстрации и проверки заданного режима работы в режиме WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="17ca1-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="17ca1-298">Усовершенствованные технологии</span><span class="sxs-lookup"><span data-stu-id="17ca1-298">Advanced technology</span></span>

* <span data-ttu-id="17ca1-299">В Azure RTOS GUIX применяются следующие усовершенствованные технологии:</span><span class="sxs-lookup"><span data-stu-id="17ca1-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="17ca1-300">Альфа-смешение</span><span class="sxs-lookup"><span data-stu-id="17ca1-300">Alpha blending</span></span>
* <span data-ttu-id="17ca1-301">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="17ca1-301">Anti-Aliasing</span></span>
* <span data-ttu-id="17ca1-302">Автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="17ca1-302">Automatic scaling</span></span>
* <span data-ttu-id="17ca1-303">Сжатие растрового изображения</span><span class="sxs-lookup"><span data-stu-id="17ca1-303">Bitmap compression</span></span>
* <span data-ttu-id="17ca1-304">Смешение на холсте</span><span class="sxs-lookup"><span data-stu-id="17ca1-304">Canvas blending</span></span>
* <span data-ttu-id="17ca1-305">Поддержка пользовательских мини-приложений</span><span class="sxs-lookup"><span data-stu-id="17ca1-305">Custom widget support</span></span>
* <span data-ttu-id="17ca1-306">Поддержка отложенного рисования</span><span class="sxs-lookup"><span data-stu-id="17ca1-306">Deferred drawing support</span></span>
* <span data-ttu-id="17ca1-307">Поддержка сглаживания</span><span class="sxs-lookup"><span data-stu-id="17ca1-307">Dithering support</span></span>
* <span data-ttu-id="17ca1-308">Программирование, независимое от порядка байтов</span><span class="sxs-lookup"><span data-stu-id="17ca1-308">Endian neutral programming</span></span>
* <span data-ttu-id="17ca1-309">Поддержка аппаратного ускорителя</span><span class="sxs-lookup"><span data-stu-id="17ca1-309">Hardware accelerator support</span></span>
* <span data-ttu-id="17ca1-310">Многоязычная поддержка и кодировка UTF-8</span><span class="sxs-lookup"><span data-stu-id="17ca1-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="17ca1-311">Поддержка нескольких дисплеев и холстов</span><span class="sxs-lookup"><span data-stu-id="17ca1-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="17ca1-312">Оптимизированные усечение, рисование и обработка событий</span><span class="sxs-lookup"><span data-stu-id="17ca1-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="17ca1-313">Декодер JPEG и PNG в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="17ca1-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="17ca1-314">Создание обложек и темы</span><span class="sxs-lookup"><span data-stu-id="17ca1-314">Skinning and Themes</span></span>
* <span data-ttu-id="17ca1-315">Поддержка различных форматов: монохромный, 32-разрядный True Color с форматами Alpha Graphics</span><span class="sxs-lookup"><span data-stu-id="17ca1-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="17ca1-316">Переходы, спрайты и поддержка анимации</span><span class="sxs-lookup"><span data-stu-id="17ca1-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="17ca1-317">Имитация Win32</span><span class="sxs-lookup"><span data-stu-id="17ca1-317">Win32 simulation</span></span>
* <span data-ttu-id="17ca1-318">Управление окнами, включая окна просмотра и поддержка Z-порядка</span><span class="sxs-lookup"><span data-stu-id="17ca1-318">Window management including Viewports and Z-order maintenance</span></span>
