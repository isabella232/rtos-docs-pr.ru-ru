---
title: Глава 3. Описание служб DNS-клиента для NetX в ОСРВ Azure
description: В этой главе приводится описание всех служб DNS для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 18e059e79f9742eaaafffbf15b55b4b5063363f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815220"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a>Глава 3. Описание служб DNS-клиента для NetX в ОСРВ Azure

В этой главе приводится описание всех служб DNS для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nx_dns_authority_zone_start_get**: *поиск начала зоны полномочий, связанной с указанным именем узла*
- **nx_dns_cache_initialize**: *инициализация кэша DNS*
- **nx_dns_cache_notify_clear**: *очистка функции уведомления о заполнении кэша*
- **nx_dns_cache_notify_set**: *задание функции уведомления о заполнении кэша*
- **nx_dns_cname_get**: *поиск канонического доменного имени для псевдонима имени входного домена*
- **nx_dns_create**: *создание экземпляра DNS-клиента*
- **nx_dns_delete**: *удаление экземпляра DNS-клиента*
- **nx_dns_domain_name_server_get**: *поиск полномочных серверов доменных имен для зоны входного домена*
- **nx_dns_domain_mail_exchange_get**: *поиск записей обмена электронной почтой, связанных с указанным именем узла*
- **nx_dns_domain_service_get**: *поиск служб, связанных с указанным именем узла*
- **nx_dns_get_serverlist_size**: *возврат размера списка серверов DNS-клиента*
- **nx_dns_info_by_name_get**: *возврат IP-адреса, запрос порта по имени входного узла*
- **nx_dns_ipv4_address_by_name_get**: *поиск IPv4-адреса по указанному имени узла*
- **nx_dns_host_by_address_get**: *поиск имени узла по указанному IP-адресу*
- **nx_dns_host_by_name_get**: *поиск IPv4-адреса по указанному имени узла*
- **nx_dns_host_text_get**: *поиск текстовых данных для имени входного домена*
- **nx_dns_packet_pool_set**: *задание пула пакетов DNS-клиента*
- **nx_dns_server_add**: *добавление DNS-сервера по указанному адресу в список клиента*
- **nx_dns_server_get**: *возврат DNS-сервера в списке клиента*
- **nx_dns_server_remove**: *удаление DNS-сервера из списка клиента*
- **nx_dns_server_remove_all**: *удаление всех DNS-серверов из списка клиента*

## <a name="nx_dns_authority_zone_start_get"></a>nx_dns_authority_zone_start_get

Поиск начала зоны полномочий для входного узла

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SOA с указанным доменным именем, чтобы получить начало зоны полномочий для имени входного домена. DNS-клиент копирует записи SOA, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*. 
>[!NOTE]
> Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX тип записи SOA (NX_DNS_SOA_ENTRY) сохраняется в виде семи 4-байтовых параметров, в сумме составляющих 28 байт.

- **nx_dns_soa_host_mname_ptr**: указатель на основной источник данных для этой зоны
- **nx_dns_soa_host_rname_ptr**: указатель на почтовый ящик, ответственный за эту зону
- **nx_dns_soa_serial**: номер версии зоны
- **nx_dns_soa_refresh**: интервал обновления
- **nx_dns_soa_retry**: интервал между повторными попытками запроса SOA
- **nx_dns_soa_expire**: время истечения срока действия SOA
- **nx_dns_soa_minmum**: поле минимального срока жизни в сообщениях ответа DNS для имени узла SOA

Хранение двух записей SOA показано ниже. Записи SOA, содержащие данные фиксированной длины, размещаются, начиная с верхней части буфера. Указатели MNAME и RNAME указывают на данные переменной длины (имена узлов), которые сохраняются в нижней части буфера. Дополнительные записи SOA размещаются после первой записи ("дополнительные записи SOA..."), и их данные переменной длины сохраняются над данными переменной длины последней записи ("дополнительные данные переменной длины SOA").

![Схема хранения двух записей SOA](media/image2.png)

Если во входном *record_buffer* невозможно сохранить все данные SOA в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.

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

