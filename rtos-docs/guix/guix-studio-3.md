---
title: Описание GUIX Studio
description: В этой главе приведено описание инструмента анализа систем GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814967"
---
# <a name="chapter-3-description-of-guix-studio"></a><span data-ttu-id="0405a-103">Глава 3. Описание инструмента GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-103">Chapter 3: Description of GUIX Studio</span></span>

<span data-ttu-id="0405a-104">В этой главе приведено описание инструмента анализа систем GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-104">This chapter contains a description of the GUIX Studio system analysis tool.</span></span> <span data-ttu-id="0405a-105">В этой главе приведено описание основных функций графического пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0405a-105">A description of the overall functionality of the GUI is found in this chapter.</span></span> 

## <a name="guix-studio-views"></a><span data-ttu-id="0405a-106">Представления GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-106">GUIX Studio Views</span></span>

<span data-ttu-id="0405a-107">Существует пять основных областей пользовательского интерфейса GUIX Studio, а именно: \***панель инструментов**, _\*_представление проекта_\*_, представление _\*_свойств_\*_, _\*_целевое представление_\*_ и _\*_представление ресурсов_\*_ .</span><span class="sxs-lookup"><span data-stu-id="0405a-107">There are five principal areas of the GUIX Studio UI, namely the ***Toolbar** _, _*_Project View_*_, _*_Properties View_*_, _*_Target View_*_, and _*_Resource View_\*_.</span></span> <span data-ttu-id="0405a-108">_ *_Рис. 2_*\* содержит базовый пользовательский интерфейс GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-108">_ *_Figure 2_*\* shows the basic GUIX Studio UI.</span></span> <span data-ttu-id="0405a-109">Каждое из представлений более подробно рассматривается в соответствующих подразделах.</span><span class="sxs-lookup"><span data-stu-id="0405a-109">Each of the views is further discussed in the following sub-sections.</span></span>

![Снимок экрана: графический интерфейс GUIX Studio.](./media/guix-studio/image_10.png)

<span data-ttu-id="0405a-111">**Рис. 2**</span><span class="sxs-lookup"><span data-stu-id="0405a-111">**Figure 2**</span></span>

### <a name="title"></a><span data-ttu-id="0405a-112">Заголовок</span><span class="sxs-lookup"><span data-stu-id="0405a-112">Title</span></span>

- <span data-ttu-id="0405a-113">GUIX Studio 18: В ***заголовке** _ указывается версия GUIX Studio и открытый проект (см. в верхней части _ *_рис. 2_** выше).</span><span class="sxs-lookup"><span data-stu-id="0405a-113">GUIX Studio 18: The ***Title** _ displays the GUIX Studio version as well as the currently open project, as shown at the top of _ *_Figure 2_** previously.</span></span>

### <a name="toolbar"></a><span data-ttu-id="0405a-114">Панель инструментов</span><span class="sxs-lookup"><span data-stu-id="0405a-114">Toolbar</span></span>

<span data-ttu-id="0405a-115">На **панели инструментов** _ отображаются кнопки, доступные разработчику GUIX Studio (см. _\*_рис. 3_\*\*).</span><span class="sxs-lookup"><span data-stu-id="0405a-115">The ***Toolbar** _ shows the buttons available to the GUIX Studio developer, as shown in _*_Figure 3_\*\*.</span></span>

![Снимок экрана: панель инструментов GUIX Studio.](./media/guix-studio/image11.jpg)

<span data-ttu-id="0405a-117">**Рис. 3**</span><span class="sxs-lookup"><span data-stu-id="0405a-117">**Figure 3**</span></span>

<span data-ttu-id="0405a-118">Назначение кнопок на панели инструментов приведено далее:</span><span class="sxs-lookup"><span data-stu-id="0405a-118">The toolbar buttons are defined as follows:</span></span>

![Кнопка «Создать»](./media/guix-studio/new-button.png) <span data-ttu-id="0405a-120">Создание нового проекта GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-120">Creates a new GUIX Studio project</span></span>

