---
title: Глава 3. Описание служб DNS-клиента для NetX Duo в ОСРВ Azure
description: В этой главе приводится описание всех служб DNS для NetX Duo в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 10368edf3cdf15d32bddbd5bd943681b3ff3dd1aa1a7042d1b9bb2bf0e71699f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791912"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a>Глава 3. Описание служб DNS-клиента для NetX Duo в ОСРВ Azure

В этой главе приводится описание всех служб DNS для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения без такого выделения полностью отключаются.

- **nx_dns_authority_zone_start_get**: *поиск начала зоны полномочий, связанной с указанным именем узла*

- **nx_dns_cache_initialize**: *инициализация кэша DNS*

- **nx_dns_cache_notify_clear**: *очистка функции уведомления о заполнении кэша*

- **nx_dns_cache_notify_set**: *задание функции уведомления о заполнении кэша*

- **nx_dns_cname_get**: *поиск канонического доменного имени для входного псевдонима доменного имени*

- **nx_dns_create**: *создание экземпляра DNS-клиента*

- **nx_dns_delete**: *удаление экземпляра DNS-клиента*

- **nx_dns_domain_name_server_get**: *поиск полномочных серверов доменных имен для входной зоны домена*

- **nx_dns_domain_mail_exchange_get**: *поиск обмена почтой, связанного с указанным именем узла*

- **nx_dns_domain_service_get**: *поиск служб, связанных с указанным именем узла*

- **nx_dns_get_serverlist_size**: *возврат размера списка серверов DNS-клиента*

- **nx_dns_info_by_name_get**: *возврат IP-адреса и порта с запросом по входному имени узла*

- **nx_dns_ipv4_address_by_name_get**: *поиск IPv4-адреса по указанному имени узла*

- **nxd_dns_ipv6_address_by_name_get**: *поиск IPv6-адреса по указанному имени узла*

- **nx_dns_host_by_address_get**: *функция-оболочка для nxd_dns_host_by_address_get для поиска имени узла по указанному IP-адресу (поддерживает только IPv4-адреса)*

- **nxd_dns_host_by_address_get**: *поиск IP-адреса по входному имени узла (поддерживает IPv4- и IPv6-адреса)*

- **nx_dns_host_by_name_get**: *функция-оболочка для nxd_dns_host_by_address_get для поиска имени узла по указанному адресу (поддерживает только IPv4-адреса)*

- **nxd_dns_host_by_name_get**: *поиск IP-адреса по входному имени узла (поддерживает IPv4- и IPv6-адреса)*

- **nx_dns_host_text_get**: *поиск текстовых данных для входного доменного имени*

- **nx_dns_packet_pool_set**: *задание пула пакетов DNS-клиента*

- **nx_dns_server_add**: *функция-оболочка для* nxd_dns_server_add *для добавления DNS-сервера по указанному адресу в список клиента (поддерживает только IPv4)*

- **nxd_dns_server_add**: *добавление DNS-сервера по указанному IP-адресу в список серверов клиента (поддерживает IPv4- или IPv6-адреса)*

- **nx_dns_server_get**: *возврат DNS-сервера из списка клиента (поддерживает только IPv4-адреса)*

- **nxd_dns_server_get**: *возврат DNS-сервера из списка клиента (поддерживает IPv4- или IPv6-адреса)*

- **nx_dns_server_remove**: *функция-оболочка для nxd_dns_server_remove для удаления DNS-сервера из списка клиента*

- **nxd_dns_server_remove** *удаление DNS-сервера по указанному IP-адресу из списка клиента (поддерживает IPv4- и IPv6-адреса)*

- **nx_dns_server_remove_all**: *удаление всех DNS-серверов из списка клиента*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Поиск начала зоны полномочий для входного узла

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SOA с указанным доменным именем, чтобы получить начало зоны полномочий для имени входного домена. DNS-клиент копирует записи SOA, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.

