---
title: Общие сведения об Azure RTOS GUIX и Azure RTOS GUIX Studio
description: GUIX в ОСРВ Azure — это пакет профессионального качества, созданный в соответствии с потребностями разработчиков внедренных систем.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815448"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="38bce-103">Общие сведения об Azure RTOS GUIX и Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="38bce-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="38bce-104">Встроенный графический пользовательский интерфейс Azure GUIX — это усовершенствованное решение промышленного класса для графического пользовательского интерфейса Майкрософт, специально предназначенное для глубоко внедренных приложений, приложений реального времени и приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="38bce-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="38bce-105">Корпорация Майкрософт также предоставляет полнофункциональное средство разработки WYSIWYG для настольных систем, называемое Azure RTOS GUIX Studio, позволяющее разработчикам проектировать графический интерфейс пользователя на рабочем столе и генерировать внедренный код графического пользовательского интерфейса Azure RTOS GUIX, который в дальнейшем можно экспортировать на целевой объект.</span><span class="sxs-lookup"><span data-stu-id="38bce-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="38bce-106">Azure RTOS GUIX полностью интегрирована с Azure RTOS ThreadX RTOS и доступна для многих процессоров, поддерживаемых в Azure RTOS ThreadX RTOS.</span><span class="sxs-lookup"><span data-stu-id="38bce-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="38bce-107">В сочетании с небольшими требованиями к ресурсам, высокой производительностью и непревзойденной простотой использования Azure RTOS GUIX является идеальным выбором при использовании самых требовательных внедренных приложений Интернета вещей, для которых требуется пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="38bce-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="38bce-108">API для Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="38bce-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="38bce-109">Интуитивно понятный и согласованный API</span><span class="sxs-lookup"><span data-stu-id="38bce-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="38bce-110">Соглашение об именовании с использованием конструкции "существительное — глагол"</span><span class="sxs-lookup"><span data-stu-id="38bce-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="38bce-111">Все API-интерфейсы имеют префикс *gx_* для упрощения идентификации их принадлежности к Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="38bce-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="38bce-112">Модель программирования на основе событий (API)</span><span class="sxs-lookup"><span data-stu-id="38bce-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="38bce-113">Полная поддержка рисования прямо на холсте (при необходимости)</span><span class="sxs-lookup"><span data-stu-id="38bce-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="38bce-114">Простота взаимодействия с кодом, генерируемом в Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="38bce-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="38bce-115">API-интерфейсы для линий, прямоугольников, многоугольников и т. д.</span><span class="sxs-lookup"><span data-stu-id="38bce-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="38bce-116">API-интерфейсы для окружностей, дуг, круговых диаграмм, аккордов, эллипсов и т. д.</span><span class="sxs-lookup"><span data-stu-id="38bce-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="38bce-117">API-интерфейсы для рисования и размещения текста</span><span class="sxs-lookup"><span data-stu-id="38bce-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="38bce-118">Сглаживание, заливка текстурой и сплошная заливка</span><span class="sxs-lookup"><span data-stu-id="38bce-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="38bce-119">API-интерфейсы для создания и изменения экранов и мини-приложений</span><span class="sxs-lookup"><span data-stu-id="38bce-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="38bce-120">Файлы, генерируемые в Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="38bce-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="38bce-121">Автоматически генерируемые исходные файлы ANSI C</span><span class="sxs-lookup"><span data-stu-id="38bce-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="38bce-122">Изолирует прикладное программное обеспечение от сведений о макете</span><span class="sxs-lookup"><span data-stu-id="38bce-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="38bce-123">Содержит шрифты и изображения, необходимые для разработки пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="38bce-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="38bce-124">Генерирует файлы, скомпилированные с кодом приложения</span><span class="sxs-lookup"><span data-stu-id="38bce-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="38bce-125">Макет экрана можно обновлять, не влияя на логику приложения</span><span class="sxs-lookup"><span data-stu-id="38bce-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="38bce-126">Идентификаторы ресурсов обеспечивают независимость от языка и темы</span><span class="sxs-lookup"><span data-stu-id="38bce-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="38bce-127">Функции рисования и обработки событий, настраиваемые пользователем</span><span class="sxs-lookup"><span data-stu-id="38bce-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="38bce-128">Библиотека мини-приложений</span><span class="sxs-lookup"><span data-stu-id="38bce-128">Widget library</span></span>

* <span data-ttu-id="38bce-129">Предварительно определенный, но настраиваемый набор общих элементов интерфейса</span><span class="sxs-lookup"><span data-stu-id="38bce-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="38bce-130">Миниатюрный, компактный и эффективный</span><span class="sxs-lookup"><span data-stu-id="38bce-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="38bce-131">Библиотека содержит кнопку, датчик, список, окно, прокрутку, ползунок, индикатор выполнения, подсказку и многое другое</span><span class="sxs-lookup"><span data-stu-id="38bce-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="38bce-132">Полностью настраиваемые рисование и внешний вид</span><span class="sxs-lookup"><span data-stu-id="38bce-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="38bce-133">Полностью настраиваемая обработка операций и событий</span><span class="sxs-lookup"><span data-stu-id="38bce-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="38bce-134">С прикладным программным обеспечением связаны только используемые мини-приложения</span><span class="sxs-lookup"><span data-stu-id="38bce-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="38bce-135">Математические функции и служебные программы</span><span class="sxs-lookup"><span data-stu-id="38bce-135">Math and utilities</span></span>

