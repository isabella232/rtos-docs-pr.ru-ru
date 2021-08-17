---
title: Глава 5. API-интерфейсы диспетчера модулей
author: philmea
description: Эта статья представляет сводные данные API-интерфейсов диспетчера модулей, доступных для резидентной части приложения.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8e4da0f9591fd0b5d6249292f00266d96ccb67923c42632a4cfd8c39fa1f129
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799121"
---
# <a name="chapter-5---module-manager-apis"></a>Глава 5. API-интерфейсы диспетчера модулей

## <a name="summary-of-module-manager-apis"></a>Сводка по API-интерфейсам диспетчера модулей

Существует несколько дополнительных API, доступных для резидентной части приложения. Они перечислены ниже.

- ***txm_module_manager_external_memory_enable** _ — _разрешить доступ модуля к общей памяти*
- ***txm_module_manager_file_load** _ — _загрузить модуль из файла с помощью FileX*
- ***txm_module_manager_in_place_load** _ — _загрузить данные модуля, выполнение на месте*
- ***txm_module_manager_initialize** _ — _инициализация диспетчера модулей*
- ***txm_module_manager_mm_initialize** _ — _инициализация оборудования для управления памятью*
- ***txm_module_manager_maximum_module_priority_set** _ — _установить максимальный приоритет потока, разрешенный в модуле*
- ***txm_module_manager_memory_fault_notify** _ — _регистрация обратного вызова приложения при сбое памяти*
- ***txm_module_manager_memory_load** _ — _загрузить модуль из памяти*
- ***txm_module_manager_object_pool_create** _ — _создать пул объектов для модулей*
- ***txm_module_manager_properties_get** _ — _получить свойства модуля*
- ***txm_module_manager_start** _ — _начать выполнение указанного модуля*
- ***txm_module_manager_stop** _ — _прервать выполнение указанного модуля*
- ***txm_module_manager_unload** _ — _выгрузить модуль*

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Разрешить модулю доступ к общему пространству памяти.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Описание

Эта служба создает запись в таблице оборудования управления памятью для области общей памяти, к которой модуль может получить доступ.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.
- **start_address** — начальный адрес области общей памяти.
- **length** — длина области общей памяти.
- **attributes** — атрибуты области памяти (кэш, чтение, запись и т. д.). Атрибуты зависят от конкретного порта. Формат атрибутов см. в [приложении](appendix.md).

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — запись в памяти успешно создана.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован или функция недоступна.
- **TX_PTR_ERROR** (0x03) — недопустимый экземпляр модуля.
- **TX_START_ERROR** (0x10) — модуль не находится в загруженном состоянии.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание начального адреса.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

Загрузка модуля из файла с помощью FileX.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Описание

Эта служба загружает двоичный образ модуля, содержащегося в указанном файле, в область памяти модуля и готовит его к выполнению. Предполагается, что указанный носитель уже открыт.

> [!NOTE]
> Для загрузки файла используется система FileX. Чтобы включить доступ к FileX, модуль, библиотека модулей, диспетчер модулей и библиотека ThreadX (с исходным кодом диспетчера модулей) должны быть построены с параметром **FX_FILEX_PRESENT**, определенным в проектах.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.
- **module_name** — имя модуля.
- **media_ptr** — указатель на уже открытый носитель FileX.
- **file_name** — имя двоичного файла модуля.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная загрузка модуля.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_NO_MEMORY** (0x10) — недостаточно памяти для загрузки модуля.
- **TX_NOT_DONE** (0x20) — не удалось открыть носитель, файл не найден или недопустимый файл.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на модуль.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) — модуль уже загружен.
- **TXM_MODULE_INVALID** (0xF2) — недопустимая преамбула модуля.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

Загружать только данные модуля, выполнять модуль в существующем расположении.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Описание

Эта служба загружает область данных модуля только в область памяти модуля и готовит ее к выполнению. Выполнение кода модуля будет выполняться на месте, то есть из смещения адреса, указанного в преамбуле модуля в указанном расположении.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.
- **module_name** — имя модуля.
- **location** — указатель на область кода модуля, сначала преамбула.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная загрузка модуля.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_NO_MEMORY** (0x10) — недостаточно памяти для загрузки модуля.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель, экземпляр модуля или преамбула модуля.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) — модуль уже загружен.
- **TXM_MODULE_INVALID** (0xF2) — недопустимая преамбула модуля.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Пример

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

Инициализация диспетчера модулей.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Описание

Эта служба инициализирует внутренние ресурсы диспетчера модулей, включая область памяти, используемую для загрузки модулей.

