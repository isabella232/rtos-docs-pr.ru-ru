---
title: Глава 4. Описание служб узлов USBX
description: Сведения о службах узлов USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816356"
---
# <a name="chapter-4---description-of-usbx-host-services"></a>Глава 4. Описание служб узлов USBX

## <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

Инициализация USBX для операции узла.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a>Описание

Эта функция будет инициализировать стек узлов USB. Заданная область памяти будет настроена для внутреннего использования USBX. Если возвращается UX_SUCCESS, USBX готов для хост-контроллера и регистрации класса.

### <a name="input-parameter"></a>Входной параметр

- **system_change_function** — указатель на необязательную подпрограмму обратного вызова для уведомления приложения об изменениях устройства.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — успешная инициализация.
- **UX_MEMORY_INSUFFICIENT** (0x12) — сбой выделения памяти.

### <a name="example"></a>Пример

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

Прерывание всех транзакций, вложенных в запрос на передачу для конечной точки.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Описание

Эта функция отменит все активные или ожидающие транзакции для конкретного запроса на передачу, связанного с конечной точкой. В запросе на передачу была вложена функция обратного вызова, которая будет вызываться с состоянием UX_TRANSACTION_ABORTED.

### <a name="input-parameter"></a>Входной параметр

- **endpoint** — указатель на конечную точку.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0X00) — без ошибок.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) — недопустимый дескриптор конечной точки.

### <a name="example"></a>Пример

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a>ux_host_stack_class_get

Получение указателя на контейнер класса.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a>Описание

Эта функция возвращает указатель на контейнер класса. Класс должен получить свой контейнер из стека USB для поиска экземпляров, когда класс или приложение хотят открыть устройство.

> [!NOTE]
> Строка C объекта class_name должна завершаться нулем, и ее длина (без конечного нуля) не должна быть больше, чем UX_MAX_CLASS_NAME_LENGTH.

### <a name="parameters"></a>Параметры

- **class_name** — указатель на имя класса.
- **class** — указатель, обновленный вызовом функции, который содержит контейнер класса для имени класса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0X00) — успешный возврат поля класса, заполненного указателем на контейнер класса.
- **UX_HOST_CLASS_UNKNOWN** (0x59) — класс неизвестен стеку.

### <a name="example"></a>Пример

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a>ux_host_stack_class_register

Регистрация класса USB в стеке USB.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a>Описание

Эта функция регистрирует класс USB в стеке USB. Класс должен указывать точку входа для стека USB, чтобы отправить перечисленные ниже команды.

- **UX_HOST_CLASS_COMMAND_QUERY**
- **UX_HOST_CLASS_COMMAND_ACTIVATE**
- **UX_HOST_CLASS_COMMAND_DESTROY**

> [!NOTE]
> Строка C объекта *class_name* должна завершаться нулем, и ее длина (без конечного нуля) не должна быть больше, чем **UX_MAX_CLASS_NAME_LENGTH**.

### <a name="parameters"></a>Параметры

- **class_name** — указатель на имя класса; допустимые записи находятся в файле ux_system_initialize.c в классах USB для USBX.
- **class_entry_address** — адрес функции входа класса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — класс успешно установлен.
- **UX_MEMORY_ARRAY_FULL** (0X1a) — недостаточно памяти для хранения этого класса.
- **UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) — класс узла уже установлен.

### <a name="example"></a>Пример.

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a>ux_host_stack_class_instance_create

Создание нового экземпляра класса для контейнера класса.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Описание

Эта функция создает новый экземпляр класса для контейнера класса. Экземпляр класса не содержится в коде класса для упрощения класса. Вместо этого каждый экземпляр класса вкладывается в контейнер класса, расположенный в главном стеке.

### <a name="parameters"></a>Параметры

- **class** — указатель на контейнер класса.
- **class_instance** — указатель на экземпляр класса, который нужно создать.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — экземпляр класса был вложен в контейнер класса.

### <a name="example"></a>Пример

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a>ux_host_stack_class_instance_destroy

Уничтожение экземпляра класса для контейнера класса.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a>Описание

Эта функция уничтожает экземпляр класса для контейнера класса.

### <a name="parameters"></a>Параметры

