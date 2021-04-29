---
title: Простой пример проекта
description: В этой главе описывается, как создать пример проекта в GUIX Studio и выполнить его в GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815004"
---
# <a name="chapter-10-example-project"></a><span data-ttu-id="7929c-103">Глава 10. Пример проекта</span><span class="sxs-lookup"><span data-stu-id="7929c-103">Chapter 10: Example Project</span></span>

<span data-ttu-id="7929c-104">В этой главе описывается, как создать пример проекта в GUIX Studio и выполнить его в GUIX.</span><span class="sxs-lookup"><span data-stu-id="7929c-104">This chapter describes how to create an example project in GUIX Studio and execute the example on GUIX.</span></span>

## <a name="create-new-project"></a><span data-ttu-id="7929c-105">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="7929c-105">Create New Project</span></span>

<span data-ttu-id="7929c-106">Сначала необходимо создать проект и настроить дисплеи и языки, которые он будет поддерживать.</span><span class="sxs-lookup"><span data-stu-id="7929c-106">The first step is creating a new project and configuring the displays and languages that the project will support.</span></span> <span data-ttu-id="7929c-107">При первом запуске GUIX Studio появляется экран ***Recent Projects*** (Недавние проекты).</span><span class="sxs-lookup"><span data-stu-id="7929c-107">When you first start GUIX Studio, you will see the ***Recent Projects*** screen:</span></span>

![Снимок экрана: диалоговое окно Recent Projects (Недавние проекты) в GUIX Studio](./media/guix-studio/recent_projects.png)

<span data-ttu-id="7929c-109">**Рис. 10.1**</span><span class="sxs-lookup"><span data-stu-id="7929c-109">**Figure 10.1**</span></span>

<span data-ttu-id="7929c-110">Нажмите кнопку \***Create New Project…** _ (Создать проект),</span><span class="sxs-lookup"><span data-stu-id="7929c-110">Click on the \***Create New Project** _…</span></span> <span data-ttu-id="7929c-111">чтобы создать проект.</span><span class="sxs-lookup"><span data-stu-id="7929c-111">button to begin a new project.</span></span> <span data-ttu-id="7929c-112">Появится диалоговое окно _ *_New GUIX Project_*\* (Новый проект GUIX), показанное ниже.</span><span class="sxs-lookup"><span data-stu-id="7929c-112">You will be presented with the _ *_New GUIX Project_*\* dialog, shown here:</span></span>

![Снимок экрана: диалоговое окно создания проекта в GUIX Studio](./media/guix-studio/create_new_project.png)

<span data-ttu-id="7929c-114">**Рис. 10.2**</span><span class="sxs-lookup"><span data-stu-id="7929c-114">**Figure 10.2**</span></span>

<span data-ttu-id="7929c-115">Введите имя проекта ***new_example***.</span><span class="sxs-lookup"><span data-stu-id="7929c-115">Type the name "***new_example***" as the project name.</span></span> <span data-ttu-id="7929c-116">Имена проектов должны следовать стандартным правилам именования переменных в C, то есть в них не должно быть специальных или зарезервированных символов.</span><span class="sxs-lookup"><span data-stu-id="7929c-116">Project names should use standard C variable naming rules, that is, no special or reserved characters.</span></span> <span data-ttu-id="7929c-117">Введите путь к расположению, где нужно сохранить проект.</span><span class="sxs-lookup"><span data-stu-id="7929c-117">Type the path to the location where the project should be saved.</span></span> <span data-ttu-id="7929c-118">Путь должен указывать на допустимый каталог файловой системы. GUIX Studio не создаст каталог, если он не существует.</span><span class="sxs-lookup"><span data-stu-id="7929c-118">The path must be a valid file system directory, that is, GUIX Studio will not create the directory if it does not exist.</span></span> <span data-ttu-id="7929c-119">Чтобы создать проект, нажмите кнопку OK.</span><span class="sxs-lookup"><span data-stu-id="7929c-119">Click "OK" to create the project.</span></span>