### <a name="example"></a>Например, .
```c
UCHAR                  record_buffer[50];
UINT                   record_count;   
NX_DNS_SOA_ENTRY       *nx_dns_soa_entry_ptr;

/* Request the start of authority zone(s) for the specified host.  */
status =  nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com",
                                          record _buffer, sizeof(record_buffer), 
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else 
{
/* If status is NX_SUCCESS a DNS query was successfully completed and SOA data is returned in soa_buffer.  */

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

```

```Output
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

```c
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
- NX_DNS_ERROR (0xA0) — кэш не выровнен по 4 байт.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a>nx_dns_cache_notify_clear

Очистка функции уведомления о заполнении кэша DNS

### <a name="prototype"></a>Прототип

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a>Описание

Эта служба очищает функцию уведомления о заполнении кэша.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель DNS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a>nx_dns_cache_notify_set

Задание функции уведомления о заполнении кэша DNS

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a>Описание

Эта служба задает функцию уведомления о заполнении кэша.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **cache_full_notify_cb**: функция обратного вызова, вызываемая при заполнении кэша

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель DNS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a>nx_dns_cname_get

Поиск канонического имени для входного имени узла

### <a name="prototype"></a>Прототип
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен в файле *nx_dns.h*, эта служба отправляет запрос типа CNAME с указанным доменным именем для получения канонического доменного имени. DNS-клиент копирует строку CNAME, возвращенную в ответе DNS-сервера, в адрес памяти *record_buffer*.

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

### <a name="example"></a>Например, .

```c
CHAR            record _buffer[50];

/* Request the canonical name for the specified host.  */
status =  nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com ", 
                            record_buffer, sizeof(record_buffer), 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the canonical host name is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test CNAME: %s\n", record_buffer);
} 
```

```Output
Test CNAME: **my_example**.com
```

## <a name="nx_dns_create"></a>nx_dns_create

Создание экземпляра DNS-клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр DNS-клиента для ранее созданного экземпляра IP.

>[!NOTE]
>Приложение должно гарантировать, что размер полезных данных пакета для пула пакетов, используемого DNS-клиентом, достаточен для поддержки сообщения DNS размером максимум 512 байт и заголовков UDP, IP и Ethernet. Если DNS-клиент создает собственный пул пакетов, он определяется параметрами NX_DNS_PACKET_POOL_SIZE и NX_DNS_PACKET_PAYLOAD. Если приложение DNS-клиента предоставляет ранее созданный пул пакетов, размер полезной нагрузки для DNS-клиента IPv4 должен составлять 512 байт для сообщения DNS максимального размера плюс 20 байт для заголовка IP, 8 байт для заголовка UDP и 14 байт для заголовка Ethernet.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **ip_ptr**: указатель на ранее созданный экземпляр IP  
- **domain_name**: указатель на доменное имя для экземпляра DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — экземпляр DNS-клиента успешно создан.
- **NX_DNS_ERROR** (0xA0) — ошибка при создании экземпляра DNS-клиента.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a>nx_dns_delete

Удаление экземпляра DNS-клиента

### <a name="prototype"></a>Прототип

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр DNS-клиента и освобождает его ресурсы. 
>[!NOTE]
> Если параметр **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** определен и DNS-клиенту был назначен определяемый пользователем пул пакетов, приложение может удалить пул пакетов DNS-клиента, если он больше не нужен.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS-**клиента**

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-клиент успешно удален.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS-клиента.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a>nx_dns_domain_name_server_get

Поиск полномочных серверов доменных имен для зоны входного домена

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа NS с указанным доменным именем, чтобы получить серверы доменных имен для имени входного домена. DNS-клиент копирует записи NS, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*. 

>[!NOTE]
>Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX тип данных NS (NX_DNS_NS_ENTRY) сохраняется в виде двух 4-байтовых параметров.

- **nx_dns_ns_ipv4_address**: IPv4-адрес сервера доменных имен
- **nx_dns_ns_hostname_ptr**: указатель на имя узла сервера доменных имен

