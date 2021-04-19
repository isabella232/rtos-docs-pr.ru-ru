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
# <a name="chapter-3---module-manager-requirements"></a>Глава 3 - Требования к диспетчеру модулей

Диспетчер модулей ThreadX находится в резидентной части приложения вместе с ОСРВ ThreadX. Диспетчер отвечает за запуск модуля, а также за отправку и отправку всех запросов модуля для служб ThreadX API.

> [!NOTE]
> Исходные файлы модуля ThreadX **Manager** (C и сборка) следует добавить в проект библиотеки ThreadX "**tx**".

Для создания диспетчера модулей ThreadX необходимы следующие шаги (каждый шаг более подробно описан ниже).

1. Блок управления **TX_THREAD** должен быть расширен для включения информации о модуле. Самый простой способ добиться этого - заменить определение **TX_THREAD_EXTENSION_2** в файле **_tx_port.h_ *_ на _* TX_THREAD_EXTENSION_2** в **_txm_module_port.h_**. См. [приложение](appendix.md) для расширений для конкретных портов.

Пример расширения:

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

   Следующие расширения должны быть определены в ***tx_port.h***.

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

2. Добавьте все файлы C и сборки ***txm_module_manager_\****  в проект библиотеки ThreadX **_tx_**.
3. Перестройте все библиотеки и исполняемые проекты. Если требуется NetX Duo, весь C-код модулей и диспетчера модулей должен быть построен с определением **TXM_MODULE_ENABLE_NETX_DUO**.

## <a name="module-manager-sources"></a>Источники диспетчера модулей

В диспетчере модулей ThreadX имеется набор исходных файлов, которые предназначены для связывания и размещения непосредственно с резидентным кодом ThreadX. Данные файлы предоставляют возможность запускать модуль и отправлять последующие запросы ThreadX API от модуля. Файлы диспетчера модулей выглядят следующим образом.