<span data-ttu-id="7929c-120">Следующий экран — Project Configuration (Конфигурация проекта).</span><span class="sxs-lookup"><span data-stu-id="7929c-120">The next screen shown is the Project Configuration screen, shown here:</span></span>

![Снимок экрана: диалоговое окно Project Configuration (Конфигурация проекта) в GUIX Studio](./media/guix-studio/config_new_project.png)

<span data-ttu-id="7929c-122">**Рис. 10.3**</span><span class="sxs-lookup"><span data-stu-id="7929c-122">**Figure 10.3**</span></span>

<span data-ttu-id="7929c-123">В этом диалоговом окне можно указать, сколько дисплеев будет поддерживать проект, и присвоить каждому из них имя.</span><span class="sxs-lookup"><span data-stu-id="7929c-123">This dialog allows you to specify how many displays your project will support, and give a name to each display.</span></span> <span data-ttu-id="7929c-124">Для каждого дисплея необходимо указать поддерживаемый формат цвета и при необходимости ввести путь к выходным файлам, создаваемым для каждого экрана.</span><span class="sxs-lookup"><span data-stu-id="7929c-124">You must specify the color format supported by each display, and optionally type a pathname for the output files generated by Studio for each display.</span></span> <span data-ttu-id="7929c-125">Каталогом по умолчанию для выходных файлов является "***.\\***", то есть выходные файлы C записываются в тот же каталог, что и сам проект.</span><span class="sxs-lookup"><span data-stu-id="7929c-125">The default directory for the output files is "***.\\***", meaning the C output files are written to the same directory as the project itself.</span></span>

<span data-ttu-id="7929c-126">В этом примере оставьте для параметра ***Number of Displays** _ (Число дисплеев) значение 1, в поле отображаемого имени введите имя _*_main_display_*_ и установите флажок _*_allocate canvas memory_\*_ (Выделить память холста).</span><span class="sxs-lookup"><span data-stu-id="7929c-126">For this example, leave the ***Number of Displays** _ set to "1", type the name "_*_main_display_*_" in the display name field, and check "_*_allocate canvas memory_\*_".</span></span> <span data-ttu-id="7929c-127">Оставьте значения по умолчанию в полях разрешения, формата цвета и каталога и нажмите кнопку _\*_OK_\*\*.</span><span class="sxs-lookup"><span data-stu-id="7929c-127">Leave the resolution, color format, and directory fields at their default values, and click _\*_OK_\*\*.</span></span>

<span data-ttu-id="7929c-128">Проект должен открыться в интегрированной среде разработки (IDE) Studio, как показано на рис. 10.4.</span><span class="sxs-lookup"><span data-stu-id="7929c-128">You should now see your project open with the Studio IDE, as shown in figure 10.4:</span></span>

![Снимок экрана: проект, открытый в IDE Studio](./media/guix-studio/initial_screen.png)

<span data-ttu-id="7929c-130">**Рис. 10.4**</span><span class="sxs-lookup"><span data-stu-id="7929c-130">**Figure 10.4**</span></span>

<span data-ttu-id="7929c-131">При создании проекта GUIX Studio автоматически создает окно по умолчанию в качестве отправной точки.</span><span class="sxs-lookup"><span data-stu-id="7929c-131">When you create a new project, GUIX Studio automatically creates a default window as the starting point for your project.</span></span> <span data-ttu-id="7929c-132">Это серое поле, находящееся по центру *целевого представления*.</span><span class="sxs-lookup"><span data-stu-id="7929c-132">This gray box is the default window created for you, centered within the *Target View*.</span></span>

