---
title: Глава 4. Описание служб NAT
description: Эта глава содержит описание всех служб API NAT для NetX Duo в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814620"
---
# <a name="chapter-4---description-of-nat-services"></a>Глава 4. Описание служб NAT

Эта глава содержит описание всех служб API NAT для NetX Duo, перечисленных ниже в алфавитном порядке.

> [!NOTE]
> В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

## <a name="nx_nat_create"></a>nx_nat_create

Создание сервера NAT

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр сервера NAT.

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на создаваемый экземпляр NAT.
- **ip_ptr** — указатель на экземпляр IP-адреса.
- **global_interface_index** — индекс глобального сетевого интерфейса.
- **dynamic_cache_memory** — указатель на зону памяти для таблицы NAT.
- **dynamic_cache_size** — размер зоны памяти для таблицы NAT.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сервер NAT успешно создан.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.
- NX_NAT_PARAM_ERROR (0xD01) — недопустимые входные данные (без указателя).
- NX_NAT_CACHE_ERROR (0xD02) — недопустимые входные данные указателя на кэш.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

Удаление сервера NAT

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее сервер NAT.

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на удаляемый экземпляр NAT.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** — (0x00) экземпляр NAT успешно удален.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

Включение NAT для экземпляра IP

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Описание

Эта служба включает NAT для экземпляра IP (для отправки пакетов на сервер NAT).

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на экземпляр NAT.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр NAT успешно включен.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

Отключение NAT для экземпляра IP

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает NAT для экземпляра IP.

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на экземпляр NAT.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр NAT успешно отключен.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

Настройка функции обратного вызова для информирования о заполнении кэша

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>Описание

Эта служба регистрирует обратный вызов для информирования о заполнении кэша, принимая в качестве входных данных указатель на определяемую пользователем функцию cache_full_notify_cb, используемую для информирования о заполнении кэша.

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на экземпляр NAT.
- **cache_full_notify_cb** — указатель на функцию для информирования о заполнении кэша.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — информирование о заполнении кэша успешно настроено.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.
- NX_NAT_PARAM_ERROR (0xD01) — недопустимые входные данные (без указателя).

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

Создание входящей записи в таблице преобразования NAT

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>Описание

Эта служба создает статическую входную запись (постоянную с неограниченным сроком действия) и добавляет ее в таблицу преобразования NAT. Такие записи обычно создаются для серверов локальных узлов, где подключение инициируется от узла во внешней сети. Сервер NAT проверяет, что указанный внешний порт еще не используется в таблице трансляции и не привязан к существующему сокету NetX Duo этого же протокола.

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на экземпляр NAT.
- **entry_ptr** — указатель на запись преобразования.
- **local_ip_address** — IP-адрес локального узла.
- **external_port** — порт назначения во внешней сети.
- **local_port** — порт источника (локального узла).
- **protocol** — протокол пакетов (например, TCP).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись успешно создана.
- **NX_NAT_PORT_UNAVAILABLE** (0xD0D) — недопустимый внешний порт.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.
- NX_NAT_PARAM_ERROR (0xD01) — недопустимые входные данные (без указателя).

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

Удаление входящей записи в таблице преобразования NAT

### <a name="prototype"></a>Прототип

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>Описание

Эта служба удаляет указанную входящую запись из таблицы преобразования.

### <a name="input-parameters"></a>Входные параметры

- **nat_ptr** — указатель на экземпляр NAT.
- **delete_entry_ptr** — указатель на запись преобразования NAT.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись успешно удалена.
- **NX_NAT_ENTRY_NOT_FOUND** (0xD04) — запись не найдена.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.
- NX_NAT_ENTRY_TYPE_ERROR (0xD0C) — недопустимый тип преобразования.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Пример

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
