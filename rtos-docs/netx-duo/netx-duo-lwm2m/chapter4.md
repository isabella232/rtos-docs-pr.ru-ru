---
title: Глава 4 - Описание услуг LWM2M CLIENT
description: Эта глава содержит описание всех клиентских служб LWM2M в алфавитном порядке.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814672"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a>Глава 4 Описание услуг LWM2M CLIENT

В данной главе приводится описание всех нижеперечисленных клиентских сервисов LWM2M в алфавитном порядке.

В разделе «Возвращаемые значения» в следующих описаниях API значения, выделенные полужирным шрифтом **BOLD**, не зависят от определения **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные жирным шрифтом, полностью отключены.

**Управление клиентом LWM2M:**

- nx_lwm2m_client_create: *Создать клиент LWM2M*

- nx_lwm2m_client_delete: *Удалить клиент LWM2M*

- nx_lwm2m_client_lock: *Заблокировать клиент LWM2M*

- nx_lwm2m_client_unlock: *Разблокировать клиент LWM2M*

**Управление клиентскими сеансами LWM2M:**

- nx_lwm2m_client_session_create: *Создать клиентский сеанс LWM2M*

- nx_lwm2m_client_session_delete: *Удалить клиентский сеанс LWM2M*

- nx_lwm2m_client_session_bootstrap: *Начать сеанс с Bootstrap Server*

- nx_lwm2m_client_session_bootstrap_dtls: *Начать безопасный сеанс с Bootstrap Server*

- nx_lwm2m_client_session_register_info_get: *Получить информацию о регистрации сервера LWM2M*

- nx_lwm2m_client_session_register: *Начать сеанс с сервером LWM2M*

- nx_lwm2m_client_session_register_dtls: *Начать безопасный сеанс с сервером LWM2M*

- nx_lwm2m_client_session_update: *Обновить сеанс с сервером LWM2M*

- nx_lwm2m_client_session_deregister: *Завершить сеанс с сервером LWM2M*

- nx_lwm2m_client_session_error_get: *Получить сведения о последней ошибке сеанса*

**Реализация объекта устройства:**

- nx_lwm2m_client_device_callbacks_set: *Установить обратные вызовы приложения объекта устройства*

- nx_lwm2m_client_device_error_push: *Добавить код ошибки в объект устройства*

- nx_lwm2m_client_device_error_reset: *Сбросить коды ошибок объекта устройства*

- nx_lwm2m_client_device_resource_changed: *Изменение сигнала ресурса объекта устройства*

**Реализация объекта обновления встроенного ПО:**

- nx_lwm2m_firmware_create: *Создать объект обновления встроенного ПО*

- nx_lwm2m_firmware_package_info_set: *Установить информацию о пакете обновления встроенного ПО*

- nx_lwm2m_firmware_result_set: *Установить результат обновления встроенного ПО*

- nx_lwm2m_firmware_state_set: *Установить состояние обновления встроенного ПО*

**Реализация пользовательских объектов:**

- nx_lwm2m_client_object_add: *Добавить реализацию объекта в клиент LWM2M*

- nx_lwm2m_client_object_remove: *Удалить реализацию объекта из клиента LWM2M*

- nx_lwm2m_client_object_instance_add: *Добавить экземпляр объекта в клиент LWM2M*

- nx_lwm2m_client_object_instance_remove: *Удалить экземпляр объекта из клиента LWM2M*

- nx_lwm2m_object_resource_changed: *Сигнальное изменение значения ресурса экземпляра объекта*

**Управление локальным устройством**

- nx_lwm2m_client_object_create: *Создать новый экземпляр объекта*

- nx_lwm2m_client_object_delete: *Удалить экземпляр объекта*

- nx_lwm2m_client_object_discover: *Найти ресурсы экземпляра объекта*

- nx_lwm2m_client_object_execute: *Выполнить ресурс экземпляра объекта*

- nx_lwm2m_client_object_next_get: *Получить список объектов, реализованных клиентом LWM2M*

