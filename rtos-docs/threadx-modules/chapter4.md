---
title: Глава 4. API-интерфейсы модуля
author: philmea
ms.author: philmea
description: В этой статье приведена сводка дополнительных API-интерфейсов, доступных для модуля.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814379"
---
# <a name="chapter-4---module-apis"></a>Глава 4. API-интерфейсы модуля

## <a name="summary-of-module-apis"></a>Общие сведения об API-интерфейсах модуля

Существует несколько дополнительных функций API, которые доступны для модуля:

- ***txm_module_application_request** _ — _специфичный для приложения запрос к резидентному коду*
- ***txm_module_object_allocate** _ — _выделение для объекта памяти вне модуля *
- ***txm_module_object_deallocate** _ — _освобождение ранее выделенной памяти объекта*
- ***txm_module_object_pointer_get** _ — _поиск системного объекта и получение указателя на него*
- ***txm_module_object_pointer_get_extended** _ — _поиск системного объекта и получение указателя на него, безопасность длины имени*

## <a name="return-values"></a>Возвращаемые значения

Для некоторых API-интерфейсов ОСРВ Azure возвращаются дополнительные коды ошибок. Эти дополнительные коды ошибок определяются следующим образом.

- **TXM_MODULE_INVALID_PROPERTIES** (0xF3): указывает, что модуль не имеет нужных свойств для вызова API. Например, вызов API трассировки в пользовательском режиме.
- **TXM_MODULE_INVALID_MEMORY** (0xF4): указывает, что память, предоставленная модулем, недопустима или находится в недопустимом расположении. Например, в модулях с защищенной памятью блоки управления объектами не разрешается размещать в памяти, к которой может обращаться модуль.
- **TXM_MODULE_INVALID_CALLBACK** (0xF5): обратный вызов, указанный в API, находится за пределами диапазона кода модуля и поэтому является недопустимым.

---

## <a name="txm_module_application_request"></a>txm_module_application_request

Специфичный для приложения запрос к резидентному коду.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a>Описание

Эта служба выполняет указанный запрос в резидентной части приложения. Предполагается, что структура запроса подготовлена перед вызовом. Фактическая обработка запроса происходит в резидентном коде в функции ***_txm_module_manager_application_request***. По умолчанию эта функция оставлена пустой и предназначена для изменения разработчиком резидентных приложений.

### <a name="input-parameters"></a>Входные параметры

- **request** — идентификатор запроса (определяется приложением).
- **param_1** — первый параметр.
- **param_2** — второй параметр.
- **param_3** — третий параметр.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешный запрос.
- **TX_NOT_AVAILABLE** (0x1D) — запрос не поддерживается резидентным кодом.

### <a name="allowed-from"></a>Разрешено из

Потоки модулей

### <a name="example"></a>Например, .

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a>txm_module_object_allocate

Выделение памяти в пуле объектов (созданном резидентным приложением) для блока управления объекта модуля.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a>Описание

Эта служба выделяет память для объекта модуля из памяти за пределами модуля, что помогает предотвратить повреждение блока управления объектами кодом модуля. В системах с защитой памяти все блоки управления объектами должны быть выделены с помощью этого API, прежде чем их можно будет создать.

### <a name="input-parameters"></a>Входные параметры

- **object_ptr** — назначение указателя объекта при успешном выделении.
- **object_size** — размер выделяемого объекта в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное выделение объекта.
- **TX_NO_MEMORY** (0x10) — недостаточно памяти.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер модулей не создал пул объектов для выделения.

### <a name="allowed-from"></a>Разрешено из

Потоки модулей

### <a name="example"></a>Пример

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a>См. также раздел

- txm_module_object_deallocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_deallocate"></a>txm_module_object_deallocate

Освобождение памяти выделенного ранее объекта

### <a name="prototype"></a>Прототип

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a>Описание

***Эта служба устарела, так как в ней нет больше необходимости***.

Память, выделенная ранее с помощью ***txm_module_object_allocate* *_, освобождается в службе _* _tx_\__delete***.

### <a name="input-parameters"></a>Входные параметры

- **object_ptr** — указатель объекта для освобождения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное выделение объекта.

### <a name="allowed-from"></a>Разрешено из

Потоки модулей

### <a name="example"></a>Пример

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a>См. также раздел

- txm_module_object_allocate
- txm_module_object_pointer_get

---

## <a name="txm_module_object_pointer_get"></a>txm_module_object_pointer_get

Поиск системного объекта и получение указателя на него

### <a name="prototype"></a>Прототип

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a>Описание

Эта служба получает указатель объекта определенного типа с определенным именем. Если объект не найден, возвращается ошибка. В противном случае, если объект найден, адрес этого объекта помещается в "object_ptr". Этот указатель можно затем использовать для вызова системных служб, взаимодействия с резидентным кодом и (или) другими загруженными модулями в системе.

### <a name="input-parameters"></a>Входные параметры

- **object_type** — тип запрошенного объекта ThreadX. Допустимые типы:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** — имя объекта, специфичное для приложения, как определено при создании объекта.
- **object_ptr** — назначение для указателя объекта.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение объекта.
- **TX_OPTION_ERROR** (0x08) — недопустимый тип объекта.
- **TX_PTR_ERROR** (0x03) — недопустимое назначение.
- **TX_SIZE_ERROR** (0x05) — недопустимый размер.
- **TX_NO_INSTANCE** (0x0D) — объект не найден.

### <a name="allowed-from"></a>Разрешено из

Потоки модулей

### <a name="example"></a>Пример

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_object_pointer_get_extended

---

## <a name="txm_module_object_pointer_get_extended"></a>txm_module_object_pointer_get_extended

Поиск системного объекта и получение указателя на него

### <a name="prototype"></a>Прототип

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a>Описание

Эта служба получает указатель объекта определенного типа с определенным именем. Если объект не найден, возвращается ошибка. В противном случае, если объект найден, адрес этого объекта помещается в "object_ptr". Этот указатель можно затем использовать для вызова системных служб, взаимодействия с резидентным кодом и (или) другими загруженными модулями в системе.

### <a name="input-parameters"></a>Входные параметры

- **object_type** — тип запрошенного объекта ThreadX. Допустимые типы:
  - TXM_BLOCK_POOL_OBJECT
  - TXM_BYTE_POOL_OBJECT
  - TXM_EVENT_FLAGS_OBJECT
  - TXM_MUTEX_OBJECT
  - TXM_QUEUE_OBJECT
  - TXM_SEMAPHORE_OBJECT
  - TXM_THREAD_OBJECT
  - TXM_TIMER_OBJECT
  - TXM_IP_OBJECT
  - TXM_PACKET_POOL_OBJECT
  - TXM_UDP_SOCKET_OBJECT
  - TXM_TCP_SOCKET_OBJECT
- **name** — имя объекта, специфичное для приложения, как определено при создании объекта.
- **name_length** — длина имени.
- **object_ptr** — назначение для указателя объекта.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение объекта.
- **TX_OPTION_ERROR** (0x08) — недопустимый тип объекта.
- **TX_PTR_ERROR** (0x03) — недопустимое назначение.
- **TX_SIZE_ERROR** (0x05) — недопустимый размер.
- **TX_NO_INSTANCE** (0x0D) — объект не найден.

### <a name="allowed-from"></a>Разрешено из

Потоки модулей

### <a name="example"></a>Пример

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_object_pointer_get
