---
title: Глава 4. Службы клиента DHCPv6 в NetX Duo для ОСРВ Azure
description: Эта глава содержит описание всех служб клиента DHCPv6 для NetX Duo в ОСРВ Azure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6caf943f990f8fe5cbd2cd6139a1253fcaf47dc207141963e31a9e31864ef839
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791743"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>Глава 4. Службы клиента DHCPv6 в NetX Duo для ОСРВ Azure

Эта глава содержит описание всех служб клиента DHCPv6 для NetX Duo в ОСРВ Azure, перечисленных ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_dhcpv6_client_create:** *создание экземпляра клиента DHCPv6* 

- **nx_dhcpv6_client_delete:** *удаление экземпляра клиента DHCPv6* 

- **nx_dhcpv6_create_client_duid:** *создание идентификатора DUID клиента DHCPv6* 

- **nx_dhcpv6_add_client_ia:** *добавление адреса удостоверения (IA) для клиента DHCPv6* 

- **nx_dhcpv6 _create_client_ia:** *добавление адреса удостоверения (IA) для клиента DHCPv6 — устаревшая операция* 

- **nx_dhcpv6_create_client_iana:** *создание ассоциации удостоверений для невременных адресов (IANA) для клиента DHCPv6* 

- **nx_dhcpv6_get_client_duid_time_id:** *получение идентификатора времени из идентификатора DUID клиента DHCPv6* 

- **nx_dhcpv6_client_set_interface:** *задание сетевого интерфейса клиента для связи с DHCPv6-сервером* 

- **nx_dhcpv6_get_IP_address:** *получение глобального IPv6-адреса, назначенного клиенту DHCPv6* 

- **nx_dhcpv6_get_lease_time_data:** *получение времени существования T1, T2, а также допустимого и предпочтительного времени существования для глобального IPv6-адреса клиента*

- **nx_dhcpv6_get_valid_ip_address_lease_time:** *получение времени существования T1, T2, а также допустимого и предпочтительного времени существования для IPv6-адреса клиента DHCPv6 по индексу адреса* 

- **nx_dhcpv6_get_iana_lease_time:** *получение значений T1 и T2 из ассоциации удостоверений (IANA), выданной в аренду клиенту DHCPv6* 

- **nx_dhcpv6_get_other_option_data:** *получение данных указанного параметра, например доменного имени или сервера часовых поясов* 

- **nx_dhcpv6_get_DNS_server_address:** *получение адреса DNS-сервера по указанному индексу в списке DNS-серверов клиента DHCPv6* 

- **nx_dhcpv6_get_time_accrued:** *получение совокупного времени, в течение которого аренда глобального IPv6-адреса была привязана к клиенту DHCPv6* 

- **nx_dhcpv6_get_time_server_address:** *получение адреса сервера времени по указанному индексу в списке серверов времени клиента DHCPv6*

- **nx_dhcpv6_get_valid_ip_address_count:** *получение числа IPv6-адресов, назначенных клиенту DHCPv6* 

- **nx_dhcpv6_reinitialize:** *повторная инициализация DHCPv6 для перезапуска конечного автомата клиента DHCPv6 и протокола DHCPv6* 

- **nx_dhcpv6_request_confirm:** *отправка запроса CONFIRM на сервер* 

- **nx_dhcpv6_request_inform_request:** *отправка сообщения INFORM REQUEST на сервер* 

- **nx_dhcpv6_request_release:** *отправка запроса RELEASE на сервер* 

- **nx_dhcpv6_request_option_DNS_server:** *добавление параметра DNS-сервера в данные клиентского запроса параметра в сообщениях запроса на сервер* 

- **nx_dhcpv6_request_option_FQDN:** *добавление параметра FQDN в данные клиентского запроса параметра в сообщениях запроса на сервер* 

- **nx_dhcpv6_request_option_domain_name:** *добавление параметра доменного имени в данные клиентского запроса параметра в сообщениях запроса на сервер* 

