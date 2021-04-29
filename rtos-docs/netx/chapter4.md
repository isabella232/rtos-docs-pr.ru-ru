---
title: Глава 4. Описание служб NetX для ОСРВ Azure
description: В этой главе содержится описание всех служб NetX для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814480"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Глава 4. Описание служб NetX для ОСРВ Azure

В этой главе содержится описание всех служб NetX для ОСРВ Azure в алфавитном порядке. Имена служб реализованы так, что все аналогичные службы группируются вместе. Например, все службы ARP указаны в начале этой главы.

> [!NOTE]
> *Обратите внимание, что сокет API, совместимый с BSD, доступен для устаревшего кода приложения, который не может использовать все преимущества высокопроизводительного API NetX. Дополнительные сведения о сокете API, совместимом с BSD, см. в приложении D*.

В разделе "Возвращаемые значения" каждого описания значения, **выделенные полужирным шрифтом**, не затрагиваются параметром NX_DISABLE_ERROR_CHECKING, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены. В разделах "Разрешено из" указывается, откуда можно вызывать каждую службу NetX.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Делает недействительными все динамические записи в кэше ARP.

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба делает недействительными все динамические записи ARP, находящиеся в кэше ARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — недействительность кэша ARP.
- **NX_NOT_ENABLED** (0x14) — ARP не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

Задание динамической записи ARP

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Описание

Эта служба выделяет динамическую запись из кэша ARP и устанавливает сопоставление указанного IP-адреса с физическим адресом. Если указан нулевой физический адрес, в сеть отправляется фактический запрос ARP, чтобы разрешить физический адрес. Также обратите внимание, что эта запись будет удалена, если активно устаревание по протоколу ARP или если кэш ARP исчерпан, а это наименее недавно использованная запись ARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: IP-адрес для сопоставления
- **physical_msw**: старшие 16 бит (47–32) физического адреса.
- **physical_msw**: младшие 32 бит (31–0) физического адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешный динамический набор записей ARP.
- **NX_NO_MORE_ENTRIES** (0x17) — в кэше ARP больше нет доступных записей ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на экземпляр IP.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_enable,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Включает протокол определения адреса (ARP).

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Описание

Эта служба инициализирует компонент ARP определенного экземпляра IP в NetX. Инициализация ARP включает в себя настройку кэша ARP и различные процедуры обработки ARP, необходимые для отправки и получения сообщений ARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **arp_cache_memory**: указатель на область памяти для размещения кэша ARP
- **arp_cache_size**: каждая запись в ARP состоит из 52 байт, а общее количество записей ARP равно размеру, деленному на 52.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение ARP.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель кэш-памяти.
- **NX_SIZE_ERROR** (0x09) — размер кэша ARP, указанный пользователем, слишком мал.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_ALREADY_ENABLED** (0x15) — этот компонент уже включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Отправка необязательного запроса ARP

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Описание

Эта служба использует все физические интерфейсы для передачи невыполненных запросов ARP, если IP-адрес интерфейса является допустимым. При последующем получении ответа ARP вызывается обработчик ответов для обработки ответа на необязательный ARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **response_handler**: указатель функции обработки ответа Если указано значение NX_NULL, ответы игнорируются.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная отправка необязательного запроса ARP.
- **NX_NO_PACKET** (0x01) — нет доступных пакетов.
- **NX_NOT_ENABLED** (0x14) — ARP не включен.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый текущий IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Обнаружение физического аппаратного адреса по IP-адресу

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Описание

Эта служба пытается найти физический адрес оборудования в кэше ARP, связанном с заданным IP-адресом.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: IP-адрес для поиска
- **physical_msw**: указатель переменной для возврата старших 16 бит (47–32) физического адреса
- **physical_lsw**: указатель переменной для возврата младших 32 бит (31–0) физического адреса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешный поиск адреса оборудования ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) — сопоставление не найдено в кэше ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель памяти.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

Получение сведений о действиях ARP

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях ARP для соответствующего экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **arp_requests_sent**: указатель места назначения для общего числа запросов ARP, отправленных из этого экземпляра IP
- **arp_requests_received**: указатель места назначения для общего числа запросов ARP, полученных от сети
- **arp_responses_sent**: указатель места назначения для общего числа ответов ARP, отправленных из этого экземпляра IP
- **arp_responses_received**: указатель места назначения для общего числа ответов ARP, полученных от сети
- **arp_dynamic_entries**: указатель места назначения для текущего числа динамических записей ARP
- **arp_static_entries**: указатель места назначения для текущего числа статических записей ARP
- **arp_aged_entries**: указатель места назначения общего числа записей ARP, которые устарели и стали недопустимыми
- **arp_invalid_messages**: указатель места назначения общего числа полученных недопустимых сообщений ARP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений ARP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_ip_address_find,
- nx_arp_static_entries_delete, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

Нахождение IP-адреса по физическому адресу

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a>Описание

Эта служба пытается найти IP-адрес в кэше ARP, связанном с переданным физическим адресом.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: указатель для возврата IP-адреса, если он найден и сопоставлен
- **physical_msw**: старшие 16 бит (47–32) физического адреса для поиска
- **physical_lsw**: младшие 32 бит (31–0) физического адреса для поиска

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешный поиск IP-адреса ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) — сопоставление не найдено в кэше ARP.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель памяти.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_INVALID_PARAMETERS** (0x4D) — значения physical_msw и physical_lsw равны 0.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_static_entries_delete,nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

Удаление всех статических записей ARP

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет все статические записи в кэше ARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — статические записи удалены.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ip_ptr.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

Создание статического IP-адреса для аппаратного сопоставления в кэше ARP

### <a name="prototype"></a>Прототип

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Описание

Эта служба создает сопоставление статического IP-адреса с физическим в кэше ARP для указанного экземпляра IP. На статические записи ARP не распространяются периодические обновления протокола ARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: IP-адрес для сопоставления
- **physical_msw**: старшие 16 бит (47–32) физического адреса для сопоставления
- **physical_lsw**: младшие 32 бит (31–0) физического адреса для сопоставления

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное создание статической записи ARP.
- **NX_NO_MORE_ENTRIES** (0x17) — в кэше ARP больше нет доступных записей ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_INVALID_PARAMETERS** (0x4D) — значения physical_msw и physical_lsw равны 0.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

Удаление статического IP-адреса для сопоставления оборудования в кэше ARP


### <a name="prototype"></a>Прототип

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Описание

Эта служба находит и удаляет ранее созданное статическое сопоставление IP-адреса с физическим адресом в кэше ARP для указанного экземпляра IP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address** IP-адрес, который был сопоставлен статически
- **physical_msw**: старшие 16 бит (47–32) физического адреса, который был сопоставлен статически
- **physical_lsw**: младшие 32 бит (31–0) физического адреса, который был сопоставлен статически

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное удаление статической записи ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) — статическая запись ARP не найдена в кэше ARP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_INVALID_PARAMETERS** (0x4D) — значения physical_msw и physical_lsw равны 0.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

Включение протокола ICMP

### <a name="prototype"></a>Прототип

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает компонент ICMP для указанного экземпляра IP.
Компонент ICMP отвечает за обработку сообщений об ошибках в Интернете, а также запросов и ответов проверки связи.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение протокола ICMP.
- **NX_ALREADY_ENABLED** (0x15) — протокол ICMP уже включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>См. также:

- nx_icmp_info_get, nx_icmp_ping

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get

Получение сведений о действиях ICMP

### <a name="prototype"></a>Прототип

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола ICMP для указанного экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **pings_sent**: указатель места назначения для общего числа отправленных проверок связи.
- **ping_timeouts**: указатель места назначения для общего числа таймаутов проверки связи.
- **ping_threads_suspended**: указатель места назначения общего числа потоков, приостановленных по запросам проверки связи.
- **ping_responses_received**: указатель места назначения общего числа полученных ответов проверки связи.
- **icmp_checksum_errors**: указатель места назначения общего числа ошибок контрольной суммы протокола ICMP.
- **icmp_unhandled_messages**: указатель места назначения общего числа необработанных сообщений ICMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений ICMP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_icmp_enable, nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

Отправка запроса проверки связи на указанный IP-адрес

### <a name="prototype"></a>Прототип

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос проверки связи по указанному IP-адресу и ожидает сообщение ответа проверки связи в течение заданного количества времени. Если ответ не получен, возвращается ошибка. В противном случае в переменной, на которую указывает response_ptr, возвращается полное ответное сообщение.

*Если возвращается NX_SUCCESS, приложение отвечает за освобождение полученного пакета после того, как он больше не нужен*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: IP-адрес в порядке байтов узла для проверки связи data: указатель области данных для сообщения проверки связи
- **data_size**: число байтов в данных проверки связи
- **response_ptr**: указатель на указатель пакета, в котором нужно вернуть ответное сообщение проверки связи
- **wait_option** определяет время ожидания ответа проверки связи Параметры ожидания определяются следующим образом.

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная проверка связи. Указатель сообщения ответа был помещен в переменную, на которую указывает response_ptr.
- **NX_NO_PACKET** (0x01) — не удалось выделить пакет запроса проверки связи.
- **NX_OVERFLOW** (0x03) — заданная область данных превышает размер пакета по умолчанию для этого экземпляра IP-адреса.
- **NX_NO_RESPONSE** (0x29) — запрошенный IP-адрес не ответил.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель ответа.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a>См. также:

- nx_icmp_enable, nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

Включение протокола IGMP

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает компонент IGMP для указанного экземпляра IP.
Компонент IGMP отвечает за поддержку операций управления группами многоадресной рассылки IP-адресов.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение протокола IGMP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_ALREADY_ENABLED** (0x15) — этот компонент уже включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get