| **Имя файла** |  **Contents** |
|-------------- | ------------- |
| ***txm_module.h*** | Включить файл, определяющий информацию о модуле (также включен в исходный код модуля). |
| ***txm_module_manager_dispatch.h*** | Включить файл, определяющий вспомогательные функции диспетчеризации.|
| ***txm_module_manager_util.h*** | Включить файл, определяющий внутренние вспомогательные макросы и функции служебных программ. |
| ***txm_module_port.h*** | Включить файл, определяющий информацию о модуле для конкретного порта (также включен в исходный код модуля). |
| ***tx_initialize_low_level.\[s,S,68\]** _ | Заменяет существующий файл библиотеки ThreadX. Обновленная таблица векторов и дополнительные обработчики векторов для диспетчера модулей и исключений памяти. _Данный файл присутствует только в Cortex-A7/ARM, Cortex-M7/ARM, Cortex-R4/ARM, Cortex-R4/IAR, MCF544xx/GHS, RX63/IAR, RX65N/IAR.*|
| ***tx_thread_context_restore.s** _ | Заменяет существующий файл библиотеки ThreadX. Восстановить контекст потока после обработки прерывания. _Данный файл присутствует только в Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***tx_thread_schedule.\[s,S,68\]*** | Заменяет существующий файл библиотеки ThreadX. Расширенный экземпляр планировщика, используемый в данном случае для обновления регистров управления памятью. |
| ***tx_thread_stack_build.s** _ | Заменяет существующий файл библиотеки ThreadX. Создает стековый фрейм потока. _Данный файл присутствует только в Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_thread_stack_build.\[s,S,68\]*** | Создает все начальные стеки модулей, включает настройку для независимого от позиции доступа к данным. |
| ***txm_module_manager_user_mode_entry.\[s,S\]** _ | Позволяет модулю войти в режим ядра. _Данный файл присутствует только в Cortex-A7/ARM, Cortex-R4/ARM, Cortex-R4/IAR.*|
| ***txm_module_manager_alignment_adjust.c*** | Обрабатывает требования к выравниванию для конкретных портов.|
| ***txm_module_manager_application_request.c*** | Обрабатывает специфичные для приложения запросы к резидентному коду. |
| ***txm_module_manager_callback_request.c*** | Отправляет запрос обратного вызова в модуль. |
| ***txm_module_manager_event_flags_notify_trampoline.c*** | Обрабатывает вызов уведомления о наборе флагов событий из ThreadX. |
| ***txm_module_manager_external_memory_enable.c*** | Создает запись в таблице управления памятью для области разделяемой памяти, к которой модуль может получить доступ. |
| ***txm_module_manager_file_load.c*** | Выделяет и загружает двоичный файл модуля в область памяти модуля и подготавливает его к выполнению. |
| ***txm_module_manager_in_place_load.c*** | Выделяет область данных модуля и готовится к выполнению модуля с предоставленного кодового адреса. |
| ***txm_module_manager_initialize.c*** | Инициализирует диспетчер модулей, включая указание области памяти модуля, доступной для загрузки и запуска модулей. |
| ***txm_module_manager_initialize_mmu.c** _ | Инициализировать MMU. Пользователи могут редактировать данный файл в соответствии со своей картой памяти. _Данный файл присутствует только в Cortex-A7/ARM* |
| ***txm_module_manager_mm_initialize.c** _ | Инициализировать MPU/MMU. Пользователи могут редактировать данный файл в соответствии со своей картой памяти. _Данный файл присутствует только в Cortex-A7/ARM* |
| ***txm_module_manager_kernel_dispatch.c*** | Обрабатывает запросы API модуля на основе идентификатора запроса. |
| ***txm_module_manager_maximum_module_priority_set.c*** | Устанавливает максимальный приоритет потока, разрешенный в рамках модуля. |
| ***txm_module_manager_memory_fault_handler.c*** | Обрабатывает ошибки памяти, обнаруженные в исполняющем модуле. |
| ***txm_module_manager_memory_fault_notify.c*** | Регистрирует обратный вызов уведомления приложения всякий раз, когда происходит сбой памяти. |
| ***txm_module_manager_memory_load.c*** | Выделяет и загружает код и данные модуля и подготавливает модуль к процедуре выполнения. |
| ***txm_module_manager_mm_register_setup.c*** | Устанавливает регистры MPU/MMU для модуля в зависимости от того, куда загружены код и данные. |
| ***txm_module_manager_object_allocate.c*** | Выделяет память для объекта модуля. |
| ***txm_module_manager_object_deallocate.c*** | Освобождает память для объекта модуля. |
| ***txm_module_manager_object_pointer_get.c*** | Выполняет поиск предоставленного типа и имени объекта и, если он найден, возвращает указатель объекта. |
| ***txm_module_manager_object_pointer_get_extended.c*** | Выполняет поиск предоставленного типа и имени объекта и, если он найден, возвращает указатель объекта. Длина имени указана для безопасности. |
| ***txm_module_manager_object_pool_create.c***  | Создает пул объектов вне области данных модуля, из которых приложения модуля могут выделять. |
| ***txm_module_manager_properties_get.c*** | Получает свойства указанного модуля. |
| ***txm_module_manager_queue_notify_trampoline.c*** | Обрабатывает вызов уведомления об очереди из ThreadX. |
| ***txm_module_manager_semaphore_notify_trampoline.c*** | Обрабатывает вызов уведомления о размещении семафора из ThreadX.|
| ***txm_module_manager_start.c*** | Запускает процедуру выполнения модуля. |
| ***txm_module_manager_stop.c*** | Останавливает процедуру выполнения модуля. |
| ***txm_module_manager_thread_create.c*** | Создает все потоки модуля. |
| ***txm_module_manager_thread_notify_trampoline.c*** | Обрабатывает вызов уведомления о входе/выходе потока из ThreadX. |
| ***txm_module_manager_thread_reset.c*** | Сбросить поток модуля. |
| ***txm_module_manager_timer_notify_trampoline.c*** | Обрабатывает истечения таймера из ThreadX. |
| ***txm_module_manager_unload.c*** | Выгружает модуль из области памяти модуля. |
| ***txm_module_manager_util.c*** | Внутренние вспомогательные функции для менеджера. |

## <a name="module-manager-initialization"></a>Инициализация диспетчера модулей

