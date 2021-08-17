---
title: Глава 3. Функциональное описание NetX LWM2M для ОСРВ Azure
description: Эта глава содержит функциональное описание NetX LWM2M для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6424023a02aedf43c7433c9adc09231b8c146af13b9bddc15ebd1f2fc02e8c8a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784943"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Глава 3. Функциональное описание NetX LWM2M для ОСРВ Azure

Эта глава содержит функциональное описание NetX LWM2M для ОСРВ Azure.

## <a name="lwm2m-client-initialization"></a>Инициализация клиента LWM2M

Клиент LWM2M инициализируется путем вызова службы ***nx_lwm2m_client_create***. Клиент LWM2M работает в отдельном потоке и может сообщать приложению о некоторых событиях с помощью обратных вызовов или путем вызова методов из пользовательских объектов, реализованных в приложении.

Кроме того, для поддержки связи с одним или несколькими серверами следует создавать сеансы клиента LWM2M путем вызова ***nx_lwm2m_client_session_create***. Каждый сеанс может взаимодействовать с серверами двух разных типов: сервером начальной загрузки или сервером LWM2M (управление устройством).

### <a name="bootstrap-server-session"></a>Сеанс сервера начальной загрузки

Сеанс связи с сервером начальной загрузки позволяет предоставить клиенту LWM2M информацию, которая ему необходима для регистрации на одном или нескольких серверах LWM2M. Этот тип сервера используется в режимах начальной загрузки, инициируемой клиентом и инициируемой сервером.

Приложение может запустить сеанс начальной загрузки путем вызова ***nx_lwm2m_client_session_bootstrap** _ или _*_nx_lwm2m_client_session_bootstrap_dtls_*_, в которых оно должно указать IP-адрес и номер порта сервера, а также необязательный идентификатор экземпляра объекта безопасности. Функция _*_nx_lwm2m_client_session_bootstrap_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_bootstrap_dtls_** создает безопасное подключение к серверу по протоколу DTLS.

Если операция начальной загрузки выполняется успешно, на сервере начальной загрузки должны быть созданы экземпляры объектов безопасности для серверов начальной загрузки и LWM2M, а также экземпляры объектов для серверов LWM2M. Эти сведения приложение должно использовать для создания сеанса связи с серверами LWM2M.

Данные начальной загрузки должны сохраняться приложением в долговременной памяти, чтобы получить возможность создать клиент LWM2M после следующей перезагрузки устройства.

### <a name="lwm2m-server-session"></a>Сеанс сервера LWM2M

Сеанс связи с сервером LWM2M используется для регистрации, управления устройствами и включения службы.

Приложение может зарегистрировать клиент LWM2M на сервере, вызвав ***nx_lwm2m_client_session_register** _ или _*_nx_lwm2m_client_session_register_dtls_*_, в которых нужно предоставить IP-адрес и номер порта сервера, а также короткий идентификатор сервера, соответствующий существующему экземпляру объекта сервера. Функция _*_nx_lwm2m_client_session_register_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_register_dtls_** создает безопасное подключение к серверу по протоколу DTLS.

Приложение может отменить регистрацию клиента LWM2M, вызвав ***nx_lwm2m_client_session_deregister** _, и попросить клиента отправить сообщение обновления (Update), вызвав _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Обратный вызов состояния сеанса

Приложение регистрирует при создании сеанса обратный вызов, который вызывается при обновлении состояния сеанса. Функция обратного вызова NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK имеет следующий прототип:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

Определены следующие состояния:

- **NX_LWM2M_CLIENT_SESSION_INIT**: исходное состояние после создания сеанса.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: клиент ожидает истечения срока таймера задержки (Hold Off) или инициируемой сервером начальной загрузки.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: клиент отправил сообщение запроса (Request) на сервер начальной загрузки (инициируемая клиентом начальная загрузка).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: клиент получает данные от сервера начальной загрузки.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: сервер начальной загрузки отправил сообщение завершения (Finished).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: сеанс начальной загрузки завершился сбоем.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: клиент отправил сообщение о регистрации (Register) на сервер LWM2M.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: клиент успешно зарегистрировался на сервере LWM2M.

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: клиент отправил сообщение обновления (Update) на сервер LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: клиент отправил сообщение отмены регистрации (De-register) на сервер LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: клиент успешно отменил регистрацию на сервере LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: сервер LWM2M отключен. Когда срок действия таймера отключения истечет, будет отправлено сообщение о регистрации.

- **NX_LWM2M_CLIENT_SESSION_ERROR**: операция регистрации или обновления на сервере LWM2M завершилась сбоем.

- **NX_LWM2M_CLIENT_SESSION_DELETED**: удален экземпляр объекта сервера, соответствующий серверу LWM2M. В случае ошибки приложение может выяснить причину ошибки, вызвав **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Управление локальным устройством

Приложение может получить доступ к объектам клиента LWM2M с помощью функций управления локальным устройством. Для этого предлагаются следующие функции:

- ***nx_lwm2m_client_object_read***: чтение ресурсов из экземпляра объекта.

- ***nx_lwm2m_client_object_discover***: получение списка ресурсов из экземпляра объекта.

- ***nx_lwm2m_client_object_read***: запись ресурсов в экземпляр объекта.

- ***nx_lwm2m_client_object_execute***: выполнение операции Execute для ресурса в экземпляре объекта.

- ***nx_lwm2m_client_object_create***: создание экземпляра объекта.

- ***nx_lwm2m_client_object_delete***: удаление существующего экземпляра объекта.

- ***nx_lwm2m_client_object_get_next***: получение следующего идентификатора объекта, реализованного клиентом LWM2M.

- ***nx_lwm2m_client_object_instance_get_next***: получение следующего экземпляра объекта.

## <a name="resource-information"></a>Сведения о ресурсе

При операциях чтения и записи в объекте ресурс представляется структурой NX_LWM2M_RESOURCE. Эта структура содержит идентификатор ресурса или экземпляра и соответствующее значение. Используемая для этого значения кодировка зависит от типа значения и его происхождения (от приложения или из сети).

Структура NX_LWM2M_RESOURCE имеет следующее определение:

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id**: идентификатор ресурса или экземпляра.
- **nx_lwm2m_resource_type**: тип значения (возможные варианты см. ниже).
- **nx_lwm2m_resource_value**: значение ресурса с учетом типа этого значения.

Определены следующие типы значений:

- **NX_LWM2M_RESOURCE_NONE**: пустой ресурс.

- **NX_LWM2M_RESOURCE_STRING**: строковое значение UTF-8, которое оканчивается символом NULL, сохраненное в *nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32**: 32-разрядное целое число, сохраненное в *nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64**: 64-разрядное целое число, сохраненное в *nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32**: 32-разрядное число с плавающей запятой, сохраненное в *nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64**: 64-разрядное число с плавающей точкой, сохраненное в *nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN**: логическое значение, сохраненное в *nx_lwm2m_resource_booleandata*.

- **NX_LWM2M_RESOURCE_OPAQUE**: значение Opaque, определенное в *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK**: значение ссылки на объект, сохраненное в *nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV**: значение в кодировке TLV, определенное в *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT**: значение в формате простого текста, определенное в *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_MULTIPLE**: ресурс с несколькими типами данных, определенный в *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* содержит указатель на массив структур **NX_LWM2M_RESOURCE**, которые содержат информацию о каждом экземпляре ресурса.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: ресурс с несколькими типами данных, определенный в *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* содержит указатель на буфер в кодировке TLV.

Для получения значения и проверки его типа предоставляются вспомогательные функции. Приложение никогда не должно напрямую обращаться к полю *nx_lwm2m_resource_value* за значениями из структуры NX_LWM2M_RESOURCE. Определены следующие функции:

- ***nx_lwm2m_resource_get_***: получение значения с указанным типом.
- ***nx_lwm2m_resource_multiple_get_***: получение значения с указанным типом из ресурса с несколькими типами.

Макрос **NX_LWM2M_RESOURCE_IS_MULTIPLE** (тип) позволяет проверить, является ли определенный ресурс ресурсом с несколькими типами.

## <a name="object-implementation"></a>Реализация объекта

Клиент LWM2M реализует обязательные объекты OMA LWM2M: Security (0), Server (1), Access Control (2) и Device (3). Другие объекты для конкретного устройства следует реализовывать в приложении.

Для определения объекта используются две структуры данных: структура NX_LWM2M_OBJECT определяет реализацию объекта, значение идентификатора и методы объекта, а структура NX_LWM2M_OBJECT_INSTANCE содержит данные для экземпляра объекта.

Структура NX_LWM2M_OBJECT имеет следующее определение:

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next**: следующий объект в списке.
- **nx_lwm2m_object_id**: идентификатор объекта.
- **nx_lwm2m_object_read**: метод Read, который описан ниже.
- **nx_lwm2m_object_discover**: метод Discover, который описан ниже.
- **nx_lwm2m_object_write**: метод Write, который описан ниже.
- **nx_lwm2m_object_execute**: метод Execute, который описан ниже.
- **nx_lwm2m_object_create**: метод Create, который описан ниже.
- **nx_lwm2m_object_delete**: метод Delete, который описан ниже.
- **nx_lwm2m_object_instances**: список экземпляров объектов, которые завершаются символом NULL.

Структура NX_LWM2M_OBJECT_INSTANCE имеет следующее определение:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next**: следующий экземпляр в списке.
- **nx_lwm2m_object_instance_id**: идентификатор экземпляра объекта.

Объект должен реализовать методы, соответствующие операциям, которые определены в интерфейсе управления устройствами LWM2M: Read, Discover, Write, Execute, Create и Delete. Для методов Create и Delete можно указать значение NULL, если объект не поддерживает динамическое создание экземпляров.

### <a name="the-read-method"></a>Метод Read

Метод Read используется для считывания значений ресурса из экземпляра объекта и имеет следующее определение:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Входные параметры определяются следующим образом:

- **object_ptr**: указатель на реализацию объекта.

- **instance_ptr**: указатель на экземпляр объекта.

- **num_values**: количество считываемых ресурсов.

- **values_ptr**: указатель на массив NX_LWM2M_RESOURCE, который содержит список считываемых идентификаторов. При возврате этот массив заполняется соответствующими типами и значениями.

### <a name="the-discover-method"></a>Метод Discover

Метод Discover используется для получения списка всех ресурсов, реализованных объектом, и имеет следующее определение:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Входные параметры определяются следующим образом:

- **object_ptr**: указатель на реализацию объекта.

- **instance_ptr**: указатель на экземпляр объекта.

- **num_resources_ptr**: на входе содержит размер целевого буфера, а на выходе — количество записанных в этот буфер элементов.

- **resources_ptr**: указатель на целевой буфер.

Сведения о ресурсе возвращаются в структуре NX_LWM2M_RESOURCE_INFO, которая определяется следующим образом:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id**: идентификатор ресурса.

- **nx_lwm2m_resource_info_flags**: см. описание ниже.

- **nx_lwm2m_resource_info_dim**: размерность ресурса с несколькими типами, если установлен флаг NX_LWM2M_RESOURCE_INFO_MULTIPLE.

Поле *nx_lwm2m_resource_flags* может иметь следующие значения:

- 0: один доступный для чтения ресурс.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE**: ресурс с несколькими типами, для которого должен быть определен *nx_lwm2m_resource_info_dim*.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: исполняемый или недоступный для чтения ресурс.

### <a name="the-write-method"></a>Метод Write