Буфер, показанный ниже, содержит четыре записи NX_DNS_NS_ENTRY. Указатель на строку имени узла в каждой записи указывает на соответствующую строку имени узла в нижней половине буфера.

![Схема буфера, содержащего четыре записи NX DNS NS](media/image3.png)

Если во входном *record_buffer* невозможно сохранить все данные NS в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.

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
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```c
#define RECORD_COUNT        10

ULONG                      record_buffer[50];
UINT                       record_count;          
NX_DNS_NS_ENTRY            *nx_dns_ns_entry_ptr[RECORD_COUNT];

/* Request the name server(s) for the specified host.  */
status =  nx_dns_domain_name_server_get(&client_dns, (UCHAR *)" www.my_example.com ",  
                                        record_buffer, sizeof(record_buffer),  
                                        &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and NS data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test NS: ");
    printf("record_count = %d \n", record_count);      

    /* Get the name server.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY)); 

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
```

```Output
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
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа MX с указанным доменным именем, чтобы получить записи обмена электронной почтой для имени входного домена. DNS-клиент копирует записи MX, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.

>[!NOTE]
>Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX тип записи почтового обмена (NX_DNS_MAIL_EXCHANGE_ENTRY) сохраняется как четыре параметра общим размером 12 байт.

- **nx_dns_mx_ipv4_address**: IPv4-адрес почтового сервера, 4 байт
- **nx_dns_mx_preference**: предпочтение, 2 байт
- **nx_dns_mx_reserved0**: зарезервировано, 2 байт
- **nx_dns_mx_hostname_ptr**: указатель на имя узла почтового сервера, 4 байт

Ниже показан буфер, содержащий четыре записи MX. Каждая запись содержит данные фиксированной длины из приведенного выше списка. Указатель на имя узла почтового сервера указывает на соответствующее имя узла в нижней части буфера.

![Схема, на которой показан буфер, содержащий четыре записи MX](media/image4.png)

Если во входном *record_buffer* невозможно сохранить все данные MX в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.

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
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```c
#define           MAX_RECORD_COUNT 10

ULONG             record_buffer[50];
UINT              record_count;  
NX_DNS_MX_ENTRY  *nx_dns_mx_entry_ptr[MAX_RECORD_COUNT];        

/* Request the mail exchange data for the specified host.  */
status =  nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)" www.my_example.com ", 
                                          record_buffer, sizeof(record_buffer),   
                                          &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
       
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and MX data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test MX: ");
    printf("record_count = %d \n", record_count);      


    /* Get the mail exchange.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_mx_entry_ptr[i] = (NX_DNS_MX_ENTRY *)(record_buffer + i * sizeof(NX_DNS_MX_ENTRY));   

        printf("record %d: IP address: %d.%d.%d.%d\n", i, 
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 24,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 16 & 0xFF,                   
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address >> 8 & 0xFF,
                nx_dns_mx_entry_ptr[i] -> nx_dns_mx_ipv4_address & 0xFF);

        printf("preference = %d \n ", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_preference);

        if(nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr)
            printf("hostname = %s\n", nx_dns_mx_entry_ptr[i] -> nx_dns_mx_hostname_ptr);
        else
            printf("hostname is not set\n");
    }
}
```

```Output
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

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a>Описание

Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SRV с указанным доменным именем для поиска служб и их номеров портов, связанных с указанным доменом. DNS-клиент копирует записи SRV, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*. 

>[!NOTE]
>Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В DNS-клиенте для NetX тип записи службы (NX_DNS_SRV_ENTRY) сохраняется в виде шести параметров общим размером 16 байт. Это позволяет эффективно хранить данные SRV переменной длины в памяти.

- **nx_dns_srv_ipv4_address**: IPv4-адрес сервера, 4 байт
- **nx_dns_srv_priority**: приоритет сервера, 2 байт
- **nx_dns_srv_weight**: вес сервера, 2 байт
- **nx_dns_srv_port_number**: номер порта службы, 2 байт
- **nx_dns_srv_reserved0**: зарезервировано для выравнивания по 4 байт, 2 байт
- ***nx_dns_srv_hostname_ptr**: указатель на имя узла сервера, 4 байт

В заданном буфере хранятся четыре записи SRV. Каждая запись NX_DNS_SRV_ENTRY содержит указатель *nx_dns_srv_hostname_ptr*, указывающий на соответствующую строку имени узла в нижней части буфера записи.

![Схема четырех записей SRV, хранящихся в заданном буфере](media/image5.png)

Если во входном *record_buffer* невозможно сохранить все данные SRV в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.

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
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
#define MAX_RECORD_COUNT  10

UCHAR                  record_buffer[50];
UINT                   record_count;
NX_DNS_SRV_ENTRY       *nx_dns_srv_entry_ptr[MAX_RECORD_COUNT];

/* Request the service(s) provided by the specified host.  */
status =  nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                    record_buffer, sizeof(record_buffer), 
                                    &record_count, 500);

