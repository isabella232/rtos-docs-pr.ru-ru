---
title: Глава 3 - Требования к диспетчеру модулей
description: Данная статья представляет собой описание шагов, необходимых для создания диспетчера модулей ThreadX.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8ea1a05096b5975de203648fddfb19c1a6105e0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815116"
---
# <a name="chapter-3---module-manager-requirements"></a><span data-ttu-id="888fd-103">Глава 3 - Требования к диспетчеру модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-103">Chapter 3 - Module Manager requirements</span></span>

<span data-ttu-id="888fd-104">Диспетчер модулей ThreadX находится в резидентной части приложения вместе с ОСРВ ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-104">The ThreadX Module Manager resides in the resident portion of the application along with the ThreadX RTOS.</span></span> <span data-ttu-id="888fd-105">Диспетчер отвечает за запуск модуля, а также за отправку и отправку всех запросов модуля для служб ThreadX API.</span><span class="sxs-lookup"><span data-stu-id="888fd-105">It is responsible for starting the module as well as fielding and dispatching all module requests for ThreadX API services.</span></span>

> [!NOTE]
> <span data-ttu-id="888fd-106">Исходные файлы модуля ThreadX **Manager** (C и сборка) следует добавить в проект библиотеки ThreadX "**tx**".</span><span class="sxs-lookup"><span data-stu-id="888fd-106">The ThreadX Module **Manager** source files (C and assembly) should be added to the ThreadX library project "**tx**".</span></span>

<span data-ttu-id="888fd-107">Для создания диспетчера модулей ThreadX необходимы следующие шаги (каждый шаг более подробно описан ниже).</span><span class="sxs-lookup"><span data-stu-id="888fd-107">The following steps are required for building the ThreadX Module Manager (each step is described in greater detail below).</span></span>

1. <span data-ttu-id="888fd-108">Блок управления **TX_THREAD** должен быть расширен для включения информации о модуле.</span><span class="sxs-lookup"><span data-stu-id="888fd-108">The **TX_THREAD** control block must be extended to include module information.</span></span> <span data-ttu-id="888fd-109">Самый простой способ добиться этого - заменить определение **TX_THREAD_EXTENSION_2** в файле **_tx_port.h_ *_ на _* TX_THREAD_EXTENSION_2** в **_txm_module_port.h_**.</span><span class="sxs-lookup"><span data-stu-id="888fd-109">The easiest way to accomplish this is to replace the definition of **TX_THREAD_EXTENSION_2** in the **_tx_port.h_*_ file with the _\* TX_THREAD_EXTENSION_2*\* found in **_txm_module_port.h_**.</span></span> <span data-ttu-id="888fd-110">См. [приложение](appendix.md) для расширений для конкретных портов.</span><span class="sxs-lookup"><span data-stu-id="888fd-110">See [appendix](appendix.md) for port-specific extensions.</span></span>

<span data-ttu-id="888fd-111">Пример расширения:</span><span class="sxs-lookup"><span data-stu-id="888fd-111">Example extension:</span></span>

   ```c
   #define TX_THREAD_EXTENSION_2                     \
       VOID      tx_thread_module_instance_ptr;      \
       VOID      tx_thread_module_entry_info_ptr;    \
       ULONG     tx_thread_module_current_user_mode; \
       ULONG     tx_thread_module_user_mode;         \
       VOID     *tx_thread_module_kernel_stack_start;\
       VOID     *tx_thread_module_kernel_stack_end;  \
       ULONG     tx_thread_module_kernel_stack_size; \
       VOID     *tx_thread_module_stack_ptr;         \
       VOID     *tx_thread_module_stack_start;       \
       VOID     *tx_thread_module_stack_end;         \
       ULONG     tx_thread_module_stack_size;        \
       VOID     *tx_thread_module_reserved;
   ```

   <span data-ttu-id="888fd-112">Следующие расширения должны быть определены в ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="888fd-112">The following extensions must be defined in ***tx_port.h***.</span></span>

   ```c
   #define TX_EVENT_FLAGS_GROUP_EXTENSION  VOID    *tx_event_flags_group_module_instance; \
        VOID   (*tx_event_flags_group_set_module_notify)(struct TX_EVENT_FLAGS_GROUP_STRUCT *group_ptr);

   #define TX_QUEUE_EXTENSION              VOID    *tx_queue_module_instance; \
        VOID   (*tx_queue_send_module_notify)(struct TX_QUEUE_STRUCT *queue_ptr);

   #define TX_SEMAPHORE_EXTENSION          VOID    *tx_semaphore_module_instance; \
        VOID   (*tx_semaphore_put_module_notify)(struct TX_SEMAPHORE_STRUCT *semaphore_ptr);

   #define TX_TIMER_EXTENSION              VOID    *tx_timer_module_instance; \
        VOID   (*tx_timer_module_expiration_function)(ULONG id);
   ```

