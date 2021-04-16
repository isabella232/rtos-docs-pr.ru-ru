---
title: Глава 1. Введение в стек узла USBX для ОСРВ Azure
description: USBX — это полнофункциональный стек USB для глубоко встраиваемых приложений. В этой главе представлены основные сведения об USBX, в том числе области применения и преимущества.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ee49903e764e20316438be16b47d2d9208b1363
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816416"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="e2974-104">Глава 1. Введение в стек узла USBX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="e2974-104">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="e2974-105">USBX — это полнофункциональный стек USB для глубоко встраиваемых приложений.</span><span class="sxs-lookup"><span data-stu-id="e2974-105">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="e2974-106">В этой главе представлены основные сведения об USBX, в том числе области применения и преимущества.</span><span class="sxs-lookup"><span data-stu-id="e2974-106">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="e2974-107">Возможности USBX</span><span class="sxs-lookup"><span data-stu-id="e2974-107">USBX features</span></span>

<span data-ttu-id="e2974-108">USBX поддерживает три существующих спецификации USB: 1.1, 2.0 и OTG.</span><span class="sxs-lookup"><span data-stu-id="e2974-108">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="e2974-109">Он может масштабироваться и адаптироваться к простым топологиям USB только с одним подключенным устройством, а также к сложным топологиям с несколькими устройствами и каскадной схемой соединения концентраторов.</span><span class="sxs-lookup"><span data-stu-id="e2974-109">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="e2974-110">USBX поддерживает все типы передачи данных по протоколам USB: контролируемая, пакетная, прерываемая и изохронная.</span><span class="sxs-lookup"><span data-stu-id="e2974-110">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="e2974-111">USBX поддерживает работу со стороной узла и устройства.</span><span class="sxs-lookup"><span data-stu-id="e2974-111">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="e2974-112">Каждая сторона включает три уровня:</span><span class="sxs-lookup"><span data-stu-id="e2974-112">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="e2974-113">уровень контроллера;</span><span class="sxs-lookup"><span data-stu-id="e2974-113">Controller layer</span></span>
- <span data-ttu-id="e2974-114">уровень стека;</span><span class="sxs-lookup"><span data-stu-id="e2974-114">Stack layer</span></span>
- <span data-ttu-id="e2974-115">уровень класса.</span><span class="sxs-lookup"><span data-stu-id="e2974-115">Class layer</span></span>

<span data-ttu-id="e2974-116">Связь между уровнями USB строится следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e2974-116">The relationship between the USB layers is as follows.</span></span>

![Уровни USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="e2974-118">Особенности продуктов</span><span class="sxs-lookup"><span data-stu-id="e2974-118">Product Highlights</span></span>

- <span data-ttu-id="e2974-119">Полная поддержка процессора ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e2974-119">Complete ThreadX processor support</span></span>
- <span data-ttu-id="e2974-120">Отсутствие лицензионных отчислений.</span><span class="sxs-lookup"><span data-stu-id="e2974-120">No royalties</span></span>
- <span data-ttu-id="e2974-121">Полный исходный код ANSI C.</span><span class="sxs-lookup"><span data-stu-id="e2974-121">Complete ANSI C source code</span></span>
- <span data-ttu-id="e2974-122">Производительность в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="e2974-122">Real-time performance</span></span>
- <span data-ttu-id="e2974-123">Быстрая техническая поддержка.</span><span class="sxs-lookup"><span data-stu-id="e2974-123">Responsive technical support</span></span>
- <span data-ttu-id="e2974-124">Поддержка нескольких контроллеров узла.</span><span class="sxs-lookup"><span data-stu-id="e2974-124">Multiple host controller support</span></span>
- <span data-ttu-id="e2974-125">Поддержка нескольких классов.</span><span class="sxs-lookup"><span data-stu-id="e2974-125">Multiple class support</span></span>
- <span data-ttu-id="e2974-126">Несколько экземпляров классов.</span><span class="sxs-lookup"><span data-stu-id="e2974-126">Multiple class instances</span></span>
- <span data-ttu-id="e2974-127">Интеграция классов со ThreadX, FileX и NetX.</span><span class="sxs-lookup"><span data-stu-id="e2974-127">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="e2974-128">Поддержка USB-устройств с несколькими конфигурациями.</span><span class="sxs-lookup"><span data-stu-id="e2974-128">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="e2974-129">Поддержка составных USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="e2974-129">Support for USB composite devices</span></span>
- <span data-ttu-id="e2974-130">Поддержка каскадной схемы соединения концентраторов.</span><span class="sxs-lookup"><span data-stu-id="e2974-130">Support for cascading hubs</span></span>
- <span data-ttu-id="e2974-131">Поддержка управления питанием по USB.</span><span class="sxs-lookup"><span data-stu-id="e2974-131">Support for USB power management</span></span>
- <span data-ttu-id="e2974-132">Поддержка OTG в USB.</span><span class="sxs-lookup"><span data-stu-id="e2974-132">Support for USB OTG</span></span>
- <span data-ttu-id="e2974-133">Экспорт событий трассировки для TraceX.</span><span class="sxs-lookup"><span data-stu-id="e2974-133">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="e2974-134">Мощные службы USBX.</span><span class="sxs-lookup"><span data-stu-id="e2974-134">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="e2974-135">Поддержка нескольких контроллеров узла.</span><span class="sxs-lookup"><span data-stu-id="e2974-135">Multiple Host Controller Support</span></span>

<span data-ttu-id="e2974-136">USBX может поддерживать одновременную работу нескольких хост-контроллеров USB.</span><span class="sxs-lookup"><span data-stu-id="e2974-136">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="e2974-137">Благодаря этой возможности USBX поддерживает стандарт USB 2.0 по схеме обратной совместимости, которая используется большинством хост-контроллеров USB 2.0, представленных на современном рынке.</span><span class="sxs-lookup"><span data-stu-id="e2974-137">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="e2974-138">Программный планировщик USB</span><span class="sxs-lookup"><span data-stu-id="e2974-138">USB Software Scheduler</span></span>

<span data-ttu-id="e2974-139">USBX включает программный планировщик USB, который требуется для поддержки контроллеров USB без обработки списка оборудования.</span><span class="sxs-lookup"><span data-stu-id="e2974-139">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="e2974-140">Программный планировщик USBX организует передачу данных по USB с нужной частотой служб и приоритетами, а также подает контроллеру USB команды на выполнение передачи данных.</span><span class="sxs-lookup"><span data-stu-id="e2974-140">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="e2974-141">Полная поддержка структуры USB-устройств</span><span class="sxs-lookup"><span data-stu-id="e2974-141">Complete USB Device Framework Support</span></span>

<span data-ttu-id="e2974-142">USBX может поддерживать самые требовательные USB-устройства, в том числе с несколькими конфигурациями, несколькими интерфейсами и несколькими альтернативными параметрами.</span><span class="sxs-lookup"><span data-stu-id="e2974-142">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="e2974-143">Простые в использовании API</span><span class="sxs-lookup"><span data-stu-id="e2974-143">Easy-To-Use APIs</span></span>

<span data-ttu-id="e2974-144">USBX предоставляет лучший глубоко внедренный стек USB, который при этом легко изучить и использовать.</span><span class="sxs-lookup"><span data-stu-id="e2974-144">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="e2974-145">API USBX обеспечивает интуитивную простоту и согласованность при работе со службами.</span><span class="sxs-lookup"><span data-stu-id="e2974-145">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="e2974-146">Благодаря предоставляемым API классов USBX пользовательскому приложению не требуется учитывать особенности протоколов USB.</span><span class="sxs-lookup"><span data-stu-id="e2974-146">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
