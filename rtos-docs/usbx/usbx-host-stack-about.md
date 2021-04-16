---
title: Руководство пользователя по стеку узлов USBX для ОСРВ Azure
description: В этом руководстве приведены полные сведения об USBX для ОСРВ Azure, высокопроизводительном базовом программном обеспечении для USB от корпорации Майкрософт.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 243b12c4757ee945def8fea01c0d4114e39312ce
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815607"
---
# <a name="azure-rtos-usbx-host-stack-user-guide"></a><span data-ttu-id="48ed8-103">Руководство пользователя по стеку узлов USBX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="48ed8-103">Azure RTOS USBX Host Stack User Guide</span></span>

<span data-ttu-id="48ed8-104">В этом руководстве приведены полные сведения об USBX для ОСРВ Azure, высокопроизводительном базовом программном обеспечении для USB от корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="48ed8-104">This guide provides comprehensive information about Azure RTOS USBX, the high-performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="48ed8-105">Оно предназначено для разработчиков внедряемого программного обеспечения, работающего в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="48ed8-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="48ed8-106">Такие разработчики должны быть знакомы со стандартными функциями операционной системы реального времени, спецификациями USB и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="48ed8-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="48ed8-107">Технические сведения о USB см. в спецификациях USB и классов USB, которые можно скачать по адресу [https://www.USB.org/developers](https://www.USB.org/developers).</span><span class="sxs-lookup"><span data-stu-id="48ed8-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at [https://www.USB.org/developers](https://www.USB.org/developers)</span></span>

## <a name="organization"></a><span data-ttu-id="48ed8-108">План</span><span class="sxs-lookup"><span data-stu-id="48ed8-108">Organization</span></span>

- <span data-ttu-id="48ed8-109">[**Глава 1**](usbx-host-stack-1.md) содержит введение в USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="48ed8-109">[**Chapter 1**](usbx-host-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="48ed8-110">[**Глава 2**](usbx-host-stack-2.md) содержит основные шаги по установке и использованию USBX для ОСРВ Azure с приложением ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="48ed8-110">[**Chapter 2**](usbx-host-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your Azure RTOS ThreadX application</span></span>

- <span data-ttu-id="48ed8-111">[**Глава 3**](usbx-host-stack-3.md) содержит функциональный обзор USBX для ОСРВ Azure и основные сведения о USB.</span><span class="sxs-lookup"><span data-stu-id="48ed8-111">[**Chapter 3**](usbx-host-stack-3.md) - provides a functional overview of Azure RTOS USBX and basic information about USB</span></span>

- <span data-ttu-id="48ed8-112">[**Глава 4**](usbx-host-stack-4.md) содержит подробные сведения об интерфейсе приложения к USBX для ОСРВ Azure в режиме узла.</span><span class="sxs-lookup"><span data-stu-id="48ed8-112">[**Chapter 4**](usbx-host-stack-4.md) - details the application's interface to Azure RTOS USBX in host mode</span></span>

- <span data-ttu-id="48ed8-113">[**Глава 5**](usbx-host-stack-5.md) описывает API для классов узла USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="48ed8-113">[**Chapter 5**](usbx-host-stack-5.md) - describes the APIs of the Azure RTOS USBX Host classes</span></span>

- <span data-ttu-id="48ed8-114">[**Глава 6**](usbx-host-stack-6.md) описывает класс CDC-ECM в USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="48ed8-114">[**Chapter 6**](usbx-host-stack-6.md) - describes the Azure RTOS USBX CDC-ECM class</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="48ed8-115">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="48ed8-115">Customer Support Center</span></span>

<span data-ttu-id="48ed8-116">Если у вас возникли вопросы или требуется помощь при выполнении приведенных здесь шагов, отправьте запрос в службу поддержки на портале Azure.</span><span class="sxs-lookup"><span data-stu-id="48ed8-116">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="48ed8-117">Предоставьте нам следующие сведения в сообщении электронной почты, чтобы мы могли более эффективно решить ваш запрос в службу поддержки:</span><span class="sxs-lookup"><span data-stu-id="48ed8-117">Please supply us with the following information in an email message so we can more efficiently resolve your support request.</span></span>

1. <span data-ttu-id="48ed8-118">Подробное описание проблемы, включая частоту возникновения и возможность гарантированного воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="48ed8-118">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="48ed8-119">Подробное описание любых изменений в приложении и (или) ОСРВ Azure ThreadX, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="48ed8-119">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="48ed8-120">Содержимое строки *_tx_version_id* в файле *tx_port.h* вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="48ed8-120">The contents of the *_tx_version_id* string found in the *tx_port.h* file of your distribution.</span></span> <span data-ttu-id="48ed8-121">Эта строка предоставит нам полезную информацию о среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="48ed8-121">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="48ed8-122">Содержимое в ОЗУ переменной *_tx_build_options* типа ULONG.</span><span class="sxs-lookup"><span data-stu-id="48ed8-122">The contents in RAM of the *_tx_build_options* ULONG variable.</span></span> <span data-ttu-id="48ed8-123">Эта переменная предоставит нам сведения о том, как была создана библиотека ОСРВ Azure ThreadX.</span><span class="sxs-lookup"><span data-stu-id="48ed8-123">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
