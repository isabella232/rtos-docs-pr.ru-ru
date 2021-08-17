---
title: Глава 4. Службы сервера ОСРВ Azure NetX Duo DHCPv6
description: В этой главе приведено описание всех служб NetX Duo DHCPv6Server
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf6b43f70a7159af6c24496ec2ae2276d5e271af2ad3af99687181df3bf6be6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792032"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a>Глава 4. Службы сервера ОСРВ Azure NetX Duo DHCPv6

В этой главе приведено описание всех служб NetX Duo DHCPv6Server (см. список ниже).

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- nx_dhcpv6_server_create *Создание DHCPv6 serverinstance*
- nx_dhcpv6_server_delete *Удаление DHCPv6 serverinstance*
- nx_dhcpv6_server_start *Запуск задачи DHCPv6-сервера*
- nx_dhcpv6_server_suspend *Приостановка задачи DHCPv6-сервера*
- nx_dhcpv6_server_resume *Возобновление клиентской обработки DHCPv6*
- nx_dhcpv6_server_suspend *Приостановка клиентской обработки DHCPv6*
- nx_dhcpv6_create_dns_address *Установка DNS-сервера для запросов параметров*
- nx_dhcpv6_create_ip_address_range *Создание диапазона IP-адресов для аренды*
- nx_dhcpv6_reserve_ip_address_range *Резервирование диапазона IP-адресов в списке сервера*
- nx_dhcpv6_set_server_duid *Установка DUID сервера для пакетов DHCPv6*
- nx_dhcpv6_add_ip_address_lease *Добавление записи аренды в таблицу DHCPv6-сервера*
- Nx_dhcpv6_retrieve_ip_address_lease *Получение записи IP-аренды из таблицы сервера*
- nx_dhcpv6_add_client_record *Добавление записи DHCPv6-клиента в таблицу сервера*
- nx_dhcpv6_retrieve_client_record *Получение записи клиента из таблицы сервера*
- nx_dhcpv6_server_interface_set *Установка индекса интерфейса для служб DHCPv6-сервера*
- nx_dhcpv6_server_option_request_handler_set *Установка обработчика запроса параметра*

## <a name="nx_dhcpv6_create_dns_address"></a>nx_dhcpv6_create_dns_address

### <a name="set-the-network-dns-server"></a>Установка сетевого DNS-сервер

**Прототип**

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

**Описание**

Эта служба загружает DHCPv6-сервер с адресом DNS-сервера для сетевого интерфейса DHCPv6 сервера.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **dns_ipv6_address** Указатель на DNS-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) DNS-сервер сохранен в экземпляре DHCPv6-сервера
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – указан недопустимый адрес
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a>nx_dhcpv6_create_ip_address_range

### <a name="create-the-server-ip-address-list"></a>Создание списка IP-адресов сервера

**Прототип**

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

**Описание**

Эта служба создает список IP-адресов, определяемый начальным и конечным адресом диапазона назначаемых адресов сервера. Начальный и конечный адреса должны совпадать с префиксом адреса интерфейса сервера (должны находиться по той же ссылке, что и интерфейс DHCPv6 сервера). Возвращается число фактически добавленных адресов.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **start_ipv6_address** Первый добавляемый адрес
- **end_ipv6_address** Последний добавляемый адрес
- ***addresses_added** Результат добавления адресов

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – список IP-адресов успешно создан
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – указан недопустимый адрес
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a>nx_dhcpv6_reserve_ip_address_range

### <a name="reserve-specified-range-of-ip-addresses"></a>Резервирование указанного диапазона IP-адресов

**Прототип**

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

**Описание**

Эта служба резервирует диапазон IP-адресов, заданный начальным и конечным адресами. Эти адреса должны находиться в пределах ранее созданного диапазона IP-адресов сервера. DHCPv6-сервер не будет назначать эти адреса клиентам. Начальный и конечный адреса должны совпадать с префиксом адреса интерфейса сервера (должны находиться по той же ссылке, что и сетевой интерфейс DHCPv6 сервера). Возвращается число фактически зарезервированных адресов.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **start_ipv6_address** Первый резервируемый адрес
- **end_ipv6_address** Последний резервируемый адрес
- ***addresses_reserved** Число зарезервированных адресов

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) RELEASE – сообщение успешно создано и обработано
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – указан недопустимый адрес
- **NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) – начальный адрес не найден в списке адресов сервера.
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a>nx_dhcpv6_server_create

### <a name="create-the-dhcpv6-server-instance"></a>Создание экземпляра DHCPv6-сервера 

**Прототип**

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

