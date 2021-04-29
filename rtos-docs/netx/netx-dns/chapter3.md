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
# <a name="chapter-3---description-of-azure-rtos-netx-dns-client-services"></a><span data-ttu-id="ca252-103">Глава 3. Описание служб DNS-клиента для NetX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="ca252-103">Chapter 3 - Description of Azure RTOS NetX DNS Client Services</span></span>

<span data-ttu-id="ca252-104">В этой главе приводится описание всех служб DNS для NetX в ОСРВ Azure, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ca252-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ca252-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ca252-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ca252-106">**nx_dns_authority_zone_start_get**: *поиск начала зоны полномочий, связанной с указанным именем узла*</span><span class="sxs-lookup"><span data-stu-id="ca252-106">**nx_dns_authority_zone_start_get**: *Look up the start of a zone of authority associated with the specified host name*</span></span>
- <span data-ttu-id="ca252-107">**nx_dns_cache_initialize**: *инициализация кэша DNS*</span><span class="sxs-lookup"><span data-stu-id="ca252-107">**nx_dns_cache_initialize**: *Initialize a DNS Cache.*</span></span>
- <span data-ttu-id="ca252-108">**nx_dns_cache_notify_clear**: *очистка функции уведомления о заполнении кэша*</span><span class="sxs-lookup"><span data-stu-id="ca252-108">**nx_dns_cache_notify_clear**: *Clear the cache full notify function.*</span></span>
- <span data-ttu-id="ca252-109">**nx_dns_cache_notify_set**: *задание функции уведомления о заполнении кэша*</span><span class="sxs-lookup"><span data-stu-id="ca252-109">**nx_dns_cache_notify_set**: *Set the cache full notify function.*</span></span>
- <span data-ttu-id="ca252-110">**nx_dns_cname_get**: *поиск канонического доменного имени для псевдонима имени входного домена*</span><span class="sxs-lookup"><span data-stu-id="ca252-110">**nx_dns_cname_get**: *Look up the canonical domain name for the input domain name alias*</span></span>
- <span data-ttu-id="ca252-111">**nx_dns_create**: *создание экземпляра DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-111">**nx_dns_create**: *Create a DNS Client instance*</span></span>
- <span data-ttu-id="ca252-112">**nx_dns_delete**: *удаление экземпляра DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-112">**nx_dns_delete**: *Delete a DNS Client instance*</span></span>
- <span data-ttu-id="ca252-113">**nx_dns_domain_name_server_get**: *поиск полномочных серверов доменных имен для зоны входного домена*</span><span class="sxs-lookup"><span data-stu-id="ca252-113">**nx_dns_domain_name_server_get**: *Look up the authoritative name servers for the input domain zone*</span></span>
- <span data-ttu-id="ca252-114">**nx_dns_domain_mail_exchange_get**: *поиск записей обмена электронной почтой, связанных с указанным именем узла*</span><span class="sxs-lookup"><span data-stu-id="ca252-114">**nx_dns_domain_mail_exchange_get**: *Look up the mail exchange associated the specified host name.*</span></span>
- <span data-ttu-id="ca252-115">**nx_dns_domain_service_get**: *поиск служб, связанных с указанным именем узла*</span><span class="sxs-lookup"><span data-stu-id="ca252-115">**nx_dns_domain_service_get**: *Look up the service(s) associated with the specified host name*</span></span>
- <span data-ttu-id="ca252-116">**nx_dns_get_serverlist_size**: *возврат размера списка серверов DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-116">**nx_dns_get_serverlist_size**: *Return the size of the DNS Client server list*</span></span>
- <span data-ttu-id="ca252-117">**nx_dns_info_by_name_get**: *возврат IP-адреса, запрос порта по имени входного узла*</span><span class="sxs-lookup"><span data-stu-id="ca252-117">**nx_dns_info_by_name_get**: *Return IP address, port querying on input host name*</span></span>
- <span data-ttu-id="ca252-118">**nx_dns_ipv4_address_by_name_get**: *поиск IPv4-адреса по указанному имени узла*</span><span class="sxs-lookup"><span data-stu-id="ca252-118">**nx_dns_ipv4_address_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="ca252-119">**nx_dns_host_by_address_get**: *поиск имени узла по указанному IP-адресу*</span><span class="sxs-lookup"><span data-stu-id="ca252-119">**nx_dns_host_by_address_get**: *Look up a host name from a specified IP address*</span></span>
- <span data-ttu-id="ca252-120">**nx_dns_host_by_name_get**: *поиск IPv4-адреса по указанному имени узла*</span><span class="sxs-lookup"><span data-stu-id="ca252-120">**nx_dns_host_by_name_get**: *Look up the IPv4 address from the specified host name*</span></span>
- <span data-ttu-id="ca252-121">**nx_dns_host_text_get**: *поиск текстовых данных для имени входного домена*</span><span class="sxs-lookup"><span data-stu-id="ca252-121">**nx_dns_host_text_get**: *Look up the text data for the input domain name*</span></span>
- <span data-ttu-id="ca252-122">**nx_dns_packet_pool_set**: *задание пула пакетов DNS-клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-122">**nx_dns_packet_pool_set**: *Set the DNS Client packet pool*</span></span>
- <span data-ttu-id="ca252-123">**nx_dns_server_add**: *добавление DNS-сервера по указанному адресу в список клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-123">**nx_dns_server_add**: *Add a DNS Server at the specified address to the Client list*</span></span>
- <span data-ttu-id="ca252-124">**nx_dns_server_get**: *возврат DNS-сервера в списке клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-124">**nx_dns_server_get**: *Return the DNS Server in the Client list*</span></span>
- <span data-ttu-id="ca252-125">**nx_dns_server_remove**: *удаление DNS-сервера из списка клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-125">**nx_dns_server_remove**: *Remove a DNS Server from the Client list*</span></span>
- <span data-ttu-id="ca252-126">**nx_dns_server_remove_all**: *удаление всех DNS-серверов из списка клиента*</span><span class="sxs-lookup"><span data-stu-id="ca252-126">**nx_dns_server_remove_all**: *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="ca252-127">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="ca252-127">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="ca252-128">Поиск начала зоны полномочий для входного узла</span><span class="sxs-lookup"><span data-stu-id="ca252-128">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-129">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-129">Prototype</span></span>