![Кнопка "Открыть"](./media/guix-studio/open-button.png) <span data-ttu-id="0405a-122">Открытие существующего проекта GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-122">Opens an existing GUIX Studio project</span></span>

![Кнопка "Сохранить"](./media/guix-studio/save-button.png) <span data-ttu-id="0405a-124">Сохранение проекта</span><span class="sxs-lookup"><span data-stu-id="0405a-124">Saves the project</span></span>

![Кнопка "Вырезать"](./media/guix-studio/cut-button.png) <span data-ttu-id="0405a-126">Вырезание выбранного мини-приложения, включая дочерние объекты</span><span class="sxs-lookup"><span data-stu-id="0405a-126">Cut widget selected, including children</span></span>

![Кнопка "Копировать"](./media/guix-studio/copy-button.png) <span data-ttu-id="0405a-128">Копирование выбранного мини-приложения, включая дочерние объекты</span><span class="sxs-lookup"><span data-stu-id="0405a-128">Copy selected widget, including children</span></span>

![Кнопка "Вставить"](./media/guix-studio/paste-button.png) <span data-ttu-id="0405a-130">Вставка мини-приложения и дочерних объектов</span><span class="sxs-lookup"><span data-stu-id="0405a-130">Paste widget and children</span></span>

![Кнопка "Выровнять по левому краю"](./media/guix-studio/left-align-button.png) <span data-ttu-id="0405a-132">Выравнивание выбранных мини-приложений по левому краю</span><span class="sxs-lookup"><span data-stu-id="0405a-132">Left-align selected widgets</span></span>

![Кнопка "Выровнять по правому краю"](./media/guix-studio/right-align-button.png) <span data-ttu-id="0405a-134">Выравнивание выбранных мини-приложений по правому краю</span><span class="sxs-lookup"><span data-stu-id="0405a-134">Right-align selected widgets</span></span>

![Кнопка "Выровнять по верхнему краю"](./media/guix-studio/top-align-button.png) <span data-ttu-id="0405a-136">Выравнивание выбранных мини-приложений по верхнему краю</span><span class="sxs-lookup"><span data-stu-id="0405a-136">Top-align selected widgets</span></span>

![Кнопка "Выровнять по нижнему краю"](./media/guix-studio/bottom-align-button.png) <span data-ttu-id="0405a-138">Выравнивание выбранных мини-приложений по нижнему краю</span><span class="sxs-lookup"><span data-stu-id="0405a-138">Bottom-align selected widgets</span></span>

![Кнопка "Распределение по вертикали"](./media/guix-studio/space-vertically-button.png) <span data-ttu-id="0405a-140">Расположение выбранных мини-приложений по вертикали с равными промежутками</span><span class="sxs-lookup"><span data-stu-id="0405a-140">Equally space selected widgets vertically</span></span>

![Кнопка "Распределение по горизонтали"](./media/guix-studio/space-horizontally-button.png) <span data-ttu-id="0405a-142">Расположение выбранных мини-приложений по горизонтали с равными промежутками</span><span class="sxs-lookup"><span data-stu-id="0405a-142">Equally space selected widgets horizontally</span></span>

![Кнопка "Равная ширина"](./media/guix-studio/equal-width-button.png) <span data-ttu-id="0405a-144">Выравнивание ширины выбранных мини-приложений</span><span class="sxs-lookup"><span data-stu-id="0405a-144">Make selected widgets equal width</span></span>

![Кнопка "Равная высота"](./media/guix-studio/equal-height-button.png) <span data-ttu-id="0405a-146">Выравнивание высоты выбранных мини-приложений</span><span class="sxs-lookup"><span data-stu-id="0405a-146">Make selected widgets equal height</span></span>

![Кнопка "Переместить вперед"](./media/guix-studio/move-front-button.png) <span data-ttu-id="0405a-148">Перемещение выбранных мини-приложений вперед</span><span class="sxs-lookup"><span data-stu-id="0405a-148">Move selected widgets to front</span></span>

![Кнопка "Переместить назад"](./media/guix-studio/move-back-button.png) <span data-ttu-id="0405a-150">Перемещение выбранных мини-приложений назад</span><span class="sxs-lookup"><span data-stu-id="0405a-150">Move selected widgets to back</span></span>