2. <span data-ttu-id="888fd-113">Добавьте все файлы C и сборки ***txm_module_manager_\****  в проект библиотеки ThreadX **_tx_**.</span><span class="sxs-lookup"><span data-stu-id="888fd-113">Add all the ***txm_module_manager_\**** C and assembly files to the ThreadX library project **_tx_**.</span></span>
3. <span data-ttu-id="888fd-114">Перестройте все библиотеки и исполняемые проекты.</span><span class="sxs-lookup"><span data-stu-id="888fd-114">Rebuild all libraries and executable projects.</span></span> <span data-ttu-id="888fd-115">Если требуется NetX Duo, весь C-код модулей и диспетчера модулей должен быть построен с определением **TXM_MODULE_ENABLE_NETX_DUO**.</span><span class="sxs-lookup"><span data-stu-id="888fd-115">If NetX Duo is required, all Module and Module Manager C code should be built with **TXM_MODULE_ENABLE_NETX_DUO** defined.</span></span>

## <a name="module-manager-sources"></a><span data-ttu-id="888fd-116">Источники диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-116">Module Manager sources</span></span>

<span data-ttu-id="888fd-117">В диспетчере модулей ThreadX имеется набор исходных файлов, которые предназначены для связывания и размещения непосредственно с резидентным кодом ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-117">The ThreadX Module Manager has a set of source files that are designed to be linked and located directly with the resident ThreadX code.</span></span> <span data-ttu-id="888fd-118">Данные файлы предоставляют возможность запускать модуль и отправлять последующие запросы ThreadX API от модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-118">These files provide the ability to launch a module and field subsequent ThreadX API requests from the module.</span></span> <span data-ttu-id="888fd-119">Файлы диспетчера модулей выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="888fd-119">The module manager files are as follows.</span></span>