**Описание**

Эта служба создает задачу DHCPv6-сервера с указанными входными данными. Обработчики обратного вызова являются необязательными входными данными. Необходимо ввести указатель стека, IP-адрес экземпляра и входные данные пула пакетов. IP-адрес экземпляра и пул пакетов необходимо создать заранее.

Пользователю рекомендуется вызвать nx_dhcpv6_server_option_request_handler_set, чтобы задать обработчик запросов параметров.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **ip_ptr** Указатель на IP-адрес экземпляра
- **name_str** Указатель на имя сервера
- **packet_pool_ptr** Указатель на пул пакетов сервера
- **stack_ptr** Указатель на память стека сервера
- **stack_size** Размер памяти стека сервера
- **dhcpv6_address_declined_handler** Указатель на обработчик сообщений об отклонении или выпуске клиента
- **dhcpv6_option_request_handler** Указатель на обработчик параметров запросов параметров

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – работа сервера успешно возобновлена
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя
- NX_DHCPV6_PARAM_ERROR – недопустимые входные данные без указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a>nx_dhcpv6_server_delete

### <a name="delete-the-dhcpv6-server"></a>Удаление DHCPv6-сервера

**Прототип**

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Описание**

Эта служба удаляет задачу DHCPv6-сервера и все запросы, выполняемые сервером.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно удален
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Потоки

**Пример**

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a>nx_dhcpv6_server_resume

### <a name="resume-dhcpv6-server-task"></a>Возобновление задачи DHCPv6-сервера 

**Прототип**

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Описание**

Эта служба возобновляет задачу DHCPv6-сервера и все запросы, выполнявшиеся сервером.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – работа сервера успешно возобновлена
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) – сервер уже запущен
- **состояние** (переменная) – состояние ошибки ThreadX и NetX Duo
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Потоки

**Пример**

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a>nx_dhcpv6_server_suspend

### <a name="suspend-dhcpv6-server-task"></a>Приостановка задачи DHCPv6-сервера 

**Прототип**

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Описание**

Эта служба приостанавливает задачу DHCPv6-сервера и все запросы, выполняемые сервером.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – работа сервера успешно возобновлена
- **NX_DHCPV6_NOT_STARTED** (0xE92) – сервер не запущен 
- **состояние** (переменная) – состояние ошибки ThreadX и NetX Duo
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Потоки

**Пример**

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a>nx_dhcpv6_server_start

### <a name="start-the-dhcpv6-server-task"></a>Запуск задачи DHCPv6-сервера 

**Прототип**

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

**Описание**

Эта служба запускает задачу DHCPv6-сервера и готовит сервер к обработке запросов приложений на получение сообщений клиента DHCPv6. Она проверяет, имеет ли экземпляр сервера достаточно информации (DUID сервера), создает и привязывает UDP-сокет для отправки и получения сообщений DHCPv6, а также активирует таймеры для отслеживания времени сеанса и истечения срока действия IP-аренды.

>[!NOTE] 
> Перед запуском DHCPv6-сервера ведущее приложение должно создать диапазон IP-адресов, из которого сервер будет назначать адреса. Оно также настраивает DUID сервера и интерфейса DHCPv6 (см. *nx_dhcpv6_server_duid_set* и *nx_dhcpv6_server_interface_set* соответственно.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно запущен
- **NX_DHCPV6_ALREADY_STARTED** (0xE91) – сервер уже запущен
- **NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) – для сервера не заданы назначаемые адреса для аренды
- **NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) – глобальный индекс адреса не задан
- **NX_DHCPV6_NO_SERVER_DUID** (0xE92) – DUID сервера не создан 
- **состояние** (переменная) – состояние ошибки ThreadX и NetX Duo
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Потоки

**Пример**

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a>nx_dhcpv6_retrieve_ip_address_lease

### <a name="get-an-ip-address-lease-from-the-server-table"></a>Получение IP-адреса для аренды из таблицы сервера

**Прототип**

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

**Описание**

Эта служба получает запись аренды IP-адреса из таблицы сервера в указанном месте таблицы по индексу. Это можно сделать до или после получения данных записи клиента.

Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6. Это не влияет на порядок сохранения данных IP-аренды и данных записи клиента в энергонезависимой памяти.

