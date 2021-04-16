---
title: Глава 3. Описание служб сервера DHCP для NetX Duo в ОСРВ Azure
description: Эта глава содержит описание всех служб сервера DHCP для NetX Duo, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814791"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a>Глава 3. Описание служб сервера DHCP для NetX Duo в ОСРВ Azure

Эта глава содержит описание всех служб сервера DHCP для NetX Duo, перечисленных ниже в алфавитном порядке.

> [!NOTE]
> В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

## <a name="nx_dhcp_server-create"></a>nx_dhcp_server_create

Создание экземпляра сервера DHCP

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр сервера DHCP, используя ранее созданный экземпляр IP.

> [!IMPORTANT]
> Приложению нужно убедиться, что созданный для службы создания IP пул пакетов поддерживает полезные данные размером 548 байт, не считая заголовков UDP, IP и Ethernet.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на блок управления сервером DHCP.
- **ip_ptr** — указатель на экземпляр IP для сервера DHCP.
- **stack_ptr** — указатель на расположение стека для сервера DHCP.
- **stack_size** — размер стека для сервера DHCP. input_address_list — указатель на список IP-адресов сервера.
- **name_ptr** — указатель на имя сервера DHCP. packet_pool_ptr — указатель на пул пакетов для сервера DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): — сервер DHCP успешно создан.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9): ошибка: слишком малый размер полезных данных в пакете.
- **NX_DHCP_NO_SERVER_OPTION_LIST** (0x96): список параметров сервера пуст
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Создание пула IP-адресов

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Описание

Эта служба создает пул доступных IP-адресов для конкретного сетевого интерфейса, которые будут назначены указанному серверу DHCP. Начальный и конечный IP-адреса должны соответствовать указанному сетевому интерфейсу. Реальное число добавленных IP-адресов может оказаться меньше заявленного общего числа адресов, если будет исчерпан список IP-адресов (его размер задается в настраиваемом пользователем параметре *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE*).

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на блок управления сервером DHCP.
- **iface_index** — индекс, соответствующий сетевому интерфейсу.
- **start_ip_address** — первый доступный IP-адрес.
- **end_ip_address** — последний доступный IP-адрес.
- **addresses_added** — число IP-адресов, добавляемых в список.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): — сервер DHCP успешно создан.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.
- **NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99): неправильно введены адреса.
- NX_DHCP_INVALID_IP_ADDRESS (0x9B): нарушение логики начального и конечного адресов.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Удаление записи клиента из базы данных сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает запись клиента из базы данных сервера.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на блок управления сервером DHCP.
- **dhcp_client_ptr** — указатель на клиент DHCP, который нужно удалить.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): — сервер DHCP успешно создан.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): вызов службы не из потока

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Настройка параметров сети в конфигурации DHCP

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a>Описание

Эта служба задает значения по умолчанию для критически важных сетевых параметров указанного интерфейса. Сервер DHCP будет включать эти параметры в ответы OFFER и ACK, возвращаемые в клиент DHCP. Если параметры интерфейса устанавливает узел, в котором выполняется сервер DHCP, будут использоваться следующие значения по умолчанию: в качестве основного шлюза для интерфейса задается адрес самого сервера DHCP, в качестве адреса DNS-сервера также задается адрес самого сервера DHCP, а в качестве маски подсети задается значение, настроенное для интерфейса сервера DHCP.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на блок управления сервером DHCP.
- **iface_index** — индекс, соответствующий сетевому интерфейсу.
- **subnet_mask** — маска подсети для сети клиента.
- **default_gateway_address** — IP-адрес маршрутизатора клиента.
- **dns_server_address** — DNS-сервер для сети клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): — сервер DHCP успешно создан.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.
- **NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3): недопустимые параметры сети
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Удаление экземпляра сервера DHCP

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр сервера DHCP.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на экземпляр сервера DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер DHCP успешно удален.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Запуск работы сервера DHCP.

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает работу сервера DHCP, в том числе создает для сервера сокет UDP, привязывает порт DHCP и ожидает получения запросов от клиента DHCP.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на ранее созданный экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сервер успешно запущен.
- **NX_DHCP_ALREADY_STARTED** (0x93): сервер DHCP уже запущен.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Остановка работы сервера DHCP

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает работу сервера DHCP, в том числе получение запросов от клиента DHCP.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr** — указатель на экземпляр сервера DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер DHCP успешно остановлен.
- **NX_DHCP_ALREADY_STARTED** (0x93): сервер DHCP уже запущен.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