<span data-ttu-id="7929c-133">Если это окно не выбрано, щелкните его, чтобы вокруг него появилось пунктирное поле выделения.</span><span class="sxs-lookup"><span data-stu-id="7929c-133">If this window is not selected, click on the window so that the dashed selection box is drawn around the window.</span></span> <span data-ttu-id="7929c-134">Теперь на панели ***Properties View** _ (Представление свойств) измените значения свойств _*_Widget Name_*_ (Имя мини-приложения), _*_Widget Id_*_ (Идентификатор мини-приложения), _*_Left_*_ (Слева), _*_Top_*_ (Сверху), _*_Width_*_ (Ширина), _*_Height_\*_ (Высота) и _ *_Border_* \* (Граница) на указанные ниже.</span><span class="sxs-lookup"><span data-stu-id="7929c-134">Now in the ***Properties View** _, change the _*_Widget Name_*_, _*_Widget Id_*_, _*_Left_*_, _*_Top_*_, _*_Width_*_, _*_Height_*_, and _ *_Border_** to match those settings shown below.</span></span> <span data-ttu-id="7929c-135">В процессе внесения этих изменений они немедленно вступают в силу в целевом представлении.</span><span class="sxs-lookup"><span data-stu-id="7929c-135">As you make these changes, you should see your changes immediately taking effect within the Target View.</span></span>

![Снимок экрана: диалоговое окно Properties View (Представление свойств)](./media/guix-studio/initial_window_properties.png)

<span data-ttu-id="7929c-137">**Рис. 10.5**</span><span class="sxs-lookup"><span data-stu-id="7929c-137">**Figure 10.5**</span></span>

<span data-ttu-id="7929c-138">Далее мы добавим ресурс карты отображения пикселей, который будет использоваться в мини-приложении \***GX_ICON** _.</span><span class="sxs-lookup"><span data-stu-id="7929c-138">Next we will add a pixelmap resource to be used within a \***GX_ICON** _ widget.</span></span> <span data-ttu-id="7929c-139">В дистрибутиве GUIX Studio есть несколько значков, которые подойдут для этого примера.</span><span class="sxs-lookup"><span data-stu-id="7929c-139">Several icons are provided with your GUIX Studio distribution that will work fine for this example.</span></span> <span data-ttu-id="7929c-140">Разверните представление ресурсов _*_Pixelmaps_*_ (Карты отображения ресурсов) и нажмите кнопку _ *_Add New Pixelmap_*\* (Добавить новую карту отображения ресурсов).</span><span class="sxs-lookup"><span data-stu-id="7929c-140">Expand your _*_Pixelmaps_*_ Resource View and click the _ *_Add New Pixelmap_*\* button:</span></span>

![Снимок экрана: кнопка Add New Pixelmap (Добавить новую карту отображения ресурсов)](./media/guix-studio/image74.jpg)

<span data-ttu-id="7929c-142">Перейдите к папке установки GUIX Studio и в папке \* **./graphics/icons** _ выберите файл с именем _*_i_history_lg.png_*_.</span><span class="sxs-lookup"><span data-stu-id="7929c-142">Browse to your GUIX Studio installation folder, and within the ***./graphics/icons** _ folder select the file named _*_i_history_lg.png_\*_.</span></span> <span data-ttu-id="7929c-143">Нажмите кнопку _\*_Открыть_\*_, чтобы добавить этот ресурс в проект.</span><span class="sxs-lookup"><span data-stu-id="7929c-143">Click _*_Open_*_ to add this resource to your project.</span></span> <span data-ttu-id="7929c-144">Теперь в представлении ресурсов _ *_Pixelmaps_*\* (Карты отображения пикселей) должно быть показано, как будет выглядеть добавленное изображение значка.</span><span class="sxs-lookup"><span data-stu-id="7929c-144">Your _ *_Pixelmaps_*\* Resource View should now show a preview of the newly added icon image:</span></span>

![Снимок экрана: представление ресурсов Pixelmaps (Карты отображения пикселей)](./media/guix-studio/example_add_pixelmap.png)

<span data-ttu-id="7929c-146">**Рис. 10.6**</span><span class="sxs-lookup"><span data-stu-id="7929c-146">**Figure 10.6**</span></span>

<span data-ttu-id="7929c-147">Этот новый ресурс изображения будет использоваться позже в макете пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="7929c-147">We will use this new image resource later as part of our UI design.</span></span>