- **nx_dhcpv6_request_option_time_server:** *добавление параметра сервера времени в данные клиентского запроса параметра в сообщениях запроса на сервер* 

- **nx_dhcpv6_request_option_timezone:** *добавление параметра часового пояса в данные клиентского запроса параметра в сообщениях запроса на сервер* 

- **nx_dhcpv6_request_solicit:** *отправка запроса DHCPv6 SOLICIT на любой сервер в сети клиента (широковещательный режим)* 

- **nx_dhcpv6_request_solicit_rapid:** *отправка запроса DHCPv6 SOLICIT на любой сервер в сети клиента (широковещательный режим) с заданным параметром "Быстрая фиксация"* 

- **nx_dhcpv6_resume:** *возобновление обработки DHCPv6 в клиенте* 

- **nx_dhcpv6_start:** *запуск задачи клиентского потока DHCPv6. Обратите внимание, что это не эквивалентно запуску конечного автомата DHCPv6 и запрос SOLICIT при этом не отправляется.* 

- **nx_dhcpv6_stop:** *остановка задачи клиентского потока DHCPv6* 

- **nx_dhcpv6_suspend:** *приостановка задачи клиентского потока DHCPv6* 

- **nx_dhcpv6_set_time_accrued:** *задание совокупного времени аренды глобального IPv6-адреса клиента в записи клиента*

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

Создание экземпляра клиента DHCPv6

### <a name="prototype"></a>Прототип

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента DHCPv6, включая функции обратного вызова.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на блок управления DHCPv6  

- **ip_ptr**: указатель на экземпляр IP для клиента  

- **name_ptr**: указатель на имя экземпляра DHCPv6

- **packet_pool_ptr**: указатель на пул пакетов клиента

- **stack_ptr**: указатель на память стека клиента

- **stack_size**: размер памяти стека клиента

- **dhcpv6_state_change_notify**: указатель на функцию обратного вызова, вызываемую при инициации клиентом нового DHCPv6-запроса к серверу

- **dhcpv6_server_error_handler**: указатель на функцию обратного вызова, вызываемую при получении клиентом состояния ошибки с сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное создание клиента.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

Удаление экземпляра клиента DHCPv6

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр клиента DHCPv6.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное удаление DHCPv6.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

Задание сетевого интерфейса клиента для DHCPv6

### <a name="prototype"></a>Прототип

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>Описание

Эта служба задает сетевой интерфейс клиента для взаимодействия с DHCPv6-серверами по указанному входному индексу интерфейса.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **interface_index**: индекс, указывающий сетевой интерфейс

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — интерфейс успешно задан.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_INVALID_INTERFACE (0x4C) — недопустимый входной индекс интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_client_create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

Задание адреса назначения, по которому необходимо отправить сообщение DHCPv6

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>Описание

Эта служба задает адрес назначения, по которому необходимо отправить сообщение DHCPv6. Значение по умолчанию — ALL_DHCP_Relay_Agents_and_Servers (FF02::1:2).

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **destination_address**: адрес назначения

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — интерфейс успешно задан.

- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.

- NX_DHCPV6_PARAM_ERROR (0xE93) — ошибка в параметре.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_client_create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

Создание объекта DUID для клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>Описание

Эта служба создает идентификатор DUID клиента на основе входных параметров. Если входные данные времени не указаны и задан тип DUID канального уровня с временем, эта функция сама задаст уникальное время, используя случайный фактор. Типы DUID, назначенные поставщиком (корпоративные), не поддерживаются.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **duid_type**: тип идентификатора DUID (аппаратный, корпоративный и т. д.)

- **hardware_type**: сетевое оборудование, например IEEE 802

- **time**: значение, используемое при создании уникального идентификатора

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — идентификатор DUID клиента успешно создан.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) — неизвестный или неподдерживаемый тип DUID. 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) — неизвестный или неподдерживаемый аппаратный тип DUID.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

Добавление ассоциации удостоверений в клиент

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>Описание