* <span data-ttu-id="38bce-136">Функции для синуса, косинуса, арксинуса, арккоссинуса, тангенса, квадратного корня</span><span class="sxs-lookup"><span data-stu-id="38bce-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="38bce-137">Функции для работы с областями экрана</span><span class="sxs-lookup"><span data-stu-id="38bce-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="38bce-138">Настройка и запуск системы</span><span class="sxs-lookup"><span data-stu-id="38bce-138">System configuration and startup</span></span>

* <span data-ttu-id="38bce-139">Определение пула памяти (необязательно)</span><span class="sxs-lookup"><span data-stu-id="38bce-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="38bce-140">Управление таймерами</span><span class="sxs-lookup"><span data-stu-id="38bce-140">Timer Management</span></span>

* <span data-ttu-id="38bce-141">Диспетчер анимации</span><span class="sxs-lookup"><span data-stu-id="38bce-141">Animation Management</span></span>

* <span data-ttu-id="38bce-142">Обслуживание "грязных" списков</span><span class="sxs-lookup"><span data-stu-id="38bce-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="38bce-143">Обработка изображений</span><span class="sxs-lookup"><span data-stu-id="38bce-143">Image processing</span></span>

* <span data-ttu-id="38bce-144">Функции для декодирования изображений JPEG и PNG в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="38bce-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="38bce-145">Применение сглаживания и преобразования цветового пространства</span><span class="sxs-lookup"><span data-stu-id="38bce-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="38bce-146">Поворот изображений</span><span class="sxs-lookup"><span data-stu-id="38bce-146">Image rotation</span></span>

* <span data-ttu-id="38bce-147">Масштабирование изображений</span><span class="sxs-lookup"><span data-stu-id="38bce-147">Image scaling</span></span>

* <span data-ttu-id="38bce-148">Смешение изображений</span><span class="sxs-lookup"><span data-stu-id="38bce-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="38bce-149">Обработка событий</span><span class="sxs-lookup"><span data-stu-id="38bce-149">Event processing</span></span>

* <span data-ttu-id="38bce-150">Автоматическая приостановка потока Azure RTOS GUIX во время простоя</span><span class="sxs-lookup"><span data-stu-id="38bce-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="38bce-151">Модель программирования на основе событий, популярная при проектировании пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="38bce-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="38bce-152">Изолирует входные драйверы от потока рисования Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="38bce-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="38bce-153">Функции для отправки и получения событий</span><span class="sxs-lookup"><span data-stu-id="38bce-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="38bce-154">Предварительно определенные типы событий для всех типов мини-приложений Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="38bce-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="38bce-155">Поддержка определяемых пользователем пользовательских событий</span><span class="sxs-lookup"><span data-stu-id="38bce-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="38bce-156">Обработка холста</span><span class="sxs-lookup"><span data-stu-id="38bce-156">Canvas processing</span></span>

* <span data-ttu-id="38bce-157">Усечение и поддержка Z-порядка</span><span class="sxs-lookup"><span data-stu-id="38bce-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="38bce-158">Изолирует библиотеку мини-приложений от сведений об оборудовании</span><span class="sxs-lookup"><span data-stu-id="38bce-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="38bce-159">Изолирует приложение от сведений об оборудовании</span><span class="sxs-lookup"><span data-stu-id="38bce-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="38bce-160">Автоматическое фоновое обновление "грязных" областей</span><span class="sxs-lookup"><span data-stu-id="38bce-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="38bce-161">Несколько холстов с поддержкой уровней и смешения</span><span class="sxs-lookup"><span data-stu-id="38bce-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="38bce-162">Может вызываться непосредственно прикладным программным обеспечением</span><span class="sxs-lookup"><span data-stu-id="38bce-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="38bce-163">Драйверы устройств ввода</span><span class="sxs-lookup"><span data-stu-id="38bce-163">Input device driver(s)</span></span>

* <span data-ttu-id="38bce-164">Специальная поддержка оборудования, Azure RTOS GUIX и приложения изолированы от сведений об оборудовании</span><span class="sxs-lookup"><span data-stu-id="38bce-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="38bce-165">Поддержка резистивного сенсорного экрана, емкостного сенсорного ввода и цифровой клавиатуры</span><span class="sxs-lookup"><span data-stu-id="38bce-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="38bce-166">Входные события передаются в очередь событий Azure RTOS GUIX</span><span class="sxs-lookup"><span data-stu-id="38bce-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="38bce-167">Драйверы дисплея</span><span class="sxs-lookup"><span data-stu-id="38bce-167">Display drivers</span></span>

* <span data-ttu-id="38bce-168">Поддержка конкретного оборудования</span><span class="sxs-lookup"><span data-stu-id="38bce-168">Hardware-specific support</span></span>

* <span data-ttu-id="38bce-169">Универсальные драйверы, предоставляемые для любой глубины и цвета и всех форматов</span><span class="sxs-lookup"><span data-stu-id="38bce-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="38bce-170">Настраивается для использования доступных графических ускорителей</span><span class="sxs-lookup"><span data-stu-id="38bce-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="38bce-171">Целевое оборудование</span><span class="sxs-lookup"><span data-stu-id="38bce-171">Target hardware</span></span>