Получение сведений о действиях IGMP

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола IGMP для указанного экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **igmp_reports_sent**: указатель места назначения для общего числа отправленных отчетов ICMP
- **igmp_queries_received**:указатель места назначения для общего числа запросов, полученных маршрутизатором многоадресной рассылки
- **igmp_checksum_errors**: указатель места назначения общего числа ошибок контрольной суммы IGMP для полученных пакетов
- **current_groups_joined**: указатель места назначения текущего числа групп, соединяемых через этот экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений IGMP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_enable, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

Отключение петлевого адреса IGMP

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает петлевой адрес IGMP для всех последующих присоединенных групп многоадресной рассылки.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное отключение петлевого адреса IGMP.
- **NX_NOT_ENABLED** (0x14) — протокол IGMP не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Включение петлевого адреса IGMP

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает петлевой адрес IGMP для всех последующих присоединенных групп многоадресной рассылки.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное отключение петлевого адреса IGMP.
- **NX_NOT_ENABLED** (0x14) — протокол IGMP не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Присоединение экземпляра IP к указанной группе многоадресной рассылки через интерфейс

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба присоединяет экземпляр IP к указанной группе многоадресной рассылки через указанный сетевой интерфейс. Внутренний счетчик поддерживается для наблюдения за тем, сколько раз была присоединена одна и та же группа. После присоединения к группе многоадресной рассылки компонент IGMP разрешит получение IP-пакетов с этим адресом группы через указанный сетевой интерфейс, а также сообщает маршрутизаторам, что этот IP-адрес является участником этой группы рассылки. Сообщения об участии в IGMP, отчетах и выходе также отправляются через указанный сетевой интерфейс.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **group_address**: адрес группы многоадресной рассылки IP-адресов класса D для присоединение в порядке байтов узла
- **interface_index**: индекс интерфейса, присоединенного к экземпляру NetX

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.
- **NX_NO_MORE_ENTRIES** (0x17) — дополнительные группы многоадресной рассылки не могут быть присоединены (превышено максимальное значение).
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — указанный адрес группы многоадресной рассылки не является допустимым адресом класса D.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — поддержка многоадресной рассылки IP не включена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Присоединение экземпляра IP к указанной группе многоадресной рассылки

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Описание

Эта служба присоединяет экземпляр IP-адреса к указанной группе многоадресной рассылки. Внутренний счетчик поддерживается для наблюдения за тем, сколько раз была присоединена одна и та же группа. Драйвер получает команду отправить отчет IGMP, если это первый запрос на присоединение в сети, указывающий на намерение узла присоединиться к группе. После присоединения компонент IGMP разрешит прием IP-пакетов с этим адресом группы и сообщит маршрутизаторам, что этот IP-адрес является членом этой группы многоадресной рассылки.

> [!NOTE]
> *Чтобы присоединить группу многоадресной рассылки на неосновном устройстве, используйте службу **nx_igmp_multicast_interface_join***.

- **Параметры**

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **group_address**: адрес группы многоадресной рассылки IP-адресов класса D для присоединения

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.
- **NX_NO_MORE_ENTRIES** (0x17) — дополнительные группы многоадресной рассылки не могут быть присоединены (превышено максимальное значение).
- **NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый адрес группы IP-адресов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Экземпляр IP покидает указанную группу многоадресной рассылки

### <a name="prototype"></a>Прототип

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Описание

Эта служба приводит к тому, что экземпляр IP покидает указанную группу многоадресной рассылки, если число запросов на выход соответствует числу запросов на присоединение. В противном случае число внутренних присоединений просто уменьшается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **group_address**: группа многоадресной рассылки для выхода

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.
- **NX_ENTRY_NOT_FOUND** (0x16) — предыдущий запрос на присоединение не найден.
- **NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый адрес группы IP-адресов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Уведомление приложения при изменении IP-адреса


### <a name="prototype"></a>Прототип

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию уведомления приложения, которая вызывается при каждом изменении IP-адреса.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **change_notify**: указатель функции уведомления об изменении IP-адреса. Если этот параметр имеет значение NX_NULL, уведомление об изменении IP-адреса отключается.
- **additional_info**: указатель необязательных дополнительных сведений, который также предоставляется функции уведомления при изменении IP-адреса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — уведомление об изменении IP-адреса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,
- nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

Получение IP-адреса и маски сети

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Описание

Эта служба извлекает IP-адрес и маску подсети основного сетевого интерфейса.

* Чтобы получить сведения о вторичном устройстве, используйте службу
- **nx_ip_interface_address_get**.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: указатель назначения IP-адреса
- **network_mask**: указатель места назначения для маски сети

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение IP-адреса.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемой переменной.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

Получение IP-адреса и маски сети

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес и маску сети для основного сетевого интерфейса.

*Чтобы задать IP-адрес и маску сети для вторичного устройства, используйте службу **nx_ip_interface_address_set**.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: новый IP-адрес
- **network_mask**: новая маска сети

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешный набор IP-адресов.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_create"></a>nx_ip_create

Создание экземпляра IP

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр IP с пользовательским IP-адресом и сетевым драйвером. Кроме того, приложение должно предоставить созданный ранее пул пакетов для экземпляра клиента PPPoE, который будет использоваться для внутреннего распределения пакетов. Обратите внимание, что указанный сетевой драйвер приложения не вызывается до тех пор, пока не будет выполнен поток этого IP-адреса.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на блок управления для создания экземпляра IP
- **name**: имя нового экземпляра IP
- **ip_address**: IP-адрес для этого нового экземпляра IP
- **network_mask**: маска для отделения сетевой части IP-адреса для подсетей и суперсетей
- **default_pool**: указатель на управляющий блок ранее созданного пула пакетов NetX
- **ip_network_driver**: предоставленный пользователем драйвер сети, используемый для отправки и получения IP-пакетов
- **memory_ptr**: указатель на область памяти для стека вспомогательного потока IP
- **memory_size**: число байтов в области памяти для стека вспомогательного потока IP
- **priority**: приоритет вспомогательного потока IP

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное создание экземпляра IP.
- **NX_NOT_IMPLEMENTED** (0x4A) — библиотека NetX настроена неправильно.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес, указатель функции сетевого драйвера, пул пакетов или указатель на память.
- **NX_SIZE_ERROR** (0x09) — указанный размер стека слишком мал.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_IP_ADDRESS_ERROR** (0x21) — указан недопустимый IP-адрес.
- **NX_OPTION_ERROR** (0x21) — указан недопустимый приоритет потока IP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Удаление ранее созданного экземпляра IP


### <a name="prototype"></a>Прототип

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр IP и освобождает все принадлежащие ему ресурсы системы.

### <a name="parameters"></a>Параметры
- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр IP успешно удален.
- **NX_SOCKETS_BOUND** (0x28) — к этому экземпляру IP все еще привязаны сокеты UDP или TCP. Перед удалением экземпляра IP необходимо отвязать и удалить все сокеты.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Отправка команды сетевому драйверу

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Описание

Эта служба предоставляет интерфейс для прямого взаимодействия с драйвером основного сетевого интерфейса приложения, указанным во время вызова ***nx_ip_create***.

Можно использовать команды для конкретного приложения, если их числовые значения больше или равны NX_LINK_USER_COMMAND.

*Чтобы отправить команду дополнительному устройству, используйте службу **nx_ip_driver_interface_direct_command**.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **command**: числовой код команды Стандартные команды определяются следующим образом.

- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)

- **return_value_ptr**: указатель возвращаемой переменной в вызывающем объекте

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная прямая команда сетевого драйвера.
- **NX_UNHANDLED_COMMAND** (0x44) — необработанная или нереализованная команда сетевого драйвера.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемого значения.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

- **Возможно вытеснение**

Нет

### <a name="example"></a>Пример

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Отправка команды сетевому драйверу

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Описание

Эта служба предоставляет прямую команду для драйвера сетевого устройства приложения в экземпляре IP. Можно использовать команды для конкретного приложения, если их числовые значения больше или равны *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **command**: числовой код команды Стандартные команды определяются следующим образом.
- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)
- **interface_index**: индекс сетевого интерфейса, которому необходимо отправить команду.
- **return_value_ptr**: указатель возвращаемой переменной в вызывающем объекте

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешная прямая команда сетевого драйвера.
- **NX_UNHANDLED_COMMAND** (0x44) — необработанная или нереализованная команда сетевого драйвера.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемого значения.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Отключение переадресации IP-пакетов

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает переадресацию IP-пакетов внутри IP-компонента NetX. При создании задачи IP эта служба автоматически отключается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное отключение переадресации IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Включение переадресации IP-пакетов

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает переадресацию IP-пакетов внутри IP-компонента NetX. При создании задачи IP эта служба автоматически отключается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное включение переадресации IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Отключение фрагментации IP-пакетов

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает возможность фрагментации и повторной сборки IP-пакетов. Пакеты, ожидающие повторной сборки, освобождаются. При создании задачи IP эта служба автоматически отключается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное отключение фрагментации IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — фрагментация IP-пакетов не включена в экземпляре IP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Включение фрагментации IP-пакетов

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает возможность фрагментации и повторной сборки IP-пакетов. При создании задачи IP эта служба автоматически отключается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение фрагментации IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функции фрагментации IP-пакетов не компилируются в NetX.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Задание IP-адреса шлюза

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес шлюза IP. Весь трафик, исходящий из сети, направляется в этот шлюз для передачи. Шлюз должен быть доступен напрямую через один из сетевых интерфейсов.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address**: IP-адрес шлюза

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — IP-адрес шлюза успешно задан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на экземпляр IP.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, поток

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>См. также:

- nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete

## <a name="nx_ip_info_get"></a>nx_ip_info_get

