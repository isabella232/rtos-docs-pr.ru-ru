---
title: Сведения о руководстве пользователя по NetX Duo в ОСРВ Azure
description: Это руководство содержит исчерпывающие сведения NetX Duo в ОСРВ Azure, высокопроизводительном двойном сетевом стеке IPv4/IPv6 от корпорации Майкрософт.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b1eef5bfa28f13d7a6b627792f96039b252f2355
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814879"
---
# <a name="about-the-azure-rtos-netx-duo-user-guide"></a><span data-ttu-id="02f5a-103">Сведения о руководстве пользователя по NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="02f5a-103">About The Azure RTOS NetX Duo User Guide</span></span>

<span data-ttu-id="02f5a-104">Это руководство содержит исчерпывающие сведения NetX Duo в ОСРВ Azure, высокопроизводительном двойном сетевом стеке IPv4/IPv6 от корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="02f5a-104">This guide contains comprehensive information about Azure RTOS NetX Duo, the Microsoft high-performance IPv4/IPv6 dual network stack.</span></span> 

<span data-ttu-id="02f5a-105">Оно предназначено для разработчиков встроенного программного обеспечения реального времени, знакомых с основными принципами работы сетей, ThreadX в ОСРВ Azure и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="02f5a-105">It is intended for embedded real-time software developers familiar with basic networking concepts, Azure RTOS ThreadX, and the C programming language.</span></span>

## <a name="organization"></a><span data-ttu-id="02f5a-106">План</span><span class="sxs-lookup"><span data-stu-id="02f5a-106">Organization</span></span>

<span data-ttu-id="02f5a-107">[Глава 1](chapter1.md) знакомит нас с NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="02f5a-107">[Chapter 1](chapter1.md) - Introduces Azure RTOS NetX Duo</span></span>

<span data-ttu-id="02f5a-108">[Глава 2](chapter2.md) содержит основные шаги по установке и использованию NetX Duo для ОСРВ Azure с приложением ThreadX.</span><span class="sxs-lookup"><span data-stu-id="02f5a-108">[Chapter 2](chapter2.md) - Gives the basic steps to install and use Azure RTOS NetX Duo with your ThreadX application</span></span>

<span data-ttu-id="02f5a-109">[Глава 3](chapter3.md) предоставляет описание возможностей системы NetX Duo для ОСРВ Azure и базовые сведения о сетевых стандартах TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="02f5a-109">[Chapter 3](chapter3.md) - Provides a functional overview of the Azure RTOS NetX Duo system and basic information about the TCP/IP networking standards</span></span>

<span data-ttu-id="02f5a-110">[Глава 4](chapter4.md) подробно описывает интерфейс между приложением и NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="02f5a-110">[Chapter 4](chapter4.md) - Details the application's interface to Azure RTOS NetX Duo</span></span>

<span data-ttu-id="02f5a-111">[Глава 5](chapter5.md) описывает сетевые драйверы для NetX Duo в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="02f5a-111">[Chapter 5](chapter5.md) - Describes network drivers for Azure RTOS NetX Duo</span></span>

<span data-ttu-id="02f5a-112">[Приложение А](appendix-a.md). Службы NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="02f5a-112">[Appendix A](appendix-a.md) - Azure RTOS NetX Duo Services</span></span>

<span data-ttu-id="02f5a-113">[Приложение B](appendix-b.md). Константы NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="02f5a-113">[Appendix B](appendix-b.md) - Azure RTOS NetX Duo Constants</span></span>

<span data-ttu-id="02f5a-114">[Приложение C](appendix-c.md). Типы данных NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="02f5a-114">[Appendix C](appendix-c.md) - Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="02f5a-115">[Приложение D](appendix-d.md). API сокета, совместимого с BSD</span><span class="sxs-lookup"><span data-stu-id="02f5a-115">[Appendix D](appendix-d.md) - BSD-Compatible Socket API</span></span>

<span data-ttu-id="02f5a-116">[Приложение E](appendix-e.md). Таблица ASCII</span><span class="sxs-lookup"><span data-stu-id="02f5a-116">[Appendix E](appendix-e.md) - ASCII Chart</span></span>

## <a name="guide-conventions"></a><span data-ttu-id="02f5a-117">Условные обозначения в руководстве</span><span class="sxs-lookup"><span data-stu-id="02f5a-117">Guide Conventions</span></span>