* <span data-ttu-id="38bce-172">С GUIX совместимо практически любое оборудование, способное выводить данные в графическом формате</span><span class="sxs-lookup"><span data-stu-id="38bce-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="38bce-173">Поддерживаются несколько физических дисплеев</span><span class="sxs-lookup"><span data-stu-id="38bce-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="38bce-174">Минимальные требования к ОЗУ и флэш-памяти</span><span class="sxs-lookup"><span data-stu-id="38bce-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="38bce-175">Создание элегантных пользовательских интерфейсов</span><span class="sxs-lookup"><span data-stu-id="38bce-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="38bce-176">Azure RTOS GUIX и Azure RTOS GUIX Studio предоставляют все необходимые функции для создания уникальных элегантных пользовательских интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="38bce-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="38bce-177">Стандартный пакет Azure RTOS GUIX содержит различные примеры пользовательских интерфейсов, включая справочник по медицинским устройствам, справочник по умным часам, справочник по домашней автоматике, справочник по управлению промышленными процессами, справочник по автомобилестроению, а также различные примеры спрайтов и анимации.</span><span class="sxs-lookup"><span data-stu-id="38bce-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="38bce-178">Щелкните приведенные ниже примеры справочников.</span><span class="sxs-lookup"><span data-stu-id="38bce-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="38bce-179">Домашняя автоматика</span><span class="sxs-lookup"><span data-stu-id="38bce-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="38bce-180">Медицина</span><span class="sxs-lookup"><span data-stu-id="38bce-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="38bce-181">Потребители</span><span class="sxs-lookup"><span data-stu-id="38bce-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="38bce-182">Белые товары</span><span class="sxs-lookup"><span data-stu-id="38bce-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="38bce-183">Автомобилестроение</span><span class="sxs-lookup"><span data-stu-id="38bce-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="38bce-184">Промышленный сектор</span><span class="sxs-lookup"><span data-stu-id="38bce-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="38bce-185">Каждый справочник в Azure RTOS GUIX содержит соответствующий проект Azure RTOS GUIX Studio, где определены все графические элементы эталонного проекта.</span><span class="sxs-lookup"><span data-stu-id="38bce-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="38bce-186">Эталонный проект можно очень легко изменить.</span><span class="sxs-lookup"><span data-stu-id="38bce-186">Changing a reference design is easy.</span></span> <span data-ttu-id="38bce-187">Просто откройте соответствующий проект Azure RTOS GUIX, внесите необходимые изменения, сохраните проект, а затем нажмите *Проект*.</span><span class="sxs-lookup"><span data-stu-id="38bce-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="38bce-188">Сгенерируйте все выходные файлы, чтобы создать код на C для Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="38bce-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="38bce-189">Затем просто перестройте целевое приложение и запустите его, чтобы проверить измененный эталонный проект.</span><span class="sxs-lookup"><span data-stu-id="38bce-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="38bce-190">Небольшой объем занимаемой памяти</span><span class="sxs-lookup"><span data-stu-id="38bce-190">Small-footprint</span></span>

<span data-ttu-id="38bce-191">Azure RTOS GUIX имеет очень небольшой объем флэш-памяти (13,2 КБ) и ОЗУ (4 КБ) для базовой поддержки, не включая память, требуемую для холста.</span><span class="sxs-lookup"><span data-stu-id="38bce-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="38bce-192">Для дисплея, где применяются внутренняя память GRAM и технологии автоматического обновления, память холста не требуется.</span><span class="sxs-lookup"><span data-stu-id="38bce-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="38bce-193">Однако для повышения качества рисования или для конфигурации дисплея, где память GRAM не используется локально для дисплея, область памяти холста определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="38bce-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="38bce-194">Требования к памяти холста зависят от размера холста и глубины цвета, которые определяются по следующей формуле:</span><span class="sxs-lookup"><span data-stu-id="38bce-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="38bce-195"><i>ОЗУ холста (байты) = (x \* y \* (бит/пкс/8))</i></span><span class="sxs-lookup"><span data-stu-id="38bce-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="38bce-196">Где "x" и "y" — размеры холста (дисплей).</span><span class="sxs-lookup"><span data-stu-id="38bce-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="38bce-197">Большинство приложений также используют графические ресурсы, которые не включены в базовые требования к хранилищу библиотеки Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="38bce-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="38bce-198">К этим ресурсам относятся шрифты, графические значки (карты отображения пикселей) и статические строки.</span><span class="sxs-lookup"><span data-stu-id="38bce-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="38bce-199">Эти данные могут храниться в разделе памяти констант (т. е. во флэш-памяти).</span><span class="sxs-lookup"><span data-stu-id="38bce-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="38bce-200">Размер этой области памяти зависит от разных факторов, к которым относятся количество и размер используемых уникальных шрифтов, количество и размер используемых графических значков, формат выходного цвета, а также необходимость применения сжатых данных в каждом из ресурсов, так как Azure RTOS GUIX поддерживает сжатие данных, связанных со шрифтами и картами отображения пикселей.</span><span class="sxs-lookup"><span data-stu-id="38bce-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="38bce-201">Требования к хранилищу для каждого ресурса отображаются в приложении Azure RTOS GUIX Studio, благодаря чему пользователь может контролировать и отслеживать объем флэш-памяти, который будет использоваться ресурсами приложения.</span><span class="sxs-lookup"><span data-stu-id="38bce-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="38bce-202">Как и в случае с Azure RTOS ThreadX, размер Azure RTOS GUIX масштабируется автоматически в зависимости от служб, фактически применяемых приложением.</span><span class="sxs-lookup"><span data-stu-id="38bce-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="38bce-203">Это практически полностью устраняет потребность в сложной настройке и параметрах сборки, что упрощает работу разработчика.</span><span class="sxs-lookup"><span data-stu-id="38bce-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="38bce-204">Быстрое выполнение</span><span class="sxs-lookup"><span data-stu-id="38bce-204">Fast execution</span></span>