| <span data-ttu-id="888fd-120">**Имя файла**</span><span class="sxs-lookup"><span data-stu-id="888fd-120">**File Name**</span></span> |  <span data-ttu-id="888fd-121">**Contents**</span><span class="sxs-lookup"><span data-stu-id="888fd-121">**Contents**</span></span> |
|-------------- | ------------- |
| <span data-ttu-id="888fd-122">***txm_module.h***</span><span class="sxs-lookup"><span data-stu-id="888fd-122">***txm_module.h***</span></span> | <span data-ttu-id="888fd-123">Включить файл, определяющий информацию о модуле (также включен в исходный код модуля).</span><span class="sxs-lookup"><span data-stu-id="888fd-123">Include file that defines module information (also included in the module source code).</span></span> |
| <span data-ttu-id="888fd-124">***txm_module_manager_dispatch.h***</span><span class="sxs-lookup"><span data-stu-id="888fd-124">***txm_module_manager_dispatch.h***</span></span> | <span data-ttu-id="888fd-125">Включить файл, определяющий вспомогательные функции диспетчеризации.</span><span class="sxs-lookup"><span data-stu-id="888fd-125">Include file that defines dispatch helper functions.</span></span>|
| <span data-ttu-id="888fd-126">***txm_module_manager_util.h***</span><span class="sxs-lookup"><span data-stu-id="888fd-126">***txm_module_manager_util.h***</span></span> | <span data-ttu-id="888fd-127">Включить файл, определяющий внутренние вспомогательные макросы и функции служебных программ.</span><span class="sxs-lookup"><span data-stu-id="888fd-127">Include file that defines internal utility helper macros & functions.</span></span> |
| <span data-ttu-id="888fd-128">***txm_module_port.h***</span><span class="sxs-lookup"><span data-stu-id="888fd-128">***txm_module_port.h***</span></span> | <span data-ttu-id="888fd-129">Включить файл, определяющий информацию о модуле для конкретного порта (также включен в исходный код модуля).</span><span class="sxs-lookup"><span data-stu-id="888fd-129">Include file that defines port-specific module information (also included in the module source code).</span></span> |
| <span data-ttu-id="888fd-130">\***tx_initialize_low_level.\[s,S,68\]** _</span><span class="sxs-lookup"><span data-stu-id="888fd-130">\***tx_initialize_low_level.\[s,S,68\]** _</span></span> | <span data-ttu-id="888fd-131">Заменяет существующий файл библиотеки ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-131">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="888fd-132">Обновленная таблица векторов и дополнительные обработчики векторов для диспетчера модулей и исключений памяти.</span><span class="sxs-lookup"><span data-stu-id="888fd-132">Updated vector table and additional vector handlers for module manager and memory exceptions.</span></span> <span data-ttu-id="888fd-133">_Данный файл присутствует только в Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="888fd-133">_This file is only in Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.\*</span></span>|
| <span data-ttu-id="888fd-134">\***tx_thread_context_restore.s** _</span><span class="sxs-lookup"><span data-stu-id="888fd-134">\***tx_thread_context_restore.s** _</span></span> | <span data-ttu-id="888fd-135">Заменяет существующий файл библиотеки ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-135">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="888fd-136">Восстановить контекст потока после обработки прерывания.</span><span class="sxs-lookup"><span data-stu-id="888fd-136">Restore thread context after interrupt processing.</span></span> <span data-ttu-id="888fd-137">_Данный файл присутствует только в Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="888fd-137">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="888fd-138">***tx_thread_schedule.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="888fd-138">***tx_thread_schedule.\[s,S,68\]***</span></span> | <span data-ttu-id="888fd-139">Заменяет существующий файл библиотеки ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-139">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="888fd-140">Расширенный экземпляр планировщика, используемый в данном случае для обновления регистров управления памятью.</span><span class="sxs-lookup"><span data-stu-id="888fd-140">Extended scheduler code, which in this case is used to update memory management registers.</span></span> |
| <span data-ttu-id="888fd-141">\***tx_thread_stack_build.s** _</span><span class="sxs-lookup"><span data-stu-id="888fd-141">\***tx_thread_stack_build.s** _</span></span> | <span data-ttu-id="888fd-142">Заменяет существующий файл библиотеки ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-142">Replaces existing ThreadX library file.</span></span> <span data-ttu-id="888fd-143">Создает стековый фрейм потока.</span><span class="sxs-lookup"><span data-stu-id="888fd-143">Builds the stack frame of a thread.</span></span> <span data-ttu-id="888fd-144">_Данный файл присутствует только в Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="888fd-144">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="888fd-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span><span class="sxs-lookup"><span data-stu-id="888fd-145">***txm_module_manager_thread_stack_build.\[s,S,68\]***</span></span> | <span data-ttu-id="888fd-146">Создает все начальные стеки модулей, включает настройку для независимого от позиции доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="888fd-146">Builds all module initial stacks, includes setup for position-independent data access.</span></span> |
| <span data-ttu-id="888fd-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span><span class="sxs-lookup"><span data-stu-id="888fd-147">\***txm_module_manager_user_mode_entry.\[s,S\]** _</span></span> | <span data-ttu-id="888fd-148">Позволяет модулю войти в режим ядра.</span><span class="sxs-lookup"><span data-stu-id="888fd-148">Allows the module to enter kernel mode.</span></span> <span data-ttu-id="888fd-149">_Данный файл присутствует только в Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span><span class="sxs-lookup"><span data-stu-id="888fd-149">_This file is only in Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.\*</span></span>|
| <span data-ttu-id="888fd-150">***txm_module_manager_alignment_adjust.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-150">***txm_module_manager_alignment_adjust.c***</span></span> | <span data-ttu-id="888fd-151">Обрабатывает требования к выравниванию для конкретных портов.</span><span class="sxs-lookup"><span data-stu-id="888fd-151">Handles port-specific alignment requirements.</span></span>|
| <span data-ttu-id="888fd-152">***txm_module_manager_application_request.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-152">***txm_module_manager_application_request.c***</span></span> | <span data-ttu-id="888fd-153">Обрабатывает специфичные для приложения запросы к резидентному коду.</span><span class="sxs-lookup"><span data-stu-id="888fd-153">Handles the application-specific requests to the resident code.</span></span> |
| <span data-ttu-id="888fd-154">***txm_module_manager_callback_request.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-154">***txm_module_manager_callback_request.c***</span></span> | <span data-ttu-id="888fd-155">Отправляет запрос обратного вызова в модуль.</span><span class="sxs-lookup"><span data-stu-id="888fd-155">Sends a callback request to a module.</span></span> |
| <span data-ttu-id="888fd-156">***txm_module_manager_event_flags_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-156">***txm_module_manager_event_flags_notify_trampoline.c***</span></span> | <span data-ttu-id="888fd-157">Обрабатывает вызов уведомления о наборе флагов событий из ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-157">Processes the event flags set notification call from ThreadX.</span></span> |
| <span data-ttu-id="888fd-158">***txm_module_manager_external_memory_enable.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-158">***txm_module_manager_external_memory_enable.c***</span></span> | <span data-ttu-id="888fd-159">Создает запись в таблице управления памятью для области разделяемой памяти, к которой модуль может получить доступ.</span><span class="sxs-lookup"><span data-stu-id="888fd-159">Creates an entry in the memory management table for a shared memory space the module can access.</span></span> |
| <span data-ttu-id="888fd-160">***txm_module_manager_file_load.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-160">***txm_module_manager_file_load.c***</span></span> | <span data-ttu-id="888fd-161">Выделяет и загружает двоичный файл модуля в область памяти модуля и подготавливает его к выполнению.</span><span class="sxs-lookup"><span data-stu-id="888fd-161">Allocates and loads a binary module file into the module memory area and prepares it for execution.</span></span> |
| <span data-ttu-id="888fd-162">***txm_module_manager_in_place_load.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-162">***txm_module_manager_in_place_load.c***</span></span> | <span data-ttu-id="888fd-163">Выделяет область данных модуля и готовится к выполнению модуля с предоставленного кодового адреса.</span><span class="sxs-lookup"><span data-stu-id="888fd-163">Allocates the module data area and prepares for module execution from the supplied code address.</span></span> |
| <span data-ttu-id="888fd-164">***txm_module_manager_initialize.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-164">***txm_module_manager_initialize.c***</span></span> | <span data-ttu-id="888fd-165">Инициализирует диспетчер модулей, включая указание области памяти модуля, доступной для загрузки и запуска модулей.</span><span class="sxs-lookup"><span data-stu-id="888fd-165">Initializes the Module Manager, including specification of the module memory area available for loading and running modules.</span></span> |
| <span data-ttu-id="888fd-166">\***txm_module_manager_initialize_mmu.c** _</span><span class="sxs-lookup"><span data-stu-id="888fd-166">\***txm_module_manager_initialize_mmu.c** _</span></span> | <span data-ttu-id="888fd-167">Инициализировать MMU.</span><span class="sxs-lookup"><span data-stu-id="888fd-167">Initialize MMU.</span></span> <span data-ttu-id="888fd-168">Пользователи могут редактировать данный файл в соответствии со своей картой памяти.</span><span class="sxs-lookup"><span data-stu-id="888fd-168">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="888fd-169">_Данный файл присутствует только в Cortex-A7/ARM\*</span><span class="sxs-lookup"><span data-stu-id="888fd-169">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="888fd-170">\***txm_module_manager_mm_initialize.c** _</span><span class="sxs-lookup"><span data-stu-id="888fd-170">\***txm_module_manager_mm_initialize.c** _</span></span> | <span data-ttu-id="888fd-171">Инициализировать MPU/MMU.</span><span class="sxs-lookup"><span data-stu-id="888fd-171">Initialize MPU/MMU.</span></span> <span data-ttu-id="888fd-172">Пользователи могут редактировать данный файл в соответствии со своей картой памяти.</span><span class="sxs-lookup"><span data-stu-id="888fd-172">Users can edit this file according to their memory map.</span></span> <span data-ttu-id="888fd-173">_Данный файл присутствует только в Cortex-A7/ARM\*</span><span class="sxs-lookup"><span data-stu-id="888fd-173">_This file is only in Cortex-A7/ARM\*</span></span> |
| <span data-ttu-id="888fd-174">***txm_module_manager_kernel_dispatch.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-174">***txm_module_manager_kernel_dispatch.c***</span></span> | <span data-ttu-id="888fd-175">Обрабатывает запросы API модуля на основе идентификатора запроса.</span><span class="sxs-lookup"><span data-stu-id="888fd-175">Handles the module API requests, based on the request ID.</span></span> |
| <span data-ttu-id="888fd-176">***txm_module_manager_maximum_module_priority_set.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-176">***txm_module_manager_maximum_module_priority_set.c***</span></span> | <span data-ttu-id="888fd-177">Устанавливает максимальный приоритет потока, разрешенный в рамках модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-177">Sets the maximum thread priority allowed in a module.</span></span> |
| <span data-ttu-id="888fd-178">***txm_module_manager_memory_fault_handler.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-178">***txm_module_manager_memory_fault_handler.c***</span></span> | <span data-ttu-id="888fd-179">Обрабатывает ошибки памяти, обнаруженные в исполняющем модуле.</span><span class="sxs-lookup"><span data-stu-id="888fd-179">Handles memory faults detected in an executing module.</span></span> |
| <span data-ttu-id="888fd-180">***txm_module_manager_memory_fault_notify.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-180">***txm_module_manager_memory_fault_notify.c***</span></span> | <span data-ttu-id="888fd-181">Регистрирует обратный вызов уведомления приложения всякий раз, когда происходит сбой памяти.</span><span class="sxs-lookup"><span data-stu-id="888fd-181">Registers an application notification callback whenever a memory fault occurs.</span></span> |
| <span data-ttu-id="888fd-182">***txm_module_manager_memory_load.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-182">***txm_module_manager_memory_load.c***</span></span> | <span data-ttu-id="888fd-183">Выделяет и загружает код и данные модуля и подготавливает модуль к процедуре выполнения.</span><span class="sxs-lookup"><span data-stu-id="888fd-183">Allocates and loads a module's code and data and prepares the module for execution.</span></span> |
| <span data-ttu-id="888fd-184">***txm_module_manager_mm_register_setup.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-184">***txm_module_manager_mm_register_setup.c***</span></span> | <span data-ttu-id="888fd-185">Устанавливает регистры MPU/MMU для модуля в зависимости от того, куда загружены код и данные.</span><span class="sxs-lookup"><span data-stu-id="888fd-185">Sets up MPU/MMU registers for the module based on where the code and data are loaded.</span></span> |
| <span data-ttu-id="888fd-186">***txm_module_manager_object_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-186">***txm_module_manager_object_allocate.c***</span></span> | <span data-ttu-id="888fd-187">Выделяет память для объекта модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-187">Allocates memory for a module object.</span></span> |
| <span data-ttu-id="888fd-188">***txm_module_manager_object_deallocate.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-188">***txm_module_manager_object_deallocate.c***</span></span> | <span data-ttu-id="888fd-189">Освобождает память для объекта модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-189">Deallocates memory for a module object.</span></span> |
| <span data-ttu-id="888fd-190">***txm_module_manager_object_pointer_get.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-190">***txm_module_manager_object_pointer_get.c***</span></span> | <span data-ttu-id="888fd-191">Выполняет поиск предоставленного типа и имени объекта и, если он найден, возвращает указатель объекта.</span><span class="sxs-lookup"><span data-stu-id="888fd-191">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> |
| <span data-ttu-id="888fd-192">***txm_module_manager_object_pointer_get_extended.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-192">***txm_module_manager_object_pointer_get_extended.c***</span></span> | <span data-ttu-id="888fd-193">Выполняет поиск предоставленного типа и имени объекта и, если он найден, возвращает указатель объекта.</span><span class="sxs-lookup"><span data-stu-id="888fd-193">Searches for the supplied object type and name, and if found, returns the object pointer.</span></span> <span data-ttu-id="888fd-194">Длина имени указана для безопасности.</span><span class="sxs-lookup"><span data-stu-id="888fd-194">Name length specified for safety.</span></span> |
| <span data-ttu-id="888fd-195">***txm_module_manager_object_pool_create.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-195">***txm_module_manager_object_pool_create.c***</span></span>  | <span data-ttu-id="888fd-196">Создает пул объектов вне области данных модуля, из которых приложения модуля могут выделять.</span><span class="sxs-lookup"><span data-stu-id="888fd-196">Creates a pool of objects outside the module's data area that module applications can allocate from.</span></span> |
| <span data-ttu-id="888fd-197">***txm_module_manager_properties_get.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-197">***txm_module_manager_properties_get.c***</span></span> | <span data-ttu-id="888fd-198">Получает свойства указанного модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-198">Gets the properties of the specified module.</span></span> |
| <span data-ttu-id="888fd-199">***txm_module_manager_queue_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-199">***txm_module_manager_queue_notify_trampoline.c***</span></span> | <span data-ttu-id="888fd-200">Обрабатывает вызов уведомления об очереди из ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-200">Processes the queue notification call from ThreadX.</span></span> |
| <span data-ttu-id="888fd-201">***txm_module_manager_semaphore_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-201">***txm_module_manager_semaphore_notify_trampoline.c***</span></span> | <span data-ttu-id="888fd-202">Обрабатывает вызов уведомления о размещении семафора из ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-202">Processes the semaphore put notification call from ThreadX.</span></span>|
| <span data-ttu-id="888fd-203">***txm_module_manager_start.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-203">***txm_module_manager_start.c***</span></span> | <span data-ttu-id="888fd-204">Запускает процедуру выполнения модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-204">Starts execution of a module.</span></span> |
| <span data-ttu-id="888fd-205">***txm_module_manager_stop.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-205">***txm_module_manager_stop.c***</span></span> | <span data-ttu-id="888fd-206">Останавливает процедуру выполнения модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-206">Stops execution of a module.</span></span> |
| <span data-ttu-id="888fd-207">***txm_module_manager_thread_create.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-207">***txm_module_manager_thread_create.c***</span></span> | <span data-ttu-id="888fd-208">Создает все потоки модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-208">Creates all module threads.</span></span> |
| <span data-ttu-id="888fd-209">***txm_module_manager_thread_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-209">***txm_module_manager_thread_notify_trampoline.c***</span></span> | <span data-ttu-id="888fd-210">Обрабатывает вызов уведомления о входе/выходе потока из ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-210">Processes the thread entry/exit notification call from ThreadX.</span></span> |
| <span data-ttu-id="888fd-211">***txm_module_manager_thread_reset.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-211">***txm_module_manager_thread_reset.c***</span></span> | <span data-ttu-id="888fd-212">Сбросить поток модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-212">Reset a module thread.</span></span> |
| <span data-ttu-id="888fd-213">***txm_module_manager_timer_notify_trampoline.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-213">***txm_module_manager_timer_notify_trampoline.c***</span></span> | <span data-ttu-id="888fd-214">Обрабатывает истечения таймера из ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-214">Processes timer expirations from ThreadX.</span></span> |
| <span data-ttu-id="888fd-215">***txm_module_manager_unload.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-215">***txm_module_manager_unload.c***</span></span> | <span data-ttu-id="888fd-216">Выгружает модуль из области памяти модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-216">Unloads the module from the module memory area.</span></span> |
| <span data-ttu-id="888fd-217">***txm_module_manager_util.c***</span><span class="sxs-lookup"><span data-stu-id="888fd-217">***txm_module_manager_util.c***</span></span> | <span data-ttu-id="888fd-218">Внутренние вспомогательные функции для менеджера.</span><span class="sxs-lookup"><span data-stu-id="888fd-218">Internal helper functions for manager.</span></span> |