```c
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="ca252-130">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-130">Description</span></span>

<span data-ttu-id="ca252-131">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SOA с указанным доменным именем, чтобы получить начало зоны полномочий для имени входного домена.</span><span class="sxs-lookup"><span data-stu-id="ca252-131">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="ca252-132">DNS-клиент копирует записи SOA, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-132">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 
>[!NOTE]
> <span data-ttu-id="ca252-133">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-133">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ca252-134">В DNS-клиенте для NetX тип записи SOA (NX_DNS_SOA_ENTRY) сохраняется в виде семи 4-байтовых параметров, в сумме составляющих 28 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-134">In NetX DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="ca252-135">**nx_dns_soa_host_mname_ptr**: указатель на основной источник данных для этой зоны</span><span class="sxs-lookup"><span data-stu-id="ca252-135">**nx_dns_soa_host_mname_ptr**: Pointer to primary source of data for this zone</span></span>
- <span data-ttu-id="ca252-136">**nx_dns_soa_host_rname_ptr**: указатель на почтовый ящик, ответственный за эту зону</span><span class="sxs-lookup"><span data-stu-id="ca252-136">**nx_dns_soa_host_rname_ptr**: Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="ca252-137">**nx_dns_soa_serial**: номер версии зоны</span><span class="sxs-lookup"><span data-stu-id="ca252-137">**nx_dns_soa_serial**: Zone version number</span></span>
- <span data-ttu-id="ca252-138">**nx_dns_soa_refresh**: интервал обновления</span><span class="sxs-lookup"><span data-stu-id="ca252-138">**nx_dns_soa_refresh**: Refresh interval</span></span>
- <span data-ttu-id="ca252-139">**nx_dns_soa_retry**: интервал между повторными попытками запроса SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-139">**nx_dns_soa_retry**: Interval between SOA query retries</span></span>
- <span data-ttu-id="ca252-140">**nx_dns_soa_expire**: время истечения срока действия SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-140">**nx_dns_soa_expire**: Time duration when SOA expires</span></span>
- <span data-ttu-id="ca252-141">**nx_dns_soa_minmum**: поле минимального срока жизни в сообщениях ответа DNS для имени узла SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-141">**nx_dns_soa_minmum**: Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="ca252-142">Хранение двух записей SOA показано ниже.</span><span class="sxs-lookup"><span data-stu-id="ca252-142">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="ca252-143">Записи SOA, содержащие данные фиксированной длины, размещаются, начиная с верхней части буфера.</span><span class="sxs-lookup"><span data-stu-id="ca252-143">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="ca252-144">Указатели MNAME и RNAME указывают на данные переменной длины (имена узлов), которые сохраняются в нижней части буфера.</span><span class="sxs-lookup"><span data-stu-id="ca252-144">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="ca252-145">Дополнительные записи SOA размещаются после первой записи ("дополнительные записи SOA..."), и их данные переменной длины сохраняются над данными переменной длины последней записи ("дополнительные данные переменной длины SOA").</span><span class="sxs-lookup"><span data-stu-id="ca252-145">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![Схема хранения двух записей SOA](media/image2.png)

<span data-ttu-id="ca252-147">Если во входном *record_buffer* невозможно сохранить все данные SOA в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="ca252-147">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ca252-148">На основе числа записей SOA, возвращенных в \**record_count*, приложение может проанализировать данные из *record_buffer* и извлечь строки имени узла зоны полномочий.</span><span class="sxs-lookup"><span data-stu-id="ca252-148">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-149">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-149">Input Parameters</span></span>

- <span data-ttu-id="ca252-150">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-150">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-151">**host_name**: указатель на имя узла, для которого следует получить данные SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-151">**host_name**: Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="ca252-152">**record_buffer**: указатель на расположение, в которое следует извлечь данные SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-152">**record_buffer**: Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="ca252-153">**buffer_size**: размер буфера для хранения данных SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-153">**buffer_size**: Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="ca252-154">**record_count**: указатель на количество полученных записей SOA</span><span class="sxs-lookup"><span data-stu-id="ca252-154">**record_count**: Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="ca252-155">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-155">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-156">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-156">Return Values</span></span>

- <span data-ttu-id="ca252-157">**NX_SUCCESS** (0x00) — данные SOA успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ca252-157">**NX_SUCCESS**: (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="ca252-158">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-158">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-159">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-159">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-160">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-160">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-161">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-161">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ca252-162">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-162">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-163">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-163">Allowed From</span></span>

<span data-ttu-id="ca252-164">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-164">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-165">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-165">Example</span></span>
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


## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="ca252-166">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="ca252-166">nx_dns_cache_initialize</span></span>

<span data-ttu-id="ca252-167">Инициализация кэша DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-167">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-168">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-168">Prototype</span></span>

```c
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                             VOID *cache_ptr, UINT cache_size);

```
### <a name="description"></a><span data-ttu-id="ca252-169">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-169">Description</span></span>

<span data-ttu-id="ca252-170">Эта служба создает кэш DNS и инициализирует его.</span><span class="sxs-lookup"><span data-stu-id="ca252-170">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-171">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-171">Input Parameters</span></span>

- <span data-ttu-id="ca252-172">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-172">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="ca252-173">**cache_ptr**: указатель на кэш DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-173">**cache_ptr**: Pointer to DNS Cache.</span></span>
- <span data-ttu-id="ca252-174">**cache_size**: размер кэша DNS в байтах</span><span class="sxs-lookup"><span data-stu-id="ca252-174">**cache_size**: Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-175">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-175">Return Values</span></span>

- <span data-ttu-id="ca252-176">**NX_SUCCESS** (0x00) — кэш DNS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="ca252-176">**NX_SUCCESS**: (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="ca252-177">NX_DNS_ERROR (0xA0) — кэш не выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-177">NX_DNS_ERROR: (0xA0) Cache is not 4-byte aligned.</span></span>
- <span data-ttu-id="ca252-178">NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-178">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ca252-179">NX_PTR_ERROR (0x07) — недопустимый указатель DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-179">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>
- <span data-ttu-id="ca252-180">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-180">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-181">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-181">Allowed From</span></span>

<span data-ttu-id="ca252-182">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-182">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-183">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-183">Example</span></span>
```c
UCHAR          dns_cache [2048]; 

/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, dns_cache, 2048);
/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="ca252-184">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="ca252-184">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="ca252-185">Очистка функции уведомления о заполнении кэша DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-185">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-186">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-186">Prototype</span></span>

```c
UINT     nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="ca252-187">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-187">Description</span></span>

<span data-ttu-id="ca252-188">Эта служба очищает функцию уведомления о заполнении кэша.</span><span class="sxs-lookup"><span data-stu-id="ca252-188">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-189">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-189">Input Parameters</span></span>

- <span data-ttu-id="ca252-190">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-190">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-191">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-191">Return Values</span></span>

- <span data-ttu-id="ca252-192">**NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.</span><span class="sxs-lookup"><span data-stu-id="ca252-192">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="ca252-193">NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-193">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ca252-194">NX_PTR_ERROR (0x07) — недопустимый указатель DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-194">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-195">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-195">Allowed From</span></span>

<span data-ttu-id="ca252-196">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-197">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-197">Example</span></span>

```c
/* Clear the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="ca252-198">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="ca252-198">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="ca252-199">Задание функции уведомления о заполнении кэша DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-199">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-200">Prototype</span></span>

```c
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr, VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="ca252-201">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-201">Description</span></span>

<span data-ttu-id="ca252-202">Эта служба задает функцию уведомления о заполнении кэша.</span><span class="sxs-lookup"><span data-stu-id="ca252-202">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-203">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-203">Input Parameters</span></span>

- <span data-ttu-id="ca252-204">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-204">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="ca252-205">**cache_full_notify_cb**: функция обратного вызова, вызываемая при заполнении кэша</span><span class="sxs-lookup"><span data-stu-id="ca252-205">**cache_full_notify_cb**: The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-206">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-206">Return Values</span></span>

- <span data-ttu-id="ca252-207">**NX_SUCCESS** (0x00) — уведомление о заполнении кэша DNS успешно задано.</span><span class="sxs-lookup"><span data-stu-id="ca252-207">**NX_SUCCESS**: (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="ca252-208">NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-208">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ca252-209">NX_PTR_ERROR (0x07) — недопустимый указатель DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-209">NX_PTR_ERROR: (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-210">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-210">Allowed From</span></span>

<span data-ttu-id="ca252-211">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-212">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-212">Example</span></span>

```c
/* Set the DNS Cache full notify function.  */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set.  */
 
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="ca252-213">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="ca252-213">nx_dns_cname_get</span></span>