- nx_lwm2m_client_object_instance_next_get: *Получить список экземпляров объекта*

- nx_lwm2m_client_object_read: *Сосчитать значения ресурсов экземпляра объекта*

- nx_lwm2m_client_object_write: *Изменить значения ресурсов экземпляра объекта*

**Информация о ресурсах и настройка значений:**

- nx_lwm2m_client_resource_info_set: *Установить информацию о ресурсе*

- nx_lwm2m_client_resource_string_set: *Задать значение ресурса как строку*

- nx_lwm2m_client_resource_integer32_set: *Установить значение ресурса как 32-битное целое число*

- nx_lwm2m_client_resource_integer64_set: *Установить значение ресурса как 64-битное целое число*

- nx_lwm2m_client_resource_float32_set: *Установить значение ресурса как 32-битное число с плавающей точкой*

- nx_lwm2m_client_resource_float64_set: *Установить значение ресурса как 64-битное число с плавающей точкой*

- nx_lwm2m_client_resource_boolean_set: *Установить значение ресурса как логическое*

- nx_lwm2m_client_resource_objlnk_set: *Установить значение ресурса как ссылку на объект*

- nx_lwm2m_client_resource_opaque_set: *Установите значение ресурса как непрозрачное*

- nx_lwm2m_client_resource_instance_set: *Установить значение ресурса как экземпляр для нескольких ресурсов*
-
- nx_lwm2m_client_resource_dim_set: *Установить измерение ресурса для нескольких ресурсов .*

**Информация о ресурсах и получении значений:**

- nx_lwm2m_client_resource_info_get: *Получить информацию о ресурсе*

- nx_lwm2m_client_resource_string_get: *Получить значение строкового ресурса*

- nx_lwm2m_client_resource_integer32_get: *Получить значение 32-битного целочисленного ресурса*

- nx_lwm2m_client_resource_integer64_get: *Получить значение 64-битного целочисленного ресурса*

- nx_lwm2m_client_resource_float32_get: *Получить значение 32-битного ресурса с плавающей точкой*

- nx_lwm2m_client_resource_float64_get: *Получить значение 64-битного ресурса с плавающей точкой*

- nx_lwm2m_client_resource_boolean_get: *Получить значение логического ресурса*

- nx_lwm2m_client_resource_objlnk_get: *Получить значение ресурса ссылки на объект*

- nx_lwm2m_client_resource_opaque_get: *Получить значение непрозрачного ресурса*

- nx_lwm2m_client_resource_instance_get: *Получить экземпляр ресурса для нескольких ресурсов*

- lwm2m_client_resource_dim_get: *Получить измерение ресурса для нескольких ресурсов.*

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Создает клиент LWM2M.

### <a name="prototype"></a>Прототип

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a>Описание

Данная служба создает экземпляр клиента LWM2M, который запускается в контексте собственного потока ThreadX.

Клиент LWM2M реализует следующие объекты OMA LWM2M: безопасность (0), сервер (1), контроль доступа (2) и устройство (3). Другие реализации объектов должны быть добавлены посредством приложения.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **ip_ptr** Указатель на ранее созданный экземпляр IP.
- **packet_pool_ptr** Указатель на пул пакетов по умолчанию для данного клиента LWM2M.
- **name_ptr** Указатель на имя конечной точки клиента LWM2M.
- **name_length** Длина имени конечной точки клиента LWM2M.
- **msisdn_ptr** Указатель на номер мобильного абонента сети ISDN, по которому можно связаться с клиентом LWM2M для использования с привязкой SMS, может иметь значение NULL, если привязка SMS не поддерживается.
- **msisdn_length** Длина номера MSISDN.
- **binding_modes** Привязка и режимы, поддерживаемые клиентом LWM2M, должны являться комбинацией флагов NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S и NX_LWM2M_BINDING_SQ.
- **stack_ptr** Указатель на область стека потока клиента LWM2M.
- **stack_size** Размер стека потока клиента LWM2M.
- **priority** Приоритет клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Клиент LWM2M успешно создан.
- **NX_LWM2M_CLIENT_ERROR** Ошибка создания клиента LWM2M.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.
- **NX_PTR_ERROR** Недопустимый указатель.
- **NX_SIZE_ERROR** Недопустимый размер стека.
- **NX_OPTION_ERROR** Недопустимый приоритет.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Удаляет клиент LWM2M.