## <a name="module-manager-initialization"></a><span data-ttu-id="888fd-219">Инициализация диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-219">Module Manager initialization</span></span>

<span data-ttu-id="888fd-220">Резидентная часть приложения отвечает за вызов функции инициализации диспетчера модулей ***txm_module_manager_initialize***.</span><span class="sxs-lookup"><span data-stu-id="888fd-220">The resident portion of the application is responsible for calling the Module Manager initialization function ***txm_module_manager_initialize***.</span></span> <span data-ttu-id="888fd-221">Данная функция устанавливает внутренние структуры для загрузки и выгрузки модулей, включая настройку области памяти, используемой для распределения памяти модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-221">This function sets up the internal structures for loading and unloading modules, including setting up the memory area used for allocating module memory.</span></span>

## <a name="module-manager-loading"></a><span data-ttu-id="888fd-222">Загрузка диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-222">Module Manager loading</span></span>

<span data-ttu-id="888fd-223">Диспетчер модулей может динамически загружать модули в память модуля из файлов двоичных модулей или из раздела кода модуля, который уже присутствует в области резидентного кода.</span><span class="sxs-lookup"><span data-stu-id="888fd-223">The Module Manager can load modules dynamically into the module memory from binary module files or from a module code section that is already present in the resident code area.</span></span> <span data-ttu-id="888fd-224">Помимо этого, диспетчер модулей может выполнять код на месте, то есть только данные модуля размещаются в памяти модуля, а выполнение кода выполняется на месте.</span><span class="sxs-lookup"><span data-stu-id="888fd-224">In addition, the module manager can execute code in place, that is, only the module data is allocated in the module memory and the code execution is done in place.</span></span> <span data-ttu-id="888fd-225">Доступны следующие функции API загрузки диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="888fd-225">The following Module Manager load API functions are available.</span></span>