<span data-ttu-id="ca252-214">Поиск канонического имени для входного имени узла</span><span class="sxs-lookup"><span data-stu-id="ca252-214">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-215">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-215">Prototype</span></span>
```c
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                      UCHAR *record_buffer, UINT buffer_size, 
                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-216">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-216">Description</span></span>

<span data-ttu-id="ca252-217">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен в файле *nx_dns.h*, эта служба отправляет запрос типа CNAME с указанным доменным именем для получения канонического доменного имени.</span><span class="sxs-lookup"><span data-stu-id="ca252-217">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nx_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="ca252-218">DNS-клиент копирует строку CNAME, возвращенную в ответе DNS-сервера, в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-218">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-219">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-219">Input Parameters</span></span>

- <span data-ttu-id="ca252-220">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-220">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-221">**host_name**: указатель на имя узла, для которого следует получить данные CNAME</span><span class="sxs-lookup"><span data-stu-id="ca252-221">**host_name**: Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="ca252-222">**record_buffer**: указатель на расположение, в которое следует извлечь данные CNAME</span><span class="sxs-lookup"><span data-stu-id="ca252-222">**record_buffer**: Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="ca252-223">**buffer_size**: размер буфера для хранения данных CNAME</span><span class="sxs-lookup"><span data-stu-id="ca252-223">**buffer_size**: Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="ca252-224">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-224">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-225">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-225">Return Values</span></span>

- <span data-ttu-id="ca252-226">**NX_SUCCESS** (0x00) — данные CNAME успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ca252-226">**NX_SUCCESS**: (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="ca252-227">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-227">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-228">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-228">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-229">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-229">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-230">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-230">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ca252-231">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-231">NX_DNS_PARAM_ERROR: (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-232">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-232">Allowed From</span></span>

<span data-ttu-id="ca252-233">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-233">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-234">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-234">Example</span></span>

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

## <a name="nx_dns_create"></a><span data-ttu-id="ca252-235">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="ca252-235">nx_dns_create</span></span>

<span data-ttu-id="ca252-236">Создание экземпляра DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-236">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-237">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-237">Prototype</span></span>

```c
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="ca252-238">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-238">Description</span></span>

<span data-ttu-id="ca252-239">Эта служба создает экземпляр DNS-клиента для ранее созданного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="ca252-239">This service creates a DNS Client instance for the previously created IP instance.</span></span>

>[!NOTE]
><span data-ttu-id="ca252-240">Приложение должно гарантировать, что размер полезных данных пакета для пула пакетов, используемого DNS-клиентом, достаточен для поддержки сообщения DNS размером максимум 512 байт и заголовков UDP, IP и Ethernet.</span><span class="sxs-lookup"><span data-stu-id="ca252-240">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="ca252-241">Если DNS-клиент создает собственный пул пакетов, он определяется параметрами NX_DNS_PACKET_POOL_SIZE и NX_DNS_PACKET_PAYLOAD.</span><span class="sxs-lookup"><span data-stu-id="ca252-241">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_POOL_SIZE and NX_DNS_PACKET_PAYLOAD.</span></span> <span data-ttu-id="ca252-242">Если приложение DNS-клиента предоставляет ранее созданный пул пакетов, размер полезной нагрузки для DNS-клиента IPv4 должен составлять 512 байт для сообщения DNS максимального размера плюс 20 байт для заголовка IP, 8 байт для заголовка UDP и 14 байт для заголовка Ethernet.</span><span class="sxs-lookup"><span data-stu-id="ca252-242">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-243">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-243">Input Parameters</span></span>

- <span data-ttu-id="ca252-244">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-244">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-245">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="ca252-245">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="ca252-246">**domain_name**: указатель на доменное имя для экземпляра DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-246">**domain_name**: Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-247">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-247">Return Values</span></span>

- <span data-ttu-id="ca252-248">**NX_SUCCESS** (0x00) — экземпляр DNS-клиента успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ca252-248">**NX_SUCCESS**: (0x00) Successful DNS create</span></span>
- <span data-ttu-id="ca252-249">**NX_DNS_ERROR** (0xA0) — ошибка при создании экземпляра DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-249">**NX_DNS_ERROR**: (0xA0) DNS create error</span></span>
- <span data-ttu-id="ca252-250">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-250">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-251">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-251">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-252">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-252">Allowed From</span></span>

<span data-ttu-id="ca252-253">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-253">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-254">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-254">Example</span></span>

```c
/* Create a DNS Client instance.  */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created.  */
```
## <a name="nx_dns_delete"></a><span data-ttu-id="ca252-255">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="ca252-255">nx_dns_delete</span></span>

<span data-ttu-id="ca252-256">Удаление экземпляра DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-256">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-257">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-257">Prototype</span></span>

```c
UINT     nx_dns_delete(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="ca252-258">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-258">Description</span></span>

<span data-ttu-id="ca252-259">Эта служба удаляет ранее созданный экземпляр DNS-клиента и освобождает его ресурсы.</span><span class="sxs-lookup"><span data-stu-id="ca252-259">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 
>[!NOTE]
> <span data-ttu-id="ca252-260">Если параметр **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** определен и DNS-клиенту был назначен определяемый пользователем пул пакетов, приложение может удалить пул пакетов DNS-клиента, если он больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="ca252-260">If **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL** is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-261">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-261">Input Parameters</span></span>

- <span data-ttu-id="ca252-262">**dns_ptr**: указатель на ранее созданный экземпляр DNS-**клиента**</span><span class="sxs-lookup"><span data-stu-id="ca252-262">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-263">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-263">Return Values</span></span>

- <span data-ttu-id="ca252-264">**NX_SUCCESS** (0x00) — DNS-клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ca252-264">**NX_SUCCESS**: (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="ca252-265">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS-клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-265">NX_PTR_ERROR: (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="ca252-266">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-266">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-267">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-267">Allowed From</span></span>

<span data-ttu-id="ca252-268">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-269">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-269">Example</span></span>

```c
/* Delete a DNS Client instance.  */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted.  */
```
## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="ca252-270">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="ca252-270">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="ca252-271">Поиск полномочных серверов доменных имен для зоны входного домена</span><span class="sxs-lookup"><span data-stu-id="ca252-271">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-272">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-272">Prototype</span></span>

```c
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-273">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-273">Description</span></span>

<span data-ttu-id="ca252-274">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа NS с указанным доменным именем, чтобы получить серверы доменных имен для имени входного домена.</span><span class="sxs-lookup"><span data-stu-id="ca252-274">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="ca252-275">DNS-клиент копирует записи NS, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-275">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ca252-276">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-276">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ca252-277">В DNS-клиенте для NetX тип данных NS (NX_DNS_NS_ENTRY) сохраняется в виде двух 4-байтовых параметров.</span><span class="sxs-lookup"><span data-stu-id="ca252-277">In NetX DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="ca252-278">**nx_dns_ns_ipv4_address**: IPv4-адрес сервера доменных имен</span><span class="sxs-lookup"><span data-stu-id="ca252-278">**nx_dns_ns_ipv4_address**: Name server’s IPv4 address</span></span>
- <span data-ttu-id="ca252-279">**nx_dns_ns_hostname_ptr**: указатель на имя узла сервера доменных имен</span><span class="sxs-lookup"><span data-stu-id="ca252-279">**nx_dns_ns_hostname_ptr**: Pointer to the name server’s hostname</span></span>

