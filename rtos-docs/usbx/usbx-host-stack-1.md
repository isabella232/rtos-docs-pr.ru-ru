---
title: Глава 1. Введение в стек узла USBX для ОСРВ Azure
description: В этой главе представлены основные сведения о стеке узла USBX, в том числе об области применения и преимуществах.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a9fdd86d47bd4680409cc550c87bc6f456d146a9
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377056"
---
# <a name="chapter-1---introduction-to-azure-rtos-usbx-host-stack"></a><span data-ttu-id="686c6-103">Глава 1. Введение в стек узла USBX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="686c6-103">Chapter 1 - Introduction to Azure RTOS USBX Host Stack</span></span>

<span data-ttu-id="686c6-104">USBX — это полнофункциональный стек USB для глубоко встраиваемых приложений.</span><span class="sxs-lookup"><span data-stu-id="686c6-104">USBX is a full-featured USB stack for deeply embedded applications.</span></span> <span data-ttu-id="686c6-105">В этой главе представлены основные сведения об USBX, в том числе области применения и преимущества.</span><span class="sxs-lookup"><span data-stu-id="686c6-105">This chapter introduces USBX, describing its applications and benefits.</span></span>

## <a name="usbx-features"></a><span data-ttu-id="686c6-106">Возможности USBX</span><span class="sxs-lookup"><span data-stu-id="686c6-106">USBX features</span></span>

<span data-ttu-id="686c6-107">USBX поддерживает три существующих спецификации USB: 1.1, 2.0 и OTG.</span><span class="sxs-lookup"><span data-stu-id="686c6-107">USBX support the three existing USB specifications: 1.1, 2.0 and OTG.</span></span> <span data-ttu-id="686c6-108">Он может масштабироваться и адаптироваться к простым топологиям USB только с одним подключенным устройством, а также к сложным топологиям с несколькими устройствами и каскадной схемой соединения концентраторов.</span><span class="sxs-lookup"><span data-stu-id="686c6-108">It is designed to be scalable and will accommodate simple USB topologies with only one connected device as well as complex topologies with multiple devices and cascading hubs.</span></span> <span data-ttu-id="686c6-109">USBX поддерживает все типы передачи данных по протоколам USB: контролируемая, пакетная, прерываемая и изохронная.</span><span class="sxs-lookup"><span data-stu-id="686c6-109">USBX supports all the data transfer types of the USB protocols: control, bulk, interrupt, and isochronous.</span></span>

<span data-ttu-id="686c6-110">USBX поддерживает работу со стороной узла и устройства.</span><span class="sxs-lookup"><span data-stu-id="686c6-110">USBX supports both the host side and the device side.</span></span> <span data-ttu-id="686c6-111">Каждая сторона включает три уровня:</span><span class="sxs-lookup"><span data-stu-id="686c6-111">Each side is comprised of three layers.</span></span>

- <span data-ttu-id="686c6-112">уровень контроллера;</span><span class="sxs-lookup"><span data-stu-id="686c6-112">Controller layer</span></span>
- <span data-ttu-id="686c6-113">уровень стека;</span><span class="sxs-lookup"><span data-stu-id="686c6-113">Stack layer</span></span>
- <span data-ttu-id="686c6-114">уровень класса.</span><span class="sxs-lookup"><span data-stu-id="686c6-114">Class layer</span></span>

<span data-ttu-id="686c6-115">Связь между уровнями USB строится следующим образом:</span><span class="sxs-lookup"><span data-stu-id="686c6-115">The relationship between the USB layers is as follows.</span></span>

![Уровни USB](./media/usbx-device-stack/usb-layers.png)

## <a name="product-highlights"></a><span data-ttu-id="686c6-117">Особенности продуктов</span><span class="sxs-lookup"><span data-stu-id="686c6-117">Product Highlights</span></span>

- <span data-ttu-id="686c6-118">Полная поддержка процессора ThreadX.</span><span class="sxs-lookup"><span data-stu-id="686c6-118">Complete ThreadX processor support</span></span>
- <span data-ttu-id="686c6-119">Отсутствие лицензионных отчислений.</span><span class="sxs-lookup"><span data-stu-id="686c6-119">No royalties</span></span>
- <span data-ttu-id="686c6-120">Полный исходный код ANSI C.</span><span class="sxs-lookup"><span data-stu-id="686c6-120">Complete ANSI C source code</span></span>
- <span data-ttu-id="686c6-121">Производительность в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="686c6-121">Real-time performance</span></span>
- <span data-ttu-id="686c6-122">Быстрая техническая поддержка.</span><span class="sxs-lookup"><span data-stu-id="686c6-122">Responsive technical support</span></span>
- <span data-ttu-id="686c6-123">Поддержка нескольких контроллеров узла.</span><span class="sxs-lookup"><span data-stu-id="686c6-123">Multiple host controller support</span></span>
- <span data-ttu-id="686c6-124">Поддержка нескольких классов.</span><span class="sxs-lookup"><span data-stu-id="686c6-124">Multiple class support</span></span>
- <span data-ttu-id="686c6-125">Несколько экземпляров классов.</span><span class="sxs-lookup"><span data-stu-id="686c6-125">Multiple class instances</span></span>
- <span data-ttu-id="686c6-126">Интеграция классов со ThreadX, FileX и NetX.</span><span class="sxs-lookup"><span data-stu-id="686c6-126">Integration of classes with ThreadX, FileX and NetX</span></span>
- <span data-ttu-id="686c6-127">Поддержка USB-устройств с несколькими конфигурациями.</span><span class="sxs-lookup"><span data-stu-id="686c6-127">Support for USB devices with multiple configuration</span></span>
- <span data-ttu-id="686c6-128">Поддержка составных USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="686c6-128">Support for USB composite devices</span></span>
- <span data-ttu-id="686c6-129">Поддержка каскадной схемы соединения концентраторов.</span><span class="sxs-lookup"><span data-stu-id="686c6-129">Support for cascading hubs</span></span>
- <span data-ttu-id="686c6-130">Поддержка управления питанием по USB.</span><span class="sxs-lookup"><span data-stu-id="686c6-130">Support for USB power management</span></span>
- <span data-ttu-id="686c6-131">Поддержка OTG в USB.</span><span class="sxs-lookup"><span data-stu-id="686c6-131">Support for USB OTG</span></span>
- <span data-ttu-id="686c6-132">Экспорт событий трассировки для TraceX.</span><span class="sxs-lookup"><span data-stu-id="686c6-132">Export trace events for TraceX</span></span>

## <a name="powerful-services-of-usbx"></a><span data-ttu-id="686c6-133">Мощные службы USBX.</span><span class="sxs-lookup"><span data-stu-id="686c6-133">Powerful Services of USBX</span></span>

### <a name="multiple-host-controller-support"></a><span data-ttu-id="686c6-134">Поддержка нескольких контроллеров узла.</span><span class="sxs-lookup"><span data-stu-id="686c6-134">Multiple Host Controller Support</span></span>

<span data-ttu-id="686c6-135">USBX может поддерживать одновременную работу нескольких хост-контроллеров USB.</span><span class="sxs-lookup"><span data-stu-id="686c6-135">USBX can support multiple USB host controllers running concurrently.</span></span> <span data-ttu-id="686c6-136">Благодаря этой возможности USBX поддерживает стандарт USB 2.0 по схеме обратной совместимости, которая используется большинством хост-контроллеров USB 2.0, представленных на современном рынке.</span><span class="sxs-lookup"><span data-stu-id="686c6-136">This feature allows USBX to support the USB 2.0 standard using the backward compatibility scheme associated with most USB 2.0 host controllers on the market today.</span></span>

### <a name="usb-software-scheduler"></a><span data-ttu-id="686c6-137">Программный планировщик USB</span><span class="sxs-lookup"><span data-stu-id="686c6-137">USB Software Scheduler</span></span>

<span data-ttu-id="686c6-138">USBX включает программный планировщик USB, который требуется для поддержки контроллеров USB без обработки списка оборудования.</span><span class="sxs-lookup"><span data-stu-id="686c6-138">USBX contains a USB software scheduler necessary to support USB controllers that do not have hardware list processing.</span></span> <span data-ttu-id="686c6-139">Программный планировщик USBX организует передачу данных по USB с нужной частотой служб и приоритетами, а также подает контроллеру USB команды на выполнение передачи данных.</span><span class="sxs-lookup"><span data-stu-id="686c6-139">The USBX software scheduler will organize USB transfers with the correct frequency of service and priority, and will instruct the USB controller to execute each transfer.</span></span>

### <a name="complete-usb-device-framework-support"></a><span data-ttu-id="686c6-140">Полная поддержка структуры USB-устройств</span><span class="sxs-lookup"><span data-stu-id="686c6-140">Complete USB Device Framework Support</span></span>

<span data-ttu-id="686c6-141">USBX может поддерживать самые требовательные USB-устройства, в том числе с несколькими конфигурациями, несколькими интерфейсами и несколькими альтернативными параметрами.</span><span class="sxs-lookup"><span data-stu-id="686c6-141">USBX can support the most demanding USB devices, including multiple configurations, multiple interfaces, and multiple alternate settings.</span></span>

### <a name="easy-to-use-apis"></a><span data-ttu-id="686c6-142">Простые в использовании API</span><span class="sxs-lookup"><span data-stu-id="686c6-142">Easy-To-Use APIs</span></span>

<span data-ttu-id="686c6-143">USBX предоставляет лучший глубоко внедренный стек USB, который при этом легко изучить и использовать.</span><span class="sxs-lookup"><span data-stu-id="686c6-143">USBX provides the very best deeply embedded USB stack in a manner that is easy to understand and use.</span></span> <span data-ttu-id="686c6-144">API USBX обеспечивает интуитивную простоту и согласованность при работе со службами.</span><span class="sxs-lookup"><span data-stu-id="686c6-144">The USBX API makes the services intuitive and consistent.</span></span> <span data-ttu-id="686c6-145">Благодаря предоставляемым API классов USBX пользовательскому приложению не требуется учитывать особенности протоколов USB.</span><span class="sxs-lookup"><span data-stu-id="686c6-145">By using the provided USBX class APIs, the user application does not need to understand the complexity of the USB protocols.</span></span>
