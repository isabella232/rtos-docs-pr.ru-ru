---
title: Командная строка GUIX Studio
description: GUIX Studio предоставляет вызов командной строки, что удобно использовать для конвейеров сборки, необходимых для обновления выходных файлов, создаваемых Studio.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9f9bfc67c524a77b5bf736407bf2ca372ce98308
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814915"
---
# <a name="chapter-9-guix-studio-command-line"></a><span data-ttu-id="a229a-103">Глава 9. Командная строка GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="a229a-103">Chapter 9: GUIX Studio Command Line</span></span>

<span data-ttu-id="a229a-104">GUIX Studio поддерживает вызов командной строки, что удобно использовать для конвейеров сборки, необходимых для обновления выходных файлов, создаваемых Studio.</span><span class="sxs-lookup"><span data-stu-id="a229a-104">GUIX Studio supports command-line invocation,  which is useful for build pipelines that are required to update of the Studio-generated output files.</span></span>

## <a name="command-line-usage"></a><span data-ttu-id="a229a-105">Использование командной строки</span><span class="sxs-lookup"><span data-stu-id="a229a-105">Command-Line Usage</span></span>

<span data-ttu-id="a229a-106">**Использование:** guix_studio \[параметр\] \[аргумент\]</span><span class="sxs-lookup"><span data-stu-id="a229a-106">**Usage:** guix_studio \[OPTION\] \[ARGUMENT\]</span></span>

<span data-ttu-id="a229a-107">Откройте *GXP*-файл проекта.</span><span class="sxs-lookup"><span data-stu-id="a229a-107">Open the *.gxp* project.</span></span>

<span data-ttu-id="a229a-108">Откройте проект Studio и создайте необходимые выходные файлы.</span><span class="sxs-lookup"><span data-stu-id="a229a-108">Open the Studio project and generate desired output files.</span></span>


<span data-ttu-id="a229a-109">**Примеры:**</span><span class="sxs-lookup"><span data-stu-id="a229a-109">**Examples:**</span></span>

`guix_studio demo.gxp`  
<span data-ttu-id="a229a-110">Открытие проекта demo.gxp.</span><span class="sxs-lookup"><span data-stu-id="a229a-110">Open "demo.gxp" project</span></span>


`guix_studio.exe –p demo.gxp`  
<span data-ttu-id="a229a-111">Открытие проекта demo.gxp.</span><span class="sxs-lookup"><span data-stu-id="a229a-111">Open "demo.gxp" project</span></span>


`guix_studio.exe –n –p demo.gxp`  
<span data-ttu-id="a229a-112">Создание всех выходных файлов проекта demo.gxp.</span><span class="sxs-lookup"><span data-stu-id="a229a-112">Generate all output files of demo.gxp project.</span></span>

`guix_studio.exe –n –r –p demo.gxp`  
<span data-ttu-id="a229a-113">Создание файлов ресурсов проекта demo.gxp.</span><span class="sxs-lookup"><span data-stu-id="a229a-113">Generate resource files of demo.gxp project</span></span>


## <a name="command-line-options"></a><span data-ttu-id="a229a-114">Параметры командной строки</span><span class="sxs-lookup"><span data-stu-id="a229a-114">Command-Line Options</span></span>

```C
***-n --nogui***  
```

<span data-ttu-id="a229a-115">Параметр nogui.</span><span class="sxs-lookup"><span data-stu-id="a229a-115">The "nogui" option.</span></span> <span data-ttu-id="a229a-116">Запуск GUIX Studio без оконного пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a229a-116">Tell GUIX Studio to run without starting the windowing UI interface.</span></span>

```C
***-o pathname***  
***--log***  
```

<span data-ttu-id="a229a-117">Параметр log позволяет указать файл журнала.</span><span class="sxs-lookup"><span data-stu-id="a229a-117">Log option, specify a log file.</span></span>

```C
***-b***  
***--binary***  
```