<span data-ttu-id="ca252-280">Буфер, показанный ниже, содержит четыре записи NX_DNS_NS_ENTRY.</span><span class="sxs-lookup"><span data-stu-id="ca252-280">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="ca252-281">Указатель на строку имени узла в каждой записи указывает на соответствующую строку имени узла в нижней половине буфера.</span><span class="sxs-lookup"><span data-stu-id="ca252-281">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![Схема буфера, содержащего четыре записи NX DNS NS](media/image3.png)

<span data-ttu-id="ca252-283">Если во входном *record_buffer* невозможно сохранить все данные NS в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="ca252-283">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ca252-284">На основе числа записей NS, возвращенных в \**record_count*, приложение может проанализировать IP-адрес и имя узла каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-284">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-285">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-285">Input Parameters</span></span>

- <span data-ttu-id="ca252-286">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-286">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-287">**host_name**: указатель на имя узла, для которого следует получить данные NS</span><span class="sxs-lookup"><span data-stu-id="ca252-287">**host_name**: Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="ca252-288">**record_buffer**: указатель на расположение, в которое следует извлечь данные NS</span><span class="sxs-lookup"><span data-stu-id="ca252-288">**record_buffer**: Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="ca252-289">**buffer_size**: размер буфера для хранения данных NS</span><span class="sxs-lookup"><span data-stu-id="ca252-289">**buffer_size**: Size of buffer to hold NS data</span></span>
- <span data-ttu-id="ca252-290">**record_count**: указатель на количество полученных записей NS</span><span class="sxs-lookup"><span data-stu-id="ca252-290">**record_count**: Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="ca252-291">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-291">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-292">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-292">Return Values</span></span>

- <span data-ttu-id="ca252-293">**NX_SUCCESS** (0x00) — данные NS успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ca252-293">**NX_SUCCESS**: (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="ca252-294">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-294">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-295">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-295">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-296">NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-296">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ca252-297">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-297">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-298">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-298">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-299">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-299">Allowed From</span></span>

<span data-ttu-id="ca252-300">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-300">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-301">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-301">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="ca252-302">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="ca252-302">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="ca252-303">Поиск записей обмена электронной почтой для имени входного узла</span><span class="sxs-lookup"><span data-stu-id="ca252-303">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-304">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-304">Prototype</span></span>
```c
UINT     nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                        VOID *record_buffer,                                        
                                        UINT buffer_size, 
                                        UINT *record_count, 
                                        ULONG wait_option);

```

### <a name="description"></a><span data-ttu-id="ca252-305">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-305">Description</span></span>

<span data-ttu-id="ca252-306">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа MX с указанным доменным именем, чтобы получить записи обмена электронной почтой для имени входного домена.</span><span class="sxs-lookup"><span data-stu-id="ca252-306">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="ca252-307">DNS-клиент копирует записи MX, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-307">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

>[!NOTE]
><span data-ttu-id="ca252-308">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-308">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ca252-309">В DNS-клиенте для NetX тип записи почтового обмена (NX_DNS_MAIL_EXCHANGE_ENTRY) сохраняется как четыре параметра общим размером 12 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-309">In NetX DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="ca252-310">**nx_dns_mx_ipv4_address**: IPv4-адрес почтового сервера, 4 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-310">**nx_dns_mx_ipv4_address**: Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="ca252-311">**nx_dns_mx_preference**: предпочтение, 2 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-311">**nx_dns_mx_preference**: Preference 2 bytes</span></span>
- <span data-ttu-id="ca252-312">**nx_dns_mx_reserved0**: зарезервировано, 2 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-312">**nx_dns_mx_reserved0**: Reserved 2 bytes</span></span>
- <span data-ttu-id="ca252-313">**nx_dns_mx_hostname_ptr**: указатель на имя узла почтового сервера, 4 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-313">**nx_dns_mx_hostname_ptr**: Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="ca252-314">Ниже показан буфер, содержащий четыре записи MX.</span><span class="sxs-lookup"><span data-stu-id="ca252-314">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="ca252-315">Каждая запись содержит данные фиксированной длины из приведенного выше списка.</span><span class="sxs-lookup"><span data-stu-id="ca252-315">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="ca252-316">Указатель на имя узла почтового сервера указывает на соответствующее имя узла в нижней части буфера.</span><span class="sxs-lookup"><span data-stu-id="ca252-316">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![Схема, на которой показан буфер, содержащий четыре записи MX](media/image4.png)

<span data-ttu-id="ca252-318">Если во входном *record_buffer* невозможно сохранить все данные MX в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="ca252-318">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ca252-319">На основе числа записей MX, возвращенных в \**record_count*, приложение может проанализировать параметры MX, включая имя узла почтового сервера каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-319">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-320">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-320">Input Parameters</span></span>

- <span data-ttu-id="ca252-321">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-321">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-322">**host_name**: указатель на имя узла, для которого следует получить данные MX</span><span class="sxs-lookup"><span data-stu-id="ca252-322">**host_name**: Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="ca252-323">**record_buffer**: указатель на расположение, в которое следует извлечь данные MX</span><span class="sxs-lookup"><span data-stu-id="ca252-323">**record_buffer**: Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="ca252-324">**buffer_size**: размер буфера для хранения данных MX</span><span class="sxs-lookup"><span data-stu-id="ca252-324">**buffer_size**: Size of buffer to hold MX data</span></span>
- <span data-ttu-id="ca252-325">**record_count**: указатель на количество полученных записей MX</span><span class="sxs-lookup"><span data-stu-id="ca252-325">**record_count**: Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="ca252-326">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-326">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-327">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-327">Return Values</span></span>

- <span data-ttu-id="ca252-328">**NX_SUCCESS** (0x00) — данные MX успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ca252-328">**NX_SUCCESS**: (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="ca252-329">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-329">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-330">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-330">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-331">NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-331">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ca252-332">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-332">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-333">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-333">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-334">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-334">Allowed From</span></span>

<span data-ttu-id="ca252-335">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-335">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-336">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-336">Example</span></span>
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


## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="ca252-337">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="ca252-337">nx_dns_domain_service_get</span></span>

<span data-ttu-id="ca252-338">Поиск служб по имени входного узла</span><span class="sxs-lookup"><span data-stu-id="ca252-338">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-339">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-339">Prototype</span></span>