![Кнопка "Размер"](./media/guix-studio/size-button.png) <span data-ttu-id="0405a-152">Подгонка размера выбранного мини-приложения под уменьшенный целевой экран содержимого</span><span class="sxs-lookup"><span data-stu-id="0405a-152">Size selected widget to content Zoom out target screen</span></span>

![Кнопка "Уменьшить"](./media/guix-studio/zoom-out-button.png) <span data-ttu-id="0405a-154">Уменьшение целевого экрана</span><span class="sxs-lookup"><span data-stu-id="0405a-154">Zoom out target screen</span></span>

![Кнопка "Увеличить"](./media/guix-studio/zoom-in-button.png) <span data-ttu-id="0405a-156">Увеличение целевого экрана</span><span class="sxs-lookup"><span data-stu-id="0405a-156">Zoom in target screen</span></span>

![Кнопка "Запись"](./media/guix-studio/record-button.png) <span data-ttu-id="0405a-158">Запись макроса</span><span class="sxs-lookup"><span data-stu-id="0405a-158">Record Macro</span></span>

![Кнопка "Воспроизвести"](./media/guix-studio/playback-button.png) <span data-ttu-id="0405a-160">Воспроизведение макроса</span><span class="sxs-lookup"><span data-stu-id="0405a-160">Playback Macro</span></span>

![Кнопка "Запустить"](./media/guix-studio/run-button.png) <span data-ttu-id="0405a-162">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="0405a-162">Run Application</span></span>

![Кнопка "О приложении"](./media/guix-studio/about-button.png) <span data-ttu-id="0405a-164">Сведения о GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-164">About GUIX Studio</span></span>

### <a name="project-view"></a><span data-ttu-id="0405a-165">представление проекта</span><span class="sxs-lookup"><span data-stu-id="0405a-165">Project View</span></span>

<span data-ttu-id="0405a-166">\***Представление проекта** _ содержит иерархический список объектов GUIX, из которых состоит встроенный пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0405a-166">The \***Project View** _ shows the hierarchical list GUIX objects that comprise the embedded UI.</span></span> <span data-ttu-id="0405a-167">Новые объекты GUIX можно добавить, щелкнув родительский объект, а затем выбрав объект в меню _\*_Вставка_\*_ (или щелкнув правой кнопкой мыши объект и выбрав пункт из контекстного меню).</span><span class="sxs-lookup"><span data-stu-id="0405a-167">New GUIX objects can be added by clicking on the parent object and then selecting an object from the _*_Insert_*_ menu (or by right-clicking on the object and selecting from the right-click menu).</span></span> <span data-ttu-id="0405a-168">На _\*_рис. 4_*_ ниже показано *_представление проекта_** GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-168">_*_Figure 4_*_ below shows the GUIX Studio _\*_Project View_\*\*.</span></span>

![Снимок экрана: представление проекта в GUIX Studio.](./media/guix-studio/image_35.png)

<span data-ttu-id="0405a-170">**Рис. 4**</span><span class="sxs-lookup"><span data-stu-id="0405a-170">**Figure 4**</span></span>

### <a name="properties-view"></a><span data-ttu-id="0405a-171">Представление свойств</span><span class="sxs-lookup"><span data-stu-id="0405a-171">Properties View</span></span>

<span data-ttu-id="0405a-172">В ***представлении свойств** _ отображаются подробные сведения о свойствах выбранного объекта GUIX, который можно выбрать в _*_представлении проекта_*_ или щелкнув непосредственно на объекте в _*_целевом представлении_\*_.</span><span class="sxs-lookup"><span data-stu-id="0405a-172">The ***Properties View** _ shows detailed property information of the currently selected GUIX object, which can be selected via the _*_Project View_*_ or by clicking directly on the object in the _*_Target View_\*_.</span></span> <span data-ttu-id="0405a-173">На _\*_рис. 5_*_ ниже показано _*_представление свойств_\*\* GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-173">_*_Figure 5_*_ below shows the GUIX Studio _\*_Properties View_\*\*.</span></span>