Метод Write используется для обновления или замены ресурсов в экземпляре объекта и имеет следующее определение:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Входные параметры определяются следующим образом:

- **object_ptr**: указатель на реализацию объекта.
- **instance_ptr**: указатель на экземпляр объекта.
- **num_values**: количество записываемых ресурсов.
- **values_ptr**: указатель на значения ресурсов.
- **write_op**: тип операций записи.

Для параметра *write_op* можно указать следующие операции записи:

- 0 &mdash; частичное обновление. Добавляет или обновляет ресурсы, указанные в новом значении, и сохраняет остальные существующие ресурсы без изменений.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; замена экземпляра. Заменяет существующий экземпляр объекта новым экземпляром с указанными значениями ресурса.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; замена ресурса. Заменяет ресурсы новыми ресурсами с указанными значениями ресурса (используется для замены ресурсов с несколькими типами).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; создание экземпляра. Инициализирует новый экземпляр объекта с указанными значениями ресурса (вызывается из метода *nx_lwm2m_object_create*).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; запись при начальной загрузке. Вызывается при выполнении последовательности начальной загрузки.

### <a name="the-execute-method"></a>Метод Execute

Метод Execute реализует выполнение ресурса объекта и имеет следующее определение:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Входные параметры определяются следующим образом:

- **object_ptr**: указатель на реализацию объекта.
- **instance_ptr**: указатель на экземпляр объекта.
- **resource_id**: идентификатор ресурса.
- **arguments_ptr**: указатель на аргументы операции исполнения. Может иметь значение NULL, если *arguments_length* равен нулю.
- **arguments_length**: длина аргументов.

Эта функция должна возвращать NX_LWM2M_NOT_FOUND, если идентификатор ресурса не существует, или NX_LWM2M_METHOD_NOT_ALLOWED, если он не поддерживает исполнение.

### <a name="the-create-method"></a>Метод Create

Метод Create реализует создание нового экземпляра объекта и имеет следующее определение:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Входные параметры определяются следующим образом:

- **object_ptr**: указатель на реализацию объекта.
- **instance_id**: идентификатор нового экземпляра.
- **num_values**: количество инициализируемых ресурсов.
- **values_ptr**: указатель на значения ресурсов.
- **instance_ptr**: указатель на целевой указатель созданного экземпляра.
- **bootstrap**: имеет значение True, если вызов осуществляется при начальной загрузке.

Объект должен выделить и инициализировать новый экземпляр объекта, используя предоставленный список значений ресурсов.

### <a name="the-delete-method"></a>Метод Delete

Метод Delete реализует удаление экземпляра объекта и имеет следующее определение:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Входные параметры определяются следующим образом:

- **object_ptr**: указатель на реализацию объекта.
- **instance_ptr**: указатель на экземпляр объекта.

При успешном выполнении объект должен освободить память, занимаемую данными экземпляра объекта и любыми ресурсами, которые выделил этот экземпляр.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Добавление реализаций и экземпляров объектов в клиент LWM2M

Приложение может добавить в клиент LWM2M новую реализацию объекта, вызвав службу ***nx_lwm2m_client_object_add***.

Если объект не поддерживает динамическое создание экземпляров, (например, используется только один экземпляр объекта), то поле *nx_lwm2m_object_instances* в структуре объекта должно указывать на список структур статических экземпляров.

Если объект поддерживает динамическое создание экземпляров, то *nx_lwm2m_object_instances* должно иметь значение NULL, а для вызова метода Create этого объекта следует использовать службу ***nx_lwm2m_client_object_create***.

## <a name="example-of-lwm2m-client-application"></a>Пример клиентского приложения LWM2M

Следующий код представляет собой пример простого клиентского приложения LWM2M, которое реализует пользовательское устройство, состоящее из датчика температуры и выключателя света.

Это устройство позволяет серверу считывать значение датчика температуры и логическое состояние выключателя света, а также устанавливать этот выключатель в положения "Включено" или "Выключено".

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