```c
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-340">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-340">Description</span></span>

<span data-ttu-id="ca252-341">Если параметр NX_DNS_ENABLE_EXTENDED_RR_TYPES определен, эта служба отправляет запрос типа SRV с указанным доменным именем для поиска служб и их номеров портов, связанных с указанным доменом.</span><span class="sxs-lookup"><span data-stu-id="ca252-341">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="ca252-342">DNS-клиент копирует записи SRV, возвращенные в ответе DNS-сервера, в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-342">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ca252-343">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-343">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ca252-344">В DNS-клиенте для NetX тип записи службы (NX_DNS_SRV_ENTRY) сохраняется в виде шести параметров общим размером 16 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-344">In NetX DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="ca252-345">Это позволяет эффективно хранить данные SRV переменной длины в памяти.</span><span class="sxs-lookup"><span data-stu-id="ca252-345">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="ca252-346">**nx_dns_srv_ipv4_address**: IPv4-адрес сервера, 4 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-346">**Server IPv4 address**: nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="ca252-347">**nx_dns_srv_priority**: приоритет сервера, 2 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-347">**Server priority**: nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="ca252-348">**nx_dns_srv_weight**: вес сервера, 2 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-348">**Server weight**: nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="ca252-349">**nx_dns_srv_port_number**: номер порта службы, 2 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-349">**Service port number**: nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="ca252-350">**nx_dns_srv_reserved0**: зарезервировано для выравнивания по 4 байт, 2 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-350">**Reserved for 4-byte alignment**: nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="ca252-351">\***nx_dns_srv_hostname_ptr**: указатель на имя узла сервера, 4 байт</span><span class="sxs-lookup"><span data-stu-id="ca252-351">**Pointer to server host name**: \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="ca252-352">В заданном буфере хранятся четыре записи SRV.</span><span class="sxs-lookup"><span data-stu-id="ca252-352">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="ca252-353">Каждая запись NX_DNS_SRV_ENTRY содержит указатель *nx_dns_srv_hostname_ptr*, указывающий на соответствующую строку имени узла в нижней части буфера записи.</span><span class="sxs-lookup"><span data-stu-id="ca252-353">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![Схема четырех записей SRV, хранящихся в заданном буфере](media/image5.png)

<span data-ttu-id="ca252-355">Если во входном *record_buffer* невозможно сохранить все данные SRV в ответе сервера, *record_buffer* будет содержать столько записей, сколько сможет, и вернет количество записей в буфере.</span><span class="sxs-lookup"><span data-stu-id="ca252-355">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="ca252-356">На основе числа записей SRV, возвращенных в \**record_count*, приложение может проанализировать параметры SRV, включая имя узла почтового сервера каждой записи в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-356">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-357">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-357">Input Parameters</span></span>

- <span data-ttu-id="ca252-358">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-358">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-359">**host_name**: указатель на имя узла, для которого следует получить данные SRV</span><span class="sxs-lookup"><span data-stu-id="ca252-359">**host_name**: Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="ca252-360">**record_buffer**: указатель на расположение, в которое следует извлечь данные SRV</span><span class="sxs-lookup"><span data-stu-id="ca252-360">**record_buffer**: Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="ca252-361">**buffer_size**: размер буфера для хранения данных SRV</span><span class="sxs-lookup"><span data-stu-id="ca252-361">**buffer_size**: Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="ca252-362">**record_count**: указатель на количество полученных записей SRV</span><span class="sxs-lookup"><span data-stu-id="ca252-362">**record_count**: Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="ca252-363">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-363">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-364">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-364">Return Values</span></span>

- <span data-ttu-id="ca252-365">**NX_SUCCESS** (0x00) — данные SRV успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ca252-365">**NX_SUCCESS**: (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="ca252-366">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-366">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-367">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-367">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-368">NX_DNS_PARAM_ERROR (0xA8) — недопустимый идентификатор DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-368">NX_DNS_PARAM_ERROR: (0xA8) Invalid DNS ID.</span></span>
- <span data-ttu-id="ca252-369">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-369">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-370">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-370">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-371">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-371">Allowed From</span></span>

<span data-ttu-id="ca252-372">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-372">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-373">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-373">Example</span></span>

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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="ca252-374">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="ca252-374">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="ca252-375">Возврат размера списка серверов DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-375">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-376">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-376">Prototype</span></span>

```c
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```

### <a name="description"></a><span data-ttu-id="ca252-377">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-377">Description</span></span>

<span data-ttu-id="ca252-378">Эта служба возвращает количество допустимых DNS-серверов в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-378">This service returns the number of valid DNS Servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-379">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-379">Input Parameters</span></span>

- <span data-ttu-id="ca252-380">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-380">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="ca252-381">**size** возвращает количество серверов в списке</span><span class="sxs-lookup"><span data-stu-id="ca252-381">**size**: Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-382">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-382">Return Values</span></span>

- <span data-ttu-id="ca252-383">**NX_SUCCESS** (0x00) — размер списка DNS-серверов успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="ca252-383">**NX_SUCCESS**: (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="ca252-384">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-384">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ca252-385">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-385">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-386">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-386">Allowed From</span></span>

<span data-ttu-id="ca252-387">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-388">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-388">Example</span></span>

```c
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list.  */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned.  */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="ca252-389">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="ca252-389">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="ca252-390">Возврат IP-адреса и порта DNS-сервера по имени узла</span><span class="sxs-lookup"><span data-stu-id="ca252-390">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-391">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-391">Prototype</span></span>

```c
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-392">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-392">Description</span></span>

<span data-ttu-id="ca252-393">Эта служба возвращает IP-адрес и порт сервера (запись службы) на основе имени входного узла по запросу DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-393">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="ca252-394">Если запись службы не найдена, эта подпрограмма возвращает нулевой IP-адрес в указателе на входной адрес и ненулевое состояние ошибки, информирующее о возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="ca252-394">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-395">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-395">Input Parameters</span></span>

- <span data-ttu-id="ca252-396">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-396">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="ca252-397">**host_name**: указатель на буфер имени узла</span><span class="sxs-lookup"><span data-stu-id="ca252-397">**host_name**: Pointer to host name buffer</span></span>
- <span data-ttu-id="ca252-398">**host_address_ptr**: указатель на возвращаемый адрес</span><span class="sxs-lookup"><span data-stu-id="ca252-398">**host_address_ptr**: Pointer to address to return</span></span>
- <span data-ttu-id="ca252-399">**host_port_ptr**: указатель на порт, возвращающий параметр ожидания wait_option для ответа DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-399">**host_port_ptr**: Pointer to port to return wait_option Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-400">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-400">Return Values</span></span>

- <span data-ttu-id="ca252-401">**NX_SUCCESS** (0x00) — запись DNS-сервера успешно возвращена.</span><span class="sxs-lookup"><span data-stu-id="ca252-401">**NX_SUCCESS**: (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="ca252-402">**NX_DNS_NO_SERVER** (0xA1) — DNS-сервер не зарегистрирован в клиенте для отправки запроса имени узла.</span><span class="sxs-lookup"><span data-stu-id="ca252-402">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="ca252-403">**NX_DNS_QUERY_FAILED** (0xA3) — не удалось выполнить запрос DNS. Ответ от DNS-серверов в списке клиента не получен, или нет доступных записей службы для имени входного узла.</span><span class="sxs-lookup"><span data-stu-id="ca252-403">**NX_DNS_QUERY_FAILED**: (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="ca252-404">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-404">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-405">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-405">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-406">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-406">Allowed From</span></span>

<span data-ttu-id="ca252-407">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-407">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-408">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-408">Example</span></span>
```c
ULONG         ip_address;
USHORT         port;

/* Attempt to resolve the IP address and ports for this host name.  */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned.  */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="ca252-409">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="ca252-409">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="ca252-410">Поиск IPv4-адреса для имени входного узла</span><span class="sxs-lookup"><span data-stu-id="ca252-410">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-411">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-411">Prototype</span></span>

