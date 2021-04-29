---
title: Глава 3. Описание служб сервера ОСРВ Azure NetX DHCP
description: В этой главе содержится описание всех служб сервера ОСРВ Azure NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815243"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>Глава 3. Описание служб сервера ОСРВ Azure NetX DHCP

В этой главе приведено описание всех служб сервера NetX DHCP.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_dhcp_server_create**: *создание экземпляра DHCP-сервера*.
- **nx_dhcp_set_interface_network_parameters**: *настройка параметров DHCP-сервера для задания критически важных параметров сети для указанного интерфейса*.
- **nx_dhcp_create_server_ip_address_list**: *создание пула доступных IP-адресов для назначения интерфейсу DHCP-клиентов*.
- **nx_dhcp_clear_client_record**: *удаление записи клиента из базы данных сервера*.
- **nx_dhcp_server_delete**: *удаление экземпляра DHCP-сервера*.
- **nx_dhcp_server_start**: *запуск или возобновление обработки DHCP-сервера*.
- **nx_dhcp_server_stop**: *остановка обработки DHCP-сервера*.

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

Создание экземпляра DHCP-сервера.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр DHCP-сервера, используя созданный ранее экземпляр IP.

> [!IMPORTANT]
> Приложение должно обеспечить, чтобы созданный для службы создания экземпляров IP пул пакетов поддерживал полезные данные размером в 548 байт, не считая заголовков UDP, IP и Ethernet.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP-сервером.  
- **ip_ptr**: указатель на экземпляр IP для DHCP-сервера.
- **stack_ptr**: указатель на расположение стека для DHCP-сервера.
- **stack_size**: размер стека DHCP-сервера.
- **input_address_list**: указатель на список IP-адресов сервера.
- **name_ptr**: указатель на имя DHCP-сервера.
- **packet_pool_ptr**: указатель на пул пакетов DHCP-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): DHCP-сервер успешно создан.
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9): ошибка из-за слишком маленького размера полезных данных в пакете.
- **NX_DHCP_NO_SERVER_OPTION_LIST** (0x96): список параметров сервера пустой.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

Создание пула IP-адресов.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>Описание

Эта служба создает пул доступных IP-адресов для конкретного сетевого интерфейса, которые будут назначаться указанным DHCP-сервером. Начальный и конечный IP-адреса должны соответствовать указанному сетевому интерфейсу. Реальное число добавленных IP-адресов может оказаться меньше заявленного общего числа адресов, если будет исчерпан список IP-адресов (его размер задается в настраиваемом пользователем параметре *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE*).

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP-сервером.  
- **iface_index**: индекс, соответствующий сетевому интерфейсу.
- **start_ip_address**: первый доступный IP-адрес.
- **end_ip_address**: последний доступный IP-адрес.
- **addresses_added**: число IP-адресов, добавляемых в список.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): DHCP-сервер успешно создан.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.
- **NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99): недопустимые входные данные адреса.
- NX_DHCP_INVALID_IP_ADDRESS (0x9B): нарушение логики начального и конечного адресов.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

Удаление записи клиента из базы данных сервера.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет запись клиента из базы данных сервера.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP-сервером.  
- **dhcp_client_ptr**: указатель на DHCP-клиент, который нужно удалить.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): DHCP-сервер успешно создан.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): вызов службы не из потока.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

Настройка параметров сети в конфигурации DHCP.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>Описание

Эта служба задает значения по умолчанию для критически важных параметров сети для указанного интерфейса. DHCP-сервер будет включать эти параметры в ответы OFFER и ACK, возвращаемые в DHCP-клиент. Если параметры интерфейса устанавливает узел, на котором выполняется DHCP-сервер, то будут использоваться следующие значения по умолчанию: в качестве основного шлюза для интерфейса задается адрес самого DHCP-сервера, в качестве адреса DNS-сервера также задается адрес самого DHCP-сервера, а в качестве маски подсети задается значение, настроенное для интерфейса DHCP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на блок управления DHCP-сервером.  
- **iface_index**: индекс, соответствующий сетевому интерфейсу.
- **subnet_mask**: маска подсети для сети клиента.
- **default_gateway_address**: IP-адрес маршрутизатора клиента.
- **dns_server_address**: DNS-сервер для сети клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): DHCP-сервер успешно создан.
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.
- **NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3): недопустимые параметры сети.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

Удаление экземпляра DHCP-сервера.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр DHCP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на экземпляр DHCP-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): DHCP-сервер успешно удален.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

Запуск обработки DHCP-сервера.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает работу DHCP-сервера, в том числе создает для сервера сокет UDP, привязывает порт DHCP и ожидает получения запросов от DHCP-клиента.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер успешно запущен.  
- **NX_DHCP_ALREADY_STARTED** (0x93): экземпляр DHCP уже запущен.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>См. также:

nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

Остановка обработки DHCP-сервера.

### <a name="prototype"></a>Прототип

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает работу DHCP-сервера, в том числе получение запросов от DHCP-клиентов.

### <a name="input-parameters"></a>Входные параметры

- **dhcp_ptr**: указатель на экземпляр DHCP-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр DHCP успешно остановлен.
- **NX_DHCP_ALREADY_STARTED** (0x93): экземпляр DHCP уже запущен.
- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.
- NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
