---
title: О руководстве по ThreadX для ОСРВ Azure
description: В этом руководстве содержатся исчерпывающие сведения о ThreadX для ОСРВ Azure — высокопроизводительной платформе Майкрософт реального времени.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ad9f782942bcdbb2dc49a9c841d865d97bcb1d4e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815115"
---
# <a name="about-the-azure-rtos-threadx-guide"></a><span data-ttu-id="223c1-103">О руководстве по ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="223c1-103">About the Azure RTOS ThreadX Guide</span></span>

<span data-ttu-id="223c1-104">В этом руководстве содержатся исчерпывающие сведения о ThreadX для ОСРВ Azure — высокопроизводительной платформе Майкрософт реального времени.</span><span class="sxs-lookup"><span data-stu-id="223c1-104">This guide provides comprehensive information about Azure RTOS ThreadX, the Microsoft high-performance real-time kernel.</span></span> 

<span data-ttu-id="223c1-105">Оно предназначено для разработчиков внедренного программного обеспечения, работающего в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="223c1-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="223c1-106">Такие разработчики должны быть знакомы со стандартными функциями операционной системы, работающими в реальном времени, и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="223c1-106">The developer should be familiar with standard real-time operating system functions and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="223c1-107">План</span><span class="sxs-lookup"><span data-stu-id="223c1-107">Organization</span></span>

<span data-ttu-id="223c1-108">[Глава 1](chapter1.md) — общий обзор ThreadX для ОСРВ Azure и связи этой платформы с разработкой внедренных решений, работающих в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="223c1-108">[Chapter 1](chapter1.md) - Provides a basic overview of Azure RTOS ThreadX and its relationship to real-time embedded development</span></span>

<span data-ttu-id="223c1-109">[Глава 2](chapter2.md) — основные шаги по установке и использованию ThreadX для ОСРВ Azure в приложении *без дополнительной настройки*.</span><span class="sxs-lookup"><span data-stu-id="223c1-109">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS ThreadX in your application right *out of the box*</span></span>

<span data-ttu-id="223c1-110">[Глава 3](chapter3.md) — подробное описание функционирования ThreadX для ОСРВ Azure, высокопроизводительного ядра реального времени.</span><span class="sxs-lookup"><span data-stu-id="223c1-110">[Chapter 3](chapter3.md) - Describes in detail the functional operation of Azure RTOS ThreadX, the high performance real-time kernel</span></span>

<span data-ttu-id="223c1-111">[Глава 4](chapter4.md) — подробные сведения об интерфейсе приложения для ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="223c1-111">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS ThreadX</span></span>

<span data-ttu-id="223c1-112">[Глава 5](chapter5.md) — сведения о создании драйверов ввода-вывода для приложений ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="223c1-112">[Chapter 5](chapter5.md) - Describes writing I/O drivers for Azure RTOS ThreadX applications</span></span>

<span data-ttu-id="223c1-113">[Глава 6](chapter6.md) — описание демонстрационного приложения, входящего в состав каждого пакета поддержки процессора ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="223c1-113">[Chapter 6](chapter6.md) - Describes the demonstration application that is supplied with every Azure RTOS ThreadX processor support package</span></span>

<span data-ttu-id="223c1-114">[Приложение A](appendix-a.md). API ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="223c1-114">[Appendix A](appendix-a.md) - Azure RTOS ThreadX API</span></span>

<span data-ttu-id="223c1-115">[Приложение Б](appendix-b.md). Константы ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="223c1-115">[Appendix B](appendix-b.md) - Azure RTOS ThreadX constants</span></span>

<span data-ttu-id="223c1-116">[Приложение В](appendix-c.md). Типы данных ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="223c1-116">[Appendix C](appendix-c.md) - Azure RTOS ThreadX data types</span></span>

<span data-ttu-id="223c1-117">[Приложение Г](appendix-d.md). Диаграмма в формате ASCII</span><span class="sxs-lookup"><span data-stu-id="223c1-117">[Appendix D](appendix-d.md) - ASCII chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="223c1-118">Соглашения для руководства</span><span class="sxs-lookup"><span data-stu-id="223c1-118">Guide Conventions</span></span>

<span data-ttu-id="223c1-119">*Курсив* — шрифт, используемый для написания названий книг, выделения важных слов и обозначения параметров.</span><span class="sxs-lookup"><span data-stu-id="223c1-119">*Italics* - typeface denotes book titles, emphasizes important words, and indicates parameters.</span></span>

<span data-ttu-id="223c1-120">**Полужирный** — шрифт, используемый для выделения ключевых слов, констант, имен типов, элементов пользовательского интерфейса, имен переменных и дополнительного выделения важных слов.</span><span class="sxs-lookup"><span data-stu-id="223c1-120">**Boldface** - typeface denotes key words, constants, type names, user interface elements, variable names, and further emphasizes important words.</span></span>

<span data-ttu-id="223c1-121">***Курсив и полужирный*** — шрифт, используемый для обозначения имен файлов и имен функций.</span><span class="sxs-lookup"><span data-stu-id="223c1-121">***Italics and Boldface*** - typeface denotes file names and function names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="223c1-122">Информационные символы привлекают внимание к важной или дополнительной информации, которая может повлиять на производительность или функцию.</span><span class="sxs-lookup"><span data-stu-id="223c1-122">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>

