---
title: Руководство пользователя по FileX (ОСРВ Azure)
description: Это руководство содержит исчерпывающую информацию о высокопроизводительной файловой системе реального времени FileX (ОСРВ Azure), разработанной корпорацией Майкрософт.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0ebcebdd2b227ed8d9ccf8b3078b716f90f35bef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814427"
---
# <a name="about-this-filex-user-guide"></a><span data-ttu-id="c1e4d-103">О руководстве пользователя FileX</span><span class="sxs-lookup"><span data-stu-id="c1e4d-103">About This FileX User Guide</span></span>

<span data-ttu-id="c1e4d-104">Это руководство содержит исчерпывающую информацию о высокопроизводительной встраиваемой файловой системе реального времени FileX (ОСРВ Azure), разработанной корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-104">This guide contains comprehensive information about Azure RTOS FileX, the high-performance, real-time embedded file system from Microsoft.</span></span> <span data-ttu-id="c1e4d-105">Для эффективной работы с этим руководством требуется знакомство с возможностями стандартной операционной системы реального времени, службами файловой системы FAT и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-105">To gain the most from this guide, you should be familiar with standard real-time operating system functions, FAT file system services, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="c1e4d-106">План</span><span class="sxs-lookup"><span data-stu-id="c1e4d-106">Organization</span></span>

<span data-ttu-id="c1e4d-107">[Глава 1](chapter1.md) — введение в FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS FileX</span></span>

<span data-ttu-id="c1e4d-108">[Глава 2](chapter2.md) — основные шаги по установке и использованию FileX (ОСРВ Azure) с приложением ThreadX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS FileX with your Azure RTOS ThreadX application</span></span>

<span data-ttu-id="c1e4d-109">[Глава 3](chapter3.md) — обзор функциональных возможностей файловой системы FileX (ОСРВ Azure) и базовые сведения о форматах файловой системы FAT.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS FileX system and basic information about FAT file system formats</span></span>

<span data-ttu-id="c1e4d-110">[Глава 4](chapter4.md) — подробное описание интерфейса между приложением и FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS FileX</span></span>

<span data-ttu-id="c1e4d-111">[Глава 5](chapter5.md) — описание предоставляемого в FileX (ОСРВ Azure) драйвера ОЗУ и способа создания собственных драйверов для FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-111">[Chapter 5](chapter5.md) - Describes the supplied Azure RTOS FileX RAM driver and how to write your own custom Azure RTOS FileX drivers</span></span>

<span data-ttu-id="c1e4d-112">[Глава 6](chapter6.md) — описание отказоустойчивого модуля FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-112">[Chapter 6](chapter6.md) - Describes the Azure RTOS FileX Fault Tolerant Module</span></span>

<span data-ttu-id="c1e4d-113">[Приложение A](appendix-a.md) — службы FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-113">[Appendix A](appendix-a.md) - Azure RTOS FileX Services</span></span>

<span data-ttu-id="c1e4d-114">[Приложение B](appendix-b.md) — константы FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-114">[Appendix B](appendix-b.md) - Azure RTOS FileX Constants</span></span>

<span data-ttu-id="c1e4d-115">[Приложение C](appendix-c.md) — типы данных FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-115">[Appendix C](appendix-c.md) - Azure RTOS FileX Data Types</span></span>

<span data-ttu-id="c1e4d-116">[Приложение D](appendix-d.md) — таблица ASCII.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-116">[Appendix D](appendix-d.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="c1e4d-117">Условные обозначения в руководстве</span><span class="sxs-lookup"><span data-stu-id="c1e4d-117">Guide Conventions</span></span>

<span data-ttu-id="c1e4d-118">*Курсивом* выделены заголовки книг, важные слова и обозначения переменных.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-118">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="c1e4d-119">**Полужирным** шрифтом выделены имена файлов и ключевые слова, а также важные слова и переменные.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="c1e4d-120">Информационные символы указывают на важные или дополнительные сведения, связанные с производительностью или работой функции.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c1e4d-121">Предупреждающие символы указывают на сценарии, которых следует избегать, так как они могут привести к неустранимым ошибкам.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="filex-data-types"></a><span data-ttu-id="c1e4d-122">Типы данных FileX</span><span class="sxs-lookup"><span data-stu-id="c1e4d-122">FileX Data Types</span></span>

<span data-ttu-id="c1e4d-123">Наряду с пользовательскими типами данных структуры управления FileX (ОСРВ Azure) существует ряд специальных типов данных, которые используются в интерфейсах вызова служб FileX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-123">In addition to the custom Azure RTOS FileX control structure data types, there is a series of special data types that are used in Azure RTOS FileX service call interfaces.</span></span> <span data-ttu-id="c1e4d-124">Эти специальные типы данных сопоставляются непосредственно с типами данных базового компилятора C.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="c1e4d-125">Это необходимо для обеспечения переносимости кода между разными компиляторами C.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="c1e4d-126">Конкретная реализация наследуется от ThreadX (ОСРВ Azure) и представлена в файле tx_port.h, включенном в состав дистрибутива ThreadX (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="c1e4d-126">The exact implementation is inherited from Azure RTOS ThreadX and can be found in the tx_port.h file included in the Azure RTOS ThreadX distribution.</span></span>