### <a name="prototype"></a>Прототип

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет ранее созданный экземпляр клиентом LWM2M.

Все сеансы, подключенные в данный момент к клиенту, также удаляются посредством данного вызова.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Клиент LWM2M успешно удален.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a>nx_lwm2m_client_device_callback_set

Устанавливает обратный вызов приложения объекта устройства.

### <a name="prototype"></a>Прототип

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a>Описание

Данная служба устанавливает обратный вызов приложения для реализации операций с ресурсами объекта устройства LWM2M, которые не обрабатываются клиентом LWM2M.

Клиент LWM2M реализует следующие ресурсы: код ошибки (11), сброс кода ошибки (12) и поддерживаемые привязки и режимы (16), операции с другими ресурсами перенаправляются в приложение.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **operation_callback** Обратный вызов операции для команд «Чтение», «Обнаружение», «Запись» и «Выполнение».

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Обратный вызов операции успешно установлен.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push
Добавляет код ошибки к объекту устройства.

### <a name="prototype"></a>Прототип

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a>Описание

Данная служба добавляет новый экземпляр к ресурсу кода ошибки (11) объектного устройства.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **code** Новый код ошибки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**

Достигнуто максимальное количество сохраненных

кодов ошибок.

NX_PTR_ERROR Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Сбрасывает коды ошибок объекта устройства.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет все экземпляры ресурса кода ошибки из объекта устройства. Это эквивалентно выполнению кода ошибки сброса ресурса (12).

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Сообщает об изменении ресурса объекта устройства.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a>Описание

Служба используется приложением для сигнализации клиенту LWM2M об изменении ресурса объектного устройства. В случае если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **resource** Указатель на структуру, описывающую измененный ресурс.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a>nx_lwm2m_client_firmware_create

Создать объект микропрограммы клиента LWM2M. 

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a>Описание

Сервис используется приложением для создания объекта встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.
- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **protocols** Поддерживаемые протоколы.
- **package_callback** Обратный вызов пакета.
- **package_uri_callback** Обратный вызов универсального кода ресурса пакета.
- **update_callback** Обратный вызов обновления.

### <a name="return-values"></a>Возвращаемые значения

**NX_SUCCESS** Операция выполнена успешно.
**NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a>nx_lwm2m_client_firmware_package_info_set

Устанавливает информацию о пакете встроенного ПО клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a>Описание

Служба используется приложением для настройки информационных ресурсов пакета объекта обновления встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.
- **name** Имя пакета встроенного ПО.
- **name_length** Длина имени.
- **version** Версия пакета встроенного ПО.
- **version_length** Длина версии.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a>nx_lwm2m_client_firmware_result_set

Задает ресурс результата обновления для объекта обновления встроенного ПО.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Описание

Служба используется приложением для установки ресурса результата обновления объекта обновления встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.
- **result** Результат обновления.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a>nx_lwm2m_client_firmware_state_set

Задает ресурс результата обновления для объекта обновления встроенного ПО.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a>Описание

Сервис используется приложением для установки состояния объекта обновления встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr** Указатель на объект встроенного ПО клиента LWM2M.
- **state** Состояние объекта встроенного ПО.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Блокирует клиент LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба блокирует клиент LWM2M с целью предотвратить одновременный доступ к объектам LWM2M с серверов или другого потока приложения.

Если клиент LWM2M на данный момент заблокирован другим потоком, функция будет заблокирована до тех пор, пока клиент LWM2M не будет разблокирован.

Вызовы к парам ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** могут быть вложенными.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Добавляет реализацию объекта в клиент LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a>Описание