>[!NOTE] 
> Не рекомендуется копировать данные в таблицах сервера без предварительной остановки или приостановки DHCPv6-сервера.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **table_index** – индекс таблицы для хранения данных аренды
- **lease_IP_address** – указатель на IP-адрес, предоставленный в аренду клиенту
- **T1** – время на возобновление, запрошенное клиентом
- **T2** – время на восстановление соединений, запрошенное клиентом
- **valid_lifetime** – срок аренды для клиента становится нерекомендуемым
- **preferred_lifetime** – срок аренды для клиента истекает

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно запущен
- **NX_DHCPV6_PARAMETER_ERROR** (0xE93) – введены недопустимые входные данные IP-аренды
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a>nx_dhcpv6_add_ip_address_lease

### <a name="add-an-ip-address-lease-to-the-server-table"></a>Добавление IP-адреса для аренды в таблицу сервера

**Прототип**

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

**Описание**

Эта служба загружает данные об аренде IP-адреса из предыдущего сеанса сервера DHCPv6, сохраненного в энергонезависимой памяти, в таблицу аренды сервера. Это необязательно, если сервер запускается в первый раз и предыдущих данных аренды нет. В этом случае ведущее приложение должно создать диапазон IP-адресов для назначения с помощью службы *nx_dhcpv6_create_ip_address_range*. Этих данных будет достаточно для воссоздания записи аренды DHCPv6. Индекс таблицы указывать не нужно. Если задано значение 0xFFFFFFFF (бесконечность), DHCPv6-сервер скопирует данные в ближайший доступный слот.

>[!NOTE] 
> Перед отправкой записей клиентов необходимо выполнить отправку данных об аренде IP-адреса. Обе операции необходимо выполнить до (повторного) запуска DHCPv6-сервера.

Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **table_index** – индекс таблицы для хранения данных аренды
- **lease_IP_address** – указатель на IP-адрес, предоставленный в аренду клиенту
- **T1** – время на возобновление, запрошенное клиентом
- **T2** – время на восстановление соединений, запрошенное клиентом
- **valid_lifetime** – срок аренды для клиента становится нерекомендуемым
- **preferred_lifetime** – срок аренды для клиента истекает

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно запущен
- **NX_DHCPV6_TABLE_FULL** (0xEC4) – нет места для добавления данных об аренде**
- **NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – вероятно, данные аренды не связаны с интерфейсом сервера DHCPv6
- **NX_DHCPV6_PARAM_ERROR** (0xE93) – недопустимые входные данные об аренде IP-адресов
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a>nx_dhcpv6_add_client_record

### <a name="add-a-client-record-to-the-server-table"></a>Добавление записи клиента в таблицу сервера

**Прототип**

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

**Описание**

Эта служба копирует данные клиента из энергонезависимой памяти в таблицу сервера по одной записи за раз. Это необходимо только при перезагрузке сервера и при наличии в памяти данных клиента из предыдущего сеанса для восстановления. Если на сервере нет данных из предыдущего сеанса, DHCPv6-сервер инициализирует таблицу клиента для добавления записей клиента.

Указывать индекс таблицы необязательно. Если задано значение 0xFFFFFFFF (бесконечность), DHCPv6-сервер будет использовать ближайший доступный слот. На основе этих данных DHCPv6-сервер может воссоздать запись клиента.

>[!NOTE] 
> Ведущее приложение ДОЛЖНО передать данные об аренде IP-адресов ПЕРЕД передачей данных записи клиента. Это позволяет внутреннему серверу DHCPv6 связывать таблицы, т.е. соединять записи клиента с записями аренды IP-адреса в соответствующих таблицах. Дополнительную информацию о передаче данных об аренде IP-адресов см. в разделе *nx_dhcpv6_add_ip_address_lease*.

>[!NOTE] 
> В зависимости от типа DUID некоторые данные можно не указывать. Например, если у клиента есть назначенный поставщиком тип DUID, он может отправить нулевое значение для параметров канального уровня DUID (MAC-адрес, тип оборудования, время DUID).

Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно запущен
- **NX_ INVALID_PARAMETERS** (0x4D) – недопустимые входные данные без указателя**
- **NX_DHCPV6_TABLE_FULL** (0xEC4) – нет свободных слотов для добавления записи клиента
- **NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) – адрес, назначенный клиенту, не найден в таблице данных сервера об аренде.
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a>nx_dhcpv6_retrieve_client_record

### <a name="retrieve-a-client-record-from-the-server-table"></a>Получение записи клиента из таблицы сервера

**Прототип**

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

**Описание**

Эта служба копирует основные данные из таблицы записей клиентов сервера для хранения в энергонезависимой памяти. Сервер может воссоздать соответствующую запись клиента из таких данных в обратном процессе (отправка данных в таблицу сервера). Независимо от типа DUID указатель не может быть нулевым значением; при инициализации для всех параметров будут установлены нулевые значения. Например, если тип DUID клиента — канальный слой и время, возвращается нулевое значение поставщика и пустая строка вместо частного идентификатора.

Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6. Это не влияет на порядок сохранения данных IP-аренды и данных записи клиента в энергонезависимой памяти.

>[!NOTE] 
> Не рекомендуется копировать данные в таблицах сервера без предварительной остановки или приостановки DHCPv6-сервера.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **table_index** Индекс для таблицы данных клиентов сервера
- **message_xid** Идентификатор транзакции клиентского сервера
- **client_address** IPv6-адрес, предоставленный клиенту в аренду
- **client_state** Состояние DHCPv6 клиента (например, "ограниченный")
- **IP_lease_time_accrued** Текущий срок аренды **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно запущен
- **NX_DHCPV6_INVALID_DUID** (0xECC) – недопустимые или противоречивые данные DUID
- **NX_PTR_ERROR** (0x16) – недопустимые входные данные указателя
- NX_INVALID_PARAMETERS (0x4D) – недопустимые входные данные без указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a>nx_dhcpv6_server_interface_set

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a>Установка индекса интерфейса для DHCPv6-сервера

**Прототип**

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

**Описание**

Эта служба задает сетевой интерфейс, на котором DHCPv6-сервер обрабатывает запросы клиента DHCPv6. Это не распространяется на версии NetX Duo, которые не поддерживают множественную адресацию, значение интерфейса будет сброшено на нуль. Индекс глобального адреса необходим для получения глобального адреса сервера в интерфейсе DHCPv6. В логике DHCPv6 он подтверждает наличие связи между адресами аренды и другими данными DHCPv6 и сервером DHCPv6.

Этот вызов должен быть выполнен перед запуском DHCPv6-сервера, даже для приложений на отдельных сетевых устройствах или без поддержки множественной адресации.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **iface_index** Интерфейс DHCPv6-сервера
- **ga_address_index** Индекс глобального адреса сервера в таблице IP-адресов экземпляров сервера

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно запущен
- **NX_INVALID_INTERFACE** (0x4C) – интерфейс не существует
- NX_NO_INTERFACE_ADDRESS (0x50) – глобальный индекс превышает максимальное число IPv6-адресов для IP-адреса экземпляра (NX_MAX_IPV6_ADDRESSES)
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a>nx_dhcpv6_set_server_duid

### <a name="set-the-server-duid-for-dhcpv6-packets"></a>Установка DUID сервера для пакетов DHCPv6

**Прототип**

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

**Описание**

Эта служба задает DUID сервера, и ее необходимо вызвать до того, как ведущее приложение запустит сервер. Для типов DUID канального уровня и времени канального уровня ведущее приложение должно предоставить данные о типе оборудования и MAC-адрес. Для DUID времени на канальном уровне указатель времени должен указывать на допустимое время. Обычно в качестве исходного значения используется количество секунд с 1 января 2000 года. Если тип DUID для сервера — предприятие и назначен поставщиком, то DUID будет создан на основе настраиваемых параметров пользователя, NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID и NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, а значения времени и MAC-адреса могут быть нулевыми.

>[!NOTE] 
> Ведущее приложение должно сохранить параметры DUID сервера в энергонезависимой памяти, чтобы между перезагрузками использовать одинаковые DUID в сообщениях для клиентов. Это необходимое условие работы по протоколу DHCPv6 (RFC 3315).

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **duid_type** Тип DUID DHCPv6-сервера
- **hardware_type** Тип оборудования (например, Ethernet)
- **mac_address_msw** Указатель на DHCPv6-сервер
- **mac_address_lsw** Указатель на DHCPv6-сервер
- **time** Значение времени для DUID

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – сервер успешно приостановлен
- **NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) – неизвестный или неподдерживаемый тип DUID
- **NX_INVALID_PARAMETERS** (0x4D) – недопустимые входные данные без указателя
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a>nx_dhcpv6_server_option_request_handler_set

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a>Установка обработчика запросов параметров для экземпляра DHCPv6-сервера 

**Прототип**

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

**Описание**

Эта служба задает расширенный обработчик запросов параметров DHCPv6-сервера.

**Входные параметры**

- **dhcpv6_server_ptr** Указатель на DHCPv6-сервер
- **dhcpv6_option_request_handler_extended** Указатель на расширенный обработчик запросов параметров

**Возвращаемые значения**

- **NX_SUCCESS** (0x00) – работа сервера успешно возобновлена
- NX_PTR_ERROR (0x16) – недопустимые входные данные указателя

**Допустимые источники**

Код приложения

**Пример**

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```