Получение сведений о действиях IP

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола IP для указанного экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_total_packets_sent**: указатель на место назначения для общего числа отправленных IP-пакетов
- **ip_total_bytes_sent**: указатель на место назначения для общего числа отправленных байтов
- **ip_total_packets_received**: указатель на место назначения для общего числа полученных IP-пакетов
- **ip_total_bytes_received**: указатель на место назначения для общего числа полученных по IP байтов
- **ip_invalid_packets**: указатель на место назначения для общего числа недопустимых IP-пакетов
- **ip_receive_packets_dropped**: указатель на место назначения для общего числа полученных и отброшенных пакетов
- **ip_receive_checksum_errors**: указатель на место назначения для общего числа ошибок контрольной суммы в полученных пакетах
- **ip_send_packets_dropped**: указатель на место назначения для общего числа отправленных и отброшенных пакетов
- **ip_total_fragments_sent**: указатель на место назначения для общего числа отправленных фрагментов
- **ip_total_fragments_received**: указатель на место назначения для общего числа полученных фрагментов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

Получение IP-адреса интерфейса

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Описание

Эта служба получает IP-адрес указанного сетевого интерфейса.

*Указанное устройство, если оно не является основным, должно быть предварительно подключено к экземпляру IP.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **interface_index**: индекс интерфейса; совпадает с индексом сетевого интерфейса, подключенного к экземпляру IP
- **ip_address**: указатель на место назначения для IP-адреса интерфейса устройства
- **network_mask**: указатель на место назначения для маски сети интерфейса устройства

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение IP-адреса.
- **NX_INVALID_INTERFACE** (0x4C) — указан недопустимый сетевой интерфейс.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_set, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

Задание IP-адреса и маски сети интерфейса

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Описание

Эта служба задает IP-адрес и маску сети для указанного интерфейса IP.

*Указанный интерфейс должен быть предварительно подключен к экземпляру IP.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **interface_index**: индекс интерфейса, присоединенного к экземпляру NetX
- **ip_address**: новый IP-адрес сетевого интерфейса
- **network_mask**: новая маска сети интерфейса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешный набор IP-адресов.
- **NX_INVALID_INTERFACE** (0x4C) — указан недопустимый сетевой интерфейс.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимые указатели.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

Подключение сетевого интерфейса к экземпляру IP

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a>Описание

Эта служба добавляет физический сетевой интерфейс к интерфейсу IP. Обратите внимание, что экземпляр IP создается с основным интерфейсом, поэтому каждый следующий интерфейс является дополнительным для него. Общее число сетевых интерфейсов, подключенных к экземпляру IP (включая основной интерфейс), не может превышать **NX_MAX_PHYSICAL_INTERFACES**.

Если поток IP еще не запущен, дополнительные интерфейсы будут инициализированы в процессе запуска потока IP, который инициализирует все физические интерфейсы.

Если поток IP еще не запущен, дополнительный интерфейс инициализируется службой ***nx_ip_interface_attach***.

*ip_ptr должен указывать на допустимую структуру IP в NetX.*

- *В **NX_MAX_PHYSICAL_INTERFACES** необходимо указать количество сетевых интерфейсов для экземпляра IP. Значение по умолчанию — 1.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **interface_name**: указатель на строку с именем интерфейса
- **ip_address**: IP-адрес устройства в порядке байтов узла
- **network_mask**: маска сети устройства в порядке байтов узла
- **ip_link_driver**: драйвер Ethernet для интерфейса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись добавлена в таблицу статической маршрутизации.
- **NX_NO_MORE_ENTRIES** (0x17) — максимальное число интерфейсов.
- Превышено значение **NX_MAX_PHYSICAL_INTERFACES**.
- **NX_DUPLICATED_ENTRY** (0x52) — указанный IP-адрес уже используется в этом экземпляре IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимые входные данные IP-адреса.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

Получение параметров сетевого интерфейса


### <a name="prototype"></a>Прототип

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a>Описание

Эта служба получает сведения о параметрах сети для указанного сетевого интерфейса. Все данные извлекаются в порядке байтов узла.

*Указатель ip_ptr должен указывать на допустимую структуру IP в NetX. Указанный интерфейс, если он не является основным, должен быть предварительно подключен к экземпляру IP.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **interface_index**: индекс, указывающий сетевой интерфейс
- **interface_name**: указатель на буфер, содержащий имя сетевого интерфейса
- **ip_address**: указатель на место назначения для IP-адреса интерфейса
- **network_mask**: указатель места назначения для маски сети
- **mtu_size**: указатель на место назначения максимальной единицы передачи для этого интерфейса
- **physical_address_msw**: указатель места назначения для старших 16 бит MAC-адреса устройства
- **physical_address_lsw**: указатель места назначения для младших 32 бит MAC-адреса устройства


### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — сведения об интерфейсе получены.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

Проверка состояния экземпляра IP