<span data-ttu-id="7929c-148">Так же, как ресурс карты отображения пикселей, мы добавим на панель элементов новый ресурс шрифта, чтобы использовать его в дальнейшем в проекте.</span><span class="sxs-lookup"><span data-stu-id="7929c-148">Similar to adding a pixelmap resource, we will add a new font resource to our toolbox so that we can use this font later in our design.</span></span> <span data-ttu-id="7929c-149">Разверните представление ресурсов ***Fonts** _ (Шрифты) и нажмите кнопку _*_Add New Font_\*_ (Добавить новый шрифт).</span><span class="sxs-lookup"><span data-stu-id="7929c-149">Expand the ***Fonts** _ Resource View and click on the _*_Add New Font_\*_ button.</span></span> <span data-ttu-id="7929c-150">Откроется диалоговое окно _*_Add/Edit Font_*_ (Добавление или изменение шрифта).</span><span class="sxs-lookup"><span data-stu-id="7929c-150">This action will invoke the _*_Add/Edit_*_ font dialog.</span></span> <span data-ttu-id="7929c-151">Перейдите к имеющимся шрифтам GUIX в папке установки GUIX Studio, _\*_ .\\fonts\\verasans_ *_, и выберите файл шрифта TrueType с именем _* _VeraIt.ttf_*_. В поле имени шрифта введите значение_* _MEDIUM_ITALIC_*_, а в поле высоты — значение_* _30_\*\*.</span><span class="sxs-lookup"><span data-stu-id="7929c-151">Next, browse to the supplied GUIX fonts in the GUIX Studio installation folder, _\*_.\\fonts\\verasans_ *_, and select the TrueType font file named _*_VeraIt.ttf_*_. Type font the font name "_*_MEDIUM_ITALIC_*_" in the font name field, and type "_*_30_\*\*" in the height field.</span></span> <span data-ttu-id="7929c-152">Теперь диалоговое окно будет выглядеть так.</span><span class="sxs-lookup"><span data-stu-id="7929c-152">Your dialog should now look like this:</span></span>

![Снимок экрана: диалоговое окно Edit Font (Изменение шрифта)](./media/guix-studio/example_add_font.png)

<span data-ttu-id="7929c-154">**Рис. 10.7**</span><span class="sxs-lookup"><span data-stu-id="7929c-154">**Figure 10.7**</span></span>

<span data-ttu-id="7929c-155">Нажмите кнопку ***OK***, чтобы добавить этот шрифт в проект.</span><span class="sxs-lookup"><span data-stu-id="7929c-155">Click ***OK*** to add this font to your project.</span></span> <span data-ttu-id="7929c-156">Теперь шрифт должен отображаться в представлении ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7929c-156">You should now see the font in your Resource View:</span></span>

![Снимок экрана: шрифты в представлении ресурсов](./media/guix-studio/example_font_added.png)

<span data-ttu-id="7929c-158">**Рис. 10.8**</span><span class="sxs-lookup"><span data-stu-id="7929c-158">**Figure 10.8**</span></span>

<span data-ttu-id="7929c-159">Этот новый шрифт будет использоваться позже в проекте пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="7929c-159">We will use this new font later in our UI design.</span></span>

<span data-ttu-id="7929c-160">Теперь, когда у нас есть новые ресурсы, необходимо добавить на экран дочерние мини-приложения, которые смогут использовать их.</span><span class="sxs-lookup"><span data-stu-id="7929c-160">Now that we have some new resources available, we need to add some child widgets to our screen that can utilize these resources.</span></span> <span data-ttu-id="7929c-161">Выберите ранее созданное окно с именем \***hello_world** _, щелкнув его правой кнопкой мыши в целевом представлении.</span><span class="sxs-lookup"><span data-stu-id="7929c-161">Select the previously created window named "\***hello_world** _" by right-clicking on the window in the Target View.</span></span> <span data-ttu-id="7929c-162">В появившемся всплывающем меню выберите команду _*_Insert > Text > Prompt_*_ (Вставить > Текст > Подсказка), чтобы вставить новое мини-приложение _ *_GX_PROMPT_*\* и прикрепить его к фоновому окну.</span><span class="sxs-lookup"><span data-stu-id="7929c-162">In the pop-up menu that is now displayed, select the menu command _*_Insert, Text, Prompt_*_ to insert a new _ *_GX_PROMPT_*\* widget and attach the widget to the background window.</span></span> <span data-ttu-id="7929c-163">Теперь окно должно выглядеть так.</span><span class="sxs-lookup"><span data-stu-id="7929c-163">Your window should now look like this:</span></span>