Эта служба идентична службе *nx_dhcpv6_add_client_ia*. Она добавляет ассоциацию удостоверений клиента, заполняя запись клиента указанными параметрами. Чтобы запросить максимальное предпочтительное и допустимое время существования, задайте для этих параметров бесконечное значение. Чтобы добавить несколько адресов IA для клиента DHCPv6, присвойте параметру NX_DHCPV6_MAX_IA_ADDRESS значение, превышающее значение по умолчанию, равное 1.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **ipv6_address**: указатель на блок IP-адресов NetX Duo

- **preferred_lifetime**: время до устаревания IP-адреса

- **valid_lifetime**: время до истечения срока действия IP-адреса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес IA клиента успешно добавлен.

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) — повторяющийся адрес IA. 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) — превышено максимальное количество адресов IA, которое может храниться в клиенте.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) — недопустимый (например, равный NULL) адрес IA.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

Создание ассоциации удостоверений (невременной) для клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>Описание

Эта служба создает для клиента невременную ассоциацию удостоверений (IANA) на основе переданных параметров. Чтобы задать для параметров T1 и T2 максимальное значение (бесконечность) в запросах клиента DHCPv6, присвойте им значение NX_DHCPV6_INFINITE_LEASE. 

> [!NOTE]
> Клиент имеет только одну ассоциацию IANA.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **IA_ident**: уникальный идентификатор ассоциации удостоверений

- **T1** — когда клиент должен начать продление IPv6-адреса.

- **T2** — когда клиент должен начать повторную привязку IPv6-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ассоциация IANA успешно создана.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

Добавление ассоциации удостоверений в клиент

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>Описание

Эта служба добавляет ассоциацию удостоверений клиента, заполняя запись клиента указанными параметрами. Чтобы запросить максимальное предпочтительное и допустимое время существования, задайте для этих параметров бесконечное значение. Чтобы добавить несколько адресов IA для клиента DHCPv6, присвойте параметру NX_DHCPV6_MAX_IA_ADDRESS значение, превышающее значение по умолчанию, равное 1.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **ipv6_address**: указатель на блок IP-адресов NetX Duo

- **preferred_lifetime**: время до устаревания IP-адреса

- **valid_lifetime**: время до истечения срока действия IP-адреса 

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес IA клиента успешно добавлен.

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) — повторяющийся адрес IA. 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) — превышено максимальное количество адресов IA, которое может храниться в клиенте.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) — недопустимый (например, равный NULL) адрес IA.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.

 
### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

Извлечение идентификатора времени из идентификатора DUID клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>Описание

Эта служба извлекает поле идентификатора времени из идентификатора DUID клиента. Приложение должно сначала вызвать *nx_dhcpv6_create_client_duid*, чтобы заполнить идентификатор DUID клиента в экземпляре клиента DHCPv6, иначе это поле будет иметь значение NULL. Цель состоит в том, чтобы приложение сохраняло эти данные и предоставляло серверу один и тот же идентификатор DUID клиента, включая поле времени, после перезагрузки.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **time_id**: указатель на поле времени в идентификаторе DUID клиента

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные по аренде IP-адреса успешно получены.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

Получение глобального IPv6-адреса клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>Описание

Эта служба получает глобальный IPv6-адрес клиента. Если у клиента нет допустимого адреса, возвращается состояние ошибки. Если у клиента более одного глобального IPv6-адреса, возвращается основной IPv6-адрес.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **ip_address**: указатель на IPv6-адрес

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — IPv6-адрес успешно назначен.

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) — недопустимый IPv6-адрес.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

Получение данных о времени аренды адреса IA клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>Описание

Эта служба получает данные о времени аренды глобального адреса IA клиента. Если адрес IA клиента находится в недопустимом состоянии, то время устанавливается в значение 0 и возвращается состояние успешного завершения. Если у клиента более одного глобального IPv6-адреса, возвращаются данные основного адреса IA.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **T1**: указатель на время продления адреса IA

- **T2**: указатель на время повторной привязки адреса IA