<span data-ttu-id="02f5a-118">Курсивом выделены заголовки книг, важные слова и обозначения переменных.</span><span class="sxs-lookup"><span data-stu-id="02f5a-118">Italics - Typeface denotes book titles, emphasizes important words, and indicates variables.</span></span>

<span data-ttu-id="02f5a-119">**Полужирным** шрифтом выделены имена файлов и ключевые слова, а также дополнительно выделены важные слова и переменные.</span><span class="sxs-lookup"><span data-stu-id="02f5a-119">**Boldface** - Typeface denotes file names, key words, and further emphasizes important words and variables.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02f5a-120">Информационные символы указывают на важные или дополнительные сведения, связанные с производительностью или работой функции.</span><span class="sxs-lookup"><span data-stu-id="02f5a-120">Information symbols draw attention to important or additional information that could affect performance or function.</span></span>
 
> [!WARNING]
> <span data-ttu-id="02f5a-121">Предупреждающие символы указывают на сценарии, которых следует избегать, так как они могут привести к неустранимым ошибкам.</span><span class="sxs-lookup"><span data-stu-id="02f5a-121">Warning symbols draw attention to situations that developers should avoid because they could cause fatal errors.</span></span>

## <a name="azure-rtos-netx-duo-data-types"></a><span data-ttu-id="02f5a-122">Типы данных NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="02f5a-122">Azure RTOS NetX Duo Data Types</span></span>

<span data-ttu-id="02f5a-123">Помимо пользовательских типов данных структур управления NetX Duo для ОСРВ Azure, есть ряд специальных типов данных, которые используются в интерфейсах вызова служб NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="02f5a-123">In addition to the custom Azure RTOS NetX Duo control structure data types, there are several special data types that are used in Azure RTOS NetX Duo service call interfaces.</span></span> <span data-ttu-id="02f5a-124">Эти специальные типы данных сопоставляются непосредственно с типами данных базового компилятора C.</span><span class="sxs-lookup"><span data-stu-id="02f5a-124">These special data types map directly to data types of the underlying C compiler.</span></span> <span data-ttu-id="02f5a-125">Это необходимо для обеспечения переносимости кода между разными компиляторами C.</span><span class="sxs-lookup"><span data-stu-id="02f5a-125">This is done to ensure portability between different C compilers.</span></span> <span data-ttu-id="02f5a-126">Конкретная реализация наследуется от ThreadX и представлена в файле ***tx_port.h***, включенном в состав дистрибутива ThreadX.</span><span class="sxs-lookup"><span data-stu-id="02f5a-126">The exact implementation is inherited from ThreadX and can be found in the ***tx_port.h*** file included in the ThreadX distribution.</span></span>

<span data-ttu-id="02f5a-127">Ниже приведен список типов данных вызова служб NetX Duo для ОСРВ Azure и их значений.</span><span class="sxs-lookup"><span data-stu-id="02f5a-127">The following is a list of Azure RTOS NetX Duo service call data types and their associated meanings:</span></span>

<span data-ttu-id="02f5a-128">**UINT**: простое целое число без знака</span><span class="sxs-lookup"><span data-stu-id="02f5a-128">**UINT**: Basic unsigned integer.</span></span> <span data-ttu-id="02f5a-129">Этот тип должен поддерживать 32-разрядные данные без знака, но свободно сопоставляется с наиболее удобным типом данных без знака.</span><span class="sxs-lookup"><span data-stu-id="02f5a-129">This type must support 32-bit unsigned data; however, it is mapped to the most convenient unsigned data type.</span></span>  
<span data-ttu-id="02f5a-130">**ULONG**: длинное целое число без знака</span><span class="sxs-lookup"><span data-stu-id="02f5a-130">**ULONG**: Unsigned long type.</span></span> <span data-ttu-id="02f5a-131">Этот тип должен поддерживать 32-разрядные данные без знака.</span><span class="sxs-lookup"><span data-stu-id="02f5a-131">This type must support 32-bit unsigned  data.</span></span>
<span data-ttu-id="02f5a-132">**VOID**: почти всегда эквивалентен типу void компилятора</span><span class="sxs-lookup"><span data-stu-id="02f5a-132">**VOID**: Almost always equivalent to the compiler's void type.</span></span>  
<span data-ttu-id="02f5a-133">**CHAR**: чаще всего это стандартный 8-разрядный символьный тип</span><span class="sxs-lookup"><span data-stu-id="02f5a-133">**CHAR**: Most often a standard 8-bit character type.</span></span>  