<span data-ttu-id="38bce-205">Azure RTOS GUIX написана исключительно на языке C и предназначена для обеспечения высокой производительности.</span><span class="sxs-lookup"><span data-stu-id="38bce-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="38bce-206">В Azure RTOS GUIX реализовано минимальное количество уровней для вызовов внутренних функций.</span><span class="sxs-lookup"><span data-stu-id="38bce-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="38bce-207">Кроме того, Azure RTOS GUIX обеспечивает оптимизированные усечение, рисование и обработку событий.</span><span class="sxs-lookup"><span data-stu-id="38bce-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="38bce-208">Благодаря этому, а также проекту, ориентированному на обеспечение высокого быстродействия, Azure RTOS GUIX способна достигать максимально высокого уровня производительности.</span><span class="sxs-lookup"><span data-stu-id="38bce-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="38bce-209">Предварительная сертификация TUV на соответствие различным стандартам безопасности</span><span class="sxs-lookup"><span data-stu-id="38bce-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="38bce-210">Azure RTOS GUIX сертифицирована организацией SGS-TUV Saar для использования в системах со строгими требованиями к безопасности в соответствии со стандартами IEC-61508 SIL 4, IEC-62304 SW (класс безопасности C), ISO 26262 ASIL D и EN 50128.</span><span class="sxs-lookup"><span data-stu-id="38bce-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="38bce-211">Данный сертификат гарантирует, что Azure RTOS GUIX можно использовать при разработке ПО с особыми требованиями к функциональной безопасности, соответствующего высочайшим уровням полноты безопасности по стандартам IEC-61508, IEC-62304, ISO 26262 и EN 50128 для "функциональной безопасности электрических, электронных и программируемых электронных систем, связанных с безопасностью".</span><span class="sxs-lookup"><span data-stu-id="38bce-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="38bce-212">Компания SGS-TUV Saar, основанная совместно немецкими компаниями SGS-Group и TUV Saarland, стала ведущей аккредитованной и независимой компанией, выполняющей тестирование, аудит, проверку и сертификацию внедренного ПО для связанных с безопасностью систем.</span><span class="sxs-lookup"><span data-stu-id="38bce-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="38bce-213">Соответствие промышленному стандарту безопасности IEC 61508 и всем его производным стандартам, в том числе IEC-62304, ISO 26262 и EN 50128, гарантирует функциональную безопасность электрических, электронных и программируемых электронных медицинских изделий, систем управления процессами, промышленного оборудования, автомобилей и систем управления железнодорожными перевозками с высоким уровнем безопасности.</span><span class="sxs-lookup"><span data-stu-id="38bce-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="38bce-214">Простота использования</span><span class="sxs-lookup"><span data-stu-id="38bce-214">Simple, easy-to-use</span></span>

<span data-ttu-id="38bce-215">Azure RTOS GUIX очень прост в использовании, а Azure RTOS GUIX Studio еще более упрощает работу в этой системе, так как позволяет разработчикам визуально проектировать на рабочем столе и генерировать код на языке C, который выполняется на фактическом целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="38bce-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="38bce-216">Затем приложения могут добавлять собственные пользовательские функции обработки событий и рисования для создания полнофункционального графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="38bce-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="38bce-217">Процедура применения API для Azure RTOS GUIX является очень простой.</span><span class="sxs-lookup"><span data-stu-id="38bce-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="38bce-218">Данный API интуитивно понятен и поддерживает много функций.</span><span class="sxs-lookup"><span data-stu-id="38bce-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="38bce-219">Названия API состоят из реальных слов, а не из набора букв и (или) сокращенных имен, которые так часто используются в других файловых системах.</span><span class="sxs-lookup"><span data-stu-id="38bce-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="38bce-220">Все API-интерфейсы для Azure RTOS GUIX имеют префикс *gx_* и соответствуют соглашению об именовании с использованием конструкции "существительное — глагол".</span><span class="sxs-lookup"><span data-stu-id="38bce-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="38bce-221">Более того, в рамках всего API обеспечивается функциональная согласованность.</span><span class="sxs-lookup"><span data-stu-id="38bce-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="38bce-222">Например, все API-интерфейсы, инициализирующие блок управления мини-приложением, называются &lt; widget_type&gt;_create, а параметры создания функции для каждого типа мини-приложения всегда определяются в одном и том же порядке.</span><span class="sxs-lookup"><span data-stu-id="38bce-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="38bce-223">Полный набор встроенных мини-приложений</span><span class="sxs-lookup"><span data-stu-id="38bce-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="38bce-224">Azure RTOS GUIX предоставляет широкий набор встроенных мини-приложений, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="38bce-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="38bce-225">Меню "гармошка"</span><span class="sxs-lookup"><span data-stu-id="38bce-225">Accordion Menu</span></span>

* <span data-ttu-id="38bce-226">Кнопка</span><span class="sxs-lookup"><span data-stu-id="38bce-226">Button</span></span>

* <span data-ttu-id="38bce-227">Флажок</span><span class="sxs-lookup"><span data-stu-id="38bce-227">Checkbox</span></span>

* <span data-ttu-id="38bce-228">Круговой датчик</span><span class="sxs-lookup"><span data-stu-id="38bce-228">Circular Gauge</span></span>

* <span data-ttu-id="38bce-229">Раскрывающийся список</span><span class="sxs-lookup"><span data-stu-id="38bce-229">Drop Down List</span></span>

* <span data-ttu-id="38bce-230">Горизонтальный список</span><span class="sxs-lookup"><span data-stu-id="38bce-230">Horizontal List</span></span>