![Снимок экрана: представление свойств GUIX Studio.](./media/guix-studio/image36.jpg)

<span data-ttu-id="0405a-175">**Рис. 5**</span><span class="sxs-lookup"><span data-stu-id="0405a-175">**Figure 5**</span></span>

### <a name="target-view"></a><span data-ttu-id="0405a-176">Целевое представление</span><span class="sxs-lookup"><span data-stu-id="0405a-176">Target View</span></span>

<span data-ttu-id="0405a-177">\***Целевое представление** _ — это область конструирования и макета экрана WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="0405a-177">The \***Target View** _ is the WYSIWYG screen design and layout area.</span></span> <span data-ttu-id="0405a-178">Это представление предназначено для представления физического экрана или экранов, доступных на целевом оборудовании.</span><span class="sxs-lookup"><span data-stu-id="0405a-178">This view is meant to represent the physical display or displays available on your target hardware.</span></span> <span data-ttu-id="0405a-179">Объекты можно выбирать, перемещать, изменять их размер и т. д. с помощью простых операций мыши.</span><span class="sxs-lookup"><span data-stu-id="0405a-179">Objects can be selected, moved, resized, etc. via simple mouse operations.</span></span> <span data-ttu-id="0405a-180">Кроме того, для выбранных объектов в целевом представлении доступны операции выравнивания и порядка наложения в виде кнопок.</span><span class="sxs-lookup"><span data-stu-id="0405a-180">In addition, alignment and Z-order button operations are available on selected objects in the Target View.</span></span> <span data-ttu-id="0405a-181">Выбор объекта в _\*_целевом представлении_\*_ также приведет к отображению свойств этого объекта в _\*_представлении свойств_\*_.</span><span class="sxs-lookup"><span data-stu-id="0405a-181">Selecting an object in the _*_Target View_*_ will also result in the properties for that object to be displayed in the _*_Properties View_*_.</span></span> <span data-ttu-id="0405a-182">На _\*_рис. 6_*_ ниже показано _*_целевое представление_\*\* GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-182">_*_Figure 6_*_ below shows the GUIX Studio _\*_Target View_\*\*.</span></span>

![Снимок экрана: целевое представление GUIX Studio.](./media/guix-studio/image_37.png)

<span data-ttu-id="0405a-184">**Рис. 6**</span><span class="sxs-lookup"><span data-stu-id="0405a-184">**Figure 6**</span></span>

### <a name="resource-view"></a><span data-ttu-id="0405a-185">Ресурсы</span><span class="sxs-lookup"><span data-stu-id="0405a-185">Resource View</span></span>

<span data-ttu-id="0405a-186">\***Представление ресурсов** _ используется для управления ресурсами (цветами, шрифтами, картами отображения пикселей и строками), доступными на экранах приложений, заданных для каждого дисплея.</span><span class="sxs-lookup"><span data-stu-id="0405a-186">The \***Resource View** _ is used to manage the resources (colors, fonts, pixelmaps, and strings) available to applications screens defined for each display.</span></span> <span data-ttu-id="0405a-187">Можно щелкнуть заголовок группы представления ресурсов, чтобы развернуть каждую группу и изучить ее содержимое.</span><span class="sxs-lookup"><span data-stu-id="0405a-187">You can click on the resource view group headers to expand each group and examine the group contents.</span></span> <span data-ttu-id="0405a-188">На _\*_рис. 7_*_ ниже показано _*_представление ресурсов_\*\* GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-188">_*_Figure 7_*_ below shows the GUIX Studio _\*_Resource View_\*\*.</span></span>

![Снимок экрана: представление ресурсов GUIX Studio.](./media/guix-studio/image38.jpg)

<span data-ttu-id="0405a-190">**Рис. 7**</span><span class="sxs-lookup"><span data-stu-id="0405a-190">**Figure 7**</span></span>