### <a name="prototype"></a>Прототип

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба проверяет и при необходимости ожидает указанное состояние сетевого интерфейса ранее созданного экземпляра IP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **interface_index**: номер индекса интерфейса
- **needed_status**: запрошенное состояние IP, определенное в виде битовой карты следующим образом
    - NX_IP_INITIALIZE_DONE (0x0001)
    - NX_IP_ADDRESS_RESOLVED (0x0002)
    - NX_IP_LINK_ENABLED (0x0004)
    - NX_IP_ARP_ENABLED (0x0008)
    - NX_IP_UDP_ENABLED (0x0010)
    - NX_IP_TCP_ENABLED (0x0020)
    - NX_IP_IGMP_ENABLED (0x0040)
    - NX_IP_RARP_COMPLETE (0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status**: указатель на место назначения фактического набора битов
- **wait_option**: определяет поведение службы в случае, если запрошенные биты состояния недоступны Параметры ожидания определяются следующим образом.
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная проверка состояния IP-адреса.
- **NX_NOT_SUCCESSFUL** (0x43) — запрос состояния не был выполнен в течение указанного времени ожидания.
- **NX_PTR_ERROR** (0x07) — указатель IP является или стал недопустимым, либо недопустимый указатель фактического состояния.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр требуемого состояния.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_INTERFACE** (0x4C) — индекс интерфейса за пределами допустимого диапазона, либо недопустимый интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

Задание функции обратного вызова для уведомления об изменении состояния канала

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Описание

Эта служба настраивает функцию обратного вызова для уведомления об изменении состояния канала. Указанная пользователем подпрограмма *link_status_change_notify* вызывается при изменении состояния основного или дополнительного интерфейса (например, при изменении IP-адреса). Если *link_status_change_notify* имеет значение NULL, функция обратного вызова для уведомления об изменении состояния канала отключена.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель блока управления IP
- **link_status_change_notify**: указанная пользователем функция обратного вызова, вызываемая при изменении физического интерфейса


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное задание.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель управляющего блока IP или новый указатель на физический адрес
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.


### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

Отключение отправки и получения необработанных пакетов


### <a name="prototype"></a>Прототип

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает передачу и получение необработанных IP-пакетов для данного экземпляра IP. Если служба необработанных пакетов была включена ранее и в очереди приема есть необработанные пакеты, эта служба освобождает все полученные необработанные пакеты.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное отключение необработанных IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

Включение обработки необработанных пакетов


### <a name="prototype"></a>Прототип

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает передачу и получение необработанных IP-пакетов для данного экземпляра IP. Входящие пакеты TCP, UDP, ICMP и IGMP по-прежнему обрабатываются NetX. Пакеты с неизвестными типами протоколов верхнего уровня обрабатываются подпрограммой приема необработанных пакетов.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение необработанных IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

Отправка необработанного IP-пакета через указанный сетевой интерфейс

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Описание

Эта служба отправляет необработанный IP-пакет на конечный IP-адрес через связанный сетевой интерфейс, используя указанный локальный IP-адрес в качестве исходного. Обратите внимание, что эта подпрограмма возвращает управление немедленно. Поэтому неизвестно, был ли IP-пакет отправлен на самом деле. Сетевой драйвер отвечает за освобождение пакета по завершении передачи. Эта служба отличается от других служб тем, что узнать, был ли пакет на самом деле отправлен, невозможно. Он мог быть потерян в процессе передачи через Интернет.

*Обратите внимание, что должна быть включена обработка необработанных IP-адресов.*

*Эта служба аналогична **nx_ip_raw_packet_send**, за исключением того, что она позволяет приложению отправлять необработанные IP-пакеты из указанных физических интерфейсов.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданную задачу IP
- **packet_ptr**: указатель на передаваемый пакет
- **destination_ip**: IP-адрес, на который нужно отправить пакет
- **address_index**: индекс адреса интерфейса, из которого нужно отправить пакет
- **type_of_service**: тип службы для пакета

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет успешно передан.
- **NX_IP_ADDRESS_ERROR** (0x21) — нет подходящего исходящего интерфейса.
- **NX_NOT_ENABLED** (0x14) — обработка необработанных IP-пакетов не включена.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_OPTION_ERROR** (0x0A) — указан недопустимый тип службы.
- **NX_OVERFLOW** (0x03) — недопустимый указатель префикса пакета.
- **NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.
- **NX_INVALID_INTERFACE** (0x4C) — указан недопустимый индекс интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

Получение необработанного IP-пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает необработанный IP-пакет из указанного экземпляра IP. При наличии IP-пакетов в очереди приема необработанных пакетов вызывающему объекту возвращается первый (самый старый) пакет. В противном случае, если пакеты недоступны, вызывающий объект может приостановить работу согласно значению параметра wait.

*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **packet_ptr**: указатель на место размещения полученного необработанного IP-пакета
- **wait_option** определяет поведение службы в случае, если нет доступных необработанных IP-пакетов Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение необработанного IP-пакета.
- **NX_NO_PACKET** (0x01) — нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемого пакета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

Отправка необработанного IP-пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Описание

Эта служба отправляет необработанный IP-пакет на целевой IP-адрес. Обратите внимание, что эта подпрограмма возвращает управление немедленно. Поэтому неизвестно, был ли IP-пакет отправлен на самом деле. Сетевой драйвер отвечает за освобождение пакета по завершении передачи.

В системе с множественной адресацией NetX ищет соответствующий сетевой интерфейс по IP-адресу назначения и использует IP-адрес интерфейса в качестве исходного адреса. Если IP-адрес назначения является широковещательным или многоадресным, используется первый допустимый интерфейс. В этом случае приложения используют ***nx_ip_raw_packet_interface_send***.

*Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Это приведет к непредсказуемым результатам, так как сетевой драйвер освободит пакет после передачи.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **packet_ptr**: указатель на отправляемый IP-пакет
- **destination_ip**: конечный IP-адрес, которым может быть IP-адрес конкретного узла, сетевой широковещательный адрес, петлевой адрес или адрес многоадресной рассылки
- **type_of_service** определяет тип службы для передачи. Допустимые значения:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная инициация отправки необработанного IP-пакета.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_NOT_ENABLED** (0x14) — функция необработанных IP-пакетов не включена.
- **NX_OPTION_ERROR** (0x0A) — недопустимый тип службы.
- **NX_UNDERFLOW** (0x02) — недостаточно места для добавления заголовка IP в начало пакета.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель пакета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send,
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

Добавление статического маршрута в таблицу маршрутизации

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Описание

Эта служба добавляет запись в таблицу статической маршрутизации. Обратите внимание, что адрес *next_hop* должен быть доступен напрямую с одного из локальных сетевых устройств.

*Обратите внимание, что указатель ip_ptr должен указывать на допустимую структуру IP в NetX, а сборка библиотеки NetX должна выполняться с параметром NX_ENABLE_IP_STATIC_ROUTING, предписывающим использование этой службы. По умолчанию сборка NetX выполняется без задания параметра NX_ENABLE_IP_STATIC_ROUTING.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **network_address**: целевой сетевой адрес в порядке байтов узла
- **net_mask**: маска целевой сети в порядке байтов узла
- **next_hop**: адрес следующего прыжка для целевой сети в порядке байтов узла

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись добавлена в таблицу статической маршрутизации.
- **NX_OVERFLOW** (0x03) — таблица статической маршрутизации заполнена.
- **NX_NOT_SUPPORTED** (0x4B) — эта функция не компилируется.
- **NX_IP_ADDRESS_ERROR** (0x21) — следующий прыжок недоступен напрямую через локальные интерфейсы.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ip_ptr.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

Удаление статического маршрута из таблицы маршрутизации

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Описание

Эта служба удаляет запись из таблицы статической маршрутизации.

*Обратите внимание, что указатель ip_ptr должен указывать на допустимую структуру IP в NetX, а сборка библиотеки NetX должна выполняться с параметром NX_ENABLE_IP_STATIC_ROUTING, предписывающим использование этой службы. По умолчанию сборка NetX выполняется без задания параметра NX_ENABLE_IP_STATIC_ROUTING.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **network_address**: целевой сетевой адрес в порядке байтов узла
- **net_mask**: маска целевой сети в порядке байтов узла

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

Проверка состояния экземпляра IP

### <a name="prototype"></a>Прототип

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба проверяет и при необходимости ожидает указанное состояние основного сетевого интерфейса ранее созданного экземпляра IP. Чтобы получить состояние дополнительных интерфейсов, приложения должны использовать службу ***nx_ip_interface_status_check***.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **needed_status**: запрошенное состояние IP, определенное в виде битовой карты следующим образом
- NX_IP_INITIALIZE_DONE (0x0001)
- NX_IP_ADDRESS_RESOLVED (0x0002)
- NX_IP_LINK_ENABLED (0x0004)
- NX_IP_ARP_ENABLED (0x0008)
- NX_IP_UDP_ENABLED (0x0010)
- NX_IP_TCP_ENABLED (0x0020)
- NX_IP_IGMP_ENABLED (0x0040)
- NX_IP_RARP_COMPLETE (0x0080)
- NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status**: указатель на место назначения фактического набора битов
- **wait_option**: определяет поведение службы в случае, если запрошенные биты состояния недоступны Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная проверка состояния IP-адреса.
- **NX_NOT_SUCCESSFUL** (0x43) — запрос состояния не был выполнен в течение указанного времени ожидания.
- **NX_PTR_ERROR** (0x07) — указатель IP является или стал недопустимым, либо недопустимый указатель фактического состояния.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр требуемого состояния.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

Выделение пакета из указанного пула

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба выделяет пакет из указанного пула и корректирует положение начального указателя в пакете в соответствии с указанным типом пакета. Если пакет недоступен, служба приостанавливает работу в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **pool_ptr**: указатель на ранее созданный пул пакетов
- **packet_ptr**: указатель на указатель выделенного пакета
- **packet_type**: определяет тип запрошенного пакета Список поддерживаемых типов пакетов см. в разделе "Пулы пакетов" главы 3 на стр. 49.
- **wait_option** определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет выделен успешно.
- **NX_NO_PACKET** (0x01) — нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.
- **NX_OPTION_ERROR** (0x0A) — недопустимый тип пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый возвращаемый указатель на пул или пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый параметр ожидания не из потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры и запросы ISR (сетевые драйверы приложений). Параметр ожидания должен иметь значение NX_NO_WAIT при использовании в ISR или контексте таймера.

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a>См. также:

- nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

Копирование пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба копирует сведения из предоставленного пакета в один новый пакет, выделенный из указанного пула пакетов, или несколько. В случае успеха возвращается указатель на новый пакет в месте назначения, на которое указывает **new_packet_ptr**.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на исходный пакет
- **new_packet_ptr**: указатель на место назначения, где нужно вернуть указатель на новую копию пакета
- **pool_ptr**: указатель на ранее созданный пул пакетов, который используется для выделения одного копируемого пакета или нескольких
- **wait_option** определяет поведение службы в случае, если нет доступных пакетов Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — пакет успешно скопирован.
- **NX_NO_PACKET** (0x01) — пакет недоступен для копирования.
- **NX_INVALID_PACKET** (0x12) — пустой исходный пакет, или не удалось выполнить копирование.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.
- **NX_PTR_ERROR** (0x07) — недопустимый пул, пакет или указатель на место назначения.
- **NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_CALLER_ERROR** (0x11) — параметр ожидания был указан при инициализации или в ISR.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Добавление данных в конец пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба добавляет данные в конец указанного пакета. Указанная область данных копируется в пакет. Если недостаточно памяти и включена функция сцепления пакетов, для выполнения запроса будет выделен один пакет или несколько. Если функция сцепления пакетов не включена, возвращается *NX_SIZE_ERROR*.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет
- **data_start**: указатель на начало пользовательской области данных для добавления к пакету
- **data_size**: размер пользовательской области данных
- **pool_ptr**: указатель на пул пакетов, из которого нужно выделить другой пакет, если в текущем пакете недостаточно места
- **wait_option** определяет поведение службы в случае, если нет доступных пакетов Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет успешно добавлен.
- **NX_NO_PACKET** (0x01) — нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.
- **NX_UNDERFLOW** (0x02) — начальный указатель меньше, чем начало полезных данных.
- **NX_OVERFLOW** (0x03) — конечный указатель меньше, чем конец полезных данных.
- **NX_PTR_ERROR** (0x07) — недопустимый пул, пакет или указатель на данные.
- **NX_SIZE_ERROR** (0x09) — недопустимый размер данных.
- **NX_CALLER_ERROR** (0x11) — недопустимый параметр ожидания не из потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры и запросы ISR (сетевые драйверы приложений)

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

Извлечение данных из пакета по смещению

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a>Описание

Эта служба копирует данные из пакета NetX (или из цепочки пакетов), начиная с указанного смещения от начального указателя пакета указанного размера в байтах в заданный буфер. Число фактически скопированных байтов возвращается в *bytes_copied*. Эта служба не удаляет данные из пакета и не настраивает начальный указатель или другую информацию о внутреннем состоянии.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на извлекаемый пакет
- **offset**: смещение от текущего начального указателя
- **buffer_start**: указатель на начало буфера сохранения
- **buffer_length**: число копируемых байтов
- **bytes_copied**: число фактически скопированных байтов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет успешно скопирован.
- **NX_PACKET_OFFSET_ERROR** (0x53) — указано недопустимое значение смещения.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на пакет или буфер.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

Получение данных из пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a>Описание

Эта служба копирует данные из предоставленного пакета в указанный буфер. Фактическое число скопированных байтов возвращается в месте назначения, на которое указывает **bytes_copied**.

Обратите внимание, что эта служба не изменяет внутреннее состояние пакета. Получаемые данные по-прежнему доступны в пакете.

*Буфер назначения должен быть достаточно большим, чтобы вместить содержимое пакета. В противном случае память будет повреждена, что приведет к непредсказуемым результатам.*

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на исходный пакет
- **buffer_start**: указатель на начало буферной области
- **bytes_copied**: указатель на место назначения для числа скопированных байтов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные успешно получены из пакета.
- **NX_INVALID_PACKET** (0x12) — недопустимый пакет.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на пакет, начало буфера или копируемые байты.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_length_get,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Получение длины данных в пакете

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Описание

Эта служба получает длину данных в указанном пакете.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет
- **length**: место назначения для длины пакета

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Создание пула пакетов в указанной области памяти

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a>Описание

Эта служба создает пул пакетов указанного размера в области памяти, заданной пользователем.

### <a name="parameters"></a>Параметры

- **pool_ptr**: указатель на блок управления пулом пакетов
- **name**: указатель на имя приложения для пула пакетов
- **payload_size**: число байтов в каждом пакете в пуле Это значение должно быть не менее 40 байт и кратно 4.
- **memory_ptr**: указатель на область памяти, в которой будет размещен пул пакетов Указатель должен быть выровнен по границе ULONG.
- **memory_size**: размер области памяти пула

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пул пакетов успешно создан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на пул или память.
- **NX_SIZE_ERROR** (0x09) — недопустимый размер блока или памяти.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Удаление ранее созданного пула пакетов

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный пул пакетов. NetX проверяет все потоки, приостановленные при обработке пакетов в пуле пакетов, и отменяет приостановку.

### <a name="parameters"></a>Параметры

- **pool_ptr**: указатель на блок управления пулом пакетов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пул пакетов успешно удален.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на пул.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

Получение сведений о пуле пакетов

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном пуле пакетов.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **pool_ptr**: указатель на ранее созданный пул пакетов
- **total_packets**: указатель на место назначения для общего числа пакетов в пуле
- **free_packets**: указатель на место назначения для общего числа пакетов, свободных в настоящее время
- **empty_pool_requests**: указатель на место назначения для общего числа запросов на выделение, если пул был пуст
- **empty_pool_suspensions**: указатель на место назначения для общего числа приостановок в пустом пуле
- **invalid_packet_releases**: указатель на место назначения для общего числа недопустимых освобождений пакетов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сведения о пуле пакетов успешно получены.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Освобождение ранее выделенного пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба освобождает пакет, а также все сцепленные с ним пакеты. Если другой поток блокируется при выделении пакета, ему предоставляется пакет и его работа возобновляется.

*Приложение должно предотвращать многократное освобождение пакета, так как оно приведет к непредсказуемым результатам.*

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет


### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — пакет успешно освобожден.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель пакета.
- **NX_UNDERFLOW** (0x02) — начальный указатель меньше, чем начало полезных данных.
- **NX_OVERFLOW** (0x03) — конечный указатель меньше, чем конец полезных данных.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры и запросы ISR (сетевые драйверы приложений)

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Освобождение переданного пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Для пакетов, отличных от TCP, эта служба освобождает переданный пакет, а также все сцепленные с ним пакеты. Если другой поток блокируется при выделении пакета, ему предоставляется пакет и его работа возобновляется. TCP-пакет помечается как передаваемый, но не освобождается, пока не будет подтвержден. Эта служба обычно вызывается из сетевого драйвера приложения после передачи пакета.

*Сетевой драйвер должен удалить заголовок физического носителя и изменить длину пакета перед вызовом этой службы.*

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — переданный пакет успешно освобожден.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель пакета.
- **NX_UNDERFLOW** (0x02) — начальный указатель меньше, чем начало полезных данных.
- **NX_OVERFLOW** (0x03) — конечный указатель меньше, чем конец полезных данных.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, сетевые драйверы приложений (запросы ISR)

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a>См. также:

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Отключение протокола RARP

### <a name="prototype"></a>Прототип

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает компонент RARP для определенного экземпляра IP в NetX. В системе с множественной адресацией эта служба отключает протокол RARP во всех интерфейсах.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное отключение RARP.
- **NX_NOT_ENABLED** (0x14) — протокол RARP не был включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>См. также:

- nx_rarp_enable, nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

Включение протокола RARP

### <a name="prototype"></a>Прототип

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает компонент RARP для определенного экземпляра IP в NetX. Компонент RARP выполняет поиск нулевого IP-адреса во всех подключенных сетевых интерфейсах. Нулевой IP-адрес означает, что интерфейсу еще не назначен IP-адрес. Протокол RARP пытается разрешить IP-адрес, включив в нем процесс RARP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение RARP.
- **NX_IP_ADDRESS_ERROR** (0x21) — уже есть действительный IP-адрес.
- **NX_ALREADY_ENABLED** (0x15) — протокол RARP уже включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>См. также:

- nx_rarp_disable, nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get

Получение сведений о действиях RARP

### <a name="prototype"></a>Прототип

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола RARP для указанного экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **rarp_requests_sent**: указатель на место назначения для общего числа отправленных запросов RARP
- **rarp_responses_received**: указатель на место назначения для общего числа полученных ответов RARP
- **rarp_invalid_messages**: указатель на место назначения для общего числа недопустимых сообщений


### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное получение сведений RARP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_rarp_disable, nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

Инициализация системы NetX

### <a name="prototype"></a>Прототип

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Описание

Эта служба инициализирует базовые системные ресурсы NetX в процессе подготовки к использованию. Она должна вызываться приложением во время инициализации до выполнения других вызовов NetX.

### <a name="parameters"></a>Параметры

None

### <a name="return-values"></a>Возвращаемые значения

Нет

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>См. также:

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Привязка клиентского сокета TCP к TCP-порту

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба привязывает ранее созданный клиентский сокет TCP к указанному TCP-порту. Допустимый диапазон сокетов TCP — от 0 до 0xFFFF. Если указанный TCP-порт недоступен, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **port**: номер порта для привязки (от 1 до 0xFFFF) Если номер порта — NX_ANY_PORT (0x0000), экземпляр IP будет искать следующий свободный порт и использует его для привязки.
- **wait_option**: определяет поведение службы в случае, если порт уже привязан к другому сокету Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно привязан.
- **NX_ALREADY_BOUND** (0x22) — этот сокет уже привязан к другому TCP-порту.
- **NX_PORT_UNAVAILABLE** (0x23) — порт уже привязан к другому сокету.
- **NX_NO_FREE_PORTS** (0x45) — нет свободного порта.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.
- **NX_INVALID_PORT** (0x46) — недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Подключение клиентского сокета TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба подключает ранее созданный и привязанный клиентский сокет TCP к указанному порту сервера. Допустимый диапазон портов TCP-сервера — от 0 до 0xFFFF. Если подключение не завершается немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **server_ip**: IP-адрес сервера
- **server_port**: номер порта сервера для подключения (от 1 до 0xFFFF)
- **wait_option** определяет поведение службы во время установления соединения Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно подключен.
- **NX_NOT_BOUND** (0x24) — сокет не привязан.
- **NX_NOT_CLOSED** (0x35) — сокет не находится в закрытом состоянии.
- **NX_IN_PROGRESS** (0x37) — параметр ожидания не указан; выполняется попытка подключения.
- **NX_INVALID_INTERFACE** (0x4C) — указан недопустимый интерфейс.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес сервера.
- **NX_INVALID_PORT** (0x46) — недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Получение номера порта, привязанного к клиентскому сокету TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Описание

Эта служба получает номер порта, связанного с сокетом, что может быть полезно при поиске порта, выделенного NetX, если во время привязки сокета было указано значение NX_ANY_PORT.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **port_ptr**: указатель на место назначения для возвращаемого номера порта Допустимые номера портов: от 1 до 0xFFFF.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно привязан.
- **NX_NOT_BOUND** (0x24) — этот сокет не привязан к порту.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета или возвращаемого порта.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Отмена привязки клиентского сокета TCP к TCP-порту

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба отменяет привязку между клиентским сокетом TCP и TCP-портом. Если есть другие потоки, ожидающие привязки другого сокета к тому же номеру порта, к порту привязывается первый приостановленный поток.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — привязка сокета успешно отменена.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_NOT_CLOSED** (0x35) — сокет не отключен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Включение компонента TCP в NetX

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает компонент протокола TCP в NetX. После включения приложение может устанавливать TCP-подключения.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение TCP.
- **NX_ALREADY_ENABLED** (0x15) — протокол TCP уже включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Поиск следующего доступного TCP-порта

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Описание

Эта служба пытается найти свободный TCP-порт (без привязки) начиная с порта, указанного приложением. Если достигнуто максимальное значение порта 0xFFFF, поиск начинается с самого начала. Если поиск завершен успешно, свободный порт возвращается в переменной, на которую указывает *free_port_ptr*.

*Если эта служба вызывается из другого потока, она может вернуть тот же порт. Чтобы предотвратить такое состояние гонки, приложение может защитить эту службу и привязку клиентского сокета мьютексом.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **port**: номер порта, с которого начинается поиск (от 1 до 0xFFFF)
- **free_port_ptr**: указатель на место назначения для возвращаемого значения свободного порта

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — поиск свободного порта успешно завершен.
- **NX_NO_FREE_PORTS** (0x45) — нет свободного порта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_INVALID_PORT** (0x46) — указан недопустимый номер порта.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

Получение сведений о действиях TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола TCP для указанного экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **tcp_packets_sent**: указатель на место назначения для общего числа отправленных TCP-пакетов
- **tcp_bytes_sent**: указатель на место назначения для общего числа отправленных по TCP байтов
- **tcp_packets_received**: указатель на место назначения для общего числа полученных TCP-пакетов
- **tcp_bytes_received**: указатель на место назначения для общего числа полученных по TCP байтов
- **tcp_invalid_packets**: указатель на место назначения для общего числа недопустимых TCP-пакетов
- **tcp_receive_packets_dropped**: указатель на место назначения для общего числа полученных и отброшенных TCP-пакетов
- **tcp_checksum_errors**: указатель на место назначения для общего числа TCP-пакетов с ошибками контрольной суммы
- **tcp_connections**: указатель на место назначения для общего числа TCP-подключений
- **tcp_disconnections**: указатель на место назначения для общего числа прерванных TCP-подключений
- **tcp_connections_dropped**: указатель на место назначения для общего числа отброшенных TCP-подключений
- **tcp_retransmit_packets**: указатель на место назначения для общего числа ретранслированных TCP-пакетов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений TCP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Принятие TCP-подключения

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба принимает (или готовится принять) запрос на подключение к клиентскому сокету TCP для порта, который ранее был настроен для ожидания передачи данных. Эту службу можно вызывать сразу после того, как приложение вызовет службу ожидания или повторного ожидания передачи данных, или после вызова подпрограммы обратного вызова для ожидания передачи данных при наличии клиентского подключения. Если подключение невозможно установить немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

*Когда подключение больше не требуется, приложение должно вызвать **nx_tcp_server_socket_unaccept**, чтобы удалить привязку сокета сервера к порту сервера.*

*Подпрограммы обратного вызова приложения вызываются из вспомогательного потока IP.*

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на управляющий блок сокета TCP-сервера
- **wait_option** определяет поведение службы во время установления соединения Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)


### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное принятие сокета TCP-сервера (пассивное подключение).
- **NX_NOT_LISTEN_STATE** (0x36) — указанный сокет сервера не находится в состоянии ожидания передачи данных.
- **NX_IN_PROGRESS** (0x37) — параметр ожидания не указан; выполняется попытка подключения.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.
- **NX_PTR_ERROR** (0x07) — ошибка указателя сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

Включение ожидания передачи данных для клиентского подключения через TCP-порт

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Описание

Эта служба включает ожидание запроса клиентского подключения через указанный TCP-порт. При получении запроса на подключение клиента указанный сокет сервера привязывается к заданному порту и вызывается указанная функция обратного вызова для ожидания передачи данных.

За выполнение подпрограммы обратного вызова для ожидания передачи данных полностью отвечает приложение. Она может включать в себя логику для пробуждения потока приложения, который затем выполняет операцию принятия. Если в приложении уже есть поток, приостановленный при обработке принятия для этого сокета, подпрограмма обратного вызова для ожидания передачи данных может не потребоваться.

Если приложение планирует обрабатывать дополнительные клиентские подключения через тот же порт, служба ***nx_tcp_server_socket_relisten*** должна быть вызвана с доступным сокетом (в закрытом состоянии) для следующего подключения. Пока не будет вызвана служба повторного ожидания передачи данных, дополнительные клиентские подключения помещаются в очередь. При превышении максимальной глубины очереди самый старый запрос на подключение отбрасывается в пользу нового. Максимальная глубина очереди задается данной службой.