/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}

else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed and SRV data is returned in record_buffer.  */

    printf("------------------------------------------------------\n");
    printf("Test SRV: ");
    printf("record_count = %d \n", record_count);      

       
    /* Get the location of services.  */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY)); 

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
```

```Output
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

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a>Описание

Эта служба возвращает количество допустимых DNS-серверов в списке клиента.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **size** возвращает количество серверов в списке

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — размер списка DNS-серверов успешно возвращен.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a>nx_dns_info_by_name_get

Возврат IP-адреса и порта DNS-сервера по имени узла

### <a name="prototype"></a>Прототип

```c
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
- **host_port_ptr**: указатель на порт, возвращающий параметр ожидания wait_option для ответа DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись DNS-сервера успешно возвращена.
- **NX_DNS_NO_SERVER** (0xA1) — DNS-сервер не зарегистрирован в клиенте для отправки запроса имени узла.
- **NX_DNS_QUERY_FAILED** (0xA3) — не удалось выполнить запрос DNS. Ответ от DNS-серверов в списке клиента не получен, или нет доступных записей службы для имени входного узла.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a>nx_dns_ipv4_address_by_name_get

Поиск IPv4-адреса для имени входного узла

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос типа A с указанным именем узла, чтобы получить IP-адреса для имени входного узла. DNS-клиент копирует IPv4-адрес из записей A, возвращенных в ответе DNS-сервера, в адрес памяти *record_buffer*. 

>[!NOTE]
>Для получения данных *record_buffer* должен быть выровнен по 4 байт.

В буфере, выровненном по 4 байт, хранится несколько IPv4-адресов, как показано ниже.

![Схема нескольких IPv4-адресов, хранящихся в буфере, выровненном по 4 байт.](media/image6.png)

Если указанный буфер не может содержать все данные IP-адреса, оставшиеся записи A не сохраняются в *record_buffer*. Это позволяет приложению получить часть доступных данных IP-адреса или все данные в ответе сервера.

На основе числа записей A, возвращенных в **record_count*, приложение может проанализировать данные IPv4-адреса из *record_buffer*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на DNS-клиент  
- **host_name_ptr**: указатель на имя узла для получения указателя буфера IPv4-адреса на расположение, в которое следует извлечь данные IPv4-адреса
- **buffer_size**: размер буфера для хранения данных IPv4-адреса
- **wait_option**: параметр ожидания для получения ответа DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — данные IPv4-адреса успешно получены.
- **NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимый входной параметр.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
#define MAX_RECORD_COUNT  20

ULONG           record_buffer[50];
UINT            record_count;
ULONG           *ipv4_address_ptr[MAX_RECORD_COUNT];

/* Request the IPv4 address for the specified host.  */
status =  nx_dns_ipv4_address_by_name_get(&client_dns, 
                                          (UCHAR *)"www.my_example.com",  
                                           record_buffer,                  
                                           sizeof(record_buffer),&record_count,                
                                           500);

        /* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
        error_counter++;
}    
else     
{
    /* If status is NX_SUCCESS a DNS query was successfully completed the IPv4 address(es) is returned in record_buffer.  */
    printf("------------------------------------------------------\n");
    printf("Test A: ");
    printf("record_count = %d \n", record_count);      


    /* Get the IPv4 addresses of host.  */
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
```

