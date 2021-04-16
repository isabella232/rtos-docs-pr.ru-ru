---
title: Глава 1. Введение в стек устройств USBX для ОСРВ Azure
description: USBX — это полнофункциональный стек USB для глубоко внедренных приложений. В этой главе представлены основные сведения о USBX, в том числе области применения и преимущества.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6965303f1fbf19212b9f7ff20f811a71fb207f54
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816468"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="abf8e-104">Глава 1. Введение в стек устройств USBX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="abf8e-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="abf8e-105">USBX — это полнофункциональный стек USB для глубоко внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="abf8e-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="abf8e-106">В этой главе представлены основные сведения о USBX, в том числе области применения и преимущества.</span><span class="sxs-lookup"><span data-stu-id="abf8e-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="abf8e-107">Возможности USBX</span><span class="sxs-lookup"><span data-stu-id="abf8e-107">USBX features</span></span>

<span data-ttu-id="abf8e-108">USBX поддерживает три существующих спецификации USB: 1.1, 2.0 и OTG.</span><span class="sxs-lookup"><span data-stu-id="abf8e-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="abf8e-109">Он может масштабироваться и адаптироваться к простым топологиям USB только с одним подключенным устройством, а также к сложным топологиям с несколькими устройствами и последовательными концентраторами.</span><span class="sxs-lookup"><span data-stu-id="abf8e-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="abf8e-110">USBX поддерживает все типы передачи данных по протоколам USB: управляющие, пакетные, прерывания и изохронные.</span><span class="sxs-lookup"><span data-stu-id="abf8e-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="abf8e-111">USBX поддерживает работу со стороной узла и устройства.</span><span class="sxs-lookup"><span data-stu-id="abf8e-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="abf8e-112">Каждая сторона включает три уровня:</span><span class="sxs-lookup"><span data-stu-id="abf8e-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="abf8e-113">уровень контроллера;</span><span class="sxs-lookup"><span data-stu-id="abf8e-113">Controller layer</span></span>
- <span data-ttu-id="abf8e-114">уровень стека;</span><span class="sxs-lookup"><span data-stu-id="abf8e-114">Stack layer</span></span>
- <span data-ttu-id="abf8e-115">уровень класса.</span><span class="sxs-lookup"><span data-stu-id="abf8e-115">Class layer</span></span>

<span data-ttu-id="abf8e-116">Отношение между уровнями USB выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="abf8e-116">The relationship between the USB layers is as follows:</span></span>

![Уровни USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="abf8e-118">Особенности продукта</span><span class="sxs-lookup"><span data-stu-id="abf8e-118">Product Highlights</span></span>

- <span data-ttu-id="abf8e-119">Полная поддержка процессора ThreadX.</span><span class="sxs-lookup"><span data-stu-id="abf8e-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="abf8e-120">Отсутствие отчислений.</span><span class="sxs-lookup"><span data-stu-id="abf8e-120">No royalties</span></span>
- <span data-ttu-id="abf8e-121">Полный исходный код ANSI C.</span><span class="sxs-lookup"><span data-stu-id="abf8e-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="abf8e-122">Производительность в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="abf8e-122">Real-time performance</span></span>
- <span data-ttu-id="abf8e-123">Быстрая техническая поддержка.</span><span class="sxs-lookup"><span data-stu-id="abf8e-123">Responsive technical support</span></span>
- <span data-ttu-id="abf8e-124">Поддержка нескольких классов.</span><span class="sxs-lookup"><span data-stu-id="abf8e-124">Multiple class support</span></span>
- <span data-ttu-id="abf8e-125">Несколько экземпляров классов.</span><span class="sxs-lookup"><span data-stu-id="abf8e-125">Multiple class instances</span></span>
- <span data-ttu-id="abf8e-126">Интеграция классов со ThreadX, FileX и NetX.</span><span class="sxs-lookup"><span data-stu-id="abf8e-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="abf8e-127">Поддержка USB-устройств с несколькими конфигурациями.</span><span class="sxs-lookup"><span data-stu-id="abf8e-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="abf8e-128">Поддержка составных USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="abf8e-128">Support for USB composite devices</span></span>
- <span data-ttu-id="abf8e-129">Поддержка управления питанием по USB.</span><span class="sxs-lookup"><span data-stu-id="abf8e-129">Support for USB power management</span></span>
- <span data-ttu-id="abf8e-130">Поддержка OTG в USB.</span><span class="sxs-lookup"><span data-stu-id="abf8e-130">Support for USB OTG</span></span>
- <span data-ttu-id="abf8e-131">Экспорт событий трассировки для TraceX.</span><span class="sxs-lookup"><span data-stu-id="abf8e-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="abf8e-132">Мощные службы USBX</span><span class="sxs-lookup"><span data-stu-id="abf8e-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="abf8e-133">Полная поддержка структуры USB-устройств</span><span class="sxs-lookup"><span data-stu-id="abf8e-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="abf8e-134">USBX может поддерживать самые требовательные USB-устройства, в том числе с несколькими конфигурациями, несколькими интерфейсами и несколькими альтернативными параметрами.</span><span class="sxs-lookup"><span data-stu-id="abf8e-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="abf8e-135">Простые в использовании API</span><span class="sxs-lookup"><span data-stu-id="abf8e-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="abf8e-136">USBX предоставляет лучший глубоко внедренный стек USB, который при этом легко изучить и использовать.</span><span class="sxs-lookup"><span data-stu-id="abf8e-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="abf8e-137">API USBX обеспечивает интуитивную простоту и согласованность при работе со службами.</span><span class="sxs-lookup"><span data-stu-id="abf8e-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="abf8e-138">Благодаря предоставляемым API классов USBX пользовательскому приложению не требуется учитывать особенности протоколов USB.</span><span class="sxs-lookup"><span data-stu-id="abf8e-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