* <span data-ttu-id="38bce-231">Окно с горизонтальной полосой прокрутки</span><span class="sxs-lookup"><span data-stu-id="38bce-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="38bce-232">Значок</span><span class="sxs-lookup"><span data-stu-id="38bce-232">Icon</span></span>

* <span data-ttu-id="38bce-233">Кнопка со значком</span><span class="sxs-lookup"><span data-stu-id="38bce-233">Icon Button</span></span>

* <span data-ttu-id="38bce-234">График</span><span class="sxs-lookup"><span data-stu-id="38bce-234">Line Chart</span></span>

* <span data-ttu-id="38bce-235">Меню</span><span class="sxs-lookup"><span data-stu-id="38bce-235">Menu</span></span>

* <span data-ttu-id="38bce-236">Кнопка с многострочным текстом</span><span class="sxs-lookup"><span data-stu-id="38bce-236">Multi Line Text Button</span></span>

* <span data-ttu-id="38bce-237">Ввод многострочного текста</span><span class="sxs-lookup"><span data-stu-id="38bce-237">Multi Line Text Input</span></span>

* <span data-ttu-id="38bce-238">Представление многострочного текста</span><span class="sxs-lookup"><span data-stu-id="38bce-238">Multi Line Text View</span></span>

* <span data-ttu-id="38bce-239">Числовой запрос карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="38bce-240">Числовой запрос</span><span class="sxs-lookup"><span data-stu-id="38bce-240">Numeric Prompt</span></span>

* <span data-ttu-id="38bce-241">Числовое колесо прокрутки</span><span class="sxs-lookup"><span data-stu-id="38bce-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="38bce-242">Кнопка карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-242">Pixelmap Button</span></span>

* <span data-ttu-id="38bce-243">Запрос карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="38bce-244">Ползунок карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-244">Pixelmap Slider</span></span>

* <span data-ttu-id="38bce-245">Спрайт карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="38bce-246">Progress Bar</span><span class="sxs-lookup"><span data-stu-id="38bce-246">Progress Bar</span></span>

* <span data-ttu-id="38bce-247">prompt</span><span class="sxs-lookup"><span data-stu-id="38bce-247">Prompt</span></span>

* <span data-ttu-id="38bce-248">Круговой индикатор выполнения</span><span class="sxs-lookup"><span data-stu-id="38bce-248">Radial Progress Bar</span></span>

* <span data-ttu-id="38bce-249">Radio Button</span><span class="sxs-lookup"><span data-stu-id="38bce-249">Radio Button</span></span>

* <span data-ttu-id="38bce-250">Колесо прокрутки</span><span class="sxs-lookup"><span data-stu-id="38bce-250">Scroll Wheel</span></span>

* <span data-ttu-id="38bce-251">Ввод однострочного текста</span><span class="sxs-lookup"><span data-stu-id="38bce-251">Single Line Text Input</span></span>

* <span data-ttu-id="38bce-252">Ползунок</span><span class="sxs-lookup"><span data-stu-id="38bce-252">Slider</span></span>

* <span data-ttu-id="38bce-253">Строковое колесо прокрутки</span><span class="sxs-lookup"><span data-stu-id="38bce-253">String Scroll Wheel</span></span>

* <span data-ttu-id="38bce-254">Кнопка "Текст"</span><span class="sxs-lookup"><span data-stu-id="38bce-254">Text Button</span></span>

* <span data-ttu-id="38bce-255">Вид дерева</span><span class="sxs-lookup"><span data-stu-id="38bce-255">Tree View</span></span>

* <span data-ttu-id="38bce-256">Вертикальный список</span><span class="sxs-lookup"><span data-stu-id="38bce-256">Vertical List</span></span>

* <span data-ttu-id="38bce-257">Вертикальная полоса прокрутки</span><span class="sxs-lookup"><span data-stu-id="38bce-257">Vertical Scrollbar</span></span>

<span data-ttu-id="38bce-258">Приложение также легко создает свои собственные мини-приложения клиента.</span><span class="sxs-lookup"><span data-stu-id="38bce-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="38bce-259">Полнофункциональный API для низкоуровневого рисования</span><span class="sxs-lookup"><span data-stu-id="38bce-259">Complete low-level drawing API</span></span>

<span data-ttu-id="38bce-260">Azure RTOS GUIX предоставляет надежный API для рисования на холсте, благодаря которому приложение может визуализировать сложные графические фигуры.</span><span class="sxs-lookup"><span data-stu-id="38bce-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="38bce-261">Все функции поддерживают сглаживание на целевых объектах с большой глубиной цвета, а все фигуры могут быть заполнены по контуру, включая сплошные заливки и узорные заливки с использованием карты отображения пикселей.</span><span class="sxs-lookup"><span data-stu-id="38bce-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="38bce-262">Все примитивы рисования поддерживают альфа-фактор кисти при работе с глубиной цвета 16 бит/пкс и больше.</span><span class="sxs-lookup"><span data-stu-id="38bce-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="38bce-263">Ниже перечислены функции рисования:</span><span class="sxs-lookup"><span data-stu-id="38bce-263">Drawing functions include:</span></span>

* <span data-ttu-id="38bce-264">Рисование дуги</span><span class="sxs-lookup"><span data-stu-id="38bce-264">Arc Draw</span></span>

* <span data-ttu-id="38bce-265">Рисование окружности</span><span class="sxs-lookup"><span data-stu-id="38bce-265">Circle Draw</span></span>

* <span data-ttu-id="38bce-266">Рисование линии</span><span class="sxs-lookup"><span data-stu-id="38bce-266">Line Draw</span></span>

