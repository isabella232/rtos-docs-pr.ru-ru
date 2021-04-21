---
title: Глава 1. Введение в стек устройств USBX для ОСРВ Azure
description: USBX — это полнофункциональный стек USB для глубоко встраиваемых приложений. В этой главе представлены основные сведения об USBX, в том числе о его преимуществах и области применения.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8b1e08130d4531fd82629378761cd5b1752f0a07
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550292"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-device-stack"></a><span data-ttu-id="2d6b1-104">Глава 1. Введение в стек устройств USBX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2d6b1-104">Chapter 1 - Introduction to Azure RTOS USBX Device Stack</span></span>

<span data-ttu-id="2d6b1-105">USBX — это полнофункциональный стек USB для глубоко внедренных приложений.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="2d6b1-106">В этой главе представлены основные сведения о USBX, в том числе области применения и преимущества.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-106">This chapter introduces USBX, describing its applications and benefits</span></span> 

## <a name="usbx-features"></a><span data-ttu-id="2d6b1-107">Возможности USBX</span><span class="sxs-lookup"><span data-stu-id="2d6b1-107">USBX features</span></span>

<span data-ttu-id="2d6b1-108">USBX поддерживает три существующих спецификации USB: 1.1, 2.0 и OTG.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-108">USBX supports the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="2d6b1-109">Он может масштабироваться и адаптироваться к простым топологиям USB только с одним подключенным устройством, а также к сложным топологиям с несколькими устройствами и последовательными концентраторами.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="2d6b1-110">USBX поддерживает все типы передачи данных по протоколам USB: контролируемая, пакетная, прерываемая и изохронная.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="2d6b1-111">USBX поддерживает работу со стороной узла и устройства.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="2d6b1-112">Каждая сторона включает три уровня:</span><span class="sxs-lookup"><span data-stu-id="2d6b1-112">Each side is composed of three layers.</span></span>

- <span data-ttu-id="2d6b1-113">уровень контроллера;</span><span class="sxs-lookup"><span data-stu-id="2d6b1-113">Controller layer</span></span>
- <span data-ttu-id="2d6b1-114">уровень стека;</span><span class="sxs-lookup"><span data-stu-id="2d6b1-114">Stack layer</span></span>
- <span data-ttu-id="2d6b1-115">уровень класса.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-115">Class layer</span></span>

<span data-ttu-id="2d6b1-116">Отношение между уровнями USB выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2d6b1-116">The relationship between the USB layers is as follows:</span></span>

![Уровни USB](media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="2d6b1-118">Особенности продукта</span><span class="sxs-lookup"><span data-stu-id="2d6b1-118">Product Highlights</span></span>

- <span data-ttu-id="2d6b1-119">Полная поддержка процессора ThreadX.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="2d6b1-120">Отсутствие лицензионных отчислений.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-120">No royalties</span></span>
- <span data-ttu-id="2d6b1-121">Полный исходный код ANSI C.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="2d6b1-122">Производительность в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-122">Real-time performance</span></span>
- <span data-ttu-id="2d6b1-123">Быстрая техническая поддержка.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-123">Responsive technical support</span></span>
- <span data-ttu-id="2d6b1-124">Поддержка нескольких классов.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-124">Multiple class support</span></span>
- <span data-ttu-id="2d6b1-125">Несколько экземпляров классов.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-125">Multiple class instances</span></span>
- <span data-ttu-id="2d6b1-126">Интеграция классов со ThreadX, FileX и NetX.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-126">Integration of classes with ThreadX, FileX, and NetX</span></span>
- <span data-ttu-id="2d6b1-127">Поддержка USB-устройств с несколькими конфигурациями.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-127">Support for USB devices with multiple configurations</span></span>
- <span data-ttu-id="2d6b1-128">Поддержка составных USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-128">Support for USB composite devices</span></span>
- <span data-ttu-id="2d6b1-129">Поддержка управления питанием по USB.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-129">Support for USB power management</span></span>
- <span data-ttu-id="2d6b1-130">Поддержка OTG в USB.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-130">Support for USB OTG</span></span>
- <span data-ttu-id="2d6b1-131">Экспорт событий трассировки для TraceX.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-131">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="2d6b1-132">Мощные службы USBX</span><span class="sxs-lookup"><span data-stu-id="2d6b1-132">Powerful Services of USBX</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="2d6b1-133">Полная поддержка структуры USB-устройств</span><span class="sxs-lookup"><span data-stu-id="2d6b1-133">Complete USB Device Framework Support</span></span>

<span data-ttu-id="2d6b1-134">USBX может поддерживать самые требовательные USB-устройства, в том числе с несколькими конфигурациями, несколькими интерфейсами и несколькими альтернативными параметрами.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-134">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="2d6b1-135">Простые в использовании API</span><span class="sxs-lookup"><span data-stu-id="2d6b1-135">Easy-To-Use APIs</span></span>

<span data-ttu-id="2d6b1-136">USBX предоставляет лучший глубоко внедренный стек USB, который при этом легко изучить и использовать.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-136">USBX provides the best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="2d6b1-137">API USBX обеспечивает интуитивную простоту и согласованность при работе со службами.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-137">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="2d6b1-138">Благодаря предоставляемым API классов USBX пользовательскому приложению не требуется учитывать особенности протоколов USB.</span><span class="sxs-lookup"><span data-stu-id="2d6b1-138">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