> [!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX Duo тип записи SOA (NX_DNS_SOA_ENTRY) сохраняется в виде семи 4-байтовых параметров, в сумме составляющих 28 байт.

- **nx_dns_soa_host_mname_ptr**: указатель на основной источник данных для этой зоны
- **nx_dns_soa_host_rname_ptr**: указатель на почтовый ящик, ответственный за эту зону
- **nx_dns_soa_serial**: номер версии зоны
- **nx_dns_soa_refresh**: интервал обновления
- **nx_dns_soa_retry**: интервал между повторными попытками запроса SOA
- **nx_dns_soa_expire**: время истечения срока действия SOA
- **nx_dns_soa_minmum**: поле минимального срока жизни в сообщениях ответа DNS для имени узла SOA

Хранение двух записей SOA показано ниже. Записи SOA, содержащие данные фиксированной длины, размещаются, начиная с верхней части буфера. Указатели MNAME и RNAME указывают на данные переменной длины (имена узлов), которые сохраняются в нижней части буфера. Дополнительные записи SOA размещаются после первой записи ("дополнительные записи SOA..."), и их данные переменной длины сохраняются над данными переменной длины последней записи ("дополнительные данные переменной длины SOA").

![Хранение двух записей SOA](media/image4.png)

Если во входном *record_buffer* невозможно сохранить все данные SOA в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.

На основе числа записей SOA, возвращенных в **record_count*, приложение может проанализировать данные из *record_buffer* и извлечь строки имени узла зоны полномочий.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name**: указатель на имя узла, для которого следует получить данные SOA
- **record_buffer**: указатель на расположение, в которое следует извлечь данные SOA
- **buffer_size**: размер буфера для хранения данных SOA
- **record_count**: указатель на количество полученных записей SOA
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные SOA успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
UCHAR  record_buffer[50];
UINT   record_count;   
NX_DNS_SOA_ENTRY *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host. */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",  
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
         error_counter++;
}
else 
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SOA data 
       is returned in soa_buffer. */

    /* Set a local pointer to the SOA buffer. */
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;

    printf("------------------------------------------------------\n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );

    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
    {
        printf("host mname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    }
    else
    {
        printf("host mame is not set\n");
    }

    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
    {
        printf("host rname = %s\n", 
               nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    }
    else
    {
     
        printf("host rname is not set\n");
    }
}

[Output]
----------------------------------------------------
Test SOA: 
serial = 2012111212
refresh = 7200
retry = 1800
expire = 1209600
minmum = 300
host mname = ns1.www.my_example.com
host rname = dns-admin.www.my_example.com
```

## <a name="nx_dns_cache_initialize"></a>nx_dns_cache_initialize

Инициализация кэша DNS

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a>Описание

Эта служба создает кэш DNS и инициализирует его.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **cache_ptr**: указатель на кэш DNS
- **cache_size**: размер кэша DNS в байтах

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — кэш DNS успешно инициализирован.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_DNS_CACHE_ERROR (0xB7) — недопустимый указатель на кэш.
- NX_PTR_ERROR (0x07) — недопустимый указатель DNS. 
- NX_DNS_ERROR (0xA0) — кэш не выровнен по 4 байт.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Очистка функции уведомления о заполнении кэша DNS

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a>Описание

Эта служба очищает функцию уведомления о заполнении кэша.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель DNS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Задание функции уведомления о заполнении кэша DNS

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Описание

Эта служба задает функцию уведомления о заполнении кэша.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **cache_full_notify_cb**: функция обратного вызова, вызываемая при заполнении кэша

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель DNS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Поиск канонического имени для входного имени узла

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен в файле *nxd_dns.h*, эта служба отправляет запрос типа CNAME с указанным доменным именем для получения канонического доменного имени. DNS-клиент копирует строку CNAME, возвращенную в ответе DNS-сервера, по адресу памяти *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name**: указатель на имя узла, для которого следует получить данные CNAME
- **record_buffer**: указатель на расположение, в которое следует извлечь данные CNAME
- **buffer_size**: размер буфера для хранения данных CNAME
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные CNAME успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
CHAR            record _buffer[50];

/* Request the canonical name for the specified host. */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                   record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and 
   the canonical host name is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 

[Output]
----------------------------------------------------
Test CNAME: my_example.com
```

##  <a name="nx_dns_create"></a>nx_dns_create

Создание экземпляра DNS-клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a>Описание

Эта служба создает экземпляр DNS-клиента для ранее созданного экземпляра IP.

> [!IMPORTANT]
> Приложение должно гарантировать, что размер полезных данных пакета для пула пакетов, используемого DNS-клиентом, достаточен для поддержки сообщения DNS размером максимум 512 байт и заголовков UDP, IP и Ethernet. Если DNS-клиент создает собственный пул пакетов, он определяется параметрами NX_DNS_PACKET_PAYLOAD и NX_DNS_PACKET_POOL_SIZE.

Если приложение DNS-клиента предоставляет ранее созданный пул пакетов, размер полезных данных для DNS-клиента IPv4 должен составлять 512 байт для сообщения DNS максимального размера плюс 20 байт для заголовка IP, 8 байт для заголовка UDP и 14 байт для заголовка Ethernet. Для IPv6 единственным отличием является заголовок IP-адреса размером 40 байт, поэтому пакет должен вмещать заголовок IPv6 в 40 байт.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **ip_ptr**: указатель на ранее созданный экземпляр IP-адреса  
- **domain_name**: указатель на доменное имя для экземпляра DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр DNS-клиента успешно создан.
- **NX_DNS_ERROR** (0xA0) — ошибка при создании экземпляра DNS-клиента.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a>nx_dns_delete

Удаление экземпляра DNS-клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр DNS-клиента и освобождает его ресурсы. 

> [!NOTE]
> Если параметр NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен и DNS-клиенту был назначен определяемый пользователем пул пакетов, приложение может удалить пул пакетов DNS-клиента, если он больше не нужен.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS-клиента

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-клиент успешно удален.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS-клиента.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Поиск полномочных серверов доменных имен для зоны входного домена

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа NS с указанным доменным именем, чтобы получить серверы доменных имен для имени входного домена. DNS-клиент копирует записи NS, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.

> [!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX Duo тип данных NS (NX_DNS_NS_ENTRY) сохраняется в виде двух 4-байтовых параметров.

- **nx_dns_ns_ipv4_address**: IPv4-адрес сервера доменных имен.
- **nx_dns_ns_hostname_ptr**: указатель на имя узла сервера доменных имен.

Буфер, показанный ниже, содержит четыре записи NX_DNS_NS_ENTRY. Указатель на строку имени узла в каждой записи указывает на соответствующую строку имени узла в нижней половине буфера.

![Содержит четыре записи NX_DNS_NS_ENTRY](media/image5.png)

Если во входном *record_buffer* невозможно сохранить все данные NS в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.

На основе числа записей NS, возвращенных в **record_count*, приложение может проанализировать IP-адрес и имя узла каждой записи в *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name**: указатель на имя узла, для которого следует получить данные NS
- **record_buffer**: указатель на расположение, в которое следует извлечь данные NS
- **buffer_size**: размер буфера для хранения данных NS
- **record_count**: указатель на количество полученных записей NS
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные NS успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
#define RECORD_COUNT    10

ULONG  record_buffer[50];
UINT   record_count;          
NX_DNS_NS_ENTRY  *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host. */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and NS data
   is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)
                               (record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address  >> 24,
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,                   
                      nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                     nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
        {
            printf("hostname = %s\n", 
                    nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
                }
        else
            printf("hostname is not set\n");
    }
}

[Output]
------------------------------------------------------
Test NS: record_count = 4 
record 0: IP address: 192.2.2.10
hostname = ns2.www.my_example.com
record 1: IP address: 192.2.2.11
hostname = ns1.www.my_example.com
record 2: IP address: 192.2.2.12
hostname = ns3.www.my_example.com
record 3: IP address: 192.2.2.13
hostname = ns4.www.my_example.com
```

## <a name="nx_dns_domain_mail_exchange_get"></a>nx_dns_domain_mail_exchange_get

Поиск записей обмена электронной почтой для имени входного узла

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа MX с указанным доменным именем, чтобы получить записи обмена электронной почтой для имени входного домена. DNS-клиент копирует записи MX, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*. 

> [!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX Duo тип записи обмена почтой (NX_DNS_MAIL_EXCHANGE_ENTRY) сохраняется как четыре параметра общим размером 12 байт.

- **nx_dns_mx_ipv4_address**: IPv4 адрес обмена почтой, 4 байт
- **nx_dns_mx_preference**: предпочтение, 2 байт
- **nx_dns_mx_reserved0**: зарезервировано, 2 байт
- **nx_dns_mx_hostname_ptr**: указатель на имя узла сервера обмена почтой, 4 байт

Ниже показан буфер, содержащий четыре записи MX. Каждая запись содержит данные фиксированной длины из приведенного выше списка. Указатель на имя узла сервера обмена почтой указывает на соответствующее имя узла в нижней части буфера.

![Буфер, содержащий четыре записи MX](media/image6.png)

Если во входном *record_buffer* невозможно сохранить все данные MX в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.

На основе числа записей MX, возвращенных в **record_count*, приложение может проанализировать параметры MX, включая имя узла почтового сервера каждой записи в *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name**: указатель на имя узла, для которого следует получить данные MX
- **record_buffer**: указатель на расположение, в которое следует извлечь данные MX
- **buffer_size**: размер буфера для хранения данных MX
- **record_count**: указатель на количество полученных записей MX
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные MX успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
#define MAX_RECORD_COUNT 10

ULONG  record_buffer[50];
UINT   record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host. */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and MX
   data is returned in record_buffer. */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)
               (record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", 
            nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", 
                    nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
}


[Output]

-----------------------------------------------------
Test MX: record_count = 5 
record 0: IP address: 192.2.2.10
preference = 40 
hostname = alt3.aspmx.l.www.my_example.com
record 1: IP address: 192.2.2.11
preference = 50 
hostname = alt4.aspmx.l.www.my_example.com
record 2: IP address: 192.2.2.12
preference = 10 
hostname = aspmx.l.www.my_example.com
record 3: IP address: 192.2.2.13
preference = 20 
hostname = alt1.aspmx.l.www.my_example.com
record 4: IP address: 192.2.2.14
preference = 30 
hostname = alt2.aspmx.l.www.my_example.com
```

## <a name="nx_dns_domain_service_get"></a>nx_dns_domain_service_get

Поиск служб по имени входного узла

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SRV с указанным доменным именем для поиска служб и их номеров портов, связанных с указанным доменом. DNS-клиент копирует записи SRV, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*. 

> [!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX Duo тип записи службы (NX_DNS_SRV_ENTRY) сохраняется в виде шести параметров общим размером 16 байт. Это позволяет эффективно хранить данные SRV переменной длины в памяти.

- **nx_dns_srv_ipv4_address**: IPv4-адрес сервера, 4 байт
- **nx_dns_srv_priority**: приоритет сервера, 2 байт
- **nx_dns_srv_weight**: вес сервера, 2 байт
- **nx_dns_srv_port_number**: номер порта службы, 2 байт
- **nx_dns_srv_reserved0**: зарезервировано для выравнивания по 4 байт, 2 байт
- ***nx_dns_srv_hostname_ptr**: указатель на имя узла сервера, 4 байт

В заданном буфере хранятся четыре записи SRV. Каждая запись NX_DNS_SRV_ENTRY содержит указатель, *nx_dns_srv_hostname_ptr*, указывающий на соответствующую строку имени узла в нижней части буфера записей.

![Четыре записи SRV](media/image7.png)

Если во входном *record_buffer* невозможно сохранить все данные SRV в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.

На основе числа записей SRV, возвращенных в **record_count*, приложение может проанализировать параметры SRV, включая имя узла почтового сервера каждой записи в *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name**: указатель на имя узла, для которого следует получить данные SRV
- **record_buffer**: указатель на расположение, в которое следует извлечь данные SRV
- **buffer_size**: размер буфера для хранения данных SRV
- **record_count**: указатель на количество полученных записей SRV
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные SRV успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый параметр без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
#define MAX_RECORD_COUNT  10

UCHAR  record_buffer[50];
UINT   record_count;          
NX_DNS_SRV_ENTRY *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host. */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data
       is returned in record_buffer. */

        printf("------------------------------------------------------\n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);      

           
        /* Get the location of services. */
        for(i =0; i< record_count; i++)
        {
            nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)
                                    (record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

            printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,                   
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                    nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

           printf("port number = %d\n", 
                   nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
           printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
           printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

           if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
           {
                printf("hostname = %s\n", 
                        nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
            }
           else
                printf("hostname is not set\n");
        }
}

[Output]
----------------------------------------------------
Test SRV: record_count = 3 
record 0: IP address: 192.2.2.10
port number = 5222
priority = 20
weight = 0
hostname = alt4.xmpp.l.www.my_example.com
record 1: IP address: 192.2.2.11
port number = 5222
priority = 5
weight = 0
hostname = xmpp.l.www.my_example.com
record 2: IP address: 192.2.2.12
port number = 5222
priority = 20
weight = 0
hostname = alt1.xmpp.l.www.my_example.com
```

## <a name="nx_dns_get_serverlist_size"></a>nx_dns_get_serverlist_size

Возврат размера списка серверов DNS-клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a>Описание

Эта служба возвращает количество допустимых DNS-серверов (IPv4 и IPv6) в списке клиента.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **size** возвращает количество серверов в списке

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — размер списка DNS-серверов успешно возвращен.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Возврат IP-адреса и порта DNS-сервера по имени узла

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба возвращает IP-адрес и порт сервера (запись службы) на основе имени входного узла по запросу DNS. Если запись службы не найдена, эта подпрограмма возвращает нулевой IP-адрес в указателе на входной адрес и ненулевое состояние ошибки, информирующее о возникновении ошибки.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **host_name**: указатель на буфер имени узла
- **host_address_ptr**: указатель на возвращаемый адрес
- **host_port_ptr**: указатель на возвращаемый порт
- **wait_option**: параметр ожидания ответа DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись DNS-сервера успешно возвращена.
- **NX_DNS_NO_SERVER** (0xA1) — DNS-сервер не зарегистрирован в клиенте для отправки запроса по имени узла.
- **NX_DNS_QUERY_FAILED** (0xA3) — не удалось выполнить запрос DNS. Ответ от DNS-серверов в списке клиента не получен, или нет доступных записей службы для входного имени узла.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Поиск IPv4-адреса для имени входного узла

### <a name="prototype"></a>Прототип
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос типа A с указанным именем узла, чтобы получить IP-адреса для имени входного узла. DNS-клиент копирует IPv4-адрес из записей A, возвращенных в ответе DNS-сервера, в адрес памяти *record_buffer*.

> [!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В буфере, выровненном по 4 байт, хранится несколько IPv4-адресов, как показано ниже.

![Выровненный по 4 байт буфер с несколькими адресами](media/image8.png)

Если указанный буфер не может содержать все данные IP-адреса, оставшиеся записи A не сохраняются в *record_buffer*. Это позволяет приложению получить часть доступных данных IP-адреса или все данные в ответе сервера.

На основе числа записей A, возвращенных в **record_count*, приложение может проанализировать данные IPv4-адреса из *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name_ptr**: указатель на имя узла для получения IPv4-адреса
- **buffer**: указатель на расположение, в которое следует извлечь данные IPv4
- **buffer_size**: размер буфера для хранения данных IPv4
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные IPv4-адреса успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый параметр без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4
       address(es) is returned in record_buffer. */

          
            printf("------------------------------------------------------\n");
            printf("Test A: ");
            printf("record_count = %d \n", record_count);      


           /* Get the IPv4 addresses of host. */
           for(i =0; i< record_count; i++)
           {
                ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG)); 
                printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                    *ipv4_address_ptr[i] >> 24,
                    *ipv4_address_ptr[i] >> 16 & 0xFF,                   
                    *ipv4_address_ptr[i] >> 8 & 0xFF,
                    *ipv4_address_ptr[i] & 0xFF);
            }

}

[Output]

------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nxd_dns_ipv6_address_by_name_get"></a>nxd_dns_ipv6_address_by_name_get

Поиск IPv6-адреса для входного имени узла

### <a name="prototype"></a>Прототип
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос типа AAAA с указанным доменным именем, чтобы получить IP-адреса для входного доменного имени. DNS-клиент копирует IPv6-адреса из записей AAAA, возвращенных в ответе DNS-сервера, по адресу памяти *record_buffer*. 

> [!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

Ниже показан формат IPv6-адресов, хранящихся в буфере, выровненном по 4 байт.

![Выровненный по 4 байт буфер формата IPv6](media/image9.png)

Если во входном *record_buffer* невозможно сохранить все данные AAAA в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и возвратит это количество записей в буфере.

На основе числа записей AAAA, возвращенных в **record_count*, приложение может проанализировать IPv6-адреса из каждой записи в *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name_ptr**: указатель на имя узла для получения IPv6-адреса
- **buffer**: указатель на расположение, в которое следует извлечь данные IPv6
- **buffer_size**: размер буфера для хранения данных IPv6
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные IPv6-адреса успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый параметр без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
#define      MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
NXD_ADDRESS    *ipv6_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host. */
status =  nxd_dns_ipv6_address_by_name_get(&client_dns, 
                                           (UCHAR *)"www.my_example.com", 
                                           record__buffer,                  
                                           sizeof(record_buffer), 
                                           &record_count, 500);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
        else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed the IPv6 
    address(es) is (are) returned in record_buffer. */
      
    printf("------------------------------------------------------\n");
    printf("Test AAAA: ");
    printf("record_count = %d \n", record_count);      

    /* Get the IPv6 addresses of host. */
    for(i =0; i< record_count; i++)
    {

        ipv6_address_ptr[i] = 
            (NX_DNS_IPV6_ADDRESS *)(record_buffer + i * sizeof(NX_DNS_IPV6_ADDRESS)); 
             
        printf("record %d: IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", i, 
                ipv6_address_ptr[i] -> ipv6_address[0]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[0]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[1]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[2]  & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  >>16 & 0xFFFF,
                ipv6_address_ptr[i] -> ipv6_address[3]  & 0xFFFF);
            }
}


[Output]
------------------------------------------------------
Test AAAA: record_count = 1 
record 0: IP address: 2001:0db8:0000:f101: 0000: 0000: 0000:01003
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Поиск имени узла по IP-адресу

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба запрашивает разрешение имен для указанного IP-адреса с одного DNS-сервера или нескольких, ранее указанных приложением. В случае успешного выполнения возвращается имя узла, оканчивающееся символом NULL, в строке, заданной *host_name_ptr*. Это функция-оболочка для службы *nxd_dns_host_by_address_get*, и она не принимает IPv6-адреса.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS
- **ip_address**: IP-адрес для разрешения в имя
- **host_name_ptr**: указатель на область назначения для имени узла
- **max_host_name_size**: размер области назначения для имени узла
- **wait_option**: определяет, как долго служба будет ожидать (в тактах таймера) ответ DNS-сервера после каждого запроса DNS и повторных попыток выполнения запроса Параметры ожидания определяются следующим образом.

  Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.

  Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.  
- **NX_DNS_TIMEOUT** (0xA2) — истекло время ожидания при получении мьютекса DNS.
- **NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

**Пример**
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a>nxd_dns_host_by_address_get

Поиск имени узла по IP-адресу

### <a name="prototype"></a>Прототип
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба запрашивает разрешение имен для IPv6- или IPv4-адреса во входном аргументе *ip_address* с одного DNS-сервера или нескольких, ранее указанных приложением. В случае успешного выполнения возвращается имя узла, оканчивающееся символом NULL, в строке, заданной *host_name_ptr*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS
- **ip_address**: IP-адрес для разрешения в имя
- **host_name_ptr**: указатель на область назначения для имени узла
- **max_host_name_size**: размер области назначения для имени узла
- **wait_option**: определяет, как долго служба будет ожидать (в тактах таймера) ответ DNS-сервера после каждого запроса DNS и повторных попыток выполнения запроса Параметры ожидания определяются следующим образом.

  Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.

  Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.  
- **NX_DNS_TIMEOUT** (0xA2) — истекло время ожидания при получении мьютекса DNS.
- **NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

**Пример**
```C
UCHAR   resolved_name[200];
NXD_ADDRESS host_address;

host_address.nxd_ip_version = NX_IP_VERISON_V6;
host_address.nxd_ip_address.v6[0] = 0x20010db8;
host_address.nxd_ip_address.v6[1] = 0x0;
host_address.nxd_ip_address.v6[2] = 0xf101;
host_address.nxd_ip-address.v6[3] = 0x108;

/* Get the name associated with theinput host_address. */
status =  nxd_dns_host_by_address_get(&my_dns, &host_address,
                                      resolved_name, sizeof(resolved_name), 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}     
else     
{
     printf("------------------------------------------------------\n");
     printf("Test PTR: %s\n", record_buffer);
}

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable. */


[Output]

 ------------------------------------------------------
 Test PTR: my_example.net
```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Поиск IP-адреса по имени узла

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба запрашивает разрешение имен для указанного имени с одного DNS-сервера или нескольких, ранее указанных приложением. В случае успешного выполнения соответствующий IP-адрес возвращается в место назначения, на которое указывает host_address_ptr. Это функция-оболочка для службы *nxd_dns_host_by_name_get*, и в качестве входных данных она поддерживает только IPv4-адреса.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS
- **host_name**: указатель на имя узла
- **host_address_ptr**: возвращенный IP-адрес DNS-сервера
- **wait_option**: определяет, как долго служба будет ожидать разрешение DNS Параметры ожидания определяются следующим образом.

  Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.

  Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.
- **NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

**Пример**
```C
ULONG host_address;

/* Get the IP address for the name “www.my_example.com”. */
   status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &host_address, 4000);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found 
        in the “ip_address” variable. */
        
    printf("------------------------------------------------------\n");
    printf("Test A: \n");
    printf("IP address: %d.%d.%d.%d\n",
    host_address >> 24,
    host_address >> 16 & 0xFF,                   
    host_address >> 8 & 0xFF,
    host_address & 0xFF);
}

[Output]
 ------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nxd_dns_host_by_name_get"></a>nxd_dns_host_by_name_get

Поиск IP-адреса по имени узла

### <a name="prototype"></a>Прототип
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a>Описание

Эта служба запрашивает разрешение имен для указанного IP-адреса с одного DNS-сервера или нескольких, ранее указанных приложением. В случае успешного выполнения соответствующий IP-адрес возвращается в NXD_ADDRESS, на который указывает *host_address_ptr*. Если вызывающий объект явно задает для входных данных lookup_type значение NX_IP_VERSION_V6, эта служба отправит запрос для IPv6-адреса узла (запись AAAA). Если вызывающий объект явно задает для входных данных lookup_type значение NX_IP_VERSION_V4, эта служба отправит запрос для IPv4-адреса узла (запись A).

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS-клиента
- **host_name**: указатель на имя узла, IP-адрес которого нужно найти
- **host_address_ptr**: указатель на назначение для NXD_ADDRESS, содержащего IP-адрес
- **wait_option**: определяет, как долго служба будет ожидать (в тактах таймера) ответ DNS-сервера для каждой передачи и повторной передачи запроса Параметры ожидания определяются следующим образом.

  Значение времени ожидания (0x00000001–0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)  

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.

  Числовое значение (1–0xFFFFFFFE) определяет максимальное количество тактов таймера, чтобы оставаться в состоянии приостановки во время ожидания разрешения DNS.

- **lookup_type**: указывает тип поиска (A или AAAA)

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.
- **NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

**Пример**
```C
NXD_ADDRESS host_ipduo_address;

/* Create an AAAA query to obtain the IPv6 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, 
                                   &host_ipduo_address, 4000, 
                                   NX_IP_VERSION_V6);

if (status != NX_SUCCESS)
{
        error_counter++;
}
else
{
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */

    printf("------------------------------------------------------\n");
    printf("Test AAAA: \n");

    printf("IP address: %x:%x:%x:%x:%x:%x:%x:%x\n", 
           host_ipduo_address.nxd_ip_address.v6[0]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[0]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[1]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[2]  & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  >>16 & 0xFFFF,
           host_ipduo_address.nxd_ip_address.v6[3]  & 0xFFFF);
}

[Output]

------------------------------------------------------
Test AAAA: 
IP address: 2607:f8b0:4007:800:0:0:0:1008
```

Ниже приведен еще один пример использования этой службы времени, на этот раз с использованием IPv4-адреса и типов записей A.
```C
/* Create a query to obtain the IPv4 address for the host “www.my_example.com”. */
status =  nxd_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000, 
                                   NX_IP_VERSION_V4);

/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{   
/* If status is NX_SUCCESS the IP address for “www.my_example.com” can be 
   found in the “ip_address” variable. */
  
     printf("------------------------------------------------------\n");
     printf("Test A: \n");
     printf("IP address: %d.%d.%d.%d\n",
            host_ipduo_address.nxd_ip_address.v4 >> 24,
            host_ipduo_address.nxd_ip_address.v4 >> 16 & 0xFF,                   
            host_ipduo_address.nxd_ip_address.v4 >> 8 & 0xFF,
            host_ipduo_address.nxd_ip_address.v4 & 0xFF);
 }

[Output]

------------------------------------------------------
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Поиск текстовой строки для имени входного домена

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос типа TXT с указанными доменным именем и буфером для получения произвольных строковых данных.

DNS-клиент копирует текстовую строку в записи TXT в ответе DNS-сервера по адресу памяти *record_buffer*. 

> [!NOTE]
> Для получения данных выравнивание record_buffer по 4 байт не требуется.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name**: указатель на имя узла, по которому следует выполнять поиск
- **record_buffer**: указатель на расположение, в которое следует извлечь данные TXT
- **buffer_size**: размер буфера для хранения данных TXT
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — строка TXT успешно получена.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

######   
Пример
```C
CHAR            record_buffer[50];

/* Request the text string for the specified host. */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                               record_buffer, 
                               sizeof(record_buffer), 500);


/* Check for DNS query error. */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and the
       text string is returned in record_buffer. */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 


[Output]

------------------------------------------------------
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Задание пула пакетов DNS-клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Описание

Эта служба задает ранее созданный пул пакетов в качестве пула пакетов DNS-клиента. DNS-клиент будет использовать этот пул пакетов для отправки запросов DNS, поэтому размер полезных данных пакета должен быть не меньше значения NX_DNS_PACKET_PAYLOAD, включающего в себя заголовки Ethernet, IP и UDP и определенного в файле *nxd_dns.h*. 

> [!NOTE]
> *П* ри удалении DNS-клиента пул пакетов не удаляется вместе с ним. Приложение может удалить пул пакетов, когда он больше не нужен.
>
> Эта служба доступна, только если параметр конфигурации NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен в файле *nxd_dns.h*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS-клиента
- **pool_ptr**: указатель на ранее созданный пул пакетов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное выполнение.
- **NX_NOT_ENABLED** (0x14) — клиент не настроен для использования этого параметра.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS-клиента.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
NXD_DNS my_dns;
NX_PACKET_POOL client_pool;
NX_IP *ip_ptr;


/* Create the DNS Client. */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client. */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool. */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set. */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Добавление DNS-сервера с IP-адресом

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Описание

Эта служба добавляет DNS-сервер с IPv4-адресом в список серверов.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **server_address**: IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сервер успешно добавлен.
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) — добавление DNS-серверов запрещено (список полон).
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) — введен адрес сервера со значением NULL.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a>nxd_dns_server_add

Добавление DNS-сервера в список клиента

### <a name="prototype"></a>Прототип
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Описание

Эта служба добавляет IP-адрес DNS-сервера в список серверов DNS-клиента. Значение server_address может быть IPv4- или IPv6-адресом. Если клиент хочет получать доступ к одному серверу по его IPv4- или IPv6-адресу, он должен добавить оба IP-адреса в качестве записей в список серверов.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **server_address**: указатель на NXD_ADDRESS, содержащий IP-адрес сервера для DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сервер успешно добавлен.
- **NX_DNS_DUPLICATE_ENTRY**  
**NX_NO_MORE_ENTRIES** (0x17) — добавление DNS-серверов запрещено (список полон). 
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) — введен адрес сервера со значением NULL.
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Add a DNS Server with the IP address pointed to by the server_address input. */
status =  nxd_dns_server_add(&my_dns, &server_address);

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Возврат DNS-сервера с IPv4-адресом из списка клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a>Описание

