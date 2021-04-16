---
title: Установка и использование GUIX Studio
description: В этой главе обсуждаются разные вопросы, связанные с установкой, настройкой и использованием средства разработки пользовательского интерфейса GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815499"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="5d24e-103">Глава 2. Установка и использование GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="5d24e-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="5d24e-104">В этой главе обсуждаются разные вопросы, связанные с установкой, настройкой и использованием средства разработки пользовательского интерфейса GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="5d24e-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="5d24e-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="5d24e-105">Product Distribution</span></span>

<span data-ttu-id="5d24e-106">Приложение GUIX Studio можно получить из [магазина приложений Microsoft Store](https://microsoft.com/store/apps), выполнив поиск по строке "GUIX Studio" или перейдя на [страницу GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab) по прямой ссылке.</span><span class="sxs-lookup"><span data-stu-id="5d24e-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="5d24e-107">После этого сделайте следующее.</span><span class="sxs-lookup"><span data-stu-id="5d24e-107">Then do the following.</span></span>

1. <span data-ttu-id="5d24e-108">На странице GUIX Studio в Microsoft Store нажмите кнопку **Получить** или **Установить**, чтобы скачать GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="5d24e-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="5d24e-109">В браузере может появиться сообщение с предложением открыть Microsoft Store, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="5d24e-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="5d24e-110">В этом случае нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="5d24e-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="5d24e-111">![Щелкните "Открыть", чтобы установить GUIX Studio.](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="5d24e-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="5d24e-112">Когда установка завершится, нажмите кнопку **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="5d24e-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="5d24e-113">При первом запуске GUIX Studio отобразится диалоговое окно с вопросом о том, нужно ли клонировать репозиторий GUIX на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="5d24e-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="5d24e-114">Вы можете выбрать вариант с клонированием репозитория, указать расположение уже клонированного ранее репозитория, или отказаться от клонирования репозитория (в этом случае на компьютере будет установлен только один пример проекта).</span><span class="sxs-lookup"><span data-stu-id="5d24e-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="5d24e-115">![Выбор между клонированием репозитория, выбором уже клонированного репозитория и отказом от клонирования.](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="5d24e-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="5d24e-116">!</span><span class="sxs-lookup"><span data-stu-id="5d24e-116">!</span></span>[!NOTE]
> <span data-ttu-id="5d24e-117">Вернуться в это диалоговое окно можно в любое время, выбрав в главном меню GUIX Studio пункт **Настроить**, а затем — **Репозиторий GUIX**.</span><span class="sxs-lookup"><span data-stu-id="5d24e-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="5d24e-118">После завершения процесса запуска приложение GUIX Studio будет готово к использованию.</span><span class="sxs-lookup"><span data-stu-id="5d24e-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="5d24e-119">Использование GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="5d24e-119">Using GUIX Studio</span></span>

<span data-ttu-id="5d24e-120">Работать с GUIX Studio очень просто. Вам нужно лишь запустить GUIX Studio с помощью кнопки "***Пуск***".</span><span class="sxs-lookup"><span data-stu-id="5d24e-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="5d24e-121">Откроется пользовательский интерфейс GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="5d24e-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="5d24e-122">Теперь все готово к созданию пользовательского интерфейса для встраиваемой системы с помощью графических средств GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="5d24e-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="5d24e-123">Здесь вы можете создать новый проект или открыть существующий проект с примерами проектов GUIX.</span><span class="sxs-lookup"><span data-stu-id="5d24e-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="5d24e-124">Можно также дважды щелкнуть любой файл проекта GUIX Studio с расширением **.gxp**. Это действие автоматически запустит GUIX Studio и откроет проект, к которому относится этот файл.</span><span class="sxs-lookup"><span data-stu-id="5d24e-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="5d24e-125">Примеры проектов GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="5d24e-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="5d24e-126">Несколько файлов с расширением **gxp** _, которые содержат примеры проектов GUIX Studio, находятся в подкаталоге_ *_Samples_*\* локальной установки.</span><span class="sxs-lookup"><span data-stu-id="5d24e-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="5d24e-127">Эти предварительно созданные примеры проектов помогут вам быстро освоиться с GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="5d24e-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="5d24e-128">Один из примеров файла проекта, который всегда присутствует, это \***samples/demo_guix_simple/guix_simple. gxp** _.</span><span class="sxs-lookup"><span data-stu-id="5d24e-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="5d24e-129">В этом примере файла проекта представлено определение простого пользовательского интерфейса GUIX, который описан в _ *_главе 7_*\* этого документа.</span><span class="sxs-lookup"><span data-stu-id="5d24e-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![Снимок экрана. Пользовательский интерфейс GUIX Studio.](./media/guix-studio/image_10.png)

<span data-ttu-id="5d24e-131">**Рисунок 1**</span><span class="sxs-lookup"><span data-stu-id="5d24e-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="5d24e-132">Сочетания клавиш</span><span class="sxs-lookup"><span data-stu-id="5d24e-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="5d24e-133">**CTRL+N:** создать проект.</span><span class="sxs-lookup"><span data-stu-id="5d24e-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="5d24e-134">**CTRL+O:** открыть проект.</span><span class="sxs-lookup"><span data-stu-id="5d24e-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="5d24e-135">**CTRL+S:** сохранить проект.</span><span class="sxs-lookup"><span data-stu-id="5d24e-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="5d24e-136">**CTRL+SHIFT+S:** сохранить проект как.</span><span class="sxs-lookup"><span data-stu-id="5d24e-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="5d24e-137">**ALT+F4:** выйти.</span><span class="sxs-lookup"><span data-stu-id="5d24e-137">**Alt + F4:** Exit</span></span>