Данная служба добавляет новую реализацию объекта в клиент LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_ptr** Указатель на структуру, определяющую реализацию объекта.
- **object_id** Идентификатор объекта
- **object_operation** Функция обратного вызова операции с объектом.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор объекта уже существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Создает новый экземпляр объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Создать» над объектом клиента LWM2M для создания нового экземпляра объекта.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id_ptr** Если клиент LWM2M должен назначить идентификатор экземпляра, указатель на идентификатор нового экземпляра может иметь значение **NULL**. Если идентификатор представляет собой зарезервированное значение 65535, клиент LWM2M назначит идентификатор экземпляра. Если это не NULL, присвоенный идентификатор назначается повторно после вызова.
- **num_values** Количество устанавливаемых значений.
- **values_ptr** Указатель на массив значений ресурсов для инициализации нового экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор экземпляра объекта уже существует.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Объект не поддерживает функцию создания экземпляров.
- **NX_LWM2M_CLIENT_NO_MEMORY** Невозможно выделить память для хранения нового экземпляра.
- **NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта не существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Удаляет экземпляр объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Удалить» для экземпляра объекта клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id** Идентификатор экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Объект не поддерживает функцию удаления экземпляра.
- **NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта или идентификатор экземпляра объекта не существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Производит поиск ресурсов экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Найти» на экземпляре объекта клиента LWM2M, в результате чего возвращается список ресурсов, реализованных объектом.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id** Идентификатор экземпляра объекта.
- **num_resources** На входе - размер целевого буфера, на выходе - количество элементов, записанных в буфер.
- **resources** Указатель на целевой буфер.

### <a name="return-values"></a>Возвращаемые значения

- *NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Буфер ресурсов слишком мал для хранения списка ресурсов.
- **NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта или идентификатор экземпляра объекта не существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Выполняет операцию «Выполнить» над ресурсом экземпляра объекта.

### <a name="prototype"></a>Прототип

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Выполнить» для ресурса экземпляра объекта клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id** Идентификатор экземпляра объекта.
- **resource_id** Идентификатор ресурса.
- **arguments_ptr** Указатель на аргументы операции выполнения. Может быть NULL, если значение arguments_length равно нулю.
- **arguments_length** The length of the arguments.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Буфер ресурсов слишком мал для хранения списка ресурсов.
- **NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта или идентификатор экземпляра объекта не существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a>nx_lwm2m_client_object_instance_add

Добавляет реализацию экземпляра объекта к объекту.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Описание

Данная служба добавляет новую реализацию экземпляра объекта в клиент LWM2M. Если значение instance_id_ptr равно **NX_LWM2M_CLIENT_RESERVED_ID**, клиент LWM2M автоматически назначит неиспользуемый идентификатор экземпляра, в противном случае клиент LWM2M будет использовать значение, установленное приложением. После успешного добавления нового экземпляра для возврата в приложение значение instance_id будет заполнено instance_id_ptr.

### <a name="parameters"></a>Параметры

- **object_ptr** Указатель на структуру, определяющую реализацию объекта.
- **instance_ptr** Указатель на структуру, определяющую реализацию экземпляра объекта.
- **instance_id_ptr** Указатель на идентификатор экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_CLIENT_LWM2M_ALREADY_EXIST** Идентификатор объекта уже существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a>nx_lwm2m_client_object_instance_next_get

Получает следующий экземпляр объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Описание

Данная служба возвращает идентификатор следующего экземпляра данного объекта. Если текущий идентификатор экземпляра установлен на NX_LWM2M_RESERVED_ID (65535), возвращается идентификатор первого экземпляра.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id_ptr** Указатель на текущий идентификатор экземпляра объекта. При возврате содержит идентификатор следующего экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_CLIENT_LWM2M_NOT_FOUND** Данный идентификатор экземпляра является последним из объекта, или идентификатор объекта не реализован.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a>nx_lwm2m_client_object_instance_remove

Удаляет реализацию экземпляра объекта из объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет экземпляр объекта из объекта.

### <a name="parameters"></a>Параметры

