---
title: Сведения о руководстве пользователя по NetX в ОСРВ Azure
description: Это руководство содержит исчерпывающие сведения о высокопроизводительном сетевом стеке NetX в ОСРВ Azure, созданном корпорацией Майкрософт.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8e1c23892c4360ddc8783b04ae8f23e371899f1d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815332"
---
# <a name="about-the-azure-rtos-netx-user-guide"></a><span data-ttu-id="489dd-103">Сведения о руководстве пользователя по NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="489dd-103">About The Azure RTOS NetX User Guide</span></span>

<span data-ttu-id="489dd-104">Это руководство содержит исчерпывающие сведения о высокопроизводительном сетевом стеке NetX в ОСРВ Azure, созданном корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="489dd-104">This guide contains comprehensive information about Azure RTOS NetX, the Microsoft high-performance network stack.</span></span>

<span data-ttu-id="489dd-105">Оно предназначено для разработчиков встроенного программного обеспечения реального времени, знакомых с основными принципами работы сетей, ThreadX в ОСРВ Azure и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="489dd-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="489dd-106">План</span><span class="sxs-lookup"><span data-stu-id="489dd-106">Organization</span></span>

<span data-ttu-id="489dd-107">[Глава 1](chapter1.md) — ознакомительные сведения о NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX</span></span>

<span data-ttu-id="489dd-108">[Глава 2](chapter2.md) — описание основных действий по установке и использованию NetX для ОСРВ Azure с приложением ThreadX.</span><span class="sxs-lookup"><span data-stu-id="489dd-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX with your ThreadX application.</span></span>

<span data-ttu-id="489dd-109">[Глава 3](chapter3.md) — описание возможностей системы NetX для ОСРВ Azure и базовые сведения о сетевых стандартах TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="489dd-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX system and basic information about the TCP/IP networking standards.</span></span>

<span data-ttu-id="489dd-110">[Глава 4](chapter4.md) — подробные сведения об интерфейсе между приложением и NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX.</span></span>

<span data-ttu-id="489dd-111">[Глава 5](chapter5.md) — описание сетевых драйверов для NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX.</span></span>

<span data-ttu-id="489dd-112">[Приложение А](appendix-a.md) — службы NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Services</span></span>

<span data-ttu-id="489dd-113">[Приложение Б](appendix-b.md) — константы NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Constants</span></span>

<span data-ttu-id="489dd-114">[Приложение В](appendix-c.md) — типы данных NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="489dd-115">[Приложение Г](appendix-d.md) — API сокета, совместимого с BSD.</span><span class="sxs-lookup"><span data-stu-id="489dd-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="489dd-116">[Приложение Д](appendix-e.md) — таблица ASCII.</span><span class="sxs-lookup"><span data-stu-id="489dd-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="azure-rtos-netx-data-types"></a><span data-ttu-id="489dd-117">Типы данных NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="489dd-117">Azure RTOS NetX Data Types</span></span>

<span data-ttu-id="489dd-118">Помимо пользовательских типов данных структур управления NetX для ОСРВ Azure, есть ряд специальных типов данных, которые используются в интерфейсах вызова служб NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-118">In addition to the custom Azure RTOS NetX control structure data types, there are several special data types that are used in Azure RTOS NetX service call interfaces.</span></span> <span data-ttu-id="489dd-119">Эти специальные типы данных сопоставляются непосредственно с типами данных базового компилятора C.</span><span class="sxs-lookup"><span data-stu-id="489dd-119">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="489dd-120">Это необходимо для обеспечения переносимости кода между разными компиляторами C.</span><span class="sxs-lookup"><span data-stu-id="489dd-120">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="489dd-121">Конкретная реализация наследуется от ThreadX и представлена в файле ***tx_port.h***, включенном в состав дистрибутива ThreadX.</span><span class="sxs-lookup"><span data-stu-id="489dd-121">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="489dd-122">Ниже приведен список типов данных вызова служб NetX для ОСРВ Azure и их значений.</span><span class="sxs-lookup"><span data-stu-id="489dd-122">The following is a list of Azure RTOS NetX service call data types and their associated meanings:</span></span>

| <!-- -->    | <!-- -->    |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="489dd-123">**UINT**</span><span class="sxs-lookup"><span data-stu-id="489dd-123">**UINT**</span></span>  | <span data-ttu-id="489dd-124">Простое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="489dd-124">Basic unsigned integer.</span></span> <span data-ttu-id="489dd-125">Этот тип должен поддерживать 32-разрядные данные без знака, но свободно сопоставляется с наиболее удобным типом данных без знака.</span><span class="sxs-lookup"><span data-stu-id="489dd-125">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span> |
| <span data-ttu-id="489dd-126">**ULONG**</span><span class="sxs-lookup"><span data-stu-id="489dd-126">**ULONG**</span></span> | <span data-ttu-id="489dd-127">Длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="489dd-127">Unsigned long type.</span></span> <span data-ttu-id="489dd-128">Этот тип должен поддерживать 32-разрядные данные без знака.</span><span class="sxs-lookup"><span data-stu-id="489dd-128">This type must support 32-bit unsigned data.</span></span>                                                                      |
| <span data-ttu-id="489dd-129">**VOID**</span><span class="sxs-lookup"><span data-stu-id="489dd-129">**VOID**</span></span>  | <span data-ttu-id="489dd-130">Почти всегда эквивалентен типу void компилятора.</span><span class="sxs-lookup"><span data-stu-id="489dd-130">Almost always equivalent to the compiler's void type.</span></span>                                                                                 |
| <span data-ttu-id="489dd-131">**CHAR**</span><span class="sxs-lookup"><span data-stu-id="489dd-131">**CHAR**</span></span>  | <span data-ttu-id="489dd-132">Чаще всего это стандартный 8-разрядный символьный тип.</span><span class="sxs-lookup"><span data-stu-id="489dd-132">Most often a standard 8-bit character type.</span></span>                                                                                           |

<span data-ttu-id="489dd-133">В исходном коде NetX для ОСРВ Azure используются дополнительные типы данных.</span><span class="sxs-lookup"><span data-stu-id="489dd-133">Additional data types are used within the Azure RTOS NetX source.</span></span> <span data-ttu-id="489dd-134">Они находятся в файлах \***tx_port.h** _ или _ \*_nx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="489dd-134">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="489dd-135">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="489dd-135">Customer Support Center</span></span>

<span data-ttu-id="489dd-136">Если у вас возникли вопросы или вам требуется помощь при выполнении описанных здесь действий, отправьте запрос в службу поддержки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-136">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="489dd-137">Предоставьте нам следующие сведения в сообщении электронной почты, чтобы мы могли более эффективно отреагировать на ваш запрос в службу поддержки:</span><span class="sxs-lookup"><span data-stu-id="489dd-137">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="489dd-138">Подробное описание проблемы, включая частоту возникновения и действия, позволяющие гарантированно воспроизвести эту проблему (если это возможно).</span><span class="sxs-lookup"><span data-stu-id="489dd-138">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>

2. <span data-ttu-id="489dd-139">Подробное описание любых изменений в приложении и (или) NetX для ОСРВ Azure, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="489dd-139">A detailed description of any changes to the application and/or Azure RTOS NetX that preceded the problem.</span></span>

3. <span data-ttu-id="489dd-140">Содержимое строк **_tx_version_id** и **_nx_version_id** из файлов **_tx_port.h_ *_ и _* _nx_port.h_** вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="489dd-140">The contents of the **_tx_version_id** and **_nx_version_id** strings found in the **_tx_port.h_*_ and _*_nx_port.h_** files of your distribution.</span></span> <span data-ttu-id="489dd-141">Эти строки предоставят нам полезную информацию о вашей среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="489dd-141">These strings will provide us valuable information regarding your run-time environment.</span></span>

4. <span data-ttu-id="489dd-142">Содержимое ОЗУ для следующих переменных **ULONG**:</span><span class="sxs-lookup"><span data-stu-id="489dd-142">The contents in RAM of the following **ULONG** variables:</span></span>

    <span data-ttu-id="489dd-143">**_tx_build_options**;</span><span class="sxs-lookup"><span data-stu-id="489dd-143">**_tx_build_options**</span></span>

    <span data-ttu-id="489dd-144">**_nx_system_build_options1**;</span><span class="sxs-lookup"><span data-stu-id="489dd-144">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="489dd-145">**_nx_system_build_options2**;</span><span class="sxs-lookup"><span data-stu-id="489dd-145">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="489dd-146">**_nx_system_build_options3**;</span><span class="sxs-lookup"><span data-stu-id="489dd-146">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="489dd-147">**_nx_system_build_options4**;</span><span class="sxs-lookup"><span data-stu-id="489dd-147">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="489dd-148">**_nx_system_build_options5**.</span><span class="sxs-lookup"><span data-stu-id="489dd-148">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="489dd-149">Эти переменные позволят нам узнать, как были созданы библиотеки ThreadX и NetX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-149">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX libraries were built.</span></span>

5. <span data-ttu-id="489dd-150">Буфер трассировки, записанный сразу после обнаружения проблемы.</span><span class="sxs-lookup"><span data-stu-id="489dd-150">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="489dd-151">Для этого необходимо скомпилировать библиотеки ThreadX и NetX для ОСРВ Azure с параметром **TX_ENABLE_EVENT_TRACE** и вызвать службу **tx_trace_enable**, указав данные буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="489dd-151">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX libraries with **TX_ENABLE_EVENT_TRACE** and calling **tx_trace_enable** with the trace buffer information.</span></span> <span data-ttu-id="489dd-152">Дополнительные сведения см. в руководстве пользователя по ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="489dd-152">Refer to the Azure RTOS TraceX User Guide for details.</span></span>
