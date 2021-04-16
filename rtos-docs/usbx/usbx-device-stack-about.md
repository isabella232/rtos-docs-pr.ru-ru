---
title: Руководство пользователя по стеку устройств USBX в ОСРВ Azure
description: В этом руководстве приведены полные сведения о USBX для ОСРВ Azure, высокопроизводительном базовом программном обеспечении для USB от корпорации Майкрософт.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: c8e9360c8b72adbc41f840a48e333668c489399e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814339"
---
# <a name="azure-rtos-usbx-device-stack-user-guide"></a><span data-ttu-id="f8771-103">Руководство пользователя по стеку устройств USBX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="f8771-103">Azure RTOS USBX Device Stack User Guide</span></span>

<span data-ttu-id="f8771-104">В этом руководстве приведены полные сведения о USBX для ОСРВ Azure, высокопроизводительном базовом программном обеспечении для USB от корпорации Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f8771-104">This guide provides comprehensive information about Azure RTOS USBX, the high performance USB foundation software from Microsoft.</span></span>

<span data-ttu-id="f8771-105">Оно предназначено для разработчиков внедренного программного обеспечения, работающего в реальном времени.</span><span class="sxs-lookup"><span data-stu-id="f8771-105">It is intended for the embedded real-time software developer.</span></span> <span data-ttu-id="f8771-106">Такие разработчики должны быть знакомы со стандартными функциями операционной системы, работающими в реальном времени, спецификациями USB и языком программирования C.</span><span class="sxs-lookup"><span data-stu-id="f8771-106">The developer should be familiar with standard real-time operating system functions, the USB specification, and the C programming language.</span></span>

<span data-ttu-id="f8771-107">Технические сведения о USB см. в спецификациях USB и классов USB, которые можно скачать по адресу https://www.USB.org/developers</span><span class="sxs-lookup"><span data-stu-id="f8771-107">For technical information related to USB, see the USB specification and USB Class specifications that can be downloaded at https://www.USB.org/developers</span></span>

## <a name="organization"></a><span data-ttu-id="f8771-108">План</span><span class="sxs-lookup"><span data-stu-id="f8771-108">Organization</span></span>

- <span data-ttu-id="f8771-109">[**Глава 1**](usbx-device-stack-1.md) содержит введение в USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="f8771-109">[**Chapter 1**](usbx-device-stack-1.md) - contains an introduction to Azure RTOS USBX</span></span>

- <span data-ttu-id="f8771-110">[**Глава 2**](usbx-device-stack-2.md) содержит основные шаги по установке и использованию USBX для ОСРВ Azure с приложением ThreadX.</span><span class="sxs-lookup"><span data-stu-id="f8771-110">[**Chapter 2**](usbx-device-stack-2.md) - gives the basic steps to install and use Azure RTOS USBX with your ThreadX application</span></span>

- <span data-ttu-id="f8771-111">[**Глава 3**](usbx-device-stack-3.md) описывает функциональные компоненты стека устройств USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="f8771-111">[**Chapter 3**](usbx-device-stack-3.md) - describes the functional components of the Azure RTOS USBX device stack</span></span>

- <span data-ttu-id="f8771-112">[**Глава 4**](usbx-device-stack-4.md) описывает службы стека устройств USBX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="f8771-112">[**Chapter 4**](usbx-device-stack-4.md) - describes the Azure RTOS USBX device stack services</span></span>

- <span data-ttu-id="f8771-113">[**Глава 5**](usbx-device-stack-5.md) описывает все классы устройств USBX для ОСРВ Azure, в том числе их API.</span><span class="sxs-lookup"><span data-stu-id="f8771-113">[**Chapter 5**](usbx-device-stack-5.md) - describes each Azure RTOS USBX device class including their APIs</span></span>

## <a name="customer-support-center"></a><span data-ttu-id="f8771-114">Центр поддержки клиентов</span><span class="sxs-lookup"><span data-stu-id="f8771-114">Customer Support Center</span></span>

<span data-ttu-id="f8771-115">Отправьте запрос в службу поддержки на портале Azure, если у вас возникли вопросы или требуется помощь при выполнении приведенных здесь шагов.</span><span class="sxs-lookup"><span data-stu-id="f8771-115">Please submit a support ticket through the Azure Portal for questions or help using the steps here.</span></span> <span data-ttu-id="f8771-116">Предоставьте нам следующие сведения в сообщении электронной почты, чтобы мы могли более эффективно решить ваш запрос в службу поддержки:</span><span class="sxs-lookup"><span data-stu-id="f8771-116">Please supply us with the following information in an email message so we can more efficiently resolve your support request:</span></span>

1. <span data-ttu-id="f8771-117">Подробное описание проблемы, включая частоту возникновения и возможность гарантированного воспроизведения.</span><span class="sxs-lookup"><span data-stu-id="f8771-117">A detailed description of the problem, including frequency of occurrence and whether it can be reliably reproduced.</span></span>
2. <span data-ttu-id="f8771-118">Подробное описание любых изменений в приложении и (или) ThreadX для ОСРВ Azure, предшествующих проблеме.</span><span class="sxs-lookup"><span data-stu-id="f8771-118">A detailed description of any changes to the application and/or Azure RTOS ThreadX that preceded the problem.</span></span>
3. <span data-ttu-id="f8771-119">Содержимое строки **_tx_version_id** в файле **_tx_port.h_** вашего дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="f8771-119">The contents of the **_tx_version_id** string found in the **_tx_port.h_** file of your distribution.</span></span> <span data-ttu-id="f8771-120">Эта строка предоставит нам полезную информацию о среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="f8771-120">This string will provide us valuable information regarding your run-time environment.</span></span>
4. <span data-ttu-id="f8771-121">Содержимое в ОЗУ переменной *_tx_build_options* типа **ULONG**.</span><span class="sxs-lookup"><span data-stu-id="f8771-121">The contents in RAM of the *_tx_build_options* **ULONG** variable.</span></span> <span data-ttu-id="f8771-122">Эта переменная предоставит нам сведения о том, как была создана библиотека ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="f8771-122">This variable will give us information on how your Azure RTOS ThreadX library was built.</span></span>