* <span data-ttu-id="38bce-267">Рисование круговых диаграмм</span><span class="sxs-lookup"><span data-stu-id="38bce-267">Pie Draw</span></span>

* <span data-ttu-id="38bce-268">Смешение карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-268">Pixelmap Blend</span></span>

* <span data-ttu-id="38bce-269">Плитка карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-269">Pixelmap Tile</span></span>

* <span data-ttu-id="38bce-270">Рисование многоугольника</span><span class="sxs-lookup"><span data-stu-id="38bce-270">Polygon Draw</span></span>

* <span data-ttu-id="38bce-271">Рисование текста</span><span class="sxs-lookup"><span data-stu-id="38bce-271">Text Draw</span></span>

* <span data-ttu-id="38bce-272">Рисование аккорда</span><span class="sxs-lookup"><span data-stu-id="38bce-272">Chord Draw</span></span>

* <span data-ttu-id="38bce-273">Рисование эллипса</span><span class="sxs-lookup"><span data-stu-id="38bce-273">Ellipse Draw</span></span>

* <span data-ttu-id="38bce-274">Рисование пикселя</span><span class="sxs-lookup"><span data-stu-id="38bce-274">Pixel Draw</span></span>

* <span data-ttu-id="38bce-275">Рисование карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-275">Pixelmap Draw</span></span>

* <span data-ttu-id="38bce-276">Вращение карты отображения пикселей</span><span class="sxs-lookup"><span data-stu-id="38bce-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="38bce-277">Рисование прямоугольника</span><span class="sxs-lookup"><span data-stu-id="38bce-277">Rectangle Draw</span></span>

* <span data-ttu-id="38bce-278">Смешение текста</span><span class="sxs-lookup"><span data-stu-id="38bce-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="38bce-279">Бесплатные шрифты по умолчанию и простое добавление шрифтов</span><span class="sxs-lookup"><span data-stu-id="38bce-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="38bce-280">Azure RTOS GUIX предоставляет бесплатный набор шрифтов TrueType.</span><span class="sxs-lookup"><span data-stu-id="38bce-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="38bce-281">При необходимости разработчики могут добавлять дополнительные шрифты TrueType.</span><span class="sxs-lookup"><span data-stu-id="38bce-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="38bce-282">Формат шрифтов в Azure RTOS GUIX поддерживает шрифты со сглаживанием 8 бит/пкс, шрифты со сглаживанием 4 бит/пкс и монохромные шрифты 1 бит/пкс.</span><span class="sxs-lookup"><span data-stu-id="38bce-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="38bce-283">Для большинства приложений, для которых существуют ограничения по ресурсам, Azure RTOS GUIX выполняет предварительную обработку шрифтов TrueType, чтобы получить сжатый растровый формат, с помощью нашего классического средства GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="38bce-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="38bce-284">Реализация пользовательского декодера JPG и PNG</span><span class="sxs-lookup"><span data-stu-id="38bce-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="38bce-285">Реализация пользовательского декодера JPG и PNG.</span><span class="sxs-lookup"><span data-stu-id="38bce-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="38bce-286">Эта реализация поддерживает преобразование цветового пространства, сглаживание и создание в среде выполнения изображений в формате карты отображения пикселей, совместимых с Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="38bce-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="38bce-287">Расширенная поддержка дисплеев и сенсорных экранов</span><span class="sxs-lookup"><span data-stu-id="38bce-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="38bce-288">Azure RTOS GUIX предоставляет универсальные драйверы дисплея практически для любых форматов цвета, включая монохромный 1 бит/пкс, палитру 8 бит/пкс, формат 8 бит/пкс 3:3:2,</span><span class="sxs-lookup"><span data-stu-id="38bce-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="38bce-289">16 бит/пкс 565 rgb, 16 бит/пкс 4:4:4:4, 32 бит/пкс x:r:g:b и 32 бит/пкс a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="38bce-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="38bce-290">Кроме того, Azure RTOS GUIX интегрируется с различными наиболее популярными ЖК-контроллерами и аппаратными ускорителями (ST ChromeArt, Renesas Synergy и т. д.).</span><span class="sxs-lookup"><span data-stu-id="38bce-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="38bce-291">Azure RTOS GUIX полностью поддерживает сенсорные экраны (включая поддержку жестов), перья и виртуальные устройства ввода с клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="38bce-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="38bce-292">Классическое средство WYSIWYG в Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="38bce-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="38bce-293">Azure RTOS GUIX Studio предоставляет законченную среду разработки экранов WYSIWYG, которая позволяет пользователю перетаскивать графические элементы, используемые для построения экранов графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="38bce-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="38bce-294">Azure RTOS GUIX Studio автоматически генерирует код на языке C, совместимый с библиотекой Azure RTOS GUIX, который готов к компиляции и выполнению на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="38bce-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="38bce-295">С помощью интегрированного средства создания шрифтов в Azure RTOS GUIX Studio разработчики могут создавать предварительно подготовленные для просмотра шрифты для использования в приложении.</span><span class="sxs-lookup"><span data-stu-id="38bce-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="38bce-296">Шрифты могут генерироваться в виде монохромного формата или формата со сглаживанием и оптимизируются для экономии места на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="38bce-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="38bce-297">Шрифты могут включать в себя любой набор символов, в том числе символы Юникода для многоязычных приложений.</span><span class="sxs-lookup"><span data-stu-id="38bce-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="38bce-298">Azure RTOS GUIX Studio упрощает импорт графики из файлов PNG или JPG с преобразованием в сжатые карты отображения пикселей Azure RTOS GUIX для использования в целевой системе.</span><span class="sxs-lookup"><span data-stu-id="38bce-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="38bce-299">Мини-приложения Azure RTOS GUIX различного типа позволяют встраивать пользовательскую графику для создания внешнего вида, удобного пользователю.</span><span class="sxs-lookup"><span data-stu-id="38bce-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="38bce-300">Кроме того, Azure RTOS GUIX Studio позволяет настраивать цвета и стили рисования по умолчанию, используемые мини-приложениями Azure RTOS GUIX, благодаря чему разработчики могут легко настраивать внешний вид интерфейса Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="38bce-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="38bce-301">Azure RTOS GUIX Studio также позволяет генерировать и поддерживать строки приложения, используя специальную встроенную функцию.</span><span class="sxs-lookup"><span data-stu-id="38bce-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="38bce-302">Благодаря этому разработчики могут проектировать приложения с помощью одного языка для разработки, а также быстро и удобно добавлять поддержку для дополнительных языков после выпуска продукта.</span><span class="sxs-lookup"><span data-stu-id="38bce-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="38bce-303">Законченное приложение Azure RTOS GUIX может выполняться на рабочем столе компьютера в среде Azure RTOS GUIX Studio, что позволяет быстро и легко генерировать и демонстрировать концепции графического пользовательского интерфейса, тестировать потоки экрана, а также наблюдать за переходами экрана и анимацией на экране.</span><span class="sxs-lookup"><span data-stu-id="38bce-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="38bce-304">По завершении проект можно экспортировать в виде готовых к работе на целевом объекте структур данных на языке C, которые готовы к компиляции и связаны с библиотеками Azure RTOS GUIX и Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="38bce-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="38bce-305">Azure RTOS GUIX и Azure RTOS GUIX Studio поддерживают различные темы ресурсов, что позволяет легко изменять внешний вид приложения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="38bce-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="38bce-306">Шрифты, цвета и карты отображения пикселей можно изменять во время выполнения с помощью одного простого API.</span><span class="sxs-lookup"><span data-stu-id="38bce-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="38bce-307">Дополнительные сведения о GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="38bce-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="38bce-308">Полнофункциональная имитация Win32</span><span class="sxs-lookup"><span data-stu-id="38bce-308">Complete Win32 simulation</span></span>