Эта служба возвращает DNS-сервер с IPv4-адресом из списка серверов по указанному индексу. 

> [!NOTE]
> Индексация начинается с нуля. Если входной индекс превышает размер списка DNS-клиента, в этом индексе находится IPv6-адрес или по указанному индексу обнаружен пустой адрес, возвращается ошибка. Сначала можно вызвать службу *nx_dns_get_serverlist_size*, чтобы получить количество DNS-серверов в списке клиента.

Эта служба поддерживает только IPv4-адреса. Она вызывает службу *nxd_dns_server_get*, которая поддерживает IPv4- и IPv6-адреса.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **index**: индекс в списке серверов DNS-клиента
- **dns_server_address**: указатель на IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сервер успешно возвращен.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) — индекс указывает на пустой слот.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — индекс указывает на пустой адрес.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a>nxd_dns_server_get

Возврат DNS-сервера из списка клиента

### <a name="prototype"></a>Прототип
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a>Описание

Эта служба возвращает DNS-сервер с IP-адресом из списка серверов по указанному индексу. 

> [!NOTE]
> Индексация начинается с нуля. Если входной индекс превышает размер списка DNS-клиента или по указанному индексу обнаружен пустой адрес, возвращается ошибка. Сначала можно вызвать службу *nx_dns_get_serverlist_size*, чтобы получить количество DNS-серверов в списке серверов.

