---
title: Глава 3. Функциональное описание клиента LWM2M
description: Эта глава содержит функциональное описание клиента LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814679"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Глава 3. Функциональное описание клиента LWM2M

> Эта глава содержит функциональное описание клиента LWM2M.

## <a name="lwm2m-client-initialization"></a>Инициализация клиента LWM2M

Клиент LWM2M инициализируется путем вызова службы ***nx_lwm2m_client_create***. Клиент LWM2M работает в отдельном потоке и может сообщать приложению о некоторых событиях с помощью обратных вызовов или путем вызова методов из пользовательских объектов, реализованных в приложении.

Кроме того, для поддержки связи с одним или несколькими серверами следует создавать сеансы клиента LWM2M путем вызова ***nx_lwm2m_client_session_create***. Каждый сеанс может взаимодействовать с серверами двух разных типов: сервером начальной загрузки или сервером LWM2M (управление устройством).

### <a name="bootstrap-server-session"></a>Сеанс сервера начальной загрузки

Сеанс связи с сервером начальной загрузки позволяет предоставить клиенту LWM2M информацию, которая необходима ему для регистрации на одном или нескольких серверах LWM2M. Этот тип сервера используется в режимах начальной загрузки, инициируемой клиентом и сервером.

Приложение может запустить сеанс начальной загрузки путем вызова ***nx_lwm2m_client_session_bootstrap** _ или _*_nx_lwm2m_client_session_bootstrap_dtls_*_, в которых оно должно указать IP-адрес и номер порта сервера, а также необязательный идентификатор экземпляра объекта безопасности. Функция _*_nx_lwm2m_client_session_bootstrap_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_bootstrap_dtls_** создает безопасное подключение к серверу по протоколу DTLS.

Если операция начальной загрузки выполняется успешно, на сервере начальной загрузки должны быть созданы экземпляры объектов безопасности для серверов начальной загрузки и LWM2M, а также экземпляры объектов сервера для серверов LWM2M. Приложение может вызвать функцию ***nx_lwm2m_client_session_register_info_get***, чтобы получить информацию о серверах LWM2M и использовать эти сведения для установления сеанса с серверами LWM2M.

Данные начальной загрузки должны сохраняться приложением в энергонезависимой памяти, чтобы было можно создать клиент LWM2M при следующей перезагрузке устройства.

### <a name="lwm2m-server-session"></a>Сеанс сервера LWM2M

Сеанс связи с сервером LWM2M используется для регистрации, управления устройствами и включения службы.

Приложение может зарегистрировать клиент LWM2M на сервере путем вызова ***nx_lwm2m_client_session_register** _ или _*_nx_lwm2m_client_session_register_dtls_*_, в которых оно должно указать IP-адрес и номер порта сервера, а также короткий идентификатор сервера, соответствующий существующему экземпляру объекта сервера. Функция _*_nx_lwm2m_client_session_register_*_ использует обмен данными без защиты, а _ *_nx_lwm2m_client_session_register_dtls_** создает безопасное подключение к серверу по протоколу DTLS.

Приложение может отменить регистрацию клиента LWM2M, вызвав ***nx_lwm2m_client_session_deregister** _, и попросить клиента отправить сообщение обновления (Update), вызвав _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Обратный вызов состояния сеанса

Приложение регистрирует при создании сеанса обратный вызов, который вызывается при обновлении состояния сеанса. Функция обратного вызова **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** имеет следующий прототип.

typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);

Определены следующие состояния.

| Состояние&nbsp;сеанса | Описание |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | Начальное состояние после создания сеанса. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | Клиент ожидает истечения срока действия таймера задержки (Hold Off) или начальной загрузки, инициированной сервером. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | Клиент отправил сообщение запроса (Request) на сервер начальной загрузки (начальная загрузка, инициированная клиентом). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | Клиент получает данные с сервера начальной загрузки. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | Сервер начальной загрузки отправил сообщение о завершении (Finished). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | Сеанс начальной загрузки завершился сбоем. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | Клиент отправил сообщение Register на сервер LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | Клиент зарегистрировался на сервере LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | Клиент отправил сообщение Update на сервер LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | Клиент отправил сообщение De-register на сервер LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | Регистрация клиента на сервере LWM2M отменена. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | Сервер LWM2M отключен. Когда срок действия таймера отключения истечет, будет отправлено сообщение Register. |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | Операция регистрации или обновления на сервере LWM2M завершилась сбоем. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | Экземпляр объекта сервера, соответствующий серверу LWM2M, удален. |

В случае ошибки приложение может определить ее причину путем вызова ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Управление локальным устройством

Приложение может получить доступ к объектам клиента LWM2M с помощью функций управления локальным устройством. Для этого предоставляются следующие функции.

| Имя&nbsp;функции | Описание |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Чтение ресурсов из экземпляра объекта. |
| ***nx_lwm2m_client_object_discover*** | Получение списка ресурсов экземпляра объекта.
| ***nx_lwm2m_client_object_write*** | Запись ресурсов в экземпляр объекта. |
| ***nx_lwm2m_client_object_execute*** | Осуществление операции выполнения в ресурсе экземпляра объекта. |
| ***nx_lwm2m_client_object_create*** | Создание нового экземпляра объекта. |
| ***nx_lwm2m_client_object_delete*** | Удаление существующего экземпляра объекта. |
| ***nx_lwm2m_client_object_next_get*** | Получение следующего идентификатора объекта клиентом LWM2M. |
| ***nx_lwm2m_client_object_instance_next_get*** | Получение следующего экземпляра объекта. |

## <a name="resource-information"></a>Сведения о ресурсе

Во время операций чтения и записи в объекте ресурс представляется структурой NX_LWM2M_CLIENT_RESOURCE. Эта структура содержит идентификатор ресурса или экземпляра и соответствующее значение.

Для настройки сведений о ресурсе и его значения существуют следующие функции.

| Имя&nbsp;функции | Описание |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Указание сведений о ресурсе: идентификатор ресурса и операция: READ, WRITE, EXECUTABLE. |
| ***nx_lwm2m_client_resource_string_set*** | Указание значения ресурса в качестве строки. |
| ***nx_lwm2m_client_resource_integer32_set*** | Указание значения ресурса в виде 32-разрядного целого числа. |
| ***nx_lwm2m_client_resource_integer64_set*** | Указание значения ресурса в виде 64-разрядного целого числа. |
| ***nx_lwm2m_client_resource_float32_set*** | Указание значения ресурса в виде 32-разрядного числа с плавающей точкой. |
| ***nx_lwm2m_client_resource_float64_set*** | Указание значения ресурса в виде 64-разрядного числа с плавающей точкой. |
| ***nx_lwm2m_client_resource_boolean_set*** | Указание значения ресурса в качестве логического значения. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Указание значения ресурса в качестве ссылки на объект. |
| ***nx_lwm2m_client_resource_opaque_set*** | Указание значения ресурса как непрозрачного. |
| ***nx_lwm2m_client_resource_instance_set*** | Указание значения ресурса как экземпляра для нескольких ресурсов. |
| ***nx_lwm2m_client_resource_dim_set*** | Указание измерения ресурса для нескольких ресурсов для обнаружения. |

Для получения сведений о ресурсе и его значения существуют следующие функции.

| Имя&nbsp;функции | Описание |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Получение сведений о ресурсе: идентификатор ресурса и операция: READ, WRITE, EXECUTABLE. |
| ***nx_lwm2m_client_resource_string_get*** | Получение значения строкового ресурса. |
| ***nx_lwm2m_client_resource_integer32_get*** | Получение значения 32-разрядного целочисленного ресурса. |
| ***nx_lwm2m_client_resource_integer64_get*** | Получение значения 64-разрядного целочисленного ресурса. |
| ***nx_lwm2m_client_resource_float32_get*** | Получение значения 32-разрядного ресурса с плавающей точкой. |
| ***nx_lwm2m_client_resource_float64_get*** | Получение значения 64-разрядного ресурса с плавающей точкой. |
| ***nx_lwm2m_client_resource_boolean_get*** | Получение значения логического ресурса. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Получение значения ресурса в виде ссылки на объект. |
| ***nx_lwm2m_client_resource_opaque_get*** | Получение значения непрозрачного ресурса. |
| ***nx_lwm2m_client_resource_instance_get*** | Получение экземпляра ресурса для нескольких ресурсов. |
| ***nx_lwm2m_client_resource_dim_get*** | Получение измерения ресурса для нескольких ресурсов. |

## <a name="object-implementation"></a>Реализация объектов

Клиент LWM2M реализует обязательные объекты OMA LWM2M: Security (0), Server (1), Access Control (2) и Device (3). Другие объекты для конкретного устройства должны быть реализованы приложением.

Для определения объекта используются две структуры данных: структура NX_LWM2M_CLIENT_OBJECT определяет реализацию объекта, идентификатор объекта и методы объекта, а структура NX_LWM2M_CLIENT_OBJECT_INSTANCE содержит данные экземпляра объекта.

Для этого предоставляются следующие функции.

| Имя&nbsp;функции | Описание |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Добавление реализации объекта в клиент LwM2M. |
| ***nx_lwm2m_client_object_remove*** | Удаление реализации объекта из клиента LwM2M. |
| ***nx_lwm2m_client_object_instance_add*** | Добавление экземпляра объекта в объект. |
| ***nx_lwm2m_client_object_instance_remove*** | Удаление экземпляра объекта из объекта. |

Функция обратного вызова метода объекта имеет сигнатуру, показанную ниже.

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>Метод Read

Метод Read используется для чтения значений ресурсов из экземпляра объекта. Параметры определяются следующим образом.

| Параметр | Описание |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Указатель на реализацию объекта. |
| **instance_ptr** | Указатель на экземпляр объекта. |
| **resource** | Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов. При возврате этот массив заполняется соответствующими типами и значениями. |
| **resource_count** | Указатель на количество считываемых ресурсов. |
| **args_ptr** | Неиспользуемый параметр для чтения. |
| **args_length** | Неиспользуемый параметр для чтения. |

### <a name="the-discover-method"></a>Метод Discover

Метод Discover используется для получения списка всех ресурсов, реализованных объектом. Параметры определяются следующим образом.

| Параметр | Описание |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Указатель на реализацию объекта. |
| **instance_ptr** | Указатель на экземпляр объекта. |
| **resource** | Указатель на массив NX_LWM2M_CLIENT_RESOURCE. При возврате этот массив заполняется соответствующими сведениями о ресурсах. |
| **resource_count** | Указатель на количество обнаруживаемых ресурсов. При возврате этот параметр должен быть обновлен как истинное значение. |
| **args_ptr** | Неиспользуемый параметр для обнаружения. |
| **args_length** | Неиспользуемый параметр для обнаружения. |

### <a name="the-write-method"></a>Метод Write

Метод Write используется для обновления или замены ресурсов экземпляра объекта. Параметры определяются следующим образом.

| Параметр  | Описание |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Указатель на реализацию объекта. |
| **instance_ptr** | Указатель на экземпляр объекта. |
| **resource** | Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов. При возврате этот массив заполняется соответствующими типами и значениями. |
| **resource_count** | Указатель на количество обнаруживаемых ресурсов. |
| **args_ptr** | Флаги для записи. |
| **args_length** | Длина аргументов. |

Для параметра *flag* можно указать следующие операции записи.

| Операция | Действие | Описание |
| --- | ---| --- |
| 0 | Частичное обновление | Добавляет или обновляет ресурсы, указанные в новом значении, и сохраняет остальные существующие ресурсы без изменений.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Замена экземпляра | Заменяет экземпляр объекта новыми указанными значениями ресурсов.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Замена ресурса | Заменяет ресурсы новыми указанными значениями ресурсов (используется для замены нескольких ресурсов). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | создание экземпляра | Инициализирует новый экземпляр объекта с указанными значениями ресурсов (вызывается из метода **_nx_lwm2m_object_create_**). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Запись при начальной загрузке | Вызывается во время начальной загрузки. |

### <a name="the-execute-method"></a>Метод Execute

Метод Execute реализует выполнение ресурса объекта.

Входные параметры определяются следующим образом.

| Параметр  | Описание |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Указатель на реализацию объекта. |
| **instance_ptr** | Указатель на экземпляр объекта. |
| **resource** | Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов. При возврате этот массив заполняется соответствующими типами и значениями. |
| **resource_count** | Указатель на количество обнаруживаемых ресурсов. |
| **args_ptr** | Указатель на аргументы. |
| **args_length** | Длина аргументов.  |

Функция должна возвращать **NX_LWM2M_CLIENT_NOT_FOUND**, если идентификатор ресурса не существует, или **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED**, если он не поддерживает выполнение.

### <a name="the-create-method"></a>Метод Create

Метод Create реализует создание нового экземпляра объекта.

Входные параметры определяются следующим образом.

| Параметр  | Описание |
| --- | --- |
| **operation** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Указатель на реализацию объекта. |
| **instance_ptr** | Неиспользуемый параметр. |
| **resource** | Указатель на массив **NX_LWM2M_CLIENT_RESOURCE**, который содержит идентификаторы считываемых ресурсов. При возврате этот массив заполняется соответствующими типами и значениями. |
| **resource_count** | Указатель на количество обнаруживаемых ресурсов. |
| **args_ptr** | Идентификатор экземпляра объекта. |
| **args_length** | Длина аргументов. |

### <a name="the-delete-method"></a>Метод Delete

Метод Delete реализует удаление экземпляра объекта. Входные параметры определяются следующим образом.

| Параметр  | Описание |
| --- | --- |
| **operation** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Указатель на реализацию объекта. |
| **instance_ptr** | Указатель на экземпляр объекта. |
| **resource** | Неиспользуемый параметр. |
| **resource_count** | Неиспользуемый параметр. |
| **args_ptr** | Неиспользуемый параметр. |
| **args_length** | Неиспользуемый параметр. |

При успешном выполнении объект должен освободить данные экземпляра объекта и любые другие ресурсы, выделенные экземпляром.

## <a name="example-of-lwm2m-client-application"></a>Пример клиентского приложения LWM2M

Следующий код представляет собой пример простого клиентского приложения LWM2M, которое реализует пользовательское устройство, состоящее из датчика температуры и выключателя света.

Это устройство позволяет серверу считывать значение датчика температуры и логическое состояние выключателя света, а также устанавливать этот выключатель в положения "Включено" или "Выключено".

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```