<span data-ttu-id="0405a-191">Заголовок групп ресурсов указывает текущее имя темы.</span><span class="sxs-lookup"><span data-stu-id="0405a-191">The title of the resource groups indicates current theme name.</span></span> <span data-ttu-id="0405a-192">Если доступны несколько тем, вы можете переключаться между ними, щелкая стрелку вверх и вниз.</span><span class="sxs-lookup"><span data-stu-id="0405a-192">If multi themes available, you are able to switch between themes by clicking on the up and down arrow.</span></span>

<span data-ttu-id="0405a-193">Каждую группу ресурсов в представлении, показанном выше, можно развернуть или свернуть, щелкнув заголовок группы.</span><span class="sxs-lookup"><span data-stu-id="0405a-193">Each resource group in the view above can be expanded or collapsed by clicking on the group header.</span></span> <span data-ttu-id="0405a-194">Более подробное описание каждой группы ресурсов приведено в следующей главе.</span><span class="sxs-lookup"><span data-stu-id="0405a-194">A more detailed description of each resource groups follows in the next chapter.</span></span>

## <a name="the-guix-studio-project"></a><span data-ttu-id="0405a-195">Проект GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-195">The GUIX Studio Project</span></span>

<span data-ttu-id="0405a-196">Проект GUIX Studio содержит сведения о дизайне экрана пользовательского интерфейса и его ресурсах.</span><span class="sxs-lookup"><span data-stu-id="0405a-196">A GUIX Studio project maintains information about your UI screen design and UI resources.</span></span> <span data-ttu-id="0405a-197">Данные проекта сохраняются в XML-файле с расширением .***gxp***.</span><span class="sxs-lookup"><span data-stu-id="0405a-197">The project data is saved to an XML format file with the extension ".***gxp***".</span></span> <span data-ttu-id="0405a-198">Поскольку файл проекта представляет собой схему XML, ему можно присваивать версии и, таким образом, им можно управлять и его можно совместно использовать так же, как любой другой исходный файл.</span><span class="sxs-lookup"><span data-stu-id="0405a-198">Since the project file is an XML schema file, it can be versioned controlled and shared similar to any other source file.</span></span>

<span data-ttu-id="0405a-199">При первом запуске в GUIX Studio необходимо открыть один из образцов проекта, имеющихся в дистрибутиве, или создать новый проект.</span><span class="sxs-lookup"><span data-stu-id="0405a-199">When you first start using GUIX Studio, you will need to either open one of the example projects provided with the distribution or create a new project.</span></span> <span data-ttu-id="0405a-200">Вся работа сохраняется в файле данных проекта.</span><span class="sxs-lookup"><span data-stu-id="0405a-200">All of your work is saved to the project data file.</span></span>

<span data-ttu-id="0405a-201">GUIX Studio также создает исходные файлы ANSI C.</span><span class="sxs-lookup"><span data-stu-id="0405a-201">GUIX Studio also produces ANSI C source files.</span></span> <span data-ttu-id="0405a-202">Эти исходные файлы содержат ресурсы приложения или структуры данных, описывающие разрабатываемые экраны.</span><span class="sxs-lookup"><span data-stu-id="0405a-202">These source files contain either your application resources or data structures describing your designed screens.</span></span> <span data-ttu-id="0405a-203">GUIX Studio также записывает в эти созданные исходные файлы функции API, которые используют созданные структуры данных для динамического создания экранов приложения.</span><span class="sxs-lookup"><span data-stu-id="0405a-203">GUIX Studio also writes to these generated source files API functions that know to utilize the generated data structures to dynamically create your application screens.</span></span> <span data-ttu-id="0405a-204">Программное обеспечение приложения будет просто вызывать имеющиеся функции API для создания экранов, разработанных в GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-204">Your application software will simply invoke the provided API functions to create the screens you have designed within GUIX Studio.</span></span>

<span data-ttu-id="0405a-205">В ходе разработки пользовательского интерфейса инструмент GUIX Studio можно использовать для периодического создания выходных файлов, совместимых с GUIX, с помощью которых можно собирать и запускать разработанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="0405a-205">As you progress in designing your user interface, you will periodically want to use GUIX Studio to generate the GUIX compatible output files that will allow you to build and run the interface you have designed.</span></span> <span data-ttu-id="0405a-206">Вы можете компилировать и запускать созданные исходные файлы на целевом оборудовании или на настольном ПК с ОС Windows, который имитирует ThreadX и GUIX.</span><span class="sxs-lookup"><span data-stu-id="0405a-206">You can compile and run the generated source files for either your target hardware or on your Windows desktop that simulates ThreadX and GUIX.</span></span>