- **preferred_lifetime**: указатель на время, когда адрес IA устаревает

- **valid_lifetime**: указатель на время, когда истекает срок действия адреса IA

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные по аренде адреса IA успешно получены.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana lease_time

Получение данных о времени аренды IANA клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>Описание

Эта служба получает данные о времени аренды глобальной ассоциации IANA клиента (T1 и T2). Если ни один из адресов IANA клиента не находится в допустимом состоянии, время устанавливается в нулевое значение и возвращается состояние успешного завершения. Если у клиента более одного глобального IPv6-адреса, возвращаются данные основного адреса IA.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **T1**: указатель на время, когда должно быть начато продление аренды

- **T2**: указатель на время, когда должна быть начата повторная привязка аренды

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные по аренде IANA успешно получены.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

Получение числа допустимых адресов IA клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>Описание

Эта служба получает количество допустимых IPv6-адресов клиента. Допустимый IPv6-адрес привязывается к клиенту (назначается ему) и регистрируется в экземпляре IP.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **address_count**: указатель на число возвращаемых адресов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные по аренде IANA успешно получены.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

Получение данных об адресе IA клиента по индексу адреса

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>Описание

Эта служба получает адрес IA клиента и данные по аренде по индексу адреса. Если указан недопустимый индекс или если IPv6-адрес по этому индексу недопустим, служба возвращает состояние ошибки NX_DHCPV6_IA_ADDRESS_NOT_VALID.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **address_index**: индекс в таблице адресов IA DHCPv6

- **ip_address**: указатель на получаемый IPv6-адрес

- **preferred_lifetime**: указатель на время, когда адрес IA устаревает

- **valid_lifetime**: указатель на время, когда истекает срок действия адреса IA

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные IANA успешно получены.

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) — недопустимый индекс, или нет недопустимого IPv6-адреса по указанному индексу. 

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

Получение адреса DNS-сервера 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>Описание

Эта служба получает IPv6-адрес DNS-сервера по указанному индексу в списке клиента. Если в списке нет адреса сервера по данному индексу, возвращается ошибка. Индекс не может превышать размер списка DNS-серверов, заданный в настраиваемом пользователем параметре NX_DHCPV6_NUM_DNS_SERVERS.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **index**: индекс в списке DNS-серверов

- **server_address**: указатель на буфер адресов сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно получен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

Получение данных параметра DHCPv6 

### <a name="prototype"></a>Прототип

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>Описание

Эта служба получает данные параметра DHCPv6 из сообщения DHCPv6 по указанному коду параметра.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **option_code**: код параметра, данные которого нужно получить

- **buffer**: указатель на буфер для копирования данных 

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные параметра успешно получены.

- **NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) — неизвестный или неподдерживаемый код параметра.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

Получение накопленного времени аренды для IP-адреса клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>Описание

Эта служба получает накопленное время аренды IPv6-адреса клиента. Функция ищет первый допустимый адрес, проверяя все IPv6-адреса, назначенные клиенту. Если допустимых адресов не найдено, возвращается нулевое значение накопленного времени.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **time_accrued**: указатель на накопленное время аренды IP-адреса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — накопленное время успешно получено.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

Получение адреса сервера времени 

### <a name="prototype"></a>Прототип

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>Описание

Эта служба получает IPv6-адрес сервера времени по указанному индексу в списке клиента. Если в списке нет адреса сервера по данному индексу, возвращается ошибка. Индекс не может превышать размер списка серверов времени, заданный в настраиваемом пользователем параметре NX_DHCPV6_NUM_TIME_SERVERS.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **index**: индекс в списке серверов времени

- **server_address**: указатель на буфер адресов сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно получен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

Удаление IP-адреса клиента из таблицы IP-адресов

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба повторно инициализирует клиент для перезапуска конечного автомата и протокола DHCPv6. Если клиент ранее не запустил конечный автомат DHPCv6 или ему не были назначены IPv6-адреса, делать это не обязательно. Очищаются как адреса, сохраненные в клиенте DHCPv6, так и адреса, зарегистрированные в экземпляре IP.

