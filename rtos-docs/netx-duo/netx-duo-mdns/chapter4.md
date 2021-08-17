---
title: Глава 4. Описание служб mDNS
description: В этой главе приведено описание всех служб mDNS в NetX.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e37698ac6023b4cff6cb4fc05330a73b678ef3d2a813a706c9b821381e123db
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797574"
---
# <a name="chapter-4---description-of-mdns-services"></a>Глава 4. Описание служб mDNS

В этой главе приведено описание всех служб mDNS в NetX.

> [!NOTE]
> В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

## <a name="nx_mdns_create"></a>nx_mdns_create

Создание экземпляра mDNS

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр mDNS в определенном экземпляре IP и связанные ресурсы. Кроме того, создается поток для обработки входящих сообщений mDNS, ответа на запросы и периодической передачи сообщений запросов.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **ip_ptr**: указатель на связанный экземпляр IP
- **packet_pool**: указатель на допустимый пул пакетов
- **priority**: приоритет потока mDNS
- **stack_ptr**: указатель на область стека для потока mDNS
- **stack_size**: размер области стека
- **host_name**: имя узла, присвоенное этому узлу
- **local_service_cache**: пространство для хранения для локальных зарегистрированных служб
- **local_service_cache_size**: размер локального кэша служб
- **peer_service_cache**: пространство для хранения полученных данных служб
- **peer_service_cache_size**: размер однорангового кэша служб
- **probing_notify**: необязательная функция обратного вызова, вызываемая по завершении операции проверки Она уведомляет приложение о том, является ли имя узла (при включении mDNS в локальном интерфейсе) или имя службы (после регистрации службы) уникальным.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр mDNS успешно создан.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a>nx_mdns_delete

Удаление экземпляра mDNS

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет экземпляр mDNS и освобождает его ресурсы.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр mDNS успешно удален.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

Запуск службы mDNS

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Описание

Этот интерфейс API включает службу mDNS в конкретном физическом интерфейсе. После включения службы модуль mDNS сначала проверяет все уникальные имена служб в сети, прежде чем отвечать на запросы, полученные через интерфейс.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления экземпляра mDNS
- **interface_index**: индекс интерфейса, в котором должна быть включена служба

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно включена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Отключение службы mDNS

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Описание

Этот интерфейс API отключает службу mDNS в указанном физическом интерфейсе. После отключения службы mDNS отправляет сообщение о завершении каждой локальной службе в сети, подключенной к интерфейсу, чтобы уведомить соседние узлы.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **interface_index**: индекс интерфейса, в котором должна быть отключена служба

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно отключена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Устанавливает функцию уведомления о заполнении кэша mDNS

### <a name="prototype"></a>Прототип

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Описание

Эта служба устанавливает предоставленную пользователем функцию обратного вызова, которая вызывается, когда заполняется локальный кэш служб или одноранговый кэш служб. При заполнении кэша служб больше нельзя добавлять записи ресурсов mDNS. Обратите внимание, что кэш служб может заполниться в результате внутренней фрагментации, когда добавляются и удаляются службы с различной длиной строк. При получении уведомления о заполнении однорангового кэша служб приложение может использовать службу *nx_mdns_service_cache_clear* для удаления всех записей в нем.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — функция обратного вызова для уведомления о заполнении кэша mDNS успешно установлена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Очистка функции уведомления о заполнении кэша служб mDNS

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает предоставленную пользователем функцию обратного вызова для уведомления о заполнении кэша служб.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — функция обратного вызова для уведомления о заполнении кэша служб mDNS успешно очищена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

Задание доменного имени

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>Описание

Эта служба задает локальное доменное имя по умолчанию. При создании экземпляра mDNS локальное доменное имя по умолчанию устанавливается в значение .local. Этот интерфейс API позволяет приложению перезаписать локальное доменное имя по умолчанию.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **domain_name**: доменное имя, которое следует использовать

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — локальный домен успешно настроен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Задание параметров времени для сообщений с объявлениями служб

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Описание

Эта служба перенастраивает параметры времени, используемые mDNS при отправке объявлений служб. Период публикации начинается с *t* тактов, и его можно увеличивать с коэффициентом 2 в степени *k*. Число повторов на объявление составляет *p*, интервал между повторными объявлениями — *interval*, а период объявления — max_time. По умолчанию начальный период равен 1 секунде, k = 1 (период каждый раз удваивается), *p = 1* (без повторения), retrans_interval = 0 (без интервала времени), period_interval = 0xFFFFFFFF (максимальный интервал периода), а max_time = 3 (число объявлений).

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **t**: число тактов начального периода Значение по умолчанию — 100 тактов в течение 1 секунды.
- **p**: число повторений Значение по умолчанию — 1.
- **k**: коэффициент увеличения Значение по умолчанию — 1.
- **retrans_interval**: число тактов, которое нужно прождать перед отправкой повторного сообщения с объявлением По умолчанию установлено значение 0.
- **period_interval**: число тактов между двумя периодами объявления Значение по умолчанию — 0xFFFFFFFF.
- **max_time**: число периодов, которое следует использовать для объявления После *max_time* периодов сообщения объявления больше не отправляются. Значение по умолчанию — 3.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — значения времени успешно заданы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

Добавление локальной службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>Описание

Этот интерфейс API регистрирует службу, предлагаемую приложением. Если установлен флаг *is_unique*, mDNS проверяет уникальность имени службы в локальной сети, прежде чем приступать к объявлению службы. *instance* — это часть имени службы, указывающая экземпляр. *service* — это часть имени службы, указывающая службу. Например, _http._tcp — это служба. Для описания службы с подтипом вызывающая сторона должна использовать параметр *subtype*. Например, если нужная служба — _printer._sub._http._tcp, поле service имеет значение _http._tcp:, а поле subtype — _printer.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **instance**: указатель на имя экземпляра службы
- **service**: указатель на тип службы mDNS без сведений о подтипе
- **subtype**: указатель на подтип службы mDNS, если применимо
- **priority**: приоритет службы
- **weight**: вес службы
- **port**: номер TCP- или UDP-порта, используемого службой
- **text**: дополнительные текстовые сведения
- **is_unique**: логический флаг, указывающий, является ли служба общей или уникальной Для служб, зарегистрированных как уникальные, mDNS должен проверить службу в сети, прежде чем предлагать ее.
- **Interface_index**: физический интерфейс, через который предоставляется служба Для службы, предоставляемой любыми связанными службами, используется значение *NX_MDNS_ALL_INTERFACES*.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно зарегистрирована.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a>nx_mdns_service_delete

Удаление ранее зарегистрированной службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a>Описание

Этот интерфейс API удаляет ранее зарегистрированную службу. После удаления службы в локальную сеть рассылаются сообщения о завершении для уведомления соседних узлов.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **instance**: указатель на имя экземпляра службы
- **service**: указатель на тип службы mDNS без сведений о подтипе
- **subtype**: указатель на подтип службы mDNS, если применимо

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно удалена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Инициация однократного обнаружения службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба выполняет однократный запрос mDNS. Если указанная служба найдена в одноранговом кэше служб, возвращается первый экземпляр. Если в локальном одноранговом кэше служб службы не найдены, модуль mDNS выдает команду запроса и ожидает ответа. Служба блокируется до получения первого ответа или истечения времени ожидания запроса.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **instance**: указатель на имя экземпляра службы, если применимо
- **service**: указатель на тип службы mDNS без сведений о подтипе Приложение должно указать тип службы.
- **subtype**: указатель на подтип службы mDNS, если применимо
- **service_ptr**: предоставляемый пользователем указатель на структуру NX_MDNS_SERVICE, в которой хранятся результаты запроса
- **wait_option**: время ожидания ответа в тактах

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сведения о службе успешно получены.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a>nx_mdns_service_continuous_query

Инициация непрерывного обнаружения службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Описание

Эта служба запускает непрерывный запрос. Обратите внимание, что служба немедленно возвращает управление. После отправки непрерывного запроса приложение может получить запись службы с помощью интерфейса API *nx_mdns_service_lookup*. Чтобы остановить выполнение непрерывного запроса, приложение может использовать интерфейс API *nx_mdns_service_query_stop*.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **instance**: указатель на имя экземпляра службы, если применимо
- **service**: указатель на тип службы mDNS без сведений о подтипе, если применимо
- **subtype**: указатель на подтип службы mDNS, если применимо

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — непрерывный запрос успешно запущен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a>nx_mdns_service_query_stop

Прекращение ранее запущенного непрерывного обнаружения службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Описание

Этот интерфейс API прекращает ранее запущенное непрерывное обнаружение службы.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **instance**: указатель на имя экземпляра службы
- **service**: указатель на тип службы mDNS со сведениями о подтипе
- **subtype**: указатель на подтип службы mDNS, если применимо

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — непрерывный запрос успешно остановлен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

Получение службы из локального однорангового кэша служб

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>Описание

Эта служба ищет службы по имени экземпляра (если оно указано) и типу службы в локальном одноранговом кэше служб. Чтобы найти первую службу в кэше, которая соответствует описанию, приложение должно запустить поиск с нулевым значением *instance_index*. Далее приложение должно увеличивать значение *instance_index*, чтобы найти дополнительные службы в кэше, пока служба не вернет *NX_NO_MORE_ENTRIES*, что указывает на конец кэша.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **instance**: указатель на имя экземпляра службы, если применимо
- **service**: указатель на тип службы mDNS без сведений о подтипе, если применимо
- **subtype**: указатель на подтип службы mDNS, если применимо
- **Instance_index**: номер индекса возвращаемого экземпляра
- **service_ptr**: предоставляемый пользователем указатель на структуру NX_MDNS_SERVICE, в которой хранятся результаты поиска

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — служба успешно получена.
- **NX_NO_MORE_ENTRIES** (0x17) — запись службы по указанному номеру индекса не найдена. Этот код ошибки указывает на конец поиска.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

Настройка набора пропускаемых служб

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>Описание

Этот интерфейс API настраивает пропуск служб, заданных битовой маской *service_mask*. Пользователь может при необходимости использовать service_mask для выбора типов служб, которые не требуется кэшировать. Список служб определяется в таблице *nx_mdns_service_types* в файле *nxd_mdns.c*. Соответствующая маска первого типа службы в nx_mdns_service_types[] — 0x00000001, маска второго типа службы — 0x00000002 и т. д.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **service_mask**: определяемые пользователем типы пропускаемых служб. Маска представляет собой 32-разрядный тип ULONG. Каждый бит представляет запись в определяемом пользователем массиве *nx_mdns_service_types*. Если задан бит, соответствующий тип службы в массиве *nx_mdns_service_type* не будет сохраняться в одноранговом кэше служб.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — маска пропуска служб успешно задана.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

Настройка функции обратного вызова для уведомления об изменении службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Описание

Этот интерфейс API настраивает функцию обратного вызова для уведомления об изменении службы. Эта функция обратного вызова вызывается, когда служба, предлагаемая другими узлами в сети, добавляется, изменяется или перестает быть доступной. Пользователь может при необходимости использовать service_mask для выбора типов отслеживаемых служб. Список отслеживаемых служб жестко задан в таблице *nx_mdns_service_types* в файле *nxd_mdns.c*.

Соответствующая маска первого типа службы в nx_mdns_service_types[] — 0x00000001, маска второго типа службы — 0x00000002 и т. д.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **service_mask**: определяемые пользователем типы отслеживаемых служб Маска представляет собой 32-разрядный тип ULONG. Каждый бит представляет запись в массиве *nx_mdns_service_types*.
- **service_change_notify**: функция обратного вызова, вызываемая при изменении указанной службы Подробные сведения о службе возвращаются в области памяти, на которую указывает *service_ptr*. Обратите внимание, что после возврата управления функцией обратного вызова содержимое в памяти становится недействительным.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

Очистка функции обратного вызова для уведомления об изменении службы

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Описание

Этот интерфейс API очищает функцию обратного вызова для уведомления об изменении службы.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — функция обратного вызова успешно очищена.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Получение адреса узла

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба выполняет запрос mDNS к IPv4- и IPv6-адресам узла. Если адрес, связанный с указанным именем узла, найден в одноранговом кэше служб, он возвращается. В противном случае модуль MDN отправляет запросы типа A и AAAA и ожидает ответа. Этот интерфейс API блокируется до получения ответа либо до истечения времени ожидания запроса.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS
- **host_name**: указатель на имя узла
- **ipv4_address**: указатель на пространство хранения IPv4-адреса, выровненное по границе 4 байт. Пользователь должен выделить 4 байт пространства для IPv4-адреса. Если приложению не требуется получать IPv4-адрес, в этот интерфейс API можно передать адрес NX_NULL.
- **ipv6_address**: указатель на пространство хранения IPv6-адреса, выровненное по границе 4 байт. Пользователь должен выделить 16 байт пространства для IPv6-адреса. Если приложению не требуется получать IPv6-адрес, в этот интерфейс API можно передать адрес NX_NULL.
- **wait_option**: время ожидания ответа в тактах

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес узла успешно получен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a>nx_mdns_local_cache_clear

Удаление всех локальных служб

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает все записи в локальном кэше служб после отправки сообщения о завершении.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — все записи в кэше успешно очищены.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

Удаление всех обнаруженных служб

### <a name="prototype"></a>Прототип

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает все записи в одноранговом кэше служб.

### <a name="input-parameters"></a>Входные параметры

- **mdns_ptr**: указатель на блок управления mDNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — все записи в кэше успешно очищены.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