![Снимок экрана: всплывающее меню с выбранной подсказкой](./media/guix-studio/image78.jpg)

<span data-ttu-id="7929c-165">**Рис. 10.9**</span><span class="sxs-lookup"><span data-stu-id="7929c-165">**Figure 10.9**</span></span>

<span data-ttu-id="7929c-166">В представлении ресурсов _ *_Fonts_*\* (Шрифты) выберите шрифт с именем \***MEDIUM_ITALIC** _ и перетащите его в мини-приложение подсказки.</span><span class="sxs-lookup"><span data-stu-id="7929c-166">Click on the font named "***MEDIUM_ITALIC** _" in the _ *_Fonts_** Resource View, and drag and drop the font on the prompt widget.</span></span> <span data-ttu-id="7929c-167">Затем измените свойства подсказки, как показано на рис. 10.10, чтобы задать ее размеры, прозрачность, текст и стиль.</span><span class="sxs-lookup"><span data-stu-id="7929c-167">Next, edit the prompt properties as shown in figure 10.10 to resize the prompt, set the prompt transparency, and change the prompt text and style:</span></span>

![Снимок экрана: представление свойств для подсказки](./media/guix-studio/image79.jpg)

<span data-ttu-id="7929c-169">**Рис. 10.10**</span><span class="sxs-lookup"><span data-stu-id="7929c-169">**Figure 10.10**</span></span>

<span data-ttu-id="7929c-170">Для просмотра всех параметров, в зависимости от разрешения экрана, может потребоваться прокрутить представление свойств вниз.</span><span class="sxs-lookup"><span data-stu-id="7929c-170">You may need to scroll vertically in the Properties View to see each of these settings depending on your screen resolution.</span></span> <span data-ttu-id="7929c-171">После внесения этих изменений целевое представление должно выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="7929c-171">After making these changes, your Target View should now look like this:</span></span>

![Снимок экрана: всплывающее меню с выделенным элементом Hello World](./media/guix-studio/image80.jpg)

<span data-ttu-id="7929c-173">**Рис. 10.11**</span><span class="sxs-lookup"><span data-stu-id="7929c-173">**Figure 10.11**</span></span>

<span data-ttu-id="7929c-174">Далее мы разместим на экране мини-приложение типа "Кнопка-значок".</span><span class="sxs-lookup"><span data-stu-id="7929c-174">Next we will place an Icon Button style widget on the screen.</span></span> <span data-ttu-id="7929c-175">Выберите фоновое окно, щелкнув его, и в меню верхнего уровня или контекстном меню выберите пункты ***Insert > Button > Icon Button** (Вставить > Кнопка > Кнопка-значок), чтобы добавить новое мини-приложение _*_GX_ICON_BUTTON_\*_ в окно.</span><span class="sxs-lookup"><span data-stu-id="7929c-175">Select the background window by clicking on it, and use either the top-level menu or the right-click pop-up menu to select ***Insert, Button, Icon Button** _ to add a new _*_GX_ICON_BUTTON_\*_ to the window.</span></span> <span data-ttu-id="7929c-176">Щелкните ранее добавленный значок с именем _ *_I_HISTORY_LG_*\* и перетащите его на кнопку-значок.</span><span class="sxs-lookup"><span data-stu-id="7929c-176">Click on the Icon named _ *_I_HISTORY_LG_*\* that we added earlier and drag it to the icon button.</span></span> <span data-ttu-id="7929c-177">В представлении свойств измените расположение и размер значка, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="7929c-177">Using the properties view, adjust the icon position and size as show below:</span></span>

![Снимок экрана: представление свойств для мини-приложения типа "Кнопка-значок"](./media/guix-studio/image81.jpg)