- ***object_ptr*** Указатель на структуру, определяющую реализацию объекта.
- **instance_ptr** Указатель на структуру, определяющую реализацию экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор объекта уже существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a>nx_lwm2m_client_object_next_get

Получает следующий объект клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a>Описание

Данная служба возвращает идентификатор следующего объекта, реализованного клиентом LWM2M. Если текущий идентификатор объекта установлен на NX_LWM2M_RESERVED_ID (65535), возвращается первый идентификатор объекта.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id_ptr** Указатель на текущий идентификатор объекта. При возврате содержит следующий идентификатор объекта, реализованный клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_NOT_FOUND** Данный идентификатор объекта является последним в базе данных.
**NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Считывает значения ресурса экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Описание

Эта служба выполняет операцию «Сосчитать» на экземпляре объекта клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id** Идентификатор экземпляра объекта.
- **num_values** Количество ресурсов для считывания.
- **values_ptr** Указатель на массив NX_LWM2M_RESOURCE, содержащий идентификаторы считываемых ресурсов По возвращении массив заполняется соответствующими типами и значениями.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Ресурс не поддерживает операцию считывания.
- **NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a>nx_lwm2m_client_object_remove

Удаляет реализацию экземпляра объекта из объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет объект из клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_ptr** Указатель на структуру, определяющую реализацию объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ALREADY_EXIST** Идентификатор объекта уже существует.
- **NX_PTR_ERROR** Недопустимый указатель.
- **NX_LWM2M_CLIENT_FORBIDDEN** Удаление внутреннего объекта недопустимо.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a>nx_lwm2m_client_object_resource_changed

Сигнализирует об изменении ресурса объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Описание

Служба используется приложением, чтобы сигнализировать клиенту LWM2M об изменении ресурса объекта. В случае если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.

### <a name="parameters"></a>Параметры

- **object_ptr** Указатель на структуру, определяющую реализацию объекта.
- ***instance_ptr*** Указатель на структуру, определяющую реализацию экземпляра объекта.
- **resource** Указатель на структуру, описывающую измененный ресурс.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Изменяет значения ресурса экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Запись» для экземпляра объекта клиента LWM2M.

Для параметра *write_op* можно указать следующие операции записи.

| Значение | Операция&nbsp;записи | Описание |
| --- | ---| --- |
| 0 | Частичное обновление | Добавляет или обновляет Ресурсы, представленные в новом значении, и оставляет другие существующие Ресурсы без изменений. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Заменить экземпляр | Заменяет экземпляр объекта новыми предоставленными значениями ресурсов. |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** | Заменить ресурс | Заменяет ресурсы новыми предоставленными значениями ресурсов (используется для замены нескольких ресурсов). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Запись при начальной загрузке | Обозначает вызов из последовательности начальной загрузки. |

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.
- **object_id** Идентификатор объекта.
- **instance_id** Идентификатор экземпляра объекта.
- **num_values** Количество записываемых ресурсов.
- **values_ptr** Указатель на массив NX_LWM2M_RESOURCE, содержащий идентификаторы ресурсов, типы и значения для записи.
- **write_op** Тип операции записи.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Тип ресурса недействителен.
- **NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Длина значения слишком велика для сохранения в экземпляре.
- **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Ресурс не поддерживает функцию операции записи.
- **NX_LWM2M_CLIENT_NO_MEMORY** Невозможно выделить память для хранения значения ресурса.
- **NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Значение ресурса недействительно.
- **NX_LWM2M_CLIENT_NOT_FOUND** Идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.
- **NX_OPTION_ERROR** Неверный тип операции записи. 
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a>nx_lwm2m_client_resource_boolean_get

Получает значение логического ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение логического ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на описание значения ресурса.
- **bool_ptr** Указатель на целевое логическое значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a>nx_lwm2m_client_resource_boolean_set

Устанавливает значение логического ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a>Описание

Служба устанавливает значение логического ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **bool_data** Логические данные.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a>nx_lwm2m_client_resource_dim_get