*Подпрограммы обратного вызова приложения вызываются из внутреннего вспомогательного потока IP.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **port**: номер порта для ожидания передачи данных (от 1 до 0xFFFF)
- **socket_ptr**: указатель на сокет, который следует использовать для подключения
- **listen_queue_size**: число запросов на клиентское подключение, которые можно поставить в очередь
- **listen_callback**: функция приложения, вызываемая при получении подключения Если указано значение NULL, функция обратного вызова для ожидания передачи данных отключена.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ожидание передачи данных через TCP-порт успешно включено.
- **NX_MAX_LISTEN** (0x33) — больше нет доступных структур запросов на ожидание передачи данных. Константа NX_MAX_LISTEN_REQUESTS в nx_api.h определяет, сколько активных запросов на ожидание передачи данных возможно.
- **NX_NOT_CLOSED** (0x35) — указанный сокет сервера не находится в закрытом состоянии.
- **NX_ALREADY_BOUND** (0x22) — указанный сокет сервера уже привязан к порту.
- **NX_DUPLICATE_LISTEN** (0x34) — для этого порта уже имеется активный запрос на ожидание передачи данных.
- **NX_INVALID_PORT** (0x46) — указан недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса или сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Повторное ожидание передачи данных для клиентского подключения через TCP-порт

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба вызывается после получения подключения через порт, который ранее был настроен для ожидания передачи данных. Основная задача этой службы — предоставление нового сокета сервера для следующего клиентского подключения. Если запрос на подключение ставится в очередь, подключение обрабатывается немедленно во время вызова этой службы.

*Подпрограмма обратного вызова, указанная в исходном запросе на ожидание передачи данных, вызывается и при наличии подключения для этого нового сокета сервера.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **port**: номер порта для повторного ожидания передачи данных (от 1 до 0xFFFF)
- **socket_ptr**: сокет, используемый для следующего клиентского подключения

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — успешное повторное ожидание передачи данных через TCP-порт.
- **NX_NOT_CLOSED** (0x35) — указанный сокет сервера не находится в закрытом состоянии.
- **NX_ALREADY_BOUND** (0x22) — указанный сокет сервера уже привязан к порту.
- **NX_INVALID_RELISTEN** (0x47) — уже имеется допустимый указатель сокета для этого порта, или у указанного порта нет активного запроса на ожидание передачи данных.
- **NX_CONNECTION_PENDING** (0x48) — то же, что NX_SUCCESS, за исключением наличия запроса на подключение в очереди, который был обработан во время этого вызова.
- **NX_INVALID_PORT** (0x46) — указан недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель обратного вызова для ожидания передачи данных.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Удаление связи сокета с прослушиваемым портом

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет связь между сокетом сервера и указанным портом сервера. Приложение должно вызывать эту службу после завершения подключения или после неудачного вызова приема.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее настроенный экземпляр сокета сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — принятие сокета сервера успешно отменено.
- **NX_NOT_LISTEN_STATE** (0x36) — сокет сервера находится в неправильном состоянии и, возможно, не отключен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

Отключение ожидания передачи данных для клиентского подключения через TCP-порт

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a>Описание

Эта служба отключает ожидание запроса клиентского подключения через указанный TCP-порт.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **port**: номер порта для отключения ожидания передачи данных (от 0 до 0xFFFF)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ожидание передачи данных через TCP-порт успешно отключено.
- **NX_ENTRY_NOT_FOUND** (0x16) — ожидание передачи данных не было включено для указанного порта.
- **NX_INVALID_PORT** (0x46) — указан недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

Получает число байтов, доступных для извлечения

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Описание

Эта служба получает число байтов, доступных для извлечения в указанном сокете TCP. Обратите внимание, что сокет TCP уже должен быть подключен.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный и подключенный сокет TCP
- **bytes_available**: указатель на место назначения для доступных байтов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно выполняется. Число байтов, доступных для чтения, возвращается вызывающему объекту.
- **NX_NOT_CONNECTED** (0x38) — сокет не находится в подключенном состоянии.
- **NX_PTR_ERROR** (0x07) — недопустимые указатели.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Создание сокета TCP клиента или сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба создает сокет TCP-клиента или сервера для указанного экземпляра IP.

*Подпрограммы обратного вызова приложения вызываются из потока, связанного с этим экземпляром IP.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **socket_ptr**: указатель на новый управляющий блок сокета TCP
- **name**: имя приложения для этого сокета TCP
- **type_of_service** определяет тип службы для передачи. Допустимые значения:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragment** указывает, разрешена ли фрагментация IP-пакетов Если указано значение NX_FRAGMENT_OKAY (0x0), то фрагментация IP-пакетов разрешена. Если указано значение NX_DONT_FRAGMENT (0x4000), то фрагментация IP-пакетов отключена.
- **time_to_live** задает 8-разрядное значение, определяющее, сколько маршрутизаторов этот пакет может пройти перед тем, как будет отброшен Значение по умолчанию задается в NX_IP_TIME_TO_LIVE.
- **window_size** определяет максимальное допустимое число байтов в очереди приема для этого сокета
- **urgent_data_callback**: функция приложения, которая вызывается каждый раз при обнаружении в потоке приема срочных данных. Если это значение равно NX_NULL, срочные данные игнорируются.
- **disconnect_callback**: функция приложения, которая вызывается каждый раз, когда сокет выдает команду на завершение подключения на другом конце соединения. Если это значение равно NX_NULL, функция обратного вызова для завершения подключения отключена.

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — сокет TCP-клиента успешно создан.
- **NX_OPTION_ERROR** (0x0A) — недопустимый тип службы, параметр фрагментации, размер окна или параметр времени существования.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса или сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Удаление сокета TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее сокет TCP. Если сокет по-прежнему привязан или подключен, служба возвращает код ошибки.

### <a name="parameters"></a>Параметры

- **socket_ptr**: ранее созданный сокет TCP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно удален.
- **NX_NOT_CREATED** (0x27) — сокет не был создан.
- **NX_STILL_BOUND** (0x42) — сокет все еще привязан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

Завершение подключений к сокетам клиента и сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба завершает установленное подключение к сокету клиента или сервера. После завершения подключения к сокету сервера должен выполняться запрос на отмену принятия, а отключенный сокет клиента остается в состоянии готовности к другому запросу на подключение. Если процесс отключения не может завершиться немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **wait_option** определяет поведение службы во время завершения соединения Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно отключен.
- **NX_NOT_CONNECTED** (0x38) — указанный сокет не подключен.
- **NX_IN_PROGRESS** (0x37) — выполняется отключение; параметр ожидания не задан.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Установка функции обратного вызова для уведомления о завершении подключения TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова, которая вызывается после завершения операции отключения сокета. Функция обратного вызова для отключения сокета TCP доступна, если сборка NetX выполнена с заданным параметром

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **tcp_disconnect_complete_notify**: функция обратного вызова, которую необходимо установить

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — функция обратного вызова успешно зарегистрирована
- **NX_NOT_SUPPORTED** (0x4B) — расширенная функция уведомления не встроена в библиотеку NetX.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Задание функции обратного вызова для уведомления об установке TCP-подключения

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова, которая вызывается после установления соединения сокетом TCP. Функция обратного вызова для установления подключения к сокету TCP доступна, если сборка NetX выполнена с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **tcp_establish_notify**: функция обратного вызова, вызываемая после установления TCP-подключения

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — функция уведомления успешно задана.
- **NX_NOT_SUPPORTED** (0x4B) — расширенная функция уведомления не встроена в библиотеку NetX.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не был включен приложением.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

Получение сведений о действиях сокета TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях сокета TCP для указанного экземпляра сокета TCP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **tcp_packets_sent**: указатель на место назначения для общего числа отправленных через сокет TCP-пакетов
- **tcp_bytes_sent**: указатель на место назначения для общего числа отправленных через сокет TCP байтов
- **tcp_packets_received**: указатель на место назначения для общего числа полученных через сокет TCP-пакетов
- **tcp_bytes_received**: указатель на место назначения для общего числа полученных через сокет TCP байтов
- **tcp_retransmit_packets**: указатель на место назначения для общего числа ретранслированных TCP-пакетов
- **tcp_packets_queued**: указатель на место назначения для общего числа TCP-пакетов, поставленных в очередь в сокете
- **tcp_checksum_errors**: указатель на место назначения для общего числа TCP-пакетов с ошибками контрольной суммы в сокете
- **tcp_socket_state**: указатель на место назначения для текущего состояния сокета
- **tcp_transmit_queue_depth**: указатель на место назначения для общего числа передаваемых пакетов, ожидающих подтверждения в очереди
- **tcp_transmit_window**: указатель на место назначения для текущего размера окна передачи
- **tcp_receive_window**: указатель на место назначения для текущего размера окна приема

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений о сокете TCP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="return-values"></a>Возвращаемые значения

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Получение MSS сокета

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Описание