<span data-ttu-id="02f5a-134">В исходном коде NetX Duo для ОСРВ Azure используются дополнительные типы данных.</span><span class="sxs-lookup"><span data-stu-id="02f5a-134">Additional data types are used within the Azure RTOS NetX Duo source.</span></span> <span data-ttu-id="02f5a-135">Они находятся в файлах \***tx_port.h** _ или _ \*_nx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="02f5a-135">They are located in either the ***tx_port.h** _ or _ *_nx_port.h_** files.</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="02f5a-136">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="02f5a-136">Customer Support Center</span></span>

<span data-ttu-id="02f5a-137">Если у вас возникли вопросы или требуется помощь при выполнении приведенных здесь шагов, отправьте запрос в службу поддержки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="02f5a-137">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="02f5a-138">Чтобы мы могли более эффективно решить ваш запрос на поддержку, укажите в сообщении электронной почты следующие сведения.</span><span class="sxs-lookup"><span data-stu-id="02f5a-138">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="02f5a-139">Подробное описание проблемы, включая частоту ее возникновения и возможность воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="02f5a-139">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="02f5a-140">Подробное описание любых изменений в приложении и (или) NetX Duo для ОСРВ Azure, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="02f5a-140">A detailed description of any changes to the application and/or Azure RTOS NetX Duo that preceded the problem.</span></span>
3. <span data-ttu-id="02f5a-141">Содержимое строк _tx_version_id и _nx_version_id из файлов tx_port.h_ и _nx_port.h вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="02f5a-141">The contents of the _tx_version_id and _nx_version_id strings found in the tx_port.h and nx_port.h files of your distribution.</span></span> <span data-ttu-id="02f5a-142">Эти строки предоставят нам полезную информацию о вашей среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="02f5a-142">These strings will provide us valuable information regarding your run- time environment.</span></span>
4. <span data-ttu-id="02f5a-143">Содержимое ОЗУ для следующих переменных ULONG</span><span class="sxs-lookup"><span data-stu-id="02f5a-143">The contents in RAM of the following ULONG variables:</span></span>

    <span data-ttu-id="02f5a-144">**_tx_build_options**</span><span class="sxs-lookup"><span data-stu-id="02f5a-144">**_tx_build_options**</span></span>

    <span data-ttu-id="02f5a-145">**_nx_system_build_options1**</span><span class="sxs-lookup"><span data-stu-id="02f5a-145">**_nx_system_build_options1**</span></span>

    <span data-ttu-id="02f5a-146">**_nx_system_build_options2**</span><span class="sxs-lookup"><span data-stu-id="02f5a-146">**_nx_system_build_options2**</span></span>

    <span data-ttu-id="02f5a-147">**_nx_system_build_options3**</span><span class="sxs-lookup"><span data-stu-id="02f5a-147">**_nx_system_build_options3**</span></span>

    <span data-ttu-id="02f5a-148">**_nx_system_build_options4**</span><span class="sxs-lookup"><span data-stu-id="02f5a-148">**_nx_system_build_options4**</span></span>

    <span data-ttu-id="02f5a-149">**_nx_system_build_options5**</span><span class="sxs-lookup"><span data-stu-id="02f5a-149">**_nx_system_build_options5**</span></span>

    <span data-ttu-id="02f5a-150">Эти переменные позволят нам узнать, как были созданы библиотеки ThreadX и NetX Duo для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="02f5a-150">These variables will give us information on how your Azure RTOS ThreadX and Azure RTOS NetX Duo libraries were built.</span></span>

5. <span data-ttu-id="02f5a-151">Буфер трассировки, записанный сразу после обнаружения проблемы.</span><span class="sxs-lookup"><span data-stu-id="02f5a-151">A trace buffer captured immediately after the problem was detected.</span></span> <span data-ttu-id="02f5a-152">Для этого необходимо выполнить сборку библиотек ThreadX и NetX Duo для ОСРВ Azure с параметром TX_ENABLE_EVENT_TRACE и вызвать службу tx_trace_enable, указав данные буфера трассировки.</span><span class="sxs-lookup"><span data-stu-id="02f5a-152">This is accomplished by building the Azure RTOS ThreadX and Azure RTOS NetX Duo libraries with TX_ENABLE_EVENT_TRACE and calling tx_trace_enable with the trace buffer information.</span></span>