```c
UINT nx_dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                       UCHAR *host_name_ptr, VOID *buffer, 
                                       UINT buffer_size, 
                                       UINT *record_count,
                                       ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-412">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-412">Description</span></span>

<span data-ttu-id="ca252-413">Эта служба отправляет запрос типа A с указанным именем узла, чтобы получить IP-адреса для имени входного узла.</span><span class="sxs-lookup"><span data-stu-id="ca252-413">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="ca252-414">DNS-клиент копирует IPv4-адрес из записей A, возвращенных в ответе DNS-сервера, в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-414">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ca252-415">Для получения данных *record_buffer* должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-415">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="ca252-416">В буфере, выровненном по 4 байт, хранится несколько IPv4-адресов, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="ca252-416">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![Схема нескольких IPv4-адресов, хранящихся в буфере, выровненном по 4 байт.](media/image6.png)

<span data-ttu-id="ca252-418">Если указанный буфер не может содержать все данные IP-адреса, оставшиеся записи A не сохраняются в *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-418">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="ca252-419">Это позволяет приложению получить часть доступных данных IP-адреса или все данные в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="ca252-419">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="ca252-420">На основе числа записей A, возвращенных в \**record_count*, приложение может проанализировать данные IPv4-адреса из *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-420">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-421">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-421">Input Parameters</span></span>

- <span data-ttu-id="ca252-422">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-422">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-423">**host_name_ptr**: указатель на имя узла для получения указателя буфера IPv4-адреса на расположение, в которое следует извлечь данные IPv4-адреса</span><span class="sxs-lookup"><span data-stu-id="ca252-423">**host_name_ptr**: Pointer to host name to obtain IPv4 address buffer Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="ca252-424">**buffer_size**: размер буфера для хранения данных IPv4-адреса</span><span class="sxs-lookup"><span data-stu-id="ca252-424">**buffer_size**: Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="ca252-425">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-425">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-426">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-426">Return Values</span></span>

- <span data-ttu-id="ca252-427">**NX_SUCCESS** (0x00) — данные IPv4-адреса успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ca252-427">**NX_SUCCESS**: (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="ca252-428">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-428">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-429">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-429">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-430">NX_DNS_PARAM_ERROR (0xA8) — недопустимый входной параметр.</span><span class="sxs-lookup"><span data-stu-id="ca252-430">NX_DNS_PARAM_ERROR: (0xA8) Invalid input parameter.</span></span>
- <span data-ttu-id="ca252-431">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-431">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="ca252-432">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-432">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-433">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-433">Allowed From</span></span>

<span data-ttu-id="ca252-434">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-434">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-435">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-435">Example</span></span>

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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="ca252-436">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="ca252-436">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="ca252-437">Поиск имени узла по IP-адресу</span><span class="sxs-lookup"><span data-stu-id="ca252-437">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-438">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-438">Prototype</span></span>

```c
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-439">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-439">Description</span></span>

<span data-ttu-id="ca252-440">Эта служба запрашивает разрешение имен для указанного IP-адреса с одного DNS-сервера или нескольких, ранее указанных приложением.</span><span class="sxs-lookup"><span data-stu-id="ca252-440">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="ca252-441">В случае успешного выполнения возвращается имя узла, оканчивающееся символом NULL, в строке, заданной *host_name_ptr*.</span><span class="sxs-lookup"><span data-stu-id="ca252-441">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-442">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-442">Input Parameters</span></span>

- <span data-ttu-id="ca252-443">**dns_ptr**: указатель на ранее созданный экземпляр DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-443">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="ca252-444">**ip_address**: IP-адрес для разрешения в имя</span><span class="sxs-lookup"><span data-stu-id="ca252-444">**ip_address**: IP address to resolve into a name</span></span>
- <span data-ttu-id="ca252-445">**host_name_ptr**: указатель на область назначения для имени узла</span><span class="sxs-lookup"><span data-stu-id="ca252-445">**host_name_ptr**: Pointer to destination area for host name</span></span>
- <span data-ttu-id="ca252-446">**max_host_name_size**: размер области назначения для имени узла</span><span class="sxs-lookup"><span data-stu-id="ca252-446">**max_host_name_size**: Size of destination area for host name</span></span>
- <span data-ttu-id="ca252-447">**wait_option** определяет, как долго служба будет ожидать (в тактах таймера) ответа DNS-сервера после каждого запроса DNS и повторных попыток выполнения запроса. Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ca252-447">**wait_option**: Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry The wait options are defined as follows:</span></span>
    - <span data-ttu-id="ca252-448">**Значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Выбор числового значения (1–0xFFFFFFFE) указывает максимальное число тактов таймера для приостановки при ожидании разрешения DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-448">**timeout value**: (0x00000001-0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="ca252-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="ca252-449">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-450">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-450">Return Values</span></span>