> [!NOTE]
> Приложение по-прежнему должно запустить клиент DHCPv6 с помощью службы *nx_dhcpv6_start* и инициировать запрос на назначение IPv6-адреса путем вызова *nx_dhcpv6_request_solicit*.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес успешно удален.

- **NX_DHCPV6_ALREADY_STARTED** (0xE91) — клиент DHCPv6 уже запущен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

Обработка состояния CONFIRM клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос CONFIRM. При получении ответа от сервера клиент DHCPv6 обновляет параметры аренды с использованием полученных данных.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сообщение CONFIRM успешно отправлено и обработано.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

Обработка состояния INFORM REQUEST клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение INFORM REQUEST. Если получен ответ, он обрабатывается с целью определить, является ли он допустимым и одобрил ли сервер запрос. Затем при необходимости экземпляр клиента обновляется с использованием сведений с сервера.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сообщение INFORM REQUEST успешно создано и обработано.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

Добавление DNS-сервера в запрос параметра DHCPv6

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба добавляет параметр для запроса сведений о DNS-сервере в запрос параметра DHCPv6. Если ответ от сервера включает в себя данные о DNS-сервере, клиент сохранит DNS-сервер при наличии места. Количество DNS-серверов, которое может хранить клиент, определяется настраиваемым параметром NX_DHCPV6_NUM_DNS_SERVERS. Значение по умолчанию — 2.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — параметр DNS-сервера включен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

Добавление параметра полного доменного имени в список запросов параметров

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>Описание

Эта служба добавляет параметр для добавления полного доменного имени клиента в запрос параметра DHCPv6. Есть три варианта параметра полного доменного имени.

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 — обновление сопоставления полного доменного имени и IPv6-адресов, используемых клиентом.

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 — обновление сопоставления полного доменного имени и IPv6-адресов, используемых клиентом, на сервере.

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 — сервер не выполняет обновлений DNS от имени клиента.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **domain_name**: строка, содержащая доменное имя

- **op**: тип применяемого параметра полного доменного имени (см. список выше)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — параметр полного доменного имени включен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

Добавление параметра доменного имени в запрос параметра DHCPv6

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба добавляет параметр доменного имени в запрос параметра в сообщениях клиента. Если ответ сервера содержит данные доменного имени, клиент сохранит их при условии, что размер доменного имени не превышает размер буфера для хранения доменного имени. Размер буфера — это настраиваемый параметр (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) со значением по умолчанию 30 байт.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — набор параметров доменного имени.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

Указание данных сервера времени в качестве необязательного запроса

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба добавляет параметр для сведений о сервере времени в запрос параметра в сообщениях клиента. Если ответ от сервера включает в себя данные о сервере времени, клиент сохранит сервер времени при наличии места. Количество серверов времени, которое может хранить клиент, определяется настраиваемым параметром

NX_DHCPV6_NUM_TIME_SERVERS. Его значение по умолчанию — 1.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — добавлен параметр сервера времени.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

Указание данных о часовом поясе в качестве необязательного запроса

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба добавляет параметр для запроса сведений о часовом поясе в запрос параметра клиента. Если ответ сервера содержит сведения о часовом поясе, клиент сохранит их при условии, что их размер не превышает размера буфера для хранения часового пояса. Размер буфера — это настраиваемый параметр (NX_DHCPV6_TIME_ZONE_BUFFER_SIZE) со значением по умолчанию 10 байт.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — добавлен параметр часового пояса.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

Отправка сообщения DHCPv6 RELEASE

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение RELEASE в сети клиента. Если сообщение успешно отправлено, возвращается состояние успешного завершения. Успешное завершение не означает, что клиент получил ответ или ему уже был предоставлен IPv6-адрес. Задача потока клиента DHCPv6 ожидает ответа от DHCPv6-сервера. Если он получен, клиент проверяет его допустимость и сохраняет данные в записи клиента.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сообщение RELEASE успешно отправлено.