Получает измерение ресурса для нескольких ресурсов

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a>Описание

Служба извлекает измерение ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **dim** Указатель на размер назначения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a>nx_lwm2m_client_resource_dim_set

Устанавливает измерение ресурса для нескольких ресурсов.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a>Описание

Служба устанавливает измерение ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value** Указатель на описание значения ресурса.
- **dim** Значение измерения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a>nx_lwm2m_client_resource_float32_get

Получает значение 32-битного ресурса **с плавающей точкой**.

### <a name="prototype"></a>Прототип

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение 32-битного ресурса **с плавающей точкой**.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **float32_ptr** Указатель на целевое 32-битное **значение с плавающей точкой**.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a>nx_lwm2m_client_resource_float32_set

Устанавливает значение 32-битного ресурса **с плавающей точкой**.

### <a name="prototype"></a>Прототип

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a>Описание

Служба устанавливает значение 32-битного ресурса **с плавающей точкой**.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **float32_data** 32-битные **данные с плавающей точкой**.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a>nx_lwm2m_client_resource_float64_get

Получает значение 64-битного ресурса с плавающей точкой.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение 64-битного ресурса **с плавающей точкой**.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **float64_ptr** Указатель на целевое 64-битное **значение с плавающей точкой**.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является значением с плавающей запятой.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a>nx_lwm2m_client_resource_float64_set

Устанавливает значение 64-битного ресурса **с плавающей точкой**.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Описание

Служба устанавливает значение 64-битного ресурса **с плавающей точкой**.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **float64_data** 64-битные **данные с плавающей точкой**.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a>nx_lwm2m_client_resource_info_get

Получает информацию о ресурсе.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a>Описание

Служба извлекает информацию о ресурсе.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **resource_id** Указатель на идентификатор ресурса назначения.
- **operation** Указатель на целевую операцию ресурса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a>nx_lwm2m_client_resource_info_set

Устанавливает информацию о ресурсе.

### <a name="prototype"></a>Прототип

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a>Описание

Сервис устанавливает информацию о ресурсе.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **resource_id** Идентификатор ресурса.
- **operation** Операция ресурса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a>nx_lwm2m_client_resource_instances_get

Получает экземпляр нескольких ресурсов.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a>Описание

Служба извлекает информацию о ресурсе.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **resource_instances** Указатель на идентификатор ресурса назначения.
- **count** Указатель на счетчик.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является логическим значением.
- **NX_LWM2M_CLIENT_NO_MEMORY** Отсутствует память для заполнения экземпляров.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a>nx_lwm2m_client_resource_instances_set

Устанавливает экземпляры ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a>Описание

Служба устанавливает экземпляры ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **resource_instance** Указатель на экземпляры ресурса.
- **count** Количество экземпляров ресурса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a>nx_lwm2m_client_resource_integer32_get

Получает значение 32-разрядного целочисленного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение 32-разрядного целочисленного ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **integer32_ptr** Указатель на 32-битное целое число.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является целым числом.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a>nx_lwm2m_client_resource_integer32_set

Устанавливает значение 32-битного целочисленного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a>Описание

Служба устанавливает значение 32-битного целого ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **integer32_data** 32-битные целочисленные данные.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a>nx_lwm2m_client_resource_integer64_get

Получает значение ресурса 64-разрядного целого числа.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение 64-битного целочисленного ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **integer64_ptr** Указатель на 64-битное целое число.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является 64-битным целым числом.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a>nx_lwm2m_client_resource_integer64_set

## <a name="set-the-value-of-a-64-bit-integer-resource"></a>Установить значение 64-битного целочисленного ресурса

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a>Описание

Сервис устанавливает значение 64-битного целого ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **integer64_data** 64-битное целое число.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a>nx_lwm2m_client_resource_objlnk_get

Получает значение ресурса ссылки на объект.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a>Описание

Служба получает значение ссылки на объект.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **object_id** Указатель на идентификатор объекта.
- **instance_id** Указатель на идентификатор экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является значением ссылки на объект.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a>nx_lwm2m_client_resource_objlnk_set