## <a name="guix-studio-project-organization"></a><span data-ttu-id="0405a-207">Организация проекта в GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="0405a-207">GUIX Studio Project Organization</span></span>

<span data-ttu-id="0405a-208">Некоторые знания о базовой организации проекта в GUIX Studio помогут понять, как можно эффективно использовать GUIX Studio, и применять информацию, имеющуюся в представлении проекта в интегрированной среде разработки GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="0405a-208">It is helpful to have some knowledge of the basic organization of a GUIX Studio project to understand how to use GUIX Studio effectively and to understand the information presented in the Project View of the GUIX Studio IDE.</span></span> <span data-ttu-id="0405a-209">Представление проекта представляет собой сводное визуальное представление всей информации, содержащейся в проекте.</span><span class="sxs-lookup"><span data-stu-id="0405a-209">The Project View is a summary visual representation of all of the information contained in your project.</span></span>

<span data-ttu-id="0405a-210">Переходя к описанию проекта, необходимо дать несколько определений.</span><span class="sxs-lookup"><span data-stu-id="0405a-210">Before describing the project, it is necessary to define few terms.</span></span> <span data-ttu-id="0405a-211">Во-первых, мы используем термин «**дисплей**» для обозначения физического устройства отображения.</span><span class="sxs-lookup"><span data-stu-id="0405a-211">First, we use the term **Display** to mean a physical display device.</span></span> <span data-ttu-id="0405a-212">Чаще всего это ЖК-дисплей, но он может работать на основе других технологий.</span><span class="sxs-lookup"><span data-stu-id="0405a-212">This is most often an LCD display device but it could be using other technology.</span></span> <span data-ttu-id="0405a-213">Следующий термин — «**экран**», означающий объект GUIX верхнего уровня, обычно это окно GUIX и все связанные с ним дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="0405a-213">The next term is **Screen**, which mean a top-level GUIX object, usually a GUIX Window, and all of its associated child elements.</span></span> <span data-ttu-id="0405a-214">Экран — это программная конструкция, которую можно определить и изменить во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0405a-214">A Screen is a software construct that can be defined and modified at runtime.</span></span> <span data-ttu-id="0405a-215">Наконец, «**тема**» — это коллекция ресурсов.</span><span class="sxs-lookup"><span data-stu-id="0405a-215">Finally, a **Theme** is a collection of resources.</span></span> <span data-ttu-id="0405a-216">Тема включает таблицу определений цветов, определений шрифтов и определений карт отображения пикселей, предназначенных для совместной работы и предоставления конечному пользователю единообразного внешнего вида и функционала.</span><span class="sxs-lookup"><span data-stu-id="0405a-216">A theme includes a table of color definitions, font definitions, and pixelmap definitions that are designed to work well together and present your end user with a consistent look and feel.</span></span>

<span data-ttu-id="0405a-217">Во-первых, проект включает набор глобальных данных, таких как имя проекта, число поддерживаемых дисплеев, разрешение и формат цвета каждого дисплея, число поддерживаемых языков, имя каждого поддерживаемого языка.</span><span class="sxs-lookup"><span data-stu-id="0405a-217">The project first includes a set of global information such as the project name, number of displays supported, the resolution and color format of each display, the number of languages supported, the name of each supported language.</span></span> <span data-ttu-id="0405a-218">Имя проекта — это первый узел, отображаемый в представлении проекта.</span><span class="sxs-lookup"><span data-stu-id="0405a-218">The project name is the first node displayed in the Project View.</span></span>