* <span data-ttu-id="888fd-226">***txm_module_manager_file_load***</span><span class="sxs-lookup"><span data-stu-id="888fd-226">***txm_module_manager_file_load***</span></span>

* <span data-ttu-id="888fd-227">***txm_module_manager_in_place_load***</span><span class="sxs-lookup"><span data-stu-id="888fd-227">***txm_module_manager_in_place_load***</span></span>

* <span data-ttu-id="888fd-228">***txm_module_manager_memory_load***</span><span class="sxs-lookup"><span data-stu-id="888fd-228">***txm_module_manager_memory_load***</span></span>

<span data-ttu-id="888fd-229">Версия менеджера модулей с защищенной памятью также гарантирует, что модуль загружен с правильным выравниванием, а регистры управления памятью настроены правильно для каждого модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-229">The memory protected version of the Module Manager also makes sure that the module is loaded with the proper alignment and the memory management registers are set up properly for each module.</span></span> <span data-ttu-id="888fd-230">Когда защита памяти включается посредством начальных опций модуля, доступ к памяти модуля ограничивается областями кода модуля и данных.</span><span class="sxs-lookup"><span data-stu-id="888fd-230">When memory protection is enabled via the module preamble options, module memory access is restricted to the module code and data areas.</span></span>

## <a name="module-manager-starting"></a><span data-ttu-id="888fd-231">Запуск диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-231">Module Manager starting</span></span>