Устанавливает экземпляры ресурса

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Описание

Служба устанавливает значение ресурса ссылки на объект.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **object_id** Идентификатор объекта.
- **instance_id** Идентификатор экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a>nx_lwm2m_client_resource_opaque_get

Получает значение непрозрачного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a>Описание

Служба извлекает значение непрозрачного ресурса. Значение непрозрачного ресурса состоит из указателя на буфер и длины.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **opaque_ptr** Указатель на непрозрачные данные.
- **opaque_length** Указатель на длину непрозрачных данных.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является непрозрачным ресурсом.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a>nx_lwm2m_client_resource_opaque_set

Устанавливает значение непрозрачного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a>Описание

Сервис устанавливает значение непрозрачного ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **opaque_ptr** Указатель на непрозрачные данные.
- **opaque_length** Длина непрозрачных данных.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a>nx_lwm2m_client_resource_string_get

Получает значение строкового ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a>Описание

Служба извлекает значение строкового ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **string_ptr** Указатель на указатель целевой строки.
- **string_length** Указатель на длину целевой строки. Может иметь значение **NULL**, если строка заканчивается нулем.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_BAD_ENCODING** Значение ресурса не является строковым значением.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a>nx_lwm2m_client_resource_string_set

Устанавливает значение строкового ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a>Описание

Сервис устанавливает значение 64-битного целого ресурса.

### <a name="parameters"></a>Параметры

- **resource** Указатель на ресурс.
- **string_ptr** Указатель на строку.
- **string_length** Длина строки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Начинает сеанс с сервером начальной загрузки.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a>Описание

Данная служба запускает сеанс с сервером начальной загрузки. Сервер должен иметь соответствующий экземпляр защиты в объекте защиты.

Если ресурс «Ожидание» отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициированной сервером начальной загрузки. Если по истечении этого периода времени сервер не инициирует загрузку, будет выполнено инициированное клиентом ускорение.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.
- **security_id** Если на сервере начальной загрузки не определен экземпляр безопасности, идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение NX_LWM2M_RESERVED_ID (65535),
- **ip_address** IP-адрес сервера.
- **port** UDP-порт сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Запускает безопасный сеанс с сервером начальной загрузки

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Описание

Данная служба запускает сеанс с сервером начальной загрузки, используя безопасное соединение DTLS. Сервер должен иметь соответствующий экземпляр защиты в объекте защиты.

Перед вызовом данной функции сеанс протокола DTLS должен быть настроен с использованием надлежащих наборов шифров и ключевого материала. Необходимо определить **NX_SECURE_ENABLE_DTLS**.

Если ресурс «Ожидание» отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициируемой сервером начальной загрузки, если сервер не инициирует загрузку по истечении этого периода времени, будет выполнено инициированное клиентом ускорение. 

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.
- **security_id** Если на сервере начальной загрузки не определен экземпляр безопасности, идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение **NX_LWM2M_RESERVED_ID** (65535).
- **ip_address** IP-адрес сервера.
- **port** UDP-порт сервера.
- **dtls_session_ptr** Сеанс DTLS, используемый для сеанса начальной загрузки.
- **dtls_local_port** Локальный UDP-порт, используемый для сеанса DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Создает клиентский сеанс LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Описание

Данная служба создает новый клиентский сеанс LWM2M, присоединенный к существующему клиенту LWM2M. Сеанс используется клиентом LWM2M для связи с сервером начальной загрузки или сервером LWM2M. 

Приложение должно предоставить функцию обратного вызова, которая будет вызываться при обновлении состояния сеанса.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.
- **client_ptr** Указатель на ранее созданный клиент LWM2M.
- **state_callback** Обратный вызов приложения, который вызывается при изменении состояния сеанса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Удаляет клиентский сеанс LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет клиентский сеанс LWM2M.