```Output
------------------------------------------------------
Test A: record_count = 5 
record 0: IP address: 192.2.2.10
record 1: IP address: 192.2.2.11
record 2: IP address: 192.2.2.12
record 3: IP address: 192.2.2.13
record 4: IP address: 192.2.2.14
```

## <a name="nx_dns_host_by_address_get"></a>nx_dns_host_by_address_get

Поиск имени узла по IP-адресу

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба запрашивает разрешение имен для указанного IP-адреса с одного DNS-сервера или нескольких, ранее указанных приложением. В случае успешного выполнения возвращается имя узла, оканчивающееся символом NULL, в строке, заданной *host_name_ptr*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS
- **ip_address**: IP-адрес для разрешения в имя
- **host_name_ptr**: указатель на область назначения для имени узла
- **max_host_name_size**: размер области назначения для имени узла
- **wait_option** определяет, как долго служба будет ожидать (в тактах таймера) ответа DNS-сервера после каждого запроса DNS и повторных попыток выполнения запроса. Параметры ожидания определяются следующим образом.
    - **Значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Выбор числового значения (1–0xFFFFFFFE) указывает максимальное число тактов таймера для приостановки при ожидании разрешения DNS.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.  
- **NX_DNS_TIMEOUT** (0xA2) — истекло время ожидания при получении мьютекса DNS.
- **NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.
- **NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a>nx_dns_host_by_name_get

Поиск IP-адреса по имени узла

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба запрашивает разрешение имен для указанного имени, на которое указывает *host_name*, с одного DNS-сервера или нескольких, ранее указанных приложением. В случае успешного выполнения соответствующий IP-адрес возвращается в место назначения, на которое указывает *host_address_ptr*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS
- **host_name**: указатель на имя узла
- **host_address_ptr**: указатель на IP-адрес узла DNS
- **wait_option** определяет, как долго служба будет ожидать разрешения DNS Параметры ожидания определяются следующим образом.
    - **Значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Выбор числового значения (1–0xFFFFFFFE) указывает максимальное число тактов таймера для приостановки при ожидании разрешения DNS.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.
- **NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.
- **NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.
- NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```c
ULONG ip_address;

    /* Get the IP address for the name “www.my_example.com”.  */
    status =  nx_dns_host_by_name_get(&my_dns, “www.my_example.com”, &ip_address, 4000);

    /* Check for DNS query error.  */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }

    else     
    {

    /* If status is NX_SUCCESS the IP address for “www.my_example.com” can be found in the “ip_address” variable.  */
        
        printf("------------------------------------------------------\n");
        printf("Test A: \n");
        printf("IP address: %d.%d.%d.%d\n",
                host_ip_address >> 24,
                host_ip_address >> 16 & 0xFF,                   
                host_ip_address >> 8 & 0xFF,
                host_ip_address & 0xFF);
    }
```

```Output
Test A: 
IP address: 192.2.2.10
```

## <a name="nx_dns_host_text_get"></a>nx_dns_host_text_get

Поиск текстовой строки для имени входного домена

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет запрос типа TXT с указанными доменным именем и буфером для получения произвольных строковых данных.

DNS-клиент копирует текстовую строку в записи TXT в ответе DNS-сервера в адрес памяти *record_buffer*. 

>[!NOTE]
>Для получения данных *record_buffer* не должен быть выровнен по 4 байт.

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

### <a name="example"></a>Например, .

```c
CHAR            record_buffer[50];

/* Request the text string for the specified host.  */
status =  nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                record_buffer, 
                                sizeof(record_buffer), 500);


/* Check for DNS query error.  */
if (status != NX_SUCCESS)
{
     error_counter++;
}
else     
{
/* If status is NX_SUCCESS a DNS query was successfully completed and the text string is returned in record_buffer.  */
 
     printf("------------------------------------------------------\n");
     printf("Test TXT:\n %s\n", record_buffer);
} 
```