<span data-ttu-id="38bce-309">Azure RTOS GUIX работает на компьютере под управлением Windows, используя точно такую же библиотеку, которая выполняется на целевой плате.</span><span class="sxs-lookup"><span data-stu-id="38bce-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="38bce-310">Благодаря применению Azure RTOS GUIX можно создавать и запускать приложение графического пользовательского интерфейса на ПК и использовать тот же код приложения на целевом объекте для отладки, быстрого создания прототипа, демонстрации и проверки заданного режима работы в режиме WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="38bce-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="38bce-311">Усовершенствованные технологии</span><span class="sxs-lookup"><span data-stu-id="38bce-311">Advanced technology</span></span>

* <span data-ttu-id="38bce-312">В Azure RTOS GUIX применяются следующие усовершенствованные технологии:</span><span class="sxs-lookup"><span data-stu-id="38bce-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="38bce-313">Альфа-смешение</span><span class="sxs-lookup"><span data-stu-id="38bce-313">Alpha blending</span></span>

* <span data-ttu-id="38bce-314">Сглаживание</span><span class="sxs-lookup"><span data-stu-id="38bce-314">Anti-Aliasing</span></span>

* <span data-ttu-id="38bce-315">Автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="38bce-315">Automatic scaling</span></span>

* <span data-ttu-id="38bce-316">Сжатие растрового изображения</span><span class="sxs-lookup"><span data-stu-id="38bce-316">Bitmap compression</span></span>

* <span data-ttu-id="38bce-317">Смешение на холсте</span><span class="sxs-lookup"><span data-stu-id="38bce-317">Canvas blending</span></span>

* <span data-ttu-id="38bce-318">Поддержка пользовательских мини-приложений</span><span class="sxs-lookup"><span data-stu-id="38bce-318">Custom widget support</span></span>

* <span data-ttu-id="38bce-319">Поддержка отложенного рисования</span><span class="sxs-lookup"><span data-stu-id="38bce-319">Deferred drawing support</span></span>

* <span data-ttu-id="38bce-320">Поддержка сглаживания</span><span class="sxs-lookup"><span data-stu-id="38bce-320">Dithering support</span></span>

* <span data-ttu-id="38bce-321">Программирование, независимое от порядка байтов</span><span class="sxs-lookup"><span data-stu-id="38bce-321">Endian neutral programming</span></span>

* <span data-ttu-id="38bce-322">Поддержка аппаратного ускорителя</span><span class="sxs-lookup"><span data-stu-id="38bce-322">Hardware accelerator support</span></span>

* <span data-ttu-id="38bce-323">Многоязычная поддержка и кодировка UTF-8</span><span class="sxs-lookup"><span data-stu-id="38bce-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="38bce-324">Поддержка нескольких дисплеев и холстов</span><span class="sxs-lookup"><span data-stu-id="38bce-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="38bce-325">Оптимизированные усечение, рисование и обработка событий</span><span class="sxs-lookup"><span data-stu-id="38bce-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="38bce-326">Декодер JPEG и PNG в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="38bce-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="38bce-327">Создание обложек и темы</span><span class="sxs-lookup"><span data-stu-id="38bce-327">Skinning and Themes</span></span>

