---
title: Глава 3. Описание служб клиента PPPoE для NetX (ОСРВ Azure)
description: В этой главе описываются все службы клиента PPPoE для NetX (ОСРВ Azure), которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8310006b7c188fa63402c931459ffd84ebb776c207dc520959208449862fe27f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790213"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a>Глава 3. Описание служб клиента PPPoE для NetX (ОСРВ Azure)

В этой главе описываются все службы клиента PPPoE для NetX (ОСРВ Azure), которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" приведенных ниже описаний API **выделенные полужирным шрифтом** значения не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_pppoe_client_create** — *создание экземпляра клиента PPPoE*.
- **nx_pppoe_client_delete** — *удаление экземпляра клиента PPPoE*.
- **nx_pppoe_client_host_uniq_set** — *настройка значения Host-Uniq для клиента PPPoE*.
- **nx_pppoe_client_host_uniq_set_extended** *Настройка значения Host-Uniq для клиента PPPoE*.
- **nx_pppoe_client_service_name_set** — *настройка имени службы для клиента PPPoE*
- **nx_pppoe_client_service_name_set_extended** — *настройка имени службы для клиента PPPoE*.
- **nx_pppoe_client_session_connect** — *подключение сеанса клиента PPPoE к серверу PPPoE*.
- **nx_pppoe_client_session_packet_send** — *отправка пакета в сеанс PPPoE*.
- **nx_pppoe_client_session_terminate** — *завершение сеанса PPPoE*.
- **nx_pppoe_client_session_get** — *получение сведений об указанном сеансе PPPoE*.

## <a name="nx_pppoe_client_create"></a>nx_pppoe_client_create

Создание экземпляра клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента PPPoE с драйвером канала, предоставленным пользователем для указанного экземпляра NetX IP. Если драйвер канала не был инициализирован и включен, программное обеспечение клиента PPPoE выполняет инициализацию драйвера канала.

Кроме того, приложение должно предоставить созданный ранее пул пакетов для экземпляра клиента PPPoE, который будет использоваться для внутреннего распределения пакетов.

> [!NOTE]
> Обычно считается, что поток NetX IP следует создавать с более высоким приоритетом, чем у потока клиента PPPoE. Дополнительные сведения об указании приоритета для потока IP см. в описании службы *nx_ip_create*.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **name** — имя текущего экземпляра клиента PPPoE.
 - **ip_ptr** — указатель на блок управления для экземпляра IP.
 - **interface_index** — индекс интерфейса.
 - **pool_ptr** — указатель на пул пакетов.
 - **stack_ptr** — указатель на начало области стека потока клиента PPPoE.
 - **stack_size** — размер в байтах в стеке потока.
 - **priority** — приоритет внутренних потоков клиента PPPoE (1–31).
 - **pppoe_link_driver** — драйвер канала, предоставленный пользователем.
 - **pppoe_packet_receive** — предоставленная пользователем функция приема пакетов.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — клиент PPPoE успешно создан.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый клиент PPPoE, IP, пул пакетов или указатель стека.
 - NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) — недопустимый интерфейс.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) — недопустимый объем полезных данных пула пакетов.
 - NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) — недопустимый объем памяти.
 - NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) — недопустимый приоритет потока клиента PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a>nx_pppoe_client_delete

Удаление экземпляра клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр клиента PPPoE.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — клиент PPPoE успешно удален.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a>nx_pppoe_client_host_uniq_set

Настройка значения Host-Uniq для клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a>Описание

Эта служба задает значение Host-Uniq для клиента PPPoE. Host-Uniq используется узлом для уникальной привязки концентратора доступа к определенному запросу узла.
Это могут быть двоичные данные с любыми значениями и любой длины, которые выбирает узел.

> [!NOTE]
> Значение Host-Uniq должно быть строковым и заканчиваться нулем.

> [!NOTE]
> использовать эту службу больше не рекомендуется. Мы рекомендуем разработчикам перейти на использование *nx_pppoe_client_host_uniq_set_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **host_uniq** — указатель на значение Host-Uniq. Значение Host-Uniq должно быть строковым и заканчиваться нулем.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — значение Host-Uniq для клиента PPPoE успешно установлено.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a>nx_pppoe_client_host_uniq_set_extended

Настройка значения Host-Uniq для клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a>Описание