```Output
Test TXT: 
v=spf1 include:_www.my_example.com ip4:192.2.2.10/31 ip4:192.2.2.11/31 ~all
```

## <a name="nx_dns_packet_pool_set"></a>nx_dns_packet_pool_set

Задание пула пакетов DNS-клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Описание

Эта служба задает ранее созданный пул пакетов в качестве пула пакетов DNS-**клиента**. DNS-клиент будет использовать этот пул пакетов для отправки запросов DNS, поэтому размер полезной нагрузки пакета должен быть не меньше значения NX_DNS_PACKET_PAYLOAD_UNALIGNED, включающего в себя кадры Ethernet, заголовки IP и UDP и определенного в файле *nx_dns.h*.
 
>[!NOTE]
>При удалении DNS-клиента пул пакетов не удаляется вместе с ним. Приложение может удалить пул пакетов, когда он больше не нужен.

>[!NOTE]
>Эта служба доступна, только если параметр конфигурации NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен в файле *nx_dns.h*.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на ранее созданный экземпляр DNS-**клиента**
- **pool_ptr**: указатель на ранее созданный пул пакетов

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — успешное выполнение.
- **NX_NOT_ENABLED** (0x14) — клиент не настроен для использования этого параметра.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS-**клиента**.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .
```c
NX_DNS             my_dns;
NX_PACKET_POOL     client_pool;
NX_IP             *ip_ptr;


/* Create the DNS Client.  */
status =  nx_dns_create(&my_dns, ip_ptr, “My DNS Client”);

/* Create a packet pool for the DNS Client.  */
status =  nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                 NX_DNS_PACKET_PAYLOAD, free_mem_pointer, 
                                 NX_DNS_PACKET_POOL_SIZE);

/* Set the DNS Client packet pool.  */
status =  nx_dns_packet_pool_set(&my_dns, &client_pool);

/* If status is NX_SUCCESS the DNS Client packet pool was successfully set.  */
```

## <a name="nx_dns_server_add"></a>nx_dns_server_add

Добавление DNS-сервера с IP-адресом

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Описание

Эта служба добавляет DNS-сервер с IPv4-адресом в список серверов.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **server_address**: IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сервер успешно добавлен.
- **NX_DNS_DUPLICATE_ENTRY** или **NX_NO_MORE_ENTRIES** (0x17) — добавление DNS-серверов запрещено (список полон).
- **NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_DNS_BAD_ADDRESS_ERROR (0xA4) — введен адрес сервера со значением NULL.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a>nx_dns_server_get

Возврат DNS-сервера с IPv4-адресом из списка клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a>Описание

Эта служба возвращает DNS-сервер с IPv4-адресом из списка серверов по указанному индексу. Обратите внимание, что индекс отсчитывается от нуля. Если значение входного индекса превышает размер списка DNS-клиента, возвращается ошибка. Сначала можно вызвать службу *nx_dns_get_serverlist_size*, чтобы получить количество DNS-серверов в списке клиента.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS  
- **index**: индекс в списке серверов DNS-клиента
- **dns_server_address**: указатель на IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — сервер успешно возвращен.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) — индекс указывает на пустой слот.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — индекс указывает на пустой адрес.
- **NX_DNS_PARAM_ERROR** (0xA8) — значение индекса превышает размер списка.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a>nx_dns_server_remove

Удаление DNS-сервера с IPv4-адресом из списка клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a>Описание

Эта служба удаляет DNS-сервер с IPv4-адресом из списка клиента.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS
- **server_address**: IP-адрес DNS-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-сервер успешно удален.
- **NX_DNS_SERVER_NOT_FOUND** (0xA9) — сервер отсутствует в списке клиента.
- **NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — введен адрес сервера со значением NULL.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a>nx_dns_server_remove_all

Удаление всех DNS-серверов из списка клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет все DNS-серверы из списка клиента.

### <a name="input-parameters"></a>Входные параметры

- **dns_ptr**: указатель на блок управления DNS

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — DNS-серверы успешно удалены.
- **NX_DNS_ERROR** (0xA0) — не удается получить мьютекс защиты.
- NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```