<span data-ttu-id="7929c-179">**Рис. 10.12**</span><span class="sxs-lookup"><span data-stu-id="7929c-179">**Figure 10.12**</span></span>

<span data-ttu-id="7929c-180">Теперь экран должен выглядеть следующим образом.</span><span class="sxs-lookup"><span data-stu-id="7929c-180">Your screen should now look like this:</span></span>

![Снимок экрана: всплывающее меню с элементом Hello World и значком буфера обмена](./media/guix-studio/image82.jpg)

<span data-ttu-id="7929c-182">**Рис. 10.13**</span><span class="sxs-lookup"><span data-stu-id="7929c-182">**Figure 10.13**</span></span>

<span data-ttu-id="7929c-183">На этом простой пример экрана завершен.</span><span class="sxs-lookup"><span data-stu-id="7929c-183">We will call this complete for the simple example screen design.</span></span> <span data-ttu-id="7929c-184">Реальные экраны приложений, скорее всего, будут гораздо более сложными, но этого достаточно для демонстрации создания собственных экранов с помощью GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="7929c-184">Your actual application screens will likely be much more sophisticated, but this is enough to show you how to use GUIX Studio to create your own application screens.</span></span>

## <a name="generate-resource-and-application-code"></a><span data-ttu-id="7929c-185">Создание кода ресурса и приложения</span><span class="sxs-lookup"><span data-stu-id="7929c-185">Generate Resource and Application Code</span></span>

<span data-ttu-id="7929c-186">Следующим шагом является создание файла ресурсов и файла спецификации, которые определяют встроенный пользовательский интерфейс GUIX времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="7929c-186">The next step is to generate the resource file and specification file that define the embedded GUIX run-time UI.</span></span> <span data-ttu-id="7929c-187">Чтобы создать выходные файлы, необходимо щелкнуть правой кнопкой мыши узел ***main_display** _ в представлении проекта и выбрать команду _ *_Generate Resource Files_** (Создать файлы ресурсов).</span><span class="sxs-lookup"><span data-stu-id="7929c-187">To generate your output files you will need right-click on the ***main_display** _ node in the Project View, and select the _ *_Generate Resource Files_** command.</span></span> <span data-ttu-id="7929c-188">Появится информационное окно с сообщением о том, что файлы ресурсов созданы, как показано на рис. 10.14.</span><span class="sxs-lookup"><span data-stu-id="7929c-188">You will observe an information window that indicates your resource files have been generated, as shown in figure 10.14:</span></span>

![Снимок экрана с диалоговым окном уведомления](./media/guix-studio/image83.jpg)

<span data-ttu-id="7929c-190">**Рис. 10.14**</span><span class="sxs-lookup"><span data-stu-id="7929c-190">**Figure 10.14**</span></span>

<span data-ttu-id="7929c-191">Нажмите кнопку ***OK** _, чтобы закрыть это уведомление, снова щелкните правой кнопкой мыши узел _*_main_display_*_ и выберите команду _ *_Generate Specification Files_** (Создать файлы спецификации).</span><span class="sxs-lookup"><span data-stu-id="7929c-191">Click ***OK** _ to dismiss this notification, and use the same procedure to right-click on the _*_main_display_*_ node and select the _ *_Generate Specification Files_** command.</span></span> <span data-ttu-id="7929c-192">Появится аналогичное окно уведомления.</span><span class="sxs-lookup"><span data-stu-id="7929c-192">You should observe a similar notification window.</span></span> <span data-ttu-id="7929c-193">Файлы простого приложения с пользовательским интерфейсом созданы.</span><span class="sxs-lookup"><span data-stu-id="7929c-193">You have now generated your simple UI application files.</span></span>

## <a name="create-user-supplied-code"></a><span data-ttu-id="7929c-194">Создание пользовательского кода</span><span class="sxs-lookup"><span data-stu-id="7929c-194">Create User Supplied Code</span></span>

