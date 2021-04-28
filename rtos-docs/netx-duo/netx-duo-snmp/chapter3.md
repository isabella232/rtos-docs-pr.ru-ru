---
title: Глава 3. Описание служб агентов SNMP для NetX Duo в ОСРВ Azure
description: Эта часть содержит описание всех служб агентов SNMP для NetX Duo, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814564"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>Глава 3. Описание служб агентов SNMP для NetX Duo в ОСРВ Azure

Эта часть содержит описание всех служб агентов SNMP для NetX Duo в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" в описаниях API ниже значения, выделенные **полужирным шрифтом**, не затрагиваются определением параметра **NX_DISABLE_ERROR_CHECKING**, который используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены.

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *Указание ключа проверки подлинности (только SNMP версии 3) для сообщений ловушки*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *Указание ключа проверки подлинности (только SNMP версии 3) для сообщений-ответов*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *Получение имени сообщества*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *Задание обработчика контекста (только для SNMP версии 3)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *Задание имени контекста (только для SNMP версии 3)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *Создание агента SNMP*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *Получение версии SNMP полученного пакета*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *Указание типа последнего запроса SNMP: GET или SET*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *Определение того, соответствует ли строка частной строке агента*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *Определение того, соответствует ли строка общедоступной строке агента*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *Настройка сетевого интерфейса для обмена сообщениями SNMP*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *Задание частной строки доступа агента SNMP*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *Задание общедоступной строки доступа агента SNMP*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *Задание статуса агента SNMP для всех версий SNMP*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *Удаление агента SNMP*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *Создание ключа md5 (только SNMP версии 3)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *Создание ключа md5 (только SNMP версии 3)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *Указание ключа шифрования (только SNMP версии 3) для сообщений ловушки*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *Указание ключа шифрования (только SNMP версии 3) для сообщений-ответов*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *Создание ключа sha (только SNMP версии 3)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *Создание ключа sha (только SNMP версии 3)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *Запуск агента SNMP*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *Остановка агента SNMP*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *Отправка SNMP-ловушки версии 1 (только IPv4)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *Отправка SNMP-ловушки версии 2 (только IPv4)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *Отправка SNMP-ловушки версии 2 (только IPv4) с указанием OID*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *Отправка SNMP-ловушки версии 3 (только IPv4)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *Отправка SNMP-ловушки версии 2 (только IPv4) с указанием OID*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *Отправка SNMP-ловушки версии 1 (IPv4 и IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *Отправка SNMP-ловушки версии 2 (IPv4 и IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *Отправка SNMP-ловушки версии 2 (IPv4 или IPv6) с указанием OID*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *Отправка SNMP-ловушки версии 3 (IPv4 и IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *Отправка SNMP-ловушки версии 2 (IPv4 или IPv6) с указанием OID*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *Задание количества перезагрузок*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *Сравнение двух объектов*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *Сравнение двух объектов*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *Копирование объекта*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *Копирование объекта*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *Получение объекта счетчика*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *Задание объекта счетчика*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *Получение 64-разрядного объекта счетчика*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *Настройка 64-разрядного объекта счетчика*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *Задание значения окончания MIB*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *Получение объекта датчика*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *Задание объекта датчика*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *Получение идентификатора объекта*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *Задание идентификатора объекта*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *Получение объекта целого числа*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *Задание объекта целого числа*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *Получение объекта IP-адреса (только IPv4)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *Задание объекта IP адреса (только IPv4)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *Получение объекта IP-адреса (только IPv6)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *Задание объекта IP-адреса (только IPv6)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *Задание значения "экземпляр отсутствует"*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *Задание значения "не найдено"*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *Получение объекта октетной строки*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *Задание объекта октетной строки*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *Получение объекта строки ASCII*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *Задание объекта строки ASCII*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *Получение объекта timetics*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *Задание объекта timetics*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
Указание ключа проверки подлинности для сообщений ловушки

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Описание

Эта служба позволяет указать ключ, используемый для настройки параметров проверки подлинности в заголовке безопасности SNMP версии 3 в сообщениях ловушки. Если задать для ключа значение NX_NULL, проверка подлинности будет отключена.

> [!NOTE]
> Ключ нужно создать заранее. См. nx_snmp_agent_md5_key_create или nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **key** — указатель на ранее созданный ключ MD5 или SHA.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ключ проверки подлинности успешно задан.
- **NX_NOT_ENABLED** (0x14) — защита SNMP отключена. 
- **NX_PTR_ERROR** (0x07) — недопустимый указатель агента SNMP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
Указание ключа проверки подлинности для сообщений-ответов

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Описание

Эта служба позволяет указать ключ, используемый для параметров проверки подлинности, в параметре безопасности SNMP версии 3 для всех запросов, которые будут выполняться после задания этого ключа. Если задать для ключа значение NX_NULL, проверка подлинности будет отключена.

> [!NOTE]
> Ключ нужно создать заранее. См. nx_snmp_agent_md5_key_create или nx_snmp_agent_sha_key_create.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **key** — указатель на ранее созданный ключ MD5 или SHA.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ключ SNMP успешно задан.
- **NX_NOT_ENABLED** (0x14) — защита SNMP отключена.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель агента SNMP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
Получение имени сообщества

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>Описание

Эта служба позволяет получить имя сообщества из самого последнего запроса SNMP, полученного агентом SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **community_string_ptr** — указатель на указатель строки для возврата строки доступа агента SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сведения о сообществе SNMP успешно получено.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
Указание типа последнего запроса SNMP: GET или SET

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>Описание

Эта служба указывает на тип самого последнего запроса из диспетчера SNMP: GET (GET, GETNEXT или GETBULK) или SET. Ее следует использовать с ответным вызовом username, в котором приложение SNMP версии 1 или SNMP версии 2 будет сравнивать полученную строку доступа с общедоступной строкой агента SNMP, если типом запроса является GET, или с частной строкой агента SNMP, если — SET.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **is_get_type** — указатель на состояние типа запроса:  
NX_TRUE, если типом является GET;  
NX_FALSE, если типом является SET.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — тип возвращаемого значения получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
Задание обработчика контекста (только для SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>Описание

Эта служба задает обработчик контекста для агента SNMP. Применима только для обработки SNMP версии 3. Если приложение использует проверку подлинности и шифрование, эту службу нужно вызывать перед созданием ключей безопасности, так как идентификатор обработчика контекста используется в процессе создания ключа. В противном случае протокол SNMP NetX Duo предоставит в начале *nxd_snmp.c:* стандартный идентификатор обработчика контекста

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **context_engine** — указатель на строку обработчика контекста.
- **context_engine_size** — размер строки обработчика контекста. Обратите внимание, что максимальное число байтов в обработчике контекста определяет служба NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — обработчик контекста SNMP успешно задан.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 3 не включен.
- **NX_SNMP_ERROR** (0x100) — ошибка при указании размера обработчика контекста.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
Задание имени контекста (только для SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>Описание

Эта служба задает имя контекста для агента SNMP. Применима только для обработки SNMP версии 3. Если не вызвать эту службу, агент SNMP NetX Duo оставит поле имени контекста пустым.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **context_name** — указатель на строку имени контекста.
- **context_name_size** — размер строки имени контекста. Обратите внимание, что максимальное число байтов в имени контекста определяет служба NX_SNMP_MAX_CONTEXT_STRING.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — имя контекста SNMP успешно задано.
- **NX_SNMP_ERROR** (0x100) — ошибка при указании размера имени контекста.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
Создание агента SNMP

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a>Описание

Эта служба создает агент SNMP в указанном экземпляре IP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **snmp_agent_name** — указатель на строку имени агента SNMP.
- **ip_ptr** — указатель на экземпляр IP-адреса.
- **stack_ptr** — указатель на указатель стека потока агента SNMP.
- **stack_size** — размер стека в байтах.
- **pool_ptr** — указатель на пул пакетов по умолчанию для этого агента SNMP.
- **snmp_agent_username_process** — указатель функции на подпрограмму обработки имени пользователя приложения.
- **snmp_agent_get_process** — указатель функции на подпрограмму обработки запроса GET приложения.
- **snmp_agent_getnext_process** — указатель функции на подпрограмму обработки запроса GETNEXT приложения.
- **snmp_agent_set_process** — указатель функции на подпрограмму обработки запроса SET приложения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — агент SNMP успешно создан.
- **NX_SNMP_ERROR** (0x100) — ошибка при создании агента SNMP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
Получение версии пакета SNMP

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>Описание

Эта служба позволяет получить версию SNMP, проанализированную из последнего полученного пакета SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **version** — указатель на версию SNMP, проанализированную из полученного пакета SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сведения о версии SNMP успешно получены.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
Проверка того, соответствует ли частная строка частной строке агента

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>Описание

Эта служба сравнивает входную строку доступа, оканчивающуюся нулевым символом, с частной строкой агента SNMP и указывает, совпадают ли они.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **community_string** — указатель на строку для сравнения.
- **is_private** — указатель на результат сравнения  
NX_TRUE — строка совпадает;  
NX_FALSE — строка не совпадает.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сравнение успешно выполнено.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
Проверка того, соответствует ли полученная общедоступная строка общедоступной строке агента

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>Описание

Эта служба сравнивает входную строку доступа, оканчивающуюся нулевым символом, с общедоступной строкой агента SNMP и указывает, совпадают ли они.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **community_string** — указатель на строку для сравнения.
- **is_public** — указатель на результат сравнения  
NX_TRUE — строка совпадает;  
NX_FALSE — строка не совпадает.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сравнение успешно выполнено.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
Задание статуса агента SNMP для каждой версии SNMP

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>Описание

Эта служба задает состояние (включено или отключено) для каждой из версий SNMP (версии 1, 2 и 3) в агенте SNMP. Обратите внимание, что эти параметры времени выполнения будут переопределять настраиваемые параметры, такие как NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 и NX_SNMP_DISABLE_V3. По умолчанию агент SNMP поддерживает все три версии.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **enabled_v1** — задает для состояния включения SNMP версии 1 значение "Вкл." или "Выкл.".
- **enabled_v2** — задает для состояния включения SNMP версии 2 значение "Вкл." или "Выкл.".
- **enabled_v3** — задает для состояния включения SNMP версии 3 значение "Вкл." или "Выкл.".

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — версия SNMP успешно задана.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
Задание частной строки агента SNMP

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>Описание

Эта служба задает как частную строку доступа агента SNMP входную строку, оканчивающуюся нулевым символом. Значение по умолчанию — NULL (без набора частных строк), следовательно, любой пакет SNMP, полученный с помощью "частной" строки доступа, не будет приниматься агентом SNMP для доступа на чтение и запись. Входная строка должна быть меньше пользовательского настраиваемого параметра NX_SNMP_MAX_USER_NAME-1 или быть равной ему (чтобы обеспечить место для завершающего нулевого символа).

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **community_string** — указатель на частную строку для назначения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — частная строка успешно задана.
- **NX_SNMP_ERROR_TOOBIG** (0x01) — размер строки слишком большой. 
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
Задание общедоступной строки агента SNMP

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>Описание

Эта служба задает как общедоступную строку доступа агента SNMP входную строку, оканчивающуюся нулевым символом. Строка доступа должна быть меньше пользовательского настраиваемого параметра NX_SNMP_MAX_USER_NAME-1 или быть равной ему (чтобы обеспечить место для завершающего нулевого символа).

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **community_string** — указатель на общедоступную строку для назначения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — общедоступная строка успешно задана.
- **NX_SNMP_ERROR_TOOBIG** (0x01) — размер строки слишком большой.
- **NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
Удаление агента SNMP

### <a name="prototype"></a>Прототип

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Описание

Эта служба удаляет созданный ранее агент SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — агент SNMP успешно удален.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
Задание сетевого интерфейса агента SNMP

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>Описание

Эта служба задает сетевой интерфейс SNMP для агента SNMP, как указано в индексе входного интерфейса. Эта служба будет полезна только для ведущих приложений SNMP в NetX Duo 5.6 или более поздней версии, поддерживающих несколько сетевых интерфейсов. Для основного интерфейса значение по умолчанию (если его не задаст узел) будет равно нулю.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **If_index** — индекс, указывающий интерфейс SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — интерфейс SNMP успешно задан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
Создание ключа md5 (только SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>Описание

Эта служба создает ключ MD5, который можно использовать для проверки подлинности и шифрования.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_snmp_agent_md5_key_create_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **password** — указатель на строку пароля.
- **destination_key** — указатель на структуру данных ключа SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ключ успешно создан.
- **NX_NOT_ENABLED** (0x14) — средства безопасности не включены.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
Создание ключа md5 (только SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>Описание

Эта служба создает ключ MD5, который можно использовать для проверки подлинности и шифрования.

Эта служба заменяет *nx_snmp_agent_md5_key_create ().* При использовании этой версии нужно, чтобы вызывающий объект предоставлял сведения о длине пароля.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **password** — указатель на строку пароля.
- **password_length** — длина строки пароля.
- **destination_key** — указатель на структуру данных ключа SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ключ успешно создан.
- **NX_NOT_ENABLED** (0x14) — средства безопасности не включены.
- **NX_SNMP_FAILED** (0x102) — ошибка протокола SNMP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
Указание ключа шифрования для сообщений о ловушке

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>Описание

Эта служба указывает, что ранее созданный ключ конфиденциальности следует использовать для шифрования и расшифровки сообщений о ловушках SNMP версии 3.

> [!NOTE]
> *Ключ проверки подлинности нужно создавать заранее. Для обеспечения конфиденциальности (шифрования) SNMP версии 3 требуется проверка подлинности. Дополнительные сведения см. в описании nx_snmp_agent_auth_trap_key_use.*

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **key** — указатель на ранее созданный ключ.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — набор ключей конфиденциальности успешно задан.
- **NX_NOT_ENABLED** (0x14) — средства безопасности не включены.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
Указание ключа шифрования для сообщений-ответов

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>Описание

Эта служба указывает, что ранее созданный ключ следует использовать для шифрования и расшифровки сообщений-ответов SNMP версии 3.

> [!NOTE]
> *Ключ проверки подлинности следует указывать заранее. Ключ проверки подлинности нужно создать, чтобы обеспечить шифрование SNMP версии 3. Дополнительные сведения см. в описании nx_snmp_agent_authentiation_key_use.*

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **key** — указатель на ранее созданный ключ.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — набор ключей конфиденциальности успешно задан.
- **NX_NOT_ENABLED** (0x14) — средства безопасности не включены.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
Создание ключа SHA (только SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>Описание

Эта служба создает ключ SHA, который можно использовать для проверки подлинности и шифрования.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_snmp_agent_sha_key_create_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **password** — указатель на строку пароля.
- **destination_key** — указатель на структуру данных ключа SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ключ успешно создан.
- **NX_SNMP_ERROR** (0x100) — ошибка при создании ключа.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель агента или ключа SNMP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
Создание ключа SHA (только SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>Описание

Эта служба создает ключ SHA, который можно использовать для проверки подлинности и шифрования.

Эта служба заменяет *nx_snmp_agent_sha_key_create ().* При использовании этой версии нужно, чтобы вызывающий объект предоставлял сведения о длине пароля.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **password** — указатель на строку пароля.
- **password_length** — длина строки пароля.
- **destination_key** — указатель на структуру данных ключа SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — ключ успешно создан.
- **NX_SNMP_ERROR** (0x100) — ошибка при создании ключа.
- **NX_SNMP_FAILED** (0x102) — ключ не удалось создать.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель агента или ключа SNMP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
Запуск агента SNMP 

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Описание

Эта служба связывает сокет UDP и порт 161 SNMP и запускает задачу потока агента SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешный запуск агента SNMP.
- **NX_SNMP_ERROR** (0x100) — ошибка при запуске агента SNMP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
Остановка агента SNMP 

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>Описание

Эта служба останавливает задачу потока агента SNMP и отменяет привязку между сокетом UDP и портом SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешная остановка агента SNMP.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель агента SNMP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
Отправка SNMP-ловушки версии 1 *(только IPv4)*

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку диспетчеру SNMP по указанному адресу IPv4. Предпочтительный метод отправки SNMP-ловушек в NetX Duo — использование службы *nxd_snmp_agent_trap_send*. *nx_snmp_agent_trap_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — адрес IPv4 диспетчера SNMP.
- **enterprise** — строка идентификатора корпоративного объекта (sysObectID).
- **trap_type** — тип запрашиваемой ловушки, например:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** — код ловушки.
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 1 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
Отправка SNMP-ловушки версии 1 *(IPv4 и IPv6)*

### <a name="prototype"></a>Прототип

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку диспетчеру SNMP по указанному IP-адресу. Эквивалентом отправки SNMP-ловушки в NetX является использование службы *nxd_snmp_agent_trap_send*.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — адрес IPv4 или IPv6 диспетчера SNMP.
- **enterprise** — строка идентификатора корпоративного объекта (sysObectID).
- **trap_type** — тип запрашиваемой ловушки, например:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** — код ловушки.
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 1 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
Отправка SNMP-ловушки версии 2 (только IPv4)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 2 диспетчеру SNMP по указанному адресу IPv4. Предпочтительный метод отправки SNMP-ловушек в NetX Duo — использование службы *nxd_snmp_agent_trapv2_send*. *nx_snmp_agent_trapv2_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — адрес IPv4 диспетчера SNMP.
- **community** — имя для доступа (имя пользователя).
- **trap_type** —  
   Тип запрошенной ловушки. Стандартными событиями являются:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Для защищаемых данных:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)
   
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 2 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
Отправка SNMP-ловушки версии 2 с непосредственным указанием OID 

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 2 в диспетчер SNMP по указанному IP-адресу (только IPv4) и позволяет вызывающему объекту напрямую указывать OID. Предпочтительный метод отправки SNMP-ловушек с указанием OID в NetX Duo — использование службы *nxd_snmp_agent_trapv2_oid_send*. *nx_snmp_agent_trapv2_oid_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — IP-адрес диспетчера SNMP.
- **community** — имя для доступа (имя пользователя).
- **oid** — указатель на буфер, содержащий OID.
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
Отправка SNMP-ловушки версии 2 (IPv4 и IPv6)

### <a name="prototype"></a>Прототип

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 2 диспетчеру SNMP по указанному IP-адресу.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — IP-адрес (IPv4 или IPv6) диспетчера SNMP.
- **community** — имя для доступа (имя пользователя).
- **trap_type** —  
   Тип запрошенной ловушки. Стандартными событиями являются:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Для защищаемых данных:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)

- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 2 не включен.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) — неподдерживаемая версия IP-адреса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
Отправка SNMP-ловушки версии 2 с непосредственным указанием OID 

### <a name="prototype"></a>Прототип

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 2 диспетчеру SNMP по указанному IP-адресу (IPv4 или IPv6) и позволяет вызывающему объекту напрямую указывать OID.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — IP-адрес диспетчера SNMP (IPv4 или IPv6).
- **community** — имя для доступа (имя пользователя).
- **oid** — указатель на буфер, содержащий OID.
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
Отправка SNMP-ловушки версии 3 (только IPv4)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 3 диспетчеру SNMP по указанному адресу IPv4. Предпочтительный метод отправки SNMP-ловушек в NetX Duo — использование службы *nxd_snmp_agent_trapv3_send*. *nx_snmp_agent_trapv3_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — адрес IPv4 диспетчера SNMP.
- **username** — имя для доступа (имя пользователя).
- **trap_type** —  
   тип запрошенной ловушки. Стандартными событиями являются:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   Для защищаемых данных:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)

- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 3 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
Отправка SNMP-ловушки версии 3 с непосредственным указанием OID 

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 3 диспетчеру SNMP по указанному IP-адресу (только IPv4) и позволяет вызывающему объекту напрямую указывать OID. Предпочтительный метод отправки SNMP-ловушек с указанием OID в NetX Duo — использование службы *nxd_snmp_agent_trapv3_oid_send*. *nx_snmp_agent_trapv3_oid_send* входит в NetX Duo и обеспечивает поддержку существующих приложений агента SNMP.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — IP-адрес диспетчера SNMP.
- **username** — имя для доступа (имя пользователя).
- **oid** — указатель на буфер, содержащий OID.
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.
- **NX_OPTION_ERROR** (0x0a) — недопустимый параметр.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
Отправка SNMP-ловушки версии 3 (IPv4 и IPv6)

### <a name="prototype"></a>Прототип

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку диспетчеру SNMP по указанному IP-адресу. Эта ловушка, по сути, аналогична SNMP-ловушке версии 2, за исключением того, что в ней формат сообщений ловушки содержится в PDU SNMP версии 3.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — IP-адрес (IPv4 или IPv6) диспетчера SNMP.
- **username** — имя для доступа (имя пользователя).
- **trap_type** —  
   тип запрошенной ловушки. Стандартными событиями являются:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   Для защищаемых данных:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (определяется в *nxd_snmp.h*)

- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_NOT_ENABLED** (0x14) — протокол SNMP версии 3 не включен.
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) — неподдерживаемая версия IP-адреса.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
Отправка SNMP-ловушки версии 3 с непосредственным указанием OID 

### <a name="prototype"></a>Прототип

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>Описание

Эта служба отправляет SNMP-ловушку версии 3 диспетчеру SNMP по указанному IP-адресу (IPv4 или IPv6) и позволяет вызывающему объекту напрямую указывать OID.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **ip_address** — указатель на IP-адрес диспетчера SNMP.
- **username** — имя пользователя (имя для доступа).
- **oid** — указатель на буфер, содержащий OID.
- **elapsed_time** — система времени исправна (sysUpTime).
- **object_list_ptr** — массив объектов и связанные с ними значения, включаемые в SNMP-ловушку. Список завершается значением NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — SNMP-ловушка успешно отправлена.
- **NX_SNMP_ERROR** (0x100) — ошибка отправки SNMP-ловушки.
- **NX_PTR_ERROR** (0x16) — недопустимый указатель на агент SNMP или параметр.
- **NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес назначения.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
Задание количества перезагрузок (если включен протокол SNMP версии 3)

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>Описание

Эта служба задает количество перезагрузок, записанных агентом SNMP. Эта служба доступна, только если для агента SNMP включен протокол SNMP версии 3, так как счетчик загрузок поддерживается только в протоколе SNMP версии 3.

### <a name="input-parameters"></a>Входные параметры

- **agent_ptr** — указатель на блок управления агента SNMP.
- **boots** — значение, которое нужно задать для счетчика загрузок агента SNMP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — количество загрузок успешно задано.
- **NX_SNMP_ERROR** (0x100) — ошибка при установке счетчика загрузки.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
Сравнение двух объектов 

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>Описание

Эта служба сравнивает указанный идентификатор объекта с идентификатором эталонного объекта. Оба идентификатора объекта указаны в нотации SMI ASCII, например, оба объекта должны начинаться со строки ASCII "1.3.6".

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_snmp_object_compare_extended ().*

### <a name="input-parameters"></a>Входные параметры

- **object** — указатель на идентификатор объекта.
- **reference_object** — указатель на идентификатор эталонного объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект соответствует эталонному объекту.
- **NX_SNMP_NEXT_ENTRY** (0x101) — объект меньше эталонного объекта.
- **NX_SNMP_ERROR** (0x100) — объект больше эталонного объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
Сравнение двух объектов 

### <a name="prototype"></a>Прототип

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>Описание

Эта служба сравнивает указанный идентификатор объекта с идентификатором эталонного объекта. Оба идентификатора объекта указаны в нотации SMI ASCII, например, оба объекта должны начинаться со строки ASCII "1.3.6".

Эта служба заменяет *nx_snmp_object_compare().* В этой версии требуется, чтобы вызывающие объекты предоставляли сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **request_object** — указатель на идентификатор объекта запроса.
- **request_object_length** — длина идентификатора объекта запроса.
- **reference_object** — указатель на идентификатор эталонного объекта.
- **reference_object_length** — длина идентификатора объекта запроса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект соответствует эталонному объекту.
- **NX_SNMP_NEXT_ENTRY** (0x101) — объект меньше эталонного объекта.
- **NX_SNMP_ERROR** (0x100) — объект больше эталонного объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
Копирование объекта 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>Описание

Эта служба копирует исходный объект в целевой в нотации SIM ASCII.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_snmp_object_copy_extended().*

### <a name="input-parameters"></a>Входные параметры

- **source_object_name** — указатель на идентификатор исходного объекта.
- **destination_object_name** — указатель на идентификатор целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **Размер** — число байтов, скопированных в имя назначения. При наличии ошибки возвращаемым значением будет ноль.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
Копирование объекта 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>Описание

Эта служба копирует исходный объект в целевой в нотации SIM ASCII.

Эта служба заменяет *nx_snmp_object_copy().* В этой версии требуется, чтобы вызывающие объекты предоставляли сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **source_object_name** — указатель на идентификатор исходного объекта.
- **source_object_name_length** — длина идентификатора исходного объекта.
- **destination_object_name_buffer** — указатель на буфер целевого объекта.
- **destination_object_name_buffer_size** — размер буфера целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **Размер** — число байтов, скопированных в имя назначения. При наличии ошибки возвращаемым значением будет ноль.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
Получение объекта счетчика 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Описание

Эта служба получает объект счетчика по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник счетчика.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект счетчика успешно получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
Задание объекта счетчика 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба устанавливает счетчик по адресу, предоставленному указателем назначения, задавая значение счетчика в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на назначение счетчика.
- **object_data** — указатель на структуру исходного объекта счетчика.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект счетчика успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
Получение 64-разрядного объекта счетчика 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает 64-разрядный объект счетчика по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник счетчика.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект счетчика успешно получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
Настройка 64-разрядного объекта счетчика 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>Описание

Эта служба устанавливает 64-разрядный счетчик по адресу, предоставленному указателем назначения, задавая значение счетчика в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на назначение счетчика.
- **object_data** — указатель на структуру исходного объекта счетчика.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект счетчика успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
Задание значения окончания MIB 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба создает объект, сигнализирующий об окончании MIB. Обычно ее следует вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **not_used_ptr** — указатель на значение "Не используется, нужно использовать NX_NULL".
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект end-of-mib успешно создан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
Получение объекта датчика 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает объект датчика по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник датчика.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект датчика успешно получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
Задание объекта датчика 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба устанавливает датчик по адресу, предоставленному указателем назначения, задавая значение датчика в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на назначение датчика.
- **object_data** — указатель на структуру исходного объекта датчика.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект датчика успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
Получение идентификатора объекта 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает идентификатор объекта (в нотации SIM ASCII) по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник идентификатора объекта.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — идентификатор объекта успешно получен.
- **NX_SNMP_ERROR** (0x100) — недопустимая длина объекта
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
Задание идентификатора объекта 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба устанавливает идентификатор объекта (в нотации SIM ASCII) по адресу, предоставленному указателем назначения, задавая в структуре данных объекта NetX идентификатор объекта. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на назначение идентификатора объекта.
- **object_data** — указатель на структуру объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — идентификатор объекта успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
Получение объекта целого числа 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает объект целого числа по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник целого числа.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект целого числа успешно получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
Задание объекта целого числа 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба устанавливает целое число по адресу, предоставленному указателем назначения, задавая значение целого числа в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на назначение целого числа.
- **object_data** — указатель на структуру исходного объекта целого числа.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект целого числа успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
Получение объекта IP-адреса (только IPv4)

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает объект IP-адреса по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник адреса IPv4.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект IP-адреса успешно получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
Получение объекта IP-адреса (только IPv6)

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>Описание

Эта служба получает объект адреса IPv6 по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX.
Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник адреса IPv6.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект IP-адреса успешно получен.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый код входного объекта SNMP.
- **NX_NOT_ENABLED** (0x14) — адрес IPv6 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
Задание объекта адреса IPv4 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба устанавливает адрес IPv4 по адресу, предоставленному указателем назначения, задавая IP-адрес в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на IP-адрес, который необходимо задать.
- **object_data** — указатель на структуру объектов IP-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект IP-адреса успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
Задание объекта адреса IPv6 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>Описание

Эта служба устанавливает адрес IPv6 по адресу, предоставленному указателем назначения, задавая IP-адрес в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на IP-адрес, который необходимо задать.
- **object_data** — указатель на структуру объектов IP-адреса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — адрес IPv6 успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_NOT_ENABLED** (0x14) — адрес IPv6 не включен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
Задание объекта без экземпляра 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба создает объект, который будет сигнализировать об отсутствии экземпляра указанного объекта. Обычно ее нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **not_used_ptr** — указатель на значение "Не используется, нужно использовать NX_NULL".
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект без экземпляра успешно создан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
Задание объекта со значением "не найдено" 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба создает объект, сигнализирующий о том, что объект не удалось найти. Обычно ее следует вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **not_used_ptr** — указатель на значение "Не используется, нужно использовать NX_NULL".
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект со значением "не найдено" успешно создан.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
Получение объекта октетной строки 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>Описание

Эта служба получает октетную строку по адресу, предоставленному указателем источника, и помещает ее в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник октетной строки.
- **object_data** — указатель на структуру целевого объекта.
- **Длина** — число байтов в октетной строке.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — октетная строка успешно получена.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
Задание объекта октетной строки 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба задает октетную строку по адресу, предоставленному указателем назначения, задавая октетную строку в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на цель для октетной строки.
- **object_data** — указатель на структуру исходного объекта октетной строки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — октетная строка успешно задана.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
Получение объекта строки ASCII 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает строку ASCII по адресу, предоставленному указателем источника, и помещает ее в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник строки ASCII.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — строка ASCII успешно получена.
- **NX_SNMP_ERROR** (0x100) — строка слишком велика.  
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
Задание объекта строки ASCII 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба задает строку ASCII по адресу, предоставленному указателем назначения, задавая строку ASCII в структуре данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на цель для строки ASCII.
- **object_data** — указатель на структуру исходного объекта строки ASCII.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — строка ASCII успешно задана.
- **NX_SNMP_ERROR** (0x100) — размер строки слишком велик.
- **NX_SNMP_ERROR_BADVALUE** (0x03) — строка содержит недопустимый символ.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
Получение объекта timetics 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба получает объект timetics по адресу, предоставленному указателем источника, и помещает его в структуру данных объекта NetX. Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова GET или GETNEXT приложения.

### <a name="input-parameters"></a>Входные параметры

- **source_ptr** — указатель на источник объекта timetics.
- **object_data** — указатель на структуру целевого объекта.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект timetics успешно получен.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
Задание объекта timetics 

### <a name="prototype"></a>Прототип

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>Описание

Эта служба задает переменную timetics по адресу, предоставленному указателем назначения, задавая timetics в структуре данных объекта NetX.
Такую подпрограмму обычно нужно вызывать из подпрограммы обратного вызова SET приложения.

### <a name="input-parameters"></a>Входные параметры

- **destination_ptr** — указатель на назначение для timetics.
- **object_data** — указатель на структуру исходного объекта timetics.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — объект timetics успешно задан.
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) — недопустимый тип объекта.
- **NX_PTR_ERROR** (0x07) — недопустимый указатель ввода.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Пример

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```