> [!WARNING]
> <span data-ttu-id="223c1-123">Предупреждающие символы привлекают внимание к ситуациям, которых следует избегать, так как они могут привести к неустранимым ошибкам.</span><span class="sxs-lookup"><span data-stu-id="223c1-123">Warning symbols draw attention to situations in which developers should take care to avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-threadx-data-types"></a><span data-ttu-id="223c1-124">Типы данных ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="223c1-124">Azure RTOS ThreadX Data Types</span></span>

<span data-ttu-id="223c1-125">Помимо пользовательских типов данных структуры управления ThreadX для ОСРВ Azure существует ряд специальных типов данных, которые используются в интерфейсах вызова службы ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="223c1-125">In addition to the custom Azure RTOS ThreadX control structure data types, there are a series of special data types that are used in Azure RTOS ThreadX service call interfaces.</span></span> <span data-ttu-id="223c1-126">Эти специальные типы данных сопоставляются непосредственно с типами данных базового компилятора C.</span><span class="sxs-lookup"><span data-stu-id="223c1-126">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="223c1-127">Это делается для обеспечения переносимости между различными компиляторами C.</span><span class="sxs-lookup"><span data-stu-id="223c1-127">This is done to insure portability between different C compilers.</span></span> <span data-ttu-id="223c1-128">Конкретную реализацию можно найти в файле ***tx_port. h***, включенном в источник.</span><span class="sxs-lookup"><span data-stu-id="223c1-128">The exact implementation can be found in the ***tx_port.h*** file included with the source.</span></span>

<span data-ttu-id="223c1-129">Ниже приведен список типов данных вызова службы ThreadX для ОСРВ Azure и их значений.</span><span class="sxs-lookup"><span data-stu-id="223c1-129">The following is a list of Azure RTOS ThreadX service call data types and their associated meanings:</span></span>

| <span data-ttu-id="223c1-130">Тип данных</span><span class="sxs-lookup"><span data-stu-id="223c1-130">Data type</span></span>  | <span data-ttu-id="223c1-131">Описание</span><span class="sxs-lookup"><span data-stu-id="223c1-131">Description</span></span> |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="223c1-132">**UINT**</span><span class="sxs-lookup"><span data-stu-id="223c1-132">**UINT**</span></span> | <span data-ttu-id="223c1-133">Базовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="223c1-133">Basic unsigned integer.</span></span> <span data-ttu-id="223c1-134">Этот тип должен поддерживать 8-разрядные данные без знака. Однако он сопоставлен с наиболее удобным типом данных без знака.</span><span class="sxs-lookup"><span data-stu-id="223c1-134">This type must support 8-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="223c1-135">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="223c1-135">**ULONG**</span></span> | <span data-ttu-id="223c1-136">Длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="223c1-136">Unsigned long type.</span></span> <span data-ttu-id="223c1-137">Этот тип должен поддерживать 32-разрядные данные без знака.</span><span class="sxs-lookup"><span data-stu-id="223c1-137">This type must support 32-bit unsigned data.</span></span> |
| <span data-ttu-id="223c1-138">**VOID**</span><span class="sxs-lookup"><span data-stu-id="223c1-138">**VOID**</span></span> | <span data-ttu-id="223c1-139">Почти всегда эквивалентен типу void компилятора.</span><span class="sxs-lookup"><span data-stu-id="223c1-139">Almost always equivalent to the compiler's void type.</span></span> |
| <span data-ttu-id="223c1-140">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="223c1-140">**CHAR**</span></span> | <span data-ttu-id="223c1-141">Чаще всего это стандартный 8-разрядный символьный тип.</span><span class="sxs-lookup"><span data-stu-id="223c1-141">Most often a standard 8-bit character type.</span></span> |
|  |  |

<span data-ttu-id="223c1-142">В источнике ThreadX для ОСРВ Azure используются дополнительные типы данных.</span><span class="sxs-lookup"><span data-stu-id="223c1-142">Additional data types are used within the Azure RTOS ThreadX source.</span></span> <span data-ttu-id="223c1-143">Они также находятся в файле ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="223c1-143">They are also located in the ***tx_port.h*** file.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="223c1-144">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="223c1-144">Customer Support Center</span></span>

<span data-ttu-id="223c1-145">Если у вас возникли вопросы или требуется помощь при выполнении приведенных здесь шагов, отправьте запрос в службу поддержки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="223c1-145">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="223c1-146">Предоставьте нам следующие сведения в сообщении электронной почты, чтобы мы могли более эффективно решить ваш запрос в службу поддержки:</span><span class="sxs-lookup"><span data-stu-id="223c1-146">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="223c1-147">Подробное описание проблемы, включая частоту возникновения и возможность гарантированного воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="223c1-147">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="223c1-148">Подробное описание любых изменений в приложении и (или) ThreadX для ОСРВ Azure, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="223c1-148">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="223c1-149">Содержимое строки *_tx_version_id* в файле *tx_port.h* вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="223c1-149">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="223c1-150">Эта строка предоставит нам полезную информацию о среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="223c1-150">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="223c1-151">Содержимое в ОЗУ переменной **_tx_build_options** типа **ULONG**.</span><span class="sxs-lookup"><span data-stu-id="223c1-151">The contents in RAM of the **_tx_build_options** **ULONG** variable.</span></span> <span data-ttu-id="223c1-152">Эта переменная предоставит нам сведения о том, как была создана библиотека ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="223c1-152">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