Эта служба поддерживает IPv4- и IPv6-адреса.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **index**: индекс в списке серверов DNS-клиента
- **dns_server_address**: указатель на IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — IP-адрес сервера успешно возвращен.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) — индекс указывает на пустой слот.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — индекс указывает на пустой адрес сервера.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Удаление DNS-сервера с IPv4-адресом из списка клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a>Описание

Эта служба удаляет DNS-сервер с IPv4-адресом из списка клиента. Это функция-оболочка для *nxd_dns_server_remove*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **server_address**: IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-сервер успешно удален.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) — сервер отсутствует в списке клиента.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — введен адрес сервера со значением NULL.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a>nxd_dns_server_remove

Удаление DNS-сервера из списка клиента

### <a name="prototype"></a>Прототип
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a>Описание

Эта служба удаляет DNS-сервер с указанным IP-адресом из списка клиента. Входной IP-адрес принимает IPv4- и IPv6-адреса. После удаления сервера оставшиеся серверы перемещаются в списке на одну позицию индекса вниз для заполнения освобожденного слота.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **server_address**: указатель на данные NXD_ADDRESS DNS-сервера, содержащие IP-адрес сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-сервер успешно удален.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) — сервер отсутствует в списке клиента.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — введен адрес сервера со значением NULL.
- **NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) — не удается обработать запись с отключенным IPv6.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_INVALID_ADDRESS_TYPE (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
NXD_ADDRESS server_address;

server_address.nxd_ip_version = NX_IP_VERISON_V6;
server_address.nxd_ip_address.v6[0] = 0x20010db8;
server_address.nxd_ip_address.v6[1] = 0x0;
server_address.nxd_ip_address.v6[2] = 0xf101;
server_address.nxd_ip-address.v6[3] = 0x108;


/* Remove the DNS Server at the specified IP address from the Client list. */
status =  nxd_dns_server_remove(&my_dns,&server_ADDRESS);

/* If status is NX_SUCCESS a DNS Server was successfully removed. */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Удаление всех DNS-серверов из списка клиента

### <a name="prototype"></a>Прототип
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a>Описание

Эта служба удаляет все DNS-серверы из списка клиента.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-серверы успешно удалены.
- **NX_DNS_ERROR** (0xA0) — не удается получить мьютекс защиты.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP-адреса или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```