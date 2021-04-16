---
title: Глава 2. Установка и использование TraceX для ОСРВ Azure
description: В этой главе описываются различные вопросы, связанные с установкой, настройкой и использованием средства системного анализа TraceX для ОСРВ Azure.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815768"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="11c95-103">Глава 2. Установка и использование TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="11c95-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="11c95-104">В этой главе описываются различные вопросы, связанные с установкой, настройкой и использованием средства системного анализа TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="11c95-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="11c95-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="11c95-105">Product Distribution</span></span>

<span data-ttu-id="11c95-106">Приложение TraceX можно получить из [Microsoft App Store](https://microsoft.com/store/apps), выполнив поиск по строке TraceX или перейдя на [страницу TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab) по прямой ссылке.</span><span class="sxs-lookup"><span data-stu-id="11c95-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="11c95-107">После этого выполните следующее.</span><span class="sxs-lookup"><span data-stu-id="11c95-107">Then do the following.</span></span>

1. <span data-ttu-id="11c95-108">На странице TraceX в App Store нажмите кнопку **Получить** или **Установить**, чтобы установить TraceX.</span><span class="sxs-lookup"><span data-stu-id="11c95-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="11c95-109">В браузере может появиться сообщение с предложением открыть Microsoft Store, как показано на рисунке ниже.</span><span class="sxs-lookup"><span data-stu-id="11c95-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="11c95-110">В этом случае нажмите кнопку **Открыть**.</span><span class="sxs-lookup"><span data-stu-id="11c95-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="11c95-111">![Нажмите "Открыть", чтобы установить TraceX.](../guix/media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="11c95-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="11c95-112">Когда установка завершится, нажмите кнопку **Запустить**.</span><span class="sxs-lookup"><span data-stu-id="11c95-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="11c95-113">Использование TraceX</span><span class="sxs-lookup"><span data-stu-id="11c95-113">Using TraceX</span></span>

<span data-ttu-id="11c95-114">Чтобы начать работу с TraceX, достаточно просто открыть в TraceX файл трассировки.</span><span class="sxs-lookup"><span data-stu-id="11c95-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="11c95-115">Запустите TraceX с помощью кнопки \***Пуск** _.</span><span class="sxs-lookup"><span data-stu-id="11c95-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="11c95-116">Отобразится графический пользовательский интерфейс TraceX.</span><span class="sxs-lookup"><span data-stu-id="11c95-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="11c95-117">Теперь вы можете использовать TraceX для просмотра существующего буфера трассировки на целевой системе в графическом виде.</span><span class="sxs-lookup"><span data-stu-id="11c95-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="11c95-118">Для этого щелкните _ *_Файл -> Открыть,_*\* а затем введите двоичный файл трассировки.</span><span class="sxs-lookup"><span data-stu-id="11c95-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="11c95-119">*Также можно дважды щелкнуть любой файл трассировки с расширением **trx,** , что автоматически запустит TraceX.*</span><span class="sxs-lookup"><span data-stu-id="11c95-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![Снимок экрана: графический пользовательский интерфейс TraceX.](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="11c95-121">**Рис. 1**</span><span class="sxs-lookup"><span data-stu-id="11c95-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="11c95-122">*Изучите инструкции в **главе 5**, где описано создание буферов трассировки на целевой системе с помощью ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="11c95-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="11c95-123">Примеры для TraceX</span><span class="sxs-lookup"><span data-stu-id="11c95-123">TraceX Examples</span></span>

<span data-ttu-id="11c95-124">При первом запуске или обновлении приложения TraceX вам будет предложено установить примеры файлов трассировки для TraceX и файл custom_events.trxc в выбранный пользователем каталог на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="11c95-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="11c95-125">Завершив этот шаг установки, вы получите примеры файлов трассировки с расширением **trx** в подкаталоге **TraceFiles** выбранного для установки каталога.</span><span class="sxs-lookup"><span data-stu-id="11c95-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="11c95-126">Эти предварительно созданные примеры помогут быстро освоиться с изучением в TraceX буферов трассировки, созданных системой ThreadX, которая работает вместе с основным приложением.</span><span class="sxs-lookup"><span data-stu-id="11c95-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="11c95-127">Один из примеров трассировки всегда присутствует в файле \***demo_threadx.trx** _.</span><span class="sxs-lookup"><span data-stu-id="11c95-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="11c95-128">В этом примере файла трассировки демонстрируется выполнение стандартных операций ThreadX, которые описаны в главе 6 _"Руководство пользователя по ThreadX"\*.</span><span class="sxs-lookup"><span data-stu-id="11c95-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![Снимок экрана: диалоговое окно открытия файла в TraceX.](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="11c95-130">**Рис. 2**</span><span class="sxs-lookup"><span data-stu-id="11c95-130">**FIGURE 2**</span></span>