<span data-ttu-id="888fd-232">Диспетчер модулей инициирует выполнение ранее загруженного модуля через функцию API ***txm_module_manager_start***.</span><span class="sxs-lookup"><span data-stu-id="888fd-232">The Module Manager initiates execution of a previously-loaded module via the ***txm_module_manager_start*** API function.</span></span> <span data-ttu-id="888fd-233">Чтобы инициировать выполнение модуля, данная функция создает поток, который входит в модуль в начальной позиции, указанной в начальной части модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-233">To initiate module execution, this function creates a thread that enters the module at the starting location specified in the module preamble.</span></span> <span data-ttu-id="888fd-234">Приоритет и размер стека данного потока также указываются в начальной части модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-234">The priority and stack size of this thread is also specified in the module preamble.</span></span>

## <a name="module-manager-stopping"></a><span data-ttu-id="888fd-235">Остановка диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-235">Module Manager stopping</span></span>

<span data-ttu-id="888fd-236">Диспетчер модулей прекращает выполнение ранее загруженного и выполняющегося модуля с помощью функции ***txm_module_manager_stop***.</span><span class="sxs-lookup"><span data-stu-id="888fd-236">The Module Manager terminates execution of a previously-loaded and executing module via the ***txm_module_manager_stop*** function.</span></span> <span data-ttu-id="888fd-237">Данная функция API сначала завершает работу и удаляет начальный запуск потоков.</span><span class="sxs-lookup"><span data-stu-id="888fd-237">This API function first terminates and deletes the initial starting thread.</span></span> <span data-ttu-id="888fd-238">Если в начальной части модуля указан стоп-поток, данный поток создается и выполняется.</span><span class="sxs-lookup"><span data-stu-id="888fd-238">If the module preamble specifies a stop thread, this thread is created and executed.</span></span> <span data-ttu-id="888fd-239">Диспетчер модулей ожидает завершения потока остановки в течение фиксированного периода времени.</span><span class="sxs-lookup"><span data-stu-id="888fd-239">The Module Manager waits for a fixed period of time for the stop thread to complete.</span></span> <span data-ttu-id="888fd-240">После завершения все системные ресурсы, созданные модулем, удаляются, и модуль переводится в неактивное состояние, из которого он может быть либо перезапущен, либо выгружен.</span><span class="sxs-lookup"><span data-stu-id="888fd-240">Once complete, all system resources created by the module are deleted and the module is placed in a dormant state, from which it can be either restarted or unloaded.</span></span>