### <a name="input-parameters"></a>Входные параметры

- **module_memory_start** — указатель на начало памяти модуля.
- **module_memory_size** — размер памяти модуля в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная инициализация.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Пример

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

Инициализация оборудования для управления памятью.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Описание

Эта служба инициализирует MMU.

### <a name="input-parameters"></a>Входные параметры

нет

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная инициализация.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

Установка максимального приоритета потока, разрешенного в модуле.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Описание

Эта служба устанавливает максимальный приоритет потока, разрешенный в модуле.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.
- **priority** — максимальный приоритет потока.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная инициализация.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_PTR_ERROR** (0x03) — недопустимый экземпляр модуля.
- **TX_START_ERROR** (0x10) — модуль не находится в загруженном состоянии.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

Регистрация обратного вызова приложения при сбое памяти.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Описание

Эта служба регистрирует указанную функцию обратного вызова уведомления о сбое в памяти приложения в диспетчере модулей. В случае сбоя памяти эта функция вызывается с указателем на вызывающий ошибку поток и экземпляр модуля, соответствующий вызывающему ошибку потоку. Обработка диспетчера модулей автоматически завершает вызывающий ошибку поток, но оставляет все остальные потоки в модуле нетронутыми. Приложение может решить, что делать с модулем, связанным с ошибкой памяти.

Дополнительные сведения об ошибках в памяти см. во внутренней структуре **_txm_module_manager_memory_fault_info**.

> [!NOTE]
> Функция обратного вызова для уведомления о сбое в памяти выполняется непосредственно из исключения ошибки памяти, поэтому можно вызывать только API-интерфейсы ThreadX, разрешенные из подпрограмм службы прерываний. Таким образом, для остановки и выгрузки модуля, вызывающего ошибку, обратный вызов уведомления приложения должен отправить сигнал задаче приложения, чтобы модуль можно было остановить и выгрузить.

### <a name="input-parameters"></a>Входные параметры

- **notify_function** — указатель на функцию обратного вызова уведомления о сбое в памяти приложения. При указании значения NULL уведомление о сбое в памяти отключается.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная регистрация функции уведомления.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

Загрузка модуля из памяти.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Описание

Эта служба загружает код модуля и область данных в область памяти модуля, настроенную с помощью ***txm_module_manager_initialize***, и готовит его к выполнению.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.
- **module_name** — имя модуля.
- **location** — указатель на область кода модуля, сначала преамбула.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная загрузка модуля.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_NO_MEMORY** (0x10) — недостаточно памяти для загрузки модуля.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель, экземпляр модуля или преамбула модуля.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) — модуль уже загружен.
- **TXM_MODULE_INVALID** (0xF2) — недопустимая преамбула модуля.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Пример

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

Создание пула объектов для модулей.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Описание

Эта служба создает пул памяти объектов диспетчера модулей, из которого модули могут распределять объекты ThreadX и NetX, тем самым оставляя системный объект вне области памяти модуля.

### <a name="input-parameters"></a>Входные параметры

- **pool_memory_start** — указатель на начало памяти объекта.
- **pool_memory_size** — размер пула памяти объектов в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная инициализация.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Пример

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

Получение свойств модуля.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Описание

Эта служба возвращает свойства модуля (указанные в преамбуле).

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.
- **module_properties_ptr** — указатель на назначение для свойств модуля.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная инициализация.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

Запуск выполнения модуля.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Описание

Эта служба запускает выполнение указанного и уже загруженного модуля.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на ранее загруженный экземпляр модуля.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешный запуск модуля.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель или экземпляр модуля.
- **TX_START_ERROR** (0x10) — модуль уже запущен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Пример

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

Прерывание выполнения модуля.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Описание

Эта служба останавливает ранее загруженный и запущенный модуль. Остановка модуля включает в себя выполнение необязательного потока остановки модуля, завершение всех потоков и удаление всех ресурсов, связанных с модулем.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная остановка модуля.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель или экземпляр модуля.
- **TX_START_ERROR** (0x10) — модуль на запущен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

Выгрузка модуля.

### <a name="prototype"></a>Прототип

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Описание

Эта служба выгружает ранее загруженный и остановленный модуль, освобождая все связанные ресурсы памяти модуля.

### <a name="input-parameters"></a>Входные параметры

- **module_instance** — указатель на экземпляр модуля.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная выгрузка модуля.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.
- **TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.
- **TX_NOT_DONE** (0x20) — недопустимый модуль или модуль не остановлен.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель или экземпляр модуля.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Пример

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>См. также раздел

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
