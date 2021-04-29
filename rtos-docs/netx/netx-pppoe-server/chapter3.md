---
title: Глава 3. Описание служб сервера PPPoE для ОСРВ Azure
description: В этой главе описываются все службы сервера NetX PPPoE для ОСРВ Azure (перечислены ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815120"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a>Глава 3. Описание служб сервера PPPoE для ОСРВ Azure

В этой главе описываются все службы сервера NetX PPPoE для ОСРВ Azure (перечислены ниже) в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_pppoe_server_create**: *создание экземпляра сервера PPPoE*

- **nx_pppoe_server_ac_name_set**: *задание имени концентратора доступа*

- **nx_pppoe_server_delete**: *удаление экземпляра сервера PPPoE*

- **nx_pppoe_server_enable**: *включение служб сервера PPPoE*

- **nx_pppoe_server_disable**: *отключение служб сервера PPPoE*

- **nx_pppoe_server_callback_notify_set**: *настройка функций уведомления об обратном вызове сервера PPPoE*

- **nx_pppoe_server_service_name_set**: *настройка имени службы сервера PPPoE*

- **nx_pppoe_server_session_send**: *отправка данных сервера PPPoE в указанный сеанс*

- **nx_pppoe_server_session_packet_send**: *отправка пакета сервера PPPoE в указанный сеанс*

- **nx_pppoe_server_session_terminate**: *завершение указанного сеанса PPPoE*

- **nx_pppoe_server_session_get**: *получение сведений об указанных сеансах*

## <a name="nx_pppoe_server_create"></a>nx_pppoe_server_create

Создание экземпляра сервера PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр сервера PPPoE с драйвером ссылки, предоставленным пользователем для указанного экземпляра NetX IP. Если драйвер ссылки не был инициализирован и включен, программное обеспечение сервера PPPoE выполняет инициализацию драйвера ссылки.

Кроме того, приложение должно предоставить созданный ранее пул пакетов для экземпляра сервера PPPoE, который будет использоваться для внутреннего распределения пакетов.

Обратите внимание, что поток NetX IP следует создать с более высоким приоритетом, чем приоритет потока сервера PPPoE. Дополнительные сведения об указании приоритета потока IP см. в службе *nx_ip_create*.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **name**: имя этого экземпляра сервера PPPoE
- **ip_ptr**: указатель на блок управления для экземпляра IP
- **interface_index**: индекс интерфейса
- **pppoe_link_driver**: драйвер ссылки, предоставленный пользователем
- **pool_ptr**: указатель на пул пакетов
- **stack_ptr**: указатель на начало области стека потока сервера PPPoE
- **stack_size**: размер в байтах в стеке потока
- **priority**: приоритет внутренних потоков сервера PPPoE (1–31)

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное создание сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый сервер PPPoE, IP, пул пакетов или указатель стека.
- NX_PPPOE_SERVER_INVALID_INTERFACE (0xC2) — недопустимый интерфейс.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR (0xC3) — недопустимый размер полезных данных пула пакетов.
- NX_PPPOE_SERVER_MEMORY_SIZE_ERROR (0xC4) — недопустимый размер памяти.
- NX_PPPOE_SERVER_PRIORITY_ERROR (0xC5) — недопустимый приоритет потока сервера PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a>nx_pppoe_server_delete

Удаление экземпляра сервера PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр сервера PPPoE.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a>nx_pppoe_server_enable

Включение службы сервера PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Описание

Эта служба включает службы сервера PPPoE.

> [!NOTE]
> Эта функция должна вызываться после *nx_pppoe_server_create* и *nx_pppoe_server_callback_notify_set*.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a>nx_pppoe_server_disable

Отключение службы сервера PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает службы сервера PPPoE.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a>nx_pppoe_server_callback_notify_set

Настройка функций уведомления об обратном вызове сервера PPPoE 

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a>Описание

Эта служба задает функции уведомления об обратном вызове сервера PPPoE.

> [!NOTE]
> Эта функция должна вызываться до *nx_pppoe_server_enabl*, а также должен быть установлен указатель на функцию pppoe_data_receive_notify, в противном случае *nx_pppoe_server_enable* завершится сбоем.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **pppoe_discover_initiation_notify**: функция приложения, которая вызывается при получении сообщения об инициации обнаружения PPPoE. Если это значение равно NULL, функция обратного вызова инициации обнаружения отключена.
- **pppoe_discover_request_notify**: функция приложения, которая вызывается при получении сообщения запроса на обнаружение PPPoE. Если это значение равно NULL, функция обратного вызова запроса обнаружения отключена.
- **pppoe_discover_terminate_notify**: функция приложения, которая вызывается при получении сообщения о прекращении обнаружения PPPoE. Если это значение равно NULL, функция обратного вызова для завершения обнаружения отключена.
- **pppoe_discover_terminate_confirm**: функция приложения, которая вызывается при отправке сообщения о прекращении обнаружения PPPoE. Если это значение равно NULL, функция обратного вызова для завершения обнаружения отключена.
- **pppoe_data_receive_notify**: функция приложения, которая вызывается при получении сообщения с данными PPPoE. Это значение должно быть равно нулю.
- **pppoe_data_send_notify**: функция приложения, которая вызывается при отправке сообщения с данными PPPoE. Если это значение равно NULL, функция обратного вызова для отправки данных отключена.

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE или указатель функции.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a>nx_pppoe_server_ac_name_set

Задание имени концентратора доступа

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a>Описание

Эта функция задает вызов функции имени концентратора доступа.

> [!NOTE]
> В конце строки ac_name должно быть указано NULL, а длина ac_name соответствует длине, указанной в списке аргументов.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **ac_name**: имя концентратора доступа
- **ac_name_length**: длина параметра ac_ame

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — сервер PPPoE успешно задан.
- **NX_PPPOE_SERVER_PTR_ERROR** (0xC1) — недопустимый сервер PPPoE, IP, пул пакетов или указатель стека.
- **NX_SIZE_ERROR** (0x09) — сбой проверки name_length.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a>nx_pppoe_server_service_name_set

Задание имени службы сервера PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a>Описание

Эта служба задает имя службы сервера PPPoE.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a>nx_pppoe_server_session_send

Отправка данных сервера PPPoE в указанный сеанс

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a>Описание

Эта служба отправляет кадр PPPoE, используя указанный идентификатор сеанса.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **session_index**: индекс сеанса
- **data_ptr**: указатель на начало кадра данных сервера PPPoE
- **data_length**: длина кадра данных сервера PPPoE

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED (0xC6) — служба сервера PPPoE не включена.
- NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a>nx_pppoe_server_session_packet_send

Отправка пакета сервера PPPoE в указанный сеанс

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет пакет PPPoE, используя указанный идентификатор сеанса.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **session_index**: индекс сеанса
- **packet_ptr**: указатель на пакет PPPoE

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.
- NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR (0xC3) — недопустимый пакет сервера PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED (0xC6) — служба сервера PPPoE не включена.
- NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a>nx_pppoe_server_session_terminate

Завершение указанного сеанса PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a>Описание

Эта служба завершает указанный сеанс PPPoE.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **session_index**: индекс сеанса

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.
- NX_PPPOE_SERVER_NOT_ENABLED (0xC6) — служба сервера PPPoE не включена.
- NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a>nx_pppoe_server_session_get

Получение сведений об указанном сеансе PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном сеансе PPPoE, физическом адресе клиента и идентификаторе сеанса.

### <a name="input-parameters"></a>Входные параметры

- **pppoe_server_ptr**: указатель на блок управления сервера PPPoE
- **session_index**: индекс сеанса
- **client_mac_msw**: указатель MSW на физический адрес клиента.
- **client_mac_lsw**: указатель MSW на физический адрес клиента.
- **session_id**: указатель идентификатора сеанса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.
- NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.
- NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.
- NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a>PppInitInd

Настройка имени службы по умолчанию

### <a name="prototype"></a>Прототип

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP настройку имени службы по умолчанию, которое PPPoE будет использовать для фильтрации входящих запросов PADI. Программное обеспечение PPPoE должно запомнить эти сведения, и, если получен пакет PADI, содержащий имя службы, которое соответствует, оно должно вызывать PppDiscoverReq.

### <a name="input-parameters"></a>Входные параметры

- **length**: длина имени службы по умолчанию.
- **aData**: имя службы по умолчанию.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a>PppDiscoverCnf

Определение поля имени службы пакета PADO

### <a name="prototype"></a>Прототип

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP определять поле имени службы пакета PADO. Программное обеспечение PPPoE не должно отправлять PADO до вызова PppDiscoverCnf.

Пакет PADO должен содержать имя концентратора доступа (с использованием идентификатора тега 0x0102, как определено в RFC2516), определенного для инициализации программного обеспечения PPPoE.

В aData можно передать несколько имен служб, при этом в конце каждого имени должно быть указано NULL.

Символ NULL используется в качестве разделителя для обеспечения максимальной гибкости в случае, если другие команды необходимо передать в качестве части имени службы.

### <a name="input-parameters"></a>Входные параметры

- **length**: длина имени службы по умолчанию.
- **aData**: имя службы по умолчанию.
- **interfaceHandle**: дескриптор интерфейса.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a>PppOpenCnf

Принятие или отклонение сеанса PPPoE

### <a name="prototype"></a>Прототип

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP принимать или отклонять сеансы PPPoE.  В ответ стек PPPoE должен принять подключение и назначить уникальный номер Session_ID PPPoE, связанный с interfaceHandle.

### <a name="input-parameters"></a>Входные параметры

- **accept**: NX_TRUE, если подключение должно быть принято.
- **interfaceHandle**: дескриптор интерфейса.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a>PppCloseInd

Закрытие сеанса PPPoE

### <a name="prototype"></a>Прототип

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP закрыть сеанс PPPoE.

Программное обеспечение PPPoE укажет строку кода причины в теге Generic-Error (0x0203) в сообщении PADT.

### <a name="input-parameters"></a>Входные параметры

- **interfaceHandle**: дескриптор интерфейса.
- **causeCode**: строка, заканчивающаяся NULL, для отправки сведений о причине закрытия соединения с сервером PPPoE.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a>PppCloseCnf

Подтверждение того, что дескриптор освобожден

### <a name="prototype"></a>Прототип

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP подтверждение того, что этот дескриптор был освобожден.

### <a name="input-parameters"></a>Входные параметры

- **interfaceHandle**: дескриптор интерфейса.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a>PppTransmitDataCnf

Разрешение подтверждения предыдущих данных PPP

### <a name="prototype"></a>Прототип

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить подтверждение предыдущего PppTransmitDataReq.  Это означает, что программное обеспечение TTP готово к созданию нового кадра PPP из PPPoE.

### <a name="input-parameters"></a>Входные параметры

- **interfaceHandle**: дескриптор интерфейса.
- **aData**: указатель принятия буфера данных PPP.
- **Packet_id**: идентификатор пакета.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a>PppReceiveDataInd

Получение данных из передачи по Ethernet

### <a name="prototype"></a>Прототип

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a>Описание

Программное обеспечение PPPoE предоставит эту функцию для получения данных для передачи по Ethernet.

### <a name="input-parameters"></a>Входные параметры

- **interfaceHandle**: дескриптор интерфейса.
- **length**: число байтов в aData.
- **aData**: буфер данных, содержащий кадр данных PPP.

### <a name="return-values"></a>Возвращаемые значения

**Нет**

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```