<span data-ttu-id="a229a-118">Параметр двоичного ресурса.</span><span class="sxs-lookup"><span data-stu-id="a229a-118">Binary resource option.</span></span> <span data-ttu-id="a229a-119">Создает двоичный файл ресурсов, а не файл C.</span><span class="sxs-lookup"><span data-stu-id="a229a-119">Produces a binary resource file rather than a C file.</span></span>

```C
***-d display1, display2***  
***--display***  
```

<span data-ttu-id="a229a-120">Параметр имен экранов.</span><span class="sxs-lookup"><span data-stu-id="a229a-120">Display names option.</span></span> <span data-ttu-id="a229a-121">Если используется этот параметр, в создаваемые файлы ресурсов или спецификаций добавляются только указанные имена экранов.</span><span class="sxs-lookup"><span data-stu-id="a229a-121">If this option is used, then only the specified display names are included in any generated resource or specification files.</span></span> <span data-ttu-id="a229a-122">Если этот параметр не используется, добавляются все экраны.</span><span class="sxs-lookup"><span data-stu-id="a229a-122">If this option is not used,  all displays are included.</span></span>

```C
***-t theme1, theme2***  
***--theme***  
```

<span data-ttu-id="a229a-123">Параметр имен тем.</span><span class="sxs-lookup"><span data-stu-id="a229a-123">Theme name(s) option.</span></span> <span data-ttu-id="a229a-124">Если используется этот параметр, в создаваемые файлы ресурсов или спецификаций добавляются только указанные имена тем.</span><span class="sxs-lookup"><span data-stu-id="a229a-124">If this option is used, then only the specified theme names are included in any generated resource or specification files.</span></span> <span data-ttu-id="a229a-125">Если этот параметр не используется, добавляются все темы.</span><span class="sxs-lookup"><span data-stu-id="a229a-125">If this option is not used, all themes are included.</span></span>

```C
***-l langage1, language2***  
***--language***  
```

<span data-ttu-id="a229a-126">Параметр имен языков.</span><span class="sxs-lookup"><span data-stu-id="a229a-126">Language name(s) option.</span></span> <span data-ttu-id="a229a-127">Если используется этот параметр, в создаваемые файлы ресурсов или спецификаций добавляются указанные имена языков.</span><span class="sxs-lookup"><span data-stu-id="a229a-127">If this option is used,  the specified language names are included in the generated resource or specification files.</span></span> <span data-ttu-id="a229a-128">В противном случае добавляются все имена языков.</span><span class="sxs-lookup"><span data-stu-id="a229a-128">Otherwise all language names are included.</span></span>

```C
***-r [filename]***  
***--resource***  
```

<span data-ttu-id="a229a-129">Параметр resource указывает, что приложение Studio должно создать файл ресурсов для ранее определенных экранов, тем и языков.</span><span class="sxs-lookup"><span data-stu-id="a229a-129">The resource option, specifies that Studio should produce a resource file for previously designated display(s), theme(s), and language(s).</span></span>

```C
***-s [filename]***  
***--specification***  
```

<span data-ttu-id="a229a-130">Параметр specification указывает, что приложение Studio должно создать файл спецификации для ранее определенных экранов, тем и языков.</span><span class="sxs-lookup"><span data-stu-id="a229a-130">The specification option, specify that studio should produce a specification file for designated display(s), theme(s), and language(s).</span></span>

```C
***-p project_pathname***  
***--project***  
```

<span data-ttu-id="a229a-131">Параметр пути к проекту позволяет указать пример проекта для загрузки.</span><span class="sxs-lookup"><span data-stu-id="a229a-131">Project pathname option, specify the example project to be loaded.</span></span>

```C
***-i [pathname]***  
***--import***  
```

<span data-ttu-id="a229a-132">Импортируйте строку из XLIFF- или CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="a229a-132">Import string from xliff or csv format file.</span></span>

<span data-ttu-id="a229a-133">***--big_endian***</span><span class="sxs-lookup"><span data-stu-id="a229a-133">***--big_endian***</span></span>  
<span data-ttu-id="a229a-134">Создание данных ресурса в формате с обратным порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="a229a-134">Generate resource data in big-endian format.</span></span>