Эта служба задает значение Host-Uniq для клиента PPPoE. Host-Uniq используется узлом для уникальной привязки концентратора доступа к определенному запросу узла.
Это могут быть двоичные данные с любыми значениями и любой длины, которые выбирает узел.

> [!NOTE]
> Значение Host-Uniq должно быть строковым и заканчиваться нулем.

> [!NOTE]
> Эта служба заменяет устаревшую *nx_pppoe_client_host_uniq_set()* . Эта версия предоставляет службе дополнительные сведения о длине.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **host_uniq** — указатель на значение Host-Uniq. Значение Host-Uniq должно быть строковым и заканчиваться нулем.
 - **host_uniq_length** — длина значения Host-Uniq

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — значение Host-Uniq для клиента PPPoE успешно установлено.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) — недопустимый указатель на клиент PPPoE.
 - **NX_SIZE_ERROR** (0x09) — проверка host_uniq_length не прошла.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a>nx_pppoe_client_service_name_set

Настройка имени службы клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a>Описание

Эта служба задает имя службы клиента PPPoE. Значение Service-Name обозначает службу, которую запрашивает узел. Если значение Service-Name не задано, узел примет любое количество служб.

> [!NOTE]
> Имя службы должно быть строковым и заканчиваться нулем.

> [!NOTE]
> использовать эту службу больше не рекомендуется. Мы рекомендуем разработчикам перейти на использование *nx_pppoe_client_service_name_set_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **service_name** — указатель на имя службы. Имя службы должно быть строковым и заканчиваться нулем.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — имя службы для клиента PPPoE успешно задано.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) — недопустимый указатель на клиент PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a>nx_pppoe_client_service_name_set_extended

Настройка имени службы клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a>Описание

Эта служба задает имя службы клиента PPPoE. Значение Service-Name обозначает службу, которую запрашивает узел. Если значение Service-Name не задано, узел примет любое количество служб.

> [!NOTE]
> Имя службы должно быть строковым и завершаться заканчиваться нулем.

> [!NOTE]
> Эта служба заменяет *nx_pppoe_client_service_name_set()* . Эта версия предоставляет функции дополнительные сведения о длине имени службы.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **service_name** — указатель на имя службы. Имя службы должно быть строковым и заканчиваться нулем.
 - **service_name_length** — длина имени службы.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — имя службы для клиента PPPoE успешно задано.
 - **NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) — недопустимый указатель на клиент PPPoE.
 - **NX_SIZE_ERROR** (0x09) — проверка service_name_length не пройдена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a>nx_pppoe_client_session_connect

Подключение к сеансу клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба создает подключение сеанса PPPoE к указанному серверу PPPoE с помощью ранее созданного клиента PPPoE.

> [!NOTE]
> Эта функция должна вызываться после *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* и *nx_pppoe_client_service_name_set*.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **wait_option** — параметр ожидания до установления соединения

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — сеанс клиента PPPoE успешно подключен.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a>nx_pppoe_client_session_packet_send

Отправка пакета клиента PPPoE в указанный сеанс

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет пакет PPPoE, используя указанный идентификатор сеанса.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.
 - **packet_ptr** — указатель на пакет PPPoE.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — пакет клиента PPPoE успешно отправлен.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.
 - NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) — недопустимый пакет клиента PPPoE.
 - NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xD8) — сеанс PPPoE не установлен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a>nx_pppoe_client_session_terminate

Завершение сеанса клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a>Описание

Эта служба завершает указанный сеанс PPPoE.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — сеанс клиента PPPoE успешно завершен.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a>nx_pppoe_client_session_connect

Получение сведений об указанном сеансе PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном сеансе PPPoE, физическом адресе сервера и идентификаторе сеанса.

### <a name="input-parameters"></a>Входные параметры

 - **pppoe_server_ptr** — указатель на блок управления для клиента PPPoE.
 - **server_mac_msw** — указатель MSW на физический адрес сервера.
 - **server_mac_lsw** — указатель LSW на физический адрес сервера.
 - **session_id**: указатель на идентификатор сеанса.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_PPPOE_CLIENT_SUCCESS** (0x00) — сеанс клиента PPPoE успешно получен.
 - NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.
 - NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xD8) — сеанс PPPoE не установлен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
