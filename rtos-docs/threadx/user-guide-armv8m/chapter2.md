---
title: Глава 2. Установка поддержки ThreadX для ARMv8-M
description: В этой главе содержатся сведения об установке и использовании исходного кода ThreadX для архитектуры ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377535"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="c4edc-103">Глава 2. Установка поддержки ThreadX для ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="c4edc-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="c4edc-104">Существуют дополнительные файлы исходного кода ThreadX для поддержки архитектуры ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="c4edc-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="c4edc-105">Если ThreadX должен выполняться в безопасном режиме, эти дополнительные файлы и API-интерфейсы не требуются.</span><span class="sxs-lookup"><span data-stu-id="c4edc-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="c4edc-106">Чтобы запустить ThreadX в безопасном режиме, укажите символ **TX_SECURE_EXECUTION** в начале файла **_tx_port.h_ *_ или в командной строке, или в параметрах проекта. Убедитесь, что _* TX_SECURE_EXECUTION** указан для всех файлов c и сборок.</span><span class="sxs-lookup"><span data-stu-id="c4edc-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="c4edc-107">ThreadX и пользовательское приложение будут выполняться в безопасном режиме.</span><span class="sxs-lookup"><span data-stu-id="c4edc-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="c4edc-108">Чтобы запустить ThreadX и пользовательское приложение в небезопасном режиме и поддерживать небезопасные вызываемые функции, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="c4edc-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="c4edc-109">Добавьте файл ***tx_thread_secure_stack.c*** в безопасное приложение.</span><span class="sxs-lookup"><span data-stu-id="c4edc-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="c4edc-110">Добавьте перечисленные ниже файлы библиотеку ThreadX.</span><span class="sxs-lookup"><span data-stu-id="c4edc-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="c4edc-111">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="c4edc-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="c4edc-112">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="c4edc-113">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="c4edc-114">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="c4edc-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="c4edc-115">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="c4edc-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="c4edc-116">Следующие два файла заменяют универсальные файлы в библиотеке ThreadX.</span><span class="sxs-lookup"><span data-stu-id="c4edc-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="c4edc-117">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="c4edc-118">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="c4edc-119">Дополнительные источники ThreadX для ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="c4edc-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="c4edc-120">Ниже описаны дополнительные файлы ThreadX для расширения TrustZone для архитектуры ARMv8-M.</span><span class="sxs-lookup"><span data-stu-id="c4edc-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="c4edc-121">**Имя файла**</span><span class="sxs-lookup"><span data-stu-id="c4edc-121">**File Name**</span></span>                            | <span data-ttu-id="c4edc-122">**Contents**</span><span class="sxs-lookup"><span data-stu-id="c4edc-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="c4edc-123">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="c4edc-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="c4edc-124">Включаемый файл, определяющий небезопасные вызываемые функции ThreadX.</span><span class="sxs-lookup"><span data-stu-id="c4edc-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="c4edc-125">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="c4edc-126">Файл проверки ошибок для API выделения безопасного стека.</span><span class="sxs-lookup"><span data-stu-id="c4edc-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="c4edc-127">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="c4edc-128">Файл проверки ошибок для API высвобождения безопасного стека.</span><span class="sxs-lookup"><span data-stu-id="c4edc-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="c4edc-129">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="c4edc-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="c4edc-130">Небезопасная оболочка для службы выделения безопасного стека.</span><span class="sxs-lookup"><span data-stu-id="c4edc-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="c4edc-131">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="c4edc-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="c4edc-132">Небезопасная оболочка для службы высвобождения безопасного стека.</span><span class="sxs-lookup"><span data-stu-id="c4edc-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="c4edc-133">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="c4edc-134">Обработчик ошибок стека потоков.</span><span class="sxs-lookup"><span data-stu-id="c4edc-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="c4edc-135">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="c4edc-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="c4edc-136">Регистрация обратного вызова уведомлений для обработки ошибок стека потоков.</span><span class="sxs-lookup"><span data-stu-id="c4edc-136">Register notification callback for handling thread stack errors.</span></span> |
