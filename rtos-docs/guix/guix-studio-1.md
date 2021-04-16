---
title: Руководство пользователя по GUIX Studio
description: Это руководство содержит подробную информацию о среде GUIX Studio на основе Microsoft Windows, которая предназначена для быстрой разработки пользовательского интерфейса и использует библиотеку среды выполнения GUIX корпорации Майкрософт.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815500"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a><span data-ttu-id="22cc0-103">Глава 1. Введение в GUIX Studio для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="22cc0-103">Chapter 1: Introduction to Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="22cc0-104">GUIX Studio для ОСРВ Azure — это среда быстрой разработки пользовательского интерфейса на основе Microsoft Windows, специально разработанная для работы с библиотекой среды выполнения GUIX корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="22cc0-104">Azure RTOS GUIX Studio is a Microsoft Windows-based rapid UI development environment specifically designed for the GUIX runtime library from Microsoft.</span></span>

<span data-ttu-id="22cc0-105">Разработчики пользовательского интерфейса для встраиваемых систем могут использовать конструктор экранов WYSIWYG в GUIX Studio для быстрого создания и обновления пользовательских интерфейсов на основе среды выполнения GUIX.</span><span class="sxs-lookup"><span data-stu-id="22cc0-105">Embedded UI Developers can utilize the GUIX Studio WYSIWYG screen designer to quickly create and update their embedded UI using the GUIX run-time environment.</span></span> <span data-ttu-id="22cc0-106">Проекты GUIX Studio сохраняются и обслуживаются в файле GUIX Studio, который имеет расширение .gxp.</span><span class="sxs-lookup"><span data-stu-id="22cc0-106">GUIX Studio designs are saved and maintained in a GUIX Studio project file, which has the extension .gxp.</span></span> <span data-ttu-id="22cc0-107">Когда проект готов к выполнению на целевой системе, GUIX Studio создает код на языке C, которые содержит все необходимые сведения о пользовательском интерфейсе и код для него.</span><span class="sxs-lookup"><span data-stu-id="22cc0-107">When your design is ready for execution on the target, GUIX Studio generates C code that contains all the necessary UI information and code.</span></span>

## <a name="guix-studio-requirements"></a><span data-ttu-id="22cc0-108">Требования для GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="22cc0-108">GUIX Studio Requirements</span></span>

<span data-ttu-id="22cc0-109">Для правильной работы Microsoft GUIX Studio требуется ОС *Windows XP* (или более поздние версии).</span><span class="sxs-lookup"><span data-stu-id="22cc0-109">In order to function properly, Microsoft's GUIX Studio requires *Windows XP* (or above).</span></span> <span data-ttu-id="22cc0-110">В системе должно быть как минимум 200 МБ ОЗУ, 2 ГБ свободного места на жестком диске и экран с разрешением не ниже 1024×768 с поддержкой 256 цветов.</span><span class="sxs-lookup"><span data-stu-id="22cc0-110">The system should have a minimum of 200MB of RAM, 2GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="22cc0-111">Кроме того, встраиваемое приложение должно работать на платформе *ThreadX/GUIX V6.0* или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="22cc0-111">In addition, the embedded application must be running on *ThreadX/GUIX V6.0* or later.</span></span>

<span data-ttu-id="22cc0-112">Если вы хотите создавать и запускать встраиваемые приложения пользовательского интерфейса как автономный исполняемый файл Microsoft Windows, потребуется также компилятор или среда сборки с поддержкой компиляции исходного кода C в исполняемые файлы Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="22cc0-112">If you would like to be able to build and run the embedded UI application as a stand-alone Microsoft Windows executable, you will also need a compiler or build environment capable of compiling C source code to produce a Microsoft Windows executable.</span></span> <span data-ttu-id="22cc0-113">Пакет оценки, входящий в состав GUIX Studio, также включает файлы проектов, совместимые с Visual Studio 2019, и решения для каждого из предоставленных примеров приложений.</span><span class="sxs-lookup"><span data-stu-id="22cc0-113">The evaluation package included with GUIX Studio also includes Visual Studio 2019 compatible project files and solutions for each of the provided example applications.</span></span> <span data-ttu-id="22cc0-114">Если вы используете другой компилятор, вам придется создать собственные файлы проекта или файлы сборки для создания примеров приложений. Если потребуется помощь, обратитесь в службу поддержки по адресу https://aka.ms/azrtos-support.</span><span class="sxs-lookup"><span data-stu-id="22cc0-114">If you are using a different compiler, you will need to create your own project files or make files for the purposes of building your example applications, or contact support at https://aka.ms/azrtos-support.</span></span>

## <a name="guix-studio-constraints"></a><span data-ttu-id="22cc0-115">Ограничения GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="22cc0-115">GUIX Studio Constraints</span></span>

<span data-ttu-id="22cc0-116">Средство разработки пользовательского интерфейса GUIX Studio имеет несколько ограничений:</span><span class="sxs-lookup"><span data-stu-id="22cc0-116">The GUIX Studio UI design tool has several constraints, as follows:</span></span>

- <span data-ttu-id="22cc0-117">Не более 4 экранов на один проект.</span><span class="sxs-lookup"><span data-stu-id="22cc0-117">A maximum of 4 displays per project.</span></span>
- <span data-ttu-id="22cc0-118">Не более 100 000 мини-приложений на один проект GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="22cc0-118">A maximum of 100,000 widgets per GUIX Studio project.</span></span>
- <span data-ttu-id="22cc0-119">Не более 100 000 различных ресурсов, в том числе цветов, шрифтов, пиксельных карт, строк и т. д.</span><span class="sxs-lookup"><span data-stu-id="22cc0-119">A maximum of 100,000 distinct resources, e.g., colors, fonts, pixelmaps, strings, etc.</span></span>