## <a name="module-manager-unloading"></a><span data-ttu-id="888fd-241">Разгрузка диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-241">Module Manager unloading</span></span>

<span data-ttu-id="888fd-242">Диспетчер модулей выгружает ранее загруженный, но не выполняющийся модуль посредством функции ***txm_module_manager_unload***.</span><span class="sxs-lookup"><span data-stu-id="888fd-242">The Module Manager unloads a previously-loaded but not executing module via the ***txm_module_manager_unload*** function.</span></span> <span data-ttu-id="888fd-243">Данный API освобождает всю память, связанную с модулем, освобождая ее для использования с другим модулем в будущем.</span><span class="sxs-lookup"><span data-stu-id="888fd-243">This API releases all memory associated with the module, freeing it for use with another module in the future.</span></span>

## <a name="module-manager-requests"></a><span data-ttu-id="888fd-244">Запросы диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-244">Module Manager requests</span></span>

<span data-ttu-id="888fd-245">Запросы модулей к диспетчеру модулей выполняются с помощью макросов в ***txm_module.h***, которые отображают все вызовы ThreadX для вызова диспетчерской функции диспетчера модулей через указатель функции, передаваемый модулю диспетчером модулей.</span><span class="sxs-lookup"><span data-stu-id="888fd-245">Requests made by modules to the Module Manager are done via macros in ***txm_module.h*** that map all ThreadX calls to call the Module Manager dispatch function via a function pointer supplied to the module by the Module Manager.</span></span>

<span data-ttu-id="888fd-246">Дополнительные сервисы для конкретных приложений, созданные с помощью модуля, вызывающего ***txm_module_application_request***, обрабатываются тем же механизмом макросов, который используется для ThreadX API.</span><span class="sxs-lookup"><span data-stu-id="888fd-246">Additional application-specific services made via the module calling ***txm_module_application_request*** are handled by the same macro mechanism used for the ThreadX API.</span></span> <span data-ttu-id="888fd-247">По умолчанию данная функция обработки в диспетчере модулей пуста и разработана таким образом, что приложение добавляет необходимый код для обработки запросов, специфичных для приложения.</span><span class="sxs-lookup"><span data-stu-id="888fd-247">By default, this handling function in the Module Manager is empty and designed such that the application adds the necessary code to process the application-specific requests.</span></span>

<span data-ttu-id="888fd-248">Если запрос не реализован диспетчером модулей, диспетчер модулей возвращает значение состояния ошибки **TX_NOT_AVAILABLE**.</span><span class="sxs-lookup"><span data-stu-id="888fd-248">If the request is not implemented by the Module Manager, a value of **TX_NOT_AVAILABLE** error status is returned by the Module Manager.</span></span> <span data-ttu-id="888fd-249">Данный код ошибки также возвращается, если модуль запрашивает операцию, выходящую за рамки доступа модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-249">This error code is also returned if the module requests an operation that is outside the scope of the module's access.</span></span> <span data-ttu-id="888fd-250">Например, модулю не разрешается создавать таймер с блоком управления таймером или адресом обратного вызова вне области кода модуля.</span><span class="sxs-lookup"><span data-stu-id="888fd-250">For example, a module is not allowed to create a timer with the timer control block or callback address outside of the module's code area.</span></span>

## <a name="module-manager-example"></a><span data-ttu-id="888fd-251">Пример диспетчера модуля</span><span class="sxs-lookup"><span data-stu-id="888fd-251">Module Manager example</span></span>

<span data-ttu-id="888fd-252">Ниже приведен пример кода диспетчера модулей, запускающего модуль-пример, ранее определенный в Главе 2.</span><span class="sxs-lookup"><span data-stu-id="888fd-252">The following is an example of Module Manager code that launches the example module previously defined in Chapter 2.</span></span> <span data-ttu-id="888fd-253">Предполагается, что модуль уже загружен, предположительно отладчиком, по адресу ПЗУ 0x00800000.</span><span class="sxs-lookup"><span data-stu-id="888fd-253">It is assumed that the module is already loaded, presumably by the debugger, at ROM address 0x00800000.</span></span>

```c
#include "tx_api.h"
#include "txm_module.h"

#define DEMO_STACK_SIZE 1024

/* Define the ThreadX object control blocks. */
TX_THREAD   module_manager;

/* Define thread prototype. */
void        module_manager_entry(ULONG thread_input);

/* Define the module object pool area. */
UCHAR       object_memory[8192];

/* Define the module data pool area. */
#define MODULE_DATA_SIZE 65536
UCHAR       module_data_area[MODULE_DATA_SIZE];

/* Define module instances. */
TXM_MODULE_INSTANCE     my_module1;
TXM_MODULE_INSTANCE     my_module2;

/* Define the count of memory faults. */
ULONG memory_faults;

/* Define fault handler. */
VOID module_fault_handler(TX_THREAD *thread, TXM_MODULE_INSTANCE *module)
{
    /* Just increment the fault counter. */
    memory_faults++;
}

/* Define main entry point. */
int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    /* Create the module manager thread. */
    tx_thread_create(&module_manager, "Module Manager Thread", module_manager_entry, 0,
                    first_unused_memory, DEMO_STACK_SIZE,
                    1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

/* Define the test threads. */
void module_manager_entry(ULONG thread_input)
{
    /* Initialize the module manager. */
    txm_module_manager_initialize((VOID *) module_data_area, MODULE_DATA_SIZE);

    /* Create a pool for module objects. */
    txm_module_manager_object_pool_create(object_memory, sizeof(object_memory));

    /* Register a fault handler. */
    txm_module_manager_memory_fault_notify(module_fault_handler);

    /* Load the module that is already there,
        in this example it is placed at 0x00800000. */
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Load a second instance of the module. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);

    /* Enable shared memory region for module2. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);

    /* Start the modules. */
    txm_module_manager_start(&my_module1);
    txm_module_manager_start(&my_module2);

    /* Sleep for a while and let the modules run... */
    tx_thread_sleep(300);

    /* Stop the modules. */
    txm_module_manager_stop(&my_module1);
    txm_module_manager_stop(&my_module2);

    /* Unload the modules. */
    txm_module_manager_unload(&my_module1);
    txm_module_manager_unload(&my_module2);

    /* Reload the modules. */
    txm_module_manager_in_place_load(&my_module2, "my module2", (VOID *) 0x00800000);
    txm_module_manager_in_place_load(&my_module1, "my module1", (VOID *) 0x00800000);

    /* Give both modules shared memory. */
    txm_module_manager_external_memory_enable(&my_module2, (void*)0x20600000, 0x010000, 0x3F);
    txm_module_manager_external_memory_enable(&my_module1, (void*)0x20600000, 0x010000, 0x3F);

    /* Set maximum module1 priority to 5. */
    txm_module_manager_maximum_module_priority_set(&my_module1, 5);

    /* Start the modules again. */
    txm_module_manager_start(&my_module2);
    txm_module_manager_start(&my_module1);

    /* Now just spin... */
    while(1)
    {
        tx_thread_sleep(100);

        /* Threads 0 and 5 in module1 are not created because they violate the maximum priority. */
    }
}
```

## <a name="module-manager-building"></a><span data-ttu-id="888fd-254">Создание диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="888fd-254">Module Manager building</span></span>

<span data-ttu-id="888fd-255">Исходные файлы ***txm_module_manager_\**** необходимо добавить в библиотеку ThreadX.</span><span class="sxs-lookup"><span data-stu-id="888fd-255">The ***txm_module_manager_\**** source files must be added to the ThreadX library.</span></span>

<span data-ttu-id="888fd-256">Приложение ThreadX Module Manager является фактически тем же самым, что и стандартное приложение ThreadX, которое представляет собой один или несколько файлов приложения, связанных вместе с библиотекой ThreadX ***tx.a***.</span><span class="sxs-lookup"><span data-stu-id="888fd-256">A ThreadX Module Manager application is effectively the same as a standard ThreadX application, which is one or more application files linked together with the ThreadX library ***tx.a***.</span></span> <span data-ttu-id="888fd-257">Создание приложения-менеджера модулей зависит от используемой цепочки инструментов.</span><span class="sxs-lookup"><span data-stu-id="888fd-257">Building a module manager application is dependent on the tool chain being used.</span></span> <span data-ttu-id="888fd-258">Примеры для конкретных портов см. в [Приложении](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="888fd-258">See [appendix](appendix.md) for port-specific examples.</span></span>