<span data-ttu-id="7929c-195">Следующим шагом является создание собственного файла приложения, который будет вызывать созданный с помощью GUIX Studio экран.</span><span class="sxs-lookup"><span data-stu-id="7929c-195">The next step is to create your own application file that will invoke the GUIX Studio-generated screen design.</span></span> <span data-ttu-id="7929c-196">В редакторе на свой выбор создайте исходный файл с именем ***new_example.c*** и введите в нем следующий исходный код.</span><span class="sxs-lookup"><span data-stu-id="7929c-196">Using your preferred editor, create a source file named ***new_example.c***, and enter the following source code into this file:</span></span>

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

<span data-ttu-id="7929c-197">Приведенный выше исходный код создает типичный поток ThreadX `GUIX New Example Thread` с размером стека 4 КБ.</span><span class="sxs-lookup"><span data-stu-id="7929c-197">The source code above creates a typical ThreadX thread named `GUIX New Example Thread` with a stack size of 4K bytes.</span></span> <span data-ttu-id="7929c-198">Самое интересное начинается в функции ***new_example_thread_entry***.</span><span class="sxs-lookup"><span data-stu-id="7929c-198">The interesting work begins in the function named ***new_example_thread_entry***.</span></span> <span data-ttu-id="7929c-199">В ней запускается выполнение потока GUIX.</span><span class="sxs-lookup"><span data-stu-id="7929c-199">This function is where the GUIX specific thread begins to run.</span></span>

<span data-ttu-id="7929c-200">Сначала вызывается функция с именем ***gx_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="7929c-200">The first call is to the function named ***gx_system_initialize***.</span></span> <span data-ttu-id="7929c-201">Этот вызов всегда должен выполняться перед вызовом любых других интерфейсов API GUIX для подготовки библиотеки GUIX к первому использованию.</span><span class="sxs-lookup"><span data-stu-id="7929c-201">This call is always required before any other GUIX APIs are invoked to prepare the GUIX library for first use.</span></span>

<span data-ttu-id="7929c-202">Далее в примере вызывается функция ***gx_studio_display_configure***.</span><span class="sxs-lookup"><span data-stu-id="7929c-202">Next, the example calls the function ***gx_studio_display_configure***.</span></span> <span data-ttu-id="7929c-203">Она создает экземпляр дисплея GUIX, устанавливает требуемый язык таблицы строк приложения, устанавливает запрошенную тему из ресурсов дисплея и возвращает указатель на корневое окно, созданное для этого дисплея.</span><span class="sxs-lookup"><span data-stu-id="7929c-203">This function creates the GUIX display instance, installs the requested language of the application string table, installs the requested theme from the display resources, and returns a pointer to the root window that has been created for this display.</span></span> <span data-ttu-id="7929c-204">Корневое окно используется в качестве родительского для всех экранов верхнего уровня, которые будут отображаться в приложении.</span><span class="sxs-lookup"><span data-stu-id="7929c-204">The root window is used as the parent of all top-level screens that our application will display.</span></span>

<span data-ttu-id="7929c-205">Далее в примере вызывается функция \***gx_studio_named_widget_create** _ для создания экземпляра экрана _ \*_hello_world_\*\*.</span><span class="sxs-lookup"><span data-stu-id="7929c-205">Next the example calls ***gx_studio_named_widget_create** _ to create an instance of our _ *_hello_world_** screen.</span></span> <span data-ttu-id="7929c-206">Эта функция использует структуры данных и ресурсы, созданные средой GUIX Studio, для создания экземпляра определенного экрана.</span><span class="sxs-lookup"><span data-stu-id="7929c-206">This function uses the data structures and resource produces by GUIX Studio to create an instance of the screen as we have defined it.</span></span> <span data-ttu-id="7929c-207">Мы передаем указатель на корневое окно в качестве второго параметра в вызов этой функции, то есть мы хотим, чтобы экран был присоединен непосредственно к корневому окну.</span><span class="sxs-lookup"><span data-stu-id="7929c-207">We pass the root window pointer as the second parameter to this function call, meaning we want the screen to be immediately attached to the root window.</span></span> <span data-ttu-id="7929c-208">Последний параметр — необязательный возвращаемый указатель, который можно использовать, если нам нужен указатель на созданный экран.</span><span class="sxs-lookup"><span data-stu-id="7929c-208">The last parameter is an optional return pointer that can be used if we want to keep a pointer to the created screen.</span></span>