<span data-ttu-id="c1e4d-127">Ниже приведен список типов данных вызова служб FileX (ОСРВ Azure) и связанных значений.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-127">The following is a list of Azure RTOS FileX service call data types and their associated meanings.</span></span>
| <span data-ttu-id="c1e4d-128">Тип</span><span class="sxs-lookup"><span data-stu-id="c1e4d-128">Type</span></span>  | <span data-ttu-id="c1e4d-129">Описание</span><span class="sxs-lookup"><span data-stu-id="c1e4d-129">Description</span></span>  |
|---|---|
| <span data-ttu-id="c1e4d-130">**UINT**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-130">**UINT**</span></span> | <span data-ttu-id="c1e4d-131">Простое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-131">Basic unsigned integer.</span></span> <span data-ttu-id="c1e4d-132">Этот тип должен поддерживать 8-разрядные данные без знака, но свободно сопоставляется с наиболее удобным типом данных без знака.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-132">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="c1e4d-133">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-133">**ULONG**</span></span> | <span data-ttu-id="c1e4d-134">Длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-134">Unsigned long type.</span></span> <span data-ttu-id="c1e4d-135">Этот тип должен поддерживать 32-разрядные данные без знака.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-135">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="c1e4d-136">**VOID**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-136">**VOID**</span></span> | <span data-ttu-id="c1e4d-137">Почти всегда эквивалентен типу void компилятора.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-137">Almost always equivalent to the compiler’s void type.</span></span> |
| <span data-ttu-id="c1e4d-138">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-138">**CHAR**</span></span> | <span data-ttu-id="c1e4d-139">Чаще всего это стандартный 8-разрядный символьный тип.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-139">Most often a standard 8-bit character type.</span></span> |
| <span data-ttu-id="c1e4d-140">**ULONG64**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-140">**ULONG64**</span></span> | <span data-ttu-id="c1e4d-141">64-разрядный целочисленный тип.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-141">64-bit unsigned integer data type.</span></span> |

<span data-ttu-id="c1e4d-142">В исходном коде FileX используются дополнительные типы данных.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-142">Additional data types are used within the FileX source.</span></span> <span data-ttu-id="c1e4d-143">Они находятся в файлах \***tx_port.h** _ или _ \*_fx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-143">They are located in either the ***tx_port.h** _ or _ *_fx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="c1e4d-144">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="c1e4d-144">Customer Support Center</span></span>

<span data-ttu-id="c1e4d-145">Отправьте запрос в службу поддержки на портале Azure, если у вас возникли вопросы или вам нужна помощь при выполнении описанных здесь шагов.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="c1e4d-146">Предоставьте нам следующие сведения в сообщении электронной почты, чтобы мы могли эффективно обработать ваш запрос в службу поддержки:</span><span class="sxs-lookup"><span data-stu-id="c1e4d-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="c1e4d-147">Подробное описание проблемы, включая частоту ее возникновения и возможность воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="c1e4d-148">Подробное описание любых изменений в приложении и (или) FileX, предшествующих возникновению проблемы.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-148">A detailed description of any changes to the application and/or FileX that preceded the problem.</span></span>
3. <span data-ttu-id="c1e4d-149">Содержимое строк _tx_version_id и _fx_version_id из файлов \***tx_port.h**_ и _ *_fx_port.h_*\* вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-149">The contents of the _tx_version_id and _fx_version_id strings found in the \***tx_port.h**_ and _ *_fx_port.h_*\* files of your distribution.</span></span> <span data-ttu-id="c1e4d-150">Эти строки предоставят нам полезную информацию о вашей среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-150">These strings will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="c1e4d-151">Содержимое ОЗУ для следующих переменных **ULONG**.</span><span class="sxs-lookup"><span data-stu-id="c1e4d-151">The contents in RAM of the following **ULONG** variables.</span></span> <span data-ttu-id="c1e4d-152">Эти переменные позволят нам узнать, как компилировались библиотеки ThreadX и FileX:</span><span class="sxs-lookup"><span data-stu-id="c1e4d-152">These variables will give us information on how your ThreadX and FileX libraries were built:</span></span>

    <span data-ttu-id="c1e4d-153">**_tx_build_options**;</span><span class="sxs-lookup"><span data-stu-id="c1e4d-153">**_tx_build_options**</span></span>

    <span data-ttu-id="c1e4d-154">**_fx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-154">**_fx_system_build_options1**</span></span>

    <span data-ttu-id="c1e4d-155">**_fx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-155">**_fx_system_build_options2**</span></span>

    <span data-ttu-id="c1e4d-156">**_fx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="c1e4d-156">**_fx_system_build_options3**</span></span>