Эта служба получает локальный максимальный размер сегмента (MSS) для указанного сокета.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный сокет
- **mss**: место назначения для возвращаемого значения MSS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение MSS.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или место назначения для MSS.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

Получение MSS однорангового сокета TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Описание

Эта служба получает максимальный размер сегмента (MSS), объявленный одноранговым сокетом.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный и подключенный сокет
- **mss**: место назначения для возвращаемого значения MSS


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение MSS однорангового сокета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или место назначения для MSS.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

Задание MSS сокета

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a>Описание

Эта служба задает максимальный размер сегмента (MSS) для указанного сокета. Обратите внимание, что значение MSS должно быть в пределах размера MTU для сетевого IP-интерфейса, чтобы было место для заголовков IP и TCP.

Эту службу следует использовать до того, как сокет TCP начнет процесс подключения. Если служба используется после установления соединения TCP, новое значение для него не действует.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный сокет
- **mss**: задаваемое значение MSS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное задание MSS.
- **NX_SIZE_ERROR** (0x09) — указано слишком большое значение MSS.
- **NX_NOT_CONNECTED** (0x38) — TCP-подключение не установлено.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

Получение сведений об одноранговом сокете TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Описание

Эта служба получает IP-адрес и сведения о порте для подключенного однорангового сокета TCP по IP-сети.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный сокет TCP
- **peer_ip_address**: указатель на место назначения для IP-адреса однорангового сокета в порядке байтов узла
- **peer_port**: указатель на место назначения для номера порта однорангового сокета в порядке байтов узла

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно выполняется. IP-адрес и номер порта однорангового сокета возвращаются вызывающему объекту.
- **NX_NOT_CONNECTED** (0x38) — сокет не находится в подключенном состоянии.
- **NX_PTR_ERROR** (0x07) — недопустимые указатели.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

Получение данных из сокета TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает данные TCP из указанного сокета. Если в указанном сокете в очереди нет данных, вызывающий объект приостанавливает выполнение на основе указанного параметра ожидания.

*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **packet_ptr**: указатель на указатель TCP-пакета
- **wait_option** определяет поведение службы в случае, если в этом сокете нет данных в очереди Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — данные сокета успешно получены.
- **NX_NOT_BOUND** (0x24) — сокет еще не привязан.
- **NX_NO_PACKET** (0x01) — данные не получены.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_NOT_CONNECTED** (0x38) — сокет больше не подключен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или возвращаемый пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

/* Получение пакета из ранее созданного и подключенного сокета TCP-клиента. Если пакет недоступен, подождите 200 тактов таймера, прежде чем завершать операцию. */ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* Если состояние — NX_SUCCESS, на полученный пакет указывает packet_ptr. */

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Уведомление приложения о полученных пакетах


### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба настраивает указатель на функцию уведомления о получении с помощью функции обратного вызова, заданной приложением. Эта функция обратного вызова затем вызывается при получении одного пакета в сокете или нескольких. Если задан указатель NX_NULL, функция уведомления отключена.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на сокет TCP
- **tcp_receive_notify**: указатель на функцию обратного вызова приложения, вызываемую при получении одного пакета в сокете или нескольких.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное уведомление о получении.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

Отправка данных через сокет TCP

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет данные TCP через подключенный ранее сокет TCP. Если последний объявленный размер окна получателя меньше, чем этот запрос, служба при необходимости приостанавливает выполнение в соответствии с указанным параметром ожидания. Эта служба гарантирует, что на уровень IP будут отправлены пакеты данных объемом не более MSS.

*Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Это приведет к непредсказуемым результатам, так как сетевой драйвер также попытается освободить пакет после передачи.*

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета TCP
- **packet_ptr**: указатель на пакет данных TCP
- **wait_option** определяет поведение службы в случае, если запрос превышает размер окна получателя Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно отправлен.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_NOT_CONNECTED** (0x38) — сокет больше не подключен.
- **NX_WINDOW_OVERFLOW** (0x39) — запрос больше объявленного размера окна получателя в байтах.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_INVALID_PACKET** (0x12) — пакет не выделен.
- **NX_TX_QUEUE_DEPTH** (0x49) — достигнута максимальная глубина очереди передачи.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Ожидание перехода сокета TCP в определенное состояние

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба ожидает перехода сокета в требуемое состояние. Если сокет не находится в нужном состоянии, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета TCP
- **desired_state**: требуемое состояние TCP Допустимые состояния сокета TCP
- NX_TCP_CLOSED (0x01)
- NX_TCP_LISTEN_STATE (0x02)
- NX_TCP_SYN_SENT (0x03)
- NX_TCP_SYN_RECEIVED (0x04)
- NX_TCP_ESTABLISHED (0x05)
- NX_TCP_CLOSE_WAIT (0x06)
- NX_TCP_FIN_WAIT_1 (0x07)
- NX_TCP_FIN_WAIT_2 (0x08)
- NX_TCP_CLOSING (0x09)
- NX_TCP_TIMED_WAIT (0x0A)
- NX_TCP_LAST_ACK (0x0B)
- **wait_option** определяет поведение службы в случае, если запрошенное состояние отсутствует Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — ожидание состояния успешно завершено.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_NOT_SUCCESSFUL** (0x43) — состояние отсутствует в течение указанного времени ожидания.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_OPTION_ERROR** (0x0A) — требуемое состояние сокета недопустимо.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Установка обратного вызова для состояния ожидания с привязкой ко времени

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова, которая вызывается, когда сокет TCP находится в состоянии ожидания с привязкой ко времени. Чтобы использовать эту службу, необходимо выполнить сборку библиотеки NetX с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **tcp_timed_wait_callback**: функция обратного вызова для ожидания с привязкой ко времени

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет функции обратного вызова успешно зарегистрирован.
- **NX_NOT_SUPPORTED** (0x4B) — сборка библиотеки NetX выполнена без включенной функции расширенного уведомления.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

Настройка параметров передачи для сокета

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a>Описание

Эта служба настраивает различные параметры передачи для указанного сокета TCP.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на сокет TCP
- **max_queue_depth**: максимальное число пакетов, которое можно поставить в очередь для передачи
- **timeout**: число тактов таймера ThreadX, в течение которого необходимо ожидать подтверждения перед повторной отправкой пакета
- **max_retries**: максимальное допустимое число попыток
- **timeout_shift**: значение, на которое сдвигается время ожидания для каждой последующей попытки Значение 0 приводит к тому, что время ожидания между последовательными повторными попытками одинаково. Значение 1 приводит к удвоению времени ожидания между попытками.

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — настройка сокета передачи успешно выполнена.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр глубины очереди.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

Уведомление приложения об изменении размера окна

### <a name="prototype"></a>Прототип

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба устанавливает подпрограмму обратного вызова для изменения окна сокета. Эта подпрограмма вызывается автоматически каждый раз, когда указанный сокет получает пакет, в котором указано увеличить размер окна для удаленного узла.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный сокет TCP
- **tcp_window_update_notify**: подпрограмма обратного вызова, вызываемая при изменении размера окна Значение NULL отключает изменение окна.

### <a name="return-values"></a>Возвращаемые значения
- **NX_SUCCESS** (0x00) — подпрограмма обратного вызова установлена в сокете.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимые указатели.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.


### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

Включение компонента UDP в NetX

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба включает компонент UDP в NetX. После включения приложение может отправлять и принимать датаграммы UDP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение UDP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_ALREADY_ENABLED** (0x15) — этот компонент уже включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>См. также:

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

Поиск следующего доступного UDP-порта

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Описание

Эта служба ищет свободный UDP-порт (без привязки), начиная с указанного приложением номера порта. Если достигнуто максимальное значение порта 0xFFFF, поиск начинается с самого начала. Если поиск завершен успешно, свободный порт возвращается в переменной, на которую указывает *free_port_ptr*.

*Если эта служба вызывается из другого потока, она может вернуть тот же порт. Чтобы предотвратить такое состояние гонки, приложение может защитить эту службу и привязку сокета мьютексом.*

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **port**: номер порта, с которого начинается поиск (от 1 до 0xFFFF)
- **free_port_ptr**: указатель на место назначения для возвращаемой переменной со свободным портом


### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — поиск свободного порта успешно завершен.
- **NX_NO_FREE_PORTS** (0x45) — нет свободного порта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.
- **NX_INVALID_PORT** (0x46) — указан недопустимый номер порта.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

Получение сведений о действиях UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола UDP для указанного экземпляра IP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **udp_packets_sent**: указатель на место назначения для общего числа отправленных UDP-пакетов
- **udp_bytes_sent**: указатель на место назначения для общего числа отправленных по UDP байтов
- **udp_packets_received**: указатель на место назначения для общего числа полученных UDP-пакетов
- **udp_bytes_received**: указатель на место назначения для общего числа полученных по UDP байтов
- **udp_invalid_packets**: указатель на место назначения для общего числа недопустимых UDP-пакетов
- **udp_receive_packets_dropped**: указатель на место назначения для общего числа полученных и отброшенных UDP-пакетов
- **udp_checksum_errors**: указатель на место назначения для общего числа UDP-пакетов с ошибками контрольной суммы

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений UDP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.


### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Извлечение параметров сети из UDP-пакета

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Описание