Когда клиент LWM2M удаляется вызовом nx_lwm2m_client_delete, также удаляются все сеансы, подключенные к клиенту.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Завершает сеанс с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Отмена регистрации» на сервере LWM2M.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Клиент не зарегистрирован на сервере.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Получает последнюю ошибку сеанса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба возвращает код ошибки сеанса в случаях, когда сеанс находится в состоянии ошибки.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Сеанс не находится в состоянии ошибки.
- **NX_LWM2M_CLIENT_ADDRESS_ERROR** Недопустимый адрес сервера.
- **NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Полезные данные запроса не помещаются в сетевой буфер.
- **NX_LWM2M_ CLIENT_DTLS_ERROR** Не удалось установить защищенное соединение с сервером.
- **NX_LWM2M_ CLIENT_ERROR** Неопределенная ошибка.
- **NX_LWM2M_ CLIENT_FORBIDDEN** В регистрации отказано со стороны сервера.
- **NX_LWM2M_ CLIENT_NOT_FOUND** Клиент не найден сервером при обновлении/отмене регистрации.
- **NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Экземпляр объекта сервера, соответствующий сеансу, был удален.
- **NX_LWM2M_ CLIENT_TIMED_OUT** Нет ответа с сервера.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Начинает сеанс с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a>Описание

Данная служба выполняет операцию «Регистрация» на сервере LWM2M. Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.

Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения «Обновить» до момента отмены регистрации клиента.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.
- **server_id** Краткий идентификатор сервера LWM2M.
- **ip_address** IP-адрес сервера.
- **port** UDP-порт сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Запускает безопасный сеанс с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Регистрация» на сервере LWM2M, используя безопасное соединение DTLS. Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.

Перед вызовом данной функции сеанс протокола DTLS должен быть настроен с использованием надлежащих наборов шифров и ключевого материала. Необходимо определить **NX_SECURE_ENABLE_DTLS**.

Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения «Обновить» до момента отмены регистрации клиента.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.
- **server_id** Краткий идентификатор сервера LWM2M.
- **ip_address** IP-адрес сервера.
- **port** UDP-порт сервера.
- **dtls_session_ptr** Сеанс протокола DTLS, используемый для сеанса LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_ERROR** Ошибка начальной загрузки.
- **NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Порт недоступен.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a>nx_lwm2m_client_session_register_info_get

Запускает безопасный сеанс с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a>Описание

После установления сеанса связи с сервером начальной загрузки. Приложение может вызвать данный API для получения информации о сервере и безопасности для следующего шага регистрации.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.
- **security_instance_id** Идентификатор экземпляра безопасности.
- **server_id** Указатель на идентификатор целевого сервера.
- **server_uri** Указатель на URI-идентификатор сервера назначения.
- **server_uri_len** Указатель на длину URI-идентификатора сервера назначения.
- **security_mode** Указатель на режим безопасности назначения.
- **pub_key_or_id** Указатель на открытый ключ или идентификатор назначения.
- **pub_key_or_id_len** Указатель на открытый ключ назначения или длину идентификатора.
- **server_pub_key** Указатель на открытый ключ целевого сервера.
- **server_pub_key_len** Указатель на длину открытого ключа целевого сервера.
- **secret_key** Указатель на секретный ключ назначения.
- **secret_key_len** Указатель на длину секретного ключа назначения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_NOT_FOUND** Экземпляр объекта безопасности отсутствует.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Обновляет сеанс с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию «Обновить» на сервере LWM2M.

### <a name="parameters"></a>Параметры

- **session_ptr** Указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_LWM2M_CLIENT_NOT_REGISTERED** Клиент не зарегистрирован на сервере.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Разблокирует клиент LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба разблокирует клиент LWM2M, ранее заблокированный вызовом ***nx_lwm2m_client_unlock***.

### <a name="parameters"></a>Параметры

- **client_ptr** Указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** Операция выполнена успешно.
- **NX_PTR_ERROR** Недопустимый указатель.

### <a name="allowed-from"></a>Разрешено с

Потоки, Инициализация

### <a name="example"></a>Пример

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```