- **class** — указатель на контейнер класса.
- **class_instance** — указатель на экземпляр, который нужно уничтожить.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — экземпляр класса уничтожен.
- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса не вложен в контейнер класса.

### <a name="example"></a>Пример

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a>ux_host_stack_class_instance_get

Получение указателя экземпляра класса для определенного класса.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a>Описание

Эта функция возвращает указатель экземпляра класса для определенного класса. Экземпляр класса не содержится в коде класса для упрощения класса. Вместо этого каждый экземпляр класса вкладывается в контейнер класса. Эта функция используется для поиска экземпляров класса в контейнере класса.

### <a name="parameters"></a>Параметры

- **class** — указатель на контейнер класса.
- **class_index** — индекс, используемый вызовом функции в списке вложенных в контейнер классов.
- **class_instance** — указатель на экземпляр, возвращаемый вызовом функции.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — экземпляр класса найден.

- **UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — в контейнер класса не вложено ни одного экземпляра класса.

### <a name="example"></a>Пример

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

Получение указателя на контейнер конфигурации.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Описание

Эта функция возвращает контейнер конфигурации на основе дескриптора устройства и индекса конфигурации.

### <a name="parameters"></a>Параметры

- **device** — указатель на контейнер устройства, которому принадлежит запрошенная конфигурация.
- **configuration_index** — индекс конфигурации, которую нужно найти.
- **configuration** — адрес указателя на возвращаемый контейнер конфигурации.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — конфигурация найдена.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) — контейнер устройства не существует.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — дескриптор конфигурации для индекса не существует.

### <a name="example"></a>Пример

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

Выбор определенной конфигурации для устройства.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a>Описание

Эта функция выбирает определенную конфигурацию для устройства. Если эта конфигурация задана для устройства, по умолчанию на устройстве активируется каждый интерфейс устройства и связанный с ним альтернативный параметр 0. Если класс устройства или интерфейса хочет изменить параметр определенного интерфейса, он должен выполнить вызов службы **ux_host_stack_interface_setting_select**.

### <a name="parameters"></a>Параметры

- **configuration** — указатель на контейнер конфигурации, который нужно включить для этого устройства.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — выбор конфигурации выполнен успешно.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — дескриптор конфигурации не существует.
- **UX_OVER_CURRENT_CONDITION** (0x43) — для этой конфигурации на шине существует перегрузка по току.

### <a name="example"></a>Пример

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

Получение указателя на контейнер устройства.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a>Описание

Эта функция возвращает контейнер устройства на основе его индекса. Индекс устройства начинается с 0. Обратите внимание, что индекс имеет тип ULONG, так как у нас может быть несколько контроллеров и индекса байта может быть недостаточно. Индекс устройства не следует путать с адресом устройства, относящимся к определенной шине.

### <a name="parameters"></a>Параметры

- **device_index** — индекс устройства.
- **device** — адрес указателя для возвращаемого контейнера устройства.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — контейнер устройства существует и возвращается.
- **UX_DEVICE_HANDLE_UNKNOWN** (0x50) — неизвестное устройство.

### <a name="example"></a>Пример

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a>ux_host_stack_interface_endpoint_get

Получение контейнера конечной точки.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a>Описание

Эта функция возвращает контейнер конечной точки на основе дескриптора интерфейса и индекса конечной точки. Предполагается, что до начала поиска конечных точек альтернативный параметр для интерфейса уже выбран или используется параметр по умолчанию.

### <a name="parameters"></a>Параметры

- **interface** — указатель на контейнер интерфейса, содержащий запрошенную конечную точку.
- **endpoint_index** — индекс конечной точки в этом интерфейсе.
- **endpoint** — адрес возвращаемого контейнера конечной точки.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — контейнер конечной точки существует и возвращается.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) — указанный интерфейс не существует.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) — индекс конечной точки не существует.

### <a name="example"></a>Пример

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

Регистрация контроллера USB в стеке USB.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a>Описание

Эта функция регистрирует контроллер USB в стеке USB. Она в основном выделяет память, используемую этим контроллером, и передает команду инициализации контроллеру.

### <a name="parameters"></a>Параметры

