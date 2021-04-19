---
title: Глава 4. Описание служб устройства USBX
description: Ознакомьтесь с информацией о службах устройства USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816144"
---
# <a name="description-of-usbx-device-services"></a>Описание служб устройства USBX

### <a name="ux_device_stack_alternate_setting_get"></a>ux_device_stack_alternate_setting_get

Получение текущего переменного параметра для значения интерфейса

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a>Описание

Эта функция используется узлом USB для получения текущего переменного параметра для определенного значения интерфейса. Она вызывается драйвером контроллера при получении запроса **GET_INTERFACE**.

### <a name="input-parameter"></a>Входной параметр

- **Interface_value** Значение интерфейса, для которого запрашивается текущий переменный параметр

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – передача данных завершена.
- **UX_ERROR** (0xFF) – неправильное значение интерфейса.

### <a name="example"></a>Пример

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a>ux_device_stack_alternate_setting_set

Установка текущего переменного параметра для значения интерфейса

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Описание

Эта функция используется узлом USB для установки текущего переменного параметра для определенного значения интерфейса. Она вызывается драйвером контроллера при получении запроса **SET_INTERFACE**. После завершения **SET_INTERFACE** к классу применяются значения переменных параметров.

Стек устройства даст команду **UX_SLAVE_CLASS_COMMAND_CHANGE** классу, владеющему этим интерфейсом, чтобы отразить изменение переменного параметра.

### <a name="parameters"></a>Параметры

- **Interface_value**: значение интерфейса, для которого установлен текущий переменный параметр.
- **alternate_setting_value**: новое значение переменного параметра.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – передача данных завершена.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) – интерфейс не подключен.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) – устройство не настроено.
- **UX_ERROR** (0xFF) – неправильное значение интерфейса.

### <a name="example"></a>Пример

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

Регистрация нового класса USB-устройств

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция используется приложением для регистрации нового класса USB-устройств. При регистрации запускается контейнер класса, а не экземпляр класса. Класс должен иметь активный поток и быть присоединен к определенному интерфейсу.

Некоторые классы предполагают наличие параметра или списка параметров. Например, класс хранения устройств ожидает геометрию устройства хранения, которое он пытается эмулировать. Поэтому поле параметра зависит от требования к классу и может быть значением или указателем на структуру, заполненную значениями класса.

> [!NOTE]
> Строка C объекта class_name должна завершаться нулем и ее длина (без конечного нуля) не должна быть больше, чем **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Параметры

- **class_name** – имя класса
- **class_entry_function** – функция записи класса.
- **configuration_number** – номер конфигурации, к которому присоединен этот класс.
- **interface_number** – номер интерфейса, к которому присоединен этот класс.
- **parameter** – указатель на список параметров конкретного класса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – класс зарегистрирован
- **UX_MEMORY_INSUFFICIENT** (0x12) – в таблице классов не осталось записей.
- **UX_THREAD_ERROR** (0X16) – не удается создать поток класса.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a>ux_device_stack_class_unregister

Отмена регистрации класса USB-устройств

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a>Описание

Эта функция используется приложением для отмены регистрации класса USB-устройств.

> [!NOTE]
> Строка C объекта class_name должна завершаться нулем и ее длина (без конечного нуля) не должна быть больше, чем **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Параметры

- **class_name**: имя класса
- **class_entry_function**: функция записи класса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – регистрация класса отменена.
- **UX_NO_CLASS_MATCH** (0x57) – класс не зарегистрирован.

### <a name="example"></a>Пример

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a>ux_device_stack_configuration_get

Получение текущей конфигурации

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a>Описание

Эта функция используется узлом для получения текущей конфигурации, используемой на устройстве.

### <a name="input-parameter"></a>Входной параметр

Нет

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) – передача данных завершена.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

Установка текущей конфигурации

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a>Описание

Эта функция используется узлом для установки текущей конфигурации, используемой на устройстве. При получении этой команды стек USB-устройств активирует переменный параметр 0 каждого интерфейса, подключенного к этой конфигурации.

### <a name="input-parameter"></a>Входной параметр

- **configuration_value** – значение конфигурации, выбранное узлом.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) – конфигурация выполнена успешно.

### <a name="example"></a>Пример

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

Отправка дескриптора на узел

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a>Описание

Эта функция используется на стороне устройства для возврата дескриптора в узел. Этот дескриптор может быть дескриптором устройства, конфигурации или строки.

### <a name="parameters"></a>Параметры

- **descriptor_type**: тип дескриптора. Необходимо установить одно из следующих значений.
  - **UX_DEVICE_DESCRIPTOR_ITEM**
  - **UX_CONFIGURATION_DESCRIPTOR_ITEM**
  - **UX_STRING_DESCRIPTOR_ITEM**
  - **UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**
  - **UX_OTHER_SPEED_DESCRIPTOR_ITEM**
- **request_index**: индекс дескриптора.
- **host_length**: требуемая длина узла.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – передача данных завершена.
- **UX_ERROR** (0xFF) перемещение не завершено.

### <a name="example"></a>Пример

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

Отключение стека устройства

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a>Описание

Менеджер VBUS вызывает эту функцию при отключении устройства. Стек устройства оповестит все классы, зарегистрированные на этом устройстве, и затем освободит все ресурсы устройства.

### <a name="input-parameter"></a>Входной параметр

Нет

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) – устройство отключено.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

Условие остановки конечной точки запроса

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a>Описание

Эта функция вызывается классом USB-устройства, когда конечная точка должна вернуть узлу условие остановки.

### <a name="input-parameter"></a>Входной параметр

- **endpoint** – конечная точка, в которой запрашивается условие остановки.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) – операция успешно выполнена.
- **UX_ERROR** (0xFF) устройство находится в недопустимом состоянии.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

