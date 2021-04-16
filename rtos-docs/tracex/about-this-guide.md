---
title: Руководство пользователя по TraceX в ОСРВ Azure
description: Это руководство содержит исчерпывающие сведения о средстве для системного анализа TraceX для ОСРВ Azure, разработанном корпорацией Майкрософт на базе Microsoft Windows.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 92d886b19a0c67292cd4f6a5f8bd7f9d3106374b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815967"
---
# <a name="about-this-guide"></a><span data-ttu-id="a5cdf-103">Об этом руководстве</span><span class="sxs-lookup"><span data-stu-id="a5cdf-103">About this guide</span></span>

<span data-ttu-id="a5cdf-104">Это руководство содержит исчерпывающие сведения о средстве для системного анализа TraceX для ОСРВ Microsoft Azure на базе Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-104">This guide contains comprehensive information about Azure RTOS TraceX, the Microsoft Windows-based system analysis tool for Microsoft Azure RTOS.</span></span>

<span data-ttu-id="a5cdf-105">Его целевой аудиторией являются разработчики встраиваемого ПО, работающего в реальном времени, которые используют операционную систему реального времени (ОСРВ) Azure, ThreadX для ОСРВ Azure и дополнительные компоненты.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-105">It is intended for the embedded real-time software developer using Azure RTOS ThreadX Real-Time Operating System (RTOS) and add-on components.</span></span> <span data-ttu-id="a5cdf-106">Разработчик должен быть знаком со стандартными понятиями ThreadX, FileX и NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-106">The developer should be familiar with standard Azure RTOS ThreadX Azure RTOS FileX, and Azure RTOS NetX concepts.</span></span>

## <a name="organization"></a><span data-ttu-id="a5cdf-107">План</span><span class="sxs-lookup"><span data-stu-id="a5cdf-107">Organization</span></span>