- **hcd_name** — имя хост-контроллера.
- **hcd_function** — функция в хост-контроллере, отвечающая за инициализацию.
- **hcd_param1** — ресурс ввода-вывода или памяти, используемый HCD.
- **hcd_param2** — значение IRQ, используемое хост-контроллером.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — контроллер инициализирован правильно.
- **UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти для этого контроллера.
- **UX_PORT_RESET_FAILED** (0x31) — не удалось выполнить сброс контроллера.
- **UX_CONTROLLER_INIT_FAILED** (0x32) — не удалось правильно инициализировать контроллер.

### <a name="example"></a>Пример

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a>ux_host_stack_configuration_interface_get

Получение указателя для контейнера интерфейса.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a>Описание

Эта функция возвращает контейнер интерфейса на основе дескриптора конфигурации, индекса интерфейса и индекса альтернативного параметра.

### <a name="parameters"></a>Параметры

- **configuration** — указатель на контейнер конфигурации, которому принадлежит интерфейс.
- **interface_index** — индекс интерфейса, который нужно найти.
- **alternate_setting_index** — альтернативный параметр в интерфейсе для поиска.
- **interface** — адрес указателя возвращаемого контейнера интерфейса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — контейнер интерфейса для индекса интерфейса и альтернативный параметр найдены и возвращены.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — конфигурация не существует.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) — интерфейс не существует.

### <a name="example"></a>Пример

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

Выбор альтернативного параметра для интерфейса.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a>Описание

Эта функция выбирает определенный альтернативный параметр для данного интерфейса выбранной конфигурации. Эта функция используется для изменения альтернативного параметра по умолчанию на новый параметр или для возврата к альтернативному параметру по умолчанию. Если выбран новый альтернативный параметр, предыдущие характеристики конечной точки являются недопустимыми, поэтому их следует перезагрузить.

### <a name="input-parameter"></a>Входной параметр

- **interface** — указатель на контейнер интерфейса, для которого выбирается альтернативный параметр.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — альтернативный параметр для этого интерфейса успешно выбран.
- **UX_INTERFACE_HANDLE_UNKNOWN** (0x52) — интерфейс не существует.

### <a name="example"></a>Пример

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a>ux_host_stack_transfer_request_abort

Прерывание ожидающего запроса на передачу.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Описание

Эта функция прерывает отправленный ранее ожидающий запрос на передачу. Эта функция отменяет только конкретный запрос на передачу. Обратный вызов функции будет иметь состояние UX_TRANSFER REQUEST_STATUS_ABORT.

### <a name="parameters"></a>Параметры

- **transfer_request** — указатель на запрос на передачу, который нужно прервать.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — передача по USB для этого запроса на передачу отменена.

### <a name="example"></a>Пример

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

Запрос передачи по USB.

### <a name="prototype"></a>Прототип

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a>Описание

Эта функция выполняет транзакцию по USB. На входе запрос на передачу задает канал конечной точки, выбранный для этой транзакции, и параметры, связанные с передачей (полезные данные, длина транзакции). Для канала управления транзакция блокируется и будет возвращаться только по завершении трех этапов передачи управления или при возникновении предыдущей ошибки. Для других каналов стек USB будет планировать транзакцию по USB, но не будет ждать ее завершения. Каждый запрос на передачу для каналов без блокировки должен указывать обработчик подпрограммы завершения.

При возвращении вызова функции следует проверять состояние запроса на передачу, так как в нем содержится результат транзакции.

### <a name="input-parameter"></a>Входной параметр

- **transfer_request** — указатель на запрос на передачу. Запрос на передачу содержит все необходимые сведения, требуемые для переноса.

### <a name="return-values"></a>Возвращаемые значения

- **UX_SUCCESS** (0x00) — перенос по USB для этого запроса на передачу запланирован правильно. Код состояния запроса на передачу следует проверить после завершения запроса на передачу.
- **UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти для выделения необходимых ресурсов контроллера.
- **UX_TRANSFER_NOT_READY** (0x25) — устройство находилось в недопустимом состоянии (допустимые состояния: ATTACHED, ADDRESSED или CONFIGURED).

### <a name="example"></a>Пример

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