- <span data-ttu-id="ca252-451">**NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="ca252-451">**NX_SUCCESS**: (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="ca252-452">**NX_DNS_TIMEOUT** (0xA2) — истекло время ожидания при получении мьютекса DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-452">**NX_DNS_TIMEOUT**: (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="ca252-453">**NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="ca252-453">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="ca252-454">**NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="ca252-454">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="ca252-455">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — входной адрес имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ca252-455">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null input address</span></span>
- <span data-ttu-id="ca252-456">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) — индекс указывает на недопустимый тип адреса (например, IPv6).</span><span class="sxs-lookup"><span data-stu-id="ca252-456">**NX_DNS_INVALID_ADDRESS_TYPE**: (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="ca252-457">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-457">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="ca252-458">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-458">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ca252-459">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-459">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-460">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-460">Allowed From</span></span>

<span data-ttu-id="ca252-461">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-461">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-462">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-462">Example</span></span>

```c
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */

```

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="ca252-463">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="ca252-463">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="ca252-464">Поиск IP-адреса по имени узла</span><span class="sxs-lookup"><span data-stu-id="ca252-464">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-465">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-465">Prototype</span></span>

```c
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-466">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-466">Description</span></span>

<span data-ttu-id="ca252-467">Эта служба запрашивает разрешение имен для указанного имени, на которое указывает *host_name*, с одного DNS-сервера или нескольких, ранее указанных приложением.</span><span class="sxs-lookup"><span data-stu-id="ca252-467">This service requests name resolution of the supplied name, pointed to by *host_name*, from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="ca252-468">В случае успешного выполнения соответствующий IP-адрес возвращается в место назначения, на которое указывает *host_address_ptr*.</span><span class="sxs-lookup"><span data-stu-id="ca252-468">If successful, the associated IP address is returned in the destination pointed to by *host_address_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-469">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-469">Input Parameters</span></span>

- <span data-ttu-id="ca252-470">**dns_ptr**: указатель на ранее созданный экземпляр DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-470">**dns_ptr**: Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="ca252-471">**host_name**: указатель на имя узла</span><span class="sxs-lookup"><span data-stu-id="ca252-471">**host_name**: Pointer to host name</span></span>
- <span data-ttu-id="ca252-472">**host_address_ptr**: указатель на IP-адрес узла DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-472">**host_address_ptr**: Pointer to DNS host IP address</span></span>
- <span data-ttu-id="ca252-473">**wait_option** определяет, как долго служба будет ожидать разрешения DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-473">**wait_option**: Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="ca252-474">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ca252-474">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="ca252-475">**Значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Выбор числового значения (1–0xFFFFFFFE) указывает максимальное число тактов таймера для приостановки при ожидании разрешения DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-475">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>
    - <span data-ttu-id="ca252-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока DNS-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="ca252-476">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-477">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-477">Return Values</span></span>

- <span data-ttu-id="ca252-478">**NX_SUCCESS** (0x00) — разрешение DNS успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="ca252-478">**NX_SUCCESS**: (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="ca252-479">**NX_DNS_NO_SERVER** (0xA1) — не указан адрес DNS-сервера.</span><span class="sxs-lookup"><span data-stu-id="ca252-479">**NX_DNS_NO_SERVER**: (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="ca252-480">**NX_DNS_QUERY_FAILED** (0xA3) — не получен ответ на запрос.</span><span class="sxs-lookup"><span data-stu-id="ca252-480">**NX_DNS_QUERY_FAILED**: (0xA3) Received no response to query</span></span>
- <span data-ttu-id="ca252-481">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-481">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="ca252-482">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-482">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ca252-483">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-483">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-484">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-484">Allowed From</span></span>

<span data-ttu-id="ca252-485">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-485">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-486">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-486">Example</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="ca252-487">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="ca252-487">nx_dns_host_text_get</span></span>

<span data-ttu-id="ca252-488">Поиск текстовой строки для имени входного домена</span><span class="sxs-lookup"><span data-stu-id="ca252-488">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-489">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-489">Prototype</span></span>

```c
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ca252-490">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-490">Description</span></span>

<span data-ttu-id="ca252-491">Эта служба отправляет запрос типа TXT с указанными доменным именем и буфером для получения произвольных строковых данных.</span><span class="sxs-lookup"><span data-stu-id="ca252-491">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="ca252-492">DNS-клиент копирует текстовую строку в записи TXT в ответе DNS-сервера в адрес памяти *record_buffer*.</span><span class="sxs-lookup"><span data-stu-id="ca252-492">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

>[!NOTE]
><span data-ttu-id="ca252-493">Для получения данных *record_buffer* не должен быть выровнен по 4 байт.</span><span class="sxs-lookup"><span data-stu-id="ca252-493">The *record_buffer* does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-494">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-494">Input Parameters</span></span>

- <span data-ttu-id="ca252-495">**dns_ptr**: указатель на DNS-клиент</span><span class="sxs-lookup"><span data-stu-id="ca252-495">**dns_ptr**: Pointer to DNS Client.</span></span>  
- <span data-ttu-id="ca252-496">**host_name**: указатель на имя узла, по которому следует выполнять поиск</span><span class="sxs-lookup"><span data-stu-id="ca252-496">**host_name**: Pointer to name of host to search on</span></span>
- <span data-ttu-id="ca252-497">**record_buffer**: указатель на расположение, в которое следует извлечь данные TXT</span><span class="sxs-lookup"><span data-stu-id="ca252-497">**record_buffer**: Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="ca252-498">**buffer_size**: размер буфера для хранения данных TXT</span><span class="sxs-lookup"><span data-stu-id="ca252-498">**buffer_size**: Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="ca252-499">**wait_option**: параметр ожидания для получения ответа DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-499">**wait_option**: Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-500">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-500">Return Values</span></span>

- <span data-ttu-id="ca252-501">**NX_SUCCESS** (0x00) — строка TXT успешно получена.</span><span class="sxs-lookup"><span data-stu-id="ca252-501">**NX_SUCCESS**: (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="ca252-502">**NX_DNS_NO_SERVER** (0xA1) — список серверов клиента пуст.</span><span class="sxs-lookup"><span data-stu-id="ca252-502">**NX_DNS_NO_SERVER**: (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="ca252-503">**NX_DNS_QUERY_FAILED** (0xA3) — не получен допустимый ответ DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-503">**NX_DNS_QUERY_FAILED**: (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="ca252-504">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-504">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ca252-505">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-505">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ca252-506">NX_DNS_PARAM_ERROR (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-506">NX_DNS_PARAM_ERROR: (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-507">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-507">Allowed From</span></span>

<span data-ttu-id="ca252-508">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-508">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-509">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-509">Example</span></span>

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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="ca252-510">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="ca252-510">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="ca252-511">Задание пула пакетов DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-511">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-512">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-512">Prototype</span></span>

```c
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="ca252-513">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-513">Description</span></span>

<span data-ttu-id="ca252-514">Эта служба задает ранее созданный пул пакетов в качестве пула пакетов DNS-**клиента**.</span><span class="sxs-lookup"><span data-stu-id="ca252-514">This service sets a previously created packet pool as the DNS **Client** packet pool.</span></span> <span data-ttu-id="ca252-515">DNS-клиент будет использовать этот пул пакетов для отправки запросов DNS, поэтому размер полезной нагрузки пакета должен быть не меньше значения NX_DNS_PACKET_PAYLOAD_UNALIGNED, включающего в себя кадры Ethernet, заголовки IP и UDP и определенного в файле *nx_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="ca252-515">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD_UNALIGNED which includes the Ethernet frame, IP and UDP headers and is defined in *nx_dns.h*.</span></span>
 
>[!NOTE]
><span data-ttu-id="ca252-516">При удалении DNS-клиента пул пакетов не удаляется вместе с ним. Приложение может удалить пул пакетов, когда он больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="ca252-516">When the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>

>[!NOTE]
><span data-ttu-id="ca252-517">Эта служба доступна, только если параметр конфигурации NX_DNS_CLIENT_USER_CREATE_PACKET_POOL определен в файле *nx_dns.h*.</span><span class="sxs-lookup"><span data-stu-id="ca252-517">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nx_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-518">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-518">Input Parameters</span></span>

- <span data-ttu-id="ca252-519">**dns_ptr**: указатель на ранее созданный экземпляр DNS-**клиента**</span><span class="sxs-lookup"><span data-stu-id="ca252-519">**dns_ptr**: Pointer to previously created DNS **Client** instance.</span></span>
- <span data-ttu-id="ca252-520">**pool_ptr**: указатель на ранее созданный пул пакетов</span><span class="sxs-lookup"><span data-stu-id="ca252-520">**pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-521">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-521">Return Values</span></span>

- <span data-ttu-id="ca252-522">**NX_SUCCESS** (0x00) — успешное выполнение.</span><span class="sxs-lookup"><span data-stu-id="ca252-522">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="ca252-523">**NX_NOT_ENABLED** (0x14) — клиент не настроен для использования этого параметра.</span><span class="sxs-lookup"><span data-stu-id="ca252-523">**NX_NOT_ENABLED**: (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="ca252-524">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS-**клиента**.</span><span class="sxs-lookup"><span data-stu-id="ca252-524">NX_PTR_ERROR: (0x07) Invalid IP or DNS **Client** pointer.</span></span>
- <span data-ttu-id="ca252-525">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-525">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-526">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-526">Allowed From</span></span>

<span data-ttu-id="ca252-527">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-527">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-528">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-528">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="ca252-529">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="ca252-529">nx_dns_server_add</span></span>

<span data-ttu-id="ca252-530">Добавление DNS-сервера с IP-адресом</span><span class="sxs-lookup"><span data-stu-id="ca252-530">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-531">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-531">Prototype</span></span>

```c
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ca252-532">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-532">Description</span></span>

<span data-ttu-id="ca252-533">Эта служба добавляет DNS-сервер с IPv4-адресом в список серверов.</span><span class="sxs-lookup"><span data-stu-id="ca252-533">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-534">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-534">Input Parameters</span></span>

- <span data-ttu-id="ca252-535">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-535">**dns_ptr**: Pointer to DNS control block.</span></span>  
- <span data-ttu-id="ca252-536">**server_address**: IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-536">**server_address**: IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-537">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-537">Return Values</span></span>

- <span data-ttu-id="ca252-538">**NX_SUCCESS** (0x00) — сервер успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="ca252-538">**NX_SUCCESS**: (0x00) Server successfully added</span></span>
- <span data-ttu-id="ca252-539">**NX_DNS_DUPLICATE_ENTRY** или **NX_NO_MORE_ENTRIES** (0x17) — добавление DNS-серверов запрещено (список полон).</span><span class="sxs-lookup"><span data-stu-id="ca252-539">**NX_DNS_DUPLICATE_ENTRY** or **NX_NO_MORE_ENTRIES**: (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="ca252-540">**NX_DNS_PARAM_ERROR** (0xA8) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-540">**NX_DNS_PARAM_ERROR**: (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="ca252-541">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ca252-541">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="ca252-542">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-542">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="ca252-543">NX_DNS_BAD_ADDRESS_ERROR (0xA4) — введен адрес сервера со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="ca252-543">NX_DNS_BAD_ADDRESS_ERROR: (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-544">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-544">Allowed From</span></span>

<span data-ttu-id="ca252-545">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-545">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-546">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-546">Example</span></span>

```c
/* Add a DNS Server at IP address 202.2.2.13.  */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added.  */
```

## <a name="nx_dns_server_get"></a><span data-ttu-id="ca252-547">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="ca252-547">nx_dns_server_get</span></span>

<span data-ttu-id="ca252-548">Возврат DNS-сервера с IPv4-адресом из списка клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-548">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-549">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-549">Prototype</span></span>

```c
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                       ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="ca252-550">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-550">Description</span></span>

<span data-ttu-id="ca252-551">Эта служба возвращает DNS-сервер с IPv4-адресом из списка серверов по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="ca252-551">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> <span data-ttu-id="ca252-552">Обратите внимание, что индекс отсчитывается от нуля.</span><span class="sxs-lookup"><span data-stu-id="ca252-552">Note that the index is zero based.</span></span> <span data-ttu-id="ca252-553">Если значение входного индекса превышает размер списка DNS-клиента, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="ca252-553">If the input index exceeds the size of the DNS Client list, an error is returned.</span></span> <span data-ttu-id="ca252-554">Сначала можно вызвать службу *nx_dns_get_serverlist_size*, чтобы получить количество DNS-серверов в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-554">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-555">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-555">Input Parameters</span></span>

- <span data-ttu-id="ca252-556">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-556">**dns_ptr**: Pointer to DNS control block</span></span>  
- <span data-ttu-id="ca252-557">**index**: индекс в списке серверов DNS-клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-557">**index**: Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="ca252-558">**dns_server_address**: указатель на IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-558">**dns_server_address**: Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-559">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-559">Return Values</span></span>

- <span data-ttu-id="ca252-560">**NX_SUCCESS** (0x00) — сервер успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="ca252-560">**NX_SUCCESS**: (0x00) Successful server returned</span></span>
- <span data-ttu-id="ca252-561">**NX_DNS_SERVER_NOT_FOUND** (0xA9) — индекс указывает на пустой слот.</span><span class="sxs-lookup"><span data-stu-id="ca252-561">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="ca252-562">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — индекс указывает на пустой адрес.</span><span class="sxs-lookup"><span data-stu-id="ca252-562">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="ca252-563">**NX_DNS_PARAM_ERROR** (0xA8) — значение индекса превышает размер списка.</span><span class="sxs-lookup"><span data-stu-id="ca252-563">**NX_DNS_PARAM_ERROR**: (0xA8) Index exceeds size of list</span></span>
- <span data-ttu-id="ca252-564">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-564">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ca252-565">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-565">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-566">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-566">Allowed From</span></span>

<span data-ttu-id="ca252-567">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-568">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-568">Example</span></span>

```c
ULONG     my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list.  */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned.  */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="ca252-569">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="ca252-569">nx_dns_server_remove</span></span>

<span data-ttu-id="ca252-570">Удаление DNS-сервера с IPv4-адресом из списка клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-570">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-571">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-571">Prototype</span></span>

```c
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ca252-572">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-572">Description</span></span>

<span data-ttu-id="ca252-573">Эта служба удаляет DNS-сервер с IPv4-адресом из списка клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-573">This service removes an IPv4 DNS Server from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-574">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-574">Input Parameters</span></span>

- <span data-ttu-id="ca252-575">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-575">**dns_ptr**: Pointer to DNS control block.</span></span>
- <span data-ttu-id="ca252-576">**server_address**: IP-адрес DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ca252-576">**server_address**: IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-577">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-577">Return Values</span></span>

- <span data-ttu-id="ca252-578">**NX_SUCCESS** (0x00) — DNS-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ca252-578">**NX_SUCCESS**: (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="ca252-579">**NX_DNS_SERVER_NOT_FOUND** (0xA9) — сервер отсутствует в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-579">**NX_DNS_SERVER_NOT_FOUND**: (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="ca252-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) — введен адрес сервера со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="ca252-580">**NX_DNS_BAD_ADDRESS_ERROR**: (0xA4) Null server address input</span></span>
- <span data-ttu-id="ca252-581">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-581">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ca252-582">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-582">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-583">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-583">Allowed From</span></span>

<span data-ttu-id="ca252-584">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-584">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-585">Например, .</span><span class="sxs-lookup"><span data-stu-id="ca252-585">Example</span></span>

```c
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="ca252-586">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="ca252-586">nx_dns_server_remove_all</span></span>

<span data-ttu-id="ca252-587">Удаление всех DNS-серверов из списка клиента</span><span class="sxs-lookup"><span data-stu-id="ca252-587">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="ca252-588">Прототип</span><span class="sxs-lookup"><span data-stu-id="ca252-588">Prototype</span></span>

```c
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="ca252-589">Описание</span><span class="sxs-lookup"><span data-stu-id="ca252-589">Description</span></span>

<span data-ttu-id="ca252-590">Эта служба удаляет все DNS-серверы из списка клиента.</span><span class="sxs-lookup"><span data-stu-id="ca252-590">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ca252-591">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ca252-591">Input Parameters</span></span>

- <span data-ttu-id="ca252-592">**dns_ptr**: указатель на блок управления DNS</span><span class="sxs-lookup"><span data-stu-id="ca252-592">**dns_ptr**: Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ca252-593">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ca252-593">Return Values</span></span>

- <span data-ttu-id="ca252-594">**NX_SUCCESS** (0x00) — DNS-серверы успешно удалены.</span><span class="sxs-lookup"><span data-stu-id="ca252-594">**NX_SUCCESS**: (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="ca252-595">**NX_DNS_ERROR** (0xA0) — не удается получить мьютекс защиты.</span><span class="sxs-lookup"><span data-stu-id="ca252-595">**NX_DNS_ERROR**: (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="ca252-596">NX_PTR_ERROR (0x07) — недопустимый указатель IP или DNS.</span><span class="sxs-lookup"><span data-stu-id="ca252-596">NX_PTR_ERROR: (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="ca252-597">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ca252-597">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ca252-598">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ca252-598">Allowed From</span></span>

<span data-ttu-id="ca252-599">Потоки</span><span class="sxs-lookup"><span data-stu-id="ca252-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ca252-600">Пример</span><span class="sxs-lookup"><span data-stu-id="ca252-600">Example</span></span>

```c

/* Remove all DNS Servers from the Client list.  */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed.  */
```