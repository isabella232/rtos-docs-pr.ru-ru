---
title: Глава 3. API-интерфейсы ThreadX для архитектуры ARMv8-M
description: В этой главе содержится описание служб ThreadX, относящихся к архитектуре ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99633db55a5d93eb32ce4fb5429f3fe2f9ab5137cffc30b27982f702cece1ca5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791505"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a>Глава 3. API-интерфейсы ThreadX для архитектуры ARMv8-M

В этой главе содержится описание служб ThreadX, относящихся к архитектуре ARMv8-M. Службы указаны в алфавитном порядке. Их имена реализованы так, что все аналогичные службы группируются вместе. В разделе "Возвращаемые значения" приведенных ниже описаний **выделенные полужирным шрифтом** значения не затрагиваются определением **TX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены.

- [tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Выделение стека потоков в защищенной памяти.
- [tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Высвобождение стека потоков в защищенной памяти.

## <a name="tx_thread_secure_stack_allocate"></a>tx_thread_secure_stack_allocate

Выделение стека потоков в защищенной памяти.

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a>Описание

Эта служба выделяет стек размером stack_size байт в защищенной памяти. Эта функция должна вызываться для каждого потока, который вызывает безопасные функции.

### <a name="input-parameters"></a>Входные параметры

- **ip_ptr** Указатель на ранее созданный поток.

- **stack_size** Размер безопасного стека.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) Запрос выполнен.

- **TX_SIZE_ERROR** (0x05) Размер стека вне допустимого диапазона.

- **TX_THREAD_ERROR** (0x0E) Недопустимый указатель потока.

- **TX_NO_MEMORY** (0x10) Не удалось выделить память.

- **NX_CALLER_ERROR (0x13)** Недопустимый вызывающий объект для этой службы.

- **TX_FEATURE_NOT_ENABLED** (0xFF) Система была скомпилирована для запуска в безопасном режиме.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a>См. также:

tx_thread_secure_stack_free

##  <a name="tx_thread_secure_stack_free"></a>tx_thread_secure_stack_free

Высвобождение стека потоков в защищенной памяти. 

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Описание

Эта служба высвобождает безопасный стек потоков в защищенной памяти. Эта функция должна вызываться, если поток имеет безопасный стек и когда потоку больше не требуется вызывать безопасные функции либо поток удален.

### <a name="input-parameters"></a>Входные параметры

- **ip_ptr** Указатель на ранее созданный поток.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) Запрос выполнен.

- **TX_THREAD_ERROR** (0x0E) Недопустимый указатель потока.

- **NX_CALLER_ERROR (0x13)** Недопустимый вызывающий объект для этой службы.

- **TX_FEATURE_NOT_ENABLED** (0xFF) Система была скомпилирована для запуска в безопасном режиме.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a>См. также:

tx_thread_secure_stack_allocate