- <span data-ttu-id="a5cdf-108">[Глава 1](chapter1.md) содержит базовое описание средства TraceX для ОСРВ Azure и его связь с разработкой систем реального времени.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-108">[Chapter 1](chapter1.md) - contains an basic overview of Azure RTOS TraceX and describes its relationship to real-time development.</span></span>
- <span data-ttu-id="a5cdf-109">[Глава 2](chapter2.md) содержит основные шаги по установке и использованию TraceX для ОСРВ Azure для анализа приложения без дополнительной настройки.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-109">[Chapter 2](chapter2.md) - gives the basic steps to install and use Azure RTOS TraceX to analyze your application right out of the box.</span></span>
- <span data-ttu-id="a5cdf-110">[Глава 3](chapter3.md) — описание основных возможностей TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-110">[Chapter 3](chapter3.md) - describes the main features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="a5cdf-111">[Глава 4](chapter4.md) — подробное описание возможностей анализа производительности TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-111">[Chapter 4](chapter4.md) - details performance analysis features of Azure RTOS TraceX.</span></span>
- <span data-ttu-id="a5cdf-112">[Глава 5](chapter5.md) — описание настройки ThreadX, FileX и NetX для ОСРВ Azure, которая позволит создать буфер трассировки для просмотра в TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-112">[Chapter 5](chapter5.md) - describes how to set up Azure RTOS ThreadX, Azure RTOS FileX, and Azure RTOS NetX in order to generate a trace buffer that is viewable by Azure RTOS TraceX.</span></span>
- <span data-ttu-id="a5cdf-113">[Глава 6](chapter6.md) — подробное описание событий TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-113">[Chapter 6](chapter6.md) - describes Azure RTOS TraceX events in detail.</span></span>
- <span data-ttu-id="a5cdf-114">[Глава 7](chapter7.md) — подробное описание событий FileX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-114">[Chapter 7](chapter7.md) - describes Azure RTOS FileX events in detail.</span></span>
- <span data-ttu-id="a5cdf-115">[Глава 8](chapter8.md) — подробное описание событий NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-115">[Chapter 8](chapter8.md) - describes Azure RTOS NetX events in detail.</span></span>
- <span data-ttu-id="a5cdf-116">[Глава 9](chapter9.md) — подробное описание событий USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-116">[Chapter 9](chapter9.md) - describes Azure RTOS USBX events in detail.</span></span>
- <span data-ttu-id="a5cdf-117">[Глава 10](chapter10.md) — подробное описание настраиваемых пользовательских событий.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-117">[Chapter 10](chapter10.md) - describes creating custom user events in detail.</span></span>
- <span data-ttu-id="a5cdf-118">[Глава 11](chapter11.md) — подробное описание внутреннего буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-118">[Chapter 11](chapter11.md) - describes the internal trace buffer in detail.</span></span>
- <span data-ttu-id="a5cdf-119">[Приложение А](appendix-a.md) — файл с зависимостью от реализации ThreadX для ОСРВ Azure, который содержит источник меток времени для сбора событий трассировки.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-119">[Appendix A](appendix-a.md) - Azure RTOS ThreadX port-specific file with its time-stamp source for gathering trace events.</span></span>
- <span data-ttu-id="a5cdf-120">[Приложение Б](appendix-b.md) — файл *tx_trace.h* для ThreadX в ОСРВ Azure, который демонстрирует подробности реализации, имеющие отношение к буферу трассировки событий.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-120">[Appendix B](appendix-b.md) - Azure RTOS ThreadX *tx_trace.h* file that shows implementation details regarding the event trace buffer.</span></span>
- <span data-ttu-id="a5cdf-121">[Приложение В](appendix-c.md) — сводные сведения о средствах командной строки для преобразования разных форматов файлов в допустимые двоичные файлы TraceX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-121">[Appendix C](appendix-c.md) - Summarizes command line utilities for converting various file formats into proper Azure RTOS TraceX binary files.</span></span>
- <span data-ttu-id="a5cdf-122">[Приложение Г](appendix-d.md) — примеры файлов дампа трассировки из разных средств разработки.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-122">[Appendix D](appendix-d.md) - Examples of dumping trace files from various development tools.</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="a5cdf-123">Условные обозначения в руководстве</span><span class="sxs-lookup"><span data-stu-id="a5cdf-123">Guide Conventions</span></span>

<span data-ttu-id="a5cdf-124">*Курсив* используется для написания названий книг, выделения важных слов и обозначения переменных.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-124">*Italics* - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="a5cdf-125">**Полужирным** шрифтом выделены имена файлов и ключевые слова, а также дополнительно выделены важные слова и переменные.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-125">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!NOTE]
> <span data-ttu-id="a5cdf-126">Обозначает информацию, которую нужно принять к сведению.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-126">Indicates information of note.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="a5cdf-127">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="a5cdf-127">Customer Support Center</span></span>

<span data-ttu-id="a5cdf-128">Если у вас возникли вопросы или требуется помощь при выполнении приведенных здесь шагов, отправьте запрос в службу поддержки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-128">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="a5cdf-129">Чтобы мы могли более эффективно решить ваш запрос на поддержку, укажите в сообщении электронной почты следующие сведения:</span><span class="sxs-lookup"><span data-stu-id="a5cdf-129">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="a5cdf-130">Подробное описание проблемы, включая частоту возникновения и действия, позволяющие гарантированно воспроизвести эту проблему (если это возможно).</span><span class="sxs-lookup"><span data-stu-id="a5cdf-130">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="a5cdf-131">Подробное описание любых изменений в приложении и (или) ThreadX для ОСРВ Azure, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-131">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="a5cdf-132">Содержимое строки *_tx_version_id* в файле *tx_port.h* вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-132">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="a5cdf-133">Эта строка предоставит нам полезную информацию о среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-133">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="a5cdf-134">Содержимое в ОЗУ переменной *_tx_build_options* типа ULONG.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-134">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="a5cdf-135">Эта переменная предоставит нам сведения о том, как была создана библиотека ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="a5cdf-135">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