* <span data-ttu-id="38bce-328">Поддержка различных форматов: монохромный, 32-разрядный True Color с форматами Alpha Graphics</span><span class="sxs-lookup"><span data-stu-id="38bce-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="38bce-329">Переходы, спрайты и поддержка анимации</span><span class="sxs-lookup"><span data-stu-id="38bce-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="38bce-330">Имитация Win32</span><span class="sxs-lookup"><span data-stu-id="38bce-330">Win32 simulation</span></span>

* <span data-ttu-id="38bce-331">Управление окнами, включая окна просмотра и поддержка Z-порядка</span><span class="sxs-lookup"><span data-stu-id="38bce-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="38bce-332">Минимальное время выхода на рынок</span><span class="sxs-lookup"><span data-stu-id="38bce-332">Fastest time-to-market</span></span>

<span data-ttu-id="38bce-333">Azure RTOS GUIX легко устанавливать, изучать, использовать, отлаживать, проверять, сертифицировать и обслуживать.</span><span class="sxs-lookup"><span data-stu-id="38bce-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="38bce-334">Azure RTOS GUIX Studio также позволяет упростить проектирование и реализацию встроенного графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="38bce-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="38bce-335">В результате Azure RTOS GUIX является одним из наиболее популярных решений графического пользовательского интерфейса для внедренных устройств Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="38bce-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="38bce-336">Наши возможности по стабильно малому времени выхода на рынок основаны на следующих факторах:</span><span class="sxs-lookup"><span data-stu-id="38bce-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="38bce-337">документация высокого качества — ознакомьтесь с нашим [руководством пользователя по Azure RTOS GUIX](about-guix.md) и убедитесь в этом сами;</span><span class="sxs-lookup"><span data-stu-id="38bce-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="38bce-338">полная доступность исходного кода;</span><span class="sxs-lookup"><span data-stu-id="38bce-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="38bce-339">простые в использовании API-интерфейсы;</span><span class="sxs-lookup"><span data-stu-id="38bce-339">Easy-to-use API</span></span>

* <span data-ttu-id="38bce-340">комплексный и широкий набор функций.</span><span class="sxs-lookup"><span data-stu-id="38bce-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="38bce-341">Одна простая лицензия</span><span class="sxs-lookup"><span data-stu-id="38bce-341">One Simple License</span></span>

<span data-ttu-id="38bce-342">Использование и тестирование исходного кода не требуют каких-либо затрат, как и производственные лицензии при развертывании на предварительно лицензированных устройствах. Для всех других устройств требуется лишь простая лицензия сроком на один год.</span><span class="sxs-lookup"><span data-stu-id="38bce-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="38bce-343">Полный и высококачественный исходный код</span><span class="sxs-lookup"><span data-stu-id="38bce-343">Full, highest-quality source code</span></span>

<span data-ttu-id="38bce-344">Уже несколько лет Azure RTOS NetX задает стандарт качества и простоты понимания.</span><span class="sxs-lookup"><span data-stu-id="38bce-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="38bce-345">Кроме того, соглашение по применению отдельного файла для каждой функции упрощает навигацию по исходному коду.</span><span class="sxs-lookup"><span data-stu-id="38bce-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="38bce-346">Поддержка большинства популярных архитектур</span><span class="sxs-lookup"><span data-stu-id="38bce-346">Supports most popular architectures</span></span>

<span data-ttu-id="38bce-347">Azure RTOS GUIX работает на большинстве популярных 32/64-разрядных микропроцессоров. Она не требует дополнительной настройки, полностью протестирована и поддерживается на разных архитектурах, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="38bce-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="38bce-348">Усовершенствованные архитектуры:</span><span class="sxs-lookup"><span data-stu-id="38bce-348">Advanced Architectures:</span></span>

<span data-ttu-id="38bce-349">**Analog Devices**: SHARC, Blackfin, CM4xx;</span><span class="sxs-lookup"><span data-stu-id="38bce-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="38bce-350">**Andes Core**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="38bce-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="38bce-351">**Ambiqmicro**: микроконтроллеры Apollo;</span><span class="sxs-lookup"><span data-stu-id="38bce-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="38bce-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M;</span><span class="sxs-lookup"><span data-stu-id="38bce-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="38bce-353">**Cadence**: Xtensa, Diamond;</span><span class="sxs-lookup"><span data-stu-id="38bce-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="38bce-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi;</span><span class="sxs-lookup"><span data-stu-id="38bce-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="38bce-355">**Cypress**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="38bce-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="38bce-356">**EnSilica**: eSi-RISC;</span><span class="sxs-lookup"><span data-stu-id="38bce-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="38bce-357">**Infineon**: XMC1000, XMC4000, TriCore;</span><span class="sxs-lookup"><span data-stu-id="38bce-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="38bce-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10;</span><span class="sxs-lookup"><span data-stu-id="38bce-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="38bce-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32;</span><span class="sxs-lookup"><span data-stu-id="38bce-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="38bce-360">**Microsemi**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="38bce-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="38bce-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4;</span><span class="sxs-lookup"><span data-stu-id="38bce-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="38bce-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy;</span><span class="sxs-lookup"><span data-stu-id="38bce-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="38bce-363">**Silicon Labs**: EFM32;</span><span class="sxs-lookup"><span data-stu-id="38bce-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="38bce-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS;</span><span class="sxs-lookup"><span data-stu-id="38bce-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="38bce-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7;</span><span class="sxs-lookup"><span data-stu-id="38bce-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="38bce-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C;</span><span class="sxs-lookup"><span data-stu-id="38bce-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="38bce-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class;</span><span class="sxs-lookup"><span data-stu-id="38bce-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="38bce-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE.</span><span class="sxs-lookup"><span data-stu-id="38bce-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