<span data-ttu-id="7929c-209">Далее вызывается функция \***gx_widget_show** _, которая делает корневое окно и все его дочерние элементы, включая экран _ \*_hello_world_\*\*, видимыми.</span><span class="sxs-lookup"><span data-stu-id="7929c-209">Next ***gx_widget_show** _ is called, which makes the root window and all of its children, including the _ *_hello_world_** screen, visible.</span></span>

<span data-ttu-id="7929c-210">Наконец, в примере вызывается ***gx_system_start***.</span><span class="sxs-lookup"><span data-stu-id="7929c-210">Finally, the example calls ***gx_system_start***.</span></span> <span data-ttu-id="7929c-211">Эта функция начинает выполнение цикла обработки системных событий GUIX.</span><span class="sxs-lookup"><span data-stu-id="7929c-211">This function begins executing the GUIX system event processing loop.</span></span>

## <a name="build-and-run-the-example"></a><span data-ttu-id="7929c-212">Сборка и запуск примера</span><span class="sxs-lookup"><span data-stu-id="7929c-212">Build and Run the Example</span></span>

<span data-ttu-id="7929c-213">Процедура сборки и запуска примера зависит от используемых средств сборки и среды.</span><span class="sxs-lookup"><span data-stu-id="7929c-213">Building and running the example is specific to your build tools and environment.</span></span> <span data-ttu-id="7929c-214">Однако в целом она выглядит так.</span><span class="sxs-lookup"><span data-stu-id="7929c-214">However we can define the general process:</span></span>

1. <span data-ttu-id="7929c-215">Создайте каталог и проект приложения.</span><span class="sxs-lookup"><span data-stu-id="7929c-215">Create a new directory and application project</span></span>
1. <span data-ttu-id="7929c-216">Добавьте в проект следующие файлы.</span><span class="sxs-lookup"><span data-stu-id="7929c-216">Add these files to the project:</span></span>

    <span data-ttu-id="7929c-217">**new_example_resources.c**</span><span class="sxs-lookup"><span data-stu-id="7929c-217">**new_example_resources.c**</span></span>

    <span data-ttu-id="7929c-218">**new_example_specification.c**</span><span class="sxs-lookup"><span data-stu-id="7929c-218">**new_example_specification.c**</span></span>

    <span data-ttu-id="7929c-219">**new_example.c**</span><span class="sxs-lookup"><span data-stu-id="7929c-219">**new_example.c**</span></span>

1. <span data-ttu-id="7929c-220">Добавьте вспомогательные файлы среды выполнения Win32 из пути установки GUIX Studio ***./win32_runtime***.</span><span class="sxs-lookup"><span data-stu-id="7929c-220">Add the Win32 run-time support files from the GUIX Studio installation path ***./win32_runtime***.</span></span> <span data-ttu-id="7929c-221">К ним относятся файлы заголовков и библиотеки времени выполнения Win32 для ThreadX и GUIX.</span><span class="sxs-lookup"><span data-stu-id="7929c-221">This includes the ThreadX and GUIX Win32 header and run-time library files.</span></span>
1. <span data-ttu-id="7929c-222">Добавьте в проект библиотеку Win32 GUIX (***gx.lib***).</span><span class="sxs-lookup"><span data-stu-id="7929c-222">Add the GUIX Win32 library (***gx.lib***) to the project</span></span>
1. <span data-ttu-id="7929c-223">Добавьте в проект библиотеку Win32 ThreadX (***tx.lib***).</span><span class="sxs-lookup"><span data-stu-id="7929c-223">Add the ThreadX Win32 library (***tx.lib***) to the project</span></span>
1. <span data-ttu-id="7929c-224">Скомпилируйте, скомпонуйте и запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="7929c-224">Compile, Link, and Run the application!</span></span>