Эта служба извлекает параметры сети, такие как IP-адрес, номер порта однорангового узла, тип протокола (всегда возвращается тип UDP) из пакета, полученного через входящий интерфейс.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет
- **ip_address**: указатель на IP-адрес отправителя
- **protocol**: указатель на протокол (UDP)
- **port**: указатель на номер порта отправителя
- **interface_index**: указатель на индекс интерфейса приема

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные интерфейса пакета успешно извлечены.
- **NX_INVALID_PACKET** (0x12) — пакет не содержит IP-кадр.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Привязка сокета UDP к UDP-порту

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба привязывает ранее созданный сокет UDP к указанному UDP-порту. Допустимый диапазон сокетов UDP — от 0 до 0xFFFF. Если запрошенный номер порта привязан к другому сокету, эта служба ожидает в течение указанного времени, пока привязка сокета к номеру порта не будет отменена.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **port**: номер порта для привязки (от 1 до 0xFFFF) Если номер порта — NX_ANY_PORT (0x0000), экземпляр IP будет искать следующий свободный порт и использует его для привязки.
- **wait_option**: определяет поведение службы в случае, если порт уже привязан к другому сокету Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно привязан.
- **NX_ALREADY_BOUND** (0x22) — этот сокет уже привязан к другому порту.
- **NX_PORT_UNAVAILABLE** (0x23) — порт уже привязан к другому сокету.
- **NX_NO_FREE_PORTS** (0x45) — нет свободного порта.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_INVALID_PORT** (0x46) — указан недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

Получает число байтов, доступных для извлечения

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Описание

Эта служба получает число байтов, доступных для приема в указанном сокете UDP.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный сокет UDP
- **bytes_available**: указатель на место назначения для доступных байтов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение доступных байтов.
- **NX_NOT_SUCCESSFUL** (0x43) — сокет не привязан к порту.
- **NX_PTR_ERROR** (0x07) — недопустимые указатели.
- **NX_NOT_ENABLED** (0x14) — функция UDP не включена.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Отключение контрольной суммы для сокета UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает логику проверки контрольной суммы при отправке и получении пакетов через указанный сокет UDP. Если логика проверки контрольной суммы отключена, в поле контрольной суммы заголовка UDP загружается значение ноль для всех пакетов, отправляемых через этот сокет. Нулевое значение контрольной суммы в заголовке UDP сообщает получателю о том, что контрольная сумма для этого пакета не вычисляется.

Обратите внимание, что эта настройка не действует, если при получении и отправке UDP-пакетов определены параметры ***NX_DISABLE_UDP_RX_CHECKSUM** _ и _ *_NX_DISABLE_UDP_TX_CHECKSUM_** соответственно.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — проверка контрольной суммы для сокета успешно отключена.
- **NX_NOT_BOUND** (0x24) — сокет не привязан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймер

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Включение контрольной суммы для сокета UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба включает логику проверки контрольной суммы при отправке и получении пакетов через указанный сокет UDP. Контрольная сумма охватывает всю область данных UDP, а также псевдозаголовок IP.

Обратите внимание, что эта настройка не действует, если при получении и отправке UDP-пакетов определены параметры **NX_DISABLE_UDP_RX_CHECKSUM** и **NX_DISABLE_UDP_TX_CHECKSUM** соответственно.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — проверка контрольной суммы для сокета успешно включена.
- **NX_NOT_BOUND** (0x24) — сокет не привязан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймер

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create

Создание сокета UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a>Описание

Эта служба создает сокет UDP для указанного экземпляра IP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **socket_ptr**: указатель на новый управляющий блок сокета UDP
- **name**: имя приложения для этого сокета UDP
- **type_of_service** определяет тип службы для передачи. Допустимые значения:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragment** указывает, разрешена ли фрагментация IP-пакетов Если указано значение NX_FRAGMENT_OKAY (0x0), то фрагментация IP-пакетов разрешена. Если указано значение NX_DONT_FRAGMENT (0x4000), то фрагментация IP-пакетов отключена.
- **time_to_live** задает 8-разрядное значение, определяющее, сколько маршрутизаторов этот пакет может пройти перед тем, как будет отброшен Значение по умолчанию задается в NX_IP_TIME_TO_LIVE.
- **queue_maximum** определяет максимальное число датаграмм UDP, которое можно поставить в очередь для этого сокета После достижения предельного размера очереди для каждого нового пакета будет освобождаться самый старый UDP-пакет.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет UDP успешно создан.
- **NX_OPTION_ERROR** (0x0A) — недопустимый тип службы, параметр фрагментации или параметр времени существования.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса или сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_delete,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Удаление сокета UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее сокет UDP. Если сокет привязан к порту, сначала необходимо отменить привязку.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно удален.
- **NX_STILL_BOUND** (0x42) — сокет все еще привязан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Получение сведений о действиях сокета UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a>Описание

Эта служба получает сведения о действиях сокета UDP для указанного экземпляра сокета UDP.

*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **udp_packets_sent**: указатель на место назначения для общего числа отправленных через сокет UDP-пакетов
- **udp_bytes_sent**: указатель на место назначения для общего числа отправленных через сокет UDP байтов
- **udp_packets_received**: указатель на место назначения для общего числа полученных через сокет UDP-пакетов
- **udp_bytes_received**: указатель на место назначения для общего числа полученных через сокет UDP байтов
- **udp_packets_queued** Указатель на место назначения для общего числа UDP-пакетов, поставленных в очередь в сокете.
- **udp_receive_packets_dropped**: указатель на место назначения для общего числа UDP-пакетов, полученных и отброшенных для сокета из-за превышения размера очереди
- **udp_checksum_errors**: указатель на место назначения для общего числа UDP-пакетов с ошибками контрольной суммы в сокете

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение сведений о сокете UDP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Выбор номера порта, привязанного к сокету UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Описание

Эта служба получает номер порта, связанного с сокетом, что может быть полезно при поиске порта, выделенного NetX, если во время привязки сокета было указано значение NX_ANY_PORT.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **port_ptr**: указатель на место назначения для возвращаемого номера порта Допустимые номера портов — от 1 до 0xFFFF.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно привязан.
- **NX_NOT_BOUND** (0x24) — этот сокет не привязан к порту.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета или возвращаемого порта.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

Получение датаграммы из сокета UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает датаграмму UDP из указанного сокета. Если в указанном сокете в очереди нет датаграмм, вызывающий объект приостанавливает выполнение на основе указанного параметра ожидания.

*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **packet_ptr**: указатель на пакет датаграммы UDP
- **wait_option** определяет поведение службы в случае, если в этом сокете нет датаграмм в очереди Параметры ожидания определяются следующим образом.
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Уведомление приложения о каждом полученном пакете

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Описание

Эта служба задает указатель на функцию уведомления о получении с помощью функции обратного вызова, заданной приложением. Эта функция обратного вызова затем вызывается при каждом получении пакета через сокет. Если задан указатель NX_NULL, функция уведомления о получении отключена.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на сокет UDP
- **udp_receive_notify**: указатель на функцию обратного вызова приложения, вызываемую при получении пакета в сокете

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

Отправка датаграммы UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Описание

Эта служба отправляет датаграмму UDP через ранее созданный и привязанный сокет UDP. NetX находит локальный IP-адрес, подходящий в качестве исходного адреса, по IP-адресу назначения. Чтобы указать определенный интерфейс и исходный IP-адрес, приложение должно использовать службу **nx_udp_socket_interface_send**.

Обратите внимание, что эта служба возвращает управление немедленно, независимо от того, была ли датаграмма UDP успешно отправлена.

Сокет должен быть привязан к локальному порту.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **packet_ptr**: указатель на пакет датаграммы UDP
- **ip_address**: конечный IP-адрес
- **port**: допустимый конечный номер порта в диапазоне от 1 до 0xFFFF в порядке байтов узла

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — отправка через сокет UDP успешно выполнена.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес сервера.
- **NX_UNDERFLOW** (0x02) — недостаточно места для заголовка UDP в пакете.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — протокол UDP не включен.
- **NX_INVALID_PORT** (0x46) — номер порта не входит в допустимый диапазон.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

Отправка датаграммы через сокет UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a>Описание

Эта служба отправляет датаграмму UDP через ранее созданный и привязанный сокет UDP и через сетевой интерфейс с IP-адресом, указанным в качестве исходного. Обратите внимание, что эта служба возвращает управление немедленно, независимо от того, была ли датаграмма UDP успешно отправлена.

### <a name="parameters"></a>Параметры

- **socket_ptr**: сокет для передачи пакета
- **packet_ptr**: указатель на передаваемый пакет
- **ip_address**: конечный IP-адрес, на который нужно отправить пакет
- **port**: конечный порт
- **address_index**: индекс адреса, связанного с интерфейсом, через который нужно отправить пакет

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет успешно отправлен.
- **NX_NOT_BOUND** (0x24) — сокет не привязан к порту.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_NOT_ENABLED** (0x14) — обработка UDP не включена.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс адреса.
- **NX_INVALID_PORT** (0x46) — номер порта превышает максимальный.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Отмена привязки сокета UDP к UDP-порту

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Описание

Эта служба освобождает привязку между сокетом UDP и UDP-портом. Все полученные пакеты, хранящиеся в очереди приема, освобождаются в рамках операции отмены привязки.

Если есть другие потоки, ожидающие привязки другого сокета к освобождаемому порту, к освобожденному порту привязывается первый приостановленный поток.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — привязка сокета успешно отменена.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Извлечение IP-адреса и порта отправки из датаграммы UDP

### <a name="prototype"></a>Прототип

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Описание

Эта служба извлекает IP-адрес и номер порта отправителя из заголовков IP и UDP в указанной датаграмме UDP.

### <a name="parameters"></a>Параметры

- **packet_ptr** Указатель на пакет датаграммы UDP.
- **ip_address**: допустимый указатель на возвращаемую переменную с IP-адресом
- **port**: допустимый указатель на возвращаемую переменную с портом

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное извлечение исходного IP-адреса и порта.
- **NX_INVALID_PACKET** (0x12) — указан недопустимый пакет.
- **NX_PTR_ERROR** (0x07) — недопустимый пакет, IP-адрес или порт назначения.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a>См. также:

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind