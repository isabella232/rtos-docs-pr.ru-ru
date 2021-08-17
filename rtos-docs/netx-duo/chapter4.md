---
title: Глава 4. Описание служб NetX Duo для ОСРВ Azure
description: В этой главе содержится описание всех служб NetX Duo для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d28ca64a6a655bb3f1ad10c563450a0e65b645a1e1a2a464c4137f9a999815bc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785028"
---
# <a name="chapter-4---description-of-azure-rtos-netx-duo-services"></a>Глава 4. Описание служб NetX Duo для ОСРВ Azure

В этой главе содержится описание всех служб NetX Duo для ОСРВ Azure в алфавитном порядке. Имена служб составлены таким образом, что все аналогичные службы объединены по группам. Например, все службы ARP находятся в начале этой главы. 

Для поддержки протоколов и операций на основе IPv6 в NetX Duo появились многочисленные новые службы. Имена служб с поддержкой IPv6 в NetX Duo начинаются с префикса ***nxd**, указывающего, что они предназначены для работы с двумя стеками IPv4 и IPv6.

Существующие службы в NetX полностью поддерживаются в NetX Duo. Приложения NetX можно перенести в NetX Duo с минимальными усилиями.

> [!NOTE]
> *Обратите внимание, что сокет API, совместимый с BSD, доступен для устаревшего кода приложения, который не может использовать все преимущества высокопроизводительного API NetX Duo. Дополнительные сведения о сокете API, совместимом с BSD, см. в приложении D*.

В разделе "Возвращаемые значения" каждого описания значения, выделенные **полужирным шрифтом**, не затрагиваются параметром NX_DISABLE_ERROR_CHECKING, используемым для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены. В разделах "Допустимые источники" указывается, откуда можно вызывать каждую службу NetX Duo.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate   
Делает недействительными все динамические записи в кэше ARP.

### <a name="prototype"></a>Прототип     

```c
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
нет

### <a name="example"></a>Пример

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);

/* If status is NX_SUCCESS the dynamic ARP entries were
   successfully invalidated. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set  
Задание динамической записи ARP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Setup a dynamic ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
                                  0x1022, 0x1234);

/* If status is NX_SUCCESS, there is now a dynamic mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   10:22:00:00:12:34. */
```
### <a name="see-also"></a>См. также: 

- nx_arp_dynamic_entries_invalidate
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_enable"></a>nx_arp_enable  
Включение протокола ARP

### <a name="prototype"></a>Прототип    

```c
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory,
    ULONG arp_cache_size);
```

### <a name="description"></a>Описание

Эта служба инициализирует компонент ARP определенного экземпляра IP в NetX Duo. Инициализация ARP включает в себя настройку кэша ARP и различных подпрограмм обработки ARP, необходимых для отправки и получения сообщений ARP.

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
нет

### <a name="example"></a>Пример

```c
/* Enable ARP and supply 1024 bytes of ARP cache memory for
   previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);

/* If status is NX_SUCCESS, ARP was successfully enabled for this IP
instance.*/
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_entry_delete"></a>nx_arp_entry_delete   
Удаление записи ARP

### <a name="prototype"></a>Прототип  

```c
UINT nx_arp_entry_delete(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Описание

Эта служба удаляет запись ARP для заданного IP-адреса из внутренней таблицы ARP, соответствующей IP-адресу.

### <a name="parameters"></a>Параметры  

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **ip_address** — запись ARP с указанным IP-адресом должна быть удалена.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное включение ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) — не удается найти запись с указанным IP-адресом.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель на кэш ЦП.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_IP_ADDRESS_ERROR** (0x21) — указан недопустимый IP-адрес.

### <a name="allowed-from"></a>Допустимые источники  
Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение  
Нет

### <a name="example"></a>Пример

```c
/* Delete the ARP entry with the IP address 1.2.3.4. */
status = nx_arp_entry_delete(&ip_0, IP_ADDRESS(1, 2, 3, 4));

/* If status is NX_SUCCESS, ARP entry with the specified IP address
   is deleted.*/
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send   
Отправка необязательного запроса ARP

### <a name="prototype"></a>Прототип  

```c
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler)(NX_IP *ip_ptr, NX_PACKET *packet_ptr));
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

нет

### <a name="example"></a>Пример

```
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully
   sent. */
```

### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find
Обнаружение физического аппаратного адреса по IP-адресу

### <a name="prototype"></a>Прототип  

```c
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

нет

### <a name="example"></a>Пример

```c
/* Search for the hardware address associated with the IP address of
   1.2.3.4 in the ARP cache of the previously created IP
   Instance 0. */
status = nx_arp_hardware_address_find(&ip_0, IP_ADDRESS(1,2,3,4),
                                      &physical_msw,
                                      &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
   physical_lsw contain the hardware address.*/
```   
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_info_get"></a>nx_arp_info_get
Получение сведений о действиях ARP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях ARP для соответствующего экземпляра IP.

> [!NOTE]
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

нет

### <a name="example"></a>Пример

```c
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(&ip_0, &arp_requests_sent,
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

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find
Нахождение IP-адреса по физическому адресу

### <a name="prototype"></a>Прототип  

```c
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

нет

### <a name="example"></a>Пример

```c
/* Search for the IP address associated with the hardware address of
   0x0:0x01234 in the ARP cache of the previously created IP
   Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
   associated IP address. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete
Удаление всех статических записей ARP

### <a name="prototype"></a>Прототип  

```c
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

нет

### <a name="example"></a>Пример

```c
/* Delete all the static ARP entries for IP Instance 0, assuming
   "ip_0" is the NX_IP structure for IP Instance 0. */
status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
   have been deleted. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create
Создание статического IP-адреса для аппаратного сопоставления в кэше ARP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Create a static ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   0x00:0x1234. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete 
Удаление статического IP-адреса для сопоставления оборудования в кэше ARP

### <a name="prototype"></a>Прототип  

```c
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
- **ip_address** — IP-адрес, сопоставленный статически.
- **physical_msw** — старшие 16 бит (47–**32) физического адреса, сопоставленного статически.
- **physical_lsw** — младшие 32 бита (31–**0) физического адреса, сопоставленного статически.

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

```c
/* Delete a static ARP entry on the previously created IP
   instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, the previously created static ARP entry
   was successfully deleted. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_icmp_enable"></a>nx_icmp_enable
Включение протокола ICMP

### <a name="prototype"></a>Прототип  

```c
UINT nx_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает компонент ICMP для указанного экземпляра IP. Компонент ICMP отвечает за обработку сообщений об ошибках в Интернете, а также запросов и ответов проверки связи. 

> [!IMPORTANT]  
> *Эта служба включает только протокол ICMP для службы IPv4. Для включения и ICMPv4, и ICMPv6 в приложениях должна использоваться служба **nxd_icmp_enable***.

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

```c
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```
### <a name="see-also"></a>См. также:

- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get
Получение сведений о действиях ICMP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях протокола ICMP для указанного экземпляра IP.

> [!NOTE]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **pings_sent**: указатель места назначения для общего числа отправленных проверок связи.
- **ping_timeouts**: указатель места назначения для общего числа таймаутов проверки связи.
- **ping_threads_suspended** — указатель на назначение общего числа потоков, приостановленных по запросам проверки связи.
- **ping_responses_received** — указатель на назначение общего числа полученных ответов проверки связи.
- **icmp_checksum_errors** — указатель на назначение общего числа ошибок контрольной суммы протокола ICMP.
- **icmp_unhandled_messages** — указатель на назначение общего числа необработанных сообщений ICMP.

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

```c
/* Retrieve ICMP information from previously created IP
   instance ip_0. */
status = nx_icmp_info_get(&ip_0, &pings_sent, &ping_timeouts,
                          &ping_threads_suspended,
                          &ping_responses_received,
                          &icmp_checksum_errors,
                          &icmp_unhandled_messages);
/* If status is NX_SUCCESS, ICMP information was retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_icmp_enable
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_ping"></a>nx_icmp_ping  
Отправка запроса проверки связи на указанный IP-адрес

### <a name="prototype"></a>Прототип  

```c
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба отправляет запрос проверки связи по указанному IP-адресу и ожидает сообщение ответа проверки связи в течение заданного количества времени. Если ответ не получен, возвращается ошибка. В противном случае в переменной, на которую указывает response_ptr, возвращается полное ответное сообщение. 

Для отправки запроса проверки связи на IPv6-адрес назначения в приложениях должна использоваться служба ***nxd_icmp_ping** _ или _ *_nxd_icmp_source_ping_**.

> [!WARNING]  
> *Если возвращается NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **ip_address** — IP-адрес в порядке байтов узла для проверки связи.
- **data** — указатель на область данных для сообщения проверки связи.
- **data_size** — число байтов в данных проверки связи.
- **response_ptr** — указатель на указатель пакета, в котором нужно вернуть ответное сообщение проверки связи.
- **wait_option** — определяет количество тактов таймера ThreadX для ожидания ответа проверки связи. Параметры ожидания определяются следующим образом:

| Параметр wait            | Значение                           |
| -----------------------|---------------------------------|
| NX_NO_WAIT             | (0x00000000)                    |
| значение времени ожидания в тактах | (от 0x00000001 до 0xFFFFFFFE) |
| NX_WAIT_FOREVER        | 0xFFFFFFFF                      |

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

```c
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

- nx_icmp_enable
- nx_icmp_info_get
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_igmp_enable"></a>nx_igmp_enable
Включение протокола IGMP

### <a name="prototype"></a>Прототип  

```c
UINT nx_igmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает компонент IGMP для указанного экземпляра IP. Компонент IGMP отвечает за поддержку операций управления группами многоадресной рассылки IP-адресов.

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

```c
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get
Получение сведений о действиях IGMP

### <a name="prototype"></a>Прототип  

```c
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```
### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола IGMP для указанного экземпляра IP.

> [!IMPORTANT]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

```c
/* Retrieve IGMP information from previously created IP Instance ip_0. */
status = nx_igmp_info_get(&ip_0, &igmp_reports_sent,
                          &igmp_queries_received,
                          &igmp_checksum_errors,
                          &current_groups_joined);

/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable
Отключение петлевого адреса IGMP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Disable IGMP loopback for all subsequent multicast groups
   joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable
Включение петлевого адреса IGMP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Enable IGMP loopback for all subsequent multicast
   groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join
Присоединение экземпляра IP к указанной группе многоадресной рассылки через интерфейс

### <a name="prototype"></a>Прототип  

```c
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба присоединяет экземпляр IP к указанной группе многоадресной рассылки через указанный сетевой интерфейс. Внутренний счетчик поддерживается для наблюдения за тем, сколько раз была присоединена одна и та же группа. После присоединения к группе многоадресной рассылки компонент IGMP разрешит получение IP-пакетов с этим адресом группы через указанный сетевой интерфейс, а также сообщает маршрутизаторам, что этот IP-адрес является участником этой группы рассылки. Сообщения о присоединении к группам IGMP, выходе из них и отчетах также отправляются через указанный сетевой интерфейс. Чтобы при присоединении к группе многоадресной рассылки IPv4 не отправлялся отчет о членстве в группах IGMP, в приложении должна использоваться служба ***nx_ipv4_multicast_interface_join***.

### <a name="parameters"></a>Параметры 

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **group_address** — адрес группы многоадресной рассылки IP-адресов класса D для присоединения в порядке байтов узла.
- **interface_index** — индекс интерфейса, подключенного к экземпляру NetX Duo.

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

```c
/* Previously created IP Instance joins the multicast group
   244.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
                                 (&ip IP_ADDRESS(244,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```   
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_leave"></a>nx_igmp_multicast_interface_leave
Выход из указанной группы многоадресной рассылки через интерфейс

### <a name="prototype"></a>Прототип  

```c
UINT nx_igmp_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба выполняет выход из указанной группы многоадресной рассылки через указанный сетевой интерфейс. Внутренний счетчик поддерживается для отслеживания количества присоединений к одной и той же группе. После выхода из группы многоадресной рассылки компонент IGMP будет отсылать соответствующий отчет о членстве и может покинуть группу, если из этого узла нет участников. Чтобы при выходе из группы многоадресной рассылки IPv4 не отправлялся отчет о членстве в группах IGMP, в приложении должна использоваться служба ***nx_ipv4_multicast_interface_leave***.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **group_address** — адрес группы многоадресной рассылки IP-адресов класса D, из которой необходимо выйти. IP-адрес указан в порядке байтов узла.
- **interface_index** — индекс интерфейса, подключенного к экземпляру NetX Duo.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.
- **NX_ENTRY_NOT_FOUND** (0x16) — указанный адрес группы многоадресной рассылки не найден в локальной таблице многоадресной рассылки.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес.
- **NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — указанный адрес группы многоадресной рассылки не является допустимым адресом класса D.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — поддержка многоадресной рассылки IP не включена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Leave the multicast group 244.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_leave
                                (&ip IP_ADDRESS(244,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join
Присоединение экземпляра IP к указанной группе многоадресной рассылки

### <a name="prototype"></a>Прототип  

```c
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Описание

Эта служба присоединяет экземпляр IP-адреса к указанной группе многоадресной рассылки. Внутренний счетчик поддерживается для наблюдения за тем, сколько раз была присоединена одна и та же группа. Драйвер получает команду отправить отчет IGMP, если это первый запрос на присоединение в сети, указывающий на намерение узла присоединиться к группе. После присоединения компонент IGMP разрешит прием IP-пакетов с этим адресом группы и сообщит маршрутизаторам, что этот IP-адрес является членом этой группы многоадресной рассылки. Чтобы при присоединении к группе многоадресной рассылки IPv4 не отправлялся отчет о членстве в группах IGMP, в приложении должна использоваться служба ***nx_ipv4_multicast_interface_join***.

> [!NOTE]  
> *Чтобы присоединиться к группе многоадресной рассылки на непервичном устройстве, используйте службу **nx_igmp_multicast_interface_join.***

### <a name="parameters"></a>Параметры

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

```c
/* Previously created IP Instance ip_0 joins the multicast group
   224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully
   joined the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave
Экземпляр IP покидает указанную группу многоадресной рассылки

### <a name="prototype"></a>Прототип  

```c
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Описание

Эта служба приводит к выходу экземпляра IP из указанной группы многоадресной рассылки, если количество запросов на выход соответствует количеству запросов на присоединение. В противном случае число внутренних присоединений просто уменьшается. Чтобы при выходе из группы многоадресной рассылки IPv4 не отправлялся отчет о членстве в группах IGMP, в приложении должна использоваться служба ***nx_ipv4_multicast_interface_leave***.

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

```c
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
   the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy
Уведомление приложения при изменении IP-адреса

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *, VOID *),
    VOID *additional_info);
```
### <a name="description"></a>Описание

Эта служба регистрирует функцию уведомления приложения, которая вызывается при каждом изменении адреса IPv4.

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

нет

### <a name="example"></a>Пример

```c
/* Register the function "my_ip_changed" to be called whenever the
   IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed,
                                      NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
   called whenever the IP address changes. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_get"></a>nx_ip_address_get
Получение IPv4-адреса и маски сети

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Описание

Эта служба получает IPv4-адрес и маску подсети основного сетевого интерфейса.

> [!IMPORTANT]   
> * Чтобы получить сведения о вторичном устройстве, используйте службу **nx_ip_interface_address_get***.

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

нет

### <a name="example"></a>Пример

```c
/* Get the IP address and network mask from the previously created
   IP Instance ip_0. */
status = nx_ip_address_get(&ip_0, &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
   network_mask contain the IP and network mask respectively. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_set"></a>nx_ip_address_set
Задание IPv4-адреса и маски сети

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Описание

Эта служба задает IPv4-адрес и маску сети для основного сетевого интерфейса.

> [!IMPORTANT]  
> * Чтобы задать IP-адрес и маску сети для вторичного устройства, используйте службу **nx_ip_interface_address_set***.

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

нет

### <a name="example"></a>Пример

```c
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00 for
   the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4),
                           0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address of
   1.2.3.4 and a network mask of 0xFFFFFF00. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_auxiliary_packet_pool_set"></a>nx_ip_auxiliary_packet_pool_set
Настройка вспомогательного пула пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_auxiliary_packet_pool_set(
    NX_IP *ip_ptr,
    NX_PACKET_POOL *aux_pool);
```
### <a name="description"></a>Описание

Эта служба настраивает вспомогательный пул пакетов в экземпляре IP. В системе с ограниченным объемом памяти пользователь может увеличить эффективность памяти, создав пул пакетов по умолчанию с размером пакета MTU и вспомогательный пул пакетов с меньшим размером пакета для потока IP-адресов, который будет передавать небольшие пакеты. Рекомендуемый размер пакета для вспомогательного пула составляет 256 байт при условии, что включены протоколы IPv6 и IPsec.

По умолчанию экземпляр IP не принимает вспомогательный пул пакетов. Чтобы включить эту функцию, необходимо задать значение *NX_DUAL_PACKET_POOL_ENABLE* при компиляции библиотеки NetX Duo.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **aux_pool** — вспомогательный пул пакетов, который необходимо настроить для экземпляра IP.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — IP-адрес успешно задан.
- **NX_NOT_SUPPORTED** (0x4B) — функция пула двойных пакетов не компилируется в библиотеке.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес или указатель пула.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение  

Нет

### <a name="example"></a>Пример

```c
#define SMALL_PAYLOAD_SIZE 256
NX_PACKET small_pool;

nx_packet_pool_create(&small_pool, "small pool", SMALL_PAYLOAD_SIZE,
                       small_pool_memory_ptr, small_pool_size);

/* Add the small packet pool to the IP instance. */
status = nx_ip_auxiliary_packet_pool_set(&ip_0, &small_pool);

/* If status is NX_SUCCESS, the IP instance now is able to use the
   small pool for transmitting small datagram. */
```
### <a name="see-also"></a>См. также:

- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_ip_create"></a>nx_ip_create
Создание экземпляра IP

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, ULONG ip_address,
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
- **network_mask** — маска для отделения сетевой части IP-адреса для подсетей и суперсетей.
- **default_pool** — указатель на блок управления ранее созданного пула пакетов NetX Duo.
- **ip_network_driver** — предоставленный пользователем драйвер сети, используемый для отправки и получения IP-пакетов.
- **memory_ptr**: указатель на область памяти для стека вспомогательного потока IP
- **memory_size**: число байтов в области памяти для стека вспомогательного потока IP
- **priority**: приоритет вспомогательного потока IP

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное создание экземпляра IP.
- **NX_NOT_IMPLEMENTED** (0x4A) — библиотека NetX Duo настроена неправильно.
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

```c
/* Create an IP instance with an IP address of 1.2.3.4 and a network
   mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
   point of the application specific network driver and the
   "stack_memory_ptr" specifies the start of a 1024 byte memory
   area that is used for this IP instance’s helper thread. */
status = nx_ip_create(&ip_0, "NetX IP Instance ip_0",
                      IP_ADDRESS(1, 2, 3, 4),
                      0xFFFFFF00UL, &pool_0, ethernet_driver,
                      stack_memory_ptr, 1024, 1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_delete"></a>nx_ip_delete
Удаление ранее созданного экземпляра IP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>См. также: 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command
Отправка команды сетевому драйверу

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_driver_direct_command
    (NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Описание

Эта служба предоставляет интерфейс для прямого взаимодействия с драйвером основного сетевого интерфейса приложения, указанным во время вызова ***nx_ip_create***. Можно использовать команды для конкретного приложения, если их числовые значения больше или равны NX_LINK_USER_COMMAND.

> [!IMPORTANT]  
> *Чтобы отправить команду дополнительному устройству, используйте службу **nx_ip_driver_interface_direct_command**.*

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

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(&ip_0, NX_LINK_GET_STATUS,
                                     &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command
Отправка команды сетевому драйверу

### <a name="prototype"></a>Прототип  

```c
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

нет

### <a name="example"></a>Пример

```c
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

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable  
Отключение переадресации IP-пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба отключает пересылку IP-пакетов внутри IP-компонента NetX Duo. При создании задачи IP эта служба автоматически отключается.

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

```c
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>См. также:  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable
Включение переадресации IP-пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает пересылку IP-пакетов внутри IP-компонента NetX Duo. При создании задачи IP эта служба автоматически отключается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное включение переадресации IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>См. также: 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable
Отключение фрагментации IP-пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба отключает возможность фрагментации и повторной сборки IP-пакетов IPv4 и IPv6. Пакеты, ожидающие повторной сборки, освобождаются. При создании задачи IP эта служба автоматически отключается.

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

нет

### <a name="example"></a>Пример

```c
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
   previously created IP instance. */
```

### <a name="see-also"></a>См. также:  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable
Включение фрагментации IP-пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает возможность фрагментации и повторной сборки IP-пакетов IPv4 и IPv6. При создании задачи IP эта служба автоматически отключается.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное включение фрагментации IP-пакетов.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функции фрагментации IP не компилированы в NetX Duo.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>См. также:  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_gateway_address_clear"></a>nx_ip_gateway_address_clear
Очистка адреса шлюза IPv4

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_gateway_address_clear(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба очищает адрес шлюза IPv4, настроенный в экземпляре. Для очистки IPv6-адреса по умолчанию, внешнего по отношению к экземпляру IP, в приложениях должна использоваться служба ***nxd_ipv6_default_router_delete***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешная очистка адреса шлюза IP.
- **NX_PTR_ERROR** (0x07) — недопустимый блок управления IP-адресом.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Clear the gateway address of IP instance. */
status = nx_ip_gateway_address_clear(&ip_0);

/* If status == NX_SUCCESS, the gateway address was successfully
   cleared from the IP instance. */
```
### <a name="see-also"></a>См. также:

-nx_ip_gateway_address_get -nx_ip_gateway_address_set -nx_ip_info_get -nx_ip_static_route_add -nx_ip_static_route_delete -nxd_ipv6_default_router_add -nxd_ipv6_default_router_delete -nxd_ipv6_default_router_entry_get -nxd_ipv6_default_router_get -nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_get"></a>nx_ip_gateway_address_get
Получение адреса шлюза IPv4

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_gateway_address_get(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Описание

Эта служба получает адрес шлюза IPv4, настроенный в экземпляре IP.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **ip_address** — указатель на память, в которой хранится адрес шлюза

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение 
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP или новый указатель на IP-адрес.
- **NX_NOT_FOUND** (0x4E) — не найден адрес шлюза
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
ULONG ip_address;

/* Get the gateway address of IP instance. */
status = nx_ip_gateway_address_get(&ip_0, &ip_address);

/* If status == NX_SUCCESS, the gateway address was successfully
   got. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set
Задание IP-адреса шлюза

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Описание

Эта служба задает IP-адрес шлюза IPv4. Весь трафик, исходящий из сети, направляется в этот шлюз для передачи. Шлюз должен быть доступен напрямую через один из сетевых интерфейсов. Чтобы настроить адрес шлюза IPv6, используйте службу ***nxd_ipv6_default_router_add.*** 

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

нет

### <a name="example"></a>Пример

```c
/* Setup the Gateway address for previously created IP
   Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99);

/* If status is NX_SUCCESS, all out-of-network send requests are
   routed to 1.2.3.99. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_info_get"></a>nx_ip_info_get
Получение сведений о действиях IP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях протокола IP для указанного экземпляра IP.

> [!NOTE]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

```c
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

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get
Получение IP-адреса интерфейса

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Описание

Эта служба получает адрес IPv4 указанного сетевого интерфейса. Для получения IPv6-адреса в приложении должна использоваться служба ***nxd_ipv6_address_get***.

> [!CAUTION]  
> *Если указанное устройство не является первичным, его необходимо предварительно подключить к экземпляру IP*.

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

```c
#define INTERFACE_INDEX 1

/* Get device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
                                     &ip_address,
                                     &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
   retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_mapping_configure"></a>nx_ip_interface_address_mapping_configure
Указание необходимости сопоставления адресов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_address_mapping_configure(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT mapping_needed);
```
### <a name="description"></a>Описание

Эта служба определяет, требуется ли сопоставление IP-адреса с MAC-адресом для указанного сетевого интерфейса. Эта служба обычно вызывается из драйвера устройства интерфейса для уведомления стека IP о том, требуется ли для базового интерфейса сопоставление IP-адреса с MAC-адресом на уровне 2.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса
- **mapping_needed** NX_TRUE — требуется сопоставление адресов, NX_FALSE — не требуется сопоставление адресов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная настройка
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс устройства
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Thread

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
UCHAR mapping_needed = NX_TRUE;

/* Configure address mapping needed specified interface. */
status = nx_ip_interface_address_mapping_configure(&ip_0,
                                             PRIMARY_INTERFACE,
                                             mapping_needed);

/* If status == NX_SUCCESS, the address mapping needed was
   successfully configured. */
```

### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set
Задание IP-адреса и маски сети интерфейса

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Описание

Эта служба задает IPv4-адрес и маску сети для указанного интерфейса IP. Для настройки адреса интерфейса IPv6 в приложении должна использоваться служба ***nxd_ipv6_address_set***. 
 
> [!WARNING]  
> *Указанный интерфейс должен быть предварительно подключен к экземпляру IP*. 

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **interface_index** — индекс интерфейса, подключенного к экземпляру NetX Duo.
- **ip_address** — новый IP-адрес сетевого интерфейса.
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

```c
#define INTERFACE_INDEX 1

/* Set device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
                                     ip_address,
                                     network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
   successfully set. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach
Подключение сетевого интерфейса к экземпляру IP

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)(struct NX_IP_DRIVER_STRUCT *));
```
### <a name="description"></a>Описание

Эта служба добавляет физический сетевой интерфейс к интерфейсу IP. Обратите внимание, что экземпляр IP создается с основным интерфейсом, поэтому каждый следующий интерфейс является дополнительным для него. Общее число сетевых интерфейсов, подключенных к экземпляру IP (включая основной интерфейс), не может превышать **NX_MAX_PHYSICAL_INTERFACES**.

Если поток IP еще не запущен, дополнительные интерфейсы будут инициализированы в процессе запуска потока IP, который инициализирует все физические интерфейсы.

Если поток IP еще не запущен, дополнительный интерфейс инициализируется службой ***nx_ip_interface_attach***.

> [!WARNING]  
> *ip_ptr должен указывать на допустимую структуру IP NetX Duo. **NX_MAX_PHYSICAL_INTERFACES** необходимо настроить для количества сетевых интерфейсов экземпляра IP. Значение по умолчанию — 1*.

### <a name="parameters"></a>Параметры 

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **interface_name**: указатель на строку с именем интерфейса
- **ip_address**: IP-адрес устройства в порядке байтов узла
- **network_mask**: маска сети устройства в порядке байтов узла
- **ip_link_driver**: драйвер Ethernet для интерфейса

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — запись добавлена в таблицу статической маршрутизации.
- **NX_NO_MORE_ENTRIES** (0x17) — максимальное число интерфейсов. Превышено значение NX_MAX_PHYSICAL_INTERFACES. Если включен протокол IPv6, эта ошибка может также указывать на то, что у драйвера может быть недостаточно ресурсов для работы с многоадресными операциями IPv6.
- **NX_DUPLICATED_ENTRY** (0x52) — указанный IP-адрес уже используется в этом экземпляре IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимые входные данные IP-адреса.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
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

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_get"></a>nx_ip_interface_capability_get
Получение возможности оборудования интерфейса

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_capability_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *interface_capability_flag);
```
### <a name="description"></a>Описание

Эта служба получает флаг возможности из указанного сетевого интерфейса. Чтобы использовать эту службу, необходимо выполнить сборку библиотеки NetX Duo с включенным параметром ***NX_ENABLE_INTERFACE_CAPABILITY***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса.
- **interface_capability_flag** — указатель на пространство в памяти для флага возможности.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешно получена информация о возможности интерфейса.
- **NX_NOT_SUPPORTED** (0x4B) — возможность интерфейса не поддерживается в этой сборке.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP или недопустимый указатель на флаг возможности.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
ULONG       capability_flag;

/* Get the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_get(&ip_0,
                                        PRIMARY_INTERFACE,
                                        &capability_flag);

/* If status == NX_SUCCESS, the capability flag from the primary
   interface was successfully retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_set"></a>nx_ip_interface_capability_set
Задание флага возможности оборудования

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_capability_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG interface_capability_flag);
```                           
### <a name="description"></a>Описание

С помощью этой службы драйвер сетевого устройства настраивает флаг возможности для указанного сетевого интерфейса. Чтобы использовать эту службу, необходимо выполнить компиляцию библиотеки NetX Duo с заданным параметром ***NX_ENABLE_INTERFACE_CAPABILITY***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса.
- **interface_capability_flag** — флаг возможности для выходных данных.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешно задан флаг возможности оборудования интерфейса.
- **NX_NOT_SUPPORTED** (0x4B) — возможность интерфейса не поддерживается в этой сборке.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса. 
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP. 
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
ULONG capability_flag = \
                 NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM |\
                 NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM;
UINT device_index = 0;

/* Set the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_set(&ip_0,
                                        PRIMARY_INTERFACE,
                                        capability_flag);

/* If status == NX_SUCCESS, the hardware capability flag was
   successfully set. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_detach"></a>nx_ip_interface_detach
Отключение указанного интерфейса от экземпляра IP

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr, 
    UINT index);
```
### <a name="description"></a>Описание

Эта служба отключает указанный IP-интерфейс от экземпляра IP. После отключения интерфейса все подключенные TCP-сокеты закрываются, а записи кэша ND и ARP для этого интерфейса удаляются из соответствующих таблиц. Членства в IGMP для этого интерфейса удаляются.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **index** — индекс удаляемого интерфейса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — физический интерфейс успешно удален.
- **NX_INVALID_INTERFACE** (0x4C) — указан недопустимый сетевой интерфейс.
- **NX_PTR_ERROR** (0x07) — недопустимые указатели.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define INTERFACE_INDEX 1

/* Detach interface 1. */
status = nx_ip_interface_detach(&IP_0, INTERFACE_INDEX);

/* If status is NX_SUCCESS the interface is successfully detached
   from the IP instance. */
```

### <a name="see-also"></a>См. также:  

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get
Получение параметров сетевого интерфейса

### <a name="prototype"></a>Прототип  

```c
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

> [!WARNING]  
> *Указатель ip_ptr должен указывать на допустимую структуру IP в NetX Duo. Указанный интерфейс, если он не является основным, должен быть предварительно подключен к экземпляру IP*.

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

```c
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

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_mtu_set"></a>nx_ip_interface_mtu_set
Задание значения MTU сетевого интерфейса

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_mtu_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG mtu_size);
```
### <a name="description"></a>Описание

С помощью этой службы драйвер устройства настраивает значение MTU IP для указанного сетевого интерфейса.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса
- **mtu_size** — размер MTU IP.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — значение MTU IP успешно задано.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
ULONG       mtu_size = 1500;

/* Set the MTU size of specified interface. */
status = nx_ip_interface_mtu_set(&ip_0,
                                 PRIMARY_INTERFACE, mtu_size);

/* If status == NX_SUCCESS, the MTU size was successfully set. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_get"></a>nx_ip_interface_physical_address_get
Получение физического адреса сетевого устройства

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_physical_address_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Описание

Эта служба получает физический адрес сетевого интерфейса из экземпляра IP.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса.
- **physical_msw** — указатель на место назначения для старших 16 бит MAC-адреса устройства.
- **physical_lsw** — указатель на место назначения для младших 32 бит MAC-адреса устройства.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное получение
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP или указатель на физический адрес.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
ULONG   physical_msw;
ULONG   physical_lsw;

/* Get the physical address of specified interface. */
status = nx_ip_interface_physical_address_get(&ip_0,
                                              PRIMARY_INTERFACE,
                                              &physical_msw,
                                              &physical_lsw);

/* If status == NX_SUCCESS, the physical address was successfully
   retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_set"></a>nx_ip_interface_physical_address_set
Задание физического адреса для указанного сетевого интерфейса

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_interface_physical_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT update_driver);
```
### <a name="description"></a>Описание

С помощью этой службы приложение или драйвер устройства настраивает физический адрес MAC-адреса указанного сетевого интерфейса. Новый MAC-адрес применяется к блоку управления структуры интерфейса. Если установлен флаг ***update_driver***, то выдается команда на уровне драйвера, поэтому драйвер устройства может обновить свой MAC-адрес, запрограммированный в контроллере Ethernet.

Обычно эта служба вызывается из драйвера устройства интерфейса на этапе инициализации для уведомления стека IP MAC-адреса. В этом случае не следует устанавливать флаг ***update_driver***.

Эту подпрограмму также можно вызвать из пользовательского приложения для перенастройки MAC-адреса интерфейса во время выполнения. В этом случае следует установить флаг ***update_driver***, чтобы новый MAC-адрес можно было применить к драйверу устройства.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса
- **physical_msw** — указатель на место назначения для старших 16 бит MAC-адреса устройства.
- **physical_lsw** — указатель на место назначения для младших 32 бит MAC-адреса устройства.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешно задано.
- **NX_UNHANDLED_COMMAND** (0x4B) — команда не распознана драйвером.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
ULONG       physical_msw = 0x00CF;
ULONG       physical_lsw = 0x01020304;

/* Set the physical address of specified device. */
status = nx_ip_interface_physical_address_set(&ip_0,
                                              PRIMARY_INTERFACE,
                                              physical_msw,
                                              physical_lsw,
                                              NX_TRUE);

/* If status == NX_SUCCESS, the physical address was successfully
   set. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check
Проверка состояния экземпляра IP

### <a name="prototype"></a>Прототип  

```c
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

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **interface_index** — запрошенное состояние номера индекса интерфейса needed_status IP-адреса, указанное в форме битовой карты следующим образом:
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **actual_status** — указатель на место назначения фактического набора битов. wait_option — определяет поведение службы в случае, если запрошенные биты состояния недоступны. Параметры ожидания определяются следующим образом:
  - **NX_NO_WAIT** (0x00000000)
  - **значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

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

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
                                      &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
   instance is up. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set
Задание функции обратного вызова для уведомления об изменении состояния канала

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID(*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
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

```c
/* Configure a callback function to be used when the physical
   interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0,
                                             my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
   is set. */
```
### <a name="see-also"></a>См. также:

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check

## <a name="nx_ip_max_payload_size_find"></a>nx_ip_max_payload_size_find
Максимальное количество полезных данных пакета для вычислений

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_max_payload_size_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *dest_address,
    UINT if_index,
    UINT src_port,
    UINT dest_port,
    ULONG protocol,
    ULONG *start_offset_ptr,
    ULONG *payload_length_ptr);
```
### <a name="description"></a>Описание

Эта служба находит максимальный размер полезных данных приложения, который не требует фрагментации IP для достижения места назначения. Например, полезные данные находятся на уровне или ниже размера MTU локального интерфейса. (или значения MTU пути, полученного при обнаружении MTU пути IPv6). Заголовок IP и максимальный размер заголовка приложения (TCP или UDP) вычитаются из общего количества полезных данных. Если политика безопасности IPsec NetX Duo применяется к этой конечной точке, заголовки IPsec (ESP/AH) и связанная нагрузка, такая как начальный вектор, также вычитаются из MTU. Эта служба применима как для IPv4-, так и для IPv6-пакетов.

Параметр *if_index* указывает интерфейс, используемый для отправки пакета. В системе с множественной адресацией вызывающему объекту необходимо указать параметр *if_index*, если назначением является широковещательный (только IPv4), многоадресный или IPv6-адрес локальной связи.

Эта служба возвращает вызывающему объекту два значения:

1) start_offset_ptr — это расположение после заголовков TCP/UDP/IP/IPsec;
2) payload_length_ptr — объем данных, которые может передавать приложение, без превышения MTU.

Эквивалентной службы в NetX не существует.

### <a name="restrictions"></a>Ограничения 

Экземпляр IP должен быть создан ранее.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.
- **dest_address** — указатель на адрес назначения пакета.
- **if_index** — указывает индекс интерфейса для использования.
- **src_port** — номер исходного порта.
- **dest_port** — номер порта назначения.
- **протокол** — используемый протокол верхнего уровня.
- **start_offset_ptr** — указатель на начало данных для максимального количества полезных данных пакета.
- **payload_length_ptr** — указатель на размер полезных данных за исключением заголовков.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — полезные данные успешно вычислены.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса или недопустимый интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель IP или недопустимый адрес назначения.
- **NX_IP_ADDRESS_ERROR** (0x21) — указан недопустимый адрес. 
- **NX_NOT_SUPPORTED** (0x4B) — недопустимый протокол (не UDP или TCP).
- **NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* The following example determines the maximum payload for UDP
   packet to remote host. */
#define PRIMARY_INTERFACE 0
status = nx_ip_max_payload_size_find(&ip_0,
                                     &dest_ipv6_address,
                                     PRIMARY_INTERFACE,
                                     source_port,
                                     dest_port, NX_PROTOCOL_UDP,
                                     &start_offset,
                                     &payload_length);

/* A return value of NX_SUCCESS indicates the packet payload
   payload_length starting at the offset start_offset is
   successfully computed. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable
Отключение отправки и получения необработанных пакетов

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);
/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been disabled for the previously created IP instance. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable
Включение обработки необработанных пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает передачу и получение необработанных IP-пакетов для этого экземпляра IP. Входящие пакеты TCP, UDP, ICMP и IGMP по-прежнему обрабатываются в NetX Duo. Пакеты с неизвестными типами протоколов верхнего уровня обрабатываются подпрограммой приема необработанных пакетов.

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

```c
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been enabled for the previously created IP instance. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_filter_set"></a>nx_ip_raw_packet_filter_set
Задание фильтра необработанных IP-пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_raw_packet_filter_set(
    NX_IP *ip_ptr,
    UINT (*raw_packet_filter)(NX_IP *, ULONG, NX_PACKET *));
```
### <a name="description"></a>Описание

Эта служба настраивает фильтр необработанных IP-пакетов. Функция фильтрации необработанных пакетов, реализованная пользовательским приложением, позволяет приложению принимать необработанные пакеты на основе определяемых пользователем условий. Обратите внимание, что уровень программы-оболочки NetX Duo BSD использует функцию фильтрации необработанных пакетов для обработки необработанных сокетов на уровне BSD. Чтобы использовать эту службу, необходимо выполнить сборку библиотеки NetX Duo с включенным параметром ***NX_ENABLE_IP_RAW_PACKET_FILTER***.

### <a name="parameters"></a>Параметры  

- **ip_ptr** — указатель на блок управления IP.
- **raw_packet_filter** — указатель на функцию фильтра необработанных пакетов.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — подпрограмма фильтра необработанных пакетов успешно задана.
- **NX_NOT_SUPPORT** (0x4B) — поддержка необработанных пакетов недоступна.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
UINT raw_packet_filter(NX_IP *ip_ptr, ULONG protocol,
                       NX_PACKET *packet_ptr)
{

/* Simply filter protocol. */
if(protocol == NX_IP_RAW)
   return NX_SUCCESS;
else
   return NX_NOT_SUCCESSFUL;
}

void raw_packet_thread_entry(ULONG id)
{

/* Set the raw packet filter of IP instance. */
status = nx_ip_raw_packet_filter_set(&ip_0,
                                     raw_packet_filter);

/* If status == NX_SUCCESS, the raw packet filter of IP instance
   was successfully set. */
}
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive
Получение необработанного IP-пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба получает необработанный IP-пакет из указанного экземпляра IP. При наличии IP-пакетов в очереди приема необработанных пакетов вызывающему объекту возвращается первый (самый старый) пакет. В противном случае, если пакеты недоступны, вызывающий объект может приостановить работу согласно значению параметра ожидания.

> [!CAUTION]   
> *Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **packet_ptr** — указатель на место размещения полученного необработанного IP-пакета.
- **wait_option** — определяет поведение службы в случае, если нет доступных пакетов. Параметры ожидания определяются следующим образом:
   - **NX_NO_WAIT** (0x00000000);
   - **NX_WAIT_FOREVER** (0xFFFFFFFF)
   - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

нет

### <a name="example"></a>Пример

```c
/* Receive a raw IP packet for this IP instance, wait for a maximum
   of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
   variable packet_ptr. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send
Отправка необработанного IP-пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```
### <a name="description"></a>Описание

Эта служба отправляет необработанный IPv4-пакет на IP-адрес назначения. Обратите внимание, что эта подпрограмма возвращает управление немедленно. Поэтому неизвестно, был ли IP-пакет отправлен на самом деле. Сетевой драйвер отвечает за освобождение пакета по завершении передачи.

В системе со множественной адресацией NetX Duo ищет соответствующий сетевой интерфейс по IP-адресу назначения и использует IP-адрес интерфейса в качестве исходного адреса. Если IP-адрес назначения является широковещательным или многоадресным, используется первый допустимый интерфейс. В этом случае приложения используют ***nx_ip_raw_packet_source_send***.

Для отправки необработанного пакета IPv6 в приложении должна использоваться служба ***nxd_ip_raw_packet_send,** _ или _ *_nxd_ip_raw_packet_source_send._**

> [!WARNING]  
> *Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Иначе это приведет к непредсказуемым результатам, так как сетевой драйвер освободит пакет после передачи*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **packet_ptr**: указатель на отправляемый IP-пакет
- **destination_ip**: конечный IP-адрес, которым может быть IP-адрес конкретного узла, сетевой широковещательный адрес, петлевой адрес или адрес многоадресной рассылки
- **type_of_service** — определяет тип службы для передачи. Допустимые значения:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)

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

нет

### <a name="example"></a>Пример

```c
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
                               IP_ADDRESS(1,2,3,5),
                               NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
   packet_ptr has been sent. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_source_send"></a>nx_ip_raw_packet_source_send
Отправка необработанного IP-пакета через указанный сетевой интерфейс

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```
### <a name="description"></a>Описание

Эта служба отправляет необработанный IP-пакет на IP-адрес назначения через связанный сетевой интерфейс, используя указанный локальный IPv4-адрес в качестве адреса источника. Обратите внимание, что эта подпрограмма возвращает управление немедленно. Поэтому неизвестно, был ли IP-пакет отправлен на самом деле. Сетевой драйвер отвечает за освобождение пакета по завершении передачи. Эта служба отличается от других служб тем, что узнать, был ли пакет на самом деле отправлен, невозможно. Он мог быть потерян в процессе передачи через Интернет.

> [!CAUTION]  
> *Обратите внимание, что должна быть включена обработка необработанных IP-адресов*.

> [!WARNING]  
> *Эта служба аналогична **nx_ip_raw_packet_send** за исключением того, что она позволяет приложению отправлять необработанные IPv4-пакеты из указанных физических интерфейсов*.

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

нет

### <a name="example"></a>Пример

```c
#define ADDRESS_IDNEX 1

/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_source_send(ip_ptr, packet_ptr,
                                      destination_ip,
                                      ADDRESS_INDEX,
                                      NX_IP_NORMAL);

/* If status is NX_SUCCESS the packet was successfully
   transmitted. */
```

### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_receive_queue_max_set"></a>nx_ip_raw_receive_queue_max_set
Задание максимального размера очереди получения необработанных пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_raw_receive_queue_max_set(
    NX_IP *ip_ptr, 
    ULONG queue_max);
```
### <a name="description"></a>Описание

Эта служба настраивает максимальную глубину очереди приема необработанных IP-пакетов. Обратите внимание, что очередь получения необработанных IP-пакетов используется совместно с пакетами IPv4 и IPv6. Когда очередь получения необработанных пакетов достигает максимальной глубины, настроенной пользователем, вновь полученные необработанные пакеты удаляются. По умолчанию глубина очереди приема необработанных IP-пакетов составляет 20.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **queue_max** — новое значение размера очереди.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — максимальная глубина очереди получения необработанных IP-пакетов успешно задана.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
ULONG queue_max = 10;

/* Set the maximum size of the IP raw packet receive queue. */
status = nx_ip_raw_receive_queue_max_set (&ip_0,
                                          queue_max);

/* If status == NX_SUCCESS, the maximum size of the IP raw packet
   receive queue was successfully set. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add
Добавление статического маршрута в таблицу маршрутизации

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```
### <a name="description"></a>Описание

Эта служба добавляет запись в таблицу статической маршрутизации. Обратите внимание, что адрес *next_hop* должен быть доступен напрямую с одного из локальных сетевых устройств.

> [!CAUTION]  
> *Обратите внимание, что указатель ip_ptr должен указывать на допустимую структуру IP в NetX Duo, а сборка библиотеки NetX Duo должна выполняться с параметром NX_ENABLE_IP_STATIC_ROUTING, предписывающим использование этой службы. По умолчанию сборка NetX Duo выполняется без задания параметра NX_ENABLE_IP_STATIC_ROUTING*.

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

```c
/* Specify the next hop for 192.168.1.68 through the gateway
   192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,1,0),
                                0xFFFFFF00UL,
                                IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
   static routing table. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete
Удаление статического маршрута из таблицы маршрутизации

### <a name="prototype"></a>Прототип  

```c
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask);
```
### <a name="description"></a>Описание

Эта служба удаляет запись из таблицы статической маршрутизации.

> [!WARNING]  
> *Обратите внимание, что указатель ip_ptr должен указывать на допустимую структуру IP в NetX Duo, а сборка библиотеки NetX Duo должна выполняться с параметром NX_ENABLE_IP_STATIC_ROUTING, предписывающим использование этой службы. По умолчанию сборка NetX Duo выполняется без задания параметра NX_ENABLE_IP_STATIC_ROUTING*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **network_address**: целевой сетевой адрес в порядке байтов узла
- **net_mask** — маска целевой сети в порядке байтов узла.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное удаление из таблицы статической маршрутизации.
- **NX_NOT_SUCCESSFUL** (0x43) — не удается найти запись в таблице маршрутизации.
- **NX_NOT_SUPPORTED** (0x4B) — эта функция не компилирована.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ip_ptr.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Remove the static route for 192.168.1.68 from the routing
   table.*/
status = nx_ip_static_route_delete(ip_ptr,
                                   IP_ADDRESS(192,168,1,0),
                                   0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
   the static routing table. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_status_check"></a>nx_ip_status_check
Проверка состояния экземпляра IP

### <a name="prototype"></a>Прототип  

```c
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
- **needed_status** —запрошенное состояние IP, определенное в виде битовой карты следующим образом:
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **actual_status** — указатель на место назначения фактического набора битов.
- **wait_option**: определяет поведение службы в случае, если запрошенные биты состояния недоступны Параметры ожидания определяются следующим образом:
  - **NX_NO_WAIT** (0x00000000)
  - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — успешная проверка состояния IP-адреса.
- **NX_NOT_SUCCESSFUL** (0x43) — запрос состояния не был выполнен в течение указанного времени ожидания.
- **NX_PTR_ERROR** (0x07) — указатель IP является или стал недопустимым, либо недопустимый указатель фактического состояния.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр требуемого состояния.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
                            &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
   is up. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ipv4_multicast_interface_join"></a>nx_ipv4_multicast_interface_join
Присоединение экземпляра IP к указанной группе многоадресной рассылки через интерфейс

### <a name="prototype"></a>Прототип  

```c
UINT nx_ipv4_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба присоединяет экземпляр IP к указанной группе многоадресной рассылки через указанный сетевой интерфейс. После того как экземпляр IP присоединяется к группе многоадресной рассылки, логика приема IP-адресов начинает пересылать пакеты данных из группы предоставления многоадресной рассылки на верхний уровень. Обратите внимание, что эта служба выполняет присоединение к группе многоадресной рассылки, не отправляя отчеты IGMP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **group_address** — адрес группы многоадресной рассылки IP-адресов класса D для присоединения в порядке байтов узла.
- **interface_index** — индекс интерфейса, подключенного к экземпляру NetX Duo.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.
- **NX_NO_MORE_ENTRIES** (0x17) — дальнейшее присоединение групп многоадресной рассылки невозможно (превышено максимальное значение).
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на экземпляр IP или недопустимый экземпляр IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_EANABLED** (0x14) — протокол IGMP не включен в этом экземпляре IP.
- **NX_IP_ADDRESS_ERROR** (0x21) — указанный адрес группы многоадресной рассылки не является допустимым адресом класса D.
- **NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Previously created IP Instance joins the multicast group
   224.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_join
                                 (&ip IP_ADDRESS(224,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ipv4_multicast_interface_leave"></a>nx_ipv4_multicast_interface_leave
Выход из указанной группы многоадресной рассылки через интерфейс

### <a name="prototype"></a>Прототип  

```c
UINT nx_ipv4_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба выполняет выход из указанной группы многоадресной рассылки через указанный сетевой интерфейс. После выхода из группы эта служба не инициирует создание сообщений IGMP.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **group_address** — адрес группы многоадресной рассылки IP-адресов класса D, из которой необходимо выйти. IP-адрес указан в порядке байтов узла.
- **interface_index** — индекс интерфейса, подключенного к экземпляру NetX Duo.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.
- **NX_ENTRY_NOT_FOUND** (0x16) — указанный адрес группы многоадресной рассылки не найден в локальной таблице многоадресной рассылки.
- **NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.
- **NX_IP_ADDRESS_ERROR** (0x21) — указанный адрес группы многоадресной рассылки не является допустимым адресом класса D.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на экземпляр IP или недопустимый экземпляр IP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Leave the multicast group 224.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_leave
                                (&ip, IP_ADDRESS(224,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_packet_allocate"></a>nx_packet_allocate
Выделение пакета из указанного пула

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба выделяет пакет из указанного пула и корректирует положение начального указателя в пакете в соответствии с указанным типом пакета. Если пакет недоступен, служба приостанавливает работу в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул пакетов.
- **packet_ptr** — указатель на указатель выделенного указателя на пакет.
- **packet_type** — определяет тип запрошенного пакета. Список поддерживаемых типов пакетов см. в разделе "Пулы пакетов" главы 3 на стр. 63.
- **wait_option** — определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов. Параметры ожидания определяются следующим образом:
  - **NX_NO_WAIT** (0x00000000);
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — пакет выделен успешно.
- **NX_NO_PACKET** (0x01) — нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.
- **NX_OPTION_ERROR** (0x0A) — недопустимый тип пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый возвращаемый указатель на пул или пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый параметр ожидания не из потока.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры и подпрограммы ISR (сетевые драйверы приложений) Параметр ожидания должен иметь значение *NX_NO_WAIT* при использовании в ISR или контексте таймера.

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Allocate a new UDP packet from the previously created packet pool
   and suspend for a maximum of 5 timer ticks if the pool is
   empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr,
                            NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
   found in the variable packet_ptr. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy
Копирование пакета

### <a name="prototype"></a>Прототип  

```c
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
- **wait_option** определяет поведение службы в случае, если нет доступных пакетов Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

```c
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
   previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append
Добавление данных в конец пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, ULONG data_size,
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
- **wait_option** определяет поведение службы в случае, если нет доступных пакетов Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пакет успешно добавлен.
- **NX_NO_PACKET** (0x01) — нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
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

```c
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
   been appended to the packet. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release


## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset
Извлечение данных из пакета по смещению

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```
### <a name="description"></a>Описание

Эта служба копирует данные из пакета NetX Duo (или из цепочки пакетов) начиная с указанного смещения от указателя начала пакета указанного размера в байтах в заданный буфер. Число фактически скопированных байтов возвращается в *bytes_copied*. Эта служба не удаляет данные из пакета и не настраивает начальный указатель или другую информацию о внутреннем состоянии.

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

нет

```c
/* Extract 10 bytes from the start of the received packet buffer
   into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
                                       &bytes_copied) ;
/* If status is NX_SUCCESS, 10 bytes were successfully copied into
   the data buffer. */
```
### <a name="see-also"></a>См. также

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve
Получение данных из пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start,
    ULONG *bytes_copied);
```
### <a name="description"></a>Описание

Эта служба копирует данные из предоставленного пакета в указанный буфер. Фактическое число скопированных байтов возвращается в месте назначения, на которое указывает **bytes_copied**.

Обратите внимание, что эта служба не изменяет внутреннее состояние пакета. Получаемые данные по-прежнему доступны в пакете. 

> [!CAUTION]  
> *Буфер назначения должен быть достаточно большим, чтобы вместить содержимое пакета. В противном случае память будет повреждена, что приведет к непредсказуемым результатам*.

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

```c
UCHAR                 buffer[512];
ULONG                 bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
   packet, the size of which is contained in "bytes_copied." */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get
Получение длины данных в пакете

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```
### <a name="description"></a>Описание

Эта служба получает длину данных в указанном пакете.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет
- **length** — место назначения для длины пакета.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное получение длины пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель пакета.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create
Создание пула пакетов в указанной области памяти

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Create a packet pool of 32000 bytes starting at physical
   address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
                               (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
   created. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete
Удаление ранее созданного пула пакетов

### <a name="prototype"></a>Прототип  

```c
UINT  nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Описание

Эта служба удаляет ранее созданный пул пакетов. NetX Duo проверяет наличие потоков, приостановленных при обработке пакетов в пуле пакетов, и отменяет приостановку.

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

```c
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
   deleted. */
```

### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get
Получение сведений о пуле пакетов

### <a name="prototype"></a>Прототип  

```c
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

> [!IMPORTANT]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

```c
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

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_low_watermark_set"></a>nx_packet_pool_low_watermark_set
Задание нижнего предела для пула пакетов

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_pool_low_watermark_set(
    NX_PACKET_POOL *pool_ptr,
    ULONG low_watermark);
```
### <a name="description"></a>Описание

Эта служба настраивает нижний предел для указанного пула пакетов. Если задано значение нижнего предела, протокол TCP или UDP не будет ставить в очередь полученные пакеты, если количество доступных пакетов в пуле пакетов меньше нижнего предела, что предотвращает нехватку трафика в пуле пакетов. Эта служба доступна, если библиотека NetX Duo создана с указанным параметром ***NX_ENABLE_LOW_WATERMARK***.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на блок управления пулом пакетов.
- **low_watermark** — значение нижнего предела для настройки.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — значение нижнего предела успешно задано.
- **NX_NOT_SUPPORTED** (0x4B) — функция нижнего предела не встроена в NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на пул.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Set pool_0 low watermark value to 2. */
status = nx_packet_pool_create(&pool_0, 2);

/* If status is NX_SUCCESS, the low watermark value is set for
   pool_0.*/
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release
Освобождение ранее выделенного пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Описание

Эта служба освобождает пакет, а также все сцепленные с ним пакеты. Если другой поток блокируется при выделении пакета, ему предоставляется пакет и его работа возобновляется.

> [!NOTE]  
> *Приложение должно предотвращать многократное освобождение пакета, так как оно приведет к непредсказуемым результатам*.

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

```c
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
   packet pool it was allocated from. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release
Освобождение переданного пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Описание

Для пакетов, отличных от TCP, эта служба освобождает переданный пакет, а также все сцепленные с ним пакеты. Если другой поток блокируется при выделении пакета, ему предоставляется пакет и его работа возобновляется. TCP-пакет помечается как передаваемый, но не освобождается, пока не будет подтвержден. Эта служба обычно вызывается из сетевого драйвера приложения после передачи пакета.

> [!WARNING] 
> *Сетевой драйвер должен удалить заголовок физического носителя и изменить длину пакета перед вызовом этой службы*.

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

```c
/* Release a previously allocated packet that was just transmitted
   from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
   returned to the packet pool it was allocated from. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable
Отключение протокола RARP

### <a name="prototype"></a>Прототип  

```c
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает компонент RARP для определенного экземпляра IP в NetX Duo. В системе со множественной адресацией эта служба отключает протокол RARP во всех интерфейсах.

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

```c
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```
### <a name="see-also"></a>См. также:

- nx_rarp_enable
- nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable
Включение протокола RARP

### <a name="prototype"></a>Прототип  

```c
UINT nx_rarp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба инициализирует компонент RARP определенного экземпляра IP в NetX Duo. Компонент RARP выполняет поиск нулевого IP-адреса во всех подключенных сетевых интерфейсах. Нулевой IP-адрес означает, что интерфейсу еще не назначен IP-адрес. Протокол RARP пытается разрешить IP-адрес, включив в нем процесс RARP.

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

```c
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
   resolve this IP instance’s address by querying the network. */
```
### <a name="see-also"></a>См. также:

- nx_rarp_disable
- nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get
Получение сведений о действиях RARP

### <a name="prototype"></a>Прототип  

```c
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```
### <a name="description"></a>Описание

Эта служба получает сведения о действиях протокола RARP для указанного экземпляра IP.

> [!IMPORTANT]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

```c
/* Retrieve RARP information from previously created IP
   Instance 0. */
status = nx_rarp_info_get(&ip_0,
                          &rarp_requests_sent,
                          &rarp_responses_received,
                          &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_rarp_disable
- nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize
Инициализация системы NetX Duo

### <a name="prototype"></a>Прототип  

```c
VOID nx_system_initialize(VOID);
```
### <a name="description"></a>Описание

Эта служба инициализирует базовые системные ресурсы NetX Duo в процессе подготовки к использованию. Она должна вызываться приложением во время инициализации до выполнения других вызовов NetX Duo.

### <a name="parameters"></a>Параметры

None

### <a name="return-values"></a>Возвращаемые значения

Нет

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

Управление системами

### <a name="example"></a>Пример

```c
/* Initialize NetX Duo for operation. */
nx_system_initialize();

/* At this point, NetX Duo is ready for IP creation and all
   subsequent network operations. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind
Привязка клиентского сокета TCP к TCP-порту

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба привязывает ранее созданный клиентский сокет TCP к указанному TCP-порту. Допустимый диапазон сокетов TCP — от 0 до 0xFFFF. Если указанный TCP-порт недоступен, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr** — указатель на ранее созданный экземпляр TCP-сокета.
- **port** — номер порта для привязки (от 1 до 0xFFFF). Если номер порта — NX_ANY_PORT (0x0000), то экземпляр IP будет искать следующий свободный порт и использует его для привязки.
- **wait_option**: определяет поведение службы в случае, если порт уже привязан к другому сокету Параметры ожидания определяются следующим образом:
- **NX_NO_WAIT** (0x00000000);
- **NX_WAIT_FOREVER** (0xFFFFFFFF)
- **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно привязан.
- **NX_ALREADY_BOUND** (0x22) — этот сокет уже привязан к другому TCP-порту.
- **NX_PORT_UNAVAILABLE** (0x23) — порт уже привязан к другому сокету.
- **NX_NO_FREE_PORTS** (0x45) — нет свободного порта.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_INVALID_PORT** (0x46) — недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Bind a previously created client socket to port 12 and wait for 7
   timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
   bound to port 12 on the associated IP instance. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect
Подключение клиентского сокета TCP

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба подключает ранее созданный и привязанный клиентский TCP-сокет к указанному порту сервера. Допустимый диапазон портов TCP-сервера — от 0 до 0xFFFF. Если подключение не завершается немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **server_ip** — IP-адрес сервера.
- **server_port** — номер порта сервера для подключения (от 1 до 0xFFFF).
- **wait_option** — определяет поведение службы во время установления соединения. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

```c
/* Initiate a TCP connection from a previously created and bound
   client socket. The connection requested in this example is to
   port 12 on the server with the IP address of 1.2.3.5. This
   service will wait 300 timer ticks for the connection to take
   place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
                                      IP_ADDRESS(1,2,3,5),
                                      12, 300);

/* If status is NX_SUCCESS, the previously created and bound
   client_socket is connected to port 12 on IP 1.2.3.5. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get
Получение номера порта, привязанного к клиентскому сокету TCP

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Описание

Эта служба получает номер порта, связанного с сокетом, что может быть полезно при поиске порта, выделенного NetX Duo, если во время привязки сокета было указано значение NX_ANY_PORT.

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

```c
/* Get the port number of previously created and bound client
   socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind
Отмена привязки клиентского сокета TCP к TCP-порту

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
   bound. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_enable"></a>nx_tcp_enable
Включение компонента протокола TCP в NetX Duo

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает компонент протокола TCP в NetX Duo. После включения приложение может устанавливать TCP-подключения.

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

```c
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find
Поиск следующего доступного TCP-порта

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Описание

Эта служба пытается найти свободный TCP-порт (без привязки) начиная с порта, указанного приложением. Если достигнуто максимальное значение порта 0xFFFF, поиск начинается с самого начала. Если поиск завершен успешно, свободный порт возвращается в переменной, на которую указывает *free_port_ptr*.

> [!WARNING]  
> *Если эта служба вызывается из другого потока, она может вернуть тот же порт. Чтобы предотвратить такое состояние гонки, приложение может защитить эту службу и привязку клиентского сокета мьютексом*.

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

```c
/* Locate a free TCP port, starting at port 12, on a previously
   created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
   on the IP instance. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get
Получение сведений о действиях TCP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях протокола TCP для указанного экземпляра IP.

> [!IMPORTANT]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

```c
/* Retrieve TCP information from previously created IP Instance
   ip_0. */
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept
Принятие TCP-подключения

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба принимает (или готовится принять) запрос на подключение к клиентскому TCP-сокету для порта, который ранее был настроен для ожидания передачи данных. Эту службу можно вызывать сразу после того, как приложение вызовет службу ожидания или повторного ожидания передачи данных, или после вызова подпрограммы обратного вызова для ожидания передачи данных при наличии клиентского подключения. Если подключение невозможно установить немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

> [!WARNING]  
> *Когда подключение больше не требуется, приложение должно вызвать **nx_tcp_server_socket_unaccept**, чтобы удалить привязку сокета сервера к порту сервера*.

> [!IMPORTANT]  
> *Подпрограммы обратного вызова приложения вызываются из вспомогательного потока IP*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на управляющий блок сокета TCP-сервера
- **wait_option** определяет поведение службы во время установления соединения Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное принятие сокета TCP-сервера (пассивное подключение).
- **NX_NOT_LISTEN_STATE** (0x36) — указанный сокет сервера не находится в состоянии ожидания передачи данных.
- **NX_IN_PROGRESS** (0x37) — параметр ожидания не указан; выполняется попытка подключения.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) — ошибка указателя сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
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
        created
    */

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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen
Включение ожидания передачи данных для клиентского подключения через TCP-порт

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```
### <a name="description"></a>Описание

Эта служба включает ожидание запроса клиентского подключения через указанный TCP-порт. При получении запроса на подключение клиента указанный сокет сервера привязывается к заданному порту и вызывается указанная функция обратного вызова для ожидания передачи данных.

За выполнение подпрограммы обратного вызова для ожидания передачи данных полностью отвечает приложение. Она может включать в себя логику для пробуждения потока приложения, который затем выполняет операцию принятия. Если в приложении уже есть поток, приостановленный при обработке принятия для этого сокета, подпрограмма обратного вызова для ожидания передачи данных может не потребоваться.

Если приложение планирует обрабатывать дополнительные клиентские подключения через тот же порт, служба ***nx_tcp_server_socket_relisten*** должна быть вызвана с доступным сокетом (в закрытом состоянии) для следующего подключения. Пока не будет вызвана служба повторного ожидания передачи данных, дополнительные клиентские подключения помещаются в очередь. При превышении максимальной глубины очереди самый старый запрос на подключение отбрасывается в пользу нового. Максимальная глубина очереди задается данной службой.

> [!IMPORTANT]  
> *Подпрограммы обратного вызова приложения вызываются из внутреннего вспомогательного потока IP*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **port**: номер порта для ожидания передачи данных (от 1 до 0xFFFF)
- **socket_ptr**: указатель на сокет, который следует использовать для подключения
- **listen_queue_size**: число запросов на клиентское подключение, которые можно поставить в очередь
- **listen_callback**: функция приложения, вызываемая при получении подключения Если указано значение NULL, функция обратного вызова для ожидания передачи данных отключена.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — ожидание передачи данных через TCP-порт успешно включено.
- **NX_MAX_LISTEN** (0x33) — больше нет доступных структур запросов на ожидание передачи данных. Константа NX_MAX_LISTEN_REQUESTS в **_nx_api.h_** определяет, сколько активных запросов на ожидание передачи данных возможно.
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

```c
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
}
```

### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten
Повторное ожидание передачи данных для клиентского подключения через TCP-порт

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Описание

Эта служба вызывается после получения подключения через порт, который ранее был настроен для ожидания передачи данных. Основная задача этой службы — предоставление нового сокета сервера для следующего клиентского подключения. Если запрос на подключение поставлен в очередь, подключение обрабатывается немедленно во время вызова этой службы.

> [!IMPORTANT]  
> *Подпрограмма обратного вызова, указанная в исходном запросе на ожидание передачи данных, вызывается и при наличии подключения для этого нового сокета сервера*.

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

нет

### <a name="example"></a>Пример

```c
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
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                                 NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                 NX_IP_TIME_TO_LIVE, 100,
                                 NX_NULL, port_12_disconnect_request);

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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept
Удаление связи сокета с прослушиваемым портом

### <a name="prototype"></a>Прототип  

```c
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

```c
NX_PACKET_POOL        my_pool;
NX_IP                 my_ip;
NX_TCP_SOCKET         server_socket;
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

NX_PACKET  *my_packet;
UINT       status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial count
      of 0 "my_ip" has already been created and the link is enabled
     "my_pool" packet pool has already been created
   */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                         Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                         NX_IP_TIME_TO_LIVE, 100,NX_NULL,
                         port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
       to
       each client and then disconnecting. */
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten
Отключение ожидания передачи данных для клиентского подключения через TCP-порт

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_server_socket_unlisten(
    NX_IP *ip_ptr, 
    UINT port);
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

нет

### <a name="example"></a>Пример

```c
NX_PACKET_POOL       my_pool;
NX_IP                my_ip;
NX_TCP_SOCKET        server_socket;

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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available
Получает число байтов, доступных для извлечения

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,&bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
   bytes_available. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create
Создание сокета TCP клиента или сервера

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, 
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Описание

Эта служба создает сокет сервера или клиента TCP для указанного экземпляра IP.

> [!NOTE]  
> *Подпрограммы обратного вызова приложения вызываются из потока, связанного с этим экземпляром IP*.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **socket_ptr**: указатель на новый управляющий блок сокета TCP
- **name**: имя приложения для этого сокета TCP
- **type_of_service** — определяет тип службы для передачи. Допустимые значения:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragment** — указывает, разрешена ли фрагментация IP-пакетов. Если указано значение NX_FRAGMENT_OKAY** (0x0), то фрагментация IP-пакетов разрешена. Если указано значение NX_DONT_FRAGMENT (0x4000), то фрагментация IP-пакетов отключена.
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

```c
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete
Удаление сокета TCP

### <a name="prototype"></a>Прототип  

```c
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

нет

### <a name="example"></a>Пример

```c
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect
Завершение подключений к сокетам клиента и сервера

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба завершает установленное подключение к сокету клиента или сервера. После завершения подключения к сокету сервера должен выполняться запрос на отмену принятия, а отключенный сокет клиента остается в состоянии готовности к другому запросу на подключение. Если процесс отключения не может завершиться немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **wait_option** определяет поведение службы во время завершения соединения Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

```c
/* Disconnect from a previously established connection and wait a
   maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
   as a result of the client socket connect or the server accept) is
   disconnected. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify
Установка функции обратного вызова для уведомления о завершении подключения TCP
 
### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова, которая вызывается после завершения операции отключения сокета. Функция обратного вызова для отключения TCP-сокета доступна, если сборка NetX Duo выполнена с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **tcp_disconnect_complete_notify**: функция обратного вызова, которую необходимо установить

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — функция обратного вызова успешно зарегистрирована.
- **NX_NOT_SUPPORTED** (0x4B) — функция расширенного уведомления не встроена в библиотеку NetX Duo. NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
                                                  callback);
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_setnx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify
Задание функции обратного вызова для уведомления об установке TCP-подключения

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова, которая вызывается после установления соединения TCP-сокетом. Функция обратного вызова для установления подключения к TCP-сокету доступна, если сборка NetX Duo выполнена с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **tcp_establish_notify**: функция обратного вызова, вызываемая после установления TCP-подключения

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — функция уведомления успешно задана.
- **NX_NOT_SUPPORTED** (0x4B) — расширенная функция уведомления не встроена в библиотеку NetX Duo. 
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не был включен приложением.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Set the function pointer "callback" as the notify function NetX
   Duo will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get
Получение сведений о действиях сокета TCP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях TCP-сокета для указанного экземпляра TCP-сокета.

> [!NOTE]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Retrieve TCP socket information from previously created
   socket_0.*/
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get
Получение MSS сокета

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket's current MSS value. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get
Получение MSS однорангового сокета TCP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket peer’s advertised MSS value. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set
Задание MSS сокета

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get
Получение сведений об одноранговом сокете TCP

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Описание

Эта служба получает одноранговый IP-адрес и сведения о порте для подключенного TCP-сокета по IPv4-сети. Эквивалентная служба, которая также поддерживает сеть IPv6, ***nxd_tcp_socket_peer_info_get***.

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

```c
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
                                     &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_queue_depth_notify_set"></a>nx_tcp_socket_queue_depth_notify_set
Задание функции уведомления очереди передачи TCP

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_queue_depth_notify_set(
              NX_TCP_SOCKET *socket_ptr,
              VOID(*tcp_socket_queue_depth_notify)(NX_TCP_SOCKET *));
```
### <a name="description"></a>Описание

Эта служба указывает функцию уведомления об обновлении глубины очереди передачи, заданную приложением, которая вызывается каждый раз, когда указанный сокет определяет, что он освободил пакеты из очереди передачи таким образом, что длина очереди больше не превышает предел. Если приложение будет заблокировано при передаче из-за глубины очереди, функция обратного вызова служит уведомлением для приложения о том, что оно может снова начать передачу. Эта служба доступна, только если библиотека NetX Duo создана с указанным параметром ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY***.

### <a name="parameters"></a>Параметры 

- **socket_ptr** — указатель на структуру сокета. 
- **tcp_socket_queue_depth_notify** — устанавливаемая функция уведомления.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — функция уведомления успешно установлена.
- **NX_NOT_SUPPORTED** (0x4B) — функция уведомления о глубине очереди TCP-сокета не встроена в библиотеку NetX Duo
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления сокетом или функцию уведомления.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
VOID tcp_socket_queue_depth_notify(NX_TCP_SOCKET *socket_ptr)
{
   /* Notify the application to resume sending. */

}
/* Install the TCP transmit queue notify function .*/
status = nxd_tcp_socket_queue_depth_notify_set(&tcp_socket,
                                  tcp_socket_queue_depth_notify);

/* If status == NX_SUCCESS, the callback function is successfully
   installed. */
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive
Получение данных из сокета TCP

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба получает данные TCP из указанного сокета. Если в указанном сокете в очереди нет данных, вызывающий объект приостанавливает выполнение на основе указанного параметра ожидания.

> [!CAUTION]  
> *Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета TCP
- **packet_ptr** — указатель на указатель TCP-пакета.
- **wait_option** — определяет поведение службы в случае, если в этом сокете есть данные в очереди. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

```c
/* Receive a packet from the previously created and connected TCP
   client socket. If no packet is available, wait for 200 timer
   ticks before giving up. */
status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by
   "packet_ptr". */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify
Уведомление приложения о полученных пакетах

### <a name="prototype"></a>Прототип   

```c
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr, 
    VOID (*tcp_receive_notify)(NX_TCP_SOCKET *socket_ptr));
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

нет

### <a name="example"></a>Пример

```c
/* Setup a receive packet callback function for the "client_socket"
   socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever one or more packets are received for
   "client_socket". */
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send
Отправка данных через сокет TCP

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба отправляет данные TCP через подключенный ранее сокет TCP. Если последний объявленный размер окна получателя меньше, чем этот запрос, служба при необходимости приостанавливает выполнение в соответствии с указанным параметром ожидания. Эта служба гарантирует, что на уровень IP будут отправлены пакеты данных объемом, не превышающим MSS. 

> [!WARNING]  
> *Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Это приведет к непредсказуемым результатам, так как сетевой драйвер также попытается освободить пакет после передачи*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета TCP
- **packet_ptr**: указатель на пакет данных TCP
- **wait_option** — определяет поведение службы в случае, если запрос превышает размер окна получателя. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

```c
/* Send a packet out on the previously created and connected TCP
   socket. If the receive window on the other side of the connection
   is less than the packet size, wait 200 timer ticks before giving
   up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait
Ожидание перехода сокета TCP в определенное состояние

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба ожидает перехода сокета в требуемое состояние. Если сокет не находится в нужном состоянии, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета TCP
- **desired_state**: требуемое состояние TCP Допустимые состояния TCP-сокета:
    - **NX_TCP_CLOSED** (0x01)
    - **NX_TCP_LISTEN_STATE** (0x02)
    - **NX_TCP_SYN_SENT** (0x03)
    - **NX_TCP_SYN_RECEIVED** (0x04)
    - **NX_TCP_ESTABLISHED** (0x05)
    - **NX_TCP_CLOSE_WAIT** (0x06)
    - **NX_TCP_FIN_WAIT_1** (0x07)
    - **NX_TCP_FIN_WAIT_2** (0x08)
    - **NX_TCP_CLOSING** (0x09)
    - **NX_TCP_TIMED_WAIT** (0x0A)
    - **NX_TCP_LAST_ACK** (0x0B)
- **wait_option** — определяет поведение службы в случае, если запрошенное состояние отсутствует. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFF)

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

```c
/* Wait 300 timer ticks for the previously created socket to enter
   the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
                                  NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
   state! */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback
Установка обратного вызова для состояния ожидания с привязкой ко времени

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова, которая вызывается, когда TCP сокет находится в состоянии ожидания с привязкой ко времени. Чтобы использовать эту службу, необходимо выполнить сборку библиотеки NetX Duo с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера
- **tcp_timed_wait_callback**: функция обратного вызова для ожидания с привязкой ко времени

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — сокет функции обратного вызова успешно зарегистрирован.
- **NX_NOT_SUPPORTED** (0x4B) — сборка библиотеки NetX Duo выполнена без включенной функции расширенного уведомления.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — функция TCP не включена.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure
Настройка параметров передачи для сокета

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Configure the "client_socket" for a maximum transmit queue depth of
   12, 100 tick timeouts, a maximum of 20 retries, and a timeout double
   on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,12,100,20,1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
   configured. */
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set
Уведомление приложения об изменении размера окна

### <a name="prototype"></a>Прототип  

```c
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_window_update_notify)(NX_TCP_SOCKET *socket_ptr));
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

нет

### <a name="example"></a>Пример

```c
/* Set the function pointer to the windows update callback after creating the
   socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
                                                my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(&data_socket)
{

/* Process update on increase TCP transmit socket window size. */
   return;
}
```
### <a name="see-also"></a>См. также:

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable
Включение компонента UDP в NetX Duo

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает компонент UDP в NetX Duo. После включения приложение может отправлять и принимать датаграммы UDP.

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

нет

### <a name="example"></a>Пример

```c
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
   instance. */
```
### <a name="see-also"></a>См. также:

- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find
Поиск следующего доступного UDP-порта

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Описание

Эта служба ищет свободный UDP-порт (без привязки), начиная с указанного приложением номера порта. Если достигнуто максимальное значение порта 0xFFFF, поиск начинается с самого начала. Если поиск завершен успешно, свободный порт возвращается в переменной, на которую указывает параметр free_port_ptr.

> [!WARNING]  
> *Если эта служба вызывается из другого потока, она может вернуть тот же порт. Чтобы предотвратить такое состояние гонки, приложение может защитить эту службу и привязку сокета мьютексом*.

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

нет

### <a name="example"></a>Пример

```c
/* Locate a free UDP port, starting at port 12, on a previously
   created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
   free UDP port on the IP instance. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get
Получение сведений о действиях UDP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях протокола UDP для указанного экземпляра IP.

> [!IMPORTANT]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

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

```c
/* Retrieve UDP information from previously created IP Instance
   ip_0. */
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

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract
Извлечение параметров сети из UDP-пакета

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Описание

Эта служба извлекает параметры сети, такие как IPv4-адрес, номер однорангового порта, тип протокола (всегда возвращается тип UDP) из пакета, полученного через входящий интерфейс. Для получения сведений о пакете, поступающем из сети IPv4 или IPv6, приложение должно использовать службу ***nxd_udp_packet_info_extract.***

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет
- **ip_address**: указатель на IP-адрес отправителя
- **protocol**: указатель на протокол (UDP)
- **port**: указатель на номер порта отправителя
- **interface_index**: указатель на индекс интерфейса приема

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — данные интерфейса пакета успешно извлечены.
- **NX_INVALID_PACKET** (0x12) — пакет не содержит кадр IPv4.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract(packet_ptr, &ip_address,
                                     &protocol, &port,
                                     &interface_index);

/* If status is NX_SUCCESS packet data was successfully
   retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind
Привязка сокета UDP к UDP-порту

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба привязывает ранее созданный сокет UDP к указанному UDP-порту. Допустимый диапазон сокетов UDP — от 0 до 0xFFFF. Если запрошенный номер порта привязан к другому сокету, эта служба ожидает в течение указанного времени, пока привязка сокета к номеру порта не будет отменена.

### <a name="parameters"></a>Параметры

- **socket_ptr** — указатель на ранее созданный экземпляр UDP-сокета.
- **port** — номер порта для привязки** (от 1 до 0xFFFF). Если номер порта — NX_ANY_PORT** (0x0000), то экземпляр IP будет искать следующий свободный порт и использует его для привязки.
- **wait_option** — определяет поведение службы в случае, если порт уже привязан к другому сокету. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

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

```c
/* Bind the previously created UDP socket to port 12 on the
   previously created IP instance. If the port is already bound,
   wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
   port 12.*/
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available
Получает число байтов, доступных для извлечения

### <a name="prototype"></a>Прототип  

```c
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

нет

### <a name="example"></a>Пример

```c
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket,
                                       &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
   retrieved.*/
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable
Отключение контрольной суммы для сокета UDP

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Описание

Эта служба отключает логику проверки контрольной суммы при отправке и получении пакетов через указанный сокет UDP. Если логика проверки контрольной суммы отключена, в поле контрольной суммы заголовка UDP загружается нулевое значение для всех пакетов, отправляемых через этот сокет. Нулевое значение контрольной суммы в заголовке UDP сообщает получателю о том, что контрольная сумма для этого пакета не вычисляется.

Обратите внимание, что эта настройка не действует, если при получении и отправке UDP-пакетов определены параметры **NX_DISABLE_UDP_RX_CHECKSUM** и **NX_DISABLE_UDP_TX_CHECKSUM** соответственно.

Обратите внимание, что эта служба не влияет на пакеты в сети IPv6, так как контрольная сумма UDP является обязательной для IPv6.

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

```c
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
   calculated. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable
Включение контрольной суммы для сокета UDP

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Описание

Эта служба включает логику проверки контрольной суммы при отправке и получении пакетов через указанный сокет UDP. Контрольная сумма охватывает всю область данных UDP, а также псевдозаголовок IP.

Обратите внимание, что эта настройка не действует, если при получении и отправке UDP-пакетов определены параметры **NX_DISABLE_UDP_RX_CHECKSUM** и **NX_DISABLE_UDP_TX_CHECKSUM** соответственно.

Обратите внимание, что эта служба не влияет на пакеты в сети IPv6. Контрольная сумма UDP является обязательной в сети IPv6.

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

```c
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
   calculated. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create
Создание UDP-сокета

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, 
    CHAR *name,
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG queue_maximum);
```
### <a name="description"></a>Описание

Эта служба создает сокет UDP для указанного экземпляра IP.

### <a name="parameters"></a>Параметры

- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **socket_ptr**: указатель на новый управляющий блок сокета UDP
- **name**: имя приложения для этого сокета UDP
- **type_of_service** — определяет тип службы для передачи. Допустимые значения:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragment** — указывает, разрешена ли фрагментация IP-пакетов. Если указано значение NX_FRAGMENT_OKAY (0x0), то фрагментация IP-пакетов разрешена. Если указано значение NX_DONT_FRAGMENT (0x4000), то фрагментация IP-пакетов отключена.
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

нет

### <a name="example"></a>Пример

```c
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
                              NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80,
                              30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
   is ready for binding. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete
Удаление сокета UDP

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
   been deleted. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get
Получение сведений о действиях сокета UDP

### <a name="prototype"></a>Прототип  

```c
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

Эта служба получает сведения о действиях UDP-сокета для указанного экземпляра UDP-сокета.

> [!IMPORTANT]  
> *Если указатель на назначение имеет значение NX_NULL, то эта информация не возвращается вызывающему объекту*.

### <a name="parameters"></a>Параметры

- **socket_ptr** — указатель на ранее созданный экземпляр UDP-сокета.
- **udp_packets_sent** — указатель на место назначения для общего числа отправленных через сокет UDP-пакетов.
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

```c
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

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get
Выбор номера порта, привязанного к сокету UDP

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_port_get(
    NX_UDP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Описание

Эта служба получает номер порта, связанного с сокетом, что может быть полезно при поиске порта, выделенного NetX Duo, если во время привязки сокета было указано значение NX_ANY_PORT.

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

```c
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive
Получение датаграммы из сокета UDP

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба получает датаграмму UDP из указанного сокета. Если в указанном сокете в очереди нет датаграмм, вызывающий объект приостанавливает выполнение на основе указанного параметра ожидания.

> [!CAUTION]  
> *Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **packet_ptr**: указатель на пакет датаграммы UDP
- **wait_option** определяет поведение службы в случае, если в этом сокете нет датаграмм в очереди Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное получение сокета.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_NO_PACKET** (0x01) — отсутствует датаграмма UDP для получения.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или возвращаемый пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — этот компонент не включен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Receive a packet from a previously created and bound UDP socket.
   If no packets are currently available, wait for 500 timer ticks
   before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
   packet_ptr. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify
Уведомление приложения о каждом полученном пакете

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)(NX_UDP_SOCKET *socket_ptr));
```
### <a name="description"></a>Описание 

Эта служба задает указатель на функцию уведомления о получении с помощью функции обратного вызова, заданной приложением. Эта функция обратного вызова затем вызывается при каждом получении пакета через сокет. Если задан указатель NX_NULL, функция уведомления о получении отключена.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на сокет UDP
- **udp_receive_notify** — указатель на функцию обратного вызова приложения, вызываемую при получении пакета в сокете.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — функция уведомления о получении заданного сокета успешно задана.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Setup a receive packet callback function for the "udp_socket"
   socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever a packet is received for
   "udp_socket". */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send
Отправка датаграммы UDP

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address, 
    UINT port);
```
### <a name="description"></a>Описание

Эта служба отправляет датаграмму UDP через ранее созданный и привязанный UDP-сокет для сетей IPv4. NetX Duo находит локальный IP-адрес, подходящий в качестве адреса источника, по IP-адресу назначения. Чтобы указать определенный интерфейс и IP-адрес источника, приложение должно использовать службу **nxd_udp_socket_source_send**.

Обратите внимание, что эта служба возвращает управление немедленно независимо от того, была ли датаграмма UDP успешно отправлена. Эквивалентная служба в NetX Duo (IPv4/IPv6) — ***nxd_udp_socket_send***.

Сокет должен быть привязан к локальному порту.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **packet_ptr** — указатель на пакет датаграммы UDP.
- **ip_address** — IPv4-адрес назначения.
- **port** — допустимый номер порта назначения в диапазоне от 1 до 0xFFFF в порядке байтов узла.

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

```c
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

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_source_send"></a>nx_udp_socket_source_send
Отправка датаграммы через UDP-сокет

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```
### <a name="description"></a>Описание

Эта служба отправляет датаграмму UDP через ранее созданный и привязанный сокет UDP и через сетевой интерфейс с IP-адресом, указанным в качестве исходного. Обратите внимание, что эта служба возвращает управление немедленно независимо от того, была ли датаграмма UDP успешно отправлена. ***nxd_udp_socket_source_send*** работает как в сети IPv4, так и в сети IPv6.

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

```c
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
   interface at index 1 in the IP task interface list. */
status = nx_udp_socket_source_send(socket_ptr, packet_ptr,
                                   destination_ip, 80,
                                   ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind
Отмена привязки UDP-сокета к UDP-порту

### <a name="prototype"></a>Прототип  

```c
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

```c
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
   unbound. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract
Извлечение IP-адреса и порта отправки из датаграммы UDP

### <a name="prototype"></a>Прототип  

```c
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, 
    UINT *port);
```
### <a name="description"></a>Описание

Эта служба извлекает IP-адрес и номер порта отправителя из заголовков IP и UDP в указанной датаграмме UDP. Обратите внимание, что служба ***nxd_udp_source_extract*** работает с пакетами из сети IPv4 или IPv6.

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

```c
/* Extract the IP and port information from the sender of the UPD packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address, &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has been stored
   in sender_ip_address and sender_port respectively.*/
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_icmp_enable"></a>nxd_icmp_enable
Включение служб ICMPv4 и ICMPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает службы ICMPv4 и ICMPv6 и может вызываться только после создания экземпляра IP. Службу можно включить либо до, либо после включения IPv6 (см. *nxd_ipv6_enable*). К службам ICMPv4 относятся запросы проверки связи и ответы на них. К службам ICMPv6 относятся запросы проверки связи и ответы на них, обнаружение соседей, обнаружение повторяющихся адресов, обнаружение маршрутизатора и автоматическая настройка адресов без отслеживания состояния. Эквивалентная служба в NetX (IPv4) — *nx_icmp_enable*.

> [!NOTE] 
> *Если IPv6-адрес настроен вручную до включения ICMPv6, то такой адрес не будет подвергаться процессу обнаружения повторяющихся адресов*.

*nx_icmp_enable* — запускает службы ICMP только для операций IPv4. Приложения, использующие службы ICMPv6, должны использовать параметр *nxd_icmp_enable* вместо *nx_icmp_enable*.

Чтобы использовать запрос маршрутизатора IPv6 и конфигурацию IPv6 без отслеживания состояния, необходимо включить ICMPv6.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — службы ICMP успешно включены.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Enable ICMP on the IP instance. */
status = nxd_icmp_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for ICMP services. */
```
### <a name="see-also"></a>См. также:

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_ping"></a>nxd_icmp_ping
Выполнение запросов проверки связи ICMPv4 или ICMPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_icmp_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr, 
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба отправляет пакет запроса проверки связи ICMP через соответствующий физический интерфейс и ожидает ответа от узла назначения. NetX Duo определяет соответствующий интерфейс на основе адреса назначения, чтобы отправить сообщение проверки связи. Приложения должны использовать службу ***nxd_icmp_source_ping***, чтобы указать физический интерфейс и точный IP-адрес источника, который будет использоваться для передачи пакетов.

Необходимо создать экземпляр IP, а также включить службы ICMPv4 или ICMPv6 (см. ***nxd_icmp_enable***).

> [!WARNING]  
> Если возвращается NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.
- **ip_address** — IP-адрес назначения для проверки связи в порядке байтов узла.
- **data_ptr** — указатель на область данных пакета проверки связи.
- **data_size** — число байтов данных проверки связи.
- **response_ptr** — указатель на указатель пакета ответа.
- **wait_option** — время ожидания ответа. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000)
    - **значение времени ожидания в тактах** (от 0x00000001 до 
    - **NX_WAIT_FOREVER** 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сообщение проверки связи успешно отправлено и получено.
- **NX_NOT_SUPPORTED** (0x4B) — IPv6 не включен.
- **NX_OVERFLOW** (0x03) — данные сообщения проверки связи превышают полезные данные пакета.
- **NX_NO_RESPONSE** (0x29) — узел назначения не ответил.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель ответа.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — компонент IP или ICMP не включен.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый входной IP-адрес.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* The following two examples illustrate how to use this API to send
   ping packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   2001:1234:5678::1 */
   
/* Declare variable address to hold the destination address. */
NXD_ADDRESS ip_address;

char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0x20011234;
ip_address.nxd_ip_address.v6[1]    = 0x56780000;
ip_address.nxd_ip_address.v6[2]    = 0;
ip_address.nxd_ip_address.v6[3]    = 1;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr,
                       NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been
   received from IP address 2001:1234:5678::1 and the response
   packet is contained in the packet pointed to by response_ptr.It
   should have the same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4[0]    = 0x01020304;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr, 10);

/* A return value of NX_SUCCESS indicates a ping reply was received
   from IP address 1.2.3.4 and the response packet is contained in
   the packet pointed to by response_ptr. It should have the same
   “abcd” four bytes of data. */
```
### <a name="see-also"></a>См. также:

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_source_ping"></a>nxd_icmp_source_ping
Выполнение запросов проверки связи ICMPv4 или ICMPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_icmp_source_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    UINT address_index,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба отправляет пакет запроса проверки связи ICMP по указанному индексу IPv4- или IPv6-адреса, а также через сетевой интерфейс, с которым связан адрес источника, и ожидает ответа на запрос проверки связи от узла назначения. Эта служба работает с IPv4- и IPv6-адресами. Параметр *address_index* указывает используемый IPv4- или IPv6-адрес источника. Для IPv4-адреса *address_index* является одним и тем же индексом для подключенного сетевого интерфейса. Для IPv6 *address_index* указывает запись в таблице IPv6-адресов.

Необходимо создать экземпляр IP, а также включить службы ICMPv4 или ICMPv6 (см. *nxd_icmp_enable*).

> [!CAUTION] 
> *Если возвращается NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.
- **ip_address** — IP-адрес назначения для проверки связи в порядке байтов узла.
- **address_index** — указывает IP-адрес для использования в качестве адреса источника
- **data_ptr** — указатель на область данных пакета проверки связи.
- **data_size** — число байтов данных проверки связи.
- **response_ptr** — указатель на указатель пакета ответа.
- **wait_option** — время ожидания ответа. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — сообщение проверки связи успешно отправлено и получено.
- **NX_NOT_SUPPORTED** (0x4B) — IPv6 не включен.
- **NX_OVERFLOW** (0x03) — данные сообщения проверки связи превышают полезные данные пакета.
- **NX_NO_RESPONSE** (0x29) — узел назначения не ответил.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель ответа.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — компонент IP или ICMP не включен.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый входной IP-адрес.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* The following two examples illustrate how to use this API to send ping
   packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   FE80::411:7B23:40dc:f181 */

/* Declare variable address to hold the destination address. */

#define PRIMARY_INTERFACE 0
#define GLOBAL_IPv6_ADDRESS 1

NXD_ADDRESS ip_address;
char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0xFE800000;
ip_address.nxd_ip_address.v6[1]    = 0x00000000;
ip_address.nxd_ip_address.v6[2]    = 0x04117B23;
ip_address.nxd_ip_address.v6[3]    = 0x40DCF181;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              GLOBAL_IPv6_ADDRESS,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been received
   from IP address FE80::411:7B23:40dc:f181 and the response packet is
   contained in the packet pointed to by response_ptr. It should have the
   same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4       = 0x01020304;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              PRIMARY_INTERFACE,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply was received from
   IP address 1.2.3.4 and the response packet is contained in the packet
   pointed to by response_ptr. It should have the same “abcd” four bytes
   of data. */
```

### <a name="see-also"></a>См. также:

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmpv6_ra_flag_callback_set"></a>nxd_icmpv6_ra_flag_callback_set
Задание функции обратного вызова изменения флага объявления маршрутизатора ICMPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_icmpv6_ra_flag_callback_set(
    NX_IP *ip_ptr, 
    VOID(*ra_callback)(NX_IP*ip_ptr, UINT ra_flag));
```
### <a name="description"></a>Описание

Эта служба задает функцию обратного вызова изменения флага объявления маршрутизатора ICMPv6. Предоставляемая пользователем функция обратного вызова вызывается, когда NetX Duo получает сообщение объявления маршрутизатора.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.
- **ra_callback** — предоставляемая пользователем функция обратного вызова.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешно задана функция обратного вызова флага объявления маршрутизатора.
- **NX_NOT_SUPPORTED** (0x4B) — IPv6 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
VOID icmpv6_ra_flag_callback(NX_IP *ip_ptr, UINT ra_flag)
{
   /* RA flag has changed. The updated value is passed in via the
      ra_flag parameter. */
}

/* Configure the user-defined ICMPv6 RA flag change callback
   function. */
status = nxd_icmpv6_ra_flag_callback_set(&ip_0,
                                         icmpv6_ra_flag_callback);

/* A status return of NX_SUCCESS indicates the callback function has
   been successfully configured. */
```
### <a name="see-also"></a>См. также:

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping

## <a name="nxd_ip_raw_packet_send"></a>nxd_ip_raw_packet_send
Отправка необработанного IP-пакета

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ip_raw_packet_send(
    NX_IP *ip_ptr, 
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination
    ULONG protocol, 
    UINT ttl, 
    ULONG tos);
```
### <a name="description"></a>Описание

Эта служба отправляет необработанный пакет IPv4 или IPv6 (без заголовков протокола транспортного уровня). Если в системе со множественной адресацией не удается определить соответствующий интерфейс (например, если IP-адрес назначения — широковещательная рассылка IPv4, адрес многоадресной рассылки или IPv6), выбирается первичное устройство. Для указания исходящего интерфейса можно использовать службу ***nxd_ip_raw_packet_source_send** _. Эквивалентная служба в NetX — _ *_nx_ip_raw_packet_send_.* *

Экземпляр IP должен быть создан ранее, а обработка необработанных IP-пакетов должна быть включена с помощью службы ***nx_ip_raw_packet_enable***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **packet_ptr** — указатель на передаваемый пакет.
- **destination_ip** — указатель на адрес назначения.
- **протокол** — протокол пакетов, хранящийся в заголовке IP.
- **ttl** — значение срока жизни или предела прыжков.
- **tos** — значение TOS или класса трафика и метки потока.

### <a name="return-value"></a>Возвращаемое значение 

- **NX_SUCCESS** (0x00) — необработанный IP-пакет успешно отправлен.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_NOT_ENABLED** (0x14) — обработка необработанных IP-адресов не включена.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv4- или IPv6-адрес.
- **NX_UNDERFLOW** (0x02) — недостаточно места для заголовка IPv4 или IPv6 в пакете.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес или указатель на пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_PARAMETERS** (0x4D) — недопустимые входные данные IPv6-адреса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS dest_address;

/* Set the destination address,in this case an IPv6 address. */
dest_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
dest_address.nxd_ip_address.v6[0]    = 0x20011234;
dest_address.nxd_ip_address.v6[1]    = 0x56780000;
dest_address.nxd_ip_address.v6[2]    = 0;
dest_address.nxd_ip_address.v6[3]    = 1;

UINT ttl, tos;

ttl = 128;

tos = 0;

/* Enable RAW IP handling on the previously created IP instance.*/
status = nx_raw_ip_packet_enable(&ip_0);

/* Allocate a packet pointed to by packet_ptr from the IP packet
   pool. */
/* Then transmit the packet to the destination address. */

status = nxd_ip_raw_packet_send(&ip_0, packet_ptr, dest_address,
                                NX_PROTOCOL_UDP, ttl, tos);

/* A status return of NX_SUCCESS indicates the packet was
   successfully transmitted. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_source_send

## <a name="nxd_ip_raw_packet_source_send"></a>nxd_ip_raw_packet_source_send
Отправка необработанного пакета по указанному адресу источника

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination_ip,
    UINT address_index,
    ULONG protocol,
    UINT ttl,
    ULONG tos);
```
### <a name="description"></a>Описание

Эта служба отправляет необработанный пакет IPv4 или IPv6, используя указанный IPv4- или IPv6-адрес в качестве адреса источника. Эта служба обычно используется в системе со множественной адресацией, если не удается определить соответствующий интерфейс (например, если IP-адрес назначения — широковещательная рассылка IPv4, адрес многоадресной рассылки или IPv6). Параметр *address_index* позволяет приложению указать адрес источника, который будет использоваться при отправке этого необработанного пакета.

Экземпляр IP должен быть создан ранее, а обработка необработанных IP-пакетов должна быть включена с помощью службы ***nx_ip_raw_packet_enable***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.
- **packet_ptr** — указатель на отправляемый пакет.
- **destination_ip** — IP-адрес назначения.
- **address_index** — индекс для IPv4- или IPv6-адресов, используемых в качестве адреса источника.
- **protocol** — значение для поля протокола.
- **ttl** — значение срока жизни или предела прыжков.
- **tos** — значение TOS или класса трафика и метки потока.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — пакет успешно отправлен.
- **NX_UNDERFLOW** (0x02) — недостаточно места для заголовка IPv4 или IPv6 в пакете.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP, пакет или destination_ip.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — обработка необработанных данных не включена.
- **NX_IP_ADDRESS_ERROR** (0x21) — ошибка адреса
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_INVALID_PARAMETERS** (0x4D) — недопустимые входные данные IPv6-адреса.

### <a name="allowed-from"></a>Допустимые источники

Thread

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define SOURCE_ADDRESS_INDEX 2

/* Send a raw packet from specified interface. */
status = nxd_ip_raw_packet_source_send(&ip_0, packet_ptr,
                                       dest_ip,
                                       SOURCE_ADDRESS_INDEX,
                                       NX_IP_RAW,
                                       NX_IP_TIME_TO_LIVE,
                                       NX_IP_NORMAL);

/* If status == NX_SUCCESS, raw packet has been sent out on the
   specified interface. */
```
### <a name="see-also"></a>См. также:

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send

## <a name="nxd_ipv6_address_change_notify"></a>nxd_ipv6_address_change_notify
Задание уведомления об изменении IPv6-адреса

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_address_change_notify(
    NX_IP *ip_ptr,
    VOID (*ip_address_change_notify)(NX_IP *, UINT, UINT, UINT, ULONG *));
```
### <a name="description"></a>Описание

Эта служба регистрирует подпрограмму обратного вызова приложения, которую NetX Duo вызывает при каждом изменении IPv6-адреса.

Эта служба доступна, если библиотека NetX Duo создана с указанием параметра ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY***.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на блок управления IP.
- **ip_address_change_notify** — функция обратного вызова приложения.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешно задано.
- **NX_NOT_SUPPORTED** (0x4B) — функция уведомления об изменении IPv6-адреса не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — уведомление об изменении IPv6-адреса не скомпилировано.

### <a name="allowed-from"></a>Допустимые источники

Thread

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
VOID ip_address_change_notify(NX_IP *ip_ptr, UINT status,
                              UINT interface_index,
                              UINT address_index,
                              ULONG *ip_address)
{

   /* Do something when ip address changed. */
}

void ip_address_thread_entry(ULONG id)
{

   /* Set the ip address change notify of IP instance. */
   status = nxd_ipv6_address_change_notify (&ip_0, ip_address_change_notify);

/* If status == NX_SUCCESS, the ip address change notify of IP
   instance was successfully set. */
}
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_delete"></a>nxd_ipv6_address_delete
Удаление IPv6-адреса

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_address_delete(
    NX_IP *ip_ptr, 
    UINT address_index);
```
### <a name="description"></a>Описание

Эта служба удаляет IPv6-адрес по указанному индексу в таблице IPv6-адресов указанного экземпляра IP. Эквивалента в NetX нет.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **address_index** — таблица IPv6-адресов для экземпляра IP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно удален.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS ip_address;
UINT        address_index;

/* Delete the IPv6 address at the specified address table index. */
address_index = 1;
status = nxd_ipv6_address_delete(&ip_0, address_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully deleted. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_get"></a>nxd_ipv6_address_get
Получение IPv6-адреса и префикса

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_address_get(
    NX_IP *ip_ptr, 
    UINT address_index, 
    NXD_ADDRESS *ip_address,
    ULONG *prefix_length,
    UINT *interface_index);
```
### <a name="description"></a>Описание

Эта служба извлекает IPv6-адрес и префикс по указанному индексу в таблице адресов указанного экземпляра IP. Индекс физического интерфейса, с которым связан IPv6-адрес, возвращается в указателе *interface_index*. Эквивалентными службами в NetX являются ***nx_ip_address_get** _ и _*_nx_ip_interface_address_get_**.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **address_index** — индекс для таблицы адресов экземпляра IP.
- **ip_address** — указатель на адрес, который необходимо задать.
- **prefix_length** — длина префикса адреса (маска подсети).
- **interface_index** — указатель на индекс интерфейса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр IPv6 успешно включен.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — нет адреса интерфейса или недопустимый address_index.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS ip_address;
UINT        address_index;
ULONG       prefix_length;
UINT        interface_index;

/* Get the IPv6 address at the specified address table index. If
   found, the address network interface is returned in the
   interface_index input, as well as the address prefix in the
   prefix_length input. */

address_index = 1;
status = nxd_ipv6_address_get(&ip_0, address_index, &ip_address,
                              &prefix_length, &interface_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_set"></a>nxd_ipv6_address_set
Задание IPv6-адреса и префикса

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_address_set(
    NX_IP *ip_ptr, 
    UINT interface_index,
    NXD_ADDRESS *ip_address,
    ULONG prefix_length,
    UINT *address_index);
```
### <a name="description"></a>Описание

Эта служба задает указанный IPv6-адрес и префикс для выбранного экземпляра IP. Если аргумент *address_index* не равен null, возвращается индекс в таблице IPv6-адресов, в которую вставляется адрес. Эквивалентными службами в NetX являются ***nx_ip_address_set** _ и _*_nx_ip_interface_address_set_**.

### <a name="parameters"></a>Параметры  

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **interface_index** — индекс интерфейса, с которым связан IPv6-адрес.
- **ip_address** — указатель на адрес, который необходимо задать.
- **prefix_length** — длина префикса адреса (маска подсети).
- **address_index** — указатель на индекс в таблице адресов, в которую вставляется адрес.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр IPv6 успешно включен.
- **NX_NO_MORE_ENTRIES** (0x15) — таблица IP-адресов заполнена.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_DUPLICATED_ENTRY** (0x52) — указанный IP-адрес уже используется в этом экземпляре IP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv6-адрес.
- **NX_INVALID_INTERFACE** (0x4C) — интерфейс указывает на недопустимый сетевой интерфейс.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS ip_address;
UINT        address_index;
UINT        interface_index;

ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                     IP_ADDRESS(1,2,3,4),
                     0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                     pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* Set the IPv6 address (a global address as indicated by the 64 bit
   prefix) using the IPv6 address just created on the primary device
   (index zero). The index into the address table is returned in
   address_index. */
interface_index = 0;
status = nxd_ipv6_address_set(&ip_0, interface_index, &ip_address,
                              64,&address_index);

/* A status return of NX_SUCCESS indicates that the IPv6 address is
   successfully assigned to the primary interface (interface 0). */
```

### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add
Добавление маршрутизатора IPv6 в таблицу маршрутизации по умолчанию

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_default_router_add(
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address,
    ULONG router_lifetime,
    UINT index_index);
```
### <a name="description"></a>Описание

Эта служба добавляет маршрутизатор IPv6 по умолчанию к указанному физическому интерфейсу в таблицу маршрутизации по умолчанию. Эквивалентная служба в NetX (IPv4) — ***nx_ip_gateway_address_set***.

*router_address* должен указывать на допустимый IPv6-адрес, а маршрутизатор должен быть напрямую доступен из указанного физического интерфейса.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **router_address** — указатель на адрес маршрутизатора по умолчанию в порядке байтов узла.
- **router_lifetime** — время существования маршрутизатора по умолчанию в секундах. Допустимые значения:
    - **0xFFFF:**  — отсутствие времени ожидания.
    - **0-0xFFFE:**  — время ожидания в секундах.
- **index_index** — указатель на допустимое расположение в памяти для сетевого индекса, через который можно обращаться к маршрутизатору.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — маршрутизатор по умолчанию успешно добавлен.
- **NX_NO_MORE_ENTRIES** (0x17) — в таблице маршрутизации по умолчанию больше нет доступных записей.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv6-адрес.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_INVALID_PARAMETERS** (0x4D) — недопустимые входные данные IPv6-адреса.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса маршрутизатора.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* This example adds a default router for the primary interface at
   fe80::1219:B9FF:FE37:ac to the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;

/* Set the router address version to IPv6 */
router_address.nxd_ip_version   = NX_IP_VERSION_V6;

/* Set the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Set IPv6 default router. */
status = nxd_ipv6_default_router_add(ip_ptr, &router_address,
                                     0xFFFF, PRIMARY_INTERFACE);

/* Unless invalid pointer input is detected by the error checking
   Service, status return is always NX_SUCCESS. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete
Удаление маршрутизатора IPv6 из таблицы маршрутизации по умолчанию

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_default_router_delete (
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address);
```
### <a name="description"></a>Описание

Эта служба удаляет маршрутизатор IPv6 по умолчанию из таблицы маршрутизации по умолчанию. Эквивалентная служба в NetX (IPv4) — ***nx_ip_gateway_address_clear***.

### <a name="restrictions"></a>Ограничения

Создан экземпляр IP. *router_address* должен указывать на допустимые сведения.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **router_address** — указатель на адрес шлюза IPv6 по умолчанию

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — маршрутизатор успешно удален.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_NOT_FOUND** (0x4E) — не удается найти запись маршрутизатора.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_PARAMETERS** (0x82) — недопустимые входные данные (без указателя).

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/*This example removes a default router:fe80::1219:B9FF:FE37:ac */

NXD_ADDRESS router_address;

/* Set the router_address version to IPv6 */
router_address.nxd_ip_version = NX_IP_VERSION_V6;

/* Program the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Delete the IPv6 default router. */
nxd_ipv6_default_router_delete(ip_ptr, &router_address);
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clearnx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_getnx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_entry_get"></a>nxd_ipv6_default_router_entry_get
Получение записи маршрутизатора по умолчанию

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_default_router_entry_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT entry_index,
    NXD_ADDRESS *router_addr,
    ULONG *router_lifetime,
    ULONG *prefix_length,
    ULONG *configuration_method);
```
### <a name="description"></a>Описание

Эта служба получает запись маршрутизатора из таблицы маршрутизации IPv6 по умолчанию, которая подключена к указанному сетевому устройству.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса.
- **entry_index** — индекс записи.
- **router_addr** — IPv6-адрес маршрутизатора.
- **router_lifetime** — время существования указателя на маршрутизатор.
- **prefix_length** — указатель на длину префикса.
- **configuration_method** — указатель на сведения о настройке записи.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное получение
- **NX_NOT_FOUND** (0x4E) — запись маршрутизатора не найдена.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
NXD_ADDRESS            router_addr;
ULONG                  router_lifetime;
ULONG                  prefix_length;
ULONG                  configuration_method;

/* Get the router entry of specified interface. */
status = nxd_ipv6_default_router_entry_get (&ip_0,
                                            PRIMARY_INTERFACE,
                                            entry_index,
                                            &router_addr,
                                            &router_lifetime,
                                            &prefix_length,
                                            &configuration_method);

/* If status == NX_SUCCESS, the router entry was successfully
   got. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_get"></a>nxd_ipv6_default_router_get
Получение маршрутизатора IPv6 из таблицы маршрутизации по умолчанию

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_default_router_get(
    NX_IP *ip_ptr, 
    UINT interface_index
    NXD_ADDRESS *router_address,
    ULONG *router_lifetime,
    ULONG *prefix_length);
```
### <a name="description"></a>Описание

Эта служба получает IPv6-адрес маршрутизатора по умолчанию, время существования и префикс длины для указанного физического интерфейса из таблицы маршрутизации по умолчанию. Эквивалентная служба в NetX (IPv4) — ***nx_ip_gateway_address_get*.**

*router_address* должен указывать на допустимую структуру NXD_ADDRESS, поэтому эта служба может заполнить IPv6-адрес маршрутизатора по умолчанию.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **interface_index** — индекс сетевого интерфейса, через который доступен маршрутизатор.
- **router_address** — указатель на дисковое пространство для возвращаемого значения адреса маршрутизатора по умолчанию в порядке байтов узла.
- **router_lifetime** —указатель на время существования маршрутизатора.
- **prefix_length** — указатель на длину префикса адреса маршрутизатора.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — маршрутизатор по умолчанию успешно добавлен.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_NOT_FOUND** (0x4E) — маршрутизатор по умолчанию не найден.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса маршрутизатора.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* This example retrieves a default router for the primary device
   from the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;
ULONG       router_lifetime;
ULONG       prefix_length;

/* Get IPv6 default router. */
status = nxd_ipv6_default_router_get(ip_ptr, PRIMARY_INTERFACE,
                                     &router_address,
                                     &router_lifetime,
                                     &prefix_length);

/* If status returns NX_SUCCESS, the router address and related
   information is returned successfully. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_number_of_entries_get"></a>nxd_ipv6_default_router_number_of_entries_get
Получение числа маршрутизаторов IPv6 по умолчанию

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_default_router_number_of_entries_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT *num_entries);
```
### <a name="description"></a>Описание

Эта служба получает количество маршрутизаторов IPv6 по умолчанию, настроенных в заданном сетевом интерфейсе.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на блок управления IP.
- **interface_index** — индекс сетевого интерфейса.
- **num_entries** — назначение для числа маршрутизаторов IPv6 на указанном сетевом устройстве.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — успешное получение
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимое значение индекса устройства.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP или указатель на num_entries.

### <a name="allowed-from"></a>Допустимые источники

Thread

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0
UINT                   num_entries;

/* Get the router entries of specified interface. */
status = nxd_ipv6_default_router_number_of_entries_get(&ip_0,
                                                       PRIMARY_INTERFACE,
                                                       &num_entries);

/* If status == NX_SUCCESS, the router entries was successfully
   retrieved. */
```
### <a name="see-also"></a>См. также:

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get

## <a name="nxd_ipv6_disable"></a>nxd_ipv6_disable
Отключение функции IPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба отключает IPv6 для указанного экземпляра IP. Она также очищает таблицу маршрутизации по умолчанию, кэш ND и таблицу IPv6-адресов, выходит из всех групп многоадресной рассылки и сбрасывает переменные запроса маршрутизатора. Эта служба не действует, если IPv6 не включен.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешное отключение.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_NOT_SUPPORT** (0x4B) — модуль IPv6 не скомпилирован.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Disable IPv6 feature on this IP instance. */
status = nxd_ipv6_disable(&ip_0);

/* If status == NX_SUCCESS, disables IPv6 feature on IP instance.*/
```
### <a name="see-also"></a>См. также: 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable
Включение служб IPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба включает службы IPv6. После включения служб IPv6 экземпляр IP присоединяется к группе многоадресной рассылки (FF02::1). Эта служба не задает локальный адрес или глобальный адрес ссылки. Приложения должны использовать *nxd_ipv6_address_set* для настройки сетевых адресов устройств. Эквивалента в NetX нет.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — экземпляр IPv6 успешно включен.
- **NX_ALREADY_ENABLED** (0x15) — протокол IPv6 уже включен.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на IP-адрес.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                      IP_ADDRESS(1,2,3,4),
                      0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                      pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for IPv6 services. */
```
### <a name="see-also"></a>См. также:

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_multicast_interface_join"></a>nxd_ipv6_multicast_interface_join
Присоединение к группе многоадресной рассылки IPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_multicast_interface_join(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```

### <a name="description"></a>Описание

Эта служба позволяет приложению присоединять определенный адрес многоадресной рассылки IPv6 в определенном сетевом интерфейсе. Чтобы добавить адрес многоадресной рассылки, необходимо уведомить драйвер канала. Эта служба доступна, если библиотека NetX Duo создана с указанным параметром ***NX_ENABLE_IPV6_MULTICAST***.

### <a name="parameters"></a>Параметры  

- **ip_ptr** — указатель на экземпляр IP.
- **group_address** — адрес многоадресной рассылки IPv6.
- **interface_index** — индекс сетевого интерфейса, связанного с группой многоадресной рассылки.

### <a name="return-values"></a>Возвращаемые значения  

- **NX_SUCCESS** (0x00) — успешно включено получение адреса многоадресной рассылки IPv6.
- **NX_NO_MORE_ENTRIES** (0x17) — больше нет записей в таблице многоадресной рассылки IPv6.
- **NX_OVERFLOW** (0x03) — в драйвере устройства больше нет доступных адресов групп.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 или многоадресная рассылка IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv6-адрес.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0

/* Join multicast group on this IP instance. */
status = nxd_ipv6_multicast_interface_join(&ip_0,
                                           &group_address,
                                           PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, interface of index on IP instance
   has joined the multicast group. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_leave

## <a name="nxd_ipv6_multicast_interface_leave"></a>nxd_ipv6_multicast_interface_leave
Выход из группы многоадресной рассылки IPv6

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_multicast_interface_leave(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба удаляет определенный адрес многоадресной рассылки IPv6 на конкретном сетевом устройстве. Драйвер канала также уведомляется об удалении адреса многоадресной рассылки IPv6. Эта служба доступна, если библиотека NetX Duo создана с указанным параметром ***NX_ENABLE_IPV6_MULTICAST***.

### <a name="parameters"></a>Параметры  

- **ip_ptr** — указатель на экземпляр IP.
- **group_address** — адрес многоадресной рассылки IPv6.
- **interface_index** — индекс сетевого интерфейса, связанного с группой.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — успешный выход из группы многоадресной рассылки.
- **NX_ENTRY_NOT_FOUND** (0x16) — запись не найдена.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 или многоадресная рассылка IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv6-адрес.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0

/* Leave multicast address on this IP instance. */
status = nxd_ipv6_multicast_interface_leave(&ip_0,
                                            &group_address,
                                            primary_interface);

/* If status == NX_SUCCESS, interface of index on IP instance
   has left the multicast group. */
```
### <a name="see-also"></a>См. также:

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join

## <a name="nxd_ipv6_stateless_address_autoconfig_disable"></a>nxd_ipv6_stateless_address_autoconfig_disable
Отключение автоматической настройки адресов без отслеживания состояния

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_stateless_address_autoconfig_disable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба отключает функцию автоматической настройки адресов IPv6 без отслеживания состояния на указанном сетевом устройстве. Она не действует, если IPv6-адрес настроен.

Эта служба доступна, если библиотека NetX Duo создана с заданным параметром ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.
- **interface_index** — индекс сетевого интерфейса, для которого должна быть отключена автоматическая настройка адресов IPv6 без отслеживания состояния.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — успешно отключает функцию автоматической настройки адресов без отслеживания состояния.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 или функция контроля автоматической настройки IPv6-адресов без отслеживания состояния не встроена в библиотеку NetX Duo.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE 0

/* Disable stateless address auto configuration on this IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_disable(&ip_0,
                                                       PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, disables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>См. также: 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_stateless_address_autoconfig_enable"></a>nxd_ipv6_stateless_address_autoconfig_enable
Включение автоматической настройки адресов без отслеживания состояния

### <a name="prototype"></a>Прототип  

```c
UINT nxd_ipv6_stateless_address_autoconfig_enable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Описание

Эта служба включает функцию автоматической настройки IPv6-адресов без отслеживания состояния на указанном сетевом устройстве.

Эта служба доступна, если библиотека NetX Duo создана с заданным параметром ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL***.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на экземпляр IP.
- **interface_index** — индекс сетевого интерфейса, для которого должна быть включена автоматическая настройка IPv6-адресов без отслеживания состояния.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — успешное включение функции автоматической настройки адресов без отслеживания состояния.
- **NX_ALREADY_ENABLED** (0x15) — уже включено.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 или функция контроля автоматической настройки IPv6-адресов без отслеживания состояния не встроена в библиотеку NetX Duo.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на блок управления IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
#define PRIMARY_INTERFACE

/* Enable stateless address auto configuration on this
   IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_enable(&ip_0,
                                                      PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, enables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>См. также: 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable

## <a name="nxd_nd_cache_entry_delete"></a>nxd_nd_cache_entry_delete
Удаление записи IPv6-адреса в кэше соседей

### <a name="prototype"></a>Прототип  

```c
UINT nxd_nd_cache_entry_delete(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Описание

Эта служба удаляет запись кэша обнаружения соседей IPv6 для заданного IP-адреса. Эквивалентная функция в NetX (IPv4) — ***nx_arp_static_entry_delete***.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **ip_address** — указатель на IPv6-адрес для удаления в порядке байтов узла.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно удален.
- **NX_ENTRY_NOT_FOUND** (0x16) — не удалось найти адрес в кэше соседей IPv6.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* This example deletes an entry from the neighbor cache table. */

NXD_ADDRESS ip_address;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Delete an entry in the neighbor cache table with the specified IPv6
   address and hardware address. */
status = nxd_nd_cache_entry_delete(&ip_0,
                                   &ip_address.nxd_ip_address.v6[0]);

/* If status == NX_SUCCESS, the entry was deleted from the neighbor cache
   table. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set
Добавление сопоставления IPv6-адреса и MAC-адреса в кэш соседей

### <a name="prototype"></a>Прототип  

```c
UINT nxd_nd_cache_entry_set(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *dest_ip,
    UINT interface_index, 
    char *mac);
```

### <a name="description"></a>Описание

Эта служба добавляет запись в кэш обнаружения соседей для указанного IP-адреса *ip_address*, сопоставленного с MAC-адресом оборудования в указанном индексе сетевого интерфейса (interface_index). Эквивалентная служба в NetX (IPv4) — ***nx_arp_static_entry_create***.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **dest_ip** — указатель на экземпляр IPv6-адреса.
- **interface_index** — индекс, указывающий физический сетевой интерфейс, с помощью которого можно связаться с адресом назначения IPv6 
- **mac** — указатель на аппаратный адрес.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — запись успешно удалена.
- **NX_NOT_SUCCESSFUL** (0x43) — недопустимый кэш или нет доступных записей кэша соседей.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимое значение индекса интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* This example adds an entry on the primary network interface to
   the neighbor cache table. */

#define PRIMARY_INTEFACE 0

NXD_ADDRESS ip_address;
UCHAR hw_address[6] = {0x0, 0xcf,0x01,0x02, 0x03, 0x04};
CHAR  *mac;

mac = (CHAR *)&hw_address[0];

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Create an entry in the neighbor cache table with the specified
   IPv6 address and hardware address. */
status = nxd_nd_cache_entry_set(&ip_0,
                                &ip_address.nxd_ip_address.v6[0],
                                PRIMARY_INTERFACE, mac);

/* If status == NX_SUCCESS, the entry was added to the neighbor
   cache table. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_hardware_address_find"></a>nxd_nd_cache_hardware_address_find
Поиск адреса оборудования для IPv6-адреса

### <a name="prototype"></a>Прототип  

```c
UINT nxd_nd_cache_hardware_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw
    UINT *interface_index);
```
### <a name="description"></a>Описание

Эта служба пытается найти физический адрес оборудования в кэше обнаружения соседей IPv6, связанном с заданным IPv6-адресом. Индекс сетевого интерфейса, через который можно получить доступ к окружению, также возвращается в параметре *interface_index*. Эквивалентная служба в NetX (IPv4) — ***nx_arp_hardware_address_find***.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **ip_address** — указатель на IP-адрес для поиска в порядке байтов узла.
- **physical_msw** — указатель на старших 16 бит (47–32) физического адреса в порядке байтов узла. 
- **physical_lsw** — указатель на младших 32 бита (31-0) физического адреса в порядке байтов узла.
- **interface_index** — указатель на допустимое расположение в памяти для индекса интерфейса, указывающего сетевое устройство, с помощью которого можно получить доступ к IPv6-адресу.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно найден.
- **NX_ENTRY_NOT_FOUND** (0x16) — сопоставление отсутствует в кэше соседей.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_INVALID_PARAMETERS** (0x4D) — указанный IP-адрес не относится к версии 6.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* This example inputs an IP address on the primary network in order
   to obtain the hardware address it is mapped to in the neighbor
   cache able. */

NXD_ADDRESS  ip_address;
ULONG physical_msw, physical_lsw;
UINT  interface_index;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Obtain the hardware address mapped to the supplied global IPv6
   address. */
status = nxd_nd_cache_hardware_address_find(&ip_0, &ip_address,
                                            &physical_msw,
                                            &physical_lsw
                                            &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the hardware address returned in
   variables physical_msw and physical_lsw, the index of the network
   interface through which the neighbor can be reached is stored in
   interface_index. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate
Аннулирование кэша обнаружения соседей

### <a name="prototype"></a>Прототип  

```c
UINT nxd_nd_cache_invalidate(NX_IP *ip_ptr);
```
### <a name="description"></a>Описание

Эта служба делает недопустимым весь кэш обнаружения соседей IPv6. Службу можно вызвать до или после включения ICMPv6. Служба неприменима для подключений по протоколу IPv4, поэтому в NetX нет эквивалентной службы.

### <a name="parameters"></a>Параметры

- **ip_ptr** — указатель на экземпляр IP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — кэш стал недопустимым.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* This example invalidates the host neighbor cache table. */

/* Invalidate the cache table bound to the IP instance. */
status = nxd_nd_cache_invalidate (&ip_0);

/* If status == NX_SUCCESS, all entries in the neighbor cache table
   are invalidated. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find
Получение IPv6-адреса для физического адреса

### <a name="prototype"></a>Прототип  

```c
UINT nxd_nd_cache_ip_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT *interface_index);
```
### <a name="description"></a>Описание

Эта служба пытается найти IPv6-адрес в кэше обнаружения соседей IPv6, связанном с заданным физическим адресом. Индекс сетевого интерфейса, через который можно получить доступ к соседям, также возвращается. Эквивалентная служба в NetX (IPv4) — ***nx_arp_ip_address_find***.

### <a name="parameters"></a>Параметры 

- **ip_ptr** — указатель на ранее созданный экземпляр IP.
- **ip_address** — указатель на допустимую структуру NXD_ADDRESS.
- **physical_msw** — старшие 16 бит (47–32) физического адреса для поиска в порядке байтов узла.
- **physical_lsw** — младшие 32 бита (31–0) физического адреса для поиска в порядке байтов узла.
- **interface_index** — указатель на индекс сетевого устройства, через который можно связаться с IPv6-адресом.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно найден.
- **NX_ENTRY_NOT_FOUND** (0x16) — не удалось найти физический адрес в кэше соседей.
- **NX_NOT_SUPPORTED** (0x4B) — функция IPv6 не встроена в библиотеку NetX Duo.
- **NX_PTR_ERROR** (0x07) — недопустимый экземпляр IP или пространство хранилища.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы. 
- **NX_INVALID_PARAMETERS** (0x4D) — MAC-адрес равен нулю.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* This example inputs a hardware address to search on for the
   matching IPv6 global address in the neighbor cache table. */

NXD_ADDRESS ip_address;
ULONG physical_msw = 0xcf;
ULONG physical_lsw = 0x01020304;
UINT  interface_index;

/* Obtain the IPv6 address mapped to the supplied hardware
   Address on the primary device. */
status = nxd_nd_cache_ip_address_find(&ip_0, &ip_address,
                                      physical_msw, physical_lsw,
                                      &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the global IPv6 address returned in
   variable ip_address. */
```
### <a name="see-also"></a>См. также:

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate

## <a name="nxd_tcp_client_socket_connect"></a>nxd_tcp_client_socket_connect
Создание TCP-подключения

### <a name="prototype"></a>Прототип  

```c
UINT nxd_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr
    NXD_ADDRESSS *server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Описание

Эта служба устанавливает TCP-подключение с помощью ранее созданного сокета клиента TCP к порту указанного сервера. Эта служба работает в сетях IPv4 или IPv6. Допустимый диапазон портов TCP-сервера — от 0 до 0xFFFF. NetX Duo определяет соответствующий физический интерфейс на основе IP-адреса сервера. Эквивалентная служба в NetX (IPv4) — ***nx_tcp_client_socket_connect***.

Сокет должен быть привязан к локальному порту.

### <a name="parameters"></a>Параметры

- **socket_ptr** — указатель на ранее созданный TCP-сокет.
- **server_ip** — указатель на IPv4- или IPv6-адрес назначения в порядке байтов узла.
- **server_port** — номер порта сервера для подключения (от 1 до 0xFFFF) в порядке байтов узла.
- **wait_option** — параметр ожидания до установления подключения. Параметры ожидания определяются следующим образом:
    - **NX_NO_WAIT** (0x00000000);
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **значение времени ожидания в тактах** (от 0x00000001 до 0xFFFFFFFE)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сокет успешно подключен.
- **NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv4- или IPv6-адрес сервера.
- **NX_NOT_BOUND** (0x24) — сокет не привязан.
- **NX_NOT_CLOSED** (0x35) — сокет не находится в закрытом состоянии.
- **NX_IN_PROGRESS** (0x37) — параметр ожидания не указан; выполняется попытка подключения.
- **NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — у сетевого интерфейса нет допустимого IPv6-адреса.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_INVALID_PORT** (0x46) — недопустимый порт.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_CONNECTED** (0x38) — сбой подключения.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS peer_ip_address;
ULONG       peer_port;

/* Set Peer IPv6 address */
peer_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
peer_ip_address.nxd_ip_address.v6[0] = 0x20010000;
peer_ip_address.nxd_ip_address.v6[1] = 0;
peer_ip_address.nxd_ip_address.v6[2] = 0;
peer_ip_address.nxd_ip_address.v6[3] = 0x101;

/* Set peer port number */
peer_port = 2563;

/* Connect to the peer */
status = nxd_tcp_client_socket_connect(socket_ptr,
                                       &peer_ip_address,
                                       peer_port, NX_WAIT_FOREVER);
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_socket_peer_info_get

## <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get
Получение IP-адреса однорангового TCP-сокета и номера порта

### <a name="prototype"></a>Прототип  

```c
UINT nxd_tcp_socket_peer_info_get
    (NX_TCP_SOCKET *socket_ptr,
    NXD_ADDRESS *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Описание

Эта служба получает одноранговый IP-адрес и сведения о порте для подключенного TCP-сокета по сети IPv4 или IPv6. Эквивалентная служба в NetX (IPv4) — ***nx_tcp_socket_peer_info_get***.

Обратите внимание, что *socket_ptr* должен указывать на TCP-сокет, который уже подключен.

### <a name="parameters"></a>Параметры

- **socket_ptr** — указатель на TCP-сокет, подключенный к одноранговому узлу.
- **peer_ip_address** — указатель на одноранговый IPv4- или IPv6-адрес. Возвращаемый IP-адрес находится в порядке байтов узла.
- **peer_port** — указатель на номер однорангового порта. Возвращенный номер порта указан в порядке байтов узла.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сведения о сокете успешно получены.
- **NX_NOT_CONNECTED** (0x38) — сокет не подключен к одноранговому узлу.
- **NX_NOT_ENABLED** (0x14) — протокол TCP не включен.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS  peer_ip_address;
ULONG        peer_port;

/* Get TCP socket information. */
status = nxd_tcp_socket_peer_info_get(socket_ptr, &peer_ip_address,
                                      &peer_port);

/* If status == NX_SUCCESS, the service returns valid peer info: */
if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V4)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v4 */

if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V6)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v6 */
```
### <a name="see-also"></a>См. также:

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect

## <a name="nxd_udp_packet_info_extract"></a>nxd_udp_packet_info_extract
Извлечение параметров сети из UDP-пакета

### <a name="prototype"></a>Прототип  

```c
UINT nxd_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Описание

Эта служба извлекает сетевые параметры из пакета, полученного в сетях UDP IPv4 или IPv6. Эквивалентная служба в NetX — ***nx_udp_packet_info_extract***.

### <a name="parameters"></a>Параметры

- **packet_ptr**: указатель на пакет
- **ip_address** — указатель на IP-адрес отправителя.
- **protocol** — указатель на возвращаемый протокол.
- **port** — указатель на номер порта отправителя.
- **interface_index** — указатель на индекс сетевого интерфейса, из которого получен этот пакет.

### <a name="return-values"></a>Возвращаемые значения 

- **NX_SUCCESS** (0x00) — данные интерфейса пакета успешно извлечены.
- **NX_INVALID_PACKET** (0x12) — пакет не относится ни к IPv4, ни к IPv6.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
/* Extract network data from UDP packet interface.*/
status = nxd_udp_packet_info_extract(packet_ptr, &ip_address,
                                    &protocol, &port,
                                    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved.*/
```
### <a name="see-also"></a>См. также: 

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send
Отправка датаграммы UDP

### <a name="prototype"></a>Прототип  

```c
UINT nxd_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port);
```
### <a name="description"></a>Описание

Эта служба отправляет датаграмму UDP через ранее созданный и привязанный UDP-сокет для сетей IPv4 или IPv6. NetX Duo находит локальный IP-адрес, подходящий в качестве адреса источника, по IP-адресу назначения. Чтобы указать определенный интерфейс и IP-адрес источника, приложение должно использовать службу ***nxd_udp_socket_source_send***.

Обратите внимание, что эта служба возвращает управление немедленно независимо от того, была ли датаграмма UDP успешно отправлена. Эквивалентная служба в NetX (IPv4) — ***nx_udp_socket_send***.

Сокет должен быть привязан к локальному порту.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **packet_ptr** — указатель на пакет датаграммы UDP.
- **ip_address** — указатель на IPv4- или IPv6-адрес назначения.
- **port** — допустимый номер порта назначения в диапазоне от 1 до 0xFFFF в порядке байтов узла.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — отправка через UDP-сокет успешно выполнена.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv4- или IPv6-адрес сервера.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_UNDERFLOW** (0x02) — недостаточно места для заголовка UDP в пакете.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет, указатель на адрес или на пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — протокол UDP не включен.
- **NX_INVALID_PORT** (0x46) — номер порта не входит в допустимый диапазон.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS ip_address, server_address;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the
   IPv6 address just created on the primary device (index 0). We
   don’t need the index into the address table, so the last argument
   is set to null. */

interface_index = 0;
status = nxd_ipv6_address_set(&client_ip, interface_index,
                              &ip_address, 64, NX_NULL);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_send(&client_socket, packet_ptr,
                             &server_address, 12);

/* If status == NX_SUCCESS, the UDP host successfully transmitted
   the packet out the UDP socket to the server. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_source_send"></a>nxd_udp_socket_source_send
Отправка датаграммы UDP

### <a name="prototype"></a>Прототип  

```c
UINT nxd_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port, 
    UINT address_index);
```
### <a name="description"></a>Описание

Эта служба отправляет датаграмму UDP через ранее созданный и привязанный UDP-сокет для сетей IPv4 или IPv6. Параметр *address_index* указывает IP-адрес источника, используемый для исходящего пакета. Обратите внимание, что эта функция возвращает управление немедленно независимо от того, была ли датаграмма UDP успешно отправлена.

Сокет должен быть привязан к локальному порту.

Эквивалентная служба в NetX (IPv4) — ***nx_udp_socket_source_send***.

### <a name="parameters"></a>Параметры

- **socket_ptr**: указатель на ранее созданный экземпляр сокета UDP
- **packet_ptr** — указатель на пакет датаграммы UDP.
- **ip_address** — указатель на порт IPv4- или IPv6-адреса назначения. Допустимый номер порта назначения (от 1 до 0xFFFF) в порядке байтов узла.
- **address_index** — индекс, указывающий адрес источника, используемый для пакета.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — отправка через UDP-сокет успешно выполнена.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IPv4- или IPv6-адрес сервера.
- **NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.
- **NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.
- **NX_NOT_FOUND** (0x4E) — не удается найти подходящий интерфейс.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет, адрес или пакет.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.
- **NX_NOT_ENABLED** (0x14) — протокол UDP не включен.
- **NX_INVALID_PORT** (0x46) — номер порта не входит в допустимый диапазон.
- **NX_INVALID_INTERFACE** (0x4C) — указан допустимый сетевой интерфейс.
- **NX_UNDERFLOW** (0x02) — недостаточно места для заголовка UDP в пакете.
- **NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS ip_address, server_address;
UINT address_index;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the IPv6
   address just created on the primary device (index 0). The address index
   is needed for nxd_udp_socket_source_send. */

status = nxd_ipv6_address_set(&client_ip, 0,
                              &ip_address, 64, &address_index);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_source_send(&client_socket, packet_ptr,
                                    &server_address, 12, address_index);

/* If status == NX_SUCCESS, the UDP host successfully transmitted the
   packet out the UDP socket to the server. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_source_extract

## <a name="nxd_udp_source_extract"></a>nxd_udp_source_extract
Получение сведений об источнике пакетов UPD

### <a name="prototype"></a>Прототип  

```c
UINT nxd_udp_source_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address, 
    UINT *port);
```
### <a name="description"></a>Описание

Эта служба извлекает IP-адрес и номер порта источника из пакета UDP, полученного через UDP-сокет узла. Эквивалентная служба в NetX (IPv4) — ***nx_udp_source_extract***.

### <a name="parameters"></a>Параметры

- **packet_ptr** — указатель на полученный пакет UDP.
- **ip_address** — указатель на структуру NXD_ADDRESS для хранения IP-адреса источника пакета.
- **port** — указатель на номер порта UDP-сокета.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное извлечение источника.
- **NX_INVALID_PACKET** (0x12) — недопустимый пакет.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.
- **NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
NXD_ADDRESS ip_address;
UINT         port;

/* Create the UDP socket client_socket and
   allocate the packet pointed to by packet_ptr (not shown). */

/* Extract the IP address and port of the packet received on the UDP
   socket specified in the packet interface. */
status = nxd_udp_source_extract(&packet_ptr, &ip_address, &port);

/* If status == NX_SUCCESS, the source IP address and port of the
   packet received on the UDP socket was successfully extracted. */
```
### <a name="see-also"></a>См. также:

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send