- **NX_DHCPV6_NOT_STARTED** (0xE92) — задача клиента DHCPv6 не запущена.

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) — адрес не привязан к клиенту.

- **NX_INVALID_INTERFACE** (0x4C) — не найдено в таблице IP-адресов.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

Отправка сообщения SOLICIT

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение SOLICIT в сеть. Если сообщение успешно отправлено, возвращается состояние успешного завершения. Успешное завершение не означает, что клиент получил ответ или ему уже был предоставлен IPv6-адрес. Задача потока клиента DHCPv6 ожидает ответа (сообщения ADVERTISE) от DHCPv6-сервера. Если он получен, клиент проверяет его допустимость, сохраняет данные в записи клиента и переходит в состояние REQUEST.

> [!NOTE] 
> Если задан параметр быстрой фиксации, то при получении допустимого сообщения ADVERTISE от сервера клиент DHCPv6 сразу переходит в состояние привязки. Дополнительные сведения см. в описании службы *nx_dhcpv6_request_solicit_rapid*.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сообщение SOLICIT успешно отправлено.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Отправка сообщения SOLICIT с параметром быстрой фиксации

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение SOLICIT в сеть с заданным параметром быстрой фиксации. Если сообщение успешно отправлено, возвращается состояние успешного завершения. Успешное завершение не означает, что клиент получил ответ или ему уже был предоставлен IPv6-адрес. Задача потока клиента DHCPv6 ожидает ответа (сообщения ADVERTISE) от DHCPv6-сервера. Если он получен, клиент проверяет его допустимость, сохраняет данные в записи клиента и переходит в состояние BOUND.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сообщение SOLICIT успешно отправлено.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

Возобновление задачи клиента DHCPv6 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба возобновляет задачу потока клиента DHCPv6. Текущее состояние клиента DHCPv6 обрабатывается (например, BOUND, SOLICIT).

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — работа клиента успешно возобновлена.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_time_accrued

Задание накопленного времени аренды для IP-адреса клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>Описание

Эта служба задает накопленное время аренды глобального IP-адреса клиента с момента назначения сервером. Следует использовать только в том случае, если клиент в настоящее время привязан к назначенному IPv6-адресу.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

- **time_accrued**: накопленное время аренды IP-адреса

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — накопленное время успешно задано.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

Запуск задачи клиента DHCPv6 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает задачу клиента DHCPv6 и подготавливает клиент к выполнению протокола DHCPv6. Она проверяет, имеет ли экземпляр клиента достаточно информации (например, DUID клиента), создает и привязывает сокет UDP для отправки и получения сообщений DHCPv6, а также активирует таймеры для отслеживания времени сеанса и истечения срока действия аренды IPv6.

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — клиент успешно запущен.

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) — у клиента отсутствуют обязательные параметры.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

Остановка задачи клиента DHCPv6 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает задачу клиента DHCPv6 и очищает счетчик ретрансляций и максимальный интервал ретрансляции, отключает таймеры сеанса и аренды и отменяет привязку порта сокета для клиента DHCPv6. Чтобы перезапустить клиент, необходимо сначала остановить и при необходимости повторно инициализировать клиент, прежде чем начинать другой сеанс с любым DHCPv6-сервером. Дополнительные сведения см. в разделе "Небольшой пример".

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — клиент успешно остановлен.

- **NX_DHCPV6_NOT_STARTED** (0xE92) — поток клиента не запущен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

Приостановка задачи клиента DHCPv6 

### <a name="prototype"></a>Прототип

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>Описание

Эта служба приостанавливает задачу клиента DHCPv6 и все запросы, которые находились в процессе обработки. Таймеры отключаются, и клиент переводится в состояние "не выполняется".

### <a name="input-parameters"></a>Входные параметры

- **dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — работа клиента успешно приостановлена.

- **NX_DHCPV6_NOT_STARTED** (0XE92) — не удается приостановить работу клиента, так как он не запущен.

- NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>См. также:

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