Активизация узла

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда устройству требуется активизировать узел. Эта команда допустима, только если устройство находится в режиме приостановки. Приложение устройства может решить, когда требуется активизировать USB-узел. Например, USB-модем может активизировать узел при обнаружении сигнала вызова по телефонной линии.

### <a name="input-parameter"></a>Входной параметр

Нет

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – вызов успешно выполнен.
- **UX_FUNCTION_NOT_SUPPORTED** (0x54) – сбой вызова (возможно, устройство не находится в приостановленном режиме).

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

Инициализация стека устройств USB

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a>Описание

Эта функция вызывается приложением для инициализации стека USB-устройства. Она не инициализирует классы или контроллеры. Для этого необходимо выполнить отдельные вызовы функций. Этот вызов в основном предназначен для создания платформы устройства для функции USB в стеке. Он поддерживает как высокую, так и полную скорость с возможностью полного разделения платформ устройств для каждой скорости. Поддерживается строковая платформа и различные языки.

### <a name="parameters"></a>Параметры

- **device_framework_high_speed**: указатель на платформу высокой скорости.
- **device_framework_length_high_speed**: длина платформы высокой скорости.
- **device_framework_full_speed**: указатель на платформу максимальной скорости.
- **device_framework_length_full_speed**: длина платформы максимальной скорости.
- **string_framework**: указатель на строковую платформу.
- **string_framework**: указатель на строковую платформу.
- **language_id_framework**: указатель на строковую языковую платформу.
- **language_id_framework_length**: длина строковой языковой платформы.
- **ux_system_slave_change_function**: функция, вызываемая при изменении состояния устройства.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – операция успешно выполнена.
- **UX_MEMORY_INSUFFICIENT** (0x12) – недостаточно памяти для инициализации стека.
- **UX_DESCRIPTOR_CORRUPTED** (0x42) — недопустимый дескриптор.

### <a name="example"></a>Пример

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Приложение может запросить обратный вызов, когда контроллер изменит свое состояние. Два основных состояния контроллера:

- **UX_DEVICE_SUSPENDED**
- **UX_DEVICE_RESUMED**

Если приложению не требуются сигналы приостановки / возобновления работы, то будет выполнена функция UX_NULL.

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

Удаление интерфейса стека

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Описание

Эта функция вызывается для удаления интерфейса. Интерфейс либо удаляется при извлечении устройства или после сброса шины, либо при наличии нового альтернативного параметра.

### <a name="input-parameter"></a>Входной параметр

- **interface**: указатель на интерфейс, который необходимо удалить.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) – операция успешно выполнена.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

Получение значения текущего интерфейса

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда узел запрашивает текущий интерфейс. Устройство возвращает текущее значение интерфейса.

> [!NOTE]
> Эта функция является устаревшей. Он доступен для устаревшего программного обеспечения, но новое программное обеспечение должно использовать функцию ***ux_device_stack_alternate_setting_get***.

### <a name="input-parameter"></a>Входной параметр

- **interface_value** – возвращаемое значение интерфейса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – операция успешно выполнена.
- **UX_ERROR** (0xFF) – интерфейс не существует.

### <a name="example"></a>Пример

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

Изменение альтернативного параметра интерфейса

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда узел запрашивает изменение альтернативного параметра для интерфейса.

### <a name="parameters"></a>Параметры

- **device_framework**: адрес платформы устройства для этого интерфейса.
- **device_framework_length**: длина платформы устройства.
- **alternate_setting_value**: значение альтернативного параметра, которое будет использоваться этим интерфейсом.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – операция успешно выполнена.
- **UX_ERROR** (0xFF) – интерфейс не существует.

### <a name="example"></a>Пример

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a>ux_device_stack_interface_start

Запуск поиска класса, к которому будет принадлежать экземпляр интерфейса

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда узел выбирает интерфейс и в стеке устройства необходимо найти класс устройства для этого экземпляра интерфейса.

### <a name="input-parameter"></a>Входной параметр

- **interface**: указатель на созданный интерфейс.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – операция успешно выполнена.
- **UX_NO_CLASS_MATCH** (0x57) – нет класса для этого интерфейса.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

Запрос на перемещение данных на узел

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда класс или стек желает передать данные на узел. Узел всегда опрашивает устройство, но устройство может заранее подготовить данные.

### <a name="parameters"></a>Параметры

- **transfer_request**: указатель на запрос на перемещение.
- **slave_length**: длина данных, возвращаемых устройством.
- **host_length**: длина данных, запрашиваемых узлом.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) – операция успешно выполнена.
- **UX_TRANSFER_NOT_READY** (0x25) – устройство находится в недопустимом состоянии; допустимы состояния **ATTACHED**, **CONFIGURED** или **ADDRESSED**.
- **UX_ERROR** (0xFF) – ошибка передачи.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

Отмена запроса на перемещение

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется отменить запрос на передачу или если стеку необходимо прервать запрос на передачу, связанный с конечной точкой.

### <a name="parameters"></a>Параметры

- **transfer_request**: указатель на запрос на перемещение.
- **completion_code**: код ошибки, возвращаемый классу, ожидающему завершения этого запроса на передачу.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) – операция успешно выполнена.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a>ux_device_stack_uninitialize

Отмена инициализации стека

### <a name="prototype"></a>Прототип

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению необходимо отменить инициализацию стека устройств USBX — все ресурсы стека устройств высвобождаются. Этот метод должен вызываться после отмены регистрации всех классов с помощью функции ux_device_stack_class_unregister.

### <a name="parameters"></a>Параметры

Отсутствуют

### <a name="return-value"></a>Возвращаемое значение

**UX_SUCCESS** (0x00) – операция успешно выполнена.
