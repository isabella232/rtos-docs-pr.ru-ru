---
title: Глава 4. Описание служб ОСРВ Azure NetX LWM2M
description: В этой главе приводится описание всех служб ОСРВ Azure NetX LWM2M, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815168"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a>Глава 4. Описание служб ОСРВ Azure NetX LWM2M

В этой главе приводится описание всех служб ОСРВ Azure NetX LWM2M, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

### <a name="lwm2m-client-management"></a>Управление клиентом LWM2M

- **nx_lwm2m_client_create**: *создание клиента LWM2M*.
- **nx_lwm2m_client_delete**: *удаление клиента LWM2M*.
- **nx_lwm2m_client_lock**: *блокирование клиента LWM2M*.
- **nx_lwm2m_client_object_add**: *добавление реализации объекта в клиент LWM2M*.
- **nx_lwm2m_client_unlock**: *разблокирование клиента LWM2M*.

### <a name="lwm2m-client-session-management"></a>Управление сеансами клиентов LWM2M

- **nx_lwm2m_client_session_bootstrap**: *запуск сеанса с сервером начальной загрузки*.
- **nx_lwm2m_client_session_bootstrap_dtls**: *запуск безопасного сеанса с сервером начальной загрузки*.
- **nx_lwm2m_client_session_create**: *создание сеанса клиента LWM2M*.
- **nx_lwm2m_client_session_delete**: *удаление сеанса клиента LWM2M*.
- **nx_lwm2m_client_session_deregister**: *завершение сеанса взаимодействия с сервером LWM2M*.
- **nx_lwm2m_client_session_error_get**: *получение сведений о последней ошибке сеанса*.
- **nx_lwm2m_client_session_register**: *запуск сеанса взаимодействия с сервером LWM2M*.
- **nx_lwm2m_client_session_register_dtls**: *запуск безопасного сеанса взаимодействия с сервером LWM2M*.
- **nx_lwm2m_client_session_update**: *обновление сеанса взаимодействия с сервером LWM2M*.

### <a name="security-object-implementation"></a>Реализация объекта безопасности

- **nx_lwm2m_client_security_key_callbacks_set**: *настройка обратных вызовов управления ключами безопасности*.

### <a name="device-object-implementation"></a>Реализация объекта устройства

- **nx_lwm2m_client_device_callbacks_set**: *настройка обратных вызовов приложения объекта устройства*.
- **nx_lwm2m_client_device_error_push**: *добавление кода ошибки в объект устройства*.
- **nx_lwm2m_client_device_error_reset**: *сброс кодов ошибок объекта устройства*.
- **nx_lwm2m_client_device_resource_changed**: *сигнальное изменение ресурса объекта устройства*.

### <a name="custom-objects-implementation"></a>Реализация пользовательских объектов

- **nx_lwm2m_object_resource_changed**: *сигнальное изменение значения ресурса экземпляра объекта*.

### <a name="local-device-management"></a>Управление локальным устройством

- **nx_lwm2m_client_object_create**: *создание нового экземпляра объекта*.
- **nx_lwm2m_client_object_delete**: *удаление экземпляра объекта*.
- **nx_lwm2m_client_object_discover**: *обнаружение ресурсов экземпляра объекта*.
- **nx_lwm2m_client_object_execute**: *выполнение ресурса экземпляра объекта*.
- **nx_lwm2m_client_object_next_get**: *получение списка объектов, реализованных в клиенте LWM2M*.
- **nx_lwm2m_client_object_instance_get_next**: *получение списка экземпляров объекта*.
- **nx_lwm2m_client_object_read**: *чтение значений ресурсов экземпляра объекта*.
- **nx_lwm2m_client_object_write**: *изменение значений ресурсов экземпляра объекта*.

### <a name="resources-values-decoding"></a>Декодирование значений ресурсов

- **nx_lwm2m_client_resource_boolean_get**: *получение значения логического ресурса*.
- **nx_lwm2m_resource_get_float32**: *получение значения 32-разрядного ресурса с плавающей запятой*.
- **nx_lwm2m_resource_get_float64**: *получение значения 64-разрядного ресурса с плавающей запятой*.
- **nx_lwm2m_resource_get_integer32**: *получение значения 32-разрядного целочисленного ресурса*.
- **nx_lwm2m_resource_get_integer64**: *получение значения 64-разрядного целочисленного ресурса*.
- **nx_lwm2m_resource_get_objlnk**: *получение значения ресурса ссылки на объект*.
- **nx_lwm2m_resource_get_opaque**: *получение значения непрозрачного ресурса*.
- **nx_lwm2m_resource_get_string**: *получение значения строкового ресурса*.
- **nx_lwm2m_resource_multiple_get_boolean**: *получение значения логического ресурса для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_float32**: *получение значения 32-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_float64**: *получение значения 64-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_integer32**: *получение значения 32-разрядного целочисленного ресурса для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_integer64**: *получение значения 64-разрядного целочисленного ресурса для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_objlnk**: *получение значения ссылки на объект для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_opaque**: *получение значения непрозрачного ресурса для нескольких экземпляров ресурса*.
- **nx_lwm2m_resource_multiple_get_string**: *получение значения строкового ресурса для нескольких экземпляров ресурса*.

### <a name="firmware-update-object"></a>Объект обновления встроенного ПО

- **nx_lwm2m_firmware_create**: *создание объекта обновления встроенного ПО*.
- **nx_lwm2m_firmware_package_info_set**: *настройка сведений о пакете обновления встроенного ПО*.
- **nx_lwm2m_firmware_result_set**: *настройка результата обновления встроенного ПО*.
- **nx_lwm2m_firmware_state_set**: *настройка состояния обновления встроенного ПО*.

## <a name="nx_lwm2m_client_create"></a>nx_lwm2m_client_create

Создание клиента LWM2M

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента LWM2M, который выполняется в контексте собственного потока ThreadX.

Клиент LWM2M реализует следующие объекты OMA LWM2M: безопасность (0), сервер (1), контроль доступа (2) и устройство (3). Другие реализации объектов должны быть добавлены посредством приложения.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **ip_ptr**: указатель на созданный ранее экземпляр IP.
- **packet_pool_ptr**: указатель на пул пакетов по умолчанию для данного клиента LWM2M.
- **local_port**: локальный UDP-порт, используемый для небезопасного взаимодействия.
- **name_ptr**: указатель на имя конечной точки клиента LWM2M.
- **msisdn_ptr**: указатель на номер мобильного абонента сети ISDN (MSISDN), по которому можно связаться с клиентом LWM2M для использования с привязкой SMS. Может иметь значение NULL, если привязка SMS не поддерживается.
- **binding_modes**: привязка и режимы, поддерживаемые клиентом LWM2M, должны являться комбинацией флагов NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S и NX_LWM2M_BINDING_SQ.
- **stack_ptr**: указатель на область стека потоков клиента LWM2M.
- **stack_size**: размер стека потоков клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: клиент LWM2M успешно создан.
- **NX_LWM2M_ERROR**: ошибка создания клиента LWM2M.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_delete"></a>nx_lwm2m_client_delete

Удаление клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет созданный ранее экземпляр клиента LWM2M.

Этот вызов также удаляет все сеансы, подключенные в данный момент к этому клиенту.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: клиент LWM2M успешно удален.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_device_callbacks_set"></a>nx_lwm2m_client_device_callbacks_set

Настройка обратных вызовов приложения объекта устройства.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a>Описание

Данная служба устанавливает обратные вызовы приложения для реализации операций с ресурсами объекта устройства LWM2M, которые не обрабатываются клиентом LWM2M.

Клиент LWM2M реализует следующие ресурсы: код ошибки (11), сброс кода ошибки (12) и поддерживаемые привязки и режимы (16). Операции с другими ресурсами перенаправляются в приложение.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **read_callback**: обратный вызов метода Read.
- **discover_callback**: обратный вызов метода Discover.
- **write_callback**: обратный вызов метода Write.
- **execute_callback**: обратный вызов метода Execute.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_device_error_push"></a>nx_lwm2m_client_device_error_push

Добавление кода ошибки в объект устройства.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a>Описание

Данная служба добавляет новый экземпляр в ресурс кода ошибки (11) объекта устройства.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **code**: новый код ошибки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BUFFER_TOO_SMALL**: достигнуто максимальное число хранимых кодов ошибок.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_device_error_reset"></a>nx_lwm2m_client_device_error_reset

Сброс кодов ошибок объекта устройства.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет все экземпляры ресурса кода ошибки из объекта устройства. Это эквивалентно выполнению кода ошибки сброса ресурса (12).

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_device_resource_changed"></a>nx_lwm2m_client_device_resource_changed

Сигнальное изменение ресурса объекта устройства.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Описание

Служба используется приложением для сообщения клиенту LWM2M об изменении ресурса объектного устройства. Если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **resource**: указатель на структуру, описывающую измененный ресурс.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_lock"></a>nx_lwm2m_client_lock

Блокировка клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба блокирует клиент LWM2M, чтобы предотвратить одновременный доступ к объектам LWM2M с серверов или из другого потока приложения.

Если клиент LWM2M на данный момент заблокирован другим потоком, функция будет заблокирована до тех пор, пока клиент LWM2M не будет разблокирован.

Вызовы пар nx_lwm2m_client_lock() и nx_lwm2m_client_unlock() могут быть вложенными.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_add"></a>nx_lwm2m_client_object_add

Добавление реализации объекта в клиент LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a>Описание

Данная служба добавляет новую реализацию объекта в клиент LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_ptr**: указатель на структуру, определяющую реализацию объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_ALREADY_EXIST**: идентификатор объекта уже существует.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_create"></a>nx_lwm2m_client_object_create

Создание нового экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Create с объектом клиента LWM2M для создания нового экземпляра объекта.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id_ptr**: указатель на идентификатор нового экземпляра. Если клиент LWM2M должен назначить идентификатор экземпляра, то этот параметр может иметь значение NULL. Если идентификатор представляет собой зарезервированное значение 65535, то клиент LWM2M назначит идентификатор экземпляра. Если значение не равно NULL, то после вызова возвращается назначенный идентификатор.
- **num_values**: количество задаваемых значений.
- **values_ptr**: указатель на массив значений ресурсов для инициализации нового экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_ALREADY_EXIST**: идентификатор экземпляра объекта уже существует.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: объект не поддерживает создание экземпляров.
- **NX_LWM2M_NO_MEMORY**: невозможно выделить память для хранения нового экземпляра.
- **NX_LWM2M_NOT_FOUND**: идентификатор объекта не существует.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_delete"></a>nx_lwm2m_client_object_delete

Удаление экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Delete с экземпляром объекта клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id**: идентификатор экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: объект не поддерживает удаления экземпляров.
- **NX_LWM2M_NOT_FOUND**: идентификатор объекта или идентификатор экземпляра объекта не существует.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_discover"></a>nx_lwm2m_client_object_discover

Обнаружение ресурсов экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Discover для экземпляра объекта клиента LWM2M, в результате чего возвращается список ресурсов, реализованных объектом.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id**: идентификатор экземпляра объекта.
- **num_resources_ptr**: для ввода содержит размер целевого буфера, а для вывода — количество записанных в этот буфер элементов.
- **resources_ptr**: указатель на целевой буфер.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция выполнена успешно.
- **NX_LWM2M_BUFFER_TOO_SMALL**: недостаточный размер буфера ресурсов для хранения списка ресурсов.
- **NX_LWM2M_NOT_FOUND**: идентификатор объекта или идентификатор экземпляра объекта не существует.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_execute"></a>nx_lwm2m_client_object_execute

Выполнение ресурса экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Execute с ресурсом экземпляра объекта клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id**: идентификатор экземпляра объекта.
- **resource_id**: идентификатор ресурса.
- **arguments_ptr**: указатель на аргументы операции выполнения. Может иметь значение NULL, если значение arguments_length равно нулю.
- **arguments_length**: длина аргументов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: ресурс не поддерживает операцию выполнения.
- **NX_LWM2M_NOT_FOUND**: идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_get_next"></a>nx_lwm2m_client_object_get_next

Получение списка объектов, реализованных клиентом LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a>Описание

Данная служба возвращает идентификатор следующего объекта, реализованного клиентом LWM2M. Если для текущего идентификатора объекта установлено значение NX_LWM2M_RESERVED_ID (65535), возвращается первый идентификатор объекта.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id_ptr**: указатель на текущий идентификатор объекта. При возврате содержит следующий идентификатор объекта, реализованный клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция выполнена успешно.
- **NX_LWM2M_NOT_FOUND**: данный идентификатор объекта является последним в базе данных.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_instance_get_next"></a>nx_lwm2m_client_object_instance_get_next

Получение списка экземпляров объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a>Описание

Данная служба возвращает идентификатор следующего экземпляра данного объекта. Если для текущего идентификатора экземпляра установлено NX_LWM2M_RESERVED_ID (65535), возвращается идентификатор первого экземпляра.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id_ptr**: указатель на текущий идентификатор экземпляра объекта. При возврате содержит идентификатор следующего экземпляра объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция выполнена успешно.
- **NX_LWM2M_NOT_FOUND**: заданный идентификатор экземпляра является последним для объекта, или идентификатор объекта не реализован.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_read"></a>nx_lwm2m_client_object_read

Чтение значений ресурсов экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a>Описание

Эта служба выполняет операцию Read с экземпляром объекта клиента LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id**: идентификатор экземпляра объекта.
- **num_values**: количество считываемых ресурсов.
- **values_ptr**: указатель на массив NX_LWM2M_RESOURCE, который содержит список считываемых идентификаторов. По возвращении массив заполняется соответствующими типами и значениями.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: ресурс не поддерживает операцию считывания.
- **NX_LWM2M_NOT_FOUND**: идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_object_write"></a>nx_lwm2m_client_object_write

Изменение значений ресурсов экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Write с экземпляром объекта клиента LWM2M.

Для параметра *write_op* можно указать следующие операции записи.

- **0**: частичное обновление. Добавляет или обновляет ресурсы, указанные в новом значении, и сохраняет остальные существующие ресурсы без изменений.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE**: замена экземпляра. Заменяет существующий экземпляр объекта новым экземпляром с указанными значениями ресурса.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE**: замена ресурса. Заменяет ресурсы новыми ресурсами с указанными значениями ресурса (используется для замены ресурсов с несколькими типами).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP**: запись начальной загрузки. Указывает вызов из последовательности начальной загрузки.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **object_id**: идентификатор объекта.
- **instance_id**: идентификатор экземпляра объекта.
- **num_values**: количество записываемых ресурсов.
- **values_ptr**: указатель на массив NX_LWM2M_RESOURCE, содержащий идентификаторы ресурсов, типы и значения для записи.
- **write_op**: тип операции записи.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: недопустимый тип ресурса.
- **NX_LWM2M_BUFFER_TOO_SMALL**: длина значения слишком велика для сохранения в экземпляре.
- **NX_LWM2M_METHOD_NOT_ALLOWED**: ресурс не поддерживает операции записи.
- **NX_LWM2M_NO_MEMORY**: невозможно выделить память для хранения значения ресурса.
- **NX_LWM2M_NOT_ACCEPTABLE**: недопустимое значение ресурса.
- **NX_LWM2M_NOT_FOUND**: идентификатор объекта, идентификатор экземпляра объекта или идентификатор ресурса не существует.
- NX_OPTION_ERROR: недопустимый тип операции записи.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a>nx_lwm2m_client_security_key_callbacks_set

Настройка обратных вызовов управления ключами объекта безопасности.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a>Описание

Эта служба устанавливает обратные вызовы приложения для реализации операций с ресурсами объекта безопасности LWM2M, связанными с ключами безопасности.

Клиент LWM2M делегирует управление ключами безопасности приложению во время сеансов начальной загрузки. Обратные вызовы вызываются, когда сервер начальной загрузки записывает или удаляет следующие ресурсы в экземпляре объекта безопасности: открытый ключ или удостоверение (3), открытый ключ сервера (4), секретный ключ (5).

Приложение отвечает за хранение данных ключей и настройку сеансов DTLS, используемых клиентом LWM2M.

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.
- **write_callback**: обратный вызов метода Write для ключа.
- **delete_callback**: обратный вызов метода Delete для ключа.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_bootstrap"></a>nx_lwm2m_client_session_bootstrap

Запуск сеанса взаимодействия с сервером начальной загрузки.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Описание

Данная служба запускает сеанс взаимодействия с сервером начальной загрузки. Сервер должен иметь соответствующий экземпляр безопасности в объекте безопасности.

Если ожидающий ресурс отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициируемой сервером начальной загрузки. Если сервер не инициирует загрузку по истечении этого периода времени, будет выполнена инициированная клиентом начальная загрузка.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.
- **security_id**: если на сервере начальной загрузки не определен экземпляр безопасности, то идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение NX_LWM2M_RESERVED_ID (65535).
- **ip_address**: IP-адрес сервера.
- **port**: UDP-порт сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта безопасности, соответствующий идентификатору экземпляра безопасности.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a>nx_lwm2m_client_session_bootstrap_dtls

Запуск безопасного сеанса взаимодействия с сервером начальной загрузки.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Описание

Данная служба запускает сеанс с сервером начальной загрузки, используя безопасное подключение DTLS. Сервер должен иметь соответствующий экземпляр безопасности в объекте безопасности.

Перед вызовом данной функции необходимо настроить сеанс DTLS с использованием соответствующих комплектов шифров и материала ключа. Необходимо определить NX_SECURE_ENABLE_DTLS.

Если ожидающий ресурс отличен от нуля в экземпляре безопасности, связанном с данным сервером, сеанс будет ожидать инициируемой сервером начальной загрузки. Если сервер не инициирует загрузку по истечении этого периода времени, будет выполнена инициированная клиентом начальная загрузка.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом сервера начальной загрузки.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.
- **security_id**: если на сервере начальной загрузки не определен экземпляр безопасности, то идентификатор экземпляра безопасности сервера начальной загрузки должен иметь значение NX_LWM2M_RESERVED_ID (65535).
- **ip_address**: IP-адрес сервера.
- **port**: UDP-порт сервера.
- **dtls_session_ptr**: сеанс DTLS, используемый для сеанса начальной загрузки.
- **dtls_local_port**: локальный UDP-порт, используемый для сеанса DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта безопасности, соответствующий идентификатору экземпляра безопасности.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_create"></a>nx_lwm2m_client_session_create

Создание сеанса клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a>Описание

Данная служба создает новый сеанс клиента LWM2M, подключенный к существующему клиенту LWM2M. Этот сеанс используется клиентом LWM2M для взаимодействия с сервером начальной загрузки или сервером LWM2M.

Приложение должно предоставить функцию обратного вызова, которая будет вызываться при обновлении состояния сеанса.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.
- **client_ptr**: указатель на созданный ранее клиент LWM2M.
- **state_callback**: обратный вызов приложения, который выполняется при изменении состояния сеанса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_delete"></a>nx_lwm2m_client_session_delete

Удаление сеанса клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба удаляет сеанс клиента LWM2M.

Когда клиент LWM2M удаляется вызовом nx_lwm2m_client_delete, также удаляются все сеансы, подключенные к этому клиенту.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_deregister"></a>nx_lwm2m_client_session_deregister

Завершение сеанса взаимодействия с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию De-Register на сервере LWM2M.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_NOT_REGISTERED**: клиент не зарегистрирован на сервере.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_error_get"></a>nx_lwm2m_client_session_error_get

Получение последней ошибки сеанса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба возвращает код ошибки сеанса в случае, когда сеанс находится в состоянии ошибки.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: сеанс не находится в состоянии ошибки.
- **NX_LWM2M_ADDRESS_ERROR**: недопустимый адрес сервера.
- **NX_LWM2M_BUFFER_TOO_SMALL**: полезные данные запроса не вмещаются в сетевой буфер.
- **NX_LWM2M_ NX_LWM2M_DTLS_ERROR**: не удалось установить защищенное подключение к серверу.
- **NX_LWM2M_ERROR**: неопределенная ошибка.
- **NX_LWM2M_FORBIDDEN**: сервер отказал в регистрации.
- **NX_LWM2M_NOT_FOUND**: клиент не найден сервером при обновлении или отмене регистрации.
- **NX_LWM2M_SERVER_INSTANCE_DELETED**: экземпляр объекта сервера, соответствующий сеансу, был удален.
- **NX_LWM2M_TIMED_OUT**: нет ответа с сервера.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_register"></a>nx_lwm2m_client_session_register

Запуск сеанса взаимодействия с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Register на сервере LWM2M. Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.

Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения Update, пока регистрация клиента не будет отменена.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.
- **server_id**: краткий идентификатор сервера LWM2M.
- **ip_address**: IP-адрес сервера.
- **port**: UDP-порт сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция выполнена успешно.
- **NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта сервера, соответствующий короткому идентификатору сервера.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_register_dtls"></a>nx_lwm2m_client_session_register_dtls

Запуск безопасного сеанса взаимодействия с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Register на сервере LWM2M, используя безопасное подключение DTLS. Сервер должен иметь соответствующий экземпляр сервера в объекте сервера.

Перед вызовом данной функции необходимо настроить сеанс DTLS с использованием соответствующих комплектов шифров и материала ключа. Необходимо определить NX_SECURE_ENABLE_DTLS.

Каждый сеанс DTLS использует собственный сокет UDP для обмена данными, поэтому локальный порт dtls_local_port должен быть разным для каждого сеанса, если приложение создает несколько безопасных сеансов.

Если регистрация прошла успешно, клиент LWM2M будет обрабатывать дальнейшие операции с сервера и периодически отправлять сообщения Update, пока регистрация клиента не будет отменена.

Любой текущий активный сеанс прерывается этим вызовом и заменяется новым сеансом LWM2M Server.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.
- **server_id**: краткий идентификатор сервера LWM2M.
- **ip_address**: IP-адрес сервера.
- **port**: UDP-порт сервера.
- **dtls_session_ptr**: сеанс DTLS, используемый для сеанса LWM2M.
- **dtls_local_port**: локальный UDP-порт, используемый для сеанса DTLS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_NOT_FOUND**: отсутствует экземпляр объекта сервера, соответствующий короткому идентификатору сервера.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_session_update"></a>nx_lwm2m_client_session_update

Обновление сеанса взаимодействия с сервером LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a>Описание

Данная служба выполняет операцию Update на сервере LWM2M.

### <a name="parameters"></a>Параметры

- **session_ptr**: указатель на блок управления сеансом клиента LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_NOT_REGISTERED**: клиент не зарегистрирован на сервере.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_client_unlock"></a>nx_lwm2m_client_unlock

Разблокирование клиента LWM2M.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Данная служба разблокирует заблокированный ранее клиент LWM2M вызовом nx_lwm2m_client_unlock().

### <a name="parameters"></a>Параметры

- **client_ptr**: указатель на блок управления клиентом LWM2M.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_firmware_create"></a>nx_lwm2m_firmware_create

Создание объекта обновления встроенного ПО.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a>Описание

Эта служба инициализирует объект обновления встроенного ПО и добавляет этот объект в созданный ранее клиент LWM2M. Объект обновления встроенного ПО реализует ресурсы для взаимодействия с сервером LWM2M, но приложение должно обеспечить обратные вызовы для реализации фактических операций со встроенным ПО (скачивание, хранение и обновление встроенного ПО).

Параметр protocols указывает, какие протоколы поддерживаются приложением для получения встроенного ПО с помощью ресурса URI пакета. Определяются следующие флаги:

NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.

### <a name="parameters"></a>Параметры

- **firmware_ptr**: указатель на блок управления объектом встроенного ПО.
- **client_ptr**: указатель на созданный ранее клиент LWM2M.
- **protocols**: флаги, указывающие, какие протоколы поддерживаются ресурсом URI пакета.
- **package_callback**: должен иметь значение NULL [подлежит уточнению].
- **package_uri_callback**: обратный вызов, используемый для реализации ресурса URI пакета.
- **update_callback**: обратный вызов, используемый для реализации ресурса обновления.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_firmware_package_info_set"></a>nx_lwm2m_firmware_package_info_set

Настройка сведений о пакете обновления встроенного ПО.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a>Описание

Эта служба изменяет значения ресурсов PkgName (6) и PkgVersion (7) объекта обновления встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr**: указатель на объект обновления встроенного ПО.
- **name**: новое значение имени пакета.
- **version**: новое значение версии пакета.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_firmware_result_set"></a>nx_lwm2m_firmware_result_set

Настройка результата обновления встроенного ПО.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a>Описание

Эта служба изменяет значение ресурса Update Result (5) объекта обновления встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr**: указатель на объект обновления встроенного ПО.
- **result**: новое значение ресурса Update Result.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_firmware_state_set"></a>nx_lwm2m_firmware_state_set

Настройка состояния обновления встроенного ПО.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a>Описание

Эта служба изменяет значение ресурса State (3) объекта обновления встроенного ПО.

### <a name="parameters"></a>Параметры

- **firmware_ptr**: указатель на объект обновления встроенного ПО.
- **state**: новое значение ресурса State.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_object_resource_changed"></a>nx_lwm2m_object_resource_changed

Сигнальное изменение значения ресурса экземпляра объекта.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a>Описание

Эта служба используется реализацией объекта для сообщения клиенту LWM2M о том, что одно из его значений ресурсов изменилось. Если за ресурсом наблюдает сервер LWM2M, клиент LWM2M отправит соответствующее уведомление.

### <a name="parameters"></a>Параметры

- **object_ptr**: указатель на реализацию объекта.
- **instance_ptr**: указатель на экземпляр объекта.
- **resource**: указатель на структуру, описывающую измененный ресурс.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- NX_PTR_ERROR: недопустимый указатель.

## <a name="nx_lwm2m_resource_get_boolean"></a>nx_lwm2m_resource_get_boolean

Получение значения логического ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение логического ресурса.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **bool_ptr**: указатель на целевое логическое значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является логическим значением.

## <a name="nx_lwm2m_resource_get_float32"></a>nx_lwm2m_resource_get_float32

Получение значения 32-разрядного ресурса с плавающей запятой.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Описание

Эта служба извлекает значение 32-разрядного ресурса с плавающей запятой.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **float32_ptr**: указатель на целевое 32-разрядное значение с плавающей запятой.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является значением с плавающей запятой.

## <a name="nx_lwm2m_resource_get_float64"></a>nx_lwm2m_resource_get_float64

Получение значения 64-разрядного ресурса с плавающей запятой.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Описание

Эта служба извлекает значение 64-разрядного ресурса с плавающей запятой.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **float64_ptr**: указатель на целевое 64-разрядное значение с плавающей запятой.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является значением с плавающей запятой.

## <a name="nx_lwm2m_resource_get_integer32"></a>nx_lwm2m_resource_get_integer32

Получение значения 32-разрядного целочисленного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение 32-разрядного целочисленного ресурса.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **int32_ptr**: указатель на целевое 32-разрядное целочисленное значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является целым числом или целочисленное значение не умещается в 32-разрядном числе.

## <a name="nx_lwm2m_resource_get_integer64"></a>nx_lwm2m_resource_get_integer64

Получение значения 64-разрядного целочисленного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение 64-разрядного целочисленного ресурса.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **int64_ptr**: указатель на целевое 64-разрядное целочисленное значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является целым числом.

## <a name="nx_lwm2m_resource_get_objlnk"></a>nx_lwm2m_resource_get_objlnk

Получение значения ресурса ссылки на объект.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Описание

Служба извлекает значение ресурса ссылки на объект.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **objlnk_ptr**: указатель на целевое значение ссылки на объект.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является ссылкой на объект.

## <a name="nx_lwm2m_resource_get_opaque"></a>nx_lwm2m_resource_get_opaque

Получение значения непрозрачного ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a>Описание

Эта служба извлекает значение непрозрачного ресурса.

Значение непрозрачного ресурса состоит из указателя на буфер и длины.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **opaque_ptr_ptr**: указатель на указатель на целевой непрозрачный буфер.
- **opaque_length_ptr**: указатель на длину целевого непрозрачного буфера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является непрозрачным значением.

## <a name="nx_lwm2m_resource_get_string"></a>nx_lwm2m_resource_get_string

Получение значения строкового ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a>Описание

Эта служба извлекает значение строкового ресурса.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения ресурса.
- **string_ptr_ptr**: указатель на указатель на целевую строку.
- **string_length_ptr**: указатель на длину целевой строки. Может иметь значение NULL, если строка оканчивается нулевым символом.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_ENCODING**: значение ресурса не является строкой.

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a>nx_lwm2m_resource_multiple_get_boolean

Получение значения логического ресурса для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра логического ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **bool_ptr**: указатель на целевое логическое значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является логическим значением.

## <a name="nx_lwm2m_resource_multiple_get_float32"></a>nx_lwm2m_resource_multiple_get_float32

Получение значения 32-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра 32-разрядного ресурса с плавающей запятой для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **float32_ptr**: указатель на целевое 32-разрядное значение с плавающей запятой.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является числом с плавающей запятой.

## <a name="nx_lwm2m_resource_multiple_get_float64"></a>nx_lwm2m_resource_multiple_get_float64

Получение значения 64-разрядного ресурса с плавающей запятой для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра 64-разрядного ресурса с плавающей запятой для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **float64_ptr**: указатель на целевое 64-разрядное значение с плавающей запятой.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является числом с плавающей запятой.

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a>nx_lwm2m_resource_multiple_get_integer32

Получение значения 32-разрядного целочисленного ресурса для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра 32-разрядного целочисленного ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **int32_ptr**: указатель на целевое 32-разрядное целочисленное значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом, значение ресурса не является целым числом или целочисленное значение не умещается в 32-разрядном числе.

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a>nx_lwm2m_resource_multiple_get_integer64

Получение значения 64-разрядного целочисленного ресурса для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра 64-разрядного целочисленного ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **int64_ptr**: указатель на целевое 64-разрядное целочисленное значение.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является целым числом.

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a>nx_lwm2m_resource_multiple_get_objlnk

Получение значения ссылки на объект для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра ресурса ссылки на объект для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **objlnk_ptr**: указатель на целевое значение ссылки на объект.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является ссылкой на объект.

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a>nx_lwm2m_resource_multiple_get_opaque

Получение значения непрозрачного ресурса для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра непрозрачного ресурса для нескольких ресурсов.

Значение непрозрачного ресурса состоит из указателя на буфер и длины.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **opaque_ptr_ptr**: указатель на указатель на целевой непрозрачный буфер.
- **opaque_length_ptr**: указатель на длину целевого непрозрачного буфера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение ресурса не является непрозрачным значением.

## <a name="nx_lwm2m_resource_multiple_get_string"></a>nx_lwm2m_resource_multiple_get_string

Получение значения строкового ресурса для нескольких экземпляров ресурса.

### <a name="prototype"></a>Прототип

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a>Описание

Эта служба получает значение экземпляра строкового ресурса для нескольких ресурсов.

### <a name="parameters"></a>Параметры

- **value**: указатель на описание значения нескольких ресурсов.
- **index**: индекс экземпляра, который необходимо получить из массива значений ресурсов.
- **instance_id_ptr**: указатель на идентификатор целевого экземпляра.
- **string_ptr_ptr**: указатель на указатель на целевую строку.
- **string_length_ptr**: указатель на длину целевой строки. Может иметь значение NULL, если строка оканчивается нулевым символом.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: операция успешно выполнена.
- **NX_LWM2M_BAD_PARAMETER**: индекс вне диапазона.
- **NX_LWM2M_BAD_ENCODING**: ресурс не является множественным ресурсом или значение экземпляра не является строкой.