<span data-ttu-id="0405a-219">Далее в проекте в упорядоченном виде содержится вся информация, необходимая для 4 физических дисплеев (макс.), а также экранов и ресурсов, доступных для каждого экрана.</span><span class="sxs-lookup"><span data-stu-id="0405a-219">The project next organizes all of the information required for up to 4 physical displays and the screens and resources available to each display.</span></span> <span data-ttu-id="0405a-220">Отображаемые имена — это узлы следующего уровня в дереве представления проекта.</span><span class="sxs-lookup"><span data-stu-id="0405a-220">The display names are the next level nodes in the Project View tree.</span></span>

<span data-ttu-id="0405a-221">Уникальная функция приложения GUIX Studio — это встроенная поддержка нескольких физических дисплеев, каждый из которых имеет собственное разрешение (x, y), цветовой формат, экраны и ресурсы.</span><span class="sxs-lookup"><span data-stu-id="0405a-221">A unique feature of the GUIX Studio application is built-in support for multiple physical displays, each with its own x,y resolution, color format, screens, and resources.</span></span> <span data-ttu-id="0405a-222">Хотя подавляющее большинство приложений GUIX предназначены только для одного физического дисплея, эта возможность важна для тех, кто делает продукт, который должен поддерживать несколько одновременно работающих физических дисплеев.</span><span class="sxs-lookup"><span data-stu-id="0405a-222">While the vast majority of GUIX applications utilize only one physical display, this capability is important for those making a product that must support multiple simultaneous physical displays.</span></span>

<span data-ttu-id="0405a-223">Под каждым определением дисплея расположены окна верхнего уровня и экраны, заданные для этого дисплея.</span><span class="sxs-lookup"><span data-stu-id="0405a-223">Beneath each display definition are the top-level windows or screens defined for that display.</span></span> <span data-ttu-id="0405a-224">Определения экранов могут быть вложены на любом уровне в зависимости от наличия вложенных дочерних мини-приложений и их числа на каждом экране.</span><span class="sxs-lookup"><span data-stu-id="0405a-224">The screen definitions can be nested to any level depending on the number and nesting of child widgets on each screen.</span></span>

<span data-ttu-id="0405a-225">Эта организация экранов и дочерних мини-приложений отображается в графическом виде в представлении проекта.</span><span class="sxs-lookup"><span data-stu-id="0405a-225">This screen and child widget organization is displayed in a graphical manner in the Project View.</span></span>

<span data-ttu-id="0405a-226">Кроме того, с каждым дисплеем связаны темы, поддерживаемые дисплеем, и содержимое ресурсов, из которых состоит тема.</span><span class="sxs-lookup"><span data-stu-id="0405a-226">Also associated with each display are the Themes supported by the display and the resource content composing each Theme.</span></span> <span data-ttu-id="0405a-227">Если проект содержит несколько дисплеев, вы заметите, что содержимое представления ресурсов меняется в зависимости от выбранного дисплея.</span><span class="sxs-lookup"><span data-stu-id="0405a-227">If your project includes multiple displays, you will notice that the Resource View changes its content when you select one display and then another.</span></span> <span data-ttu-id="0405a-228">Это связано с тем, что содержимое ресурсов связано с конкретным дисплеем.</span><span class="sxs-lookup"><span data-stu-id="0405a-228">This is because the resource content is linked to each display.</span></span> <span data-ttu-id="0405a-229">Для каждого физического дисплея может отличаться не только формат цвета, но и карты отображения пикселей, цвета и шрифты, доступные для использования.</span><span class="sxs-lookup"><span data-stu-id="0405a-229">Not only the color format may be different, but the pixelmaps, colors, and fonts you choose to use may vary from one physical display to another.</span></span>

<span data-ttu-id="0405a-230">Последним компонентом, поддерживаемым проектом, являются данные таблицы строк, связанные с каждым из дисплеев.</span><span class="sxs-lookup"><span data-stu-id="0405a-230">The final component maintained by the project is the string table data associated with each display.</span></span> <span data-ttu-id="0405a-231">Так как дисплеи могут иметь совершенно разные разрешения (x, y), строковые данные сохраняются отдельно для каждого дисплея, заданного в проекте.</span><span class="sxs-lookup"><span data-stu-id="0405a-231">Since displays can be of very different x,y resolutions, the string data is maintained independently for each display defined in the project.</span></span>