Резидентная часть приложения отвечает за вызов функции инициализации диспетчера модулей ***txm_module_manager_initialize***. Данная функция устанавливает внутренние структуры для загрузки и выгрузки модулей, включая настройку области памяти, используемой для распределения памяти модуля.

## <a name="module-manager-loading"></a>Загрузка диспетчера модулей

Диспетчер модулей может динамически загружать модули в память модуля из файлов двоичных модулей или из раздела кода модуля, который уже присутствует в области резидентного кода. Помимо этого, диспетчер модулей может выполнять код на месте, то есть только данные модуля размещаются в памяти модуля, а выполнение кода выполняется на месте. Доступны следующие функции API загрузки диспетчера модулей.

* ***txm_module_manager_file_load***

* ***txm_module_manager_in_place_load***

* ***txm_module_manager_memory_load***

Версия менеджера модулей с защищенной памятью также гарантирует, что модуль загружен с правильным выравниванием, а регистры управления памятью настроены правильно для каждого модуля. Когда защита памяти включается посредством начальных опций модуля, доступ к памяти модуля ограничивается областями кода модуля и данных.

## <a name="module-manager-starting"></a>Запуск диспетчера модулей

Диспетчер модулей инициирует выполнение ранее загруженного модуля через функцию API ***txm_module_manager_start***. Чтобы инициировать выполнение модуля, данная функция создает поток, который входит в модуль в начальной позиции, указанной в начальной части модуля. Приоритет и размер стека данного потока также указываются в начальной части модуля.

## <a name="module-manager-stopping"></a>Остановка диспетчера модулей

Диспетчер модулей прекращает выполнение ранее загруженного и выполняющегося модуля с помощью функции ***txm_module_manager_stop***. Данная функция API сначала завершает работу и удаляет начальный запуск потоков. Если в начальной части модуля указан стоп-поток, данный поток создается и выполняется. Диспетчер модулей ожидает завершения потока остановки в течение фиксированного периода времени. После завершения все системные ресурсы, созданные модулем, удаляются, и модуль переводится в неактивное состояние, из которого он может быть либо перезапущен, либо выгружен.

## <a name="module-manager-unloading"></a>Разгрузка диспетчера модулей

Диспетчер модулей выгружает ранее загруженный, но не выполняющийся модуль посредством функции ***txm_module_manager_unload***. Данный API освобождает всю память, связанную с модулем, освобождая ее для использования с другим модулем в будущем.

## <a name="module-manager-requests"></a>Запросы диспетчера модулей

Запросы модулей к диспетчеру модулей выполняются с помощью макросов в ***txm_module.h***, которые отображают все вызовы ThreadX для вызова диспетчерской функции диспетчера модулей через указатель функции, передаваемый модулю диспетчером модулей.

Дополнительные сервисы для конкретных приложений, созданные с помощью модуля, вызывающего ***txm_module_application_request***, обрабатываются тем же механизмом макросов, который используется для ThreadX API. По умолчанию данная функция обработки в диспетчере модулей пуста и разработана таким образом, что приложение добавляет необходимый код для обработки запросов, специфичных для приложения.

Если запрос не реализован диспетчером модулей, диспетчер модулей возвращает значение состояния ошибки **TX_NOT_AVAILABLE**. Данный код ошибки также возвращается, если модуль запрашивает операцию, выходящую за рамки доступа модуля. Например, модулю не разрешается создавать таймер с блоком управления таймером или адресом обратного вызова вне области кода модуля.

## <a name="module-manager-example"></a>Пример диспетчера модуля

Ниже приведен пример кода диспетчера модулей, запускающего модуль-пример, ранее определенный в Главе 2. Предполагается, что модуль уже загружен, предположительно отладчиком, по адресу ПЗУ 0x00800000.

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

## <a name="module-manager-building"></a>Создание диспетчера модулей

Исходные файлы ***txm_module_manager_\**** необходимо добавить в библиотеку ThreadX.

Приложение ThreadX Module Manager является фактически тем же самым, что и стандартное приложение ThreadX, которое представляет собой один или несколько файлов приложения, связанных вместе с библиотекой ThreadX ***tx.a***. Создание приложения-менеджера модулей зависит от используемой цепочки инструментов. Примеры для конкретных портов см. в [Приложении](appendix.md).
